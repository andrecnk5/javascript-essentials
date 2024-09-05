# Dia 16: Objetos - Avançados

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Utilizar padrões de design com objetos em JavaScript
2. Implementar mixins e composição avançada
3. Trabalhar com objetos imutáveis e freezing
4. Entender e aplicar programação orientada a objetos funcional
5. Utilizar proxies e reflect para metaprogramação
6. Aplicar técnicas de otimização de objetos

## 1. Padrões de Design com Objetos

### 1.1 Padrão Singleton

O padrão Singleton garante que uma classe tenha apenas uma instância e fornece um ponto global de acesso a ela.

```javascript
const Singleton = (function() {
    let instance;

    function createInstance() {
        const object = new Object("Eu sou a instância");
        return object;
    }

    return {
        getInstance: function() {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();

const instance1 = Singleton.getInstance();
const instance2 = Singleton.getInstance();
console.log(instance1 === instance2); // true
```

### 1.2 Padrão Factory

O padrão Factory define uma interface para criar um objeto, mas deixa as subclasses decidirem qual classe instanciar.

```javascript
function Carro(modelo) {
    this.modelo = modelo;
    this.buzinar = function() {
        console.log(this.modelo + " buzina: Beep!");
    }
}

function Moto(modelo) {
    this.modelo = modelo;
    this.empinar = function() {
        console.log(this.modelo + " empina!");
    }
}

function VeiculoFactory() {
    this.criarVeiculo = function(tipo, modelo) {
        switch(tipo) {
            case "carro":
                return new Carro(modelo);
            case "moto":
                return new Moto(modelo);
        }
    }
}

const factory = new VeiculoFactory();
const carro = factory.criarVeiculo("carro", "Fusca");
const moto = factory.criarVeiculo("moto", "Harley");

carro.buzinar(); // Fusca buzina: Beep!
moto.empinar(); // Harley empina!
```

## 2. Mixins e Composição Avançada

Mixins permitem adicionar funcionalidades a objetos sem usar herança.

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

function criarPato(nome) {
    return Object.assign({}, nadadorMixin, voadorMixin, { nome });
}

const pato = criarPato("Donald");
pato.nadar(); // Donald está nadando.
pato.voar(); // Donald está voando.
```

## 3. Objetos Imutáveis e Freezing

Criar objetos imutáveis ajuda a prevenir efeitos colaterais indesejados.

```javascript
const configuracoesImutaveis = Object.freeze({
    API_URL: "https://api.exemplo.com",
    TIMEOUT: 5000
});

// Tentativa de modificação não terá efeito
configuracoesImutaveis.TIMEOUT = 6000;
console.log(configuracoesImutaveis.TIMEOUT); // Ainda é 5000

// Para "modificar", crie um novo objeto
const novasConfiguracoes = { ...configuracoesImutaveis, TIMEOUT: 6000 };
console.log(novasConfiguracoes.TIMEOUT); // 6000
```

## 4. Programação Orientada a Objetos Funcional

Combina conceitos de programação funcional com objetos.

```javascript
const Pessoa = (nome, idade) => ({
    nome,
    idade,
    saudacao: () => `Olá, meu nome é ${nome} e tenho ${idade} anos.`
});

const incrementarIdade = pessoa => ({
    ...pessoa,
    idade: pessoa.idade + 1
});

let joao = Pessoa("João", 30);
console.log(joao.saudacao()); // Olá, meu nome é João e tenho 30 anos.

joao = incrementarIdade(joao);
console.log(joao.idade); // 31
```

## 5. Proxies e Reflect

Proxies permitem definir comportamentos customizados para operações fundamentais em objetos.

```javascript
const handler = {
    get: function(obj, prop) {
        return prop in obj ? obj[prop] : "Propriedade não encontrada";
    }
};

const pessoa = { nome: "Ana", idade: 28 };
const proxy = new Proxy(pessoa, handler);

console.log(proxy.nome); // Ana
console.log(proxy.profissao); // Propriedade não encontrada

// Usando Reflect
const objeto = { a: 1, b: 2 };
console.log(Reflect.has(objeto, 'a')); // true
Reflect.set(objeto, 'c', 3);
console.log(objeto.c); // 3
```

## 6. Otimização de Objetos

### 6.1 Usando Object.create() para Performance

```javascript
const protoMetodos = {
    saudacao() {
        return `Olá, eu sou ${this.nome}`;
    }
};

