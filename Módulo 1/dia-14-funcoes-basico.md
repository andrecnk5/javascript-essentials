# Dia 14: Funções - Básico

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
function nomeFuncao(parametro) {
    return console.log(parametro);
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

Funções anônimas são funções que são definidas sem um nome associado a elas. Elas são frequentemente usadas como argumentos para outras funções ou atribuídas a variáveis. As funções anônimas são particularmente úteis em situações onde você precisa de uma função temporária ou de uso único.

Características principais das funções anônimas:

1. Não possuem um nome identificador.
2. Podem ser atribuídas a variáveis ou passadas como argumentos para outras funções.
3. São frequentemente usadas como callbacks ou em closures.
4. Podem ser executadas imediatamente após serem definidas (IIFE - Immediately Invoked Function Expression).
5. São flexíveis e podem ajudar a manter o escopo limpo.

Sintaxe básica:

```javascript
function() {
    // corpo da função
}
```

Agora, vamos analisar o exemplo a:

```javascript
setTimeout(function() {
    console.log("Isso será executado após 2 segundos");
}, 2000);
```

Detalhamento:

1. `setTimeout`: Esta é uma função built-in do JavaScript que agenda a execução de um código para ocorrer após um determinado período de tempo.

2. `function() { ... }`: Esta é a função anônima. Ela não tem nome e é passada diretamente como o primeiro argumento para `setTimeout`. Esta função será executada quando o tempo especificado tiver decorrido.

3. `console.log("Isso será executado após 2 segundos")`: Este é o corpo da função anônima. Quando a função for executada, ela imprimirá esta mensagem no console.

4. `2000`: Este é o segundo argumento passado para `setTimeout`. Representa o tempo de espera em milissegundos (neste caso, 2 segundos) antes que a função anônima seja executada.

O que este código faz:

1. A função `setTimeout` é chamada com dois argumentos: uma função anônima e um valor numérico (2000).
2. O JavaScript agenda a execução da função anônima para ocorrer após 2000 milissegundos (2 segundos).
3. Após 2 segundos, a função anônima é executada, imprimindo a mensagem no console.

A utilização de uma função anônima neste contexto é muito comum e adequada, pois:

- A função só precisa ser executada uma vez, após o tempo especificado.
- Não há necessidade de reutilizar esta função em outras partes do código.
- Mantém o código mais limpo e encapsulado, evitando a criação de uma função nomeada que só seria usada neste local.

Este padrão é frequentemente usado em programação assíncrona, manipulação de eventos e callbacks, onde você precisa definir um comportamento que será executado em resposta a algum evento ou após um certo período.

Se você quisesse reescrever isso usando uma arrow function (que também é uma forma de função anônima), ficaria assim:

```javascript
setTimeout(() => {
    console.log("Isso será executado após 2 segundos");
}, 2000);
```

Isso demonstra como as funções anônimas podem ser flexíveis e úteis em diferentes contextos de programação JavaScript.

## 7. Arrow Functions

Uma sintaxe mais concisa para escrever funções, introduzida no ES6:

Arrow functions, também conhecidas como funções de seta, são uma forma concisa de escrever funções em JavaScript, introduzidas no ECMAScript 6 (ES6). Elas oferecem uma sintaxe mais curta em comparação com as funções tradicionais e têm algumas diferenças semânticas importantes.

Características principais:

1. Sintaxe concisa: Utilizam a notação `=>`, que se assemelha a uma seta.
2. Return implícito: Para funções de uma única expressão, o `return` é implícito.
3. Escopo léxico do `this`: O `this` é herdado do contexto circundante.
4. Não possuem seus próprios objetos `arguments`.
5. Não podem ser usadas como construtores.

Sintaxe básica:

```javascript
(parâmetros) => { corpo da função }
```

Agora, vamos analisar o exemplo abaixo:

```javascript
const quadrado = (numero) => numero * numero;

console.log(quadrado(4)); // Saída: 16
```

1. `const quadrado =`: Declaramos uma constante chamada `quadrado`. Isso significa que não podemos reatribuir um novo valor a `quadrado` posteriormente.

2. `(numero) =>`: Esta é a parte da arrow function. O parâmetro `numero` está entre parênteses. Se tivéssemos apenas um parâmetro, poderíamos omitir os parênteses, mas é uma boa prática mantê-los para maior clareza.

3. `numero * numero`: Esta é a expressão que a função retorna. Como é uma função de uma única expressão, o `return` é implícito. A função multiplica o número por ele mesmo, calculando assim o seu quadrado.

4. `console.log(quadrado(4));`: Aqui, estamos chamando a função `quadrado` com o argumento 4 e imprimindo o resultado no console.

5. `// Saída: 16`: Este é o resultado esperado, já que 4 ao quadrado é 16.

Esta arrow function é um exemplo perfeito de como podemos usar essa sintaxe para criar funções simples e concisas. Em uma única linha, definimos uma função que calcula o quadrado de um número.

Se quiséssemos escrever a mesma função usando a sintaxe tradicional, seria algo assim:

```javascript
function quadrado(numero) {
    return numero * numero;
}
```

Como você pode ver, a arrow function nos permite escrever o mesmo código de forma mais compacta.

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
