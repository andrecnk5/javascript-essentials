# Dia 6: Estruturas de Decisão (if, else)

## Índice
1. [Introdução às Estruturas de Decisão](#introdução-às-estruturas-de-decisão)
2. [Sintaxe do "if" em JavaScript](#sintaxe-do-if-em-javascript)
3. [Variações do "if"](#variações-do-if)
4. [Operadores de Comparação e Lógicos](#operadores-de-comparação-e-lógicos)
5. [Boas Práticas](#boas-práticas)
6. [Exercícios Teóricos](#exercícios-teóricos)
7. [Exercícios Práticos](#exercícios-práticos)
8. [Conclusão](#conclusão)
9. [Referências e Dicas de Estudo](#referências-e-dicas-de-estudo)

## Introdução às Estruturas de Decisão

As estruturas de decisão são fundamentais na programação, permitindo que o código tome diferentes caminhos com base em condições específicas. Em JavaScript, a estrutura de decisão mais básica e amplamente utilizada é o "if".

### O que é uma estrutura de decisão?

Uma estrutura de decisão é um recurso de programação que permite ao código executar diferentes blocos de instruções dependendo de uma condição ser verdadeira ou falsa.

**Exemplo:**
```javascript
// Estrutura básica de um if
if (condicao) {
    // Código a ser executado se a condição for verdadeira
}
```

### Importância das estruturas de decisão

As estruturas de decisão são cruciais para criar programas dinâmicos e interativos, capazes de responder a diferentes situações e entradas de usuário.

**Exemplo:**
```javascript
let idade = 18;

if (idade >= 18) {
    console.log("Você é maior de idade.");
} // Este código decide se exibe a mensagem com base na idade
```

## Sintaxe do "if" em JavaScript

A sintaxe do "if" em JavaScript é simples e direta, consistindo em uma palavra-chave seguida por uma condição entre parênteses e um bloco de código entre chaves.

### Estrutura básica

A estrutura básica do "if" consiste em:

1. A palavra-chave `if`
2. Uma condição entre parênteses `()`
3. Um bloco de código entre chaves `{}`

**Exemplo:**
```javascript
if (condicao) {
    // Código a ser executado
}
```

### Condições

As condições no "if" são expressões que resultam em um valor booleano (verdadeiro ou falso).

**Exemplo:**
```javascript
let numero = 10;

if (numero > 0) {
    console.log("O número é positivo");
}
// A condição (numero > 0) é avaliada como verdadeira
```

### Bloco de código

O bloco de código dentro das chaves `{}` é executado apenas se a condição for verdadeira.

**Exemplo:**
```javascript
let temperatura = 30;

if (temperatura > 25) {
    console.log("Está quente!");
    console.log("Lembre-se de beber água.");
}
// Ambas as linhas de código serão executadas se a temperatura for maior que 25
```

## Variações do "if"

Existem várias formas de usar o "if" para criar lógicas de decisão mais complexas.

### if...else

O `else` é usado para especificar um bloco de código a ser executado se a condição for falsa.

**Exemplo:**
```javascript
let hora = 14;

if (hora < 12) {
    console.log("Bom dia!");
} else {
    console.log("Boa tarde!");
}
// Como hora é 14, "Boa tarde!" será exibido
```

### if...else if...else

Usado quando há múltiplas condições a serem verificadas.

**Exemplo:**
```javascript
let nota = 75;

if (nota >= 90) {
    console.log("A");
} else if (nota >= 80) {
    console.log("B");
} else if (nota >= 70) {
    console.log("C");
} else {
    console.log("D");
}
// Neste caso, "C" será exibido
```

### Operador ternário

Uma forma abreviada de escrever uma estrutura if...else simples.

**Exemplo:**
```javascript
let idade = 20;
let status = (idade >= 18) ? "Adulto" : "Menor";
console.log(status); // Exibe "Adulto"
```

## Operadores de Comparação e Lógicos

Os operadores de comparação e lógicos são frequentemente usados nas condições do "if".

### Operadores de comparação

- `==` (igualdade)
- `===` (igualdade estrita)
- `!=` (diferença)
- `!==` (diferença estrita)
- `>` (maior que)
- `<` (menor que)
- `>=` (maior ou igual)
- `<=` (menor ou igual)

**Exemplo:**
```javascript
let x = 5;
let y = "5";

if (x == y) {
    console.log("x é igual a y em valor");
}

if (x === y) {
    console.log("x é igual a y em valor e tipo");
} else {
    console.log("x e y são diferentes em tipo");
}
```

### Operadores lógicos

- `&&` (E lógico)
- `||` (OU lógico)
- `!` (NÃO lógico)

**Exemplo:**
```javascript
let idade = 25;
let temCarteira = true;

if (idade >= 18 && temCarteira) {
    console.log("Pode dirigir");
}

if (idade < 18 || !temCarteira) {
    console.log("Não pode dirigir");
}
```

## Boas Práticas

Ao usar estruturas "if", é importante seguir algumas boas práticas para manter o código limpo e eficiente.

1. Use chaves mesmo para blocos de uma linha
2. Evite negações complexas
3. Use operadores de comparação apropriados
4. Mantenha as condições simples
5. Use nomes de variáveis descritivos
6. Evite aninhamentos excessivos de 'if's

**Exemplos:**
```javascript
// Bom
if (condicao) {
    fazerAlgo();
}

// Evite
if (condicao) fazerAlgo();

// Bom
if (estaLogado) {
    // código
}

// Evite
if (!naoEstaLogado) {
    // código
}

// Bom
if (x === 0) {
    console.log("x é zero");
}

// Evite
if (x == "0") {
    console.log("Isso pode levar a comportamentos inesperados");
}
```

## Exercícios Teóricos

### Questões Dissertativas

1. Explique a diferença entre `if...else` e `if...else if...else`. Quando você usaria cada um?

2. Descreva o que é o operador ternário e forneça um exemplo de quando ele seria útil.

### Questões de Múltipla Escolha

1. Qual é a saída do seguinte código?

```javascript
let x = 5;
if (x > 0) {
    console.log("Positivo");
} else if (x < 0) {
    console.log("Negativo");
} else {
    console.log("Zero");
}
```

a) Positivo
b) Negativo
c) Zero
d) Nada será impresso

2. Qual operador é usado para comparação estrita em JavaScript?

a) ==
b) ===
c) =
d) !=

### Questões de Caixa de Múltiplas Escolhas

1. Quais das seguintes são estruturas de decisão válidas em JavaScript? (Selecione todas as corretas)

[ ] if
[ ] if...else
[ ] if...else if
[ ] if...else if...else
[ ] switch

2. Quais dos seguintes são operadores lógicos em JavaScript? (Selecione todos os corretos)

[ ] &&
[ ] ||
[ ] !
[ ] &
[ ] |

### Questões Verdadeiro ou Falso

1. O bloco de código dentro de um `if` sempre será executado, independentemente da condição. (V/F)

2. É possível usar o `if` sem chaves `{}` se o bloco contiver apenas uma instrução. (V/F)

3. O operador `===` compara tanto o valor quanto o tipo dos operandos. (V/F)

### Questões de Associação

Associe os conceitos da coluna A com as descrições da coluna B:

| Coluna A             | Coluna B                                                     |
| -------------------- | ------------------------------------------------------------ |
| 1. if                | a) Usado quando há múltiplas condições a serem verificadas   |
| 2. else              | b) Executa um bloco de código se a condição for verdadeira   |
| 3. else if           | c) Uma forma abreviada de escrever uma estrutura if...else simples |
| 4. Operador ternário | d) Especifica um bloco de código a ser executado se a condição for falsa |

