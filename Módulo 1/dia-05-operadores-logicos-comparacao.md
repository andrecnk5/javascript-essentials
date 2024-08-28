# Dia 5: Operadores Lógicos e de Comparação

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Utilizar operadores de comparação para avaliar e comparar valores
2. Compreender e aplicar operadores lógicos para combinar condições
3. Entender a precedência entre operadores lógicos e de comparação
4. Aplicar estes operadores em estruturas condicionais simples

# Operadores de Comparação em JavaScript

## 1. Introdução aos Operadores de Comparação

Os operadores de comparação em JavaScript são utilizados para comparar valores e retornar um resultado booleano (verdadeiro ou falso). Esses operadores são fundamentais para a lógica de programação, permitindo que você tome decisões em seu código com base em comparações entre valores.

### Exemplo:
```javascript
// Comparando dois números
let x = 5;
let y = 10;
console.log(x < y); // Saída: true

// Comparando duas strings
let nome1 = "Alice";
let nome2 = "Bob";
console.log(nome1 === nome2); // Saída: false
```

## 2. Tipos de Operadores de Comparação

### 2.1 Operador de Igualdade (==)

O operador de igualdade compara dois valores, realizando coerção de tipo se necessário.

#### Exemplo:
```javascript
console.log(5 == "5"); // Saída: true
// O operador == converte a string "5" em um número antes da comparação
```

### 2.2 Operador de Igualdade Estrita (===)

O operador de igualdade estrita compara dois valores sem realizar coerção de tipo.

#### Exemplo:
```javascript
console.log(5 === "5"); // Saída: false
// O operador === não realiza coerção de tipo, então um número e uma string são considerados diferentes
```

### 2.3 Operador de Desigualdade (!=)

O operador de desigualdade compara dois valores, retornando true se forem diferentes após a coerção de tipo.

#### Exemplo:
```javascript
console.log(5 != "6"); // Saída: true
console.log(5 != "5"); // Saída: false
```

### 2.4 Operador de Desigualdade Estrita (!==)

O operador de desigualdade estrita compara dois valores, retornando true se forem diferentes em valor ou tipo.

#### Exemplo:
```javascript
console.log(5 !== "5"); // Saída: true
console.log(5 !== 5); // Saída: false
```

### 2.5 Operador Maior Que (>)

O operador maior que retorna true se o valor à esquerda for maior que o valor à direita.

#### Exemplo:
```javascript
console.log(10 > 5); // Saída: true
console.log(5 > 10); // Saída: false
```

### 2.6 Operador Menor Que (<)

O operador menor que retorna true se o valor à esquerda for menor que o valor à direita.

#### Exemplo:
```javascript
console.log(5 < 10); // Saída: true
console.log(10 < 5); // Saída: false
```

### 2.7 Operador Maior ou Igual a (>=)

O operador maior ou igual a retorna true se o valor à esquerda for maior ou igual ao valor à direita.

#### Exemplo:
```javascript
console.log(10 >= 10); // Saída: true
console.log(11 >= 10); // Saída: true
console.log(9 >= 10); // Saída: false
```

### 2.8 Operador Menor ou Igual a (<=)

O operador menor ou igual a retorna true se o valor à esquerda for menor ou igual ao valor à direita.

#### Exemplo:
```javascript
console.log(10 <= 10); // Saída: true
console.log(9 <= 10); // Saída: true
console.log(11 <= 10); // Saída: false
```

## 3. Exercícios Teóricos

### 3.1 Questão Dissertativa

Explique a diferença entre os operadores de igualdade (==) e igualdade estrita (===) em JavaScript. Forneça exemplos para ilustrar sua resposta.

**Resposta:**
O operador de igualdade (==) realiza coerção de tipo antes de fazer a comparação, enquanto o operador de igualdade estrita (===) compara os valores sem realizar coerção de tipo. 

Exemplo:
```javascript
console.log(5 == "5");  // true (coerção de tipo)
console.log(5 === "5"); // false (tipos diferentes)
```

No primeiro caso, o operador == converte a string "5" em um número antes da comparação, resultando em true. No segundo caso, === compara tanto o valor quanto o tipo, resultando em false porque um é número e o outro é string.

### 3.2 Questão de Múltipla Escolha

Qual é o resultado da expressão `10 > "5"` em JavaScript?

a) true
b) false
c) undefined
d) Error

**Resposta correta: a) true**

