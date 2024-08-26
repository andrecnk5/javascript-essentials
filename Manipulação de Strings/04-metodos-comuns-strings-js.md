# 4. Métodos Comuns de Strings em JavaScript

## 4.1 Introdução aos Métodos de Strings

JavaScript fornece uma variedade de métodos embutidos para manipular strings. Esses métodos permitem realizar operações comuns como busca, extração, modificação e formatação de strings.

## 4.2 Métodos de Transformação

### 4.2.1 toLowerCase() e toUpperCase()

Estes métodos transformam a string para minúsculas ou maiúsculas, respectivamente.

```javascript
let str = "Hello, World!";
console.log(str.toLowerCase()); // "hello, world!"
console.log(str.toUpperCase()); // "HELLO, WORLD!"
```

### 4.2.2 trim(), trimStart(), e trimEnd()

Estes métodos removem espaços em branco do início e/ou fim da string.

```javascript
let str = "   Hello, World!   ";
console.log(str.trim());      // "Hello, World!"
console.log(str.trimStart()); // "Hello, World!   "
console.log(str.trimEnd());   // "   Hello, World!"
```

## 4.3 Métodos de Acesso e Busca

### 4.3.1 charAt() e charCodeAt()

`charAt(index)` retorna o caractere na posição especificada, enquanto `charCodeAt(index)` retorna o código Unicode desse caractere.

```javascript
let str = "Hello";
console.log(str.charAt(1));     // "e"
console.log(str.charCodeAt(1)); // 101
```

### 4.3.2 indexOf() e lastIndexOf()

Estes métodos buscam uma substring e retornam sua posição (ou -1 se não encontrada).

```javascript
let str = "Hello, Hello, World!";
console.log(str.indexOf("Hello"));     // 0
console.log(str.lastIndexOf("Hello")); // 7
```

## 4.4 Métodos de Extração

### 4.4.1 slice() e substring()

Estes métodos extraem uma parte da string.

```javascript
let str = "Hello, World!";
console.log(str.slice(7, 12));    // "World"
console.log(str.substring(7, 12)); // "World"
```

### 4.4.2 substr() (deprecated)

Este método extrai uma parte da string, começando em um índice especificado e extraindo um número especificado de caracteres.

```javascript
let str = "Hello, World!";
console.log(str.substr(7, 5)); // "World"
```

## 4.5 Métodos de Substituição

### 4.5.1 replace() e replaceAll()

`replace()` substitui a primeira ocorrência de uma substring, enquanto `replaceAll()` substitui todas as ocorrências.

```javascript
let str = "Hello, Hello, World!";
console.log(str.replace("Hello", "Hi"));     // "Hi, Hello, World!"
console.log(str.replaceAll("Hello", "Hi"));  // "Hi, Hi, World!"
```

## 4.6 Método de Divisão

### 4.6.1 split()

Este método divide uma string em um array de substrings.

```javascript
let str = "apple,banana,orange";
console.log(str.split(",")); // ["apple", "banana", "orange"]
```

## 4.7 Métodos de Verificação

### 4.7.1 includes(), startsWith(), e endsWith()

Estes métodos verificam se uma string contém, começa com, ou termina com uma determinada substring.

```javascript
let str = "Hello, World!";
console.log(str.includes("World"));   // true
console.log(str.startsWith("Hello")); // true
console.log(str.endsWith("!"));       // true
```

## 4.8 Método de Repetição

### 4.8.1 repeat()

Este método retorna uma nova string com um número especificado de cópias da string original.

```javascript
let str = "Ha";
console.log(str.repeat(3)); // "HaHaHa"
```

## Questionário

1. O que o método `toLowerCase()` faz em uma string?

   Resposta: O método `toLowerCase()` retorna uma nova string com todos os caracteres convertidos para minúsculas.

   Justificativa: Este método é útil para normalizar strings para comparações sem distinção entre maiúsculas e minúsculas.

2. Verdadeiro ou Falso: O método `trim()` remove todos os espaços em branco de uma string, incluindo os espaços entre palavras.

   Resposta: Falso.

   Justificativa: O método `trim()` remove apenas os espaços em branco do início e do fim da string, não afetando os espaços entre palavras.

3. Qual será o output do seguinte código?
   ```javascript
   let str = "JavaScript";
   console.log(str.charAt(4));
   ```
   a) "S"
   b) "s"
   c) "a"
   d) undefined

   Resposta: a) "S"

   Justificativa: O método `charAt(4)` retorna o caractere na posição 4 (lembrando que a indexação começa em 0), que é "S" em "JavaScript".

4. Como você pode encontrar a última ocorrência de uma substring em uma string?

   Resposta: Você pode usar o método `lastIndexOf()` para encontrar a última ocorrência de uma substring em uma string.

   Justificativa: O método `lastIndexOf()` procura da direita para a esquerda na string e retorna o índice da última ocorrência da substring especificada.

5. Qual é a diferença entre os métodos `slice()` e `substring()`?

   Resposta: A principal diferença é que `slice()` aceita índices negativos (que contam a partir do final da string), enquanto `substring()` trata índices negativos como 0. Além disso, se o segundo argumento for menor que o primeiro, `substring()` troca os dois argumentos, enquanto `slice()` retorna uma string vazia.

   Justificativa: Essas diferenças podem levar a comportamentos diferentes em certos casos, embora para uso básico ambos os métodos funcionem de maneira similar.

6. O que o método `replace()` faz quando há múltiplas ocorrências da substring a ser substituída?

   Resposta: O método `replace()` substitui apenas a primeira ocorrência da substring especificada.

   Justificativa: Para substituir todas as ocorrências, você precisa usar `replaceAll()` ou uma expressão regular com o flag global.

