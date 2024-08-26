# 9. Exercícios Práticos: Strings em JavaScript

## 9.1 Criar Código

1. Escreva uma função chamada `inverterString` que aceita uma string como parâmetro e retorna a string invertida.

Resposta:
```javascript
function inverterString(str) {
    return str.split('').reverse().join('');
}

console.log(inverterString("hello")); // "olleh"
```

Justificativa: Esta função divide a string em um array de caracteres, inverte o array e então junta os caracteres de volta em uma string. É uma maneira eficiente e concisa de inverter uma string em JavaScript.

2. Crie uma função chamada `contarVogais` que conta o número de vogais em uma string (considere a, e, i, o, u, tanto maiúsculas quanto minúsculas).

Resposta:
```javascript
function contarVogais(str) {
    return (str.match(/[aeiou]/gi) || []).length;
}

console.log(contarVogais("Hello World")); // 3
```

Justificativa: Esta função usa uma expressão regular para encontrar todas as vogais na string. A flag 'g' faz a busca global, e 'i' torna a busca case-insensitive. O `|| []` garante que um array vazio seja retornado se nenhuma vogal for encontrada, evitando erros.

## 9.2 Analisar Código

3. Analise o seguinte código e explique o que ele faz:

```javascript
function processarString(str) {
    return str.split(' ')
              .map(word => word.charAt(0).toUpperCase() + word.slice(1))
              .join(' ');
}
```

Resposta: Esta função capitaliza a primeira letra de cada palavra em uma string. Ela faz isso dividindo a string em um array de palavras, transformando a primeira letra de cada palavra em maiúscula, e então juntando as palavras de volta em uma string.

Justificativa: Este é um exemplo comum de manipulação de strings para formatar texto, frequentemente usado para títulos ou nomes.

4. O que o seguinte código irá imprimir e por quê?

```javascript
let str = "JavaScript";
console.log(str.padStart(15, "*").padEnd(20, "*"));
```

Resposta: O código irá imprimir: "****JavaScript*****"

Justificativa: `padStart(15, "*")` adiciona asteriscos no início da string até que ela tenha 15 caracteres. Em seguida, `padEnd(20, "*")` adiciona asteriscos no final até que a string tenha 20 caracteres no total.

## 9.3 Corrigir Código

5. O seguinte código deveria remover todos os espaços de uma string, mas não está funcionando corretamente. Corrija-o:

```javascript
function removerEspacos(str) {
    return str.replace(" ", "");
}
```

Resposta corrigida:
```javascript
function removerEspacos(str) {
    return str.replace(/\s/g, "");
}
```

Justificativa: A versão original só remove o primeiro espaço encontrado. A versão corrigida usa uma expressão regular com a flag 'g' para substituir todos os espaços na string.

6. Este código deveria converter uma string para snake_case, mas está com erro. Corrija-o:

```javascript
function toSnakeCase(str) {
    return str.toLowerCase().replace(" ", "_");
}
```

Resposta corrigida:
```javascript
function toSnakeCase(str) {
    return str.toLowerCase().replace(/\s+/g, "_");
}
```

Justificativa: A versão original só substitui o primeiro espaço. A versão corrigida usa uma expressão regular para substituir um ou mais espaços consecutivos por um underscore.

## 9.4 Completar Códigos

7. Complete o código abaixo para criar uma função que verifica se uma string é um palíndromo (lê-se igual de trás para frente, ignorando espaços e pontuação):

```javascript
function isPalindrome(str) {
    // Seu código aqui
}
```

Resposta:
```javascript
function isPalindrome(str) {
    str = str.toLowerCase().replace(/[^a-z0-9]/g, '');
    return str === str.split('').reverse().join('');
}

console.log(isPalindrome("A man, a plan, a canal: Panama")); // true
```

Justificativa: Esta função remove todos os caracteres não alfanuméricos e converte a string para minúsculas antes de verificar se ela é igual à sua versão invertida.

8. Complete o código abaixo para criar uma função que converte uma string para camelCase:

```javascript
function toCamelCase(str) {
    // Seu código aqui
}
```

Resposta:
```javascript
function toCamelCase(str) {
    return str.replace(/[-_\s]+(.)?/g, (_, c) => c ? c.toUpperCase() : '');
}

console.log(toCamelCase("hello-world_example")); // "helloWorldExample"
```

Justificativa: Esta função usa uma expressão regular para encontrar hífens, underscores ou espaços seguidos por qualquer caractere, e então converte esse caractere para maiúscula, efetivamente transformando a string em camelCase.

9. Implemente uma função `truncate` que corta uma string se ela for mais longa que o comprimento máximo especificado, adicionando "..." no final:

