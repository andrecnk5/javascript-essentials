# Dia 16: Classes - Básico

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de classes em JavaScript
2. Criar e utilizar classes básicas
3. Trabalhar com construtores e métodos de classe
4. Utilizar propriedades e métodos estáticos
5. Implementar getters e setters em classes
6. Compreender a diferença entre classes e funções construtoras

## 1. Introdução às Classes

Classes em JavaScript, introduzidas no ES6, fornecem uma sintaxe mais clara e simples para criar objetos e implementar herança baseada em protótipo.

```javascript
class Pessoa {
    constructor(nome, idade) {
        this.nome = nome;
        this.idade = idade;
    }

    apresentar() {
        console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
    }
}

const pessoa1 = new Pessoa("Ana", 30);
pessoa1.apresentar(); // Saída: Olá, meu nome é Ana e tenho 30 anos.
```

## 2. Construtores

O método `constructor` é um método especial para criar e inicializar objetos criados com a classe.

```javascript
class Carro {
    constructor(marca, modelo, ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
        this.velocidade = 0;
    }
}

const meuCarro = new Carro("Toyota", "Corolla", 2022);
console.log(meuCarro.modelo); // Saída: Corolla
```

## 3. Métodos de Classe

Métodos são funções definidas dentro da classe e podem ser chamados em instâncias da classe.

```javascript
class Calculadora {
    somar(a, b) {
        return a + b;
    }

    subtrair(a, b) {
        return a - b;
    }
}

const calc = new Calculadora();
console.log(calc.somar(5, 3)); // Saída: 8
console.log(calc.subtrair(10, 4)); // Saída: 6
```

## 4. Propriedades e Métodos Estáticos

Membros estáticos pertencem à própria classe, não às instâncias da classe.

```javascript
class Utilitarios {
    static PI = 3.14159;

    static areaCirculo(raio) {
        return this.PI * raio * raio;
    }
}

console.log(Utilitarios.PI); // Saída: 3.14159
console.log(Utilitarios.areaCirculo(5)); // Saída: 78.53975
```

## 5. Getters e Setters

Getters e setters permitem definir como acessar e modificar as propriedades de uma classe.

```javascript
class Temperatura {
    constructor(celsius) {
        this._celsius = celsius;
    }

    get fahrenheit() {
        return (this._celsius * 9/5) + 32;
    }

    set fahrenheit(valor) {
        this._celsius = (valor - 32) * 5/9;
    }
}

const temp = new Temperatura(25);
console.log(temp.fahrenheit); // Saída: 77
temp.fahrenheit = 86;
console.log(temp._celsius); // Saída: 30
```

## 6. Classes vs. Funções Construtoras

Classes em JavaScript são essencialmente "açúcar sintático" sobre o sistema de protótipos existente.

```javascript
// Usando função construtora
function PessoaFunc(nome, idade) {
    this.nome = nome;
    this.idade = idade;
}

PessoaFunc.prototype.apresentar = function() {
    console.log(`Olá, sou ${this.nome} e tenho ${this.idade} anos.`);
};

// Usando classe
class PessoaClasse {
    constructor(nome, idade) {
        this.nome = nome;
        this.idade = idade;
    }

    apresentar() {
        console.log(`Olá, sou ${this.nome} e tenho ${this.idade} anos.`);
    }
}

// Ambos funcionam de maneira similar
const pessoa1 = new PessoaFunc("João", 25);
const pessoa2 = new PessoaClasse("Maria", 30);

pessoa1.apresentar(); // Saída: Olá, sou João e tenho 25 anos.
pessoa2.apresentar(); // Saída: Olá, sou Maria e tenho 30 anos.
```

## Exercício Prático

Crie um sistema básico de gerenciamento de biblioteca usando classes:

1. Crie uma classe `Livro` com propriedades como título, autor e ISBN.
2. Crie uma classe `Biblioteca` que gerencia uma coleção de livros.
3. Implemente métodos para adicionar livros, remover livros e buscar livros por título ou autor.
4. Use um getter para obter o número total de livros na biblioteca.
5. Implemente um método estático para gerar um ISBN único para novos livros.

Exemplo de solução:

```javascript
class Livro {
    constructor(titulo, autor) {
        this.titulo = titulo;
        this.autor = autor;
        this.isbn = Livro.gerarISBN();
    }

    static gerarISBN() {
        return 'ISBN-' + Math.random().toString(36).substr(2, 9);
    }
}

class Biblioteca {
    constructor() {
        this.livros = [];
    }

    adicionarLivro(livro) {
        this.livros.push(livro);
    }

    removerLivro(isbn) {
        this.livros = this.livros.filter(livro => livro.isbn !== isbn);
    }

    buscarPorTitulo(titulo) {
        return this.livros.filter(livro => 
            livro.titulo.toLowerCase().includes(titulo.toLowerCase())
        );
    }

    buscarPorAutor(autor) {
        return this.livros.filter(livro => 
            livro.autor.toLowerCase().includes(autor.toLowerCase())
        );
    }

    get totalLivros() {
        return this.livros.length;
    }
}

// Uso do sistema
const biblioteca = new Biblioteca();

const livro1 = new Livro("O Senhor dos Anéis", "J.R.R. Tolkien");
const livro2 = new Livro("Harry Potter", "J.K. Rowling");

biblioteca.adicionarLivro(livro1);
biblioteca.adicionarLivro(livro2);

console.log(biblioteca.totalLivros); // Saída: 2

console.log(biblioteca.buscarPorAutor("Tolkien")); 
// Saída: [Livro { titulo: 'O Senhor dos Anéis', autor: 'J.R.R. Tolkien', isbn: '...' }]

biblioteca.removerLivro(livro1.isbn);
console.log(biblioteca.totalLivros); // Saída: 1
```

## Dicas Úteis

1. Use classes para criar objetos com estruturas e comportamentos relacionados.
2. O construtor é chamado automaticamente quando um novo objeto é criado.
3. Métodos estáticos são úteis para funcionalidades que não dependem de uma instância específica.
4. Getters e setters permitem um controle mais fino sobre como as propriedades são acessadas e modificadas.
5. Lembre-se de que classes em JavaScript são uma abstração sobre o sistema de protótipos existente.

## Recursos Adicionais

- [Classes (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes)
- [Introdução a classes JavaScript (JavaScript.info em português)](https://javascript.info/class)
- [Entendendo Classes em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-entendendo-classes/40418)

## Próxima Aula

Na próxima aula, exploraremos conceitos mais avançados de classes em JavaScript, incluindo herança, polimorfismo e encapsulamento.

