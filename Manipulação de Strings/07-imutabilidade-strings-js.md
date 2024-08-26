# 7. Imutabilidade de Strings em JavaScript

## 7.1 Introdução à Imutabilidade

Em JavaScript, as strings são imutáveis. Isso significa que, uma vez que uma string é criada, seu conteúdo não pode ser alterado. Qualquer operação que pareça modificar uma string na verdade cria uma nova string.

## 7.2 Conceito de Imutabilidade

Imutabilidade é um conceito fundamental em programação que se refere à incapacidade de um objeto de ser modificado após sua criação. No caso das strings em JavaScript, isso significa que cada operação que parece alterar uma string na verdade retorna uma nova string.

## 7.3 Exemplos de Imutabilidade

### 7.3.1 Tentativa de Modificação Direta

```javascript
let str = "Hello";
str[0] = "h"; // Isso não produz erro, mas também não modifica a string
console.log(str); // Ainda imprime "Hello"
```

### 7.3.2 Métodos que Retornam Novas Strings

```javascript
let original = "JavaScript";
let maiusculas = original.toUpperCase();

console.log(original);   // "JavaScript"
console.log(maiusculas); // "JAVASCRIPT"
```

## 7.4 Implicações da Imutabilidade

### 7.4.1 Performance

A imutabilidade pode ter implicações de performance, especialmente quando se trabalha com grandes strings ou muitas operações de string.

```javascript
let resultado = "";
for (let i = 0; i < 1000; i++) {
    resultado += "a"; // Cria uma nova string a cada iteração
}
```

### 7.4.2 Segurança

A imutabilidade fornece uma camada de segurança, garantindo que o valor de uma string não possa ser alterado acidentalmente.

### 7.4.3 Previsibilidade

Strings imutáveis são mais previsíveis e fáceis de raciocinar sobre, pois seu valor não muda inesperadamente.

## 7.5 Trabalhando com Strings Imutáveis

### 7.5.1 Reatribuição

Para "modificar" uma string, você precisa reatribuí-la:

```javascript
let str = "Hello";
str = "Hello, World!"; // Cria uma nova string e atribui a str
```

### 7.5.2 Uso de Métodos de String

Utilize métodos de string que retornam novas strings:

```javascript
let str = "   trim me   ";
let trimmed = str.trim();
console.log(trimmed); // "trim me"
```

### 7.5.3 Concatenação Eficiente

Para operações que envolvem muitas concatenações, considere usar `Array.join()` ou template literals:

```javascript
let partes = ['Hello', 'World', '!'];
let resultado = partes.join(' ');
console.log(resultado); // "Hello World !"
```

## 7.6 Comparação com Outros Tipos

Ao contrário das strings, arrays e objetos em JavaScript são mutáveis:

```javascript
let arr = [1, 2, 3];
arr[0] = 4; // Modifica o array original
console.log(arr); // [4, 2, 3]

let obj = {nome: "Alice"};
obj.nome = "Bob"; // Modifica o objeto original
console.log(obj); // {nome: "Bob"}
```

## Questionário

1. O que significa dizer que as strings são imutáveis em JavaScript?

   Resposta: Dizer que as strings são imutáveis em JavaScript significa que, uma vez que uma string é criada, seu conteúdo não pode ser alterado. Qualquer operação que pareça modificar uma string na verdade cria uma nova string.

   Justificativa: A imutabilidade é uma característica fundamental das strings em JavaScript, afetando como elas são manipuladas e otimizadas pelo motor JavaScript.

2. Verdadeiro ou Falso: Você pode modificar um caractere individual em uma string usando notação de colchetes.

   Resposta: Falso.

   Justificativa: Devido à imutabilidade das strings, tentar modificar um caractere individual usando notação de colchetes (como `str[0] = 'x'`) não resultará em erro, mas também não modificará a string original.

3. O que o seguinte código irá imprimir?
   ```javascript
   let str = "Hello";
   str[0] = "h";
   console.log(str);
   ```
   a) "hello"
   b) "Hello"
   c) "hello"
   d) Error

   Resposta: b) "Hello"

   Justificativa: Devido à imutabilidade das strings, a tentativa de modificar um caractere individual não tem efeito. A string original permanece inalterada.

