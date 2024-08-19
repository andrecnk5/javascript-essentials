# Dia 10: Arrays - Introdução

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de arrays e sua importância em JavaScript
2. Criar e inicializar arrays
3. Acessar e modificar elementos de um array
4. Utilizar propriedades e métodos básicos de arrays
5. Iterar sobre arrays usando diferentes técnicas

## 1. O que são Arrays?

Arrays são estruturas de dados que permitem armazenar múltiplos valores em uma única variável. Eles são fundamentais para organizar e manipular coleções de dados em JavaScript.

## 2. Criando Arrays

Há duas formas principais de criar arrays em JavaScript:

```javascript
// Usando colchetes (forma mais comum)
let frutas = ["maçã", "banana", "laranja"];

// Usando o construtor Array
let numeros = new Array(1, 2, 3, 4, 5);
```

## 3. Acessando Elementos de um Array

Os elementos de um array são acessados por meio de índices, que começam em 0:

```javascript
let cores = ["vermelho", "verde", "azul"];
console.log(cores[0]); // Saída: "vermelho"
console.log(cores[2]); // Saída: "azul"
```

## 4. Modificando Elementos de um Array

Você pode modificar elementos existentes ou adicionar novos:

```javascript
let animais = ["gato", "cachorro", "peixe"];
animais[1] = "pássaro"; // Modifica o segundo elemento
console.log(animais); // Saída: ["gato", "pássaro", "peixe"]

animais[3] = "hamster"; // Adiciona um novo elemento
console.log(animais); // Saída: ["gato", "pássaro", "peixe", "hamster"]
```

## 5. Propriedades e Métodos Básicos de Arrays

### Propriedade length
Retorna o número de elementos no array:

```javascript
let numeros = [1, 2, 3, 4, 5];
console.log(numeros.length); // Saída: 5
```

### Método push()
Adiciona um ou mais elementos ao final do array:

```javascript
let frutas = ["maçã", "banana"];
frutas.push("laranja");
console.log(frutas); // Saída: ["maçã", "banana", "laranja"]
```

### Método pop()
Remove o último elemento do array:

```javascript
let cores = ["vermelho", "verde", "azul"];
let ultimaCor = cores.pop();
console.log(ultimaCor); // Saída: "azul"
console.log(cores); // Saída: ["vermelho", "verde"]
```

### Método unshift()
Adiciona um ou mais elementos no início do array:

```javascript
let numeros = [2, 3, 4];
numeros.unshift(1);
console.log(numeros); // Saída: [1, 2, 3, 4]
```

### Método shift()
Remove o primeiro elemento do array:

```javascript
let dias = ["segunda", "terça", "quarta"];
let primeiroDia = dias.shift();
console.log(primeiroDia); // Saída: "segunda"
console.log(dias); // Saída: ["terça", "quarta"]
```

## 6. Iterando sobre Arrays

Existem várias formas de iterar sobre um array:

### Usando for
```javascript
let frutas = ["maçã", "banana", "laranja"];
for (let i = 0; i < frutas.length; i++) {
    console.log(frutas[i]);
}
```

### Usando for...of
```javascript
let numeros = [1, 2, 3, 4, 5];
for (let numero of numeros) {
    console.log(numero);
}
```

### Usando forEach()
```javascript
let cores = ["vermelho", "verde", "azul"];
cores.forEach(function(cor) {
    console.log(cor);
});
```

## Exercício Prático

Crie um programa que simule uma lista de tarefas:
1. Inicie com um array vazio chamado `tarefas`
2. Crie um loop que pergunta ao usuário se ele quer adicionar uma tarefa, remover uma tarefa ou sair
3. Se escolher adicionar, peça a descrição da tarefa e adicione ao array
4. Se escolher remover, mostre a lista de tarefas numeradas e peça o número da tarefa a ser removida
5. Após cada operação, mostre a lista atualizada de tarefas
6. Continue até o usuário escolher sair

Exemplo de solução:

```javascript
let tarefas = [];

while (true) {
    let escolha = prompt("Escolha uma opção: 1 - Adicionar tarefa, 2 - Remover tarefa, 3 - Sair");
    
    if (escolha === "1") {
        let novaTarefa = prompt("Digite a nova tarefa:");
        tarefas.push(novaTarefa);
    } else if (escolha === "2") {
        if (tarefas.length === 0) {
            console.log("Não há tarefas para remover.");
        } else {
            console.log("Tarefas atuais:");
            tarefas.forEach((tarefa, index) => {
                console.log(`${index + 1} - ${tarefa}`);
            });
            let indiceRemover = parseInt(prompt("Digite o número da tarefa a ser removida:")) - 1;
            if (indiceRemover >= 0 && indiceRemover < tarefas.length) {
                tarefas.splice(indiceRemover, 1);
            } else {
                console.log("Índice inválido.");
            }
        }
    } else if (escolha === "3") {
        break;
    }
    
    console.log("Lista de Tarefas Atual:", tarefas);
}

console.log("Programa finalizado. Lista final de tarefas:", tarefas);
```

## Dicas Úteis

1. Arrays em JavaScript podem conter diferentes tipos de dados, incluindo outros arrays (arrays multidimensionais).
2. Use `const` para declarar arrays que você não pretende reatribuir, mas lembre-se que ainda pode modificar seus elementos.
3. Evite usar `delete` para remover elementos de um array, pois isso deixa "buracos" undefined. Prefira métodos como `splice()`.
4. Para copiar arrays, cuidado com a atribuição direta (`let novoArray = arrayAntigo`), pois isso cria uma referência, não uma cópia. Use métodos como `slice()` ou o operador spread `[...arrayAntigo]` para criar cópias reais.

## Recursos Adicionais

- [Arrays (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [JavaScript Arrays (W3Schools em português)](https://www.w3schools.com/js/js_arrays.asp)
- [Trabalhando com Arrays em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-arrays/4079)

## Próxima Aula

Na próxima aula, aprofundaremos nosso conhecimento sobre objetos em JavaScript, outra estrutura de dados fundamental para organizar e trabalhar com informações complexas.

