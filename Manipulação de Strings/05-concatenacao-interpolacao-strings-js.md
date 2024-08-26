# 5. Concatenação e Interpolação de Strings em JavaScript

## 5.1 Introdução

A concatenação e interpolação de strings são técnicas fundamentais em JavaScript para combinar strings e incorporar valores dinâmicos em strings. Estas técnicas são essenciais para criar mensagens dinâmicas, construir URLs, gerar HTML dinâmico e muito mais.

## 5.2 Concatenação de Strings

A concatenação de strings é o processo de combinar duas ou mais strings em uma única string.

### 5.2.1 Usando o Operador +

O método mais básico de concatenação é usar o operador +.

```javascript
let primeiroNome = "João";
let sobrenome = "Silva";
let nomeCompleto = primeiroNome + " " + sobrenome;
console.log(nomeCompleto); // "João Silva"
```

### 5.2.2 Usando o Método concat()

O método `concat()` pode ser usado para concatenar duas ou mais strings.

```javascript
let saudacao = "Olá";
let nome = "Maria";
let mensagem = saudacao.concat(", ", nome, "!");
console.log(mensagem); // "Olá, Maria!"
```

### 5.2.3 Concatenação com Atribuição +=

O operador += pode ser usado para concatenar e atribuir em uma única operação.

```javascript
let frase = "JavaScript ";
frase += "é ";
frase += "incrível!";
console.log(frase); // "JavaScript é incrível!"
```

## 5.3 Interpolação de Strings

A interpolação de strings permite incorporar expressões diretamente dentro de strings literais.

### 5.3.1 Template Literals

Introduzidos no ES6, template literals usam backticks (`) e permitem interpolação com ${expressão}.

```javascript
let nome = "Alice";
let idade = 30;
let mensagem = `${nome} tem ${idade} anos.`;
console.log(mensagem); // "Alice tem 30 anos."
```

### 5.3.2 Expressões em Template Literals

Você pode incluir qualquer expressão JavaScript válida dentro de ${}.

```javascript
let a = 5;
let b = 10;
console.log(`Quinze é ${a + b} e não ${2 * a + b}.`);
// "Quinze é 15 e não 20."
```

### 5.3.3 Template Literals Multilinha

Template literals preservam quebras de linha, tornando-os ideais para strings multilinhas.

```javascript
let poema = `
  Roses are red,
  Violets are blue,
  JavaScript is awesome,
  And so are you!
`;
console.log(poema);
```

## 5.4 Comparação entre Concatenação e Interpolação

Interpolação com template literals geralmente resulta em código mais legível e fácil de manter, especialmente para strings complexas.

```javascript
// Concatenação
let html = '<div class="' + classe + '">' +
           '<p>' + texto + '</p>' +
           '</div>';

// Interpolação
let html = `
  <div class="${classe}">
    <p>${texto}</p>
  </div>
`;
```

## 5.5 Performance

Para operações simples, a diferença de performance entre concatenação e interpolação é geralmente insignificante. Para concatenações em larga escala, considere usar `Array.join()` ou `StringBuilder` em ambientes que os suportem.

## Questionário

1. O que é concatenação de strings em JavaScript?

   Resposta: Concatenação de strings é o processo de combinar duas ou mais strings em uma única string.

   Justificativa: Esta é a definição básica de concatenação de strings, uma operação fundamental em programação para manipulação de texto.

2. Verdadeiro ou Falso: O operador += pode ser usado para concatenar strings em JavaScript.

   Resposta: Verdadeiro.

   Justificativa: O operador += é uma forma abreviada de concatenar e atribuir strings em uma única operação. Por exemplo, `str += "texto"` é equivalente a `str = str + "texto"`.

3. Qual será o output do seguinte código?
   ```javascript
   let a = "5";
   let b = 2;
   console.log(a + b);
   ```
   a) 7
   b) "52"
   c) "5 2"
   d) Error

   Resposta: b) "52"

   Justificativa: Quando o operador + é usado com uma string e um número, o número é convertido para string e ocorre uma concatenação, não uma adição numérica.

4. Como você pode usar o método `concat()` para combinar três strings?

   Resposta: Você pode usar o método `concat()` para combinar três strings da seguinte forma:
   ```javascript
   let resultado = string1.concat(string2, string3);
   ```

   Justificativa: O método `concat()` pode aceitar múltiplos argumentos, permitindo concatenar várias strings em uma única chamada.

5. O que são template literals em JavaScript e como eles são declarados?

   Resposta: Template literals são uma forma de criar strings que permitem interpolação de expressões e strings multilinhas. Eles são declarados usando backticks (`) ao invés de aspas simples ou duplas. Por exemplo:
   ```javascript
   let nome = "Alice";
   let saudacao = `Olá, ${nome}!`;
   ```

   Justificativa: Template literals foram introduzidos no ES6 e oferecem uma sintaxe mais flexível e poderosa para criar strings, especialmente quando se trata de incorporar valores dinâmicos.

