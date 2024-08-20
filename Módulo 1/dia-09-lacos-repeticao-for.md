# Dia 9: Laços de Repetição (for)

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender a estrutura e o funcionamento do laço for em JavaScript
2. Implementar laços for para iteração controlada por contagem
3. Utilizar laços for para percorrer arrays
4. Aplicar laços for aninhados para trabalhar com estruturas de dados multidimensionais
5. Comparar e escolher entre laços for e while em diferentes cenários

## 1. Introdução ao Laço For

O laço `for` é uma estrutura de repetição mais compacta e frequentemente usada quando se sabe antecipadamente o número de iterações necessárias.

Sintaxe:
```javascript
for (inicialização; condição; incremento) {
    // código a ser executado
}
```

## 2. Anatomia de um Laço For

1. **Inicialização**: Executada uma vez no início do laço
2. **Condição**: Verificada antes de cada iteração
3. **Incremento**: Executado no final de cada iteração
4. **Corpo do laço**: Código executado em cada iteração

Exemplo básico:
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```
Saída:
```
0
1
2
3
4
```

## 3. Utilizando For com Arrays

O laço `for` é muito útil para percorrer arrays:

```javascript
let frutas = ["maçã", "banana", "laranja", "uva", "manga"];

for (let i = 0; i < frutas.length; i++) {
    console.log(`Fruta ${i + 1}: ${frutas[i]}`);
}
```
Saída:
```
Fruta 1: maçã
Fruta 2: banana
Fruta 3: laranja
Fruta 4: uva
Fruta 5: manga
```

## 4. Laços For Aninhados

Laços `for` aninhados são úteis para trabalhar com estruturas de dados multidimensionais:

```javascript
let matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

for (let i = 0; i < matriz.length; i++) {
    for (let j = 0; j < matriz[i].length; j++) {
        console.log(`Elemento na posição [${i}][${j}]: ${matriz[i][j]}`);
    }
}
```

## 5. Variações do For

### For...in
Usado para iterar sobre as propriedades enumeráveis de um objeto:

```javascript
let pessoa = {nome: "João", idade: 30, profissao: "Desenvolvedor"};

for (let propriedade in pessoa) {
    console.log(`${propriedade}: ${pessoa[propriedade]}`);
}
```

### For...of
Usado para iterar sobre elementos de coleções iteráveis (como arrays):

```javascript
let numeros = [1, 2, 3, 4, 5];

for (let numero of numeros) {
    console.log(numero);
}
```

## 6. Break e Continue no For

Assim como no `while`, podemos usar `break` e `continue` em laços `for`:

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // Sai do laço quando i é 5
    }
    if (i % 2 === 0) {
        continue; // Pula os números pares
    }
    console.log(i);
}
```
Saída:
```
1
3
```

## 7. For vs While

- Use `for` quando souber o número exato de iterações ou estiver trabalhando com coleções de tamanho conhecido.
- Use `while` quando a condição de parada não for baseada em um contador ou quando não souber quantas iterações serão necessárias.

## Exercício Prático

Crie um programa que simule um jogo de batalha naval simples:
1. Crie uma matriz 5x5 para representar o tabuleiro
2. Posicione 3 navios aleatoriamente no tabuleiro (podem ser representados por '1')
3. Use um laço for para permitir que o jogador faça 10 tentativas de acertar os navios
4. A cada tentativa, peça ao jogador as coordenadas (linha e coluna)
5. Informe se acertou um navio ou água
6. No final, mostre quantos navios foram acertados

Exemplo de solução:

```javascript
// Criando o tabuleiro
let tabuleiro = Array(5).fill().map(() => Array(5).fill(0));

// Posicionando os navios
for (let i = 0; i < 3; i++) {
    let linha, coluna;
    do {
        linha = Math.floor(Math.random() * 5);
        coluna = Math.floor(Math.random() * 5);
    } while (tabuleiro[linha][coluna] === 1);
    tabuleiro[linha][coluna] = 1;
}

let naviosAcertados = 0;

// Jogo
for (let tentativa = 1; tentativa <= 10; tentativa++) {
    console.log(`Tentativa ${tentativa}`);
    let linha = parseInt(prompt("Digite a linha (0-4):"));
    let coluna = parseInt(prompt("Digite a coluna (0-4):"));
    
    if (tabuleiro[linha][coluna] === 1) {
        console.log("Você acertou um navio!");
        naviosAcertados++;
        tabuleiro[linha][coluna] = 'X';  // Marca como acertado
    } else {
        console.log("Água!");
    }
}

console.log(`Fim do jogo! Você acertou ${naviosAcertados} navio(s).`);
```

## Dicas Úteis

1. Use nomes descritivos para variáveis de controle (ex: `for (let index = 0;...)` em vez de `for (let i = 0;...)`).
2. Evite modificar a variável de controle dentro do corpo do laço.
3. Prefira `for...of` para iteração simples sobre arrays.
4. Use `break` e `continue` com cautela para não tornar o código difícil de entender.

## Recursos Adicionais

- [Laços e iterações (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Loops_and_iteration#for_statement)
- [JavaScript for Loop (W3Schools em português)](https://www.w3schools.com/js/js_loop_for.asp)
- [Estruturas de repetição em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-estruturas-de-repeticao/41018)

## Próxima Aula

Na próxima aula, exploraremos as funções em JavaScript, que nos permitirão organizar e reutilizar código de forma eficiente.

