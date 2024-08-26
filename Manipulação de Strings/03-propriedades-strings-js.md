# 3. Propriedades de Strings em JavaScript

## 3.1 Introdução às Propriedades de Strings

As strings em JavaScript são tratadas como objetos e, portanto, possuem propriedades e métodos associados a elas. Nesta seção, focaremos nas propriedades mais importantes das strings.

## 3.2 A Propriedade length

A propriedade mais comumente usada em strings é `length`. Esta propriedade retorna o número de caracteres na string.

Exemplo:
```javascript
let str = "Hello, World!";
console.log(str.length); // 13
```

Observações importantes:
- Espaços e pontuações são contados como caracteres.
- `length` é uma propriedade, não um método, então não usamos parênteses.

## 3.3 Acesso a Caracteres Individuais

Embora não seja estritamente uma propriedade, é importante entender como acessar caracteres individuais em uma string.

### 3.3.1 Notação de Colchetes

Você pode acessar caracteres individuais usando a notação de colchetes, como se a string fosse um array.

Exemplo:
```javascript
let str = "JavaScript";
console.log(str[0]); // "J"
console.log(str[4]); // "S"
```

Observações:
- A indexação começa em 0.
- Se você tentar acessar um índice que não existe, receberá `undefined`.

### 3.3.2 O Método charAt()

Alternativamente, você pode usar o método `charAt()` para acessar caracteres individuais.

Exemplo:
```javascript
let str = "JavaScript";
console.log(str.charAt(0)); // "J"
console.log(str.charAt(4)); // "S"
```

A diferença principal é que `charAt()` retorna uma string vazia para índices fora do intervalo, enquanto a notação de colchetes retorna `undefined`.

## 3.4 Propriedades de Strings Primitivas vs. Objetos String

É importante notar que, embora strings primitivas não sejam objetos, JavaScript as trata como objetos quando você tenta acessar suas propriedades ou métodos.

Exemplo:
```javascript
let primitiveString = "Hello";
console.log(primitiveString.length); // 5

let objectString = new String("Hello");
console.log(objectString.length); // 5
```

No primeiro caso, JavaScript temporariamente converte a string primitiva em um objeto String para acessar a propriedade `length`.

## 3.5 Imutabilidade de Strings

Uma característica importante das strings em JavaScript é que elas são imutáveis. Isso significa que, uma vez criada, uma string não pode ser modificada.

Exemplo:
```javascript
let str = "Hello";
str[0] = "h"; // Isso não produz erro, mas também não modifica a string
console.log(str); // Ainda imprime "Hello"
```

Quando você realiza operações que parecem modificar uma string, na verdade está criando uma nova string.

## Questionário

1. O que a propriedade `length` retorna em uma string?

   Resposta: A propriedade `length` retorna o número total de caracteres na string, incluindo espaços e pontuações.

   Justificativa: `length` é uma propriedade fundamental das strings em JavaScript que conta todos os caracteres, independentemente de serem letras, números, espaços ou símbolos.

2. Verdadeiro ou Falso: A indexação de caracteres em uma string JavaScript começa em 1.

   Resposta: Falso.

   Justificativa: A indexação de caracteres em strings JavaScript (assim como em arrays) começa em 0, não em 1.

3. Qual será o output do seguinte código?
   ```javascript
   let str = "JavaScript";
   console.log(str[str.length]);
   ```
   a) "t"
   b) undefined
   c) ""
   d) Error

   Resposta: b) undefined

   Justificativa: `str.length` é 10, mas o último caractere está no índice 9 (lembre-se, a indexação começa em 0). Portanto, `str[10]` está fora dos limites da string e retorna `undefined`.

4. Como você pode acessar o último caractere de uma string em JavaScript?

   Resposta: Você pode acessar o último caractere de uma string usando `str[str.length - 1]` ou `str.charAt(str.length - 1)`.

   Justificativa: Como a indexação começa em 0 e `length` dá o número total de caracteres, o último caractere está sempre no índice `length - 1`.

