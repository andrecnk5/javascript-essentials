# Dia 13: Objetos - Introdução

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Entender o conceito de objetos em JavaScript
2. Criar e manipular objetos usando diferentes notações
3. Acessar e modificar propriedades de objetos
4. Utilizar métodos em objetos
5. Compreender a diferença entre objetos e arrays
6. Iterar sobre propriedades de objetos

## 1. O que são Objetos?

Objetos em JavaScript são estruturas de dados que permitem armazenar coleções de pares chave-valor. Eles são usados para representar entidades do mundo real ou conceitos abstratos em nossos programas.

### Exemplo Básico:

```javascript
let pessoa = {
    nome: "Maria",
    idade: 30,
    profissao: "Engenheira"
};
```

Neste exemplo, `pessoa` é um objeto com três propriedades: `nome`, `idade` e `profissao`.

## 2. Criando Objetos

Existem várias formas de criar objetos em JavaScript:

### 2.1 Notação Literal de Objeto

```javascript
let carro = {
    marca: "Toyota",
    modelo: "Corolla",
    ano: 2022
};
```

### 2.2 Usando o Construtor Object()

```javascript
let pessoa = new Object();
pessoa.nome = "João";
pessoa.idade = 25;
```

### 2.3 Função Construtora

```javascript
function Livro(titulo, autor) {
    this.titulo = titulo;
    this.autor = autor;
}

let meuLivro = new Livro("O Senhor dos Anéis", "J.R.R. Tolkien");
```

## 3. Acessando Propriedades de Objetos

Você pode acessar as propriedades de um objeto de duas maneiras:

### 3.1 Notação de Ponto

```javascript
console.log(pessoa.nome); // Saída: Maria
```

### 3.2 Notação de Colchetes

```javascript
console.log(pessoa["idade"]); // Saída: 30
```

A notação de colchetes é útil quando o nome da propriedade é dinâmico ou contém caracteres especiais.

## 4. Modificando Propriedades de Objetos

Você pode modificar propriedades existentes ou adicionar novas:

```javascript
pessoa.idade = 31; // Modifica uma propriedade existente
pessoa.email = "maria@example.com"; // Adiciona uma nova propriedade
```

## 5. Métodos em Objetos

Métodos são funções que pertencem a um objeto.

```javascript
let calculadora = {
    somar: function(a, b) {
        return a + b;
    },
    subtrair: function(a, b) {
        return a - b;
    }
};

console.log(calculadora.somar(5, 3)); // Saída: 8
```

## 6. Objetos vs. Arrays

- Objetos usam chaves nomeadas, arrays usam índices numéricos.
- Objetos são melhores para representar entidades com múltiplas características.
- Arrays são melhores para listas ordenadas de itens.

```javascript
// Objeto
let pessoa = {
    nome: "Carlos",
    idade: 35
};

// Array
let numeros = [1, 2, 3, 4, 5];
```

## 7. Iterando sobre Propriedades de Objetos

### 7.1 Usando for...in

```javascript
for (let chave in pessoa) {
    console.log(chave + ": " + pessoa[chave]);
}
```

### 7.2 Usando Object.keys()

```javascript
Object.keys(pessoa).forEach(chave => {
    console.log(chave + ": " + pessoa[chave]);
});
```

## Exercício Prático

Crie um objeto `biblioteca` que representa uma biblioteca. Este objeto deve:

1. Ter uma propriedade `livros` que é um array de objetos, cada um representando um livro.
2. Ter um método `adicionarLivro` que adiciona um novo livro ao array.
3. Ter um método `buscarPorAutor` que retorna todos os livros de um determinado autor.

Exemplo de solução:

```javascript
let biblioteca = {
    livros: [],
    adicionarLivro: function(titulo, autor, anoPublicacao) {
        this.livros.push({ titulo, autor, anoPublicacao });
    },
    buscarPorAutor: function(autorBuscado) {
        return this.livros.filter(livro => livro.autor === autorBuscado);
    }
};

biblioteca.adicionarLivro("Dom Quixote", "Miguel de Cervantes", 1605);
biblioteca.adicionarLivro("1984", "George Orwell", 1949);
biblioteca.adicionarLivro("O Hobbit", "J.R.R. Tolkien", 1937);

console.log(biblioteca.buscarPorAutor("George Orwell"));
// Saída: [{ titulo: "1984", autor: "George Orwell", anoPublicacao: 1949 }]
```

## Dicas Úteis

1. Use objetos para agrupar dados relacionados e funcionalidades.
2. Escolha nomes descritivos para propriedades e métodos.
3. Prefira a notação de ponto para acessar propriedades, a menos que precise de acesso dinâmico.
4. Lembre-se que objetos em JavaScript são mutáveis por padrão.

## Recursos Adicionais

- [Trabalhando com objetos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
- [Objetos JavaScript (W3Schools em português)](https://www.w3schools.com/js/js_objects.asp)
- [Entendendo Objetos em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-objetos/25670)

## Próxima Aula

Na próxima aula, aprofundaremos nosso conhecimento sobre objetos, explorando conceitos mais avançados como protótipos, herança e métodos de objeto.
