# Dia 15: Objetos - Intermediário

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender e utilizar métodos de objetos
2. Trabalhar com o protótipo de objetos
3. Criar objetos usando diferentes padrões
4. Utilizar as propriedades e métodos estáticos
5. Compreender e aplicar a herança de objetos
6. Manipular propriedades de objetos de forma avançada

## 1. Métodos de Objetos

Os métodos são funções que pertencem a um objeto. Eles podem acessar e manipular as propriedades do objeto usando a palavra-chave `this`.

Exemplo:
```javascript
const pessoa = {
    nome: "Ana",
    idade: 30,
    saudacao: function() {
        return `Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`;
    },
    envelhecer() {  // Sintaxe abreviada para métodos (ES6+)
        this.idade++;
    }
};

console.log(pessoa.saudacao());  // Saída: Olá, meu nome é Ana e tenho 30 anos.
pessoa.envelhecer();
console.log(pessoa.idade);  // Saída: 31
```

## 2. Protótipos de Objetos

Cada objeto em JavaScript tem um protótipo, que é outro objeto do qual ele herda propriedades e métodos.

```javascript
function Pessoa(nome, idade) {
    this.nome = nome;
    this.idade = idade;
}

Pessoa.prototype.saudacao = function() {
    return `Olá, meu nome é ${this.nome}.`;
};

const joao = new Pessoa("João", 25);
console.log(joao.saudacao());  // Saída: Olá, meu nome é João.
```

## 3. Padrões de Criação de Objetos

### 3.1 Padrão de Fábrica (Factory Pattern)
```javascript
function criarPessoa(nome, idade) {
    return {
        nome,
        idade,
        saudacao() {
            return `Olá, meu nome é ${this.nome}.`;
        }
    };
}

const maria = criarPessoa("Maria", 28);
console.log(maria.saudacao());  // Saída: Olá, meu nome é Maria.
```

### 3.2 Padrão Construtor
```javascript
function Pessoa(nome, idade) {
    this.nome = nome;
    this.idade = idade;
    this.saudacao = function() {
        return `Olá, meu nome é ${this.nome}.`;
    };
}

const pedro = new Pessoa("Pedro", 32);
console.log(pedro.saudacao());  // Saída: Olá, meu nome é Pedro.
```

## 4. Propriedades e Métodos Estáticos

Propriedades e métodos estáticos pertencem à classe/função construtora, não às instâncias.

```javascript
class Calculadora {
    static PI = 3.14159;

    static soma(a, b) {
        return a + b;
    }
}

console.log(Calculadora.PI);  // Saída: 3.14159
console.log(Calculadora.soma(5, 3));  // Saída: 8
```

## 5. Herança de Objetos

A herança permite que um objeto base suas propriedades e métodos em outro objeto.

```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;
    }

    falar() {
        return `${this.nome} faz um som.`;
    }
}

class Cachorro extends Animal {
    falar() {
        return `${this.nome} late.`;
    }
}

const rex = new Cachorro("Rex");
console.log(rex.falar());  // Saída: Rex late.
```

## 6. Manipulação Avançada de Propriedades

### 6.1 Object.defineProperty()
```javascript
const pessoa = {};

Object.defineProperty(pessoa, 'nome', {
    value: 'Carlos',
    writable: false,
    enumerable: true,
    configurable: true
});

pessoa.nome = 'João';  // Isso não mudará o valor
console.log(pessoa.nome);  // Saída: Carlos
```

### 6.2 Getters e Setters
```javascript
const conta = {
    saldoPrivado: 0,
    get saldo() {
        return `R$ ${this.saldoPrivado.toFixed(2)}`;
    },
    set saldo(valor) {
        if (valor >= 0) {
            this.saldoPrivado = valor;
        }
    }
};

conta.saldo = 100;
console.log(conta.saldo);  // Saída: R$ 100.00
```

## Exercício Prático

Crie um sistema de gerenciamento de biblioteca:

1. Crie uma classe `Livro` com propriedades como título, autor, ISBN e status de empréstimo.
2. Crie uma classe `Biblioteca` que gerencia uma coleção de livros.
3. Implemente métodos para adicionar livros, emprestar livros e devolver livros.
4. Use getters e setters para controlar o acesso a propriedades sensíveis.
5. Implemente um método estático na classe `Biblioteca` para gerar relatórios.

Exemplo de solução:

```javascript
class Livro {
    constructor(titulo, autor, isbn) {
        this.titulo = titulo;
        this.autor = autor;
        this.isbn = isbn;
        this._emprestado = false;
    }

    get emprestado() {
        return this._emprestado;
    }

    emprestar() {
        if (!this._emprestado) {
            this._emprestado = true;
            return true;
        }
        return false;
    }

    devolver() {
        if (this._emprestado) {
            this._emprestado = false;
            return true;
        }
        return false;
    }
}

class Biblioteca {
    constructor() {
        this.livros = [];
    }

    adicionarLivro(livro) {
        this.livros.push(livro);
    }

    emprestarLivro(isbn) {
        const livro = this.livros.find(l => l.isbn === isbn);
        return livro ? livro.emprestar() : false;
    }

    devolverLivro(isbn) {
        const livro = this.livros.find(l => l.isbn === isbn);
        return livro ? livro.devolver() : false;
    }

    static gerarRelatorio(biblioteca) {
        const totalLivros = biblioteca.livros.length;
        const livrosEmprestados = biblioteca.livros.filter(l => l.emprestado).length;
        return `Total de livros: ${totalLivros}, Emprestados: ${livrosEmprestados}`;
    }
}

// Uso do sistema
const biblioteca = new Biblioteca();
const livro1 = new Livro("1984", "George Orwell", "9780451524935");
const livro2 = new Livro("O Senhor dos Anéis", "J.R.R. Tolkien", "9788533613379");

biblioteca.adicionarLivro(livro1);
biblioteca.adicionarLivro(livro2);

console.log(biblioteca.emprestarLivro("9780451524935"));  // true
console.log(biblioteca.emprestarLivro("9780451524935"));  // false (já emprestado)

console.log(Biblioteca.gerarRelatorio(biblioteca));  // Total de livros: 2, Emprestados: 1
```

## Dicas Úteis

1. Use métodos de objeto para encapsular comportamentos relacionados ao objeto.
2. Aproveite os protótipos para compartilhar métodos entre instâncias, economizando memória.
3. Escolha o padrão de criação de objetos mais adequado para cada situação.
4. Use propriedades e métodos estáticos para funcionalidades que não dependem de instâncias específicas.
5. Utilize getters e setters para um melhor controle sobre o acesso e modificação de propriedades.

## Recursos Adicionais

- [Trabalhando com objetos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
- [Herança e cadeia de protótipos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [Objetos JavaScript em detalhe (JavaScript.info em português)](https://javascript.info/object)

## Próxima Aula

Na próxima aula, exploraremos conceitos avançados de funções em JavaScript, incluindo closures, funções de ordem superior e programação funcional.

