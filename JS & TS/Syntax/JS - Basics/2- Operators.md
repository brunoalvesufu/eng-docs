Os operadores são símbolos especiais que realizamos operações em variáveis e valores. Vamos dividir os operadores em categorias principais:

1. Operadores Aritméticos:
   - Adição (+): `5 + 3 // 8`
   - Subtração (-): `5 - 3 // 2`
   - Multiplicação (*): `5 * 3 // 15`
   - Divisão (/): `6 / 3 // 2`
   - Módulo (%): `7 % 3 // 1` (resto da divisão)
   - Exponenciação (**): `2 ** 3 // 8`
   - Incremento (++): `let x = 5; x++; // x agora é 6`
   - Decremento (--): `let y = 5; y--; // y agora é 4`

2. Operadores de Comparação:
   - Igual (`==`): `5 == "5" // true` (compara valor, com coerção de tipo)
   - Estritamente igual (`===`): `5 === "5" // false` (compara valor e tipo)
   - Diferente (!=): `5 != "6" // true`
   - Estritamente diferente (`!==`): `5 !== "5" // true`
   - Maior que (>): `5 > 3 // true`
   - Menor que (<): `3 < 5 // true`
   - Maior ou igual (>=): `5 >= 5 // true`
   - Menor ou igual (<=): `4 <= 5 // true`

3. Operadores Lógicos:
   - AND (&&): `true && false // false`
   - OR (||): `true || false // true`
   - NOT (!): `!true // false`

4. Operadores de Atribuição:
   - Atribuição simples (=): `let x = 5;`
   - Atribuição com adição (+=): `x += 3; // equivalente a x = x + 3`
   - Atribuição com subtração (-=): `x -= 2;`
   - Atribuição com multiplicação (*=): `x *= 2;`
   - Atribuição com divisão (/=): `x /= 2;`

5. Operador Ternário:
   - Sintaxe: `condição ? expressão1 : expressão2`
   - Exemplo: `let status = age >= 18 ? "adulto" : "menor";`

6. Operadores de Tipo:
   - typeof: `typeof 42; // "number"`
   - instanceof: `[] instanceof Array; // true`

7. Operadores de Bit a Bit (menos comuns, mas importantes em certos contextos):
   - AND (&), OR (|), XOR (^), NOT (~), Left shift (<<), Right shift (>>), Zero-fill right shift (>>>)

Exemplo de uso combinado de operadores:

```javascript
let x = 10;
let y = 5;
let z = 2;

let result = (x + y) * z;
console.log(result); // 30

let isEven = x % 2 === 0;
console.log(isEven); // true

let message = x > y ? "x é maior que y" : "x não é maior que y";
console.log(message); // "x é maior que y"
```

Estes operadores são fundamentais para realizar cálculos, comparações e tomadas de decisão em JavaScript. Ao avançar para TypeScript, você encontrará operadores adicionais específicos para trabalhar com tipos.