## Exercícios Práticos

### Nível Iniciante

1. Escreva um programa que verifica se um número é positivo, negativo ou zero.

2. Crie uma função que recebe a idade de uma pessoa e retorna se ela pode votar (idade >= 16) ou não.

3. Faça um programa que recebe três números e retorna o maior deles.

4. Escreva uma função que verifica se um ano é bissexto.

5. Crie um programa que classifica um triângulo como equilátero, isósceles ou escaleno com base no comprimento de seus lados.

### Nível Intermediário

1. Implemente uma calculadora simples que realiza operações básicas (+, -, *, /) entre dois números.

2. Escreva um programa que converte uma nota numérica para uma letra (A, B, C, D, F) seguindo uma escala predefinida.

3. Crie uma função que verifica se uma string é um palíndromo.

4. Implemente um validador de senhas que verifica se uma senha atende a critérios específicos.

5. Desenvolva um programa que determina o dia da semana com base em um número de 1 a 7.

## Conclusão

As estruturas de decisão "if" são fundamentais na programação JavaScript, permitindo que os desenvolvedores criem lógica condicional em seus programas. Dominar o uso do "if" e suas variações é essencial para escrever código eficiente e capaz de lidar com diferentes cenários.

Ao longo deste material, exploramos a sintaxe básica do "if", suas variações como "if...else" e "if...else if...else", o operador ternário, e discutimos sobre operadores de comparação e lógicos comumente usados em condições. Também abordamos boas práticas para escrever estruturas de decisão claras e eficientes.

Lembre-se de que a prática é fundamental para aperfeiçoar o uso dessas estruturas. Experimente criar diferentes cenários e condições para solidificar seu entendimento e desenvolver a habilidade de escolher a estrutura mais apropriada para cada situação.

## Referências e Dicas de Estudo

1. MDN Web Docs - if...else: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else
2. JavaScript.info - Conditional branching: if, '?': https://javascript.info/ifelse
3. W3Schools - JavaScript if, else, and else if: https://www.w3schools.com/js/js_if_else.asp

Dicas de estudo:
1. Pratique escrevendo diferentes tipos de condições e estruturas de decisão.
2. Experimente combinar múltiplas condições usando operadores lógicos.
3. Tente refatorar código existente para usar estruturas de decisão mais eficientes.
4. Crie pequenos projetos que envolvam tomada de decisões baseadas em entrada do usuário ou dados externos.
5. Revise e compare seu código com exemplos de boas práticas para melhorar continuamente sua escrita de código.

## Próxima Aula

Na próxima aula, exploraremos as estruturas de decisões avançadas em JavaScript com [`switch case`](dia-07-switch-case.md)
