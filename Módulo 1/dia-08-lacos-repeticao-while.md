# Dia 8: Laços de Repetição (while)

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o conceito de laços de repetição e sua importância na programação
2. Implementar e utilizar o laço while em JavaScript
3. Controlar a execução de laços usando break e continue
4. Evitar loops infinitos e entender como depurá-los
5. Aplicar laços while em situações práticas de programação

## 1. Introdução aos Laços de Repetição

Laços de repetição, ou loops, são estruturas que permitem executar um bloco de código várias vezes. Eles são fundamentais para automatizar tarefas repetitivas e processar coleções de dados.

O loop `while` é uma estrutura de repetição fundamental em JavaScript que permite executar um bloco de código repetidamente enquanto uma condição específica for verdadeira.

### Características principais:
- Utilizado quando não sabemos antecipadamente quantas vezes um bloco de código precisa ser executado.
- A condição é verificada antes de cada iteração do loop.
- Se a condição for falsa logo no início, o bloco de código dentro do `while` nunca será executado.
- É crucial garantir que a condição eventualmente se torne falsa para evitar loops infinitos.

## 2. Sintaxe do while

A sintaxe do `while` é simples e direta:

```javascript
while (condição) {
    // código a ser executado
}
```

### Explicação detalhada:
- A palavra-chave `while` indica o início da estrutura de repetição.
- A condição é uma expressão que retorna um valor booleano (verdadeiro ou falso).
- O bloco de código é delimitado por chaves `{}` e contém as instruções a serem repetidas.

### Exemplo comentado:
```javascript
let contador = 0;  // Inicialização

while (contador < 5) {  // Condição
    console.log("Contagem: " + contador);  // Corpo do laço
    contador++;  // Atualização
}
console.log("Loop concluído!");  // Executa após o término do loop
```

## 3. Anatomia de um Laço While

1. **Inicialização**: Geralmente feita antes do laço (ex: `let contador = 0;`)
2. **Condição**: Avaliada no início de cada iteração (`contador < 5`)
3. **Corpo do laço**: Código executado em cada iteração
4. **Atualização**: Geralmente no final do corpo do laço (`contador++`)

## 4. Controle de fluxo dentro do while

Dentro de um loop `while`, podemos usar instruções de controle de fluxo para modificar o comportamento padrão do loop.

### Break
O `break` é usado para sair imediatamente de um laço.

Exemplo:
```javascript
let i = 0;
while (true) {
    if (i >= 5) {
        break;
    }
    console.log(i);
    i++;
}
```

### Continue
O `continue` pula o resto da iteração atual e passa para a próxima verificação da condição.

Exemplo:
```javascript
let i = 0;
while (i < 5) {
    i++;
    if (i === 3) {
        continue;
    }
    console.log(i);
}
```
Saída:
```
1
2
4
5
```

## 5. Loop while vs. do...while

O loop `while` tem uma variação chamada `do...while`, que garante que o bloco de código seja executado pelo menos uma vez.

### Explicação:
- No `while`, a condição é verificada antes da primeira execução.
- No `do...while`, o bloco de código é executado uma vez antes de verificar a condição.

### Exemplo:
```javascript
// Exemplo de while
let i = 5;
while (i < 5) {
    console.log(i);
    i++;
}
// Não imprime nada, pois a condição é falsa desde o início

// Exemplo de do...while
let j = 5;
do {
    console.log(j);
    j++;
} while (j < 5);
// Imprime 5, pois executa uma vez antes de verificar a condição
```

## 6. Casos de uso comuns para while

O loop `while` é particularmente útil em certas situações específicas:

- Leitura de dados: Quando você precisa ler dados até que uma certa condição seja atendida.
- Processamento de listas de tamanho desconhecido: Quando você não sabe quantos itens precisará processar.
- Jogos: Para manter o jogo rodando até que certas condições sejam atingidas.
- Validação de entrada: Para continuar solicitando entrada até que seja válida.

### Exemplo: Jogo de Adivinhação
```javascript
let numeroSecreto = 7;
let tentativa = 0;
let acertou = false;

while (!acertou) {
    tentativa++;
    let palpite = parseInt(prompt("Adivinhe o número (entre 1 e 10):"));

    if (palpite === numeroSecreto) {
        acertou = true;
        console.log(`Parabéns! Você acertou em ${tentativa} tentativas.`);
    } else {
        console.log("Tente novamente!");
    }
}
```

## 7. Evitando Loops Infinitos

Um loop infinito ocorre quando a condição do while nunca se torna falsa. Para evitar:

1. Certifique-se de que a condição eventualmente se tornará falsa
2. Use um contador ou uma condição de saída
3. Verifique se a variável de controle está sendo atualizada corretamente

