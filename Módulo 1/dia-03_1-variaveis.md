# Dia 3: Variáveis

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Entender o conceito de variáveis em JavaScript
2. Declarar variáveis usando `var`, `let` e `const`

## 1. Variáveis em JavaScript: Conceitos Fundamentais

### 1.1 O que são variáveis?

Variáveis em JavaScript são contêineres para armazenar dados. Elas são usadas para guardar valores que podem ser alterados durante a execução do programa. Essencialmente, uma variável é um nome simbólico associado a um local de memória onde os dados são armazenados.

### 1.2 Importância das variáveis

As variáveis são fundamentais na programação porque:

- Permitem armazenar e manipular dados
- Facilitam a reutilização de valores
- Tornam o código mais legível e manutenível
- Possibilitam a criação de programas dinâmicos

### Exemplo

```javascript
// Declaração e atribuição de uma variável
let idade = 25;

// Uso da variável
console.log("A idade é: " + idade); // Saída: A idade é: 25

// Modificação do valor da variável
idade = 26;
console.log("A nova idade é: " + idade); // Saída: A nova idade é: 26
```

Neste exemplo, `idade` é uma variável que inicialmente armazena o valor 25. Posteriormente, seu valor é alterado para 26, demonstrando como as variáveis podem ser modificadas durante a execução do programa.

## 2. Declaração de Variáveis

Em JavaScript, existem três formas principais de declarar variáveis: `var`, `let` e `const`.

### 2.1 var

`var` era a forma original de declarar variáveis em JavaScript. Ela tem escopo de função ou global.

#### Exemplo:

```javascript
// Declaração com var
var nome = "Alice";
console.log(nome); // Saída: Alice

// var tem escopo de função
function exemploVar() {
    var x = 10;
    if (true) {
        var x = 20; // mesma variável
        console.log(x); // Saída: 20
    }
    console.log(x); // Saída: 20
}
exemploVar();
```

### 2.2 let

`let` foi introduzido no ES6 (ECMAScript 2015) e tem escopo de bloco.

#### Exemplo:

```javascript
// Declaração com let
let idade = 30;
console.log(idade); // Saída: 30

// let tem escopo de bloco
function exemploLet() {
    let y = 10;
    if (true) {
        let y = 20; // variável diferente
        console.log(y); // Saída: 20
    }
    console.log(y); // Saída: 10
}
exemploLet();
```

### 2.3 const

`const` também foi introduzido no ES6 e é usado para declarar constantes (valores que não serão reatribuídos).

#### Exemplo:

```javascript
// Declaração com const
const PI = 3.14159;
console.log(PI); // Saída: 3.14159

// Tentativa de reatribuição (gera erro)
// PI = 3.14; // Uncaught TypeError: Assignment to a constant variable

// const com objetos
const pessoa = { nome: "Carlos" };
pessoa.nome = "Ana"; // Válido, pois modifica a propriedade, não a referência
console.log(pessoa.nome); // Saída: Ana
```

## 3. Escopo de Variáveis

O escopo determina onde uma variável é acessível no código.

### 3.1 Escopo Global

Variáveis declaradas fora de qualquer função têm escopo global.

#### Exemplo:

```javascript
// Variável global
var globalVar = "Sou global";

function exemploGlobal() {
    console.log(globalVar); // Acessível aqui
}

exemploGlobal(); // Saída: Sou global
console.log(globalVar); // Também acessível aqui
```

### 3.2 Escopo Local (de Função)

Variáveis declaradas dentro de uma função são locais a essa função.

#### Exemplo:

```javascript
function exemploLocal() {
    var localVar = "Sou local";
    console.log(localVar); // Acessível aqui
}

exemploLocal(); // Saída: Sou local
// console.log(localVar); // Erro: localVar is not defined
```

### 3.3 Escopo de Bloco

Introduzido com `let` e `const`, limita a variável ao bloco onde foi declarada.

#### Exemplo:

```javascript
function exemploBloco() {
    if (true) {
        let blocoVar = "Variável de bloco";
        console.log(blocoVar); // Acessível aqui
    }
    // console.log(blocoVar); // Erro: blocoVar is not defined
}

exemploBloco();
```

## 4. Hoisting

Hoisting é um comportamento do JavaScript onde declarações de variáveis e funções são movidas para o topo de seu escopo antes da execução do código.

### Exemplo:

```javascript
console.log(x); // Saída: undefined
var x = 5;

// O código acima é interpretado como:
// var x;
// console.log(x);
// x = 5;

// Hoisting não funciona com let e const
// console.log(y); // Erro: Cannot access 'y' before initialization
let y = 10;
```

## 5. Boas Práticas na Utilização de Variáveis

1. Use nomes descritivos e significativos
2. Siga convenções de nomenclatura (camelCase para variáveis e funções)
3. Prefira `const` quando o valor não for reatribuído
4. Use `let` para variáveis que serão reatribuídas
5. Evite variáveis globais sempre que possível
6. Declare variáveis no topo do seu escopo
7. Inicialize variáveis na declaração, quando possível

### Exemplo:

