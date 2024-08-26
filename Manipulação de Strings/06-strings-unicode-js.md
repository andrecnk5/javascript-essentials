# 6. Strings e Unicode em JavaScript

## 6.1 Introdução ao Unicode em JavaScript

JavaScript usa Unicode para representar strings, o que permite o suporte a uma ampla gama de caracteres de diferentes idiomas e símbolos.

## 6.2 Codificação Unicode

Unicode é um padrão de codificação de caracteres que atribui um número único (chamado de ponto de código) a cada caractere.

### 6.2.1 UTF-16

JavaScript internamente usa UTF-16 para representar strings. Isso significa que cada unidade de código (char) em uma string JavaScript ocupa 16 bits.

## 6.3 Escape Sequences

JavaScript suporta várias sequências de escape para representar caracteres especiais.

### 6.3.1 Sequências de Escape Comuns

```javascript
console.log("Linha 1\nLinha 2"); // Nova linha
console.log("Coluna1\tColuna2"); // Tab
console.log("Aspas \"duplas\""); // Aspas duplas
console.log('Aspas \'simples\''); // Aspas simples
console.log("Barra invertida \\"); // Barra invertida
```

### 6.3.2 Sequências de Escape Unicode

Você pode usar `\u` seguido por quatro dígitos hexadecimais para representar um caractere Unicode.

```javascript
console.log("\u00A9"); // ©
console.log("\u{1F600}"); // 😀 (nota: requer suporte a ES6)
```

## 6.4 Caracteres Especiais e Emojis

JavaScript suporta totalmente emojis e outros caracteres especiais.

```javascript
let texto = "Olá 🌍! Bem-vindo ao 🇧🇷";
console.log(texto);
```

## 6.5 Manipulação de Strings Unicode

### 6.5.1 Comprimento de Strings

O método `length` retorna o número de unidades de código UTF-16, não necessariamente o número de caracteres visíveis.

```javascript
console.log("😀".length); // 2
```

### 6.5.2 Iteração sobre Strings

Para iterar corretamente sobre strings que incluem caracteres fora do BMP (Basic Multilingual Plane), use `for...of` ou o método `Array.from()`.

```javascript
for (let char of "😀") {
    console.log(char);
}
```

### 6.5.3 Método charCodeAt() e codePointAt()

`charCodeAt()` retorna o valor Unicode da unidade de código UTF-16 em um índice específico, enquanto `codePointAt()` pode lidar com caracteres que ocupam duas unidades de código.

```javascript
console.log("A".charCodeAt(0)); // 65
console.log("😀".codePointAt(0)); // 128512
```

## 6.6 Normalização de Strings

O método `normalize()` permite normalizar strings Unicode para comparação.

```javascript
let s1 = "\u00F1"; // ñ
let s2 = "\u006E\u0303"; // n seguido de ˜
console.log(s1 === s2); // false
console.log(s1.normalize() === s2.normalize()); // true
```

## 6.7 Considerações de Performance

Ao trabalhar com grandes volumes de texto Unicode, considere o uso de bibliotecas especializadas para manipulação de strings para melhor performance.

## Questionário

1. O que é Unicode e por que é importante em JavaScript?

   Resposta: Unicode é um padrão de codificação de caracteres que atribui um número único (ponto de código) a cada caractere. É importante em JavaScript porque permite o suporte a uma ampla gama de caracteres de diferentes idiomas e símbolos, tornando possível a internacionalização de aplicações.

   Justificativa: O suporte ao Unicode é crucial para criar aplicações que possam ser usadas globalmente, lidando com diversos alfabetos e símbolos.

2. Verdadeiro ou Falso: JavaScript internamente usa UTF-8 para representar strings.

   Resposta: Falso.

   Justificativa: JavaScript internamente usa UTF-16, não UTF-8, para representar strings. Isso significa que cada unidade de código (char) em uma string JavaScript ocupa 16 bits.

