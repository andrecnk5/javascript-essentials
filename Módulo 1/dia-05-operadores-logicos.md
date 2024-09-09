# Dia 5: Operadores Lógicos em JavaScript

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Utilizar operadores de comparação para avaliar e comparar valores
2. Compreender e aplicar operadores lógicos para combinar condições
3. Entender a precedência entre operadores lógicos e de comparação
4. Aplicar estes operadores em estruturas condicionais simples

## 1. Introdução aos Operadores Lógicos

Os operadores lógicos em JavaScript são ferramentas fundamentais para realizar operações de lógica booleana. Eles são utilizados para comparar valores, combinar condições e tomar decisões com base em expressões lógicas. Esses operadores são essenciais para controle de fluxo em programas e são frequentemente usados em estruturas condicionais e loops.

## 2. Tipos de Operadores Lógicos

JavaScript possui três operadores lógicos principais:

### 2.1 Operador AND (&&)

O operador AND (&&) retorna true se ambos os operandos forem verdadeiros. Caso contrário, retorna false.

#### Exemplo

```javascript
let x = 5;
let y = 10;

console.log(x > 0 && y < 20); // true
console.log(x > 10 && y < 20); // false

// Explicação:
// Na primeira expressão, ambas as condições são verdadeiras (5 > 0 e 10 < 20), então o resultado é true.
// Na segunda expressão, a primeira condição é falsa (5 não é maior que 10), então o resultado é false.
```

### 2.2 Operador OR (||)

O operador OR (||) retorna true se pelo menos um dos operandos for verdadeiro. Retorna false apenas se ambos os operandos forem falsos.

#### Exemplo

```javascript
let a = 3;
let b = -2;

console.log(a > 0 || b > 0); // true
console.log(a < 0 || b > 0); // false

// Explicação:
// Na primeira expressão, a primeira condição é verdadeira (3 > 0), então o resultado é true.
// Na segunda expressão, ambas as condições são falsas (3 não é menor que 0 e -2 não é maior que 0), então o resultado é false.
```

### 2.3 Operador NOT (!)

O operador NOT (!) inverte o valor lógico do operando. Se o operando for true, retorna false, e vice-versa.

#### Exemplo

```javascript
let isRaining = true;

console.log(!isRaining); // false
console.log(!(10 > 5)); // false

// Explicação:
// No primeiro caso, isRaining é true, então !isRaining é false.
// No segundo caso, (10 > 5) é true, então !(10 > 5) é false.
```

## 3. Precedência dos Operadores Lógicos

A precedência dos operadores lógicos em JavaScript é a seguinte (do maior para o menor):

1. NOT (!)
2. AND (&&)
3. OR (||)

Isso significa que o NOT será avaliado primeiro, seguido pelo AND e, por último, o OR.

#### Exemplo

```javascript
let result = true && !false || false && !true;

console.log(result); // true

// Explicação passo a passo:
// 1. !false é avaliado primeiro, resultando em true
// 2. !true é avaliado, resultando em false
// 3. true && true || false && false
// 4. true || false
// 5. O resultado final é true
```

## 4. Curto-Circuito (Short-Circuit Evaluation)

JavaScript utiliza a avaliação de curto-circuito para operadores lógicos. Isso significa que a avaliação para assim que o resultado final pode ser determinado.

### 4.1 Curto-Circuito com AND (&&)

Se o primeiro operando for false, o segundo operando não será avaliado, pois o resultado final já será false.

#### Exemplo

```javascript
let x = 5;
let y;

console.log(x > 10 && y++); // false
console.log(y); // undefined

// Explicação:
// Como x > 10 é false, y++ não é avaliado.
// y permanece undefined.
```

### 4.2 Curto-Circuito com OR (||)

Se o primeiro operando for true, o segundo operando não será avaliado, pois o resultado final já será true.

#### Exemplo:

```javascript
let a = 5;
let b;

console.log(a > 0 || b++); // true
console.log(b); // undefined

// Explicação:
// Como a > 0 é true, b++ não é avaliado.
// b permanece undefined.
```

## 5. Operadores Lógicos com Valores Não Booleanos

Em JavaScript, os operadores lógicos podem ser usados com valores não booleanos. Nestes casos, eles não necessariamente retornam um valor booleano.

### 5.1 AND (&&) com Valores Não Booleanos

Retorna o primeiro operando se ele for falsy, caso contrário, retorna o segundo operando.

#### Exemplo

```javascript
console.log(0 && "Hello"); // 0
console.log(1 && "World"); // "World"

// Explicação:
// 0 é falsy, então é retornado imediatamente.
// 1 é truthy, então "World" é retornado.
```

### 5.2 OR (||) com Valores Não Booleanos

Retorna o primeiro operando se ele for truthy, caso contrário, retorna o segundo operando.

#### Exemplo

```javascript
console.log("" || "Default"); // "Default"
console.log("Hello" || "World"); // "Hello"

// Explicação:
// "" é falsy, então "Default" é retornado.
// "Hello" é truthy, então é retornado imediatamente.
```

## 6. Aplicações Práticas

Os operadores lógicos são amplamente utilizados em várias situações de programação:

### 6.1 Controle de Fluxo

Usados em estruturas condicionais para tomar decisões.

