# Cheat Sheet — HTML, CSS e JavaScript

**Mateus Vaz Dos Santos**

----------

Esse documento é um guia de referência que fiz pra consultar quando eu tiver dúvidas básicas. Nada muito complicado, só os conceitos que mais uso no dia a dia.

----------

## HTML

### Estrutura básica

Todo arquivo HTML tem que começa assim, para o navegador poder interpretar a página.

```html
<!DOCTYPE html>
<html lang="pt-BR">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Minha Página</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <!-- conteúdo aqui -->
    <script src="script.js"></script>
  </body>
</html>

```

### Tags mais usadas

```html
<!-- títulos: só um h1 por página -->
<h1>Título</h1>
<h2>Subtítulo</h2>

<!-- parágrafo e contêiner genérico -->
<p>Um texto qualquer.</p>
<div class="card"><p>Conteúdo</p></div>

<!-- link e imagem -->
<a href="https://google.com" target="_blank">Google</a>
<img src="foto.jpg" alt="Descrição da imagem" />

<!-- listas -->
<ul><li>Item sem ordem</li></ul>
<ol><li>Item numerado</li></ol>

<!-- formulário básico -->
<form action="/enviar" method="POST">
  <input type="text" name="nome" placeholder="Seu nome" required />
  <input type="email" name="email" required />
  <button type="submit">Enviar</button>
</form>

<!-- tags semânticas -->
<header>cabeçalho</header>
<nav>menu</nav>
<main>conteúdo principal</main>
<footer>rodapé</footer>

```

### Boas práticas em HTML

-   Sempre usar `alt` nas imagens
-   Colocar `<script>` no fim do `<body>`
-   Não pular níveis de cabeçalho (h1 → h2 → h3)
-   Preferir tags semânticas em vez de só `<div>`

----------

## CSS

### Seletores

```css
/* por tag */
p { color: blue; }

/* por classe — mais usado */
.card { background: white; }

/* por id — evitar usar muito */
#header { height: 60px; }

/* descendente */
.menu a { text-decoration: none; }

/* pseudo-classe */
a:hover { color: red; }
input:focus { border-color: blue; }

/* primeiro e último filho */
li:first-child { font-weight: bold; }
li:last-child { margin-bottom: 0; }

```

### Propriedades essenciais

**Texto e fonte**

```css
p {
  color: #333;               /* cor do texto */
  font-size: 16px;           /* tamanho */
  font-weight: bold;         /* negrito */
  font-family: sans-serif;   /* fonte */
  line-height: 1.6;          /* espaço entre linhas */
  text-align: center;        /* alinhamento */
  text-decoration: none;     /* remove sublinhado de links */
}

```

**Box model — margem, padding e borda**

```css
/* margin = espaço fora do elemento */
/* padding = espaço dentro do elemento */
.caixa {
  margin: 16px;              /* todos os lados */
  margin: 10px 20px;         /* cima/baixo  esquerda/direita */
  padding: 12px 24px;
  border: 1px solid #ccc;
  border-radius: 8px;        /* bordas arredondadas */
  width: 300px;
  height: 200px;

  /* box-sizing: border-box faz o padding não aumentar o tamanho */
  box-sizing: border-box;
}

```

**Display e posicionamento**

```css
.elemento {
  display: block;        /* ocupa linha inteira */
  display: inline;       /* fica na mesma linha */
  display: inline-block; /* mistura dos dois */
  display: none;         /* some da tela */
}

.relativo {
  position: relative;
}

.absoluto {
  position: absolute;   /* relativo ao pai com position */
  top: 10px;
  right: 10px;
}

.fixo {
  position: fixed;      /* fica na tela mesmo ao rolar */
  bottom: 0;
  left: 0;
}

```

**Flexbox** — pra alinhar elementos em linha ou coluna

```css
.container {
  display: flex;
  flex-direction: row;        /* row (padrão) ou column */
  justify-content: center;    /* alinha no eixo principal */
  align-items: center;        /* alinha no eixo cruzado */
  gap: 16px;                  /* espaço entre os filhos */
  flex-wrap: wrap;            /* permite quebrar linha */
}

/* item individual */
.item {
  flex: 1;                    /* ocupa espaço proporcional */
}

```