3. Como você pode representar o símbolo de copyright (©) em uma string JavaScript usando uma sequência de escape Unicode?

   Resposta: Você pode representar o símbolo de copyright usando a sequência de escape Unicode `\u00A9`.

   Justificativa: Esta sequência de escape Unicode representa o ponto de código U+00A9, que é o símbolo de copyright no padrão Unicode.

4. O que o seguinte código irá imprimir?
   ```javascript
   console.log("😀".length);
   ```
   a) 1
   b) 2
   c) 4
   d) Error

   Resposta: b) 2

   Justificativa: Muitos emojis, incluindo 😀, são representados por dois caracteres UTF-16 em JavaScript. Portanto, embora visualmente seja um único caractere, `length` retorna 2.

5. Qual método você usaria para obter o valor Unicode de um caractere em uma string?

   Resposta: Você pode usar o método `charCodeAt()` para obter o valor Unicode de um caractere em uma string. Para caracteres que estão fora do BMP (Basic Multilingual Plane), você deve usar `codePointAt()`.

   Justificativa: `charCodeAt()` retorna o valor Unicode da unidade de código UTF-16 em um índice específico, enquanto `codePointAt()` pode lidar com caracteres que ocupam duas unidades de código.

6. O que o seguinte código irá imprimir?
   ```javascript
   console.log("\u{1F600}");
   ```

   Resposta: O código irá imprimir o emoji 😀 (rosto sorridente).

   Justificativa: A notação `\u{1F600}` é uma forma de representar um ponto de código Unicode usando a sintaxe de escape Unicode introduzida no ECMAScript 2015 (ES6).

7. Verdadeiro ou Falso: Todas as strings em JavaScript ocupam o mesmo espaço em memória, independentemente dos caracteres que contêm.

   Resposta: Falso.

   Justificativa: O espaço ocupado por uma string depende dos caracteres que ela contém. Caracteres que estão fora do BMP (Basic Multilingual Plane) ocupam duas unidades de código UTF-16, enquanto a maioria dos caracteres ocupa apenas uma.

8. Como você pode iterar corretamente sobre uma string que contém emojis em JavaScript?

   Resposta: Para iterar corretamente sobre uma string que contém emojis, você pode usar o loop `for...of` ou o método `Array.from()`. Por exemplo:

   ```javascript
   for (let char of "Olá 😀") {
       console.log(char);
   }
   ```

   Justificativa: O loop `for...of` e `Array.from()` tratam corretamente caracteres Unicode que ocupam mais de uma unidade de código UTF-16, como muitos emojis.

9. O que é normalização de strings Unicode e por que é importante?

   Resposta: Normalização de strings Unicode é o processo de converter uma string para uma forma canônica, garantindo que sequências de caracteres equivalentes tenham uma representação única. É importante para comparação precisa de strings, especialmente quando lidando com caracteres acentuados ou compostos.

   Justificativa: Sem normalização, strings que parecem idênticas visualmente podem ter representações internas diferentes e, portanto, não seriam consideradas iguais em comparações.

10. Marque todas as afirmações verdadeiras sobre strings Unicode em JavaScript:
    [ ] Todos os caracteres em uma string ocupam uma única unidade de código UTF-16
    [ ] A propriedade `length` sempre retorna o número de caracteres visíveis
    [ ] JavaScript suporta totalmente emojis em strings
    [ ] O método `charAt()` sempre retorna um único caractere visível

    Resposta: A única afirmação verdadeira é:
    - JavaScript suporta totalmente emojis em strings

    Justificativa: Alguns caracteres (como emojis) ocupam mais de uma unidade de código, `length` retorna o número de unidades de código (não necessariamente caracteres visíveis), e `charAt()` retorna uma única unidade de código, que pode não ser um caractere visível completo para alguns símbolos.

11. Como você pode representar uma barra invertida em uma string JavaScript?

    Resposta: Você pode representar uma barra invertida em uma string JavaScript usando duas barras invertidas: "\\".

    Justificativa: A barra invertida é um caractere de escape em JavaScript, então para representá-la literalmente, você precisa escapá-la com outra barra invertida.