#### Exemplo

```javascript
let idade = 18;
let temCarteira = true;

if (idade >= 18 && temCarteira) {
    console.log("Pode dirigir");
} else {
    console.log("Não pode dirigir");
}

// Explicação:
// A pessoa só pode dirigir se tiver 18 anos ou mais E possuir carteira de motorista.
```

### 6.2 Validação de Formulários

Úteis para verificar múltiplas condições em validações de entrada de usuário.

#### Exemplo

```javascript
function validarSenha(senha) {
    return senha.length >= 8 && /[A-Z]/.test(senha) && /[0-9]/.test(senha);
}

console.log(validarSenha("Abc12345")); // true
console.log(validarSenha("abc123")); // false

// Explicação:
// A senha é válida se tiver pelo menos 8 caracteres, uma letra maiúscula e um número.
```

### 6.3 Configuração de Valores Padrão

O operador OR é frequentemente usado para definir valores padrão.

#### Exemplo

```javascript
function saudacao(nome) {
    nome = nome || "Visitante";
    console.log("Olá, " + nome + "!");
}

saudacao("Maria"); // Olá, Maria!
saudacao(); // Olá, Visitante!

// Explicação:
// Se nome não for fornecido (undefined), será usado "Visitante" como valor padrão.
```

## 7. Exercícios: Operadores Lógicos em JavaScript

## Exercícios Teóricos

### 1. Questões Dissertativas

a) Explique a diferença entre os operadores AND (&&) e OR (||) em JavaScript.

b) Como funciona o curto-circuito (short-circuit evaluation) nos operadores lógicos em JavaScript?

### 2. Questões de Múltipla Escolha

a) Qual é o resultado da expressão: true && false || true?

1. [ ] true
2. [ ]  false
3. [ ]  undefined
4. [ ]  null

b) Qual operador lógico tem a maior precedência em JavaScript?

1. [ ]  AND (&&)
2. [ ]  OR (||)
3. [ ]  NOT (!)
4. [ ]  Todos têm a mesma precedência

### 3. Questões de Caixa de Múltiplas Escolhas

Quais das seguintes afirmações são verdadeiras sobre os operadores lógicos em JavaScript? (Selecione todas as opções corretas)

1. [ ] O operador AND (&&) sempre retorna um valor booleano.
2. [ ] O operador OR (||) pode ser usado para definir valores padrão.
3. [ ] O operador NOT (!) inverte o valor de verdade do seu operando.
4. [ ] Os operadores lógicos em JavaScript usam avaliação de curto-circuito.
5. [ ] O operador XOR (^) é um operador lógico nativo em JavaScript.

### 4. Questões Verdadeiro ou Falso

a) O operador AND (&&) em JavaScript retorna o último valor verdadeiro se todos os operandos forem verdadeiros.

1. [ ] Verdadeiro
2. [ ] Falso

b) Em JavaScript, uma string vazia é considerada um valor falsy.

1. [ ] Verdadeiro
2. [ ] Falso

c) O operador OR (||) sempre retorna um valor booleano.

1. [ ] Verdadeiro
2. [ ] Falso

## 8. Conclusão

Os operadores lógicos em JavaScript são ferramentas poderosas e versáteis. Eles não apenas permitem a criação de lógica condicional complexa, mas também oferecem funcionalidades únicas quando usados com valores não booleanos. Dominar esses operadores é essencial para escrever código JavaScript eficiente e expressivo.

A compreensão profunda dos operadores lógicos, incluindo seu comportamento de curto-circuito e interação com diferentes tipos de dados, permite aos desenvolvedores criar soluções mais elegantes e otimizadas. À medida que você avança em sua jornada de programação em JavaScript, você descobrirá cada vez mais usos criativos e eficientes para esses operadores fundamentais.

## Referências e Dicas de Estudo

1. Mozilla Developer Network (MDN) - Operadores Lógicos:
   [https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_Operators#operadores_logicos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Expressions_and_Operators#operadores_logicos)

2. JavaScript.info - Operadores Lógicos:
   [https://javascript.info/logical-operators](https://javascript.info/logical-operators)

3. W3Schools - JavaScript Operators:
   [https://www.w3schools.com/js/js_operators.asp](https://www.w3schools.com/js/js_operators.asp)

4. Livro "Eloquent JavaScript" por Marijn Haverbeke:
   [https://eloquentjavascript.net/](https://eloquentjavascript.net/)

5. Curso online "JavaScript: Understanding the Weird Parts" na Udemy

Dicas de Estudo:

- Pratique regularmente escrevendo código que utiliza operadores lógicos.
- Experimente combinar operadores lógicos de diferentes maneiras e observe os resultados.
- Crie pequenos projetos que envolvam tomada de decisões complexas usando operadores lógicos.
- Participe de desafios de codificação online que envolvam lógica booleana.
- Estude o comportamento dos operadores lógicos com diferentes tipos de dados em JavaScript.
- Revise e analise código de outros desenvolvedores para ver como eles utilizam operadores lógicos em situações reais.

## Próxima Aula

Na próxima aula, mergulharemos nas estruturas de controle em JavaScript, começando com [estruturas de decisões](dia-06-estruturas-decisao.md) como `if`, `else if`, e `else`.
