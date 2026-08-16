# 🐍 Lógica de Programação com Python — Guia Interativo

Um guia gamificado, em português, para aprender os fundamentos da **lógica de programação com Python** — com teoria direto ao ponto, exercícios interativos e provas gamificadas. Tudo em um único arquivo HTML, sem dependências de build.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML](https://img.shields.io/badge/HTML-single--file-orange.svg)
![No build step](https://img.shields.io/badge/build-none%20needed-brightgreen.svg)

## 📖 Sobre o projeto

Este projeto é um curso interativo de **lógica de programação** voltado a quem está começando em Python. Em vez de apenas ler teoria, quem estuda:

- aprende cada conceito com explicações curtas e exemplos de código reais;
- pratica na hora com exercícios interativos (organizar passos, completar código, prever a saída, encontrar erros, montar programas inteiros linha por linha, acertar a indentação);
- é testado com provas rápidas por módulo e uma **prova final gamificada**, com vidas, cronômetro e pontuação;
- acompanha o próprio progresso por um sistema de XP, níveis e uma **dificuldade que sobe sozinha** conforme o XP aumenta.

Tudo isso roda inteiramente no navegador — não há backend, servidor ou instalação de pacotes.

## ✨ Funcionalidades

- **8 módulos progressivos**, cada um com teoria, um exercício prático e uma prova rápida.
- **Sorteio + geração procedural de perguntas**: cada módulo tem um *banco* de exercícios e perguntas maior do que o exibido por vez. A cada visita (ou a pedido, com o botão 🔄), o app sorteia um exercício e algumas perguntas desse banco — e boa parte delas é **gerada na hora**, com números, nomes e alternativas diferentes a cada sorteio, para evitar que dê para simplesmente decorar a resposta.
- **6 tipos de exercício interativo**: ordenar passos de um algoritmo, completar código (banco de palavras), prever a saída de um trecho, encontrar o erro de sintaxe, **montar um programa inteiro linha por linha** e **acertar a indentação** de um bloco de código.
- **Dificuldade progressiva em 4 níveis** (Fácil → Médio → Difícil → Mestre), que sobe sozinha conforme o XP aumenta — ver seção dedicada abaixo.
- **Prova final gamificada**: perguntas sorteadas de um banco combinado com mais de 40 itens (fixos + gerados), 3 vidas, 30 segundos por pergunta e badges de Bronze 🥉 a Platina 🏆. A quantidade de perguntas também cresce com a dificuldade (8 a 15). No nível Mestre, a prova pode sortear os mesmos desafios de **montar código** e **indentação** dos módulos — não é só múltipla escolha.
- **Sistema de XP e níveis**, com progresso visual no cabeçalho.
- **Progresso salvo automaticamente**, com opção de zerar tudo a qualquer momento.
- **Tema claro ou retrô** (verde e preto, estilo terminal Unix, com fontes `VT323` e `Share Tech Mono`), alternável a qualquer momento e salvo entre sessões.
- **Realce de sintaxe Python** feito à mão (sem bibliotecas externas de highlighting), adaptado à paleta do tema ativo.
- **Design responsivo**, com um tema visual inspirado em editores de código e um cabeçalho que se reorganiza em telas pequenas para nunca sobrepor botões.
- Respeita `prefers-reduced-motion` e tem estados de foco visíveis para navegação por teclado.

## 📈 Dificuldade progressiva

A dificuldade sobe sozinha conforme o XP aumenta — não precisa configurar nada:

| XP | Dificuldade | Perguntas por prova rápida | Perguntas na prova final |
|---|---|---|---|
| 0–199 | 🟢 Fácil | 3 | 8 |
| 200–499 | 🟡 Médio | 4 | 10 |
| 500–799 | 🔴 Difícil | 5 | 12 |
| 800+ | 🟣 Mestre | 6 | 15 |

O nível de dificuldade atual aparece no cabeçalho, na página de cada módulo e na introdução da prova final. Ao subir de dificuldade, um aviso rápido aparece na tela.

Isso afeta três eixos ao mesmo tempo:

1. **Mais itens ficam disponíveis nos bancos**: perguntas e exercícios mais avançados (marcados com `difficulty: 'medio'`, `'dificil'` ou `'mestre'` no código) só entram no sorteio a partir do nível correspondente — o banco de cada módulo cresce conforme você avança.
2. **As próprias perguntas geradas ficam mais complexas**: cada função geradora recebe o nível atual e ajusta o que produz — números maiores, mais alternativas, expressões compostas (como `(a + b) % c` em vez de só `a % b`), condições combinadas com `and`/`or`, laços com passo (`range` com terceiro argumento), funções aninhadas, e por aí vai. No nível Mestre, essas mesmas geradoras usam a versão mais difícil já existente (a do nível Difícil) — a novidade do Mestre está no próximo ponto.
3. **Desafios exclusivos do nível Mestre**: cada um dos 8 módulos ganha um exercício de **montar código linha por linha**, incluindo a **indentação** correta — o tipo de desafio mais avançado do guia, descrito na próxima seção.

## 🧗 Desafios do nível Mestre: montar código e indentação

A partir de 800 XP, cada módulo passa a sortear, entre seus exercícios possíveis, um desafio maior e mais realista — programas de verdade, com 4 a 9 linhas, combinando conceitos de várias partes do guia. Existem dois formatos:

- **Montar código (`codebuild`)**: as linhas do programa aparecem embaralhadas como blocos clicáveis; você clica nelas para montar o programa. Em boa parte dos módulos, também é preciso escolher o nível de indentação (0, 1, 2 ou 3 — cada nível equivale a 4 espaços) de cada linha depois de posicioná-la, usando os botões numerados. Uma pré-visualização do código, já formatado e com destaque de sintaxe, é atualizada em tempo real.
- **Indentação (`indent`)**: uma variação mais focada — as linhas já vêm na ordem certa, e o desafio é só acertar o nível de indentação de cada uma (útil para praticar blocos aninhados sem se preocupar com a ordem lógica ao mesmo tempo).

A checagem da ordem é feita por **dependência real entre as linhas**, não por posição fixa: cada linha do exercício sabe de quais outras ela genuinamente precisa (guardado em `dependsOn`, um array de índices). Por exemplo, no desafio do Módulo 2, `nome = input(...)`, `idade = int(input(...))` e `altura = float(input(...))` não dependem uma da outra — qualquer ordem entre as três é aceita, e só o `print()` final precisa vir depois de todas. Já em desafios como o do Módulo 1 (`if/elif/else`) ou o do Módulo 8 (definição de função), a ordem é realmente única, porque é assim que a sintaxe do Python exige. Isso evita marcar como errada uma solução que é perfeitamente válida em Python só porque a ordem ficou diferente da "original".

Ambos os formatos verificam a resposta como um todo (ordem válida e, quando aplicável, indentação certa em todas as linhas) e destacam, linha a linha, onde o código ainda está errado.

**Esses desafios também aparecem na Prova Final.** No nível Mestre, o banco da prova (`EXAM_POOL`) inclui, além das perguntas de múltipla escolha, alguns desafios de montar código e de indentação exclusivos da prova — mais complexos que os dos módulos, combinando conceitos de partes diferentes do guia (como uma função que verifica se um número é primo, com laço e condicional aninhados dentro dela, ou um programa que soma apenas números pares de uma lista). Dentro da prova, o cronômetro e as vidas continuam valendo do mesmo jeito: acertar a ordem/indentação soma +15 XP, errar custa uma vida.

## 🎨 Tema claro ou retrô

Um botão no cabeçalho (🖥️ / ☀️) alterna entre dois temas, salvos automaticamente entre sessões:

- **Claro** (padrão): visual de "console de aprendizado", com painéis estilo terminal e paleta inspirada nas cores do Python (azul e dourado).
- **Retrô** (verde e preto): tema escuro inspirado em terminais Unix antigos, com texto em tons de verde fosforescente sobre fundo quase preto, títulos na fonte `VT323` (efeito CRT pixelado) e o restante da interface em `Share Tech Mono`. O destaque de sintaxe dos blocos de código também muda para uma paleta monocromática em tons de verde nesse modo.

Como quase toda a interface é construída sobre variáveis CSS (`--ink`, `--paper`, `--console` etc.), a troca de tema é só uma substituição de valores — nenhum componente precisa de regras duplicadas.

## 🎲 Como funciona o sorteio procedural

Cada módulo define dois bancos no código-fonte:

- `exercisePool` — uma lista de exercícios práticos possíveis para aquele módulo.
- `quizPool` — uma lista maior de perguntas possíveis para a prova rápida daquele módulo.

Cada item de um banco pode ser:

1. **Um objeto estático** (pergunta/exercício fixo, escrito à mão), ou
2. **Uma função geradora**, que quando chamada devolve uma versão **nova** da pergunta — sorteando números (ex.: valores de `a` e `b` em `a // b`), nomes, listas ou índices, recalculando a resposta certa a partir desses valores e embaralhando a posição das alternativas.

Quando o exercício envolve texto (como as variáveis do Módulo 2), o valor sorteado respeita o **contexto da variável**: uma variável chamada `cidade` só recebe nomes de cidades de verdade, uma `nome` só recebe nomes de pessoas, e assim por diante — nunca uma palavra solta e sem relação, mesmo que ela seja tecnicamente uma string válida.

Ao abrir um módulo, o app sorteia 1 exercício do `exercisePool` e algumas perguntas do `quizPool` (a quantidade depende da dificuldade atual — ver seção acima), chamando as geradoras encontradas nesse sorteio. Os botões **🔄 outro** (no exercício) e **🔄 Novas perguntas** (na prova rápida) repetem esse sorteio a qualquer momento, para praticar com números diferentes. A Prova Final segue a mesma lógica, sorteando perguntas de um banco combinado (`EXAM_POOL`) com mais de 40 itens fixos e gerados.

As funções geradoras têm testes automatizados que rodam cada uma milhares de vezes, em cada um dos 4 níveis de dificuldade, validando que a resposta correta e as alternativas erradas nunca colidem e que a estrutura de cada exercício está sempre correta — mesmo com valores aleatórios diferentes a cada execução.

## 🧠 Módulos incluídos

| # | Módulo | Exemplos de exercício no banco | Desafio Mestre |
|---|--------|-----------|-----------|
| 01 | O que é Lógica de Programação? | Ordenar os passos de até 5 algoritmos diferentes (sorteado) | Montar um classificador de números (if/elif/else) |
| 02 | Variáveis e Tipos de Dados | Completar código com variáveis e tipos sorteados | Montar um programa de cadastro (leituras independentes) |
| 03 | Entrada e Saída de Dados | Prever a saída de f-strings com nomes/idades sorteados | Montar um programa de verificação de idade para votar |
| 04 | Operadores | Prever o resultado de contas com números sorteados | Montar um verificador de divisibilidade |
| 05 | Estruturas Condicionais | Encontrar o erro de sintaxe (entre vários cenários possíveis) | Acertar a indentação de uma cadeia if/elif/elif/else |
| 06 | Estruturas de Repetição | Completar um range() com limites sorteados | Montar uma soma de números pares (laço aninhado) |
| 07 | Listas | Prever a saída de índices sorteados em listas variadas | Montar um filtro de números pares em uma lista |
| 08 | Funções | Completar funções que retornam True/False | Montar uma função com três ramos e usá-la |

## 🚀 Como usar

Não é preciso instalar nada.

1. Baixe (ou clone) este repositório.
2. Abra o arquivo `logica-python.html` diretamente no navegador — dando duplo clique nele já funciona.

Se preferir servir localmente (opcional, útil para evitar restrições de alguns navegadores com arquivos locais):

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Depois acesse `http://localhost:8000/logica-python.html`.

## 🗂️ Estrutura do projeto

```
.
├── logica-python.html   # Aplicativo completo (HTML + CSS + JS em um único arquivo)
├── README.md
└── LICENSE
```

O arquivo é organizado internamente em três partes, todas no mesmo `.html`:

- `<style>` — tokens de design (cores, tipografia, espaçamento) e todos os componentes visuais, incluindo as variáveis do tema retrô.
- Dados (`MODULES`, `EXAM_POOL`) e as funções geradoras — todo o conteúdo do curso.
- Lógica da aplicação — estado, dificuldade, renderização, exercícios, prova final, tema e persistência.

## 🧩 Adicionando ou editando conteúdo

Todo o conteúdo do curso vive nos arrays `MODULES` e `EXAM_POOL`, dentro da tag `<script>`. Cada módulo tem um `exercisePool` e um `quizPool` — arrays onde cada item é um objeto estático **ou** o nome de uma função geradora (`function genAlgumaCoisa(tier){ ... return {...}; }`). Para adicionar conteúdo novo:

- **Item fixo**: adicione um objeto no mesmo formato dos existentes (`{ q, options, correct, explanation }` para perguntas, ou `{ type, instructions, ... }` para exercícios). Marque `difficulty: 'medio' | 'dificil' | 'mestre'` se quiser que o item só apareça a partir de um certo nível — sem esse campo, o item fica sempre disponível.
- **Item procedural**: escreva uma função que recebe o nível atual (`tier`) como argumento, sorteie valores de acordo com ele, calcule a resposta certa a partir deles e devolva o objeto no mesmo formato — depois adicione o **nome da função** (sem chamá-la) na lista do pool.
- **Exercício de montar código** (`type: 'codebuild'`) ou **de indentação** (`type: 'indent'`): cada linha é um objeto `{ text, indent, dependsOn }`, em que `dependsOn` lista os índices das linhas que precisam vir antes dela. Linhas sem dependência entre si podem ser resolvidas em qualquer ordem — só declare `dependsOn` de acordo com o que o código realmente exige.

A interface se adapta automaticamente a qualquer tamanho de pool, sem precisar mexer no código de renderização.

## 💾 Progresso e armazenamento

O progresso (XP, módulos concluídos, melhor pontuação na prova, tema escolhido) é salvo automaticamente através de um pequeno adaptador de armazenamento (`AppStorage`), definido no início do bloco de script, que escolhe o backend disponível:

1. **`window.storage`** — a API nativa de artefatos do Claude.ai (assíncrona, por usuário), usada automaticamente quando o app roda dentro do Claude.ai.
2. **`localStorage`** — usado como *fallback* automático sempre que `window.storage` não existir, o que é o caso ao publicar o arquivo no GitHub Pages, abrir localmente ou hospedar em qualquer servidor próprio. Os dados ficam salvos no `localStorage` do navegador, sob chaves como `logica_python__progresso` e `logica_python__tema`, e persistem entre sessões normalmente.

Não é preciso nenhuma configuração: o app detecta o ambiente sozinho, na inicialização, e informa o backend escolhido no console do navegador (`console.info`). Se nenhum dos dois estiver disponível (por exemplo, em modo de navegação privada que bloqueia `localStorage`), o app continua funcionando normalmente — apenas sem salvar o progresso entre sessões.

## 🎨 Design

A identidade visual segue um conceito de "console de aprendizado": painéis com barra de título estilo terminal, tipografia `Space Grotesk` + `IBM Plex Sans` + `IBM Plex Mono` no tema claro (trocada por `VT323` + `Share Tech Mono` no tema retrô), e uma paleta inspirada nas cores do Python (azul e dourado) — ou em tons de verde fosforescente, no tema retrô. O cabeçalho usa CSS Grid com uma área reservada para os botões de ação, garantindo que nunca sobreponham a barra de XP mesmo em telas bem estreitas.

## 🛠️ Tecnologias

- HTML5, CSS3 (sem frameworks) e JavaScript puro (vanilla, sem frameworks ou bundlers).
- Nenhuma dependência externa além de fontes do Google Fonts (com fallback para fontes do sistema caso não carreguem).

## 🤝 Contribuindo

Sugestões, correções de conteúdo e novos módulos são bem-vindos. Abra uma *issue* ou envie um *pull request*.

## 📄 Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](./LICENSE) para mais detalhes.

## 👤 Autoria

Criado por **Bandeirinha**.
