# 8. Comparação de Strings em JavaScript

## 8.1 Introdução à Comparação de Strings

A comparação de strings é uma operação fundamental em programação, especialmente em tarefas como ordenação, busca e validação de entrada do usuário. Em JavaScript, existem várias maneiras de comparar strings, cada uma com suas próprias características e casos de uso.

## 8.2 Operadores de Comparação

JavaScript fornece operadores de comparação que podem ser usados com strings.

### 8.2.1 Igualdade (== e ===)

```javascript
console.log("hello" == "hello");  // true
console.log("Hello" == "hello");  // false
console.log("5" == 5);            // true
console.log("5" === 5);           // false
```

O operador `==` realiza coerção de tipo, enquanto `===` compara sem coerção.

### 8.2.2 Desigualdade (!= e !==)

```javascript
console.log("hello" != "world");  // true
console.log("5" !== 5);           // true
```

### 8.2.3 Maior que (>), Menor que (<), Maior ou igual (>=), Menor ou igual (<=)

```javascript
console.log("apple" < "banana");  // true
console.log("Zebra" < "alphabet"); // true (comparação lexicográfica)
```

Estes operadores comparam strings lexicograficamente, baseado nos valores Unicode dos caracteres.

## 8.3 Método localeCompare()

O método `localeCompare()` oferece uma comparação que respeita as regras de ordenação específicas do idioma.

```javascript
console.log("á".localeCompare("b", "pt"));  // -1 (á vem antes de b em português)
console.log("ä".localeCompare("z", "de"));  // -1 (ä vem antes de z em alemão)
```

## 8.4 Comparação Case-Insensitive

Para comparar strings ignorando maiúsculas e minúsculas, você pode converter ambas para o mesmo caso antes da comparação.

```javascript
let str1 = "Hello";
let str2 = "hello";
console.log(str1.toLowerCase() === str2.toLowerCase());  // true
```

## 8.5 Comparação de Substrings

O método `startsWith()`, `endsWith()`, e `includes()` são úteis para comparar partes de strings.

```javascript
let str = "Hello, World!";
console.log(str.startsWith("Hello"));  // true
console.log(str.endsWith("World!"));   // true
console.log(str.includes("o, Wo"));    // true
```

## 8.6 Comparação com Expressões Regulares

Expressões regulares oferecem uma maneira poderosa de comparar padrões em strings.

```javascript
let pattern = /^[A-Z][a-z]*$/;
console.log(pattern.test("Hello"));  // true
console.log(pattern.test("hello"));  // false
```

## 8.7 Comparação de Strings Unicode

Ao comparar strings com caracteres Unicode, é importante considerar a normalização.

```javascript
console.log("café" === "café");  // pode ser false dependendo da representação Unicode
console.log("café".normalize() === "café".normalize());  // sempre true
```

## 8.8 Considerações de Performance

Para comparações simples, os operadores de comparação são geralmente mais rápidos. Para comparações mais complexas ou específicas do idioma, métodos como `localeCompare()` são mais apropriados, mas podem ser mais lentos.

## Questionário

1. O que o operador `===` faz ao comparar strings em JavaScript?

   Resposta: O operador `===` compara strings em JavaScript verificando se elas são exatamente iguais, incluindo o tipo e o conteúdo, sem realizar nenhuma coerção de tipo.

   Justificativa: Este é o operador de igualdade estrita em JavaScript, que compara tanto o valor quanto o tipo dos operandos.

2. Verdadeiro ou Falso: A comparação de strings em JavaScript é sempre case-sensitive.

   Resposta: Verdadeiro.

   Justificativa: Por padrão, as comparações de strings em JavaScript são case-sensitive. "Hello" e "hello" são consideradas strings diferentes.

3. O que o seguinte código irá imprimir?
   ```javascript
   console.log("apple" < "banana");
   ```
   a) true
   b) false
   c) undefined
   d) Error

   Resposta: a) true

   Justificativa: As strings são comparadas lexicograficamente, e "apple" vem antes de "banana" na ordem alfabética.