```javascript
// Bom
const MAX_USERS = 100;
let currentUserCount = 0;

function addUser(userName) {
    if (currentUserCount < MAX_USERS) {
        // Lógica para adicionar usuário
        currentUserCount++;
    }
}

// Evite
var x = 5; // Nome não descritivo
```

## Exercícios Teóricos

### Questões Dissertativas

1. Explique a diferença entre `let`, `var` e `const` na declaração de variáveis em JavaScript.

2. O que é hoisting em JavaScript e como ele afeta as variáveis?

### Questões de Múltipla Escolha

Qual das seguintes opções NÃO é uma forma válida de declarar uma variável em JavaScript moderno?

1. [ ] `let x = 5;`
2. [ ] `var y = 10;`
3. [ ] `const z = 15;`
4. [ ] `int w = 20;`

Qual é o resultado do seguinte código?

```javascript
console.log(x);
var x = 5;
```

1. [ ] 5
2. [ ] undefined
3. [ ] Erro de referência
4. [ ] null

### Questões de Caixa de Múltiplas Escolhas

1. Quais das seguintes afirmações sobre `const` são verdadeiras? (Selecione todas as corretas)

   1. [ ] Variáveis declaradas com `const` não podem ter seu valor alterado
   2. [ ] `const` tem escopo de bloco
   3. [ ] Objetos declarados com `const` podem ter suas propriedades modificadas
   4. [ ] `const` pode ser redeclarado no mesmo escopo

### Questões Verdadeiro ou Falso

1. Verdadeiro ou Falso: Variáveis declaradas com `let` podem ser acessadas antes de sua declaração no código.

    1. [ ] Verdadeiro
    2. [ ] Falso

2. Verdadeiro ou Falso: Em JavaScript, é possível declarar múltiplas variáveis em uma única linha.

    1. [ ] Verdadeiro
    2. [ ] Falso

### Questões de Associação

Associe os conceitos da coluna A com suas descrições na coluna B:

| Coluna A | Coluna B |
|----------|----------|
| 1. var   | a) Tem escopo de bloco e não pode ser redeclarada |
| 2. let   | b) Usada para declarar constantes |
| 3. const | c) Tem escopo de função ou global |
| 4. Hoisting | d) Pode ser redeclarada no mesmo escopo |
| 5. Escopo | e) Movimentação de declarações para o topo |

## Exercícios Práticos

1. Declare uma variável chamada `nome` usando `let` e atribua seu nome a ela. Em seguida, imprima o valor no console.

2. Declare uma constante chamada `PI` e atribua o valor 3.14159 a ela. Tente reatribuir um novo valor a `PI` e observe o erro.

3. Crie uma variável `idade` usando `let` e atribua sua idade a ela. Em seguida, incremente esta variável em 1 e imprima o resultado.

4. Declare uma variável `temperatura` sem atribuir um valor inicial. Imprima seu valor no console.

5. Crie uma variável `frutas` como um array contendo três frutas. Use `const` para a declaração. Adicione uma nova fruta ao array e imprima o resultado.

6. Crie uma função que receba um parâmetro `nome` e declare uma variável local `saudacao` usando `let`. Retorne uma string combinando `saudacao` e `nome`.

7. Demonstre o comportamento de hoisting com uma variável declarada com `var`. Tente acessar a variável antes de sua declaração no código.

8. Crie um objeto `pessoa` usando `const` com propriedades `nome` e `idade`. Modifique a idade e adicione uma nova propriedade `cidade`. Imprima o objeto antes e depois das modificações.

9. Demonstre a diferença de escopo entre `var` e `let` dentro de um bloco `if`.

10. Crie uma função que demonstre o conceito de closure, usando uma variável declarada com `let`.

## Conclusão

Variáveis são fundamentais na programação JavaScript, permitindo o armazenamento e manipulação de dados. Compreender os diferentes tipos de declaração (`var`, `let`, `const`), escopos, e comportamentos como hoisting é crucial para escrever código JavaScript eficiente e livre de erros. A escolha adequada entre `let`, `const`, e ocasionalmente `var`, junto com boas práticas de nomeação e escopo, contribui significativamente para a clareza e manutenibilidade do código.

## Referências e Dicas de Estudo

1. Mozilla Developer Network (MDN) - JavaScript Guide: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
2. JavaScript.info - Variables: https://javascript.info/variables
3. "You Don't Know JS" series by Kyle Simpson
4. Eloquent JavaScript by Marijn Haverbeke: https://eloquentjavascript.net/
5. FreeCodeCamp JavaScript Algorithms and Data Structures: https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/

Dicas de Estudo:
- Pratique regularmente escrevendo código
- Experimente diferentes cenários no console do navegador
- Participe de desafios de codificação online
- Construa pequenos projetos para aplicar seus conhecimentos
- Junte-se a comunidades online de desenvolvedores JavaScript para discutir e aprender

## Próxima Aula

Na próxima aula, exploraremos os [`Tipos de Dados em JavaScript`](dia-03_2-tipos-dados.md), que nos permitirão realizar operações com nossas variáveis e valores.
