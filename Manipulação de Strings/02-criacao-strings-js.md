# 2. Criação de Strings em JavaScript

## 2.1 Métodos de Criação de Strings

Em JavaScript, existem várias maneiras de criar strings. Vamos explorar cada uma delas em detalhes.

### 2.1.1 Literais de String

Os literais de string são a forma mais comum e direta de criar strings em JavaScript.

1. Aspas Simples:
```javascript
let saudacao = 'Olá, mundo!';
```

2. Aspas Duplas:
```javascript
let mensagem = "Bem-vindo ao JavaScript!";
```

3. Template Literals (Backticks):
```javascript
let nome = "Alice";
let bemVindo = `Olá, ${nome}!`;
```

### 2.1.2 Construtor String()

Strings primitivas são simples valores e não têm métodos ou propriedades próprias. No entanto, quando você acessa um método de string, como `strPrimitive.length`, o JavaScript cria temporariamente um objeto `String` para que você possa usar métodos e propriedades. Esse objeto é descartado imediatamente após o uso.

Uma **string objeto** é criada quando você usa o construtor `new String()`. Isso cria uma instância do objeto `String`, que é mais complexo e pesado em termos de desempenho do que uma string primitiva.

Embora menos comum, você também pode criar strings usando o construtor `String()`:

```javascript
let str1 = new String("Isso é uma string objeto");
let str2 = String("Isso é uma string primitiva");
```

### Principais Diferenças

1. **Tipo de Dado**

   - **String Primitiva**: Tipo primitivo (`typeof` retorna `"string"`).
   - **String Objeto**: Tipo objeto (`typeof` retorna `"object"`).

   ```js
   let strPrimitive = "Hello";
   let strObject = new String("Hello");
   
   console.log(typeof strPrimitive); // "string"
   console.log(typeof strObject);    // "object"
   ```

2. **Comparação de Valores**

   - **String Primitiva**: Comparações de igualdade (`==` ou `===`) funcionam como esperado, comparando valores.
   - **String Objeto**: Comparações de igualdade com `===` ou `==` entre objetos `String` retornam `false`, a menos que sejam exatamente o mesmo objeto, porque objetos são comparados por referência, não por valor.

   ```js
   let strPrimitive1 = "Hello";
   let strPrimitive2 = "Hello";
   
   let strObject1 = new String("Hello");
   let strObject2 = new String("Hello");
   
   console.log(strPrimitive1 === strPrimitive2); // true (valores são iguais)
   console.log(strObject1 === strObject2);       // false (objetos diferentes)
   console.log(strObject1 == strObject2);        // false (mesmo com ==)
   ```

   Porém, uma comparação entre uma string primitiva e um objeto `String` pode funcionar como esperado em algumas situações devido à coerção de tipos.

   ```js
   console.log(strPrimitive1 == strObject1); // true (JavaScript converte para primitivo)
   ```

3. **Performance**

   - **String Primitiva**: Leve e rápida. Ideal para a maioria dos casos em que você trabalha com texto.
   - **String Objeto**: Mais pesado e desnecessário na maioria dos casos. Use apenas se realmente precisar das propriedades de um objeto.

## 2.2 Diferenças e Quando Usar Cada Método

### 2.2.1 Aspas Simples vs. Aspas Duplas

Funcionalmente, não há diferença entre usar aspas simples e duplas. A escolha geralmente é uma questão de preferência pessoal ou convenção de estilo de código.

```javascript
let aspasSimples = 'JavaScript';
let aspasDuplas = "JavaScript";
console.log(aspasSimples === aspasDuplas); // true
```

Uma vantagem prática: se sua string contém aspas, você pode usar o outro tipo para evitar o escape:

```javascript
let citacao1 = "Ele disse 'Olá'";
let citacao2 = 'Ela respondeu "Oi"';
```

### 2.2.2 Template Literals

Template literals oferecem mais flexibilidade:

1. Interpolação de Strings:
```javascript
let nome = "Bob";
let idade = 30;
console.log(`${nome} tem ${idade} anos.`);
```

2. Strings Multilinhas:
```javascript
let poema = `
  Roses are red,
  Violets are blue,
  JavaScript is awesome,
  And so are you!
`;
```

3. Expressões em Templates:
```javascript
console.log(`2 + 2 = ${2 + 2}`);
```

### 2.2.3 Construtor String()

O construtor `String()` é útil quando você precisa converter explicitamente um valor em uma string:

```javascript
let num = 42;
let strNum = String(num); // "42"
```

## 2.3 Caracteres Especiais e Escape

Às vezes, você precisa incluir caracteres especiais em suas strings:

```javascript
let newLine = "Primeira linha\nSegunda linha";
let tab = "Coluna1\tColuna2";
let backslash = "Isso é uma barra invertida: \\";
```

