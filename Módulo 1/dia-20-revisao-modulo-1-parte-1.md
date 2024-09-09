# Dia 20: Revisão do Módulo 1 - Parte 1/3

## Objetivos da Revisão
Nesta primeira parte da revisão, vamos recapitular e reforçar os seguintes tópicos:
1. Variáveis e Tipos de Dados
2. Operadores
3. Estruturas de Controle
4. Funções Básicas
5. Arrays

## 1. Variáveis e Tipos de Dados

### Declaração de Variáveis
Em JavaScript, temos três formas de declarar variáveis:

```javascript
var x = 5;     // Forma antiga, evite usar
let y = 10;    // Preferível para variáveis que podem mudar
const z = 15;  // Para valores constantes
```

### Tipos de Dados Primitivos
JavaScript tem seis tipos de dados primitivos:

1. **Number**: Representa números inteiros ou de ponto flutuante
2. **String**: Representa texto
3. **Boolean**: Representa verdadeiro (`true`) ou falso (`false`)
4. **Undefined**: Representa uma variável declarada, mas não inicializada
5. **Null**: Representa a ausência intencional de qualquer valor
6. **Symbol**: Representa um identificador único (introduzido no ES6)

Exemplo:
```javascript
let numero = 42;                  // Number
let texto = "Olá, mundo!";        // String
let eVerdade = true;              // Boolean
let naoDefinido;                  // Undefined
let nulo = null;                  // Null
let simbolo = Symbol("id");       // Symbol
```

### Verificação de Tipos
Use o operador `typeof` para verificar o tipo de uma variável:

```javascript
console.log(typeof numero);       // "number"
console.log(typeof texto);        // "string"
console.log(typeof eVerdade);     // "boolean"
console.log(typeof naoDefinido);  // "undefined"
console.log(typeof nulo);         // "object" (um bug histórico em JavaScript)
console.log(typeof simbolo);      // "symbol"
```

## 2. Operadores

### Operadores Aritméticos
```javascript
let a = 10, b = 3;
console.log(a + b);  // Adição: 13
console.log(a - b);  // Subtração: 7
console.log(a * b);  // Multiplicação: 30
console.log(a / b);  // Divisão: 3.3333...
console.log(a % b);  // Módulo (resto): 1
console.log(a ** b); // Exponenciação: 1000
```

### Operadores de Comparação
```javascript
console.log(5 == "5");   // true (comparação de valor)
console.log(5 === "5");  // false (comparação de valor e tipo)
console.log(5 != "5");   // false
console.log(5 !== "5");  // true
console.log(5 > 3);      // true
console.log(5 <= 5);     // true
```

### Operadores Lógicos
```javascript
console.log(true && false);  // AND lógico: false
console.log(true || false);  // OR lógico: true
console.log(!true);          // NOT lógico: false
```

## 3. Estruturas de Controle

### If...Else
```javascript
let idade = 18;

if (idade >= 18) {
    console.log("Maior de idade");
} else if (idade >= 13) {
    console.log("Adolescente");
} else {
    console.log("Criança");
}
```

### Switch
```javascript
let diaSemana = 3;
switch (diaSemana) {
    case 1:
        console.log("Segunda-feira");
        break;
    case 2:
        console.log("Terça-feira");
        break;
    case 3:
        console.log("Quarta-feira");
        break;
    // ... outros casos ...
    default:
        console.log("Dia inválido");
}
```

### Loops
```javascript
// For loop
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// While loop
let j = 0;
while (j < 5) {
    console.log(j);
    j++;
}

// Do...While loop
let k = 0;
do {
    console.log(k);
    k++;
} while (k < 5);
```

## 4. Funções Básicas

### Declaração de Função
```javascript
function saudacao(nome) {
    return `Olá, ${nome}!`;
}

console.log(saudacao("Maria")); // Saída: Olá, Maria!
```

### Função de Expressão
```javascript
const quadrado = function(numero) {
    return numero * numero;
};

console.log(quadrado(4)); // Saída: 16
```

### Arrow Function
```javascript
const cubo = (numero) => numero ** 3;

console.log(cubo(3)); // Saída: 27
```

## 5. Arrays

### Criação e Acesso
```javascript
let frutas = ["maçã", "banana", "laranja"];
console.log(frutas[1]); // Saída: banana
```

### Métodos de Array
```javascript
// Adicionar ao final
frutas.push("uva");

// Remover do final
let ultimaFruta = frutas.pop();

// Adicionar ao início
frutas.unshift("morango");

// Remover do início
let primeiraFruta = frutas.shift();

console.log(frutas); // Saída: ["morango", "maçã", "banana", "laranja"]
```

### Iteração em Arrays
```javascript
frutas.forEach((fruta, index) => {
    console.log(`${index + 1}: ${fruta}`);
});

// Usando map
let frutasMaiusculas = frutas.map(fruta => fruta.toUpperCase());

// Usando filter
let frutasComA = frutas.filter(fruta => fruta.includes('a'));
```

## Exercício de Revisão

Crie uma função que recebe um array de números e retorna um novo array contendo apenas os números pares, dobrados. Use as estruturas e conceitos que revisamos.

Exemplo de solução:

```javascript
function dobrarPares(numeros) {
    return numeros
        .filter(num => num % 2 === 0)
        .map(num => num * 2);
}

let nums = [1, 2, 3, 4, 5, 6, 7, 8];
console.log(dobrarPares(nums)); // Saída: [4, 8, 12, 16]
```

## Recursos Adicionais

- [Guia JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide)
- [JavaScript básico (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [W3Schools JavaScript Tutorial (em português)](https://www.w3schools.com/js/default.asp)

Na próxima parte da revisão, abordaremos objetos, JSON, e começaremos a revisar classes em JavaScript.

