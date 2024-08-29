# Dia 3: Tipos de Dados

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Identificar e trabalhar com os tipos de dados primitivos em JavaScript
2. Realizar conversões básicas entre tipos de dados

## 1. Introdução aos Tipos de Dados Primitivos

Os tipos de dados primitivos em JavaScript são os blocos de construção fundamentais da linguagem. Eles representam os valores mais básicos e imutáveis que podem ser manipulados em um programa JavaScript.

### 1.1 Definição

Os tipos de dados primitivos são valores que não são objetos e não têm métodos. São imutáveis, o que significa que uma vez criados, seu valor não pode ser alterado.

### 1.2 Importância

Entender os tipos de dados primitivos é crucial para manipular informações corretamente em JavaScript, evitar erros de tipo e escrever código mais eficiente.

## 2. Os Seis Tipos de Dados Primitivos

JavaScript tem seis tipos de dados primitivos:

1. Number
2. String
3. Boolean
4. Undefined
5. Null
6. Symbol (adicionado no ECMAScript 2015)

Vamos explorar cada um deles em detalhes.

## 3. Number

### 3.1 Definição

O tipo `Number` representa tanto números inteiros quanto números de ponto flutuante.

### 3.2 Características

- Pode representar números positivos e negativos.
- Inclui o valor especial `Infinity` para representar infinito.
- Tem o valor `NaN` (Not a Number) para representar resultados inválidos de operações matemáticas.

### 3.3 Exemplo Comentado

```javascript
// Declaração de números inteiros
let idade = 25;
let anoNascimento = -1995;

// Declaração de números de ponto flutuante
let altura = 1.75;
let pi = 3.14159;

// Uso de notação científica
let grandeNumero = 1e6; // 1 milhão

// Valores especiais
let infinito = Infinity;
let naoNumero = NaN;

console.log(typeof idade); // Saída: "number"
console.log(typeof altura); // Saída: "number"
console.log(typeof infinito); // Saída: "number"
console.log(typeof naoNumero); // Saída: "number"
```

Neste exemplo, demonstramos várias formas de declarar e utilizar o tipo `Number`. Note que tanto números inteiros quanto de ponto flutuante são do mesmo tipo em JavaScript.

## 4. String

### 4.1 Definição

O tipo `String` representa texto e é usado para armazenar e manipular sequências de caracteres.

### 4.2 Características

- Pode ser definido usando aspas simples, duplas ou backticks (template literals).
- É imutável, o que significa que operações em strings sempre retornam novas strings.
- Possui propriedades e métodos úteis para manipulação de texto.

### 4.3 Exemplo Comentado

```javascript
// Declaração de strings com diferentes tipos de aspas
let nome = 'Alice';
let sobrenome = "Silva";
let frase = `Olá, mundo!`;

// Concatenação de strings
let nomeCompleto = nome + ' ' + sobrenome;

// Uso de template literals
let saudacao = `Bem-vindo, ${nomeCompleto}!`;

// Acesso a caracteres individuais (baseado em zero)
let primeiraLetra = nome[0]; // 'A'

// Propriedade length
console.log(nome.length); // Saída: 5

// Métodos de string
console.log(nome.toUpperCase()); // Saída: "ALICE"
console.log(frase.split(' ')); // Saída: ["Olá,", "mundo!"]

console.log(typeof nome); // Saída: "string"
```

Este exemplo mostra diferentes formas de criar strings, bem como algumas operações básicas que podem ser realizadas com elas.

## 5. Boolean

### 5.1 Definição

O tipo `Boolean` representa um valor lógico e pode ter apenas dois valores: `true` ou `false`.

### 5.2 Características

- Usado para operações lógicas e de controle de fluxo.
- Resultado de comparações e operações lógicas.

### 5.3 Exemplo Comentado

```javascript
// Declaração de booleanos
let estaChovendo = true;
let estaSol = false;

// Resultado de comparações
let maiorDeIdade = 18 <= 20; // true

// Operações lógicas
let precisoGuardaChuva = estaChovendo && !estaSol;

// Uso em estruturas de controle
if (estaChovendo) {
    console.log("Leve um guarda-chuva!");
} else {
    console.log("Bom tempo!");
}

// Conversão para boolean
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean("texto")); // true

console.log(typeof estaChovendo); // Saída: "boolean"
```

Este exemplo demonstra como declarar e usar booleanos, bem como alguns contextos em que eles são comumente utilizados.

## 6. Undefined

### 6.1 Definição