## 2.4 Strings Unicode

JavaScript suporta caracteres Unicode, permitindo criar strings com caracteres de qualquer idioma:

```javascript
let saudacaoJapones = "こんにちは"; // "Olá" em japonês
let emoji = "😊";
```

## Questionário

1. Quais são os três principais métodos de criar strings literais em JavaScript?

   Resposta: Os três principais métodos de criar strings literais em JavaScript são:
   1. Usando aspas simples: 'string'
   2. Usando aspas duplas: "string"
   3. Usando template literals (backticks): `string`

   Justificativa: Estes são os três métodos padrão para criar strings literais em JavaScript, cada um com suas próprias características e casos de uso.

2. Verdadeiro ou Falso: Há uma diferença funcional significativa entre usar aspas simples e aspas duplas para criar strings em JavaScript.

   Resposta: Falso.

   Justificativa: Não há diferença funcional significativa entre usar aspas simples e aspas duplas para criar strings em JavaScript. A escolha entre elas é geralmente uma questão de preferência pessoal ou convenção de estilo de código.

3. O que o seguinte código irá imprimir?
   ```javascript
   let nome = "Alice";
   console.log(`Olá, ${nome}!`);
   ```
   a) Olá, ${nome}!
   b) Olá, Alice!
   c) Olá, "Alice"!
   d) Error

   Resposta: b) Olá, Alice!

   Justificativa: Este código usa um template literal (backticks), que permite a interpolação de strings. A expressão `${nome}` é avaliada e substituída pelo valor da variável `nome`.

4. Como você pode criar uma string multilinha em JavaScript?

   Resposta: Você pode criar uma string multilinha em JavaScript usando template literals (backticks). Por exemplo:

   ```javascript
   let multiline = `
     Esta é uma
     string de
     múltiplas linhas
   `;
   ```

   Justificativa: Template literals preservam quebras de linha, tornando-os ideais para criar strings multilinhas de forma legível.

5. Qual é a diferença entre `new String("texto")` e `String("texto")`?

   Resposta: `new String("texto")` cria um objeto String, enquanto `String("texto")` cria uma string primitiva.

   Justificativa: O construtor `String` quando usado com `new` cria um objeto wrapper String, que é diferente de uma string primitiva. Sem `new`, `String()` funciona como uma função de conversão, retornando uma string primitiva.

6. O que o seguinte código irá imprimir?
   ```javascript
   console.log("2" + 2);
   ```
   a) 4
   b) "22"
   c) 22
   d) Error

   Resposta: b) "22"

   Justificativa: Quando o operador `+` é usado com uma string e um número, o número é convertido para string e ocorre uma concatenação, não uma adição numérica.

7. Como você incluiria uma aspa dupla dentro de uma string delimitada por aspas duplas?

   Resposta: Você pode incluir uma aspa dupla dentro de uma string delimitada por aspas duplas escapando-a com uma barra invertida. Por exemplo:

   ```javascript
   let str = "Ela disse \"Olá\"";
   ```

   Justificativa: Escapar caracteres especiais com uma barra invertida (\) permite incluí-los literalmente em uma string, mesmo quando normalmente teriam um significado especial.

8. Verdadeiro ou Falso: Template literals sempre resultam em strings multilinhas.

   Resposta: Falso.

   Justificativa: Embora template literals possam ser usados para criar strings multilinhas, eles não necessariamente resultam em strings multilinhas. Você pode usar template literals para strings de uma única linha também.

9. O que o seguinte código irá imprimir?
   ```javascript
   let a = 5;
   let b = 10;
   console.log(`Quinze é ${a + b} e não ${2 * a + b}.`);
   ```

   Resposta: Quinze é 15 e não 20.

   Justificativa: Este código demonstra a capacidade dos template literals de incluir expressões JavaScript. As expressões `${a + b}` e `${2 * a + b}` são avaliadas e seus resultados são inseridos na string.

10. Marque todas as afirmações verdadeiras sobre a criação de strings em JavaScript:
    [ ] Strings criadas com aspas simples e duplas são funcionalmente idênticas
    [ ] Template literals só podem ser usados para interpolação de strings
    [ ] O construtor String() sempre cria um objeto String
    [ ] Você pode usar \n para inserir uma nova linha em qualquer tipo de string literal

    Resposta: As afirmações verdadeiras são:
    - Strings criadas com aspas simples e duplas são funcionalmente idênticas
    - Você pode usar \n para inserir uma nova linha em qualquer tipo de string literal

    Justificativa: Template literals têm mais funcionalidades além da interpolação, e o construtor String() sem 'new' cria uma string primitiva, não um objeto String.