**Grid** — pra layouts mais complexos em 2 dimensões

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 colunas iguais */
  grid-template-rows: auto;
  gap: 20px;
}

/* item que ocupa 2 colunas */
.destaque {
  grid-column: span 2;
}

```

**Responsividade com media queries**

```css
/* aplica só em telas menores que 768px */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }

  h1 {
    font-size: 24px;
  }
}

```

**Variáveis CSS** — facilita muito manter consistência

```css
:root {
  --cor-primaria: #3b82f6;
  --cor-texto: #111827;
  --espacamento: 16px;
}

button {
  background-color: var(--cor-primaria);
  padding: var(--espacamento);
}

```

### Boas práticas em CSS

-   Usar `box-sizing: border-box` no início
-   Evitar usar `!important` 
-   Preferir classes em vez de ids pra estilização
-   Usar variáveis CSS pra cores e tamanhos repetidos
-   Mobile first: escrever o CSS base pro mobile e usar `min-width` nas media queries

----------

## JavaScript

### Variáveis

```js
// const = não pode reatribuir (preferir sempre)
const nome = "Mateus";

// let = pode mudar o valor
let contador = 0;
contador = contador + 1;

// var = evitar, tem escopo estranho
// var idade = 20;

```

### Tipos básicos

```js
const texto = "olá";            // string
const numero = 42;              // number
const decimal = 3.14;           // também number
const verdadeiro = true;        // boolean
const nada = null;              // null (vazio de propósito)
let indefinido;                 // undefined (não foi definido)

// array
const frutas = ["maçã", "banana", "uva"];

// objeto
const usuario = {
  nome: "Mateus",
  idade: 20,
  ativo: true
};

console.log(usuario.nome); // "Mateus"
console.log(frutas[0]);    // "maçã"

```

### Funções

```js
// função tradicional
function somar(a, b) {
  return a + b;
}

// arrow function — mais curta, muito usada hoje
const multiplicar = (a, b) => a * b;

// função com valor padrão
const saudar = (nome = "visitante") => {
  return `Olá, ${nome}!`;
};

console.log(somar(3, 4));       // 7
console.log(saudar());          // "Olá, visitante!"
console.log(saudar("Mateus"));  // "Olá, Mateus!"

```

### Condicionais e loops

```js
// if/else
const hora = 14;

if (hora < 12) {
  console.log("Bom dia!");
} else if (hora < 18) {
  console.log("Boa tarde!");
} else {
  console.log("Boa noite!");
}

// operador ternário — bom pra casos simples
const msg = hora < 18 ? "Ainda é dia" : "Já é noite";

// loop com for
for (let i = 0; i < 5; i++) {
  console.log(i);
}

// loop em array
const nomes = ["Ana", "Carlos", "Julia"];
nomes.forEach(nome => console.log(nome));

// map — cria novo array transformado
const maiusculos = nomes.map(nome => nome.toUpperCase());

// filter — filtra itens
const numeros = [1, 2, 3, 4, 5, 6];
const pares = numeros.filter(n => n % 2 === 0); // [2, 4, 6]

```

### Manipulação do DOM

```js
// selecionar elementos
const titulo = document.querySelector("h1");
const botoes = document.querySelectorAll(".btn");
const formulario = document.getElementById("form-contato");

// alterar conteúdo e estilo
titulo.textContent = "Novo título";
titulo.style.color = "blue";

// adicionar/remover classes
titulo.classList.add("destaque");
titulo.classList.remove("oculto");
titulo.classList.toggle("ativo"); // alterna

// criar e adicionar elemento novo
const paragrafo = document.createElement("p");
paragrafo.textContent = "Parágrafo criado pelo JS";
document.body.appendChild(paragrafo);

```

### Eventos

```js
const botao = document.querySelector("#meu-botao");

// click
botao.addEventListener("click", function () {
  alert("Botão clicado!");
});

// input em tempo real
const campo = document.querySelector("#campo-nome");
campo.addEventListener("input", (e) => {
  console.log("Digitando:", e.target.value);
});