5. Qual é a diferença entre usar a notação de colchetes e o método `charAt()` para acessar caracteres em uma string?

   Resposta: A principal diferença é o que eles retornam quando o índice está fora dos limites da string. A notação de colchetes (`str[index]`) retorna `undefined`, enquanto `charAt(index)` retorna uma string vazia ('').

   Justificativa: Esta diferença pode ser importante em certas situações de programação, especialmente ao lidar com índices potencialmente inválidos.

6. O que acontece quando você tenta modificar um caractere em uma string usando a notação de colchetes?

   Resposta: Quando você tenta modificar um caractere em uma string usando a notação de colchetes, a operação é silenciosamente ignorada em modo não estrito. A string permanece inalterada.

   Justificativa: Isso ocorre devido à imutabilidade das strings em JavaScript. Strings não podem ser modificadas após serem criadas; operações que parecem modificá-las na verdade criam novas strings.

7. Verdadeiro ou Falso: O método `length` de uma string retorna o número de caracteres visíveis na string.

   Resposta: Falso.

   Justificativa: A propriedade `length` retorna o número total de unidades de código na string, que pode não corresponder ao número de caracteres visíveis, especialmente quando se trata de caracteres Unicode que podem ser representados por múltiplas unidades de código.

8. O que o seguinte código irá imprimir?
   ```javascript
   let str = "🚀";
   console.log(str.length);
   ```
   a) 1
   b) 2
   c) 4
   d) Error

   Resposta: b) 2

   Justificativa: Muitos emojis, incluindo o foguete (🚀), são representados por duas unidades de código UTF-16 em JavaScript. Portanto, embora visualmente seja um único caractere, `length` retorna 2.

9. Como você pode verificar se uma string está vazia em JavaScript?

   Resposta: Você pode verificar se uma string está vazia de várias maneiras:
   1. Verificando se o comprimento é zero: `str.length === 0`
   2. Comparando com uma string vazia: `str === ""` 
   3. Usando o operador lógico NOT duas vezes: `!!str` (retorna false para strings vazias)

   Justificativa: Todas essas abordagens são válidas e comumente usadas. A escolha entre elas geralmente depende do contexto e do estilo de codificação preferido.

10. Marque todas as afirmações verdadeiras sobre propriedades de strings em JavaScript:
    [ ] Strings são imutáveis em JavaScript
    [ ] A propriedade `length` de uma string pode ser modificada
    [ ] Você pode acessar caracteres individuais usando a notação de colchetes
    [ ] O método `charAt()` retorna `undefined` para índices fora dos limites

    Resposta: As afirmações verdadeiras são:
    - Strings são imutáveis em JavaScript
    - Você pode acessar caracteres individuais usando a notação de colchetes

    Justificativa: Strings são imutáveis, e a notação de colchetes pode ser usada para acesso. A propriedade `length` é somente leitura, e `charAt()` retorna uma string vazia (não `undefined`) para índices fora dos limites.

11. O que acontece quando você tenta acessar um caractere em uma string usando um índice negativo?

    Resposta: Quando você tenta acessar um caractere em uma string usando um índice negativo, o resultado é `undefined`.

    Justificativa: Diferente de algumas outras linguagens de programação, JavaScript não suporta indexação negativa para strings. Qualquer tentativa de usar um índice negativo resultará em `undefined`.

12. Como você pode obter uma substring de uma string em JavaScript?

    Resposta: Você pode obter uma substring de uma string em JavaScript usando os métodos `slice()`, `substring()`, ou `substr()`. Por exemplo:
    
    ```javascript
    let str = "JavaScript";
    console.log(str.slice(0, 4));  // "Java"
    console.log(str.substring(4)); // "Script"
    console.log(str.substr(0, 4)); // "Java" (deprecated)
    ```

    Justificativa: Estes métodos permitem extrair partes de uma string. `slice()` e `substring()` são preferidos, enquanto `substr()` é considerado obsoleto.

