Diferenças entre var, let e const em JavaScript:

1. var:
   - Era a forma original de declarar variáveis em JavaScript.
   - Tem escopo de função ou global, mas não de bloco.
   - Pode ser redeclarada e reatribuída.
   - Sofre de "hoisting" (elevação), o que significa que a declaração é movida para o topo do seu escopo, mas não a inicialização.

2. let:
   - Introduzido no ES6 (ECMAScript 2015).
   - Tem escopo de bloco.
   - Pode ser reatribuída, mas não redeclarada no mesmo escopo.
   - Não sofre hoisting da mesma forma que var (fica na "temporal dead zone" até ser declarada).

3. const:
   - Também introduzido no ES6.
   - Tem escopo de bloco.
   - Não pode ser reatribuída nem redeclarada.
   - Para objetos e arrays, o conteúdo pode ser modificado, mas a referência não pode ser alterada.
   - Também fica na "temporal dead zone" até ser declarada.

Exemplos:

```javascript
// var
var x = 1;
if (true) {
    var x = 2;  // mesma variável!
    console.log(x);  // 2
}
console.log(x);  // 2

// let
let y = 1;
if (true) {
    let y = 2;  // variável diferente
    console.log(y);  // 2
}
console.log(y);  // 1

// const
const z = 1;
// z = 2;  // Isso causaria um erro

const obj = {prop: 1};
obj.prop = 2;  // Isso é permitido
// obj = {};  // Isso causaria um erro
```

Recomendações de uso:
1. Use `const` por padrão.
2. Use `let` apenas quando você precisa reatribuir a variável.
3. Evite usar `var` em código moderno.

Essas práticas ajudam a tornar o código mais previsível e menos propenso a erros relacionados ao escopo e mutabilidade das variáveis.

JavaScript é uma linguagem dinamicamente tipada, o que significa que as variáveis podem conter diferentes tipos de dados ao longo do tempo. Os tipos de dados básicos em JavaScript são:

1. Number:
   - Representa tanto inteiros quanto números de ponto flutuante.
   - Exemplo: `let age = 30;` ou `let pi = 3.14;`

2. String:
   - Representa texto.
   - Pode ser definido com aspas simples, duplas ou backticks.
   - Exemplo: `let name = "Alice";` ou `let greeting = `Hello, ${name}`;`

3. Boolean:
   - Representa um valor verdadeiro ou falso.
   - Exemplo: `let isActive = true;`

4. Undefined:
   - Representa uma variável que foi declarada, mas não atribuída.
   - Exemplo: `let x;` (x será undefined)

5. Null:
   - Representa a ausência intencional de qualquer valor ou objeto.
   - Exemplo: `let empty = null;`

6. Object:
   - Estrutura de dados que armazena coleções de dados e entidades mais complexas.
   - Exemplo: `let person = {name: "Bob", age: 25};`

7. Array:
   - Um tipo especial de objeto usado para armazenar listas ordenadas de valores.
   - Exemplo: `let fruits = ["apple", "banana", "orange"];`

8. Symbol (introduzido no ES6):
   - Representa um identificador único.
   - Exemplo: `let id = Symbol("id");`

9. BigInt (introduzido mais recentemente):
   - Representa inteiros muito grandes que o tipo Number não pode representar com precisão.
   - Exemplo: `let bigNumber = 1234567890123456789012345678901234567890n;`

Você pode usar o operador `typeof` para verificar o tipo de uma variável:

```javascript
console.log(typeof 42);  // "number"
console.log(typeof "hello");  // "string"
console.log(typeof true);  // "boolean"
console.log(typeof undefined);  // "undefined"
console.log(typeof null);  // "object" (isso é considerado um bug histórico em JavaScript)
console.log(typeof {});  // "object"
console.log(typeof []);  // "object"
console.log(typeof Symbol("id"));  // "symbol"
console.log(typeof 42n);  // "bigint"
```

É importante notar que, em TypeScript, você terá a capacidade de definir tipos mais explicitamente, o que ajuda a prevenir erros relacionados a tipos durante o desenvolvimento.
