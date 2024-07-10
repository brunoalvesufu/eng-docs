# 👀 Problema

- Filmes, séries e jogos recebem notas de analistas, que por sua vez são compiladas em vários sites.
- Tanto a opinião de um crítico em específico, como a nota média de todos os críticos, são importantes na tomada de decisão do que consumir.
- Navegar por todos esses sites consome tempo, além de ser confuso em alguns casos.

---

# 💭 Proposta

- Proponho um sistema que faça o scrapping desses sites e reporte as notas ao usuário baseado em algumas regras, como: crítico específico, gênero específico, diretor ou atores envolvidos, empresa responsável, etc.
- O sistema não envia análises em que a nota é menor que 80.
- A princípio, o sistema receberá o link do site a realizar o scrapping e o email para onde o report será enviado.
- A primeira versão fará o scrapping apenas do site Opencritic, especificamente das notas dadas pelo [Metro Game Central](https://opencritic.com/outlet/75/metro-gamecentral).
- O futuro do projeto deverá contemplar outras páginas do site Opencritic, além dos sites Metacritic, Rotten Tomatoes e IMDB.
- A implementação do código deve contemplar Injeção de Dependência, onde apenas o módulo para um site específica precisará ser desenvolvido. Métodos como fetchWeb, fetchDB e sendReport serão diferentes para cada ambiente.
- Haverá uma página wed disponível para que o usuário insira seu nome, e-mail e site a ser varrido.
- O sistema irá rodar todos os dias às 20h.

---

# 🛫 Plano

- O sistema será desenvolvido em Typescript, usando arquitetura hexagonal.
    
- O sistema terá quatro módulos principais, colocados em um único repositório e separado por diretórios.
    
- Em uma segunda versão, os módulos serão convertidos em micro-serviços com comunicação por Kafka.
    
- Os módulos são:
    
    - fetch: busca os elementos na web e os salva sem análise em uma tabela SQL chamada **elementsDB (elemHash, page, element);**
    - scrape: extrai as informações relevantes dos elementos da tabela elements e as salva em outra tabela chamada **reviewsDB (elemHash, title, grade, grade2, description, source);**
    - request: endpoint onde o usuário passa suas informações e requisita a geração de um novo report, os usuários serão salvos na tabela **usersDB (userID, name, email)**, suas requisições serão salvas na tabela **requestsDB (requestID, page, users_ids[userID], lastElemHash);**
    - report: monta os relatórios e os envia aos usuários.
    
    ```mermaid
    flowchart TD
      user((user)) <-->|system endpoint| request
      request -->|store request| requestsDB[("requestsDB")]
      request -->|store user| usersDB[("usersDB")]
      Trigger_at_8pm --> fetch
      requestsDB -->|fetch page| fetch 
      fetch <-->|HTTP| website("website")
      fetch -->|store elements| elementsDB[("elementsDB")]
      fetch -->|elements_ids| scrape
      elementsDB[("elementsDB")]-->|fetch elements| scrape 
      scrape -->|stores reviews| reviewsDB[("reviewsDB")]
      scrape -->|elements_ids| report
    	reviewsDB[("reviewsDB")] -->|fetch_reviews| report
    	elementsDB -->|fetch pages| report
    	usersDB -->|fetch users| report
    	report -->|e-mail| user((user))
    ```
    

1. usuário acessa a página de cadastro (disponibilizada por request) e informa nome, e-mail e página a ser varrida;
2. request salva as informações do usuário em usersDB e as informações da requisição em requestsDB;
3. fetch, diariamente as 8pm, busca as páginas que devem ser varridas;
4. fetch, uma a uma, varre a página e:
    1. faz um diff com o hash dos elementos já presentes no banco (uso de hash como blindagem ao tamanho dos elementos);
    2. para varrimento de páginas sequenciais, fetch avancará até encontrar o hash primeiro elemento encontrado no último varrimento.
5. fetch salva os novos elementos na tabela elementsDB;
6. fetch avisa ao scrape se há novas informações, passando os ids dos elementos;
7. scrape consulta os ids na tabela de elementsDB, realiza a extração das informações e as salva em reviewsDB;
8. scrape avisa ao report sobre as novas reviews, enviando os ids dos elementos;
9. report usa os ids dos elementos para consultar a página dos novos elementos em elementsDB;
10. report consulta os usuários que solicitaram informações naquela página;
11. report usa os ids dos elementos para consultar as reviews em reviewsDB;
12. report cria o relatório usando os dados das reviews e envia ao email dos usuários.

PS: O excesso de consulta e escrita do banco de dados é proposital, com objetivo didático.