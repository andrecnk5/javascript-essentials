# Dia 5: Operadores Lógicos e de Comparação

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Utilizar operadores de comparação para avaliar e comparar valores
2. Compreender e aplicar operadores lógicos para combinar condições
3. Entender a precedência entre operadores lógicos e de comparação
4. Aplicar estes operadores em estruturas condicionais simples

## 1. Operadores de Comparação

Os operadores de comparação são usados para comparar valores e retornam um valor booleano (true ou false).

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `==`     | Igual a (compara valor) | `5 == "5"` retorna `true` |
| `===`    | Estritamente igual a (compara valor e tipo) | `5 === "5"` retorna `false` |
| `!=`     | Diferente de (compara valor) | `5 != "6"` retorna `true` |
| `!==`    | Estritamente diferente de (compara valor e tipo) | `5 !== "5"` retorna `true` |
| `>`      | Maior que | `7 > 5` retorna `true` |
| `<`      | Menor que | `5 < 3` retorna `false` |
| `>=`     | Maior ou igual a | `7 >= 7` retorna `true` |
| `<=`     | Menor ou igual a | `5 <= 5` retorna `true` |

Exemplo:

```javascript
console.log(5 == "5");   // true (compara apenas o valor)
console.log(5 === "5");  // false (compara valor e tipo)
console.log(10 !== 10);  // false
console.log(10 != "10"); // false
console.log(10 !== "10"); // true (tipos diferentes)
console.log(5 > 3);      // true
console.log(5 < 3);      // false
console.log(5 >= 5);     // true
console.log(5 <= 6);     // true
```

## 2. Operadores Lógicos

Os operadores lógicos são usados para determinar a lógica entre variáveis ou valores.

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `&&`     | E lógico  | `true && true` retorna `true` |
| `||`     | OU lógico | `true || false` retorna `true` |
| `!`      | NÃO lógico | `!true` retorna `false` |

Exemplo:

```javascript
let x = 5;
let y = 10;

console.log(x < 10 && y > 5);  // true (ambas as condições são verdadeiras)
console.log(x < 10 || y < 5);  // true (pelo menos uma condição é verdadeira)
console.log(!(x === y));       // true (x não é igual a y)
```

## 3. Precedência de Operadores

A ordem de precedência dos operadores lógicos é:
1. `!` (NÃO)
2. `&&` (E)
3. `||` (OU)

Os operadores de comparação são avaliados antes dos operadores lógicos.

Exemplo:

```javascript
let a = 5;
let b = 10;
let c = 15;

console.log(a < b && b < c);  // true
console.log(a > b || b < c);  // true
console.log(!(a < b) || c < b);  // false

// Uso de parênteses para alterar a precedência
console.log((a > b || b < c) && c > a);  // true
```

## 4. Aplicação em Estruturas Condicionais

Os operadores de comparação e lógicos são frequentemente usados em estruturas condicionais como `if...else`.

Exemplo:

```javascript
let idade = 18;
let temCarteira = true;

if (idade >= 18 && temCarteira) {
    console.log("Pode dirigir");
} else if (idade >= 18 && !temCarteira) {
    console.log("Precisa tirar a carteira");
} else {
    console.log("Não pode dirigir");
}
```

## Exercício Prático

Crie um script que:
1. Declare variáveis para representar a temperatura e se está chovendo
2. Use operadores de comparação e lógicos para decidir se uma pessoa deve:
   - Ficar em casa (se estiver chovendo e a temperatura for menor que 15°C)
   - Ir à praia (se não estiver chovendo e a temperatura for maior ou igual a 25°C)
   - Ir ao parque (em qualquer outra situação)
3. Imprima a decisão no console

Exemplo de solução:

```javascript
let temperatura = 20;
let estaChovendo = false;

if (estaChovendo && temperatura < 15) {
    console.log("Melhor ficar em casa");
} else if (!estaChovendo && temperatura >= 25) {
    console.log("Ótimo dia para ir à praia!");
} else {
    console.log("Que tal um passeio no parque?");
}
```

## Dicas Úteis

1. Sempre use `===` e `!==` para comparações, a menos que você tenha uma razão específica para usar `==` ou `!=`.
2. Use parênteses para tornar suas expressões lógicas mais claras e evitar erros de precedência.
3. Lembre-se que `&&` retorna o primeiro valor falso ou o último valor se todos forem verdadeiros, enquanto `||` retorna o primeiro valor verdadeiro ou o último valor se todos forem falsos.

## Recursos Adicionais

- [Operadores lógicos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Logical_Operators)
- [Operadores de comparação (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)
- [JavaScript Comparações e Operadores Lógicos (W3Schools em português)](https://www.w3schools.com/js/js_comparisons.asp)

## Próxima Aula

Na próxima aula, mergulharemos nas estruturas de controle em JavaScript, começando com declarações condicionais como `if`, `else if`, e `else`.

