# 📘 Documentação Frontend: Landing Page SEPE 2025

Esta documentação descreve a estrutura, o estilo e as funcionalidades da interface web desenvolvida para a **Semana Acadêmica 2025**. O projeto é composto por um arquivo HTML principal e uma folha de estilos CSS, utilizando JavaScript puro (Vanilla) para interatividade.

---

## 📂 Arquitetura do Projeto

### 1. `index.html` (Estrutura)
O arquivo HTML está organizado semanticamente em seções principais que facilitam a navegação e o SEO.

* **`<head>`:**
    * Importação das fontes **Urbanist** e **Lato** via Google Fonts.
    * Inclusão de arquivos de estilo (`reset.css` e `style.css`).
    * Meta tags para responsividade (`viewport`).
* **`<nav class="navbar">`:** Barra de navegação fixa que contém o logotipo e links de âncora. Inclui um menu "hambúrguer" para dispositivos móveis.
* **`<header class="banner">`:** Seção de destaque (Hero) com imagem de fundo, título do evento, botão de inscrição e uma seta animada indicando rolagem.
* **`<section id="programacao">`:** Lista cronológica das palestras. Cada palestrante é apresentado em um cartão (`div.principal`) contendo foto, tema, status da palestra e bio.
* **`<section id="apoiadores">`:** Grid responsivo exibindo os logotipos dos patrocinadores.
* **`<section id="local">`:** Informações geográficas incluindo um `iframe` do Google Maps e descrição do campus.
* **Modais:** Estruturas ocultas (`display: none`) para:
    * Detalhes do palestrante.
    * Confirmação de inscrição.

### 2. `style.css` (Estilização)
O CSS utiliza variáveis globais e design responsivo.

* **Variáveis (`:root`):** Define a paleta de cores (azuis e cinzas) para facilitar a manutenção do tema.
    * Ex: `--azul-escuro`, `--destaque`, `--cinza`.
* **Layout:** Uso extensivo de **Flexbox** (para alinhamentos na navbar e cards) e **Grid** (para a seção de patrocinadores).
* **Responsividade:** O arquivo contém *Media Queries* (`@media (max-width: 768px)`) que ajustam:
    * A navbar para um menu lateral em tela cheia.
    * O tamanho das fontes e alinhamento de textos.
    * A disposição dos elementos da programação (imagem acima do texto no mobile).
* **Animações:**
    * `bounce`: Animação da seta no banner.
    * Transições suaves (`transition`) em botões, links e imagens (escala de cinza para cor).
    * Efeito de progresso no sublinhado (`.highlight`) ao rolar a página.

---

## ⚙️ Funcionalidades JavaScript

Os scripts estão embutidos no final do `<body>` para garantir o carregamento do DOM antes da execução.

### 1. Menu Mobile (`.hamburger`)
Alterna a classe `.active` na barra de navegação e no ícone do menu ao clicar, transformando o menu horizontal em um menu vertical de tela cheia. Fecha automaticamente ao clicar em um link.

### 2. Controle de Modais
Gerencia a abertura e fechamento de janelas sobrepostas:
* **Palestrantes:** Preenche dinamicamente o conteúdo do modal (foto, nome, descrição) usando atributos de dados (`data-nome`, `data-descricao`) dos cards clicados.
* **Inscrição:** Exibe um modal de confirmação ao clicar no botão de inscrição.

### 3. Status das Palestras (Tempo Real)
Um script executa ao carregar a página (`DOMContentLoaded`) para classificar visualmente as palestras:
* Lê os atributos `data-data` (ex: "06/10/2025 19:30") e `data-vesp` (duração).
* Compara com o horário atual (`new Date()`).
* Aplica classes CSS automáticas:
    * `.palestra-futuro`: Azul (Ainda vai acontecer).
    * `.palestra-rolando`: Verde (Acontecendo agora).
    * `.palestra-passada`: Cinza (Já encerrada).

### 4. Efeitos de Scroll
* **Navbar Dinâmica:** A barra de navegação inicia transparente e ganha uma cor de fundo sólida (`#031a2e`) quando o usuário rola mais de 50px.
* **Highlight de Texto:** Calcula a posição dos elementos com a classe `.highlight` e anima uma barra de progresso sublinhada conforme eles entram na área visível da tela.

### 5. Truncamento de Texto (Mobile)
Para telas menores que 768px, o script varre as descrições dos palestrantes:
* Se o texto tiver mais de 30 palavras, ele é cortado.
* Cria um botão **"Ver mais / Ver menos"** que expande ou recolhe o texto completo dinamicamente, melhorando a experiência do usuário em telas pequenas.

