# Dia 24: Avaliação - Módulo 1: Fundamentos de JavaScript

## Objetivo
Esta avaliação tem como objetivo verificar a compreensão e aplicação dos conceitos fundamentais de JavaScript aprendidos no Módulo 1.

## Instruções
- Leia cada questão cuidadosamente antes de responder.
- A avaliação contém diferentes tipos de questões, incluindo múltipla escolha, verdadeiro ou falso, análise de código e questões práticas.
- Para as questões práticas, escreva o código JavaScript necessário para resolver o problema proposto.

## Avaliação

### Parte 1: Múltipla Escolha

1. Qual das seguintes opções NÃO é um tipo de dado primitivo em JavaScript?
   a) Number
   b) String
   c) Boolean
   d) Array

   **Resposta: d) Array**
   
   **Justificativa:** Arrays são objetos em JavaScript, não tipos primitivos. Os tipos primitivos são: Number, String, Boolean, Undefined, Null, Symbol e BigInt.

2. Qual é o resultado da expressão `3 + 4 + "5"`?
   a) "345"
   b) "75"
   c) 12
   d) "12"

   **Resposta: b) "75"**
   
   **Justificativa:** JavaScript avalia a expressão da esquerda para a direita. Primeiro, 3 + 4 é calculado como 7 (número), então 7 é concatenado com a string "5", resultando em "75".

### Parte 2: Verdadeiro ou Falso

3. [ ] `let` e `const` têm escopo de bloco, enquanto `var` tem escopo de função.
4. [ ] O operador `===` compara valor e tipo, enquanto `==` compara apenas o valor.
5. [ ] Arrays em JavaScript podem conter elementos de diferentes tipos.

**Respostas:**
3. Verdadeiro
4. Verdadeiro
5. Verdadeiro

**Justificativas:**
3. `let` e `const` foram introduzidos no ES6 e têm escopo de bloco, o que oferece um controle mais preciso sobre as variáveis.
4. `===` é o operador de igualdade estrita, que verifica tanto o valor quanto o tipo. `==` pode realizar coerção de tipos.
5. JavaScript permite que arrays contenham elementos de qualquer tipo, incluindo mistura de tipos diferentes.

### Parte 3: Associação de Colunas

Associe os métodos de array à sua função:

6. 
   A. push()     1. Remove o último elemento
   B. pop()      2. Adiciona elemento(s) ao final
   C. shift()    3. Remove o primeiro elemento
   D. unshift()  4. Adiciona elemento(s) ao início

**Respostas:**
A-2, B-1, C-3, D-4

**Justificativa:** Estes são os métodos básicos para manipulação de arrays em JavaScript, cada um com uma função específica para adicionar ou remover elementos no início ou no final do array.

### Parte 4: Análise de Código

7. O que será impresso no console após a execução do seguinte código?

```javascript
let x = 1;
function foo() {
    let x = 2;
    console.log(x);
}
foo();
console.log(x);
```

**Resposta:**
```
2
1
```

**Justificativa:** A função `foo()` cria uma nova variável `x` com escopo local, que não afeta a variável `x` no escopo global. Portanto, dentro da função, `x` é 2, mas fora da função, `x` mantém seu valor original de 1.

### Parte 5: Questão Prática

8. Escreva uma função chamada `contarVogais` que recebe uma string como parâmetro e retorna o número de vogais (a, e, i, o, u) nessa string. A função deve ser case-insensitive (não diferenciar maiúsculas de minúsculas).

**Exemplo de solução:**

```javascript
function contarVogais(str) {
    const vogais = ['a', 'e', 'i', 'o', 'u'];
    return str.toLowerCase().split('').filter(char => vogais.includes(char)).length;
}

console.log(contarVogais("JavaScript")); // Deve retornar 3
```

**Justificativa:** Esta função converte a string para minúsculas, divide-a em um array de caracteres, filtra apenas as vogais e conta o número de elementos resultantes. Isso demonstra o uso de métodos de string e array, bem como funções de alta ordem (filter).

### Parte 6: Múltipla Escolha (Caixas de Seleção)

9. Quais das seguintes afirmações sobre funções em JavaScript são verdadeiras? (Selecione todas as opções corretas)
   [ ] Funções em JavaScript são objetos de primeira classe.
   [ ] Arrow functions sempre criam um novo contexto `this`.
   [ ] Funções podem ser passadas como argumentos para outras funções.
   [ ] Todas as funções em JavaScript devem ter um valor de retorno explícito.

**Respostas corretas:**
- Funções em JavaScript são objetos de primeira classe.
- Funções podem ser passadas como argumentos para outras funções.

**Justificativa:** Funções em JavaScript são tratadas como objetos de primeira classe, o que significa que podem ser atribuídas a variáveis, passadas como argumentos e retornadas por outras funções. Arrow functions, na verdade, não criam um novo contexto `this`. Nem todas as funções precisam ter um retorno explícito; funções sem `return` retornam `undefined` implicitamente.

## Recursos Adicionais

- [Guia JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide)
- [JavaScript Básico (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [Funções JavaScript (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions)

## Conclusão

Esta avaliação cobre os principais conceitos do Módulo 1: Fundamentos de JavaScript. Revise as áreas em que teve dificuldades e pratique regularmente para consolidar seu aprendizado.

