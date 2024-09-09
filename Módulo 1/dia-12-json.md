# Dia 12: JSON (JavaScript Object Notation) - Detalhado

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

1. Compreender profundamente o que é JSON e sua importância no desenvolvimento web
2. Criar e ler estruturas de dados complexas em formato JSON
3. Dominar a conversão entre objetos JavaScript e strings JSON
4. Trabalhar com dados JSON em diversas aplicações práticas
5. Entender as nuances, limitações e melhores práticas ao usar JSON
6. Manipular JSON em cenários avançados, incluindo aninhamento e arrays

## 1. O que é JSON?

JSON (JavaScript Object Notation) é um formato de dados leve, independente de linguagem e fácil de ler e escrever. Desenvolvido por Douglas Crockford, JSON tornou-se um padrão para troca de dados na web devido à sua simplicidade e eficiência.

### Características principais

- Baseado em um subconjunto da linguagem JavaScript
- Utiliza convenções familiares a programadores de diversas linguagens
- Estrutura de dados universal, suportada por praticamente todas as linguagens de programação modernas

## 2. Estrutura Detalhada do JSON

JSON é construído sobre duas estruturas fundamentais:

### 2.1 Objetos

Um objeto é um conjunto não ordenado de pares nome/valor. Um objeto começa com `{` (chave de abertura) e termina com `}` (chave de fechamento). Cada nome é seguido por `:` (dois pontos) e os pares nome/valor são separados por `,` (vírgula).

Exemplo detalhado de um objeto JSON:

```json
{
  "nome": "Ana Silva",
  "idade": 28,
  "casado": false,
  "profissao": "Engenheira de Software",
  "hobbies": ["leitura", "natação", "fotografia"],
  "endereco": {
    "rua": "Avenida Principal",
    "numero": 123,
    "cidade": "São Paulo",
    "cep": "01234-567"
  },
  "telefones": [
    {
      "tipo": "casa",
      "numero": "11 2345-6789"
    },
    {
      "tipo": "celular",
      "numero": "11 98765-4321"
    }
  ]
}
```

### 2.2 Arrays

Um array é uma coleção ordenada de valores. Um array começa com `[` (colchete de abertura) e termina com `]` (colchete de fechamento). Os valores são separados por `,` (vírgula).

Exemplo detalhado de um array JSON:

```json
[
  {
    "id": 1,
    "produto": "Notebook",
    "preco": 2500.00,
    "emEstoque": true
  },
  {
    "id": 2,
    "produto": "Smartphone",
    "preco": 1500.00,
    "emEstoque": false
  },
  {
    "id": 3,
    "produto": "Tablet",
    "preco": 800.00,
    "emEstoque": true
  }
]
```

## 3. Tipos de Dados em JSON

JSON suporta os seguintes tipos de dados:

1. **String**: Sequência de zero ou mais caracteres Unicode, envolta em aspas duplas.
   Exemplo: `"Olá, mundo!"`

2. **Número**: Inteiro ou número de ponto flutuante.
   Exemplos: `42`, `-273.15`, `1.2e-10`

3. **Booleano**: Verdadeiro ou falso.
   Exemplos: `true`, `false`

4. **Array**: Coleção ordenada de valores, que podem ser de qualquer tipo.
   Exemplo: `[1, "dois", true, null]`

5. **Objeto**: Coleção não ordenada de pares nome/valor.
   Exemplo: `{"chave": "valor"}`

6. **null**: Representa um valor nulo.
   Exemplo: `null`

Exemplo combinando vários tipos:

```json
{
  "nome": "Loja Tech",
  "fundadaEm": 2010,
  "ativa": true,
  "categorias": ["Eletrônicos", "Informática", "Acessórios"],
  "localizacao": {
    "latitude": -23.550520,
    "longitude": -46.633309
  },
  "gerenteAtual": null
}
```

## 4. Convertendo entre JSON e Objetos JavaScript

JavaScript fornece métodos nativos para converter entre strings JSON e objetos JavaScript:

### 4.1 JSON.parse()

Converte uma string JSON em um objeto JavaScript.

Exemplo detalhado:

```javascript
const jsonString = `{
  "nome": "Carlos",
  "idade": 35,
  "hobbies": ["guitar", "codificação", "ciclismo"],
  "endereco": {
    "cidade": "Rio de Janeiro",
    "bairro": "Copacabana"
  }
}`;

try {
  const objeto = JSON.parse(jsonString);
  console.log(objeto.nome); // Saída: Carlos
  console.log(objeto.hobbies[1]); // Saída: codificação
  console.log(objeto.endereco.cidade); // Saída: Rio de Janeiro
} catch (erro) {
  console.error("Erro ao analisar JSON:", erro);
}
```

### 4.2 JSON.stringify()

Converte um objeto JavaScript em uma string JSON.

Exemplo detalhado:

```javascript
const objeto = {
  nome: "Ana",
  idade: 28,
  skills: ["JavaScript", "Python", "React"],
  experiencia: {
    anos: 5,
    empresas: ["TechCorp", "InnovaSoft"]
  },
  disponivel: true
};

const jsonString = JSON.stringify(objeto, null, 2);
console.log(jsonString);
```

Saída:
```json
{
  "nome": "Ana",
  "idade": 28,
  "skills": [
    "JavaScript",
    "Python",
    "React"
  ],
  "experiencia": {
    "anos": 5,
    "empresas": [
      "TechCorp",
      "InnovaSoft"
    ]
  },
  "disponivel": true
}
```

O segundo e terceiro argumentos de `JSON.stringify()` são opcionais:

- O segundo argumento (`null` neste caso) pode ser uma função ou um array para transformar o resultado.
- O terceiro argumento (`2` neste caso) especifica o número de espaços para indentação, melhorando a legibilidade.

## 5. Trabalhando com JSON em Aplicações Práticas

### 5.1 Armazenando e Recuperando Dados no LocalStorage

```javascript
// Salvando dados complexos
const configuracaoUsuario = {
  nome: "Alice",
  tema: "escuro",
  notificacoes: {
    email: true,
    push: false
  },
  ultimoAcesso: new Date().toISOString()
};

localStorage.setItem('userConfig', JSON.stringify(configuracaoUsuario));

// Recuperando e usando dados
const configSalva = JSON.parse(localStorage.getItem('userConfig'));
if (configSalva) {
  console.log(`Bem-vindo de volta, ${configSalva.nome}!`);
  console.log(`Seu tema atual é: ${configSalva.tema}`);
  console.log(`Último acesso: ${new Date(configSalva.ultimoAcesso).toLocaleString()}`);
}
```

### 5.2 Fazendo uma Requisição a uma API e Processando Dados JSON

```javascript
function buscarDadosUsuario(userId) {
  fetch(`https://api.exemplo.com/usuarios/${userId}`)
    .then(response => {
      if (!response.ok) {
        throw new Error('Falha na requisição');
      }
      return response.json();
    })
    .then(dados => {
      console.log("Dados do usuário:", dados);
      exibirPerfilUsuario(dados);
    })
    .catch(erro => console.error('Erro:', erro));
}

function exibirPerfilUsuario(usuario) {
  const perfilHTML = `
    <h2>${usuario.nome}</h2>
    <p>Email: ${usuario.email}</p>
    <p>Cidade: ${usuario.endereco.cidade}</p>
    <h3>Posts Recentes:</h3>
    <ul>
      ${usuario.posts.map(post => `<li>${post.titulo}</li>`).join('')}
    </ul>
  `;
  document.getElementById('perfil').innerHTML = perfilHTML;
}

buscarDadosUsuario(123);
```

## 6. Limitações e Boas Práticas

### Limitações:

1. JSON não suporta comentários.
2. Todas as chaves devem ser strings e usar aspas duplas.
3. Não suporta diretamente tipos como `Date`, `undefined`, ou `Function`.
4. Não tem suporte nativo para referências circulares.

### Boas Práticas:

1. Valide sempre o JSON antes de usar `JSON.parse()`.
2. Use try-catch ao analisar JSON para lidar com possíveis erros.
3. Evite armazenar dados sensíveis em JSON sem criptografia.
4. Para datas, use strings ISO 8601 (ex: "2023-04-01T12:00:00Z") e converta-as no lado do cliente.
5. Ao trabalhar com APIs, verifique a documentação para entender a estrutura JSON esperada.

## 7. Manipulação Avançada de JSON

### 7.1 Transformando Dados com JSON.stringify()

```javascript
const dados = {
  id: 1,
  nome: "Produto Especial",
  preco: 99.99,
  emEstoque: true,
  categoria: null,
  detalhes: {
    peso: "500g",
    dimensoes: "10x20x5cm"
  }
};