`Undefined` é um tipo que tem apenas um valor: `undefined`. Representa uma variável que foi declarada, mas não foi atribuída a um valor.

### 6.2 Características

- Valor padrão para variáveis não inicializadas.
- Retorno de funções que não retornam explicitamente um valor.

### 6.3 Exemplo Comentado

```javascript
// Variável declarada mas não inicializada
let variavelNaoInicializada;
console.log(variavelNaoInicializada); // Saída: undefined

// Função sem retorno explícito
function semRetorno() {
    let a = 1 + 1;
}
console.log(semRetorno()); // Saída: undefined

// Acesso a propriedade inexistente de um objeto
let obj = {};
console.log(obj.propriedadeInexistente); // Saída: undefined

// Verificando se uma variável é undefined
if (typeof variavelNaoInicializada === 'undefined') {
    console.log("A variável não foi inicializada");
}

console.log(typeof undefined); // Saída: "undefined"
```

Este exemplo ilustra diferentes situações em que o valor `undefined` aparece em JavaScript.

## 7. Null

### 7.1 Definição

`Null` é um tipo que tem apenas um valor: `null`. Representa a ausência intencional de qualquer valor de objeto.

### 7.2 Características

- Usado para indicar "nenhum valor" ou "valor vazio".
- Diferente de `undefined`, `null` é geralmente atribuído explicitamente.

### 7.3 Exemplo Comentado

```javascript
// Atribuição explícita de null
let valorVazio = null;

// Uso comum em funções que podem retornar um objeto ou null
function buscarUsuario(id) {
    // Simula uma busca no banco de dados
    if (id === 1) {
        return { nome: "Alice", idade: 30 };
    } else {
        return null; // Usuário não encontrado
    }
}

let usuario = buscarUsuario(2);
console.log(usuario); // Saída: null

// Verificando se um valor é null
if (usuario === null) {
    console.log("Usuário não encontrado");
}

console.log(typeof null); // Saída: "object" (isso é considerado um bug em JavaScript)
```

Este exemplo mostra como `null` é usado para representar a ausência intencional de um valor.

## 8. Symbol

### 8.1 Definição

`Symbol` é um tipo de dado primitivo introduzido no ECMAScript 2015 (ES6). Representa um identificador único e imutável.

### 8.2 Características

- Cada símbolo criado é único.
- Usado principalmente como chaves de propriedades de objetos.
- Não é automaticamente convertido para string.

### 8.3 Exemplo Comentado

```javascript
// Criando símbolos
let sym1 = Symbol();
let sym2 = Symbol("descricao");
let sym3 = Symbol("descricao");

console.log(sym2 === sym3); // Saída: false (símbolos são sempre únicos)

// Uso como chave de propriedade de objeto
let obj = {};
obj[sym1] = "Valor associado ao sym1";

console.log(obj[sym1]); // Saída: "Valor associado ao sym1"

// Símbolos não são enumeráveis em loops for...in
for (let key in obj) {
    console.log(key); // Não imprime nada
}

// Obter símbolos de um objeto
console.log(Object.getOwnPropertySymbols(obj)); // Saída: [Symbol()]

console.log(typeof sym1); // Saída: "symbol"
```

Este exemplo demonstra a criação e uso de símbolos, destacando sua unicidade e aplicação como chaves de propriedades de objetos.

## Exercícios Teóricos

### Questões Dissertativas

1. Explique a diferença entre tipos de dados primitivos e tipos de dados de referência em JavaScript.

2. Por que é importante entender os tipos de dados primitivos em JavaScript? Dê exemplos de situações onde esse conhecimento é crucial.

### Questões de Múltipla Escolha

1. Qual dos seguintes NÃO é um tipo de dado primitivo em JavaScript?
   1. [ ] Number
   2. [ ] String
   3. [ ] Boolean
   4. [ ]  Array
   5. [ ] Symbol

2. Qual é o resultado da expressão `typeof null` em JavaScript?
   1. [ ] "null"
   2. [ ] "undefined"
   3. [ ] "object"
   4. [ ] "number"
   5. [ ] "boolean"

### Questões de Caixa de Múltiplas Escolhas

1. Quais dos seguintes são considerados valores "falsy" em JavaScript? (Selecione todas as opções corretas)
   1. [ ] 0
   2. [ ] ""
   3. [ ] null
   4. [ ] undefined
   5. [ ] false
   6. [ ] NaN

