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

2. Verdadeiro ou Falso: Há uma diferença funcional significativa entre usar aspas simples e aspas duplas para criar strings em JavaScript.

3. O que o seguinte código irá imprimir?
   ```javascript
   let nome = "Alice";
   console.log(`Olá, ${nome}!`);
   ```
   a) Olá, ${nome}!
   b) Olá, Alice!
   c) Olá, "Alice"!
   d) Error

4. Como você pode criar uma string multilinha em JavaScript?

5. Qual é a diferença entre `new String("texto")` e `String("texto")`?

6. O que o seguinte código irá imprimir?
   ```javascript
   console.log("2" + 2);
   ```
   a) 4
   b) "22"
   c) 22
   d) Error

7. Como você incluiria uma aspa dupla dentro de uma string delimitada por aspas duplas?

8. Verdadeiro ou Falso: Template literals sempre resultam em strings multilinhas.

9. O que o seguinte código irá imprimir?
   ```javascript
   let a = 5;
   let b = 10;
   console.log(`Quinze é ${a + b} e não ${2 * a + b}.`);
   ```
10. Marque todas as afirmações verdadeiras sobre a criação de strings em JavaScript:
    [ ] Strings criadas com aspas simples e duplas são funcionalmente idênticas
    [ ] Template literals só podem ser usados para interpolação de strings
    [ ] O construtor String() sempre cria um objeto String
    [ ] Você pode usar \n para inserir uma nova linha em qualquer tipo de string literal

11. Como você pode incluir um caractere de tabulação em uma string?

12. O que é interpolação de string e como ela é realizada em JavaScript?

13. Verdadeiro ou Falso: JavaScript suporta caracteres Unicode em strings.

14. Como você criaria uma string contendo aspas simples e duplas?

15. O que o seguinte código irá imprimir?
    ```javascript
    console.log("Line 1\nLine 2");
    ```
    a) Line 1\nLine 2
    b) Line 1
       Line 2
    c) Line 1/nLine 2
    d) Error

16. Associe os métodos de criação de string com suas descrições:
    1. 'texto'          A. Permite interpolação e strings multilinhas
    2. "texto"          B. Cria um objeto String
    3. `texto`          C. Cria uma string primitiva
    4. new String()     D. Cria uma string primitiva

17. Como você pode verificar se uma variável contém uma string primitiva ou um objeto String?

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

19. Verdadeiro ou Falso: Em JavaScript, strings criadas com o construtor String() sem 'new' são sempre objetos.

20. Como você pode criar uma string contendo caracteres que não estão no seu teclado?