6. O que o seguinte código irá imprimir?
   ```javascript
   let x = 10;
   let y = 20;
   console.log(`A soma de ${x} e ${y} é ${x + y}`);
   ```

   Resposta: A soma de 10 e 20 é 30

   Justificativa: Este código demonstra a interpolação de strings usando template literals. As expressões dentro de ${} são avaliadas e seus resultados são inseridos na string.

7. Verdadeiro ou Falso: Template literals sempre resultam em strings multilinhas.

   Resposta: Falso.

   Justificativa: Embora template literals possam ser usados para criar strings multilinhas facilmente, eles não necessariamente resultam em strings multilinhas. Você pode usar template literals para strings de uma única linha também.

8. Como você pode incluir aspas duplas dentro de uma string sem usar escape characters?

   Resposta: Você pode incluir aspas duplas dentro de uma string sem usar escape characters de duas maneiras:
   1. Usando aspas simples para delimitar a string: `let str = 'Ele disse "Olá"';`
   2. Usando template literals: ``let str = `Ele disse "Olá"`;``

   Justificativa: Ambos os métodos permitem incluir aspas duplas diretamente na string sem a necessidade de escapá-las com \.

9. Qual é a principal vantagem de usar template literals em vez de concatenação tradicional?

   Resposta: A principal vantagem de usar template literals é a capacidade de criar strings mais legíveis e fáceis de manter, especialmente quando se trata de strings complexas ou multilinhas com valores dinâmicos.

   Justificativa: Template literals permitem interpolação direta de expressões e preservam a formatação, tornando o código mais claro e reduzindo a necessidade de concatenações complexas.

10. Marque todas as afirmações verdadeiras sobre concatenação e interpolação de strings:
    [ ] Concatenação sempre resulta em melhor performance que interpolação
    [ ] Template literals permitem a execução de funções dentro de ${}
    [ ] O método concat() modifica a string original
    [ ] Interpolação com template literals é suportada em todas as versões de JavaScript

    Resposta: A única afirmação verdadeira é:
    - Template literals permitem a execução de funções dentro de ${}

    Justificativa: A performance depende do caso específico, concat() não modifica a string original, e template literals foram introduzidos no ES6, não sendo suportados em versões mais antigas de JavaScript.

11. Como você pode criar uma string multilinha usando concatenação tradicional?

    Resposta: Você pode criar uma string multilinha usando concatenação tradicional de várias maneiras:
    1. Usando o caractere de nova linha \n:
       ```javascript
       let str = "Linha 1\n" +
                 "Linha 2\n" +
                 "Linha 3";
       ```
    2. Usando operador de concatenação + no final de cada linha:
       ```javascript
       let str = "Linha 1" +
                 "Linha 2" +
                 "Linha 3";
       ```

    Justificativa: Ambos os métodos funcionam, mas podem ser menos legíveis e mais propensos a erros comparados com template literals para strings multilinhas.

12. O que acontece se você tentar interpolar uma variável não definida em um template literal?

    Resposta: Se você tentar interpolar uma variável não definida em um template literal, o resultado será a string "undefined".

    Exemplo:
    ```javascript
    let name;
    console.log(`Olá, ${name}!`); // "Olá, undefined!"
    ```

    Justificativa: JavaScript não lança um erro neste caso, mas trata a variável não definida como se seu valor fosse undefined e o converte para string.

