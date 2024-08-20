# Dia 3: Variáveis e Tipos de Dados

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de variáveis em JavaScript
2. Declarar variáveis usando `var`, `let` e `const`
3. Identificar e trabalhar com os tipos de dados primitivos em JavaScript
4. Realizar conversões básicas entre tipos de dados

## 1. Variáveis em JavaScript

Variáveis são "contêineres" para armazenar dados em seu programa. Elas são fundamentais em qualquer linguagem de programação.

### Declaração de Variáveis

Em JavaScript, temos três formas de declarar variáveis:

1. `var` (forma antiga, menos usada atualmente)
2. `let` (para variáveis que podem mudar de valor)
3. `const` (para variáveis que não mudam de valor)

Exemplo:

```javascript
var idade = 25;  // Forma antiga
let nome = "Maria";  // Variável que pode mudar
const PI = 3.14159;  // Constante, não pode ser reatribuída
```

### Regras para Nomes de Variáveis

- Devem começar com uma letra, $ ou _
- Não podem começar com números
- São case-sensitive (nome ≠ Nome)
- Não podem ser palavras reservadas (como `let`, `const`, `if`, etc.)

Exemplo de nomes válidos:
```javascript
let nomeCompleto = "João Silva";
let $preco = 19.99;
let _contador = 0;
```

## 2. Tipos de Dados Primitivos

JavaScript tem seis tipos de dados primitivos:

1. **Number**: Representa números (inteiros ou decimais)
2. **String**: Representa texto
3. **Boolean**: Representa verdadeiro (`true`) ou falso (`false`)
4. **Undefined**: Representa uma variável que foi declarada mas não inicializada
5. **Null**: Representa a ausência intencional de qualquer valor
6. **Symbol**: Representa um identificador único (menos comum, introduzido no ES6)

### Exemplos:

```javascript
let idade = 30;                 // Number
let nome = "Carlos";            // String
let eMaiorDeIdade = true;       // Boolean
let endereco;                   // Undefined
let saldoBancario = null;       // Null
let id = Symbol("id");          // Symbol
```

## 3. Trabalhando com Tipos de Dados

### Verificando o Tipo

Podemos usar o operador `typeof` para verificar o tipo de uma variável:

```javascript
console.log(typeof idade);       // "number"
console.log(typeof nome);        // "string"
console.log(typeof eMaiorDeIdade); // "boolean"
console.log(typeof endereco);    // "undefined"
console.log(typeof saldoBancario); // "object" (isso é um bug histórico do JavaScript)
console.log(typeof id);          // "symbol"
```

### Conversão de Tipos

Às vezes, precisamos converter entre diferentes tipos de dados:

```javascript
let numero = "123";
let numeroConvertido = Number(numero);  // Converte string para número
console.log(numeroConvertido + 7);  // 130

let booleano = 1;
let booleanoConvertido = Boolean(booleano);  // Converte para boolean
console.log(booleanoConvertido);  // true

let texto = 456;
let textoConvertido = String(texto);  // Converte para string
console.log(textoConvertido + " é um texto agora");  // "456 é um texto agora"
```

## Exercício Prático

Crie um script que:
1. Declare variáveis para armazenar seu nome, idade e se você é estudante (use os tipos apropriados)
2. Imprima essas informações no console
3. Tente mudar o valor da sua idade e imprima novamente

Exemplo de solução:

```javascript
let nome = "Ana";
let idade = 22;
const eEstudante = true;

console.log(`Nome: ${nome}, Idade: ${idade}, É estudante? ${eEstudante}`);

idade = 23;  // A idade pode mudar, pois usamos 'let'
console.log(`Nome: ${nome}, Nova idade: ${idade}, É estudante? ${eEstudante}`);

// Isso causaria um erro, pois 'eEstudante' é uma constante:
// eEstudante = false;
```

## Dicas Úteis

1. Use `const` sempre que possível, e `let` quando precisar reatribuir valores.
2. Evite usar `var`, pois ele tem um comportamento de escopo que pode causar confusão.
3. Sempre inicialize suas variáveis para evitar `undefined` inesperado.

## Recursos Adicionais

- [Variáveis em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types#Declarações)
- [Tipos de dados e estruturas em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Data_structures)
- [JavaScript - Variáveis e Tipos de Dados (W3Schools em português)](https://www.w3schools.com/js/js_variables.asp)

## Próxima Aula

Na próxima aula, exploraremos os operadores em JavaScript, que nos permitirão realizar operações com nossas variáveis e valores.

