# Dia 19: Classes - Intermediário

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Implementar herança entre classes usando `extends`
2. Utilizar o método `super()` para chamar o construtor da classe pai
3. Sobrescrever métodos da classe pai na classe filha
4. Criar e usar métodos e propriedades privadas
5. Implementar polimorfismo em JavaScript
6. Utilizar classes abstratas e métodos abstratos

## 1. Herança de Classes

A herança permite que uma classe herde propriedades e métodos de outra classe.

```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;
    }

    falar() {
        console.log(`${this.nome} faz um som.`);
    }
}

class Cachorro extends Animal {
    falar() {
        console.log(`${this.nome} late.`);
    }
}

const animal = new Animal("Animal");
animal.falar(); // Saída: Animal faz um som.

const cachorro = new Cachorro("Rex");
cachorro.falar(); // Saída: Rex late.
```

## 2. Utilizando `super()`

O método `super()` é usado para chamar o construtor da classe pai.

```javascript
class Veiculo {
    constructor(marca, modelo) {
        this.marca = marca;
        this.modelo = modelo;
    }

    descrever() {
        return `${this.marca} ${this.modelo}`;
    }
}

class Carro extends Veiculo {
    constructor(marca, modelo, ano) {
        super(marca, modelo);
        this.ano = ano;
    }

    descrever() {
        return `${super.descrever()} (${this.ano})`;
    }
}

const meuCarro = new Carro("Toyota", "Corolla", 2022);
console.log(meuCarro.descrever()); // Saída: Toyota Corolla (2022)
```

## 3. Sobrescrevendo Métodos

Métodos da classe pai podem ser sobrescritos na classe filha para modificar ou estender seu comportamento.

```javascript
class Forma {
    calcularArea() {
        return 0;
    }
}

class Retangulo extends Forma {
    constructor(largura, altura) {
        super();
        this.largura = largura;
        this.altura = altura;
    }

    calcularArea() {
        return this.largura * this.altura;
    }
}

const retangulo = new Retangulo(5, 3);
console.log(retangulo.calcularArea()); // Saída: 15
```

## 4. Propriedades e Métodos Privados

JavaScript introduziu suporte a propriedades e métodos privados usando o prefixo `#`.

```javascript
class ContaBancaria {
    #saldo = 0;

    constructor(titular) {
        this.titular = titular;
    }

    depositar(valor) {
        if (valor > 0) {
            this.#saldo += valor;
            this.#registrarTransacao("Depósito", valor);
        }
    }

    sacar(valor) {
        if (valor > 0 && valor <= this.#saldo) {
            this.#saldo -= valor;
            this.#registrarTransacao("Saque", valor);
            return true;
        }
        return false;
    }

    consultarSaldo() {
        return this.#saldo;
    }

    #registrarTransacao(tipo, valor) {
        console.log(`${tipo}: ${valor}`);
    }
}

const conta = new ContaBancaria("João");
conta.depositar(100);
conta.sacar(50);
console.log(conta.consultarSaldo()); // Saída: 50
// conta.#saldo; // Erro: propriedade privada
// conta.#registrarTransacao(); // Erro: método privado
```

## 5. Polimorfismo

Polimorfismo permite que objetos de diferentes classes sejam tratados de maneira uniforme.

```javascript
class Funcionario {
    constructor(nome, salario) {
        this.nome = nome;
        this.salario = salario;
    }

    calcularBonus() {
        return this.salario * 0.1;
    }
}

class Gerente extends Funcionario {
    calcularBonus() {
        return this.salario * 0.2;
    }
}

class Desenvolvedor extends Funcionario {
    calcularBonus() {
        return this.salario * 0.15;
    }
}

function imprimirBonus(funcionario) {
    console.log(`${funcionario.nome} recebe um bônus de ${funcionario.calcularBonus()}`);
}

const func1 = new Funcionario("Ana", 3000);
const func2 = new Gerente("Carlos", 5000);
const func3 = new Desenvolvedor("Mariana", 4000);

imprimirBonus(func1); // Ana recebe um bônus de 300
imprimirBonus(func2); // Carlos recebe um bônus de 1000
imprimirBonus(func3); // Mariana recebe um bônus de 600
```