11. Como você pode incluir um caractere de tabulação em uma string?

    Resposta: Você pode incluir um caractere de tabulação em uma string usando a sequência de escape `\t`. Por exemplo:

    ```javascript
    let tabulacao = "Coluna1\tColuna2";
    ```

    Justificativa: `\t` é uma sequência de escape reconhecida em JavaScript que representa um caractere de tabulação.

12. O que é interpolação de string e como ela é realizada em JavaScript?

    Resposta: Interpolação de string é o processo de inserir expressões dentro de strings literais. Em JavaScript, isso é realizado usando template literals (backticks) e a sintaxe ${expressão}. Por exemplo:

    ```javascript
    let nome = "Alice";
    let idade = 30;
    console.log(`${nome} tem ${idade} anos.`);
    ```

    Justificativa: A interpolação de string permite a inclusão de expressões JavaScript diretamente dentro de strings, tornando a construção de strings dinâmicas mais fácil e legível.

13. Verdadeiro ou Falso: JavaScript suporta caracteres Unicode em strings.

    Resposta: Verdadeiro.

    Justificativa: JavaScript usa UTF-16 para codificação de strings, o que permite a inclusão de caracteres Unicode, incluindo emojis e caracteres de diferentes idiomas.

14. Como você criaria uma string contendo aspas simples e duplas?

    Resposta: Você pode criar uma string contendo aspas simples e duplas de várias maneiras:

    1. Usando template literals: `` `Ela disse "Não" e ele respondeu 'Ok'` ``
    2. Usando aspas duplas e escapando as aspas duplas internas: "Ela disse \"Não\" e ele respondeu 'Ok'"
    3. Usando aspas simples e escapando as aspas simples internas: 'Ela disse "Não" e ele respondeu \'Ok\''

    Justificativa: Cada método tem suas vantagens. Template literals são os mais flexíveis, enquanto os outros métodos requerem escape de caracteres.

15. O que o seguinte código irá imprimir?
    ```javascript
    console.log("Line 1\nLine 2");
    ```
    a) Line 1\nLine 2
    b) Line 1
       Line 2
    c) Line 1/nLine 2
    d) Error

    Resposta: b) 
    Line 1
    Line 2

    Justificativa: `\n` é uma sequência de escape que representa uma nova linha. Quando a string é impressa, esta sequência é interpretada como uma quebra de linha real.

16. Associe os métodos de criação de string com suas descrições:
    1. 'texto'          A. Permite interpolação e strings multilinhas
    2. "texto"          B. Cria um objeto String
    3. `texto`          C. Cria uma string primitiva
    4. new String()     D. Cria uma string primitiva

    Resposta: 1-D, 2-D, 3-A, 4-B

    Justificativa: Aspas simples e duplas criam strings primitivas, template literals (backticks) permitem interpolação e strings multilinhas, e `new String()` cria um objeto String.

17. Como você pode verificar se uma variável contém uma string primitiva ou um objeto String?

    Resposta: Você pode usar o operador `typeof` em combinação com `instanceof`. Por exemplo:

    ```javascript
    function checkStringType(str) {
      if (typeof str === 'string') {
        return "String primitiva";
      } else if (str instanceof String) {
        return "Objeto String";
      }
      return "Não é uma string";
    }
    ```

    Justificativa: `typeof` retorna 'string' para strings primitivas, enquanto `instanceof String` é verdadeiro para objetos String.

18. O que o seguinte código irá imprimir?
    ```javascript
    let str1 = "Hello";
    let str2 = new String("Hello");
    console.log(str1 === str2);
    console.log(str1 == str2);
    ```
    a) true, true
    b) false, true
    c) true, false
    d) false, false

    Resposta: b) false, true

    Justificativa: `===` verifica igualdade estrita (valor e tipo), que é falsa porque str1 é uma string primitiva e str2 é um objeto. `==` realiza coerção de tipo, então retorna true porque os valores são iguais após a coerção.

19. Verdadeiro ou Falso: Em JavaScript, strings criadas com o construtor String() sem 'new' são sempre objetos.

    Resposta: Falso.

    Justificativa: Strings criadas com o construtor String() sem 'new' são strings primitivas, não objetos. Apenas quando usado com 'new', o construtor String cria um objeto String.

20. Como você pode criar uma string contendo caracteres que não estão no seu teclado?

    Resposta: Você pode criar uma string contendo caracteres que não estão no seu teclado de várias maneiras:

    1. Usando sequências de escape Unicode: `"\u00A9"` para o símbolo de copyright (©)
    2. Usando notação de ponto de código: `"\u{1F600}"` para um emoji de rosto sorridente (😀)
    3. Copiando e colando o caractere diretamente na string: `"©"` ou `"😀"`

    Justificativa: JavaScript suporta totalmente Unicode, permitindo a inclusão de qualquer caractere Unicode em strings, seja através de sequências de escape ou diretamente.

