# Dia 12: Funções - Básico

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de funções em JavaScript
2. Criar e declarar funções
3. Chamar funções e passar argumentos
4. Trabalhar com retorno de funções
5. Compreender o escopo de variáveis em funções
6. Utilizar funções anônimas e arrow functions

## 1. O que são Funções?

Funções são blocos de código reutilizáveis que realizam uma tarefa específica. Elas ajudam a organizar o código, evitar repetições e tornar o programa mais modular.

## 2. Declarando Funções

Existem várias formas de declarar funções em JavaScript:

### Declaração de Função

```javascript
function saudacao(nome) {
    console.log(`Olá, ${nome}!`);
}
```

### Expressão de Função

```javascript
const saudacao = function(nome) {
    console.log(`Olá, ${nome}!`);
};
```

## 3. Chamando Funções e Passando Argumentos

Para executar uma função, você a chama pelo nome seguido de parênteses, passando os argumentos necessários:

```javascript
saudacao("Maria"); // Saída: Olá, Maria!
```

## 4. Retorno de Funções

Funções podem retornar valores usando a palavra-chave `return`:

```javascript
function soma(a, b) {
    return a + b;
}

let resultado = soma(5, 3);
console.log(resultado); // Saída: 8
```

## 5. Escopo de Variáveis em Funções

Variáveis declaradas dentro de uma função são locais a essa função:

```javascript
function exemploEscopo() {
    let variavelLocal = "Eu sou local";
    console.log(variavelLocal); // Funciona
}

exemploEscopo();
// console.log(variavelLocal); // Erro: variavelLocal is not defined
```

## 6. Funções Anônimas

Funções sem nome, geralmente usadas como argumentos para outras funções:

```javascript
setTimeout(function() {
    console.log("Isso será executado após 2 segundos");
}, 2000);
```

## 7. Arrow Functions

Uma sintaxe mais concisa para escrever funções, introduzida no ES6:

```javascript
const quadrado = (numero) => numero * numero;

console.log(quadrado(4)); // Saída: 16
```

## 8. Parâmetros Padrão

Você pode definir valores padrão para parâmetros de função:

```javascript
function saudacao(nome = "Visitante") {
    console.log(`Olá, ${nome}!`);
}

saudacao(); // Saída: Olá, Visitante!
saudacao("João"); // Saída: Olá, João!
```

## Exercício Prático

Crie um programa de calculadora simples:
1. Crie funções separadas para adição, subtração, multiplicação e divisão.
2. Cada função deve aceitar dois parâmetros e retornar o resultado.
3. Crie uma função principal `calculadora` que aceita três parâmetros: dois números e uma operação (string).
4. A função `calculadora` deve chamar a função apropriada com base na operação e retornar o resultado.
5. Teste a calculadora com diferentes operações.

Exemplo de solução:

```javascript
function adicao(a, b) {
    return a + b;
}

function subtracao(a, b) {
    return a - b;
}

function multiplicacao(a, b) {
    return a * b;
}

function divisao(a, b) {
    if (b === 0) {
        return "Erro: Divisão por zero!";
    }
    return a / b;
}

function calculadora(num1, num2, operacao) {
    switch (operacao) {
        case "+":
            return adicao(num1, num2);
        case "-":
            return subtracao(num1, num2);
        case "*":
            return multiplicacao(num1, num2);
        case "/":
            return divisao(num1, num2);
        default:
            return "Operação inválida";
    }
}

console.log(calculadora(5, 3, "+")); // Saída: 8
console.log(calculadora(10, 4, "-")); // Saída: 6
console.log(calculadora(3, 7, "*")); // Saída: 21
console.log(calculadora(15, 3, "/")); // Saída: 5
console.log(calculadora(10, 0, "/")); // Saída: Erro: Divisão por zero!
```

## Dicas Úteis

1. Mantenha suas funções pequenas e focadas em uma única tarefa.
2. Use nomes descritivos para suas funções e parâmetros.
3. Prefira arrow functions para funções curtas e simples.
4. Lembre-se de que funções podem ser passadas como argumentos para outras funções (funções de ordem superior).
5. Evite efeitos colaterais em funções puras sempre que possível.

## Recursos Adicionais

- [Funções (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions)
- [JavaScript Funções (W3Schools em português)](https://www.w3schools.com/js/js_functions.asp)
- [Entendendo Funções em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-funcoes/37630)

## Próxima Aula

Na próxima aula, aprofundaremos nosso conhecimento sobre funções, explorando conceitos mais avançados como closures, funções de ordem superior e métodos de array que utilizam funções.

