# Dia 11: Objetos - Introdução

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de objetos em JavaScript
2. Criar e inicializar objetos
3. Acessar e modificar propriedades de objetos
4. Utilizar métodos em objetos
5. Compreender a diferença entre objetos e arrays
6. Iterar sobre propriedades de objetos

## 1. O que são Objetos?

Objetos em JavaScript são estruturas de dados que permitem armazenar coleções de pares chave-valor. Eles são usados para representar entidades do mundo real ou conceitos abstratos em nossos programas.

## 2. Criando Objetos

Existem duas formas principais de criar objetos em JavaScript:

```javascript
// Usando a notação literal de objeto
let pessoa = {
    nome: "Maria",
    idade: 30,
    profissao: "Engenheira"
};

// Usando o construtor Object
let carro = new Object();
carro.marca = "Toyota";
carro.modelo = "Corolla";
carro.ano = 2020;
```

## 3. Acessando Propriedades de Objetos

Você pode acessar as propriedades de um objeto de duas maneiras:

```javascript
let pessoa = {
    nome: "João",
    idade: 25
};

// Usando a notação de ponto
console.log(pessoa.nome); // Saída: "João"

// Usando a notação de colchetes
console.log(pessoa["idade"]); // Saída: 25
```

## 4. Modificando Propriedades de Objetos

Você pode modificar propriedades existentes ou adicionar novas:

```javascript
let produto = {
    nome: "Notebook",
    preco: 2500
};

produto.preco = 2300; // Modifica uma propriedade existente
produto.marca = "Dell"; // Adiciona uma nova propriedade

console.log(produto);
// Saída: { nome: "Notebook", preco: 2300, marca: "Dell" }
```

## 5. Métodos em Objetos

Métodos são funções que pertencem a um objeto. Eles podem acessar e manipular as propriedades do objeto.

```javascript
let pessoa = {
    nome: "Ana",
    idade: 28,
    saudacao: function() {
        console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
    }
};

pessoa.saudacao(); // Saída: "Olá, meu nome é Ana e tenho 28 anos."
```

## 6. Objetos vs. Arrays

- Objetos usam chaves nomeadas, arrays usam índices numéricos.
- Objetos são melhores para representar entidades com múltiplas características.
- Arrays são melhores para listas ordenadas de itens.

```javascript
// Objeto
let pessoa = {
    nome: "Carlos",
    idade: 35,
    cidade: "São Paulo"
};

// Array
let frutas = ["maçã", "banana", "laranja"];
```

## 7. Iterando sobre Propriedades de Objetos

Você pode usar o loop `for...in` para iterar sobre as propriedades de um objeto:

```javascript
let carro = {
    marca: "Ford",
    modelo: "Fiesta",
    ano: 2019
};

for (let propriedade in carro) {
    console.log(`${propriedade}: ${carro[propriedade]}`);
}
// Saída:
// marca: Ford
// modelo: Fiesta
// ano: 2019
```

## 8. Object.keys(), Object.values(), e Object.entries()

Estes métodos permitem obter arrays com as chaves, valores ou pares chave-valor de um objeto:

```javascript
let pessoa = {
    nome: "Lucia",
    idade: 42,
    profissao: "Médica"
};

console.log(Object.keys(pessoa));
// Saída: ["nome", "idade", "profissao"]

console.log(Object.values(pessoa));
// Saída: ["Lucia", 42, "Médica"]

console.log(Object.entries(pessoa));
// Saída: [["nome", "Lucia"], ["idade", 42], ["profissao", "Médica"]]
```

## Exercício Prático

Crie um programa que simule um sistema de cadastro de livros:
1. Crie uma função que recebe título, autor e ano de publicação e retorna um objeto livro.
2. Crie um array para armazenar múltiplos livros.
3. Adicione alguns livros ao array.
4. Crie uma função para exibir todos os livros.
5. Crie uma função para buscar livros por autor.

Exemplo de solução:

```javascript
function criarLivro(titulo, autor, ano) {
    return {
        titulo: titulo,
        autor: autor,
        ano: ano,
        informacoes: function() {
            console.log(`${this.titulo} por ${this.autor}, publicado em ${this.ano}`);
        }
    };
}

let biblioteca = [];

biblioteca.push(criarLivro("Dom Quixote", "Miguel de Cervantes", 1605));
biblioteca.push(criarLivro("1984", "George Orwell", 1949));
biblioteca.push(criarLivro("O Pequeno Príncipe", "Antoine de Saint-Exupéry", 1943));

function exibirTodosLivros() {
    console.log("Livros na biblioteca:");
    biblioteca.forEach(livro => livro.informacoes());
}

function buscarPorAutor(autor) {
    return biblioteca.filter(livro => livro.autor.toLowerCase().includes(autor.toLowerCase()));
}

exibirTodosLivros();

console.log("\nLivros de Orwell:");
let livrosOrwell = buscarPorAutor("Orwell");
livrosOrwell.forEach(livro => livro.informacoes());
```

## Dicas Úteis

1. Use objetos para representar entidades com múltiplas características relacionadas.
2. Nomes de propriedades com mais de uma palavra devem usar camelCase (ex: `anoPublicacao`).
3. Você pode usar a palavra-chave `this` dentro de métodos para se referir ao próprio objeto.
4. Para checar se uma propriedade existe em um objeto, use o operador `in` ou o método `hasOwnProperty()`.

## Recursos Adicionais

- [Trabalhando com objetos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
- [JavaScript Objetos (W3Schools em português)](https://www.w3schools.com/js/js_objects.asp)
- [Entendendo Objetos em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-objetos/25670)

## Próxima Aula

Na próxima aula, exploraremos funções em JavaScript, que são blocos de código reutilizáveis e fundamentais para organizar e estruturar nossos programas.

