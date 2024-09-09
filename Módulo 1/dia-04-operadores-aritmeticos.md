# Dia 4: Operadores Aritméticos

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender e utilizar os operadores aritméticos básicos em JavaScript
2. Compreender a ordem de precedência dos operadores
3. Utilizar operadores de incremento e decremento
4. Aplicar operadores de atribuição composta

## 1. Operadores Aritméticos Básicos

JavaScript fornece os seguintes operadores aritméticos básicos:

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `+`      | Adição    | `5 + 3` |
| `-`      | Subtração | `7 - 2` |
| `*`      | Multiplicação | `4 * 6` |
| `/`      | Divisão   | `8 / 2` |
| `%`      | Módulo (resto da divisão) | `9 % 4` |
| `**`     | Exponenciação | `2 ** 3` |

Exemplos:

```javascript
let soma = 5 + 3;        // 8
let subtracao = 7 - 2;   // 5
let multiplicacao = 4 * 6; // 24
let divisao = 8 / 2;     // 4
let modulo = 9 % 4;      // 1 (resto da divisão de 9 por 4)
let exponenciacao = 2 ** 3; // 8 (2 elevado à 3ª potência)

console.log(soma, subtracao, multiplicacao, divisao, modulo, exponenciacao);
```

## 2. Precedência de Operadores

A ordem em que as operações são realizadas é importante. JavaScript segue a ordem matemática padrão:

1. Parênteses `()`
2. Exponenciação `**`
3. Multiplicação `*`, Divisão `/`, Módulo `%`
4. Adição `+`, Subtração `-`

Exemplo:

```javascript
let resultado = 5 + 3 * 2;  // 11 (não 16)
console.log(resultado);

let resultadoComParenteses = (5 + 3) * 2;  // 16
console.log(resultadoComParenteses);
```

## 3. Operadores de Incremento e Decremento

JavaScript oferece operadores para aumentar ou diminuir um valor em 1:

- `++` : Incremento
- `--` : Decremento

Estes operadores podem ser usados antes (pré-fixo) ou depois (pós-fixo) da variável:

```javascript
let contador = 5;

console.log(contador++);  // Exibe 5, depois incrementa para 6
console.log(contador);    // Exibe 6

console.log(++contador);  // Incrementa para 7, depois exibe 7
console.log(contador);    // Exibe 7

console.log(contador--);  // Exibe 7, depois decrementa para 6
console.log(--contador);  // Decrementa para 5, depois exibe 5
```

## 4. Operadores de Atribuição Composta

Estes operadores combinam uma operação aritmética com atribuição:

| Operador | Equivalente a |
|----------|---------------|
| `+=`     | `x = x + y`   |
| `-=`     | `x = x - y`   |
| `*=`     | `x = x * y`   |
| `/=`     | `x = x / y`   |
| `%=`     | `x = x % y`   |
| `**=`    | `x = x ** y`  |

Exemplo:

```javascript
let numero = 10;

numero += 5;  // numero agora é 15
console.log(numero);

numero -= 3;  // numero agora é 12
console.log(numero);

numero *= 2;  // numero agora é 24
console.log(numero);

numero /= 4;  // numero agora é 6
console.log(numero);

numero %= 4;  // numero agora é 2 (resto de 6 dividido por 4)
console.log(numero);

numero **= 3; // numero agora é 8 (2 elevado à 3ª potência)
console.log(numero);
```

## Exercício Prático

Crie um script que:

1. Declare duas variáveis numéricas
2. Realize todas as operações aritméticas básicas com essas variáveis
3. Use operadores de incremento e decremento
4. Aplique operadores de atribuição composta
5. Imprima todos os resultados no console

## Dicas Úteis

1. Sempre use parênteses quando não tiver certeza sobre a ordem das operações.
2. Cuidado ao usar `++` e `--`, pois o momento em que são aplicados (antes ou depois da variável) pode afetar o resultado.
3. Os operadores de atribuição composta são úteis para tornar o código mais conciso e legível.

## Recursos Adicionais

- [Expressões e operadores (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_operators)
- [Operadores aritméticos em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-operadores-aritmeticos/39761)
- [JavaScript Arithmetic (W3Schools em português)](https://www.w3schools.com/js/js_arithmetic.asp)

## Próxima Aula

Na próxima aula, exploraremos os operadores de comparação e lógicos em JavaScript, que nos permitirão criar expressões condicionais e tomar decisões em nossos programas.