## 6. Classes e Métodos Abstratos

JavaScript não tem suporte nativo para classes abstratas, mas podemos simular esse comportamento.

```javascript
class FormaAbstrata {
    constructor() {
        if (new.target === FormaAbstrata) {
            throw new Error("Não pode instanciar uma classe abstrata");
        }
    }

    calcularArea() {
        throw new Error("Método abstrato deve ser implementado");
    }
}

class Circulo extends FormaAbstrata {
    constructor(raio) {
        super();
        this.raio = raio;
    }

    calcularArea() {
        return Math.PI * this.raio * this.raio;
    }
}

// const forma = new FormaAbstrata(); // Erro
const circulo = new Circulo(5);
console.log(circulo.calcularArea()); // Aproximadamente 78.54
```

## Exercício Prático

Crie um sistema de gerenciamento de funcionários de uma empresa:

1. Crie uma classe base `Funcionario` com propriedades como nome, id e salário.
2. Crie classes derivadas como `Gerente`, `Desenvolvedor` e `Designer`.
3. Implemente um método `calcularSalarioAnual()` na classe base e sobrescreva-o nas classes derivadas para incluir bônus específicos.
4. Use propriedades privadas para o salário.
5. Crie uma classe `Empresa` que gerencia uma lista de funcionários e calcula a folha de pagamento total.

Exemplo de solução:

```javascript
class Funcionario {
    #salario;

    constructor(nome, id, salario) {
        this.nome = nome;
        this.id = id;
        this.#salario = salario;
    }

    calcularSalarioAnual() {
        return this.#salario * 12;
    }

    get salario() {
        return this.#salario;
    }
}

class Gerente extends Funcionario {
    calcularSalarioAnual() {
        return super.calcularSalarioAnual() + this.salario * 0.1;
    }
}

class Desenvolvedor extends Funcionario {
    calcularSalarioAnual() {
        return super.calcularSalarioAnual() + 5000; // Bônus anual fixo
    }
}

class Designer extends Funcionario {
    calcularSalarioAnual() {
        return super.calcularSalarioAnual() + this.salario * 0.05;
    }
}

class Empresa {
    constructor() {
        this.funcionarios = [];
    }

    adicionarFuncionario(funcionario) {
        this.funcionarios.push(funcionario);
    }

    calcularFolhaPagamentoAnual() {
        return this.funcionarios.reduce((total, func) => total + func.calcularSalarioAnual(), 0);
    }
}

// Uso do sistema
const empresa = new Empresa();

empresa.adicionarFuncionario(new Gerente("Ana", 1, 10000));
empresa.adicionarFuncionario(new Desenvolvedor("Carlos", 2, 8000));
empresa.adicionarFuncionario(new Designer("Mariana", 3, 7000));

console.log(`Folha de pagamento anual: R$ ${empresa.calcularFolhaPagamentoAnual()}`);
```

## Dicas Úteis

1. Use herança para compartilhar comportamentos comuns entre classes relacionadas.
2. Sobrescreva métodos quando precisar modificar ou estender o comportamento da classe pai.
3. Utilize propriedades e métodos privados para encapsular detalhes de implementação.
4. Aproveite o polimorfismo para criar código mais flexível e extensível.
5. Ao simular classes abstratas, use verificações no construtor para evitar instanciação direta.

## Recursos Adicionais

- [Herança em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Objects/Inheritance)
- [Polimorfismo em JavaScript (DevMedia em português)](https://www.devmedia.com.br/polimorfismo-em-javascript/39645)
- [Classes em JavaScript (JavaScript.info em português)](https://javascript.info/classes)

## Próxima Aula

Na próxima aula, exploraremos conceitos avançados de manipulação do DOM (Document Object Model) com JavaScript, permitindo-nos criar interações dinâmicas em páginas web.

