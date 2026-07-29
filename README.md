# 🐍 Lógica de Programação com Python — Guia Interativo

Um guia gamificado, em português, para aprender os fundamentos da **lógica de programação com Python** — com teoria direto ao ponto, exercícios interativos e provas gamificadas. Tudo em um único arquivo HTML, sem dependências de build.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML](https://img.shields.io/badge/HTML-single--file-orange.svg)
![No build step](https://img.shields.io/badge/build-none%20needed-brightgreen.svg)

## 📖 Sobre o projeto

Este projeto é um curso interativo de **lógica de programação** voltado a quem está começando em Python. Em vez de apenas ler teoria, quem estuda:

- aprende cada conceito com explicações curtas e exemplos de código reais;
- pratica na hora com exercícios interativos (organizar passos, completar código, prever a saída, encontrar erros);
- é testado com provas rápidas por módulo e uma **prova final gamificada**, com vidas, cronômetro e pontuação;
- acompanha o próprio progresso por um sistema de XP, níveis e badges.

Tudo isso roda inteiramente no navegador — não há backend, servidor ou instalação de pacotes.

## ✨ Funcionalidades

- **8 módulos progressivos**, cada um com teoria, um exercício prático e uma prova rápida.
- **4 tipos de exercício interativo**: ordenar passos de um algoritmo, completar código (banco de palavras), prever a saída de um trecho e encontrar o erro de sintaxe.
- **Prova final gamificada**: 10 perguntas sorteadas de um banco maior, 3 vidas, 30 segundos por pergunta e badges de Bronze 🥉 a Platina 🏆.
- **Sistema de XP e níveis**, com progresso visual no cabeçalho.
- **Progresso salvo automaticamente**, com opção de zerar tudo a qualquer momento.
- **Realce de sintaxe Python** feito à mão (sem bibliotecas externas de highlighting).
- **Design responsivo**, com um tema visual inspirado em editores de código.
- Respeita `prefers-reduced-motion` e tem estados de foco visíveis para navegação por teclado.

## 🧠 Módulos incluídos

| # | Módulo | Exercício |
|---|--------|-----------|
| 01 | O que é Lógica de Programação? | Ordenar os passos de um algoritmo |
| 02 | Variáveis e Tipos de Dados | Completar código (tipos) |
| 03 | Entrada e Saída de Dados | Prever a saída (f-strings) |
| 04 | Operadores | Prever a saída (aritméticos) |
| 05 | Estruturas Condicionais | Encontrar o erro de sintaxe |
| 06 | Estruturas de Repetição | Completar código (range) |
| 07 | Listas | Prever a saída (índices) |
| 08 | Funções | Completar código (return) |

## 🚀 Como usar

Não é preciso instalar nada.

1. Baixe (ou clone) este repositório.
2. Abra o arquivo `index.html` diretamente no navegador — dando duplo clique nele já funciona.

Se preferir servir localmente (opcional, útil para evitar restrições de alguns navegadores com arquivos locais):

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Depois acesse `http://localhost:8000/index.html`.

## 🗂️ Estrutura do projeto

```
.
├── index.html   # Aplicativo completo (HTML + CSS + JS em um único arquivo)
├── README.md
└── LICENSE
```

O arquivo é organizado internamente em três partes, todas no mesmo `.html`:

- `<style>` — tokens de design (cores, tipografia, espaçamento) e todos os componentes visuais.
- Dados (`MODULES`, `EXAM_POOL`) — todo o conteúdo do curso, em objetos JavaScript simples.
- Lógica da aplicação — estado, renderização, exercícios, prova final e persistência.

## 🧩 Adicionando ou editando conteúdo

Todo o conteúdo do curso vive nos arrays `MODULES` e `EXAM_POOL`, dentro da tag `<script>`. Para adicionar um módulo novo, basta seguir a mesma estrutura de um módulo existente (`theory`, `exercise`, `quiz`) — a interface se adapta automaticamente, sem precisar mexer no código de renderização.

## 💾 Progresso e armazenamento

O progresso (XP, módulos concluídos, melhor pontuação na prova) é salvo automaticamente através de um pequeno adaptador de armazenamento (`AppStorage`), definido no início do bloco de script, que escolhe o backend disponível:

1. **`window.storage`** — a API nativa de artefatos do Claude.ai (assíncrona, por usuário), usada automaticamente quando o app roda dentro do Claude.ai.
2. **`localStorage`** — usado como *fallback* automático sempre que `window.storage` não existir, o que é o caso ao publicar o arquivo no GitHub Pages, abrir localmente ou hospedar em qualquer servidor próprio. Os dados ficam salvos no `localStorage` do navegador, sob a chave `logica_python__progresso`, e persistem entre sessões normalmente.

Não é preciso nenhuma configuração: o app detecta o ambiente sozinho, na inicialização, e informa o backend escolhido no console do navegador (`console.info`). Se nenhum dos dois estiver disponível (por exemplo, em modo de navegação privada que bloqueia `localStorage`), o app continua funcionando normalmente — apenas sem salvar o progresso entre sessões.

## 🎨 Design

A identidade visual segue um conceito de "console de aprendizado": painéis com barra de título estilo terminal, tipografia `Space Grotesk` + `IBM Plex Sans` + `IBM Plex Mono`, e uma paleta inspirada nas cores do Python (azul e dourado).

## 🛠️ Tecnologias

- HTML5, CSS3 (sem frameworks) e JavaScript puro (vanilla, sem frameworks ou bundlers).
- Nenhuma dependência externa além de fontes do Google Fonts (com fallback para fontes do sistema caso não carreguem).

## 🤝 Contribuindo

Sugestões, correções de conteúdo e novos módulos são bem-vindos. Abra uma *issue* ou envie um *pull request*.

## 📄 Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](./LICENSE) para mais detalhes.

## 👤 Autoria

Criado por **Bandeirinha**.
