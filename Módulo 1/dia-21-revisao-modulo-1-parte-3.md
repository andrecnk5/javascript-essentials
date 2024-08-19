# Dia 21: Revisão do Módulo 1 - Parte 3/3

## Objetivos da Revisão
Nesta terceira e última parte da revisão, vamos recapitular e reforçar os seguintes tópicos:
1. Funções Avançadas
2. Programação Assíncrona
3. Manipulação de Erros
4. Módulos em JavaScript
5. Boas Práticas e Padrões de Projeto
6. Revisão Geral do Módulo

## 1. Funções Avançadas

### Closures
Closures são funções que têm acesso a variáveis em seu escopo externo.

```javascript
function criarContador() {
    let contador = 0;
    return function() {
        return ++contador;
    };
}

const contar = criarContador();
console.log(contar()); // 1
console.log(contar()); // 2
```

### Funções de Alta Ordem
Funções que recebem ou retornam outras funções.

```javascript
function aplicarOperacao(a, b, operacao) {
    return operacao(a, b);
}

const soma = (x, y) => x + y;
const multiplica = (x, y) => x * y;

console.log(aplicarOperacao(5, 3, soma)); // 8
console.log(aplicarOperacao(5, 3, multiplica)); // 15
```

## 2. Programação Assíncrona

### Promises
Promises representam uma operação assíncrona que pode ser bem-sucedida ou falhar.

```javascript
function buscarDados(id) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (id > 0) {
                resolve(`Dados do usuário ${id}`);
            } else {
                reject("ID inválido");
            }
        }, 1000);
    });
}

buscarDados(1)
    .then(dados => console.log(dados))
    .catch(erro => console.error(erro));
```

### Async/Await
Uma forma mais limpa de trabalhar com promises.

```javascript
async function buscarUsuario(id) {
    try {
        const dados = await buscarDados(id);
        console.log(dados);
    } catch (erro) {
        console.error(erro);
    }
}

buscarUsuario(2);
```

## 3. Manipulação de Erros

### Try...Catch
Usado para capturar e tratar erros.

```javascript
function dividir(a, b) {
    if (b === 0) {
        throw new Error("Divisão por zero!");
    }
    return a / b;
}

try {
    console.log(dividir(10, 2)); // 5
    console.log(dividir(10, 0)); // Lança erro
} catch (erro) {
    console.error("Ocorreu um erro:", erro.message);
} finally {
    console.log("Operação concluída");
}
```

## 4. Módulos em JavaScript

Módulos permitem organizar o código em arquivos separados.

```javascript
// math.js
export function soma(a, b) {
    return a + b;
}

export function multiplica(a, b) {
    return a * b;
}

// main.js
import { soma, multiplica } from './math.js';

console.log(soma(5, 3)); // 8
console.log(multiplica(4, 2)); // 8
```

## 5. Boas Práticas e Padrões de Projeto

### Destructuring
```javascript
const pessoa = { nome: "Ana", idade: 30 };
const { nome, idade } = pessoa;
console.log(nome, idade); // Ana 30

const numeros = [1, 2, 3];
const [primeiro, ...resto] = numeros;
console.log(primeiro, resto); // 1 [2, 3]
```

### Template Literals
```javascript
const nome = "Maria";
const mensagem = `Olá, ${nome}! Bem-vinda ao curso.`;
console.log(mensagem);
```

### Arrow Functions
```javascript
const quadrado = x => x * x;
console.log(quadrado(4)); // 16
```

## 6. Revisão Geral do Módulo

### Principais Conceitos Aprendidos:
1. Variáveis, tipos de dados e operadores
2. Estruturas de controle (if, switch, loops)
3. Funções e escopo
4. Arrays e objetos
5. Manipulação do DOM e eventos
6. Classes e herança
7. Programação assíncrona
8. Módulos e organização de código

### Projeto de Revisão

Crie uma aplicação de lista de tarefas que incorpore os conceitos aprendidos:

1. Use classes para representar tarefas
2. Implemente funcionalidades de adicionar, remover e marcar tarefas como concluídas
3. Utilize o DOM para renderizar a lista e manipular elementos
4. Implemente armazenamento local usando `localStorage`
5. Use módulos para organizar o código
6. Implemente tratamento de erros

Exemplo de estrutura:

```javascript
// tarefa.js
export class Tarefa {
    constructor(descricao) {
        this.id = Date.now();
        this.descricao = descricao;
        this.concluida = false;
    }
}

// listaTarefas.js
import { Tarefa } from './tarefa.js';

export class ListaTarefas {
    constructor() {
        this.tarefas = [];
    }

    adicionarTarefa(descricao) {
        const tarefa = new Tarefa(descricao);
        this.tarefas.push(tarefa);
        this.salvar();
    }

    removerTarefa(id) {
        this.tarefas = this.tarefas.filter(t => t.id !== id);
        this.salvar();
    }

    marcarComoConcluida(id) {
        const tarefa = this.tarefas.find(t => t.id === id);
        if (tarefa) {
            tarefa.concluida = !tarefa.concluida;
            this.salvar();
        }
    }

    salvar() {
        localStorage.setItem('tarefas', JSON.stringify(this.tarefas));
    }

    carregar() {
        const tarefasSalvas = localStorage.getItem('tarefas');
        this.tarefas = tarefasSalvas ? JSON.parse(tarefasSalvas) : [];
    }
}

// main.js
import { ListaTarefas } from './listaTarefas.js';

const lista = new ListaTarefas();
lista.carregar();

function renderizarLista() {
    const ul = document.getElementById('listaTarefas');
    ul.innerHTML = '';
    lista.tarefas.forEach(tarefa => {
        const li = document.createElement('li');
        li.textContent = tarefa.descricao;
        if (tarefa.concluida) li.style.textDecoration = 'line-through';
        ul.appendChild(li);
    });
}

document.getElementById('formTarefa').addEventListener('submit', (e) => {
    e.preventDefault();
    const input = document.getElementById('novaTarefa');
    lista.adicionarTarefa(input.value);
    input.value = '';
    renderizarLista();
});

renderizarLista();
```

## Recursos Adicionais

- [JavaScript Assíncrono (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous)
- [Módulos JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Modules)
- [Boas práticas em JavaScript (DevMedia em português)](https://www.devmedia.com.br/boas-praticas-em-javascript/28451)

Parabéns por concluir a revisão do Módulo 1! Continue praticando e aplicando esses conceitos em projetos reais para solidificar seu aprendizado.

