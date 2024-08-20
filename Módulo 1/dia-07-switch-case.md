# Dia 7: Estruturas Condicionais Avançadas (Switch Case)

## Objetivos de Aprendizagem
Ao final desta lição, você será capaz de:
1. Entender o propósito e a sintaxe da estrutura switch case
2. Implementar switch case para lidar com múltiplas condições
3. Utilizar a cláusula break corretamente dentro do switch
4. Aplicar a cláusula default para tratar casos não especificados
5. Comparar switch case com estruturas if...else if e escolher a mais apropriada

## 1. Introdução ao Switch Case

A estrutura `switch case` é uma alternativa às múltiplas declarações `if...else if` quando se está comparando uma variável com vários valores possíveis.

## 2. Sintaxe do Switch Case

```javascript
switch (expressão) {
  case valor1:
    // código a ser executado
    break;
  case valor2:
    // código a ser executado
    break;
  // ...
  default:
    // código a ser executado se nenhum caso corresponder
}
```

## 3. Exemplo Básico de Switch Case

Vamos começar com um exemplo simples que verifica o dia da semana:

```javascript
let diaDaSemana = 3;
let nomeDoDia;

switch (diaDaSemana) {
  case 1:
    nomeDoDia = "Domingo";
    break;
  case 2:
    nomeDoDia = "Segunda-feira";
    break;
  case 3:
    nomeDoDia = "Terça-feira";
    break;
  case 4:
    nomeDoDia = "Quarta-feira";
    break;
  case 5:
    nomeDoDia = "Quinta-feira";
    break;
  case 6:
    nomeDoDia = "Sexta-feira";
    break;
  case 7:
    nomeDoDia = "Sábado";
    break;
  default:
    nomeDoDia = "Dia inválido";
}

console.log(nomeDoDia); // Saída: "Terça-feira"
```

## 4. A Importância do Break

A cláusula `break` é crucial no `switch`. Sem ela, a execução continuará para os próximos casos, mesmo que não correspondam.

Exemplo sem break:

```javascript
let fruta = "maçã";
let categoria;

switch (fruta) {
  case "maçã":
    categoria = "Fruta";
    // Sem break, a execução continua
  case "cenoura":
    categoria = "Vegetal";
    // Sem break, a execução continua
  case "bife":
    categoria = "Carne";
}

console.log(categoria); // Saída: "Carne"
```

## 5. Agrupando Casos

Você pode agrupar casos que compartilham o mesmo código:

```javascript
let mes = 7;
let estacao;

switch (mes) {
  case 12:
  case 1:
  case 2:
    estacao = "Verão";
    break;
  case 3:
  case 4:
  case 5:
    estacao = "Outono";
    break;
  case 6:
  case 7:
  case 8:
    estacao = "Inverno";
    break;
  case 9:
  case 10:
  case 11:
    estacao = "Primavera";
    break;
  default:
    estacao = "Mês inválido";
}

console.log(estacao); // Saída: "Inverno"
```

## 6. Usando Expressões no Switch

O `switch` pode usar expressões, não apenas valores simples:

```javascript
let idade = 18;

switch (true) {
  case idade < 13:
    console.log("Criança");
    break;
  case idade < 18:
    console.log("Adolescente");
    break;
  case idade >= 18:
    console.log("Adulto");
    break;
}
// Saída: "Adulto"
```

## 7. Switch vs. If...Else If

O `switch` é geralmente mais legível e eficiente quando se compara uma única variável com muitos valores possíveis. Use `if...else if` para comparações mais complexas ou quando as condições não são igualdades simples.

## Exercício Prático

Crie um programa que converte notas numéricas em conceitos:
- A: 90-100
- B: 80-89
- C: 70-79
- D: 60-69
- F: 0-59

Use `switch` com expressões para implementar esta lógica.

Exemplo de solução:

```javascript
let nota = 85;
let conceito;

switch (true) {
  case nota >= 90 && nota <= 100:
    conceito = 'A';
    break;
  case nota >= 80 && nota < 90:
    conceito = 'B';
    break;
  case nota >= 70 && nota < 80:
    conceito = 'C';
    break;
  case nota >= 60 && nota < 70:
    conceito = 'D';
    break;
  case nota >= 0 && nota < 60:
    conceito = 'F';
    break;
  default:
    conceito = 'Nota inválida';
}

console.log(`Sua nota ${nota} corresponde ao conceito ${conceito}.`);
```

## Dicas Úteis

1. Sempre use `break` ao final de cada caso, a menos que você intencionalmente queira que a execução continue para o próximo caso.
2. Use o `default` para lidar com casos inesperados ou inválidos.
3. Considere usar `switch` quando tiver muitas condições baseadas no valor de uma única variável.
4. Lembre-se que o `switch` usa comparação estrita (`===`), então tenha cuidado com tipos de dados.

## Recursos Adicionais

- [Switch (MDN em português)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/switch)
- [Estrutura Switch Case em JavaScript (DevMedia em português)](https://www.devmedia.com.br/javascript-switch/39761)
- [JavaScript Switch Statement (W3Schools em português)](https://www.w3schools.com/js/js_switch.asp)

## Próxima Aula

Na próxima aula, começaremos a explorar as estruturas de repetição em JavaScript, começando com o laço `while`.

