# Dia 10: Laços de Repetição (for)

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender a estrutura e o funcionamento do laço for em JavaScript
2. Implementar laços for para iteração controlada por contagem
3. Utilizar laços for para percorrer arrays
4. Aplicar laços for aninhados para trabalhar com estruturas de dados multidimensionais
5. Comparar e escolher entre laços for e while em diferentes cenários

## 1. Estruturas de Repetição: "for"

### 1. for

#### 1.1 Explicação:

O loop `for` é uma das estruturas de repetição mais comuns em JavaScript. Ele permite que você execute um bloco de código repetidamente com base em uma condição específica. A sintaxe básica do `for` é composta por três partes principais: inicialização, condição e expressão final.

Sintaxe:
```javascript
for (inicialização; condição; expressão final) {
  // código a ser executado
}
```

- Inicialização: Esta parte é executada apenas uma vez, no início do loop. Geralmente, é usada para declarar e inicializar uma variável de controle.
- Condição: É avaliada antes de cada iteração. Se for verdadeira, o loop continua; se for falsa, o loop termina.
- Expressão final: É executada no final de cada iteração, geralmente usada para atualizar a variável de controle.

#### 1.2 Exemplo comentado:

```javascript
// Este exemplo imprime os números de 1 a 5
for (let i = 1; i <= 5; i++) {
  console.log(i);
}

// Explicação detalhada:
// - let i = 1: Inicializa a variável de controle 'i' com o valor 1
// - i <= 5: Define a condição de continuação do loop (enquanto i for menor ou igual a 5)
// - i++: Incrementa i em 1 a cada iteração
// - O código dentro do loop (console.log(i)) é executado 5 vezes, imprimindo os valores de 1 a 5
```

### 2. for...in

#### 2.1 Explicação:

O loop `for...in` é usado para iterar sobre as propriedades enumeráveis de um objeto. Ele é especialmente útil quando você precisa percorrer as chaves de um objeto, mas não é recomendado para arrays.

Sintaxe:
```javascript
for (variavel in objeto) {
  // código a ser executado
}
```

- variavel: A cada iteração, uma propriedade do objeto é atribuída a esta variável.
- objeto: O objeto cujas propriedades enumeráveis serão iteradas.

#### 2.2 Exemplo comentado:

```javascript
const pessoa = {
  nome: "Alice",
  idade: 30,
  profissao: "Engenheira"
};

for (let chave in pessoa) {
  console.log(chave + ": " + pessoa[chave]);
}

// Explicação detalhada:
// - O loop itera sobre cada propriedade do objeto 'pessoa'
// - A cada iteração, 'chave' recebe o nome de uma propriedade (nome, idade, profissao)
// - pessoa[chave] acessa o valor correspondente à chave atual
// - O resultado será:
//   nome: Alice
//   idade: 30
//   profissao: Engenheira
```

#### 2.3 Iterar em um arrays de objetos com `for in`

```javascript
// Array de objetos representando 5 pessoas
const pessoas = [
  { nome: "Alice", idade: 30, profissao: "Engenheira" },
  { nome: "Bob", idade: 25, profissao: "Designer" },
  { nome: "Carol", idade: 35, profissao: "Médica" },
  { nome: "David", idade: 28, profissao: "Programador" },
  { nome: "Eva", idade: 32, profissao: "Advogada" }
];

// Utilizando for...in para iterar sobre o array e os objetos
for (let index in pessoas) {
  console.log(`Pessoa ${parseInt(index) + 1}:`);
  
  // Objeto atual
  let pessoa = pessoas[index];
  
  // Iterando sobre as propriedades de cada objeto pessoa
  for (let prop in pessoa) {
console.log(`  ${prop}: ${pessoa[prop]}`);
  }
  
  console.log(); // Linha em branco para separar as pessoas
}

// Explicação detalhada:
// 1. O primeiro loop for...in (for (let index in pessoas)) itera sobre os índices do array 'pessoas'.
//- 'index' será uma string representando cada índice do array (0, 1, 2, 3, 4).
//- Usamos parseInt(index) + 1 para exibir números de pessoa começando em 1 ao invés de 0.

// 2. Dentro do primeiro loop, acessamos cada objeto pessoa com pessoas[index].

// 3. O segundo loop for...in (for (let prop in pessoa)) itera sobre as propriedades de cada objeto pessoa.
//- 'prop' será uma string representando cada nome de propriedade ('nome', 'idade', 'profissao').
//- Usamos pessoa[prop] para acessar o valor de cada propriedade.

// 4. O resultado será uma lista detalhada de cada pessoa e suas informações.

// Observações importantes:
// - for...in não é geralmente recomendado para arrays, pois pode incluir propriedades adicionadas ao protótipo do Array.
// - Neste caso, usamos for...in para demonstrar como ele funciona com estruturas aninhadas (array de objetos).
// - Para arrays, geralmente é preferível usar for...of ou métodos como forEach.

```