Justificativa: JavaScript realiza coerção de tipo quando necessário em comparações. Neste caso, a string "5" é convertida para o número 5 antes da comparação. Como 10 é maior que 5, a expressão retorna true.

### 3.3 Questão de Caixa de Múltiplas Escolhas

Quais das seguintes expressões retornam `true` em JavaScript? (Selecione todas as opções corretas)

[ ] 5 === "5"
[x] 5 == "5"
[x] 10 >= 10
[x] "a" < "b"
[ ] null == undefined
[x] null === null

**Respostas corretas: b, c, d, f**

Justificativa:
- `5 === "5"` é falso porque compara tipos diferentes sem coerção.
- `5 == "5"` é verdadeiro devido à coerção de tipo.
- `10 >= 10` é verdadeiro porque 10 é igual a 10.
- `"a" < "b"` é verdadeiro porque na ordem lexicográfica, "a" vem antes de "b".
- `null == undefined` é verdadeiro em JavaScript (coerção de tipo).
- `null === null` é verdadeiro porque null é igual a si mesmo.

### 3.4 Questão Verdadeiro ou Falso

Determine se as seguintes afirmações são verdadeiras ou falsas:

1. O operador `>` pode ser usado para comparar strings. [V]
2. `NaN === NaN` retorna true. [F]
3. O operador `<=` retorna true se o valor à esquerda for menor ou igual ao valor à direita. [V]
4. `"10" === 10` retorna true. [F]

**Respostas:**
1. Verdadeiro. Strings são comparadas lexicograficamente.
2. Falso. NaN não é igual a nada, nem mesmo a si mesmo.
3. Verdadeiro. Esta é a definição correta do operador `<=`.
4. Falso. O operador `===` compara valor e tipo, e uma string não é igual a um número.

### 3.5 Questão de Associação

Associe os operadores de comparação com suas descrições:

| Operador | Descrição |
|----------|-----------|
| 1. ==    | A. Igualdade estrita |
| 2. ===   | B. Maior que |
| 3. !=    | C. Menor ou igual a |
| 4. >     | D. Igualdade (com coerção) |
| 5. <=    | E. Desigualdade (com coerção) |

**Respostas:**
1-D, 2-A, 3-E, 4-B, 5-C

Justificativa:
- `==` realiza comparação de igualdade com coerção de tipo.
- `===` realiza comparação de igualdade estrita, sem coerção.
- `!=` verifica desigualdade com coerção de tipo.
- `>` verifica se o valor à esquerda é maior que o valor à direita.
- `<=` verifica se o valor à esquerda é menor ou igual ao valor à direita.

## 5. Conclusão

Os operadores de comparação são fundamentais na programação JavaScript, permitindo a criação de lógica condicional e tomada de decisões em seu código. Eles são essenciais para controle de fluxo, validações e implementação de regras de negócio. É crucial entender as nuances entre os diferentes operadores, especialmente a diferença entre igualdade (==) e igualdade estrita (===), para evitar bugs sutis em seu código. Praticar o uso desses operadores em diferentes contextos ajudará a solidificar seu entendimento e melhorar suas habilidades de programação.

## 6. Referências e Dicas de Estudo

1. Mozilla Developer Network (MDN) - JavaScript Comparison Operators:
   https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators

2. JavaScript.info - Comparisons:
   https://javascript.info/comparison

3. W3Schools - JavaScript Comparison and Logical Operators:
   https://www.w3schools.com/js/js_comparisons.asp

4. Eloquent JavaScript by Marijn Haverbeke - Chapter 1: Values, Types, and Operators:
   https://eloquentjavascript.net/01_values.html

Dicas de Estudo:
1. Pratique regularmente usando o console do navegador ou um ambiente Node.js.
2. Crie pequenos programas que utilizam diferentes operadores de comparação.
3. Experimente com diferentes tipos de dados (números, strings, booleanos, null, undefined) para entender como os operadores se comportam.
4. Estude os conceitos de coerção de tipo em JavaScript para compreender melhor o comportamento dos operadores == e !=.
5. Resolva exercícios e desafios de codificação que envolvam operadores de comparação.
6. Participe de comunidades online de desenvolvedores JavaScript para discutir e aprender com outros programadores.


## Próxima Aula

Na próxima aula, mergulharemos nas estruturas de controle em JavaScript, começando com [estruturas de decisões](dia-06-estruturas-decisao.md) como `if`, `else if`, e `else`.