12. O que é o BMP (Basic Multilingual Plane) no contexto do Unicode?

    Resposta: O BMP (Basic Multilingual Plane) é o primeiro plano (0) do Unicode, que contém os caracteres mais comumente usados. Ele inclui pontos de código de U+0000 a U+FFFF, que podem ser representados por uma única unidade de código UTF-16.

    Justificativa: Entender o BMP é importante porque caracteres fora do BMP requerem tratamento especial em JavaScript, ocupando duas unidades de código UTF-16.

13. Verdadeiro ou Falso: O método `String.fromCharCode()` pode ser usado para criar qualquer caractere Unicode.

    Resposta: Falso.

    Justificativa: `String.fromCharCode()` só pode criar caracteres dentro do BMP (até U+FFFF). Para criar caracteres fora do BMP, você deve usar `String.fromCodePoint()`.

14. O que o seguinte código irá imprimir?
    ```javascript
    console.log("é" === "e\u0301");
    ```
    a) true
    b) false

    Resposta: b) false

    Justificativa: Embora "é" e "e\u0301" (e seguido de um acento agudo combinante) pareçam visualmente idênticos, eles têm representações internas diferentes e, portanto, não são considerados iguais sem normalização.

15. Como você pode converter um ponto de código Unicode para um caractere em JavaScript?

    Resposta: Você pode converter um ponto de código Unicode para um caractere usando `String.fromCodePoint()`. Por exemplo:

    ```javascript
    console.log(String.fromCodePoint(0x1F600)); // 😀
    ```

    Justificativa: `String.fromCodePoint()` é o método mais recente e capaz de lidar com todos os pontos de código Unicode, incluindo aqueles fora do BMP.

16. Associe os métodos com suas descrições:
    1. normalize()    A. Retorna o valor Unicode de uma unidade de código
    2. charCodeAt()   B. Converte strings para uma forma canônica
    3. codePointAt()  C. Cria uma string a partir de pontos de código
    4. fromCodePoint() D. Retorna o ponto de código Unicode completo

    Resposta: 1-B, 2-A, 3-D, 4-C

    Justificativa: Cada método tem uma função específica no tratamento de strings Unicode em JavaScript.

17. O que acontece se você tentar usar `charCodeAt()` com um emoji?

    Resposta: Se você usar `charCodeAt()` com um emoji, ele retornará o valor Unicode da primeira unidade de código UTF-16 do emoji. Para muitos emojis, isso será um valor na faixa surrogate (entre 0xD800 e 0xDFFF).

    Exemplo:
    ```javascript
    console.log("😀".charCodeAt(0)); // Retorna um valor na faixa surrogate
    ```

    Justificativa: `charCodeAt()` trabalha com unidades de código individuais, não com pontos de código completos, o que pode levar a resultados inesperados com caracteres que ocupam múltiplas unidades de código.

18. Como você pode determinar se uma string contém caracteres fora do BMP?

    Resposta: Você pode determinar se uma string contém caracteres fora do BMP comparando o comprimento da string com o número de pontos de código. Por exemplo:

    ```javascript
    function temCaracteresForaDoBMP(str) {
        return str.length !== [...str].length;
    }
    ```

    Justificativa: Caracteres fora do BMP ocupam duas unidades de código, então se o comprimento da string é maior que o número de pontos de código (que pode ser obtido convertendo a string para um array), a string contém caracteres fora do BMP.

19. Verdadeiro ou Falso: Todos os emojis em JavaScript são representados por um único ponto de código Unicode.

    Resposta: Falso.

    Justificativa: Embora alguns emojis sejam representados por um único ponto de código, muitos emojis modernos, especialmente aqueles com variações de tom de pele ou emojis compostos, são formados por sequências de múltiplos pontos de código.

20. O que o seguinte código irá imprimir?
    ```javascript
    console.log("🇧🇷".length);
    ```
    a) 1
    b) 2
    c) 4
    d) 8

    Resposta: c) 4

    Justificativa: A bandeira do Brasil 🇧🇷 é composta por dois caracteres Unicode (Regional Indicator Symbol Letter B + Regional Indicator Symbol Letter R), cada um ocupando duas unidades de código UTF-16. Portanto, o comprimento total é 4.