13. Verdadeiro ou Falso: A propriedade `length` de uma string pode ser usada para truncar a string.

    Resposta: Falso.

    Justificativa: A propriedade `length` de uma string é somente leitura em JavaScript. Tentar modificá-la não terá efeito na string e, em modo estrito, resultará em um erro.

14. O que o seguinte código irá imprimir?
    ```javascript
    let str = "Hello";
    str.length = 10;
    console.log(str.length);
    ```
    a) 5
    b) 10
    c) undefined
    d) Error

    Resposta: a) 5

    Justificativa: A tentativa de modificar `length` é silenciosamente ignorada em modo não estrito. A string permanece inalterada, então `length` continua sendo 5.

15. Como você pode converter uma string em um array de caracteres em JavaScript?

    Resposta: Você pode converter uma string em um array de caracteres usando o método `split()` com uma string vazia como separador, ou usando o operador spread (...). Por exemplo:

    ```javascript
    let str = "hello";
    let arr1 = str.split('');
    let arr2 = [...str];
    console.log(arr1); // ['h', 'e', 'l', 'l', 'o']
    console.log(arr2); // ['h', 'e', 'l', 'l', 'o']
    ```

    Justificativa: Ambos os métodos são eficazes para converter uma string em um array de seus caracteres individuais.

16. Associe os métodos/propriedades com suas descrições:
    1. length         A. Retorna o caractere em um índice específico
    2. charAt()       B. Retorna o número de unidades de código na string
    3. charCodeAt()   C. Retorna o valor Unicode do caractere em um índice específico
    4. indexOf()      D. Retorna a posição da primeira ocorrência de uma substring

    Resposta: 1-B, 2-A, 3-C, 4-D

    Justificativa: Cada método/propriedade tem uma função específica relacionada à manipulação ou análise de strings.

17. O que acontece quando você usa o operador de adição (+) com uma string e outro tipo de dado em JavaScript?

    Resposta: Quando você usa o operador de adição (+) com uma string e outro tipo de dado em JavaScript, o outro tipo de dado é convertido para string e então ocorre a concatenação.

    Justificativa: Este comportamento é parte da coerção de tipo em JavaScript. Por exemplo, `"5" + 3` resulta em `"53"`, não em `8`.

18. Como você pode verificar se uma string contém outra string em JavaScript?

    Resposta: Você pode verificar se uma string contém outra string usando o método `includes()`, `indexOf()`, ou uma expressão regular. Por exemplo:

    ```javascript
    let str = "Hello, World!";
    console.log(str.includes("World")); // true
    console.log(str.indexOf("World") !== -1); // true
    console.log(/World/.test(str)); // true
    ```

    Justificativa: Estes são métodos comuns para verificar a presença de uma substring. `includes()` é o mais direto, `indexOf()` é suportado em versões mais antigas de JavaScript, e expressões regulares oferecem mais flexibilidade.

19. Verdadeiro ou Falso: Strings em JavaScript são objetos.

    Resposta: Falso, mas com uma explicação.

    Justificativa: Strings primitivas em JavaScript não são objetos, mas são tratadas como objetos quando você tenta acessar suas propriedades ou métodos. JavaScript temporariamente converte (ou "envolve") a string primitiva em um objeto String para permitir o acesso a propriedades e métodos.

20. O que o seguinte código irá imprimir?
    ```javascript
    let str1 = "2" + 2;
    let str2 = 2 + "2";
    console.log(str1 === str2);
    ```
    a) true
    b) false
    c) undefined
    d) Error

    Resposta: a) true

    Justificativa: Em ambos os casos, a operação de adição com uma string resulta em concatenação. Tanto `str1` quanto `str2` terão o valor `"22"`. A comparação estrita (`===`) retorna `true` porque ambas são strings idênticas.