4. Como você pode "modificar" uma string em JavaScript, considerando sua imutabilidade?

   Resposta: Para "modificar" uma string em JavaScript, você precisa criar uma nova string com as alterações desejadas e reatribuí-la à variável. Isso pode ser feito usando métodos de string que retornam novas strings ou através de concatenação.

   Justificativa: Devido à imutabilidade, não podemos modificar uma string existente diretamente. Em vez disso, criamos uma nova string com as alterações desejadas.

5. Qual é uma das principais vantagens da imutabilidade de strings em termos de segurança?

   Resposta: Uma das principais vantagens da imutabilidade de strings em termos de segurança é que ela garante que o valor de uma string não possa ser alterado acidentalmente ou maliciosamente após sua criação.

   Justificativa: A imutabilidade ajuda a prevenir modificações não intencionais ou não autorizadas em dados sensíveis representados como strings.

6. O que o seguinte código irá imprimir?
   ```javascript
   let original = "JavaScript";
   let modificada = original.toLowerCase();
   console.log(original);
   ```

   Resposta: O código irá imprimir "JavaScript".

   Justificativa: O método `toLowerCase()` não modifica a string original. Em vez disso, ele retorna uma nova string em minúsculas. A variável `original` permanece inalterada.

7. Verdadeiro ou Falso: A imutabilidade de strings sempre leva a um melhor desempenho em JavaScript.

   Resposta: Falso.

   Justificativa: Embora a imutabilidade tenha vantagens, ela pode levar a problemas de desempenho em certas situações, especialmente quando se trabalha com muitas operações de string ou strings muito grandes, pois cada operação cria uma nova string.

8. Qual das seguintes opções é uma maneira eficiente de concatenar muitas strings em JavaScript?

   a) Usar o operador + repetidamente
   b) Usar o método concat() em um loop
   c) Usar Array.join()
   d) Usar um loop for para concatenar caractere por caractere

   Resposta: c) Usar Array.join()

   Justificativa: Array.join() é geralmente mais eficiente para concatenar muitas strings, pois minimiza a criação de strings intermediárias.

9. Como a imutabilidade de strings afeta o uso de memória em JavaScript?

   Resposta: A imutabilidade de strings pode levar a um maior uso de memória em certas situações, pois cada operação que parece modificar uma string na verdade cria uma nova string na memória.

   Justificativa: Isso é particularmente notável em operações que envolvem muitas modificações de string, onde cada modificação resulta em uma nova alocação de memória.

10. Marque todas as afirmações verdadeiras sobre imutabilidade de strings em JavaScript:
    [ ] Strings podem ser modificadas diretamente
    [ ] Métodos de string sempre retornam novas strings
    [ ] A imutabilidade ajuda na previsibilidade do código
    [ ] Strings e arrays têm o mesmo comportamento em termos de mutabilidade

    Resposta: As afirmações verdadeiras são:
    - Métodos de string sempre retornam novas strings
    - A imutabilidade ajuda na previsibilidade do código

    Justificativa: Strings não podem ser modificadas diretamente e têm comportamento diferente dos arrays em termos de mutabilidade.

11. Como você pode eficientemente construir uma string grande a partir de muitas partes menores em JavaScript?

    Resposta: Para construir eficientemente uma string grande a partir de muitas partes menores, você pode:
    1. Usar um array para armazenar as partes e então usar `Array.join()`.
    2. Usar um objeto `StringBuilder` se disponível no ambiente.
    3. Em navegadores modernos, concatenação simples com `+=` pode ser otimizada internamente.

    Exemplo:
    ```javascript
    let partes = ['parte1', 'parte2', 'parte3', /* ... */];
    let resultado = partes.join('');
    ```

    Justificativa: Essas abordagens minimizam a criação de strings intermediárias, melhorando a eficiência da operação.

