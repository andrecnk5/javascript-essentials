# Dia 13: Funções - Avançadas

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Compreender e utilizar closures em JavaScript
2. Trabalhar com funções de ordem superior
3. Implementar e usar funções recursivas
4. Entender o conceito de IIFE (Immediately Invoked Function Expression)
5. Utilizar métodos de array que aceitam funções como argumentos

## 1. Closures

Closures são funções que têm acesso a variáveis em seu escopo externo, mesmo após a função externa ter retornado.

Exemplo:
```javascript
function criarContador() {
    let contador = 0;
    return function() {
        contador++;
        return contador;
    };
}

const contagem = criarContador();
console.log(contagem()); // 1
console.log(contagem()); // 2
console.log(contagem()); // 3
```

## 2. Funções de Ordem Superior

Funções que aceitam outras funções como argumentos ou retornam funções.

Exemplo:
```javascript
function aplicarOperacao(a, b, operacao) {
    return operacao(a, b);
}

const soma = (x, y) => x + y;
const multiplicacao = (x, y) => x * y;

console.log(aplicarOperacao(5, 3, soma)); // 8
console.log(aplicarOperacao(5, 3, multiplicacao)); // 15
```

## 3. Funções Recursivas

Funções que chamam a si mesmas para resolver um problema.

Exemplo (cálculo de fatorial):
```javascript
function fatorial(n) {
    if (n <= 1) return 1;
    return n * fatorial(n - 1);
}

console.log(fatorial(5)); // 120
```

## 4. IIFE (Immediately Invoked Function Expression)

Funções que são executadas imediatamente após serem definidas.

Exemplo:
```javascript
(function() {
    let mensagem = "Esta função é executada imediatamente!";
    console.log(mensagem);
})();
```

## 5. Métodos de Array com Funções

JavaScript oferece vários métodos de array que aceitam funções como argumentos.

### map()
Cria um novo array com os resultados da chamada de uma função para cada elemento.

```javascript
const numeros = [1, 2, 3, 4, 5];
const dobrados = numeros.map(num => num * 2);
console.log(dobrados); // [2, 4, 6, 8, 10]
```

### filter()
Cria um novo array com todos os elementos que passam no teste implementado pela função fornecida.

```javascript
const numeros = [1, 2, 3, 4, 5, 6];
const pares = numeros.filter(num => num % 2 === 0);
console.log(pares); // [2, 4, 6]
```

### reduce()
Executa uma função redutora para cada elemento do array, resultando em um único valor de retorno.

```javascript
const numeros = [1, 2, 3, 4, 5];
const soma = numeros.reduce((acumulador, atual) => acumulador + atual, 0);
console.log(soma); // 15
```

## Exercício Prático

Crie um programa que simula um sistema de processamento de pedidos:

1. Crie uma função `criarPedido` que retorna um objeto pedido com propriedades como id, item e quantidade.
2. Implemente uma função de ordem superior `processarPedidos` que aceita um array de pedidos e uma função de processamento.
3. Crie funções de processamento como `calcularTotal`, `aplicarDesconto`, e `adicionarFrete`.
4. Use métodos de array como `map`, `filter`, e `reduce` para manipular os pedidos.

Exemplo de solução:

```javascript
function criarPedido(id, item, quantidade, precoUnitario) {
    return { id, item, quantidade, precoUnitario };
}

function processarPedidos(pedidos, processamento) {
    return pedidos.map(processamento);
}

const calcularTotal = pedido => ({
    ...pedido,
    total: pedido.quantidade * pedido.precoUnitario
});

const aplicarDesconto = percentual => pedido => ({
    ...pedido,
    total: pedido.total * (1 - percentual)
});

const adicionarFrete = valorFrete => pedido => ({
    ...pedido,
    total: pedido.total + valorFrete
});

// Criando pedidos
const pedidos = [
    criarPedido(1, "Camiseta", 2, 29.99),
    criarPedido(2, "Calça", 1, 79.99),
    criarPedido(3, "Meia", 3, 9.99)
];

// Processando pedidos
const pedidosProcessados = processarPedidos(pedidos, pedido => 
    adicionarFrete(5)(
        aplicarDesconto(0.1)(
            calcularTotal(pedido)
        )
    )
);

console.log(pedidosProcessados);

// Calculando o total geral
const totalGeral = pedidosProcessados.reduce((acc, pedido) => acc + pedido.total, 0);
console.log(`Total geral dos pedidos: R$ ${totalGeral.toFixed(2)}`);
```

## Dicas Úteis

1. Use closures para criar variáveis privadas e encapsulamento.
2. Funções de ordem superior podem tornar seu código mais flexível e reutilizável.
3. Cuidado com recursão profunda, que pode causar estouro de pilha.
4. IIFE são úteis para criar escopos isolados e evitar poluição do escopo global.
5. Métodos como `map`, `filter`, e `reduce` são poderosos para manipulação de dados e podem substituir muitos loops tradicionais.

## Recursos Adicionais

- [Closures (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Closures)
- [Funções de ordem superior (Artigo em português)](https://medium.com/trainingcenter/entendendo-funções-de-alta-ordem-em-javascript-a62f139ea19)
- [Métodos de Array (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)

## Próxima Aula

Na próxima aula, revisaremos todos os conceitos aprendidos até agora e nos prepararemos para o projeto final do módulo, onde aplicaremos todos esses conhecimentos em um cenário prático.

