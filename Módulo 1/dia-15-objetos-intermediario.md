# Dia 16: Objetos - Intermediário

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender e utilizar protótipos em JavaScript
2. Implementar herança de objetos
3. Trabalhar com métodos avançados de objetos
4. Utilizar getters e setters
5. Compreender o conceito de encapsulamento em JavaScript
6. Aplicar técnicas de composição de objetos

## 1. Protótipos em JavaScript

Os protótipos são o mecanismo pelo qual objetos JavaScript herdam características uns dos outros.

### Exemplo de Protótipo:

```javascript
function Animal(nome) {
    this.nome = nome;
}

Animal.prototype.fazerSom = function() {
    console.log(`${this.nome} faz um som.`);
};

let cachorro = new Animal("Rex");
cachorro.fazerSom(); // Saída: Rex faz um som.
```

## 2. Herança de Objetos

A herança permite que um objeto base suas propriedades e métodos em outro objeto.

### Exemplo de Herança:

```javascript
function Cachorro(nome) {
    Animal.call(this, nome); // Chama o construtor pai
}

Cachorro.prototype = Object.create(Animal.prototype);
Cachorro.prototype.constructor = Cachorro;

Cachorro.prototype.latir = function() {
    console.log(`${this.nome} está latindo!`);
};

let meuCachorro = new Cachorro("Buddy");
meuCachorro.fazerSom(); // Saída: Buddy faz um som.
meuCachorro.latir(); // Saída: Buddy está latindo!
```

## 3. Métodos Avançados de Objetos

### Object.create()

Cria um novo objeto com o protótipo especificado.

```javascript
let pessoa = {
    saudacao: function() {
        console.log(`Olá, meu nome é ${this.nome}`);
    }
};

let joao = Object.create(pessoa);
joao.nome = "João";
joao.saudacao(); // Saída: Olá, meu nome é João
```

### Object.assign()

Copia as propriedades de um ou mais objetos fonte para um objeto alvo.

```javascript
let objetoBase = { a: 1, b: 2 };
let extensao = { b: 3, c: 4 };
let objetoCompleto = Object.assign({}, objetoBase, extensao);
console.log(objetoCompleto); // Saída: { a: 1, b: 3, c: 4 }
```

## 4. Getters e Setters

Permitem definir como acessar e modificar as propriedades de um objeto.

```javascript
let pessoa = {
    primeiroNome: "João",
    ultimoNome: "Silva",
    get nomeCompleto() {
        return `${this.primeiroNome} ${this.ultimoNome}`;
    },
    set nomeCompleto(nome) {
        let partes = nome.split(" ");
        this.primeiroNome = partes[0];
        this.ultimoNome = partes[1];
    }
};

console.log(pessoa.nomeCompleto); // Saída: João Silva
pessoa.nomeCompleto = "Maria Santos";
console.log(pessoa.primeiroNome); // Saída: Maria
```

## 5. Encapsulamento em JavaScript

Embora JavaScript não tenha modificadores de acesso como outras linguagens, podemos simular encapsulamento usando closures.

```javascript
function ContaBancaria(saldoInicial) {
    let saldo = saldoInicial;
    
    return {
        depositar: function(valor) {
            saldo += valor;
        },
        sacar: function(valor) {
            if (valor <= saldo) {
                saldo -= valor;
                return true;
            }
            return false;
        },
        consultarSaldo: function() {
            return saldo;
        }
    };
}

let minhaConta = ContaBancaria(1000);
minhaConta.depositar(500);
console.log(minhaConta.consultarSaldo()); // Saída: 1500
console.log(minhaConta.saldo); // Saída: undefined (saldo é privado)
```

## 6. Composição de Objetos

A composição é uma técnica para criar objetos complexos combinando objetos mais simples.

```javascript
function criarPessoa(nome) {
    return {
        nome: nome,
        apresentar: function() {
            console.log(`Olá, eu sou ${this.nome}.`);
        }
    };
}

function criarEmpregado(pessoa, cargo) {
    return Object.assign({}, pessoa, {
        cargo: cargo,
        trabalhar: function() {
            console.log(`${this.nome} está trabalhando como ${this.cargo}.`);
        }
    });
}

let pessoa = criarPessoa("Ana");
let empregado = criarEmpregado(pessoa, "Desenvolvedora");
empregado.apresentar(); // Saída: Olá, eu sou Ana.
empregado.trabalhar(); // Saída: Ana está trabalhando como Desenvolvedora.
```

## Exercício Prático

Crie um sistema de gerenciamento de uma biblioteca usando os conceitos aprendidos:

1. Crie uma função construtora `Livro` com propriedades como título, autor e ISBN.
2. Implemente um protótipo para `Livro` com um método `exibirDetalhes`.
3. Crie uma função construtora `Biblioteca` que gerencia uma coleção de livros.
4. Adicione métodos para adicionar livros, remover livros e buscar por título ou autor.
5. Use encapsulamento para proteger a coleção de livros.
6. Implemente getters e setters para acessar e modificar informações da biblioteca.

Exemplo de solução:

```javascript
function Livro(titulo, autor, isbn) {
    this.titulo = titulo;
    this.autor = autor;
    this.isbn = isbn;
}

Livro.prototype.exibirDetalhes = function() {
    console.log(`${this.titulo} por ${this.autor}, ISBN: ${this.isbn}`);
};

function Biblioteca() {
    let livros = [];

    this.adicionarLivro = function(livro) {
        livros.push(livro);
    };

    this.removerLivro = function(isbn) {
        livros = livros.filter(livro => livro.isbn !== isbn);
    };

    this.buscarPorTitulo = function(titulo) {
        return livros.filter(livro => livro.titulo.includes(titulo));
    };

    Object.defineProperty(this, 'quantidadeDeLivros', {
        get: function() {
            return livros.length;
        }
    });
}

let minhaBiblioteca = new Biblioteca();
let livro1 = new Livro("O Senhor dos Anéis", "J.R.R. Tolkien", "9788533613379");
let livro2 = new Livro("1984", "George Orwell", "9788535914849");

minhaBiblioteca.adicionarLivro(livro1);
minhaBiblioteca.adicionarLivro(livro2);

console.log(minhaBiblioteca.quantidadeDeLivros); // Saída: 2
minhaBiblioteca.buscarPorTitulo("Anéis")[0].exibirDetalhes();
// Saída: O Senhor dos Anéis por J.R.R. Tolkien, ISBN: 9788533613379
```

## Dicas Úteis

1. Use protótipos para compartilhar métodos entre instâncias de objetos, economizando memória.
2. Prefira composição sobre herança quando possível para criar estruturas de objetos mais flexíveis.
3. Use getters e setters para controlar o acesso e modificação de propriedades de objetos.
4. Aproveite o encapsulamento para proteger dados e implementar a lógica de negócios.

## Recursos Adicionais

- [Herança e cadeia de protótipos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [Trabalhando com objetos (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
- [Programação Orientada a Objetos em JavaScript (DevMedia em português)](https://www.devmedia.com.br/programacao-orientada-a-objetos-em-javascript/28434)

## Próxima Aula

Na próxima aula, exploraremos conceitos avançados de objetos em JavaScript, incluindo padrões de design e técnicas de otimização.