13. Verdadeiro ou Falso: O método `concat()` é geralmente mais eficiente que o operador + para concatenar muitas strings.

    Resposta: Falso.

    Justificativa: Na maioria dos casos, o operador + é otimizado pelos engines JavaScript modernos e pode ser tão ou mais eficiente que `concat()`. Para concatenações em larga escala, métodos como `Array.join()` ou uso de um StringBuilder (em ambientes que o suportem) podem ser mais eficientes.

14. O que o seguinte código irá imprimir?
    ```javascript
    let obj = { x: 5, y: 10 };
    console.log(`${obj}`);
    ```
    a) { x: 5, y: 10 }
    b) [object Object]
    c) undefined
    d) Error

    Resposta: b) [object Object]

    Justificativa: Quando um objeto é interpolado em um template literal, JavaScript automaticamente chama o método `toString()` do objeto, que por padrão retorna "[object Object]" para objetos regulares.

15. Como você pode incluir uma expressão ternária dentro de um template literal?

    Resposta: Você pode incluir uma expressão ternária dentro de um template literal da seguinte forma:
    ```javascript
    let idade = 20;
    console.log(`Você é ${idade >= 18 ? 'maior' : 'menor'} de idade.`);
    ```

    Justificativa: Expressões ternárias são expressões válidas em JavaScript e podem ser usadas dentro de ${} em template literals, permitindo lógica condicional inline.

16. Associe os métodos/operadores com suas descrições:
    1. +           A. Método que retorna uma nova string combinando duas ou mais strings
    2. +=          B. Usado para delimitar template literals
    3. concat()    C. Operador de concatenação de strings
    4. `           D. Operador de concatenação e atribuição

    Resposta: 1-C, 2-D, 3-A, 4-B

    Justificativa: Cada operador ou método tem uma função específica na concatenação ou interpolação de strings.

17. O que acontece se você usar template literals com uma string que contém ${}?

    Resposta: Se você usar template literals com uma string que contém ${}, o conteúdo dentro de ${} será tratado como uma expressão JavaScript e avaliado. Se você quiser que ${} apareça literalmente na string, você precisa escapar o $ usando \${}. Exemplo:

    ```javascript
    console.log(`O valor é: ${10}`);  // "O valor é: 10"
    console.log(`Use \${} para interpolação`);  // "Use ${} para interpolação"
    ```

    Justificativa: Esta é uma característica importante dos template literals que permite tanto interpolação quanto a inclusão literal de ${} quando necessário.

18. Como você pode usar template literals para criar HTML dinâmico?

    Resposta: Você pode usar template literals para criar HTML dinâmico incorporando variáveis e expressões diretamente na string HTML. Por exemplo:

    ```javascript
    let nome = "Alice";
    let idade = 30;
    let html = `
      <div class="perfil">
        <h2>${nome}</h2>
        <p>Idade: ${idade}</p>
        <p>Status: ${idade >= 18 ? 'Adulto' : 'Menor'}</p>
      </div>
    `;
    ```

    Justificativa: Template literals são particularmente úteis para criar strings HTML dinâmicas, pois preservam a formatação e permitem fácil interpolação de valores e lógica.

19. Verdadeiro ou Falso: Template literals podem conter expressões de múltiplas linhas.

    Resposta: Verdadeiro.

    Justificativa: Template literals podem conter expressões de múltiplas linhas dentro de ${}. Isso permite incluir lógica mais complexa ou até mesmo funções dentro da interpolação.

20. O que o seguinte código irá imprimir?
    ```javascript
    function upper(strings, ...values) {
      return strings.reduce((result, string, i) => 
        result + string + (values[i] ? values[i].toUpperCase() : ''), '');
    }
    let nome = "alice";
    console.log(upper`Olá, ${nome}!`);
    ```
    a) Olá, alice!
    b) Olá, ALICE!
    c) OLÁ, ALICE!
    d) Error

    Resposta: b) Olá, ALICE!

    Justificativa: Este código demonstra o uso de tagged template literals. A função `upper` é uma tag que processa o template literal, convertendo os valores interpolados para maiúsculas, mas mantendo o restante da string inalterado.