2. Quais dos seguintes métodos podem ser usados para converter outros tipos em String? (Selecione todas as opções corretas)
   1. [ ] toString()
   2. [ ] String()
   3. [ ] toFixed()
   4. [ ] concat()
   5. [ ] valueOf()

### Questões Verdadeiro ou Falso

1. [ ] Em JavaScript, o tipo Number pode representar tanto números inteiros quanto números de ponto flutuante.

2. [ ] O valor `undefined` é atribuído automaticamente a variáveis que são declaradas mas não inicializadas.

3. [ ] Símbolos em JavaScript são automaticamente convertidos para strings quando usados em operações de concatenação.

4. [ ] O tipo Boolean em JavaScript só pode ter os valores `true` ou `false`.

5. [ ] O operador `typeof` sempre retorna uma string representando o tipo do operando.

### Questões de Associação

Associe os tipos de dados primitivos com suas características:

| Tipo de Dado | Característica                                      |
|--------------|-----------------------------------------------------|
| 1. Number    | A. Representa valores lógicos                       |
| 2. String    | B. Representa a ausência intencional de valor       |
| 3. Boolean   | C. Representa texto                                 |
| 4. Undefined | D. Representa identificadores únicos                |
| 5. Null      | E. Representa números inteiros e de ponto flutuante |
| 6. Symbol    | F. Representa uma variável declarada sem valor      |

## Exercícios Práticos

### Nível Iniciante

1. Crie uma variável para cada tipo de dado primitivo em JavaScript e imprima seu tipo usando o operador `typeof`.

2. Escreva uma função que receba dois números como parâmetros e retorne `true` se o primeiro número for maior que o segundo, e `false` caso contrário.

3. Declare uma variável sem atribuir um valor a ela. Em seguida, verifique se ela é do tipo `undefined` usando uma estrutura condicional.

4. Crie uma string contendo seu nome completo e use métodos de string para:
   a) Imprimir o nome em maiúsculas
   b) Contar o número de caracteres
   c) Extrair o primeiro nome

5. Declare uma variável com o valor `null` e outra com o valor `undefined`. Compare-as usando os operadores `==` e `===`. Explique o resultado.

### Nível Intermediário

1. Crie uma função que aceite um número como entrada e retorne `true` se for um número primo, e `false` caso contrário.

2. Implemente uma função que receba uma string e retorne um objeto contendo a contagem de cada caractere na string.

3. Escreva uma função que aceite um array de números e retorne o segundo maior número do array.

4. Crie uma função que gere um número aleatório entre 1 e 100, e então peça ao usuário para adivinhar o número. A função deve dar dicas se o palpite é muito alto ou muito baixo, até que o usuário acerte.

5. Implemente uma função que receba um objeto e um símbolo como parâmetros. A função deve adicionar uma nova propriedade ao objeto usando o símbolo como chave e retornar o objeto modificado.

## Conclusão

Compreender os tipos de dados primitivos em JavaScript é fundamental para qualquer desenvolvedor que trabalhe com a linguagem. Esses tipos formam a base sobre a qual construímos estruturas de dados mais complexas e implementamos lógica em nossos programas.

Cada tipo primitivo tem suas próprias características e usos específicos:

- `Number` nos permite trabalhar com valores numéricos e realizar operações matemáticas.
- `String` é essencial para manipulação de texto e dados baseados em caracteres.
- `Boolean` é crucial para lógica condicional e tomada de decisões em nossos programas.
- `Undefined` e `Null` nos ajudam a lidar com a ausência de valores, cada um com seu próprio significado semântico.
- `Symbol` fornece uma maneira de criar identificadores únicos, úteis em certos padrões de design e para evitar colisões de nomes de propriedades.

Ao dominar esses tipos primitivos, você estará melhor equipado para escrever código JavaScript mais eficiente, legível e livre de erros. Além disso, esse conhecimento serve como base para entender conceitos mais avançados da linguagem, como coerção de tipos, operações de comparação e manipulação de objetos.

Continue praticando e explorando cada tipo em diferentes contextos para solidificar seu entendimento. Lembre-se de que a prática constante e a aplicação desses conceitos em projetos reais são as melhores maneiras de aprimorar suas habilidades em JavaScript.

## Referências e Dicas de Estudo

1. [MDN Web Docs - JavaScript Data Types and Data Structures:](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

2. [JavaScript.info - Data Types:](https://javascript.info/types)

## Próxima Aula

Na próxima aula, exploraremos os [`Operadores Aritméticos`](dia-04-operadores-aritmeticos.md) em JavaScript, que nos permitirão realizar operações com nossas variáveis e valores.