const jsonPersonalizado = JSON.stringify(dados, (chave, valor) => {
  if (typeof valor === 'number') {
    return valor.toFixed(2);
  }
  if (valor === null) {
    return undefined; // Remove propriedades null
  }
  return valor;
}, 2);

console.log(jsonPersonalizado);
```

### 7.2 Parsing Condicional com JSON.parse()

```javascript
const jsonComDatas = `{
  "nome": "Evento Importante",
  "dataInicio": "2023-12-01T09:00:00Z",
  "dataFim": "2023-12-03T18:00:00Z"
}`;

const evento = JSON.parse(jsonComDatas, (chave, valor) => {
  if (typeof valor === 'string' && /^\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}Z$/.test(valor)) {
    return new Date(valor);
  }
  return valor;
});

console.log(evento.dataInicio.toLocaleString()); // Exibe a data formatada
```

## Exercício Prático Avançado

Crie um sistema de gerenciamento de biblioteca que utilize JSON para armazenar e manipular dados:

1. Crie uma estrutura JSON para representar livros, incluindo título, autor, ISBN, ano de publicação, gêneros (array) e status de empréstimo.
2. Implemente funções para adicionar novos livros, atualizar informações de livros existentes, e marcar livros como emprestados ou devolvidos.
3. Crie uma função de busca que permita encontrar livros por título, autor ou ISBN.
4. Implemente uma funcionalidade de exportação que converta toda a biblioteca para uma string JSON formatada.
5. Adicione uma funcionalidade de importação que possa ler uma string JSON e adicionar os livros à biblioteca existente.
6. Use `localStorage` para persistir os dados da biblioteca entre sessões.

Exemplo de solução parcial:

```javascript
let biblioteca = [];

function adicionarLivro(titulo, autor, isbn, anoPublicacao, generos) {
  const livro = {
    id: Date.now(), // Usando timestamp como ID único
    titulo,
    autor,
    isbn,
    anoPublicacao,
    generos,
    emprestado: false
  };
  biblioteca.push(livro);
  salvarBiblioteca();
}

function atualizarLivro(id, atualizacoes) {
  const index = biblioteca.findIndex(livro => livro.id === id);
  if (index !== -1) {
    biblioteca[index] = { ...biblioteca[index], ...atualizacoes };
    salvarBiblioteca();
  }
}

function marcarComoEmprestado(id, status) {
  const livro = biblioteca.find(livro => livro.id === id);
  if (livro) {
    livro.emprestado = status;
    salvarBiblioteca();
  }
}

function buscarLivros(termo) {
  return biblioteca.filter(livro =>
    livro.titulo.toLowerCase().includes(termo.toLowerCase()) ||
    livro.autor.toLowerCase().includes(termo.toLowerCase()) ||
    livro.isbn.includes(termo)
  );
}

function exportarBiblioteca() {
  return JSON.stringify(biblioteca, null, 2);
}

function importarBiblioteca(jsonString) {
  try {
    const livrosImportados = JSON.parse(jsonString);
    biblioteca = [...biblioteca, ...livrosImportados];
    salvarBiblioteca();
  } catch (erro) {
    console.error("Erro ao importar biblioteca:", erro);
  }
}

function salvarBiblioteca() {
  localStorage.setItem('biblioteca', JSON.stringify(biblioteca));
}

function carregarBiblioteca() {
  const bibliotecaSalva = localStorage.getItem('biblioteca');
  if (bibliotecaSalva) {
    biblioteca = JSON.parse(bibliotecaSalva);
  }
}

// Inicialização
carregarBiblioteca();

// Exemplo de uso
adicionarLivro("O Senhor dos Anéis", "J.R.R. Tolkien", "9788533613379", 1954, ["Fantasia", "Aventura"]);
console.log(buscarLivros("Tolkien"));
console.log(exportarBiblioteca());
```

Este exercício abrange vários aspectos do trabalho com JSON, incluindo criação, manipulação, busca, persistência e importação/exportação de dados estruturados.

## Recursos Adicionais

- [JSON.org (em português)](https://www.json.org/json-pt.html)