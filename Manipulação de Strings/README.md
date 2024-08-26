# Plano de Aula: Strings em JavaScript

## Objetivo da Aula
Ao final desta aula, o aluno será capaz de compreender, manipular e utilizar eficientemente strings em JavaScript, incluindo criação, métodos comuns, e boas práticas.

## Duração Estimada
3 horas

## Pré-requisitos
- Conhecimento básico de JavaScript
- Familiaridade com variáveis e tipos de dados primitivos

## Materiais Necessários
- Ambiente de desenvolvimento JavaScript (navegador com console ou Node.js)
- Editor de código (ex: Visual Studio Code, Sublime Text)

## Conteúdo

### 1. Introdução às Strings (15 minutos)
- Definição de string
- Importância das strings em programação

### 2. Criação de Strings (20 minutos)
- Usando aspas simples
- Usando aspas duplas
- Usando template literals (backticks)
- Diferenças e quando usar cada uma

### 3. Propriedades de Strings (15 minutos)
- length
- Acesso a caracteres individuais (notação de colchetes)

### 4. Métodos Comuns de Strings (60 minutos)
- toLowerCase() e toUpperCase()
- trim(), trimStart(), trimEnd()
- charAt() e charCodeAt()
- indexOf() e lastIndexOf()
- slice(), substring(), e substr()
- replace() e replaceAll()
- split()
- includes(), startsWith(), e endsWith()

### 5. Concatenação e Interpolação de Strings (30 minutos)
- Usando o operador +
- Usando o método concat()
- Template literals e interpolação

### 6. Strings e Unicode (20 minutos)
- Representação de caracteres especiais
- Escape characters (\n, \t, etc.)
- Emoji e outros caracteres Unicode

### 7. Imutabilidade de Strings (15 minutos)
- Conceito de imutabilidade
- Implicações práticas

### 8. Comparação de Strings (15 minutos)
- Operadores de comparação (==, ===, <, >)
- Método localeCompare()

### 9. Exercícios Práticos (30 minutos)
- Manipulação de strings
- Resolução de problemas comuns envolvendo strings

### 10. Boas Práticas e Otimização (15 minutos)
- Performance em operações com strings
- Quando usar strings vs. outros tipos de dados

### 11. Recapitulação e Dúvidas (15 minutos)

## Metodologia
- Exposição teórica com exemplos práticos
- Demonstrações de código ao vivo
- Exercícios hands-on
- Discussões em grupo

## Avaliação
- Exercícios práticos durante a aula
- Projeto: Criar uma função que realiza múltiplas manipulações em uma string

## Recursos Adicionais
- MDN Web Docs: JavaScript String
- "Eloquent JavaScript" por Marijn Haverbeke, capítulo sobre Strings e Arrays
- JavaScript.info: Strings

## Próximos Passos
- Explorar métodos avançados de manipulação de strings
- Estudar expressões regulares para manipulação de strings mais complexa

## Exercícios Práticos Sugeridos

1. Crie uma função que inverta uma string.

2. Implemente uma função que verifique se uma string é um palíndromo.

3. Desenvolva uma função que conte o número de ocorrências de uma substring em uma string.

4. Crie uma função que converta uma string em "camelCase".

5. Implemente uma função que remova todos os espaços em branco de uma string.

6. Desenvolva uma função que capitalize a primeira letra de cada palavra em uma frase.

7. Crie uma função que mascare parte de um número de cartão de crédito, deixando apenas os últimos 4 dígitos visíveis.

8. Implemente uma função que verifique se uma string contém todas as letras do alfabeto.

9. Desenvolva uma função que converta uma string em um "slug" para URL (ex: "Olá Mundo" -> "ola-mundo").

10. Crie uma função que encontre a palavra mais longa em uma frase.

## Projeto Final

Desenvolva uma classe `StringManipulator` que inclua métodos para realizar as seguintes operações:

1. Inverter a string
2. Contar o número de vogais e consoantes
3. Converter para camelCase
4. Verificar se é um palíndromo
5. Capitalizar a primeira letra de cada palavra
6. Remover caracteres duplicados
7. Gerar um acrônimo a partir de uma frase
8. Codificar a string em ROT13
9. Encontrar todas as substrings palindrômicas
10. Formatar um número como uma string de telefone