Este exemplo demonstra como o `for...in` pode ser usado para iterar tanto sobre os índices de um array quanto sobre as propriedades de objetos dentro desse array. Aqui estão alguns pontos importantes a considerar:

1. Uso com Arrays: Embora o `for...in` possa ser usado com arrays, como demonstrado aqui, não é geralmente recomendado para essa finalidade. Isso porque ele itera sobre todas as propriedades enumeráveis, o que pode incluir propriedades adicionadas ao protótipo do Array.

2. Estruturas Aninhadas: Este exemplo mostra como `for...in` pode ser útil para navegar em estruturas de dados mais complexas, como arrays de objetos.

3. Conversão de Índice: Note que usamos `parseInt(index) + 1` para exibir números de pessoa começando em 1. Isso é necessário porque `for...in` trata os índices do array como strings.

4. Flexibilidade: O `for...in` permite acessar tanto as chaves (índices ou nomes de propriedades) quanto os valores, o que pode ser útil em certos cenários.

5. Alternativas: Para arrays, geralmente é mais apropriado usar `for...of`, `forEach()`, ou um loop `for` tradicional. Para objetos individuais, `for...in` ou `Object.keys()` / `Object.entries()` são opções válidas.

Uma alternativa mais moderna e segura para iterar sobre este array de objetos seria:

```javascript
pessoas.forEach((pessoa, index) => {
  console.log(`Pessoa ${index + 1}:`);
  for (let [prop, value] of Object.entries(pessoa)) {
console.log(`  ${prop}: ${value}`);
  }
  console.log();
});
```

Este código usa `forEach` para o array e `Object.entries()` com destructuring para os objetos, oferecendo uma abordagem mais robusta e atual.

### 3. for...of

#### 3.1 Explicação:

O loop `for...of` foi introduzido no ECMAScript 6 (ES6) e é usado para iterar sobre objetos iteráveis como arrays, strings, maps, sets, etc. Diferente do `for...in`, que itera sobre as chaves, o `for...of` itera diretamente sobre os valores.

Sintaxe:
```javascript
for (variavel of iteravel) {
  // código a ser executado
}
```

- variavel: A cada iteração, o próximo valor do objeto iterável é atribuído a esta variável.
- iteravel: Um objeto que possui um protocolo de iteração, como um array ou uma string.

#### 3.2 Exemplo comentado:

```javascript
const frutas = ["maçã", "banana", "laranja"];

for (let fruta of frutas) {
  console.log(fruta);
}

// Explicação detalhada:
// - O loop itera sobre cada elemento do array 'frutas'
// - A cada iteração, 'fruta' recebe o valor de um elemento do array
// - O resultado será:
//   maçã
//   banana
//   laranja

// Exemplo com string:
const palavra = "JavaScript";

for (let letra of palavra) {
  console.log(letra);
}

// Explicação:
// - Aqui, o loop itera sobre cada caractere da string 'JavaScript'
// - Cada letra é impressa em uma linha separada
```

## 4. For vs While

- Use `for` quando souber o número exato de iterações ou estiver trabalhando com coleções de tamanho conhecido.
- Use `while` quando a condição de parada não for baseada em um contador ou quando não souber quantas iterações serão necessárias.

### 5. Exercícios Teóricos

#### a. Questão Dissertativa:
Explique a diferença principal entre o loop `for...in` e o loop `for...of` em JavaScript. Dê um exemplo de situação em que seria mais apropriado usar cada um deles.

#### b. Questão de Múltipla Escolha:
Qual é a saída do seguinte código?

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i);
}
```
```css
A) 1 2 3
B) 0 1 2
C) 0 1 2 3
D) 1 2
```

#### c. Questão de Caixa de Múltiplas Escolhas:
Quais das seguintes afirmações sobre o loop `for` em JavaScript são verdadeiras? (Selecione todas as corretas)

```markdown
□ A inicialização no loop `for` é executada apenas uma vez.
□ A condição no loop `for` é verificada antes de cada iteração.
□ A expressão final no loop `for` é executada após cada iteração.
□ O loop `for` sempre precisa ter os três componentes (inicialização, condição, expressão final) preenchidos.
□ É possível ter múltiplas expressões na inicialização e na expressão final do loop `for`.
```

#### d. Questões Verdadeiro ou Falso:

1. O loop `for...in` é recomendado para iterar sobre arrays em JavaScript.
    □ Verdadeiro
    □ Falso

2. O loop `for...of` pode ser usado para iterar sobre as propriedades de um objeto simples.
    □ Verdadeiro
    □ Falso
   Resposta: Falso

#### e. Questão de Associação:

Associe os loops com suas características mais apropriadas:

1. for
2. for...in
3. for...of

A. Melhor para iterar sobre os valores de um array  (  )
B. Permite controle preciso sobre o número de iterações (  )
C. Usado para iterar sobre as propriedades de um objeto (  )

### 6. Exercícios Práticos

#### Exercício 1

  ```js
