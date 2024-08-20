# Dia 1: Introdução à Programação e JavaScript

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Definir o que é programação e sua importância
2. Compreender o papel do JavaScript no desenvolvimento web
3. Reconhecer a evolução histórica do JavaScript
4. Diferenciar entre JavaScript no navegador e no servidor (Node.js)

## 1. O que é Programação?

Programação é o processo de criar um conjunto de instruções que dizem a um computador como realizar uma tarefa. É como escrever uma receita muito detalhada para o computador seguir.

### Exemplo: Fazer um Sanduíche
Imagine que você está ensinando um robô a fazer um sanduíche. Você precisaria fornecer instruções muito específicas:

```css
1. Pegue duas fatias de pão
2. Coloque uma fatia na mesa
3. Pegue a manteiga
4. Espalhe a manteiga na fatia de pão
5. Pegue uma fatia de queijo
6. Coloque o queijo sobre o pão com manteiga
7. Pegue a outra fatia de pão
8. Coloque-a sobre o queijo
```

Programação é similar: você fornece instruções detalhadas para o computador executar tarefas.

## 2. Importância do JavaScript

JavaScript é uma das linguagens de programação mais populares e versáteis do mundo. Sua importância se deve a vários fatores:

- **Onipresença**: Praticamente todos os sites modernos usam JavaScript.
- **Versatilidade**: Pode ser usado tanto no front-end quanto no back-end.
- **Comunidade Ativa**: Grande número de bibliotecas e frameworks disponíveis.
- **Fácil de Aprender**: Sintaxe relativamente simples para iniciantes.

### Exemplo: Interatividade em uma Página Web
Sem JavaScript:
```html
<button>Clique-me!</button>
```
Este botão não faria nada quando clicado.

Com JavaScript:
```html
<button onclick="alert('Olá, Mundo!')">Clique-me!</button>
```
Agora, ao clicar no botão, uma mensagem "Olá, Mundo!" aparecerá.

## 3. História do JavaScript

- **1995**: Criado por Brendan Eich na Netscape em apenas 10 dias.
- **1997**: Padronizado pela ECMA International (ECMAScript).
- **2009**: Node.js é criado, permitindo JavaScript no servidor.
- **2015**: ECMAScript 6 (ES6) lança com muitas novas features.
- **Hoje**: Atualizações anuais (ES2016, ES2017, etc.)

### Exemplo: Evolução da Sintaxe

ES5 (pré-2015):
```javascript
var saudacao = function(nome) {
    return "Olá, " + nome + "!";
};
```

ES6+ (2015 em diante):
```javascript
const saudacao = (nome) => `Olá, ${nome}!`;
```

## 4. JavaScript no Navegador vs. Servidor (Node.js)

### JavaScript no Navegador:
- Roda no ambiente do navegador do usuário.
- Manipula o DOM (estrutura da página web).
- Interage com APIs do navegador (localStorage, fetch, etc.).

#### Exemplo: Alterando o Conteúdo da Página
```javascript
document.getElementById('mensagem').innerHTML = 'Bem-vindo!';
```

### JavaScript no Servidor (Node.js):
- Roda no servidor.
- Acessa o sistema de arquivos, banco de dados, etc.
- Não tem acesso ao DOM ou APIs do navegador.

#### Exemplo: Lendo um Arquivo no Servidor
```javascript
const fs = require('fs');
fs.readFile('arquivo.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

## Resumo
- Programação é dar instruções precisas para um computador.
- JavaScript é uma linguagem versátil usada tanto no front-end quanto no back-end.
- Desde 1995, JavaScript evoluiu significativamente.
- JavaScript no navegador lida com interações do usuário, enquanto no servidor (Node.js) lida com operações do lado do servidor.

## Exercício Prático
Tente escrever um "programa" em linguagem natural para uma tarefa simples, como fazer café. Depois, pense em como isso se relaciona com a programação em JavaScript.

## Leitura Adicional
- [Uma Breve História do JavaScript](https://auth0.com/blog/a-brief-history-of-javascript/)
- [Introdução ao JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Introduction)

Próxima aula: Configuração do Ambiente de Desenvolvimento JavaScript.

------

[🏠](README.md) | [➡️](dia02-configuracao-ambiente.md)