4. Como você pode realizar uma comparação de strings case-insensitive em JavaScript?

   Resposta: Para realizar uma comparação de strings case-insensitive em JavaScript, você pode converter ambas as strings para o mesmo caso (geralmente minúsculas) antes de compará-las. Por exemplo:

   ```javascript
   let str1 = "Hello";
   let str2 = "hello";
   if (str1.toLowerCase() === str2.toLowerCase()) {
       console.log("As strings são iguais (ignorando maiúsculas/minúsculas)");
   }
   ```

   Justificativa: Converter ambas as strings para minúsculas (ou maiúsculas) antes da comparação elimina as diferenças de caso.

5. Qual é a principal diferença entre os operadores `==` e `===` ao comparar strings?

   Resposta: A principal diferença é que `==` realiza coerção de tipo antes da comparação, enquanto `===` não realiza coerção de tipo.

   Justificativa: Isso significa que `"5" == 5` retornará `true`, mas `"5" === 5` retornará `false`.

6. O que o método `localeCompare()` faz e quando é útil?

   Resposta: O método `localeCompare()` compara strings levando em consideração as regras de ordenação específicas do idioma. É útil quando você precisa comparar strings de uma maneira que respeite as convenções linguísticas, como a ordenação de caracteres acentuados.

   Justificativa: Este método é especialmente importante em aplicações multilíngues onde a ordem alfabética pode variar dependendo do idioma.

7. Verdadeiro ou Falso: O método `includes()` retorna a posição onde a substring é encontrada.

   Resposta: Falso.

   Justificativa: O método `includes()` retorna um booleano indicando se a substring está presente ou não. Para obter a posição, você deve usar o método `indexOf()`.

8. Como você pode verificar se uma string começa com uma determinada substring?

   Resposta: Você pode usar o método `startsWith()` para verificar se uma string começa com uma determinada substring. Por exemplo:

   ```javascript
   let str = "Hello, World!";
   console.log(str.startsWith("Hello"));  // true
   ```

   Justificativa: O método `startsWith()` é uma maneira concisa e legível de verificar o início de uma string.

9. O que acontece quando você compara strings com caracteres Unicode?

   Resposta: Ao comparar strings com caracteres Unicode, a comparação é feita com base nos valores dos pontos de código Unicode dos caracteres. Isso pode levar a resultados inesperados se as strings não estiverem normalizadas.

   Justificativa: Diferentes representações Unicode do mesmo caractere visual podem ser consideradas diferentes em uma comparação direta.

10. Marque todas as afirmações verdadeiras sobre comparação de strings em JavaScript:
    [ ] Strings são sempre comparadas byte a byte
    [ ] A comparação de strings é sempre sensível a maiúsculas e minúsculas
    [ ] O método `localeCompare()` sempre retorna -1, 0 ou 1
    [ ] Expressões regulares podem ser usadas para comparações complexas de strings

    Resposta: As afirmações verdadeiras são:
    - A comparação de strings é sempre sensível a maiúsculas e minúsculas
    - Expressões regulares podem ser usadas para comparações complexas de strings

    Justificativa: Strings não são sempre comparadas byte a byte (especialmente com caracteres Unicode), e `localeCompare()` pode retornar outros números além de -1, 0 e 1 em algumas implementações.

11. Como você pode comparar strings ignorando os acentos?

    Resposta: Para comparar strings ignorando os acentos, você pode usar uma combinação de normalização Unicode e remoção de diacríticos. Uma abordagem é:

    ```javascript
    function compareWithoutAccents(str1, str2) {
        return str1.normalize("NFD").replace(/[\u0300-\u036f]/g, "") === 
               str2.normalize("NFD").replace(/[\u0300-\u036f]/g, "");
    }
    ```

    Justificativa: Esta função normaliza as strings e remove os caracteres diacríticos antes da comparação.

