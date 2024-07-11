Node.js e TypeScript oferecem várias ferramentas e técnicas para facilitar o processo de depuração. Vamos explorar algumas delas:

1. Console Logging: Embora básico, o console.log ainda é uma ferramenta útil para debugging rápido.
    
    ```jsx
    console.log('Variable value:', someVariable);
    console.error('An error occurred:', error);
    console.table([{ a: 1, b: 'Y' }, { a: 'Z', b: 2 }]);
    
    ```
    
2. Node.js Debugger: Node.js tem um debugger embutido que pode ser usado com a flag --inspect.
    
    ```bash
    node --inspect your-script.js
    
    ```
    
    Você pode então conectar-se ao debugger usando o Chrome DevTools.
    
3. VS Code Debugger: O VS Code tem excelente suporte para debugging Node.js e TypeScript.
    
    Exemplo de launch.json para Node.js:
    
    ```json
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "program": "${workspaceFolder}/app.js"
    }
    
    ```
    
    Para TypeScript:
    
    ```json
    {
      "type": "node",
      "request": "launch",
      "name": "Launch TypeScript",
      "program": "${workspaceFolder}/app.ts",
      "preLaunchTask": "tsc: build - tsconfig.json",
      "outFiles": ["${workspaceFolder}/dist/**/*.js"]
    }
    
    ```
    
4. Breakpoints: No VS Code, você pode definir breakpoints clicando na margem esquerda do editor.
    
5. Variáveis de Ambiente: Para debugging de configurações específicas de ambiente:
    
    ```jsx
    if (process.env.DEBUG) {
      console.log('Debug info:', debugInfo);
    }
    
    ```
    
6. Source Maps para TypeScript: Source maps permitem que você depure o código TypeScript diretamente, em vez do JavaScript transpilado.
    
    Configuração no tsconfig.json:
    
    ```json
    {
      "compilerOptions": {
        "sourceMap": true
      }
    }
    
    ```
    
7. Debugging Assíncrono: Use `async/await` para tornar o debugging de código assíncrono mais fácil:
    
    ```jsx
    async function fetchData() {
      try {
        const response = await axios.get('<https://api.example.com/data>');
        console.log('Response:', response.data);
      } catch (error) {
        console.error('Error:', error);
      }
    }
    
    ```
    
8. Performance Profiling: Node.js vem com um profiler embutido:
    
    ```bash
    node --prof app.js
    
    ```
    
    Depois de executar seu aplicativo, use o processador de log para analisar os resultados:
    
    ```bash
    node --prof-process isolate-0xnnnnnnnnnnnn-v8.log > processed.txt
    
    ```
    
9. Memory Leaks: Use o heap snapshot no Chrome DevTools para identificar vazamentos de memória.
    
10. Error Handling: Implemente tratamento de erros adequado para facilitar o debugging:
    
    ```jsx
    process.on('unhandledRejection', (reason, promise) => {
      console.log('Unhandled Rejection at:', promise, 'reason:', reason);
    });
    
    ```
    
11. Logging Avançado: Considere usar uma biblioteca de logging como Winston para logging mais robusto:
    
    ```jsx
    const winston = require('winston');
    const logger = winston.createLogger({
      level: 'info',
      format: winston.format.json(),
      transports: [
        new winston.transports.File({ filename: 'error.log', level: 'error' }),
        new winston.transports.File({ filename: 'combined.log' })
      ]
    });
    
    ```
    

Lembre-se, o debugging eficaz geralmente envolve uma combinação dessas técnicas, dependendo da natureza específica do problema que você está enfrentando.