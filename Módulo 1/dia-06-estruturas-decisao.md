# Dia 6: Estruturas de Decisão (if, else)

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de estruturas de decisão em programação
2. Utilizar a estrutura if para executar código condicionalmente
3. Implementar estruturas if...else para lidar com múltiplos cenários
4. Criar estruturas de decisão aninhadas e if...else if para situações mais complexas
5. Utilizar o operador ternário para decisões simples e concisas

## 1. Introdução às Estruturas de Decisão

As estruturas de decisão permitem que um programa execute diferentes blocos de código baseados em condições específicas. Elas são fundamentais para criar programas que podem responder a diferentes situações.

## 2. A Estrutura if

A estrutura `if` é a mais básica das estruturas de decisão. Ela executa um bloco de código apenas se uma condição for verdadeira.

Sintaxe:
```javascript
if (condição) {
    // código a ser executado se a condição for verdadeira
}
```

Exemplo:
```javascript
let idade = 18;

if (idade >= 18) {
    console.log("Você é maior de idade.");
}
```

## 3. A Estrutura if...else

A estrutura `if...else` permite especificar um bloco de código a ser executado quando a condição é falsa.

Sintaxe:
```javascript
if (condição) {
    // código a ser executado se a condição for verdadeira
} else {
    // código a ser executado se a condição for falsa
}
```

Exemplo:
```javascript
let temperatura = 30;

if (temperatura > 30) {
    console.log("Está quente hoje!");
} else {
    console.log("A temperatura está agradável.");
}
```

## 4. Estruturas if...else if...else

Para lidar com múltiplas condições, podemos usar a estrutura `if...else if...else`.

Sintaxe:
```javascript
if (condição1) {
    // código a ser executado se condição1 for verdadeira
} else if (condição2) {
    // código a ser executado se condição2 for verdadeira
} else {
    // código a ser executado se nenhuma das condições anteriores for verdadeira
}
```

Exemplo:
```javascript
let nota = 75;

if (nota >= 90) {
    console.log("Excelente!");
} else if (nota >= 70) {
    console.log("Bom trabalho!");
} else if (nota >= 50) {
    console.log("Você passou, mas pode melhorar.");
} else {
    console.log("Você precisa estudar mais.");
}
```

## 5. Estruturas de Decisão Aninhadas

Podemos ter estruturas de decisão dentro de outras estruturas de decisão. Isso é chamado de aninhamento.

Exemplo:
```javascript
let idade = 18;
let temCarteira = true;

if (idade >= 18) {
    if (temCarteira) {
        console.log("Você pode dirigir.");
    } else {
        console.log("Você precisa tirar a carteira de motorista.");
    }
} else {
    console.log("Você é muito jovem para dirigir.");
}
```

## 6. Operador Ternário

O operador ternário é uma forma concisa de escrever uma estrutura if...else simples.

Sintaxe:
```javascript
condição ? expressão1 : expressão2
```

Exemplo:
```javascript
let idade = 20;
let status = idade >= 18 ? "adulto" : "menor";
console.log(status);  // Saída: "adulto"
```

## Exercício Prático

Crie um programa que determine o preço de um ingresso baseado na idade do cliente:
- Crianças (0-12 anos): R$ 10
- Adolescentes (13-17 anos): R$ 15
- Adultos (18-59 anos): R$ 20
- Idosos (60+ anos): R$ 12

Use estruturas if...else if para implementar esta lógica.

Exemplo de solução:

```javascript
let idade = 25;
let preço;

if (idade <= 12) {
    preço = 10;
} else if (idade <= 17) {
    preço = 15;
} else if (idade <= 59) {
    preço = 20;
} else {
    preço = 12;
}

console.log(`O preço do ingresso é R$ ${preço}.`);
```

## Dicas Úteis

1. Sempre use chaves `{}` em suas estruturas de decisão, mesmo que o bloco tenha apenas uma linha. Isso torna o código mais legível e evita erros.
2. Evite aninhar muitas estruturas de decisão. Se você tem muitos níveis de aninhamento, considere refatorar seu código.
3. Use o operador ternário para decisões simples, mas evite-o para lógica complexa.

## Recursos Adicionais

- [Estruturas condicionais (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Building_blocks/conditionals)
- [Tomando decisões no seu código — condicionais (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Building_blocks/conditionals)
- [JavaScript if, else e else if (W3Schools em português)](https://www.w3schools.com/js/js_if_else.asp)

## Próxima Aula

Na próxima aula, exploraremos as estruturas de decisões avançadas em JavaScript com `switch case`
