# Dia 18: Revisão do Módulo 1 - Parte 2/3

## Objetivos da Revisão
Nesta segunda parte da revisão, vamos recapitular e reforçar os seguintes tópicos:
1. Objetos
2. JSON (JavaScript Object Notation)
3. Classes Básicas
4. Manipulação do DOM (Introdução)
5. Eventos Básicos

## 1. Objetos

Os objetos em JavaScript são estruturas que agrupam propriedades e métodos relacionados.

### Criação de Objetos
```javascript
// Usando literal de objeto
let pessoa = {
    nome: "Ana",
    idade: 30,
    saudacao: function() {
        console.log(`Olá, meu nome é ${this.nome}`);
    }
};

// Usando construtor de objeto
function Carro(marca, modelo) {
    this.marca = marca;
    this.modelo = modelo;
}

let meuCarro = new Carro("Toyota", "Corolla");
```

### Acessando e Modificando Propriedades
```javascript
console.log(pessoa.nome);  // Ana
pessoa['idade'] = 31;
console.log(pessoa.idade);  // 31

pessoa.profissao = "Engenheira";  // Adicionando nova propriedade
delete pessoa.idade;  // Removendo uma propriedade
```

### Métodos de Objeto
```javascript
let calculadora = {
    somar: function(a, b) {
        return a + b;
    },
    subtrair: (a, b) => a - b  // Usando arrow function
};

console.log(calculadora.somar(5, 3));  // 8
```

## 2. JSON (JavaScript Object Notation)

JSON é um formato leve de troca de dados, fácil para humanos lerem e escreverem.

### Sintaxe JSON
```json
{
  "nome": "Maria",
  "idade": 25,
  "cidade": "São Paulo",
  "hobbies": ["leitura", "natação"]
}
```

### Conversão entre JSON e Objetos JavaScript
```javascript
// Objeto para JSON
let obj = { nome: "João", idade: 30 };
let jsonString = JSON.stringify(obj);
console.log(jsonString);  // {"nome":"João","idade":30}

// JSON para Objeto
let jsonObj = JSON.parse(jsonString);
console.log(jsonObj.nome);  // João
```

## 3. Classes Básicas

Classes em JavaScript, introduzidas no ES6, fornecem uma sintaxe mais clara para criar objetos e implementar herança.

### Definindo uma Classe
```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;
    }

    falar() {
        console.log(`${this.nome} faz um som.`);
    }
}

let cachorro = new Animal("Rex");
cachorro.falar();  // Rex faz um som.
```

### Herança
```javascript
class Gato extends Animal {
    falar() {
        console.log(`${this.nome} mia.`);
    }
}

let gato = new Gato("Mimi");
gato.falar();  // Mimi mia.
```

## 4. Manipulação do DOM (Introdução)

O DOM (Document Object Model) é uma interface de programação para documentos HTML e XML.

### Selecionando Elementos
```javascript
let titulo = document.getElementById("titulo");
let paragrafos = document.getElementsByClassName("paragrafo");
let botoes = document.getElementsByTagName("button");

let primeiroLink = document.querySelector("a");
let todosLinks = document.querySelectorAll("a");
```

### Modificando Elementos
```javascript
titulo.textContent = "Novo Título";
primeiroLink.setAttribute("href", "https://www.exemplo.com");
botoes[0].style.backgroundColor = "blue";
```

### Criando e Removendo Elementos
```javascript
let novoParagrafo = document.createElement("p");
novoParagrafo.textContent = "Este é um novo parágrafo.";
document.body.appendChild(novoParagrafo);

let paraRemover = document.querySelector(".remover");
paraRemover.parentNode.removeChild(paraRemover);
```

## 5. Eventos Básicos

Eventos permitem que o JavaScript reaja a ações do usuário ou do navegador.

### Adicionando Event Listeners
```javascript
let botao = document.getElementById("meuBotao");

botao.addEventListener("click", function() {
    console.log("Botão clicado!");
});

// Usando arrow function
botao.addEventListener("mouseover", () => {
    botao.style.backgroundColor = "red";
});
```

### Eventos Comuns
```javascript
// Evento de carregamento da página
window.addEventListener("load", () => {
    console.log("Página carregada!");
});

// Evento de submissão de formulário
let formulario = document.getElementById("meuFormulario");
formulario.addEventListener("submit", (evento) => {
    evento.preventDefault();  // Previne o envio padrão do formulário
    console.log("Formulário enviado!");
});
```

## Exercício de Revisão

Crie uma página HTML simples com um botão e um parágrafo. Use JavaScript para:
1. Alterar o texto do parágrafo quando o botão for clicado.
2. Mudar a cor de fundo do botão quando o mouse passar sobre ele.
3. Armazenar o número de cliques em um objeto e exibi-lo no parágrafo.

Exemplo de solução:

```html
<!DOCTYPE html>
<html>
<body>
    <button id="meuBotao">Clique-me</button>
    <p id="contagem">Cliques: 0</p>

    <script>
        let botao = document.getElementById("meuBotao");
        let paragrafo = document.getElementById("contagem");
        let contador = { cliques: 0 };

        botao.addEventListener("click", () => {
            contador.cliques++;
            paragrafo.textContent = `Cliques: ${contador.cliques}`;
        });

        botao.addEventListener("mouseover", () => {
            botao.style.backgroundColor = "lightblue";
        });

        botao.addEventListener("mouseout", () => {
            botao.style.backgroundColor = "";
        });
    </script>
</body>
</html>
```

## Recursos Adicionais

- [Objetos JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
- [JSON (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON)
- [Classes em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes)
- [Introdução ao DOM (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model/Introduction)
- [Eventos em JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/Events)

Na próxima parte da revisão, abordaremos tópicos avançados de funções, programação assíncrona e uma revisão geral do módulo.

