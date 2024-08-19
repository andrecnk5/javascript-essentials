# Dia 15: Objetos - Avançados

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Utilizar descritores de propriedades para controle fino de objetos
2. Implementar e compreender o padrão de módulo em JavaScript
3. Criar e usar mixins para compartilhar funcionalidades entre objetos
4. Aplicar técnicas de composição de objetos
5. Entender e utilizar o conceito de programação orientada a objetos em JavaScript
6. Trabalhar com objetos imutáveis e entender suas vantagens

## 1. Descritores de Propriedades

Os descritores de propriedades permitem um controle mais preciso sobre as características das propriedades de um objeto.

```javascript
const pessoa = {};

Object.defineProperty(pessoa, 'nome', {
    value: 'Ana',
    writable: false,
    enumerable: true,
    configurable: false
});

Object.defineProperty(pessoa, 'idade', {
    value: 30,
    writable: true,
    enumerable: false,
    configurable: true
});

console.log(pessoa.nome); // Ana
pessoa.nome = 'Maria'; // Não altera o valor devido a writable: false
console.log(pessoa.nome); // Ana

for (let prop in pessoa) {
    console.log(prop); // Apenas 'nome' será exibido, pois 'idade' tem enumerable: false
}

// Tentar reconfigurar 'nome' lançará um erro devido a configurable: false
// Object.defineProperty(pessoa, 'nome', { writable: true }); // Erro
```

## 2. Padrão de Módulo

O padrão de módulo utiliza closures para criar escopo privado e público em objetos.

```javascript
const ContaBancaria = (function() {
    let saldo = 0; // Variável privada

    function depositar(valor) {
        saldo += valor;
    }

    function sacar(valor) {
        if (valor <= saldo) {
            saldo -= valor;
            return true;
        }
        return false;
    }

    return {
        depositar: depositar,
        sacar: sacar,
        consultarSaldo: function() {
            return saldo;
        }
    };
})();

ContaBancaria.depositar(100);
console.log(ContaBancaria.consultarSaldo()); // 100
console.log(ContaBancaria.sacar(50)); // true
console.log(ContaBancaria.consultarSaldo()); // 50
console.log(ContaBancaria.saldo); // undefined (variável privada)
```

## 3. Mixins

Mixins são uma forma de adicionar métodos a objetos sem usar herança.

```javascript
const nadadorMixin = {
    nadar() {
        console.log(`${this.nome} está nadando.`);
    }
};

const voadorMixin = {
    voar() {
        console.log(`${this.nome} está voando.`);
    }
};

class Animal {
    constructor(nome) {
        this.nome = nome;
    }
}

class Pato extends Animal {}
Object.assign(Pato.prototype, nadadorMixin, voadorMixin);

const pato = new Pato('Donald');
pato.nadar(); // Donald está nadando.
pato.voar(); // Donald está voando.
```

## 4. Composição de Objetos

A composição é uma técnica para criar objetos complexos combinando objetos mais simples.

```javascript
function criarPessoa(nome) {
    return {
        nome,
        apresentar() {
            console.log(`Olá, eu sou ${this.nome}.`);
        }
    };
}

function criarEmpregado(pessoa, cargo) {
    return Object.assign({}, pessoa, {
        cargo,
        trabalhar() {
            console.log(`${this.nome} está trabalhando como ${this.cargo}.`);
        }
    });
}

const pessoa = criarPessoa('Carlos');
const empregado = criarEmpregado(pessoa, 'Desenvolvedor');

empregado.apresentar(); // Olá, eu sou Carlos.
empregado.trabalhar(); // Carlos está trabalhando como Desenvolvedor.
```

## 5. Programação Orientada a Objetos em JavaScript

JavaScript suporta POO através de protótipos e, mais recentemente, com a sintaxe de classe (ES6+).

```javascript
class Veiculo {
    constructor(marca, modelo) {
        this.marca = marca;
        this.modelo = modelo;
    }

    descrever() {
        return `Este é um ${this.marca} ${this.modelo}.`;
    }
}

class Carro extends Veiculo {
    constructor(marca, modelo, portas) {
        super(marca, modelo);
        this.portas = portas;
    }

    descrever() {
        return `${super.descrever()} Tem ${this.portas} portas.`;
    }
}

const meuCarro = new Carro('Toyota', 'Corolla', 4);
console.log(meuCarro.descrever()); // Este é um Toyota Corolla. Tem 4 portas.
```

## 6. Objetos Imutáveis

Objetos imutáveis são aqueles cujo estado não pode ser alterado após a criação.

