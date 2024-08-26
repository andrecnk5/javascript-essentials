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

2. Verdadeiro ou Falso: A indexação de caracteres em uma string JavaScript começa em 1.

3. Qual será o output do seguinte código?
   ```javascript
   let str = "JavaScript";
   console.log(str[str.length]);
   ```
   a) "t"
   b) undefined
   c) ""
   d) Error

4. Como você pode acessar o último caractere de uma string em JavaScript?

5. Qual é a diferença entre usar a notação de colchetes e o método `charAt()` para acessar caracteres em uma string?

6. O que acontece quando você tenta modificar um caractere em uma string usando a notação de colchetes?

7. Verdadeiro ou Falso: O método `length` de uma string retorna o número de caracteres visíveis na string.

8. O que o seguinte código irá imprimir?
   ```javascript
   let str = "🚀";
   console.log(str.length);
   ```
   a) 1
   b) 2
   c) 4
   d) Error

9. Como você pode verificar se uma string está vazia em JavaScript?

10. Marque todas as afirmações verdadeiras sobre propriedades de strings em JavaScript:
    [ ] Strings são imutáveis em JavaScript
    [ ] A propriedade `length` de uma string pode ser modificada
    [ ] Você pode acessar caracteres individuais usando a notação de colchetes
    [ ] O método `charAt()` retorna `undefined` para índices fora dos limites

11. O que acontece quando você tenta acessar um caractere em uma string usando um índice negativo?

12. Como você pode obter uma substring de uma string em JavaScript?

13. Verdadeiro ou Falso: A propriedade `length` de uma string pode ser usada para truncar a string.

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

15. Como você pode converter uma string em um array de caracteres em JavaScript?

16. Associe os métodos/propriedades com suas descrições:
    1. length         A. Retorna o caractere em um índice específico
    2. charAt()       B. Retorna o número de unidades de código na string
    3. charCodeAt()   C. Retorna o valor Unicode do caractere em um índice específico
    4. indexOf()      D. Retorna a posição da primeira ocorrência de uma substring

17. O que acontece quando você usa o operador de adição (+) com uma string e outro tipo de dado em JavaScript?

18. Como você pode verificar se uma string contém outra string em JavaScript?

19. Verdadeiro ou Falso: Strings em JavaScript são objetos.

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