```javascript
function truncate(str, maxLength) {
    // Seu código aqui
}
```

Resposta:
```javascript
function truncate(str, maxLength) {
    return str.length > maxLength ? str.slice(0, maxLength - 3) + '...' : str;
}

console.log(truncate("This is a long string", 10)); // "This is..."
```

Justificativa: Esta função verifica se a string é mais longa que o comprimento máximo. Se for, ela corta a string e adiciona "..." no final, garantindo que o resultado final tenha exatamente o comprimento máximo especificado.

10. Crie uma função que converte uma string para título (primeira letra de cada palavra em maiúscula, exceto para algumas palavras como "a", "an", "the", etc.):

```javascript
function toTitleCase(str) {
    // Seu código aqui
}
```

Resposta:
```javascript
function toTitleCase(str) {
    const exceptions = ['a', 'an', 'the', 'and', 'but', 'or', 'for', 'nor', 'on', 'at', 'to', 'from', 'by', 'in'];
    return str.toLowerCase().replace(/\w+/g, function(word, index) {
        if (index === 0 || !exceptions.includes(word)) {
            return word.charAt(0).toUpperCase() + word.slice(1);
        }
        return word;
    });
}

console.log(toTitleCase("the quick brown fox jumps over the lazy dog"));
// "The Quick Brown Fox Jumps over the Lazy Dog"
```

Justificativa: Esta função converte a string para minúsculas e então capitaliza a primeira letra de cada palavra, exceto para as palavras na lista de exceções (a menos que seja a primeira palavra da frase).

11. Analise e corrija o seguinte código que deveria extrair um domínio de um email:

```javascript
function extractDomain(email) {
    return email.slice(email.indexOf("@"));
}
```

Resposta corrigida:
```javascript
function extractDomain(email) {
    return email.slice(email.indexOf("@") + 1);
}

console.log(extractDomain("user@example.com")); // "example.com"
```

Justificativa: A versão original incluía o símbolo "@" no resultado. A versão corrigida adiciona 1 ao índice retornado por `indexOf("@")` para começar a extração após o "@".

12. Complete o código para criar uma função que mascara parte de uma string, deixando visíveis apenas os últimos `n` caracteres:

```javascript
function maskString(str, n) {
    // Seu código aqui
}
```

Resposta:
```javascript
function maskString(str, n) {
    return str.slice(-n).padStart(str.length, '*');
}

console.log(maskString("1234567890", 4)); // "******7890"
```

Justificativa: Esta função usa `slice(-n)` para pegar os últimos `n` caracteres da string, e então usa `padStart` para adicionar asteriscos no início até que a string tenha o comprimento original.

13. Implemente uma função que verifica se uma string contém todas as letras do alfabeto (pangrama):

```javascript
function isPangram(str) {
    // Seu código aqui
}
```

Resposta:
```javascript
function isPangram(str) {
    const alphabet = 'abcdefghijklmnopqrstuvwxyz';
    return alphabet.split('').every(letter => str.toLowerCase().includes(letter));
}

console.log(isPangram("The quick brown fox jumps over the lazy dog")); // true
```

Justificativa: Esta função verifica se cada letra do alfabeto está presente na string (ignorando maiúsculas/minúsculas). Usa o método `every` para garantir que todas as letras sejam encontradas.

14. Corrija o seguinte código que deveria contar a ocorrência de cada caractere em uma string:

```javascript
function countChars(str) {
    let count = {};
    for (let char of str) {
        count[char] = 1;
    }
    return count;
}
```

Resposta corrigida:
```javascript
function countChars(str) {
    let count = {};
    for (let char of str) {
        count[char] = (count[char] || 0) + 1;
    }
    return count;
}

console.log(countChars("hello")); // { h: 1, e: 1, l: 2, o: 1 }
```

Justificativa: A versão original sempre definia a contagem como 1, ignorando caracteres repetidos. A versão corrigida incrementa a contagem existente ou inicia em 1 se o caractere não foi encontrado antes.

15. Complete o código para criar uma função que gera um slug a partir de uma string (por exemplo, para URLs amigáveis):

```javascript
function generateSlug(str) {
    // Seu código aqui
}
```

Resposta:
```javascript
function generateSlug(str) {
    return str
        .toLowerCase()
        .trim()
        .replace(/[^\w\s-]/g, '')
        .replace(/[\s_-]+/g, '-')
        .replace(/^-+|-+$/g, '');
}

console.log(generateSlug("Hello World! This is a test.")); // "hello-world-this-is-a-test"
```

Justificativa: Esta função converte a string para minúsculas, remove espaços extras no início e fim, substitui caracteres especiais por '', substitui espaços, underscores e hífens por um único hífen, e remove hífens do início e do fim da string.