Exemplo de loop infinito (não execute!):
```javascript
let x = 1;
while (x > 0) {
    console.log(x);
    x++;  // x sempre será maior que 0
}
```

## Exercícios Teóricos

### Questões Dissertativas

1. Explique a diferença principal entre um loop `while` e um loop `for` em JavaScript.

2. Em que situações você consideraria usar um loop `while` em vez de outras estruturas de repetição?

3. Descreva o que é um loop infinito e como evitá-lo ao usar a estrutura `while`.

### Questões de Múltipla Escolha

1. Qual é a sintaxe correta para um loop `while` em JavaScript?
   a) `while (condição) { }`
   b) `while { condição }`
   c) `while: condição { }`
   d) `while condição do { }`

2. O que acontece se a condição de um loop `while` for falsa desde o início?
   a) O loop executa uma vez e então para
   b) O loop executa infinitamente
   c) O loop não executa nenhuma vez
   d) Ocorre um erro de sintaxe

### Questões de Caixa de Múltiplas Escolhas

1. Quais das seguintes afirmações sobre o loop `while` são verdadeiras? (Selecione todas as aplicáveis)
   [ ] A condição é verificada no início de cada iteração
   [ ] O loop sempre executa pelo menos uma vez
   [ ] Pode-se usar `break` para sair do loop prematuramente
   [ ] A condição deve ser uma expressão booleana

2. Quais das seguintes são boas práticas ao usar loops `while`? (Selecione todas as aplicáveis)
   [ ] Garantir que a condição eventualmente se torne falsa
   [ ] Usar variáveis de controle para gerenciar o loop
   [ ] Evitar modificar a variável de controle fora do loop
   [ ] Preferir `while` sobre `for` em todas as situações

### Questões Verdadeiro ou Falso

1. Um loop `while` sempre executa seu bloco de código pelo menos uma vez. (V/F)

2. É possível usar múltiplas condições em um único loop `while`. (V/F)

3. A palavra-chave `continue` faz com que o loop `while` termine imediatamente. (V/F)

4. Um loop `while` pode ser transformado em um loop `for` equivalente em todos os casos. (V/F)

### Questões de Associação

Associe os conceitos da coluna A com suas descrições na coluna B:

Coluna A:

1. while
2. do...while
3. break
4. continue
5. Condição

Coluna B:
a) Verifica-se no início de cada iteração
b) Executa o bloco pelo menos uma vez antes de verificar a condição
c) Sai imediatamente do loop
d) Pula para a próxima iteração do loop
e) Estrutura de repetição básica em JavaScript

## Exercícios Práticos

### Nível Iniciante

1. Contagem Regressiva
   Crie um programa que faça uma contagem regressiva de 10 até 1 usando um loop while.

2. Soma de Números
   Escreva um programa que some todos os números de 1 a 100 usando um loop while.

3. Tabuada
   Crie um programa que imprima a tabuada de um número fornecido pelo usuário.

### Nível Intermediário

1. Sequência de Fibonacci
   Crie um programa que gere os primeiros 20 números da sequência de Fibonacci usando um loop while.

2. Validação de Senha
   Implemente um sistema que peça ao usuário para criar uma senha que atenda a certos critérios (por exemplo, pelo menos 8 caracteres, contendo letras e números).

## Conclusão

O loop `while` é uma estrutura de repetição poderosa e flexível em JavaScript. Ele permite que os desenvolvedores criem loops baseados em condições, oferecendo grande controle sobre o fluxo de execução do programa. A chave para usar o `while` efetivamente está em entender bem seu funcionamento, evitar armadilhas comuns como loops infinitos, e saber quando ele é a melhor escolha em comparação com outras estruturas de loop.

## Recursos Adicionais

1. [MDN Web Docs: While Statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)
2. [JavaScript.info: While and For Loops](https://javascript.info/while-for)
3. [W3Schools: JavaScript While Loop](https://www.w3schools.com/js/js_loop_while.asp)
4. [Eloquent JavaScript: Chapter 2: Program Structure](https://eloquentjavascript.net/02_program_structure.html)

Dicas de Estudo:
- Pratique escrevendo diferentes tipos de loops `while` para resolver problemas variados.
- Compare implementações usando `while` com outras estruturas de loop.
- Experimente com ferramentas de depuração para visualizar a execução passo a passo de seus loops `while`.
- Participe de comunidades online de programação para discutir e aprender mais sobre técnicas avançadas de uso de loops em JavaScript.s

## Próxima Aula

Na próxima aula, exploraremos outro tipo de laço de repetição em JavaScript: o laço [`for`](dia-09-lacos-repeticao-for.md), que oferece uma sintaxe mais compacta para iterações controladas por contagem.
