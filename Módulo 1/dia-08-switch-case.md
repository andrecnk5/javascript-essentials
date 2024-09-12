# Dia 8: Estruturas Condicionais Avançadas (Switch Case)

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Entender o propósito e a sintaxe da estrutura switch case
2. Implementar switch case para lidar com múltiplas condições
3. Utilizar a cláusula break corretamente dentro do switch
4. Aplicar a cláusula default para tratar casos não especificados
5. Comparar switch case com estruturas if...else if e escolher a mais apropriada

## 1. Introdução ao switch case

O `switch case` é uma estrutura de controle de fluxo em JavaScript que permite executar diferentes blocos de código com base no valor de uma expressão. É uma alternativa mais legível e eficiente ao uso de múltiplas instruções `if...else if` quando se deseja comparar uma variável com vários valores possíveis.

### Exemplo comentado:

```javascript
let diaDaSemana = 3;
let nomeDoDia;

switch (diaDaSemana) {
    case 1: // Se diaDaSemana for igual a 1
        nomeDoDia = "Domingo";
        break; // Encerra a execução do switch
    case 2:
        nomeDoDia = "Segunda-feira";
        break;
    case 3:
        nomeDoDia = "Terça-feira";
        break;
    // ... outros casos ...
    default: // Caso nenhum dos casos anteriores seja verdadeiro
        nomeDoDia = "Dia inválido";
}

console.log(nomeDoDia); // Saída: Terça-feira
```

## 2. Sintaxe do switch case

A estrutura básica do `switch case` consiste em:

1. A palavra-chave `switch`
2. Uma expressão entre parênteses
3. Um bloco de código delimitado por chaves `{}`
4. Múltiplas cláusulas `case` seguidas por um valor e dois pontos `:`
5. Blocos de código para cada `case`
6. A palavra-chave `break` ao final de cada bloco (opcional, mas geralmente necessária)
7. Uma cláusula `default` opcional para lidar com casos não especificados

### Exemplo comentado

```javascript
switch (expressao) {
    case valor1: // Se expressao === valor1
        // Código a ser executado
        break;
    case valor2: // Se expressao === valor2
        // Código a ser executado
        break;
    // ... mais casos ...
    default: // Se nenhum caso anterior for verdadeiro
        // Código a ser executado
}
```

## 3. Comportamento de fall-through

No `switch case`, se não houver um `break` ao final de um `case`, a execução continuará para o próximo `case`, mesmo que sua condição não seja verdadeira. Isso é chamado de "fall-through" e pode ser útil em algumas situações, mas também pode causar bugs se não for intencional.

### Exemplo comentado

```javascript
let tipoFruta = "maçã";
let categoria;

switch (tipoFruta) {
    case "maçã":
    case "pera":
    case "uva":
        categoria = "Fruta comum";
        break; // Sem este break, a execução continuaria para o próximo case
    case "kiwi":
    case "mangostão":
        categoria = "Fruta exótica";
        break;
    default:
        categoria = "Não classificado";
}

console.log(categoria); // Saída: Fruta comum
```

## 4. Comparação com if...else

O `switch case` é mais adequado quando se compara uma única variável com múltiplos valores constantes. Para condições mais complexas ou comparações de intervalos, o `if...else` pode ser mais apropriado.

### Exemplo comentado

```javascript
// Usando switch case
let nota = 85;
let conceito;

switch (true) {
    case nota >= 90:
        conceito = "A";
        break;
    case nota >= 80:
        conceito = "B";
        break;
    case nota >= 70:
        conceito = "C";
        break;
    default:
        conceito = "D";
}

console.log(conceito); // Saída: B

// Equivalente usando if...else
if (nota >= 90) {
    conceito = "A";
} else if (nota >= 80) {
    conceito = "B";
} else if (nota >= 70) {
    conceito = "C";
} else {
    conceito = "D";
}

console.log(conceito); // Saída: B
```

## 5. Switch case com expressões