function criarPessoa(nome) {
    return Object.create(protoMetodos, {
        nome: { value: nome }
    });
}

const maria = criarPessoa("Maria");
console.log(maria.saudacao()); // Olá, eu sou Maria
```

### 6.2 Evitando Modificações de Protótipo em Runtime

```javascript
const Pessoa = function(nome) {
    this.nome = nome;
};

Pessoa.prototype.saudacao = function() {
    return `Olá, eu sou ${this.nome}`;
};

Object.seal(Pessoa.prototype);
// Agora, não é possível adicionar ou remover métodos do protótipo
```

## Exercício Prático

Crie um sistema de gerenciamento de loja online utilizando conceitos avançados de objetos:

1. Use o padrão Singleton para gerenciar o estado global da loja.
2. Implemente um Factory para criar diferentes tipos de produtos.
3. Use mixins para adicionar funcionalidades como "descontável" ou "enviável".
4. Implemente um Proxy para controlar o acesso ao estoque.
5. Utilize programação orientada a objetos funcional para operações de carrinho de compras.

Exemplo de solução parcial:

```javascript
// Singleton para gerenciamento da loja
const LojaManager = (function() {
    let instance;

    function criarInstancia() {
        return {
            estoque: {},
            adicionarAoEstoque(produto, quantidade) {
                if (!this.estoque[produto.id]) {
                    this.estoque[produto.id] = { produto, quantidade };
                } else {
                    this.estoque[produto.id].quantidade += quantidade;
                }
            }
        };
    }

    return {
        getInstance: function() {
            if (!instance) {
                instance = criarInstancia();
            }
            return instance;
        }
    };
})();

// Factory para produtos
function ProdutoFactory() {
    this.criarProduto = function(tipo, nome, preco) {
        switch(tipo) {
            case "livro":
                return new Livro(nome, preco);
            case "eletronico":
                return new Eletronico(nome, preco);
            // Adicione mais tipos conforme necessário
        }
    }
}

// Mixins
const descontavelMixin = {
    aplicarDesconto(percentual) {
        this.preco = this.preco * (1 - percentual);
    }
};

// Classes de produtos
function Produto(nome, preco) {
    this.nome = nome;
    this.preco = preco;
    this.id = Date.now(); // ID único simplificado
}

function Livro(nome, preco) {
    Produto.call(this, nome, preco);
    this.tipo = "livro";
}

function Eletronico(nome, preco) {
    Produto.call(this, nome, preco);
    this.tipo = "eletronico";
}

// Aplicando mixin
Object.assign(Livro.prototype, descontavelMixin);

// Uso
const loja = LojaManager.getInstance();
const factory = new ProdutoFactory();

const livro = factory.criarProduto("livro", "JavaScript Avançado", 50);
const eletronico = factory.criarProduto("eletronico", "Smartphone", 1000);

loja.adicionarAoEstoque(livro, 10);
loja.adicionarAoEstoque(eletronico, 5);

livro.aplicarDesconto(0.1);
console.log(livro.preco); // 45

console.log(loja.estoque);
```

## Dicas Úteis

1. Use padrões de design para resolver problemas comuns de forma eficiente.
2. Prefira composição sobre herança para criar estruturas de objetos mais flexíveis.
3. Utilize objetos imutáveis para prevenir efeitos colaterais indesejados.
4. Aproveite as capacidades de metaprogramação do JavaScript com Proxies e Reflect.
5. Otimize a criação de objetos considerando o desempenho em aplicações de larga escala.

## Recursos Adicionais

- [Padrões de Design em JavaScript (em português)](https://www.patterns.dev/posts/classic-design-patterns/)
- [Objetos JavaScript Avançado (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)
- [Programação Orientada a Objetos em JavaScript (DevMedia em português)](https://www.devmedia.com.br/programacao-orientada-a-objetos-em-javascript/28434)

## Próxima Aula

Na próxima aula, exploraremos técnicas avançadas de manipulação do DOM e eventos em JavaScript, aplicando muitos dos conceitos de objetos que aprendemos até agora.

