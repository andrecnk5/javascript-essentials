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

## 2. O Laço While

O laço `while` executa um bloco de código enquanto uma condição especificada for verdadeira.

Sintaxe:
```javascript
while (condição) {
    // código a ser executado
}
```

Exemplo básico:
```javascript
let contador = 0;
while (contador < 5) {
    console.log(contador);
    contador++;
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

## 3. Anatomia de um Laço While

1. **Inicialização**: Geralmente feita antes do laço (ex: `let contador = 0;`)
2. **Condição**: Avaliada no início de cada iteração (`contador < 5`)
3. **Corpo do laço**: Código executado em cada iteração
4. **Atualização**: Geralmente no final do corpo do laço (`contador++`)

## 4. Exemplo Prático: Adivinhe o Número

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

## 5. Controlando a Execução do Laço

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
O `continue` pula para a próxima iteração do laço.

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

## 6. Evitando Loops Infinitos

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

## 7. Do...While

Uma variação do while é o `do...while`, que garante que o código seja executado pelo menos uma vez.

Sintaxe:
```javascript
do {
    // código a ser executado
} while (condição);
```

Exemplo:
```javascript
let i = 0;
do {
    console.log(i);
    i++;
} while (i < 5);
```

## Exercício Prático

Crie um programa que simule um caixa eletrônico:
1. Comece com um saldo de R$ 1000
2. Em um laço while, pergunte ao usuário que operação deseja fazer: sacar, depositar ou ver saldo
3. Implemente cada operação
4. Continue perguntando até que o usuário escolha sair
5. Use break para sair do loop quando o usuário escolher sair

Exemplo de solução:

```javascript
let saldo = 1000;
let continuar = true;

while (continuar) {
    let operacao = prompt("Escolha uma operação: sacar, depositar, ver saldo ou sair");
    
    switch (operacao) {
        case "sacar":
            let valorSaque = parseFloat(prompt("Quanto deseja sacar?"));
            if (valorSaque <= saldo) {
                saldo -= valorSaque;
                console.log(`Saque de R$ ${valorSaque} realizado. Novo saldo: R$ ${saldo}`);
            } else {
                console.log("Saldo insuficiente");
            }
            break;
        case "depositar":
            let valorDeposito = parseFloat(prompt("Quanto deseja depositar?"));
            saldo += valorDeposito;
            console.log(`Depósito de R$ ${valorDeposito} realizado. Novo saldo: R$ ${saldo}`);
            break;
        case "ver saldo":
            console.log(`Seu saldo atual é R$ ${saldo}`);
            break;
        case "sair":
            continuar = false;
            console.log("Obrigado por usar nosso caixa eletrônico!");
            break;
        default:
            console.log("Operação inválida");
    }
}
```

## Dicas Úteis

1. Sempre tenha uma condição de saída clara para seus laços while.
2. Use variáveis de controle para gerenciar a execução do laço.
3. Evite modificar a variável de controle dentro do corpo do laço, a menos que seja intencional.
4. Use do...while quando precisar que o código seja executado pelo menos uma vez.

## Recursos Adicionais

- [Laços e iterações (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Loops_and_iteration)
- [JavaScript while Loop (W3Schools em português)](https://www.w3schools.com/js/js_loop_while.asp)
- [Estruturas de repetição em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-estruturas-de-repeticao/41015)

## Próxima Aula

Na próxima aula, exploraremos outro tipo de laço de repetição em JavaScript: o laço `for`, que oferece uma sintaxe mais compacta para iterações controladas por contagem.