// submit de formulário
const form = document.querySelector("form");
form.addEventListener("submit", (e) => {
  e.preventDefault(); // impede recarregar a página
  const dados = new FormData(form);
  console.log(dados.get("nome"));
});

```

### Fetch API — requisições assíncronas

```js
// buscar dados de uma API
async function buscarUsuario(id) {
  try {
    const resposta = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`);
    const dados = await resposta.json();
    console.log(dados.name);
  } catch (erro) {
    console.error("Deu erro:", erro);
  }
}

buscarUsuario(1);

```

### Exemplo prático — contador simples

```html
<button id="menos">-</button>
<span id="valor">0</span>
<button id="mais">+</button>

```

```js
let count = 0;
const display = document.getElementById("valor");

document.getElementById("mais").addEventListener("click", () => {
  count++;
  display.textContent = count;
});

document.getElementById("menos").addEventListener("click", () => {
  count--;
  display.textContent = count;
});

```

### Boas práticas em JavaScript

-   Usar `const` por padrão, `let` só quando precisar reatribuir
-   Sempre tratar erros em chamadas assíncronas com `try/catch`
-   Evitar manipular o DOM dentro de loops (lento demais)
-   Usar `===` em vez de `==` pra comparação (mais seguro)
-   Comentar o "porquê" do código, não o "o quê"

----------

### PWA (Progressive Web App)

É um site que pode se comportar como um aplicativo nativo. 

**O que precisa pra ser PWA:**

-   HTTPS
-   Um arquivo `manifest.json`
-   Um Service Worker

```json
// manifest.json — configurações do "app"
{
  "name": "Meu App",
  "short_name": "App",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#3b82f6",
  "icons": [
    { "src": "icon-192.png", "sizes": "192x192", "type": "image/png" },
    { "src": "icon-512.png", "sizes": "512x512", "type": "image/png" }
  ]
}

```

```js
// registrar o service worker no main JS
if ("serviceWorker" in navigator) {
  navigator.serviceWorker.register("/sw.js");
}

```

### Cache e Armazenamento no Navegador

**localStorage** — salva dados sem prazo de validade

```js
// salvar
localStorage.setItem("tema", "escuro");

// ler
const tema = localStorage.getItem("tema");

// remover
localStorage.removeItem("tema");

```

**sessionStorage** — igual ao localStorage, mas some quando fecha o aba

```js
sessionStorage.setItem("passo-atual", "2");

```

**IndexedDB** — banco de dados no navegador, pra grandes volumes de dados estruturados. Mais complexo, mas muito poderoso. Geralmente usado com bibliotecas como o `idb`.

**Cache API** — usada nos Service Workers pra guardar arquivos e respostas HTTP (deixa o site funcionar offline)

```js
// dentro do service worker
self.addEventListener("install", (e) => {
  e.waitUntil(
    caches.open("v1").then((cache) => {
      return cache.addAll(["/", "/style.css", "/script.js"]);
    })
  );
});

```

### Internet (resumo)

-   **HTTP/HTTPS** — protocolo de comunicação entre cliente e servidor. HTTPS é criptografado (mais seguro)
-   **Cliente/Servidor** — o navegador (cliente) faz requisições, o servidor responde com HTML, JSON, etc.
-   **Status HTTP mais comuns:**
    -   `200` — OK, deu certo
    -   `301` — redirecionamento permanente
    -   `404` — não encontrado
    -   `500` — erro no servidor

### Git — comandos básicos que uso sempre

```bash
git init                      # iniciar repositório
git add .                     # adicionar tudo
git commit -m "mensagem"      # salvar ponto
git push origin main          # enviar pro GitHub
git pull                      # baixar atualizações
git status                    # ver o que mudou
git log --oneline             # ver histórico resumido


### Performance — dicas 

-   Compactar imagens antes de subir (usar WebP quando possível)
-   Minificar CSS e JS em produção
-   Usar `loading="lazy"` em imagens fora da tela
-   Carregar fontes com `font-display: swap`
-   Evitar JavaScript que bloqueia o carregamento da página

----------
