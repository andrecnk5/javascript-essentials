# Dia 23: Mini-Projeto 1 - Gerenciador de Tarefas

## Objetivo do Projeto
Criar um aplicativo de gerenciamento de tarefas que permita aos usuários adicionar, visualizar, marcar como concluídas e excluir tarefas. Este projeto aplicará vários conceitos fundamentais de JavaScript aprendidos até agora.

## Requisitos do Projeto

1. Interface de Usuário:
   - Campo de entrada para adicionar novas tarefas
   - Botão para adicionar tarefas
   - Lista de tarefas existentes
   - Opção para marcar tarefas como concluídas
   - Opção para excluir tarefas

2. Funcionalidades:
   - Adicionar novas tarefas à lista
   - Exibir a lista de tarefas
   - Marcar tarefas como concluídas (visual diferente)
   - Excluir tarefas da lista
   - Armazenar tarefas no localStorage para persistência de dados

3. Implementação:
   - Usar HTML para a estrutura básica
   - Estilizar com CSS (pode ser mínimo)
   - Implementar toda a lógica com JavaScript

## Estrutura do Projeto

```
mini-projeto-1/
│
├── index.html
├── style.css
└── script.js
```

## Passo a Passo

### 1. Estrutura HTML (index.html)

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerenciador de Tarefas</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Gerenciador de Tarefas</h1>
        <form id="taskForm">
            <input type="text" id="taskInput" placeholder="Adicione uma nova tarefa" required>
            <button type="submit">Adicionar</button>
        </form>
        <ul id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### 2. Estilo Básico (style.css)

```css
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 500px;
    margin: auto;
    overflow: auto;
    padding: 0 10px;
}

#taskInput {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
}

#taskList {
    list-style-type: none;
    padding: 0;
}

.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px;
}

.task.done {
    text-decoration: line-through;
    color: #888;
}
```

### 3. JavaScript (script.js)

```javascript
// Seleção de elementos do DOM
const taskForm = document.getElementById('taskForm');
const taskInput = document.getElementById('taskInput');
const taskList = document.getElementById('taskList');

// Array para armazenar as tarefas
let tasks = [];

// Carregar tarefas do localStorage
function loadTasks() {
    const storedTasks = localStorage.getItem('tasks');
    if (storedTasks) {
        tasks = JSON.parse(storedTasks);
        renderTasks();
    }
}

// Salvar tarefas no localStorage
function saveTasks() {
    localStorage.setItem('tasks', JSON.stringify(tasks));
}

// Renderizar tarefas na lista
function renderTasks() {
    taskList.innerHTML = '';
    tasks.forEach((task, index) => {
        const li = document.createElement('li');
        li.className = `task ${task.done ? 'done' : ''}`;
        li.innerHTML = `
            <span>${task.text}</span>
            <button onclick="toggleTask(${index})">✓</button>
            <button onclick="deleteTask(${index})">✗</button>
        `;
        taskList.appendChild(li);
    });
}

// Adicionar nova tarefa
function addTask(text) {
    tasks.push({ text, done: false });
    saveTasks();
    renderTasks();
}

// Alternar status da tarefa (concluída/não concluída)
function toggleTask(index) {
    tasks[index].done = !tasks[index].done;
    saveTasks();
    renderTasks();
}

// Excluir tarefa
function deleteTask(index) {
    tasks.splice(index, 1);
    saveTasks();
    renderTasks();
}

// Event listener para o formulário
taskForm.addEventListener('submit', (e) => {
    e.preventDefault();
    const text = taskInput.value.trim();
    if (text) {
        addTask(text);
        taskInput.value = '';
    }
});

// Carregar tarefas ao iniciar
loadTasks();
```

## Explicação do Código

1. **Estrutura de Dados**: Usamos um array `tasks` para armazenar objetos de tarefas.

2. **localStorage**: Utilizamos `localStorage` para persistir as tarefas entre sessões.

3. **Manipulação do DOM**: Criamos elementos dinamicamente e atualizamos a lista de tarefas.

4. **Event Listeners**: Usamos um listener no formulário para adicionar novas tarefas.

5. **Funções**: Implementamos funções para adicionar, alternar e excluir tarefas.

6. **Renderização**: A função `renderTasks()` atualiza a interface do usuário.

## Desafios Adicionais

1. Adicione uma funcionalidade de filtro para mostrar apenas tarefas concluídas ou não concluídas.
2. Implemente uma funcionalidade de edição de tarefas existentes.
3. Adicione categorias ou tags às tarefas.
4. Implemente um sistema de prioridade para as tarefas.

## Recursos Adicionais

- [Trabalhando com o DOM (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model/Introduction)
- [Usando o Web Storage API (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
- [JavaScript para iniciantes (W3Schools em português)](https://www.w3schools.com/js/default.asp)

## Conclusão

Este mini-projeto permite aplicar vários conceitos fundamentais de JavaScript, incluindo manipulação do DOM, eventos, armazenamento local e funções. Ele também oferece uma base sólida para expandir com funcionalidades mais avançadas à medida que você progride no curso.