7. Verdadeiro ou Falso: O método `split()` sempre retorna um array.

   Resposta: Verdadeiro.

   Justificativa: O método `split()` sempre retorna um array, mesmo quando a string não contém o separador especificado (neste caso, retorna um array com a string original como único elemento).

8. O que o seguinte código irá imprimir?
   ```javascript
   let str = "Hello, World!";
   console.log(str.includes("world"));
   ```
   a) true
   b) false
   c) undefined
   d) Error

   Resposta: b) false

   Justificativa: O método `includes()` é case-sensitive. "world" (em minúsculas) não está presente na string "Hello, World!" (que tem "World" com W maiúsculo).

9. Como você pode verificar se uma string começa com uma determinada substring?

   Resposta: Você pode usar o método `startsWith()` para verificar se uma string começa com uma determinada substring.

   Justificativa: O método `startsWith()` retorna `true` se a string começa com a substring especificada, e `false` caso contrário.

10. Marque todas as afirmações verdadeiras sobre o método `repeat()`:
    [ ] Retorna uma nova string
    [ ] Modifica a string original
    [ ] Aceita números decimais como argumento
    [ ] Lança um erro se o argumento for negativo

    Resposta: As afirmações verdadeiras são:
    - Retorna uma nova string
    - Lança um erro se o argumento for negativo

    Justificativa: `repeat()` cria e retorna uma nova string, não modifica a original. Ele não aceita números decimais e lança um erro para argumentos negativos.

11. O que o método `charCodeAt()` retorna?

    Resposta: O método `charCodeAt()` retorna um número que representa o valor Unicode do caractere no índice especificado.

    Justificativa: Este método é útil quando você precisa trabalhar com os valores numéricos dos caracteres, como em algoritmos de criptografia ou processamento de texto avançado.

12. Como você pode converter uma string em um array de caracteres?

    Resposta: Você pode converter uma string em um array de caracteres usando o método `split()` com uma string vazia como argumento, ou usando o operador spread (...). Por exemplo:

    ```javascript
    let str = "hello";
    let arr1 = str.split('');
    let arr2 = [...str];
    console.log(arr1); // ['h', 'e', 'l', 'l', 'o']
    console.log(arr2); // ['h', 'e', 'l', 'l', 'o']
    ```

    Justificativa: Ambos os métodos são eficazes para converter uma string em um array de seus caracteres individuais.

13. Verdadeiro ou Falso: O método `toUpperCase()` modifica a string original.

    Resposta: Falso.

    Justificativa: Como strings são imutáveis em JavaScript, `toUpperCase()` (assim como outros métodos de string) não modifica a string original, mas retorna uma nova string.

14. O que o seguinte código irá imprimir?
    ```javascript
    let str = "   Hello, World!   ";
    console.log(str.trimStart().length);
    ```
    a) 13
    b) 16
    c) 18
    d) 15

    Resposta: b) 16

    Justificativa: `trimStart()` remove os espaços no início da string, mas mantém os espaços no final. Então a string resultante é "Hello, World!   ", que tem 16 caracteres.

15. Como você pode substituir todas as ocorrências de uma substring em uma string?

    Resposta: Você pode substituir todas as ocorrências de uma substring em uma string usando o método `replaceAll()` ou usando uma expressão regular com o flag global com o método `replace()`. Por exemplo:

    ```javascript
    let str = "Hello, Hello, World!";
    console.log(str.replaceAll("Hello", "Hi")); // "Hi, Hi, World!"
    // ou
    console.log(str.replace(/Hello/g, "Hi")); // "Hi, Hi, World!"
    ```

    Justificativa: `replaceAll()` é um método mais recente e mais direto, enquanto o uso de expressões regulares com `replace()` é uma técnica mais antiga mas ainda amplamente utilizada.

16. Associe os métodos com suas descrições:
    1. indexOf()    A. Retorna uma parte da string
    2. substr()     B. Divide a string em um array
    3. slice()      C. Encontra a posição de uma substring
    4. split()      D. Extrai caracteres a partir de uma posição

    Resposta: 1-C, 2-D, 3-A, 4-B

    Justificativa: Cada método tem uma função específica na manipulação de strings.

17. O que acontece se você passar um número negativo para o método `repeat()`?

    Resposta: Se você passar um número negativo para o método `repeat()`, ele lançará um RangeError.

    Justificativa: O método `repeat()` espera um número não-negativo como argumento. Números negativos não fazem sentido no contexto de repetição de strings.

18. Como você pode verificar se uma string termina com uma determinada substring?

    Resposta: Você pode usar o método `endsWith()` para verificar se uma string termina com uma determinada substring. Por exemplo:

    ```javascript
    let str = "Hello, World!";
    console.log(str.endsWith("World!")); // true
    ```

    Justificativa: O método `endsWith()` retorna `true` se a string termina com a substring especificada, e `false` caso contrário.

19. Verdadeiro ou Falso: O método `substring()` pode aceitar argumentos negativos.

    Resposta: Falso.

    Justificativa: Diferente de `slice()`, o método `substring()` trata argumentos negativos como 0. Se você precisa usar índices negativos, `slice()` é a escolha mais apropriada.

20. O que o seguinte código irá imprimir?
    ```javascript
    let str = "JavaScript";
    console.log(str.substring(4, 2));
    ```
    a) "va"
    b) "aS"
    c) "Sc"
    d) ""

    Resposta: b) "aS"

    Justificativa: Quando o segundo argumento de `substring()` é menor que o primeiro, o método troca os argumentos. Então `str.substring(4, 2)` é equivalente a `str.substring(2, 4)`, que retorna "aS".