12. O que o método `endsWith()` faz e como ele difere de `includes()`?

    Resposta: O método `endsWith()` verifica se uma string termina com uma determinada substring, enquanto `includes()` verifica se a substring está presente em qualquer parte da string.

    Exemplo:
    ```javascript
    let str = "Hello, World!";
    console.log(str.endsWith("World!"));  // true
    console.log(str.includes("World"));   // true
    console.log(str.endsWith("Hello"));   // false
    ```

    Justificativa: `endsWith()` é mais específico, verificando apenas o final da string, enquanto `includes()` procura em toda a string.

13. Verdadeiro ou Falso: A comparação de strings em JavaScript é sempre baseada na tabela ASCII.

    Resposta: Falso.

    Justificativa: JavaScript usa Unicode para representar strings, não ASCII. Isso significa que a comparação de strings leva em conta caracteres de todos os idiomas e símbolos suportados pelo Unicode.

14. O que o seguinte código irá imprimir?
    ```javascript
    console.log("2" > "10");
    ```
    a) true
    b) false
    c) undefined
    d) Error

    Resposta: a) true

    Justificativa: Quando strings são comparadas com operadores como `>`, a comparação é feita lexicograficamente. "2" vem depois de "1" na ordem lexicográfica, então "2" é considerado "maior" que "10".

15. Como você pode usar expressões regulares para comparar strings em JavaScript?

    Resposta: Você pode usar expressões regulares para comparar strings em JavaScript usando o método `test()` do objeto RegExp ou o método `match()` da string. Por exemplo:

    ```javascript
    let pattern = /^[A-Z][a-z]+$/;
    console.log(pattern.test("Hello"));  // true
    console.log("Hello".match(pattern)); // ["Hello"]
    ```

    Justificativa: Expressões regulares oferecem uma maneira poderosa e flexível de comparar padrões em strings.

16. Associe os métodos com suas descrições:
    1. startsWith()    A. Verifica se a string termina com uma substring
    2. endsWith()      B. Compara strings respeitando regras de idioma
    3. includes()      C. Verifica se a string começa com uma substring
    4. localeCompare() D. Verifica se a string contém uma substring

    Resposta: 1-C, 2-A, 3-D, 4-B

    Justificativa: Cada método tem uma função específica na comparação ou busca de strings.

17. Como a normalização Unicode afeta a comparação de strings?

    Resposta: A normalização Unicode garante que strings que parecem idênticas visualmente sejam tratadas como iguais na comparação, mesmo que tenham representações internas diferentes. Por exemplo:

    ```javascript
    let a = "café";  // 'é' como um único caractere
    let b = "cafe\u0301";  // 'e' seguido de um acento agudo combinante
    console.log(a === b);  // false
    console.log(a.normalize() === b.normalize());  // true
    ```

    Justificativa: A normalização é crucial para comparações consistentes de strings, especialmente em aplicações multilíngues.

18. Verdadeiro ou Falso: O método `localeCompare()` sempre produz o mesmo resultado em todos os ambientes JavaScript.

    Resposta: Falso.

    Justificativa: O comportamento exato de `localeCompare()` pode variar dependendo da implementação JavaScript e das configurações de localidade do sistema. É importante testar em diferentes ambientes se a consistência precisa é necessária.

19. Como você pode comparar strings numericamente em JavaScript?

    Resposta: Para comparar strings numericamente em JavaScript, você pode convertê-las para números antes da comparação. Por exemplo:

    ```javascript
    function compareNumerically(a, b) {
        return Number(a) - Number(b);
    }
    console.log(["2", "10"].sort(compareNumerically));  // ["2", "10"]
    ```

    Justificativa: Converter para números antes da comparação garante que as strings sejam tratadas como valores numéricos, não como texto.

20. O que o seguinte código irá imprimir e por quê?
    ```javascript
    console.log("a" < "A");
    ```
    a) true
    b) false
    c) undefined
    d) Error

    Resposta: b) false

    Justificativa: Na tabela Unicode, as letras maiúsculas têm valores menores que as letras minúsculas correspondentes. Portanto, "A" é considerado "menor" que "a" em uma comparação lexicográfica.