```javascript
const configuracaoImutavel = Object.freeze({
    API_URL: 'https://api.exemplo.com',
    TIMEOUT: 5000
});

// Tentativa de modificação não terá efeito
configuracaoImutavel.TIMEOUT = 6000;
console.log(configuracaoImutavel.TIMEOUT); // Ainda é 5000

// Para "modificar", crie um novo objeto
const novaConfiguracao = Object.assign({}, configuracaoImutavel, { TIMEOUT: 6000 });
console.log(novaConfiguracao.TIMEOUT); // 6000
```

## Exercício Prático

Crie um sistema de gerenciamento de loja online utilizando conceitos avançados de objetos:

1. Use o padrão de módulo para criar um módulo de gerenciamento de estoque.
2. Implemente uma classe `Produto` com propriedades privadas usando Symbol.
3. Crie um mixin para adicionar funcionalidades de desconto aos produtos.
4. Use composição para criar diferentes tipos de produtos (por exemplo, produtos físicos e digitais).
5. Implemente um sistema de carrinho de compras usando objetos imutáveis.

Exemplo de solução:

```javascript
// Módulo de gerenciamento de estoque
const GerenciadorEstoque = (function() {
    const estoque = new Map();

    return {
        adicionarProduto(produto, quantidade) {
            estoque.set(produto, (estoque.get(produto) || 0) + quantidade);
        },
        removerProduto(produto, quantidade) {
            const estoqueAtual = estoque.get(produto) || 0;
            if (estoqueAtual >= quantidade) {
                estoque.set(produto, estoqueAtual - quantidade);
                return true;
            }
            return false;
        },
        consultarEstoque(produto) {
            return estoque.get(produto) || 0;
        }
    };
})();

// Classe Produto com propriedade privada
const precoProdutoPrivado = Symbol('precoProduto');

class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this[precoProdutoPrivado] = preco;
    }

    get preco() {
        return this[precoProdutoPrivado];
    }
}

// Mixin de desconto
const descontoMixin = {
    aplicarDesconto(percentual) {
        const desconto = this.preco * (percentual / 100);
        return Object.create(this, {
            precoComDesconto: {
                value: this.preco - desconto,
                enumerable: true
            }
        });
    }
};

// Composição para diferentes tipos de produtos
function criarProdutoFisico(produto, peso) {
    return Object.assign({}, produto, { peso, calcularFrete() { /* lógica de frete */ } });
}

function criarProdutoDigital(produto) {
    return Object.assign({}, produto, { download() { /* lógica de download */ } });
}

// Carrinho de compras imutável
const CarrinhoDeCompras = {
    itens: [],
    adicionarItem(produto, quantidade) {
        return Object.assign(Object.create(CarrinhoDeCompras), {
            itens: [...this.itens, { produto, quantidade }]
        });
    },
    removerItem(index) {
        return Object.assign(Object.create(CarrinhoDeCompras), {
            itens: this.itens.filter((_, i) => i !== index)
        });
    },
    calcularTotal() {
        return this.itens.reduce((total, item) => total + item.produto.preco * item.quantidade, 0);
    }
};

// Uso do sistema
const camiseta = new Produto('Camiseta', 29.99);
Object.assign(Produto.prototype, descontoMixin);

GerenciadorEstoque.adicionarProduto(camiseta, 100);

const camisetaComDesconto = camiseta.aplicarDesconto(10);
console.log(camisetaComDesconto.precoComDesconto); // 26.991

const camisetaFisica = criarProdutoFisico(camiseta, 0.2);
const ebook = criarProdutoDigital(new Produto('E-book JavaScript', 19.99));

let carrinho = CarrinhoDeCompras;
carrinho = carrinho.adicionarItem(camisetaFisica, 2);
carrinho = carrinho.adicionarItem(ebook, 1);

console.log(carrinho.calcularTotal()); // 79.97
console.log(GerenciadorEstoque.consultarEstoque(camiseta)); // 100
```

## Dicas Úteis

1. Use descritores de propriedades para um controle fino sobre as características das propriedades.
2. O padrão de módulo é útil para encapsular lógica e criar escopos privados.
3. Prefira composição sobre herança quando possível para criar objetos mais flexíveis.
4. Utilize mixins para adicionar funcionalidades a objetos sem criar hierarquias complexas.
5. Considere usar objetos imutáveis para evitar efeitos colaterais indesejados em sua aplicação.

## Recursos Adicionais

- [Objetos JavaScript Avançado (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)
- [Programação Orientada a Objetos em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
- [Padrões de Design JavaScript (em português)](https://www.patterns.dev/posts/classic-design-patterns/)

## Próxima Aula

Na próxima aula, exploraremos técnicas avançadas de manipulação de arrays e aplicação de métodos funcionais em JavaScript.