12. Qual é a diferença entre imutabilidade e constância em JavaScript?

    Resposta: Imutabilidade refere-se à incapacidade de mudar o conteúdo de um valor, enquanto constância (como em `const`) refere-se à incapacidade de reatribuir uma variável. Uma string é imutável, mas uma variável `const` contendo uma string ainda pode ter seu valor reatribuído para uma string diferente.

    Justificativa: Entender esta diferença é crucial para compreender o comportamento de strings e variáveis em JavaScript.

13. Verdadeiro ou Falso: O método `replace()` modifica a string original.

    Resposta: Falso.

    Justificativa: Devido à imutabilidade das strings, o método `replace()` não modifica a string original. Em vez disso, ele retorna uma nova string com a substituição aplicada.

14. O que o seguinte código irá imprimir?
    ```javascript
    let str = "Hello";
    str.toUpperCase();
    console.log(str);
    ```
    a) "HELLO"
    b) "Hello"
    c) "hello"
    d) undefined

    Resposta: b) "Hello"

    Justificativa: O método `toUpperCase()` retorna uma nova string em maiúsculas, mas não modifica a string original. Como o resultado não é atribuído ou usado, a string original permanece inalterada.

15. Como a imutabilidade de strings afeta o desempenho de loops que manipulam strings?

    Resposta: A imutabilidade de strings pode afetar negativamente o desempenho de loops que manipulam strings, especialmente se houver muitas operações de concatenação ou modificação. Cada operação cria uma nova string, o que pode ser ineficiente em termos de memória e tempo de execução.

    Justificativa: Em loops com muitas iterações, a criação constante de novas strings pode levar a problemas de desempenho. Nestes casos, é geralmente mais eficiente usar outras estruturas de dados (como arrays) e concatenar no final.

16. Associe os conceitos com suas descrições:
    1. Imutabilidade    A. Não pode ser reatribuído
    2. Constância       B. Não pode ser modificado internamente
    3. Referência       C. Aponta para um local na memória
    4. Valor            D. O conteúdo real armazenado

    Resposta: 1-B, 2-A, 3-C, 4-D

    Justificativa: Cada conceito tem um significado específico no contexto de programação em JavaScript.

17. Como você pode "modificar" eficientemente uma parte de uma string longa sem criar muitas strings intermediárias?

    Resposta: Uma abordagem eficiente para "modificar" parte de uma string longa é:
    1. Converter a string em um array de caracteres.
    2. Modificar o array conforme necessário.
    3. Juntar o array de volta em uma string.

    Exemplo:
    ```javascript
    let str = "uma string muito longa";
    let arr = str.split('');
    arr[4] = 'S';
    let novaStr = arr.join('');
    ```

    Justificativa: Esta abordagem minimiza a criação de strings intermediárias, sendo mais eficiente para modificações em strings longas.

18. Verdadeiro ou Falso: A imutabilidade de strings em JavaScript é uma característica de implementação que pode variar entre diferentes engines JavaScript.

    Resposta: Falso.

    Justificativa: A imutabilidade de strings é uma característica fundamental da linguagem JavaScript, especificada pelo ECMAScript, e não uma característica de implementação que pode variar entre engines.

19. Como a imutabilidade de strings afeta o compartilhamento de memória em JavaScript?

    Resposta: A imutabilidade de strings permite que o JavaScript otimize o uso de memória através do compartilhamento de strings idênticas. Múltiplas variáveis podem apontar para a mesma string na memória sem risco de uma modificação afetar as outras.

    Justificativa: Esta otimização, conhecida como "string interning", é possível devido à garantia de que as strings não serão modificadas após a criação.

20. O que o seguinte código irá imprimir e por quê?
    ```javascript
    let a = "Hello";
    let b = a;
    a += " World";
    console.log(b);
    ```
    a) "Hello World"
    b) "Hello"
    c) undefined
    d) Error

    Resposta: b) "Hello"

    Justificativa: Quando `a += " World"` é executado, uma nova string é criada e atribuída a `a`. A variável `b` continua apontando para a string original "Hello". Isso demonstra como a imutabilidade afeta as operações de string e atribuições de variáveis.