A partir do ECMAScript 2015 (ES6), é possível usar expressões mais complexas nos casos do `switch`, desde que elas resultem em valores que possam ser comparados com a expressão do `switch`.

### Exemplo comentado

```javascript
let temperatura = 25;

switch (true) {
    case temperatura < 0:
        console.log("Congelante");
        break;
    case temperatura >= 0 && temperatura < 20:
        console.log("Frio");
        break;
    case temperatura >= 20 && temperatura < 30:
        console.log("Agradável");
        break;
    default:
        console.log("Quente");
}
// Saída: Agradável
```

## Exercícios Teóricos

### Questão Dissertativa

1. Explique a diferença entre o uso de `switch case` e múltiplos `if...else if` em termos de legibilidade e performance.

### Questão de Múltipla Escolha

2. Qual é a função principal da palavra-chave `break` em um `switch case`?

   1. [ ] a) Iniciar um novo bloco de código
   2. [ ] b) Encerrar a execução do switch e passar para o código seguinte
   3. [ ] c) Definir um caso padrão
   4. [ ] d) Comparar o valor da expressão com o caso

### Questão de Caixa de Múltiplas Escolhas

3. Quais das seguintes afirmações sobre o `switch case` em JavaScript são verdadeiras? (Selecione todas as aplicáveis)

   1. [ ] O `switch case` pode ser usado com tipos de dados não primitivos como objetos.
   2. [ ] A cláusula `default` é obrigatória em todo `switch case`.
   3. [ ] Se não houver `break` ao final de um `case`, a execução continuará para o próximo `case`.
   4. [ ] O `switch case` é mais eficiente que `if...else` para comparar uma variável com muitos valores possíveis.

### Questão Verdadeiro ou Falso

4. Determine se as seguintes afirmações são verdadeiras ou falsas:

   1. [ ] a) O `switch case` só pode ser usado com valores numéricos.
   2. [ ] b) É possível ter múltiplos `case` que executem o mesmo bloco de código.
   3. [ ] c) A cláusula `default` deve sempre ser a última no `switch case`.
   4. [ ] d) O `break` é sempre necessário ao final de cada `case`.

### Questão de Associação

5. Associe os conceitos da coluna da esquerda com suas descrições na coluna da direita:

| Conceito | Descrição |
|----------|-----------|
| 1. switch | A. Palavra-chave que define um caso específico |
| 2. case   | B. Bloco executado se nenhum caso corresponder |
| 3. break  | C. Inicia a estrutura de decisão |
| 4. default| D. Previne a execução do próximo caso |

## Conclusão

O `switch case` é uma estrutura de controle poderosa em JavaScript que oferece uma alternativa elegante e eficiente para múltiplas comparações. Sua sintaxe clara e capacidade de agrupar casos relacionados tornam o código mais legível e manutenível. Embora tenha algumas limitações, como a necessidade de usar `break` para evitar o fall-through indesejado, o `switch case` permanece uma ferramenta valiosa no arsenal de qualquer desenvolvedor JavaScript.

## Referências e Dicas de Estudo

1. MDN Web Docs: [switch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch)
2. JavaScript.info: [The "switch" statement](https://javascript.info/switch)
3. W3Schools: [JavaScript Switch Statement](https://www.w3schools.com/js/js_switch.asp)
4. Eloquent JavaScript: [Control Flow](https://eloquentjavascript.net/02_program_structure.html)
5. You Don't Know JS: [Types & Grammar](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/types%20%26%20grammar/ch5.md)

Dicas de estudo:

- Pratique escrevendo `switch case` para diferentes cenários.
- Compare implementações usando `switch case` e `if...else` para entender melhor as diferenças.
- Experimente com o comportamento de fall-through para entender seus usos e potenciais armadilhas.
- Leia o código de outros desenvolvedores para ver como eles usam `switch case` em projetos reais.

## Próxima Aula

Na próxima aula, começaremos a explorar as estruturas de repetição em JavaScript, começando com o laço [`while`](dia-08-lacos-repeticao-while.md).