// Exercício 1: Contador de Vogais
// Nível: Iniciante

// Descrição:
// Escreva uma função que receba uma string como entrada e retorne o número de vogais na string.
// Considere as vogais como 'a', 'e', 'i', 'o', 'u' (maiúsculas ou minúsculas).

// Dicas:
// - Use um loop for...of para iterar sobre cada caractere da string.
// - Converta cada caractere para minúsculo antes de verificar se é uma vogal.
// - Use um conjunto (Set) para armazenar as vogais e facilitar a verificação.

// Solução:
  ```
#### Exercício 2

```js
// Exercício 2: Soma de Números Pares
// Nível: Iniciante

// Descrição:
// Escreva uma função que receba um número n como entrada e retorne a soma de todos os números pares de 2 até n (inclusive).

// Dicas:
// - Use um loop for tradicional.
// - Verifique se cada número é par usando o operador módulo (%).
// - Acumule a soma em uma variável.

// Solução:
```

#### Exercício 3
```js
// Exercício 3: Gerador de Padrão de Asteriscos
// Nível: Intermediário

// Descrição:
// Escreva uma função que receba um número n como entrada e imprima um padrão de asteriscos em forma de triângulo.
// O padrão deve ter n linhas, com a primeira linha contendo 1 asterisco e a última contendo n asteriscos.

// Dicas:
// - Use loops aninhados: um para as linhas e outro para os asteriscos em cada linha.
// - Use console.log() para imprimir cada linha.
// - Lembre-se de que cada linha deve ter um número de asteriscos igual ao número da linha.

// Solução:
```


#### Exercício 4
```js
// Exercício 4: Encontrar Números Primos
// Nível: Intermediário

// Descrição:
// Escreva uma função que receba um número n como entrada e retorne um array contendo todos os números primos até n (inclusive).
// Um número primo é aquele que é divisível apenas por 1 e por ele mesmo.

// Dicas:
// - Use um loop for para verificar cada número de 2 até n.
// - Crie uma função auxiliar para verificar se um número é primo.
// - Use um array para armazenar os números primos encontrados.

// Solução:
```

#### Exercício 5
```js
// Exercício 5: Matriz em Espiral
// Nível: Intermediário/Avançado

// Descrição:
// Escreva uma função que receba um número n como entrada e retorne uma matriz n x n preenchida em espiral
// com números de 1 a n^2, começando do canto superior esquerdo e movendo-se no sentido horário.

// Dicas:
// - Crie uma matriz n x n preenchida com zeros.
// - Use quatro loops for para preencher cada lado da espiral.
// - Mantenha controle das bordas da espiral que já foram preenchidas.

// Solução:
```

### 7. Conclusão

As estruturas de repetição `for` em JavaScript são ferramentas poderosas e flexíveis para controlar o fluxo de execução em nossos programas. O `for` tradicional oferece controle preciso sobre as iterações, sendo útil em uma ampla variedade de situações. O `for...in` é especializado em iterar sobre as propriedades de objetos, tornando-o valioso para trabalhar com estruturas de dados complexas. Por fim, o `for...of` simplifica a iteração sobre coleções de dados, como arrays e strings, focando nos valores em vez das chaves ou índices.

Cada tipo de loop tem seu lugar e uso apropriado, e entender as diferenças entre eles permite que os desenvolvedores escolham a ferramenta certa para cada tarefa. Dominar essas estruturas de repetição é essencial para escrever código JavaScript eficiente e legível.

### 8. Referências e Dicas de Estudo

Referências:
1. MDN Web Docs: [JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
2. JavaScript.info: [Loops: while and for](https://javascript.info/while-for)
3. W3Schools: [JavaScript Loops](https://www.w3schools.com/js/js_loop_for.asp)

Dicas de Estudo:
1. Pratique implementando cada tipo de loop em diferentes cenários.
2. Experimente converter loops de um tipo para outro para entender melhor suas diferenças e semelhanças.
3. Estude casos de uso reais onde cada tipo de loop é mais apropriado.
4. Crie pequenos projetos que envolvam a manipulação de arrays e objetos usando diferentes tipos de loops.
5. Participe de desafios de codificação online que envolvam loops para aprimorar suas habilidades.
6. Revise e analise código de outros desenvolvedores para ver como eles utilizam loops em seus projetos.
7. Experimente combinar loops com outros conceitos de JavaScript, como funções e condicionais, para criar lógicas mais complexas.

## Próxima Aula

Na próxima aula, exploraremos as [`arrays`](dia-10-arrays-introducao.md) em JavaScript, que nos permitirão organizar e reutilizar código de forma eficiente.
