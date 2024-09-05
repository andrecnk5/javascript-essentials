# Dia 23: Quiz - Módulo 1: Fundamentos de JavaScript

## Objetivo
Este quiz tem como objetivo revisar e consolidar os conhecimentos adquiridos no Módulo 1: Fundamentos de JavaScript. Cada questão abordará um conceito importante, e as explicações detalhadas ajudarão a reforçar o aprendizado.

## Instruções
- Leia cada questão cuidadosamente.
- Escolha a melhor resposta para cada pergunta.
- Após responder, leia a explicação detalhada para entender melhor o conceito.

## Questões

1. Qual é a saída do seguinte código?
   ```javascript
   let x = 5;
   console.log(x++);
   console.log(x);
   ```
   a) 5, 5
   b) 5, 6
   c) 6, 6
   d) 6, 5

   **Resposta correta: b) 5, 6**
   
   **Explicação:** O operador `++` pós-fixado (x++) incrementa a variável, mas retorna o valor original. Portanto, o primeiro `console.log` mostra 5, e só depois x é incrementado. O segundo `console.log` mostra o novo valor de x, que é 6.

2. Qual método de array remove o último elemento?
   a) pop()
   b) push()
   c) shift()
   d) unshift()

   **Resposta correta: a) pop()**
   
   **Explicação:** `pop()` remove e retorna o último elemento de um array. `push()` adiciona um elemento ao final, `shift()` remove o primeiro elemento, e `unshift()` adiciona um elemento no início.

3. Como se declara uma função de seta (arrow function) que recebe dois parâmetros e retorna sua soma?
   a) const soma = (a, b) => a + b;
   b) const soma = (a, b) => { return a + b };
   c) const soma = function(a, b) { return a + b };
   d) const soma = (a, b) => (a + b);

   **Resposta correta: a) const soma = (a, b) => a + b;**
   
   **Explicação:** Esta é a forma mais concisa de escrever uma arrow function com retorno implícito. As opções b) e d) também estão corretas, mas a) é a mais simples para esta operação. A opção c) é uma função regular, não uma arrow function.

4. Qual é o resultado de `typeof null`?
   a) "null"
   b) "undefined"
   c) "object"
   d) "number"

   **Resposta correta: c) "object"**
   
   **Explicação:** Em JavaScript, `typeof null` retorna "object". Isso é considerado um erro na linguagem, mas é mantido por razões históricas de compatibilidade.

5. Como se acessa o terceiro elemento de um array chamado `frutas`?
   a) frutas[3]
   b) frutas[2]
   c) frutas.3
   d) frutas(2)

   **Resposta correta: b) frutas[2]**
   
   **Explicação:** Os índices de arrays em JavaScript começam em 0. Portanto, o terceiro elemento está no índice 2.

6. Qual método é usado para converter um objeto JavaScript em uma string JSON?
   a) JSON.parse()
   b) JSON.stringify()
   c) object.toJSON()
   d) JSON.toText()

   **Resposta correta: b) JSON.stringify()**
   
   **Explicação:** `JSON.stringify()` converte um objeto JavaScript em uma string JSON. `JSON.parse()` faz o oposto, convertendo uma string JSON em um objeto JavaScript.

7. O que o seguinte código irá exibir?
   ```javascript
   let x = 10;
   if (true) {
     let x = 20;
     console.log(x);
   }
   console.log(x);
   ```
   a) 20, 20
   b) 20, 10
   c) 10, 10
   d) 10, 20

   **Resposta correta: b) 20, 10**
   
   **Explicação:** O `let` dentro do bloco `if` cria uma nova variável `x` com escopo local. Ela não afeta a variável `x` fora do bloco. Portanto, dentro do bloco, `x` é 20, mas fora, mantém o valor original de 10.

8. Qual é a forma correta de checar se uma variável `x` não é igual a `null` em valor e tipo?
   a) x != null
   b) x !== null
   c) x !=== null
   d) x =! null

   **Resposta correta: b) x !== null**
   
   **Explicação:** O operador `!==` compara valor e tipo, enquanto `!=` compara apenas o valor. `!==` é mais estrito e geralmente preferido em JavaScript.

9. Como se define uma classe em JavaScript?
   a) class MinhaClasse { }
   b) function MinhaClasse() { }
   c) objeto MinhaClasse { }
   d) def MinhaClasse { }

   **Resposta correta: a) class MinhaClasse { }**
   
   **Explicação:** A palavra-chave `class` foi introduzida no ES6 para declarar classes. Embora b) seja uma forma válida de criar um construtor de função, a) é a sintaxe moderna para definir classes.

10. Qual é o resultado de `3 + 2 + "7"`?
    a) "57"
    b) 12
    c) "327"
    d) "12"

    **Resposta correta: a) "57"**
    
    **Explicação:** JavaScript avalia expressões da esquerda para a direita. Primeiro, 3 + 2 é calculado, resultando em 5. Então, 5 é concatenado com a string "7", resultando na string "57".

## Recursos Adicionais

- [JavaScript Básico (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [Guia JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide)
- [JavaScript para Iniciantes (W3Schools em português)](https://www.w3schools.com/js/default.asp)

## Conclusão

Este quiz abrange os conceitos fundamentais de JavaScript vistos no Módulo 1. Se você teve dificuldades com alguma questão, revise o tópico correspondente no material do curso. Lembre-se, a prática constante é essencial para dominar a programação JavaScript!

