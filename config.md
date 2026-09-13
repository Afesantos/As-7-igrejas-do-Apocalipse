# CONFIGURAÇÃO E ESPECIFICAÇÃO TÉCNICA DO PROJETO
## Aplicação: As 7 Igrejas do Apocalipse - Estudo Bíblico Interativo

Este documento contém toda a arquitetura, estrutura HTML, estilização CSS, modelos de dados, regras de lógica JavaScript e comportamentos de interface necessários para que qualquer IA ou desenvolvedor possa reproduzir ou evoluir esta aplicação web completa do zero com 100% de fidelidade.

---

## 1. Visão Geral e Propósito

- **Tipo de Aplicação**: Single Page Application (SPA) autossuficiente em arquivo único (`igrejas_apocalipse.html`), sem necessidade de transpiladores, bundlers ou servidores backend.
- **Objetivo**: Proporcionar um estudo bíblico expositivo, interativo e visualmente imersivo sobre as 7 cartas às igrejas da Ásia Menor (Apocalipse caps. 1 a 3 e sua consumação profética nos caps. 7 a 22), incluindo o cenário histórico com fotos reais das ruínas arqueológicas, teofania de Cristo, promessas, denúncias judiciais e alcance universal.
- **Linguagem / Stack**: HTML5 Semântico, CSS3 Moderno (Custom Properties, Flexbox, CSS Grid, Animações, Glassmorphism, Dark Theme, Stroke Text) e Vanilla JavaScript (ES6+).
- **Recursos Locais**:
  - Pasta `assets/`: Galeria fotográfica e de imagens em alta resolução:
    - `assets/04 - Jesus no Apocalipse.png`: Imagem da visão teofânica de Cristo (Tela 1 e Galeria).
    - `assets/efeso.jpg`: Biblioteca de Celso e ruínas de Éfeso.
    - `assets/esmirna.jpg`: Pórticos e colunatas da Ágora de Esmirna (Izmir).
    - `assets/pergamo.jpg`: Cume monumental e Acrópole de Pérgamo.
    - `assets/tiatira.jpg`: Colunas e vestígios arqueológicos de Tiatira (Akhisar).
    - `assets/sardes.jpg`: Ginásio e complexo monumental de Sardes.
    - `assets/filadelfia.jpg`: Colossais pilares da Basílica de São João em Filadélfia (Alaşehir).
    - `assets/laodiceia.jpg`: Avenida colunada e ruínas de Laodiceia no vale de Lico.

---

## 2. Paleta de Cores e Design System

### 2.1. Variáveis CSS Globais (`:root`)
```css
:root {
  --bg: #0f172a;               /* Fundo principal escuro (Slate 900) */
  --card-bg: #1e293b;          /* Fundo dos cards e containers (Slate 800) */
  --accent: #f59e0b;           /* Dourado / Âmbar padrão */
  --accent-light: #fbbf24;     /* Dourado claro */
  --accent-orange: #f97316;    /* Laranja fogo / tribunal */
  --accent-emerald: #10b981;   /* Verde esmeralda / redenção */
  --accent-blue: #38bdf8;      /* Azul celeste / promessas */
  --accent-red: #f43f5e;       /* Vermelho alerta / juízo */
  --accent-purple: #c084fc;    /* Roxo / alcance universal */
  --text: #f8fafc;             /* Texto principal branco acinzentado */
  --text-muted: #94a3b8;       /* Texto secundário / descrições */
  --border: #334155;           /* Borda sutil de componentes (Slate 700) */
  --badge-bg: rgba(245, 158, 11, 0.15); /* Fundo de badges de referências */
}
```

### 2.2. Identidade Visual por Tela
- **Tela 1 (Teofania & Apresentação)**: Tons Dourados / Âmbar (`#f59e0b`, `#fbbf24`) simbolizando realeza, glória e divindade.
- **Tela 2 (Contexto Histórico das Cidades)**: Tons Âmbar / Ocre Dourado (`#fbbf24`, `#f59e0b`) e Dourado Antigo com galeria dinâmica de ruínas históricas.
- **Tela 3 (Promessas ao Vencedor)**: Tons de Azul Celeste (`#38bdf8`) com destaques em Ouro (`#fef08a`) simbolizando esperança e herança celestial.
- **Tela 4 (Denúncia & Juízo Legal)**: Tons Laranja e Vermelho (`#fb923c`, `#f43f5e`, `#fda4af`) representando o Tribunal Divino e discernimento judicial.
- **Tela 5 (Cumprimento Profético)**: Tons de Verde Esmeralda (`#34d399`, `#10b981`) e Dourado simbolizando a Nova Jerusalém e vida eterna restaurada.
- **Tela 6 (Alcance Coletivo & Universal)**: Tons de Roxo e Dourado (`#c084fc`, `#fbbf24`) destacando a voz universal do Espírito à Igreja global.
- **Tela 7 (Síntese & Lembretes)**: Combinação multicor harmoniosa em 6 cards verticais estruturados com barras laterais coloridas.
- **Tela 8 (Bibliografia & Fontes Iconográficas)**: Tons de Azul Celeste e Dourado com lista estruturada de referências bibliográficas acadêmicas, exibindo miniaturas fotográficas das ruínas e teofania, fichas iconográficas e botões com links externos diretos para as fontes na web (Wikipedia e Wikimedia Commons).

### 2.3. Numeração Gigante Vazada de Fundo (Watermark)
Cada tela possui um número d'água gigante vazado (`.page-watermark-number`) renderizado em segundo plano com `font-size: 50vh`, peso 900, preenchimento transparente, traçado `-webkit-text-stroke: 4px` e brilho neon suave específico por tela:
- **Tela 1**: Traço Ouro (`rgba(251, 191, 36, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(245, 158, 11, 0.15))`
- **Tela 2**: Traço Âmbar (`rgba(245, 158, 11, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(245, 158, 11, 0.15))`
- **Tela 3**: Traço Azul (`rgba(56, 189, 248, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(56, 189, 248, 0.15))`
- **Tela 4**: Traço Laranja (`rgba(251, 146, 60, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(251, 146, 60, 0.15))`
- **Tela 5**: Traço Esmeralda (`rgba(52, 211, 153, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(52, 211, 153, 0.15))`
- **Tela 6**: Traço Roxo (`rgba(192, 132, 252, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(192, 132, 252, 0.15))`
- **Tela 7**: Traço Ouro (`rgba(251, 191, 36, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(251, 191, 36, 0.15))`
- **Tela 8**: Traço Azul Celeste (`rgba(56, 189, 248, 0.22)`), Brilho `drop-shadow(0 0 25px rgba(56, 189, 248, 0.15))`

---

## 3. Arquitetura das Telas (8 Views Detalhadas)

O fluxo da aplicação é composto por 8 telas (`#screen1` a `#screen8`) controladas dinamicamente pela classe `.screen-view.active`:

```
[ Tela 1: Teofania & Apresentação ] 
              │ (Avançar: Seta >)
              ▼
[ Tela 2: Contexto Histórico das Igrejas ] ─── [ Tabela Completa Alternável ]
              │ (Avançar: Seta > | Voltar: Seta <)
              ▼
[ Tela 3: Promessas ao Vencedor ] ─── [ Tabela Completa Alternável ]
              │ (Avançar: Seta > | Voltar: Seta <)
              ▼
[ Tela 4: Denúncia & Juízo Legal ] ─── [ Tabela Completa Alternável ]
              │ (Avançar: Seta > | Voltar: Seta <)
              ▼
[ Tela 5: Cumprimento na Nova Jerusalém ] ─── [ Tabela Completa Alternável ]
              │ (Avançar: Seta > | Voltar: Seta <)
              ▼
[ Tela 6: Alcance Coletivo & Universal ]
              │ (Avançar: Seta > | Voltar: Seta <)
              ▼
[ Tela 7: Síntese e Lembretes ao Aluno ]
              │ (Avançar: Seta > ou Botão Bibliografia | Voltar: Seta <)
              ▼
[ Tela 8: Bibliografia & Fontes Iconográficas ] ─── (Miniaturas, Citações e Links Externos / Botão Reiniciar -> Tela 1)
```

### Detalhamento Estrutural por Tela:

### **Tela 1: Apresentação & Teofania (`#screen1`)**
- **Watermark**: Número `1`.
- **Cabeçalho**: Título `As 7 Igrejas do Apocalipse` estilizado em amarelo forte (`#fbbf24` / `var(--accent-light)`) e subtítulo explicativo.
- **Seletor Compacto (`.select-box-compact`)**: Combobox `#churchSelect1` + Botão circular "Próxima" (`#btnNextChurch1`).
- **Card Lateral de Imagem com Zoom (`.top-image-card`)**:
  - Imagem local `assets/04 - Jesus no Apocalipse.png` com hover scale e badge "Clique para ampliar".
  - Clique abre modal lightbox `#imageModal` com imagem ampliada em alta resolução.
- **Setas de Navegação**: Botão transparente com SVG neon `>` (`#btnNextArrow1`) que chama `switchScreen(2)`.
- **Área de Cards Dinâmicos (`#resultContainer1` - Grid de 3 colunas)**:
  1. *Apresentação de Cristo para a Igreja* (citação de Cristo para a igreja selecionada).
  2. *Correspondência no Cap. 1, sua Teofania* (referência e citação textual direta da teofania).
  3. *Situação / Desafio dos Irmãos na Época* (análise contextual histórica e espiritual).

---

### **Tela 2: Contexto Histórico das Igrejas (`#screen2`)**
- **Watermark**: Número `2`.
- **Cabeçalho**: Título estilizado `CONTEXTO Histórico` (Dourado/Âmbar).
- **Seletor Âmbar**: Combobox `#churchSelect2` + Botão "Próxima" `#btnNextChurch2`.
- **Card Lateral com Imagem Dinâmica (`#historyImageCard`)**:
  - Exibe a foto da ruína arqueológica da igreja selecionada (`assets/[churchKey].jpg`).
  - Título dourado `#churchHistoryTitle` e legenda descritiva `#churchHistoryDesc`.
  - Clique abre o **Lightbox Modal `#imageModal`** em alta resolução com a legenda histórica da cidade.
  - Ao mudar a igreja no seletor ou clicar em "Próxima", a foto é atualizada imediatamente.
- **Setas de Navegação**: `<` (Voltar Tela 1) e `>` (Avançar Tela 3).
- **Área de Cards Dinâmicos (`#resultContainer2` - Grid de 3 colunas)**:
  1. *🏛️ Cidade & Ambiente Cultural / Religioso* (o cenário metropolitano, templos, economia ou política local).
  2. *⚔️ Desafio Espiritual & Social dos Cristãos* (a pressão sofrida pela congregação no primeiro século).
  3. *💡 Conexão com a Mensagem de Cristo* (como o louvor, repreensão ou metáforas de Jesus dialogam com a história local).
- **Seção de Tabela Completa**:
  - Botão `#btnToggleTable2` com texto dinâmico (`"Ver Tabela Completa do Contexto Histórico"` / `"Ocultar Tabela Completa"`).
  - Container colapsável `#fullTableContainer2` contendo a tabela comparativa do contexto histórico das 7 igrejas preenchida via script.

---

### **Tela 3: Promessas ao Vencedor (`#screen3`)**
- **Watermark**: Número `3`.
- **Cabeçalho**: Título estilizado `PROMESSAS ao vencedor` (Laranja/Azul).
- **Seletor Azul**: Combobox `#churchSelect3` + Botão "Próxima" `#btnNextChurch3`.
- **Card Lateral Temático (`.top-side-card card-border-blue`)**: Ícone 👑 "Ao Vencedor" com frase reflexiva de incentivo.
- **Setas de Navegação**: `<` (Voltar Tela 2) e `>` (Avançar Tela 4).
- **Área de Cards Dinâmicos (`#resultContainer3`)**:
  1. *⚠️ Problema Principal* (com badge de referência bíblica).
  2. *🌟 Promessa de Esperança (Ao Vencedor)* (com destaque dourado).
  3. *💎 Significado do Incentivo* (significado espiritual com referências de apoio).
- **Seção de Tabela Completa**:
  - Botão `#btnToggleTable3` (`"Ver Tabela Completa das Promessas"` / `"Ocultar Tabela Completa"`).
  - Container colapsável `#fullTableContainer3` com a tabela comparativa de promessas.

---

### **Tela 4: Denúncia e Juízo Legal (`#screen4`)**
- **Watermark**: Número `4`.
- **Cabeçalho**: Título estilizado `DENÚNCIA e Juízo` e subtítulo *Tribunal Divino*.
- **Seletor Laranja**: Combobox `#churchSelect4` + Botão "Próxima" `#btnNextChurch4`.
- **Card Lateral Temático (`.top-side-card card-border-orange`)**: Ícone ⚖️ "Tribunal Divino" (Juízo, discernimento e Teshuvah).
- **Setas de Navegação**: `<` (Voltar Tela 3) e `>` (Avançar Tela 5).
- **Área de Cards Dinâmicos (`#resultContainer4`)**:
  1. *🔍 Diagnóstico / Repreensão* (apresentação do pecado/desvio ou atestado de fidelidade).
  2. *⚖️ Sentença / Advertência Judicial* (sanções, combate com a espada ou aviso de provação).
  3. *📜 Exigência Legal de Correção* (chamado ao arrependimento prático e restauração).
- **Seção de Tabela Completa**:
  - Botão `#btnToggleTable4` (`"Ver Tabela Completa da Denúncia"` / `"Ocultar Tabela Completa"`).
  - Container colapsável `#fullTableContainer4` com a tabela judicial comparativa.

---

### **Tela 5: Cumprimento Profético na Nova Jerusalém (`#screen5`)**
- **Watermark**: Número `5`.
- **Cabeçalho**: Título estilizado `CUMPRIMENTO Profético`:
  - `CUMPRIMENTO`: Verde Esmeralda vibrante (`#34d399`), *Itálico* (`font-style: italic`), **Extra-Bold** (`font-weight: 800`), em caixa alta.
  - `Profético`: Dourado/Âmbar (`#fbbf24`), *Itálico* (`font-style: italic`), peso regular (`font-weight: 400`), em Title Case.
- **Seletor Esmeralda**: Combobox `#churchSelect5` + Botão "Próxima" `#btnNextChurch5`.
- **Card Lateral Temático (`.top-side-card card-border-emerald`)**: Ícone 🏛️ "Nova Jerusalém" com ênfase na eternidade.
- **Setas de Navegação**: `<` (Voltar Tela 4) e `>` (Avançar Tela 6).
- **Área de Cards Dinâmicos (`#resultContainer5`)**:
  1. *👑 Promessa em Apocalipse 2–3* (texto da promessa concedida).
  2. *📖 Cumprimento em Apocalipse 7–22* (versículos citados na íntegra com referências em destaque).
  3. *✨ Concretização na Nova Jerusalém* (síntese teológica e escatológica).
- **Seção de Tabela Completa**:
  - Botão `#btnToggleTable5` (`"Ver Tabela Completa do Cumprimento"` / `"Ocultar Tabela Completa"`).
  - Container colapsável `#fullTableContainer5` com a tabela de cumprimento profético.

---

### **Tela 6: Alcance Coletivo & Mensagem Universal (`#screen6`)**
- **Watermark**: Número `6`.
- **Cabeçalho**: Título estilizado `ALCANCE Coletivo`:
  - `ALCANCE`: Roxo/Lilás vibrante (`#c084fc`), *Itálico* (`font-style: italic`), **Extra-Bold** (`font-weight: 800`), em caixa alta.
  - `Coletivo`: Dourado/Âmbar (`#fbbf24`), *Itálico* (`font-style: italic`), peso regular (`font-weight: 400`), em Title Case.
  - **Subtítulo**: *"A advertência solene e universal de Cristo repetida ao final de cada uma das sete cartas."*
- **Setas de Navegação**: Botões horizontais `<` (Voltar Tela 5) e `>` (Avançar Tela 7).
- **Conteúdo Central Tipográfico de Alto Impacto (`.universal-content-wrapper`)**:
  - Layout sem moldura, integrado ao fundo escuro permitindo visualizar o watermark translúcido.
  - Linhas introdutórias (`.universal-intro-text`):
    - *"A mensagem para cada igreja serve para todos os cristãos."*
    - *"O encerramento padronizado em cada uma das cartas reforça esse alcance coletivo:"*
  - Citação em tamanho expandido em **exatamente 2 linhas** (`.universal-quote-text` com `.quote-line`):
    - Linha 1: *“Quem tem ouvidos, ouça o que o <span class="word-espirito">Espírito</span> diz*
    - Linha 2: *às <span class="word-igrejas">igrejas</span>”*
    - Efeito de brilho neon azul-lavanda em "Espírito" e lilás vibrante em "igrejas".
  - Nota de ênfase inferior (`.universal-bottom-note`): *(no plural, não apenas à igreja endereçada individualmente).*
  - Texto limpo e estático, sem cursor de link, integrado naturalmente à visualização.

---

### **Tela 7: Síntese e Lembretes ao Aluno (`#screen7`)**
- **Watermark**: Número `7`.
- **Cabeçalho**: Título estilizado `SÍNTESE e Lembretes` em Dourado/Azul (sem card lateral, foco direto nos 6 pilares de síntese).
- **Setas de Navegação**: Botões horizontais `<` (Voltar Tela 6), `>` (Avançar Tela 8) e 🏠 Ícone Home (`#btnHomeArrow7` -> Retorna à Tela 1).
- **6 Cards Verticais Estruturados (`.summary-cards-container`)**:
  1. 👁️ *A Revelação de Cristo e Sua Teofania* (Borda Dourada | Badge: Soberania & Presença).
  2. 🏛️ *O Contexto Histórico e Cultural das Cidades* (Borda Âmbar | Badge: Geografia & Realidade Local).
  3. 👑 *As Promessas e Recompensas ao Vencedor* (Borda Azul | Badge: Esperança & Triunfo).
  4. ⚖️ *O Discernimento do Tribunal Divino e Chamado à Correção* (Borda Laranja | Badge: Juízo & Teshuvah).
  5. 🏛️ *A Consumação Profética na Glória Eterna* (Borda Esmeralda | Badge: Nova Jerusalém).
  6. 📢 *O Alcance Universal e Contínuo a Todas as Igrejas* (Borda Roxa | Badge: Voz do Espírito).
- **Botões Finais**:
  - `📚 Ver Bibliografia & Fontes das Imagens (Página 8)` (`#btnGoToGallery7` -> Leva à Tela 8).
  - `Reiniciar Estudo Bíblico` (`#btnRestartStudy` -> Retorna à Tela 1 no topo da página).

---

### **Tela 8: Bibliografia & Fontes Iconográficas (`#screen8`)**
- **Watermark**: Número `8`.
- **Cabeçalho**: Título estilizado `BIBLIOGRAFIA e Fontes de Imagens` em tons Azul Celeste e Ouro, com subtítulo: *"Catálogo bibliográfico com as miniaturas das imagens, registros arqueológicos e links externos diretos para as fontes na web."*
- **Setas de Navegação na Mesma Linha**: Botões horizontais `<` (Voltar Tela 7) e 🏠 Ícone Home (`#btnHomeArrow8` -> Retorna à Tela 1) alinhados lado a lado no topo direito.
- **Lista Bibliográfica Estruturada (`.biblio-list`)**:
  Contém 8 cards de referências iconográficas (`.biblio-card`):
  1. **Visão de Cristo no Apocalipse**:
     - Miniatura: `assets/04 - Jesus no Apocalipse.png` (`.biblio-thumb-wrapper`)
     - Badge: `Fig. 1 • Teofania`
     - Título: *01. Visão de Cristo Glorificado entre os Candeeiros*
     - Referência: JOÃO, Apóstolo. *A Revelação de Jesus Cristo* (Apocalipse 1:12-20). Teofania Joanina na Ilha de Patmos. (Imagem gerada por IA).
     - Link Externo: [Wikipedia: Visão de João do Filho do Homem](https://pt.wikipedia.org/wiki/Vis%C3%A3o_de_Jo%C3%A3o_do_Filho_do_Homem)
  2. **Ruínas de Éfeso**:
     - Miniatura: `assets/efeso.jpg`
     - Badge: `Fig. 2 • Éfeso`
     - Título: *02. Ruínas Arqueológicas de Éfeso — Biblioteca de Celso*
     - Referência: WIKIMEDIA COMMONS. *Ephesus Archeological Site & Library of Celsus*. Selçuk, Turquia.
     - Links Externos: [Wikimedia Commons: Ephesus](https://commons.wikimedia.org/wiki/Category:Ephesus) e [Wikipedia: Éfeso](https://pt.wikipedia.org/wiki/%C3%89feso)
  3. **Ágora de Esmirna**:
     - Miniatura: `assets/esmirna.jpg`
     - Badge: `Fig. 3 • Esmirna`
     - Título: *03. Ágora de Esmirna — Colunatas e Pórticos Romanos*
     - Referência: WIKIMEDIA COMMONS. *Agora of Smyrna Archeological Complex*. Izmir, Turquia.
     - Links Externos: [Wikimedia Commons: Agora of Smyrna](https://commons.wikimedia.org/wiki/Category:Agora_of_Smyrna) e [Wikipedia: Esmirna](https://pt.wikipedia.org/wiki/Esmirna)
  4. **Acrópole de Pérgamo**:
     - Miniatura: `assets/pergamo.jpg`
     - Badge: `Fig. 4 • Pérgamo`
     - Título: *04. Acrópole de Pérgamo — Altar de Zeus e Cume Monumental*
     - Referência: WIKIMEDIA COMMONS. *Acropolis of Pergamon*. Bergama, Turquia.
     - Links Externos: [Wikimedia Commons: Acropolis of Pergamon](https://commons.wikimedia.org/wiki/Category:Acropolis_of_Pergamon) e [Wikipedia: Pérgamo](https://pt.wikipedia.org/wiki/P%C3%A9rgamo)
  5. **Colunas de Tiatira**:
     - Miniatura: `assets/tiatira.jpg`
     - Badge: `Fig. 5 • Tiatira`
     - Título: *05. Sítio Arqueológico de Tiatira — Colunas Históricas*
     - Referência: WIKIMEDIA COMMONS. *Thyatira Archeological Remains*. Akhisar, Turquia.
     - Links Externos: [Wikimedia Commons: Thyatira](https://commons.wikimedia.org/wiki/Category:Thyatira) e [Wikipedia: Tiatira](https://pt.wikipedia.org/wiki/Tiatira)
  6. **Complexo de Sardes**:
     - Miniatura: `assets/sardes.jpg`
     - Badge: `Fig. 6 • Sardes`
     - Título: *06. Complexo Monumental de Sardes — Ginásio e Cidadela*
     - Referência: WIKIMEDIA COMMONS. *Sardis Gymnasium and Synagogue Complex*. Sart, Turquia.
     - Links Externos: [Wikimedia Commons: Sardis](https://commons.wikimedia.org/wiki/Category:Sardis) e [Wikipedia: Sardes](https://pt.wikipedia.org/wiki/Sardes)
  7. **Pilares de Filadélfia**:
     - Miniatura: `assets/filadelfia.jpg`
     - Badge: `Fig. 7 • Filadélfia`
     - Título: *07. Basílica de São João em Filadélfia — Pilares Remanescentes*
     - Referência: WIKIMEDIA COMMONS. *Church of St. John in Philadelphia*. Alaşehir, Turquia.
     - Links Externos: [Wikimedia Commons: Church of St John](https://commons.wikimedia.org/wiki/Category:Church_of_St_John,_Philadelphia) e [Wikipedia: Filadélfia](https://pt.wikipedia.org/wiki/Filad%C3%A9lfia_(%C3%81sia_Menor))
  8. **Ruínas de Laodiceia**:
     - Miniatura: `assets/laodiceia.jpg`
     - Badge: `Fig. 8 • Laodiceia`
     - Título: *08. Ruínas e Avenida Colunada de Laodiceia no Lico*
     - Referência: WIKIMEDIA COMMONS. *Laodicea on the Lycus Colonnaded Street*. Denizli, Turquia.
     - Links Externos: [Wikimedia Commons: Laodicea on the Lycus](https://commons.wikimedia.org/wiki/Category:Laodicea_on_the_Lycus) e [Wikipedia: Laodiceia](https://pt.wikipedia.org/wiki/Laodiceia_do_Lico)
- **Botão Final**: `Reiniciar Estudo Bíblico` (`#btnRestartStudyFromGallery` -> Retorna à Tela 1 no topo da página).

---

## 4. Modelos de Dados em JavaScript

### 4.1. `churchImages` (Galeria Fotográfica das Ruínas Históricas)
```javascript
const churchImages = {
  efeso: {
    src: "assets/efeso.jpg",
    titulo: "Ruínas de Éfeso",
    descricao: "Biblioteca de Celso e metrópole do culto a Ártemis",
    alt: "Ruínas históricas de Éfeso"
  },
  esmirna: {
    src: "assets/esmirna.jpg",
    titulo: "Ágora de Esmirna",
    descricao: "Pórticos e colunatas da leal Esmirna (atual Izmir)",
    alt: "Ruínas da Ágora de Esmirna"
  },
  pergamo: {
    src: "assets/pergamo.jpg",
    titulo: "Acrópole de Pérgamo",
    descricao: "Cume monumental da montanha do grande Altar",
    alt: "Ruínas da Acrópole de Pérgamo"
  },
  tiatira: {
    src: "assets/tiatira.jpg",
    titulo: "Colunas de Tiatira",
    descricao: "Vestígios arqueológicos da cidade das guildas comerciais",
    alt: "Ruínas das Colunas de Tiatira"
  },
  sardes: {
    src: "assets/sardes.jpg",
    titulo: "Complexo de Sardes",
    descricao: "Ginásio e vestígios da orgulhosa fortaleza da Lídia",
    alt: "Complexo arqueológico de Sardes"
  },
  filadelfia: {
    src: "assets/filadelfia.jpg",
    titulo: "Colunas de Filadélfia",
    descricao: "Pilares históricos remanescentes em Alaşehir",
    alt: "Pilares e ruínas de Filadélfia"
  },
  laodiceia: {
    src: "assets/laodiceia.jpg",
    titulo: "Ruínas de Laodiceia",
    descricao: "Avenida colunada da rica metrópole bancária e médica",
    alt: "Ruínas monumentais de Laodiceia"
  }
};
```

### 4.2. `churchesData` (Tela 1: Teofania & Apresentação)
```javascript
const churchesData = {
  efeso: {
    nome: "Éfeso",
    apresentacao: "“Aquele que conserva na mão direita as sete estrelas e que anda no meio dos sete candeeiros de ouro”",
    teofania: "Ap 1:12–13, 16, 20: Viu sete candeeiros de ouro e, no meio deles, um semelhante a filho de homem; tinha na mão direita sete estrelas.",
    situacao: "Eram doutrinariamente vigilantes, perseverantes e rejeitavam falsos apóstolos, mas haviam abandonado o primeiro amor. A ênfase de Cristo andando entre os candeeiros lembrava que a permanência deles como testemunho dependia desse amor."
  },
  esmirna: {
    nome: "Esmirna",
    apresentacao: "“Estas coisas diz o primeiro e o último, que esteve morto e tornou a viver”",
    teofania: "Ap 1:17–18: “Eu sou o primeiro e o último e aquele que vive; estive morto, mas eis que estou vivo pelos séculos dos séculos...”",
    situacao: "Enfrentavam intensa pobreza, calúnia, perseguição e iminência de martírio (prisão por dez dias). A apresentação daquele que venceu a morte garantia que a fidelidade até a morte resultaria na coroa da vida."
  },
  pergamo: {
    nome: "Pérgamo",
    apresentacao: "“Estas coisas diz aquele que tem a espada afiada de dois gumes”",
    teofania: "Ap 1:16: “Saía da sua boca uma espada afiada de dois gumes...” ",
    situacao: "Viviam onde “está o trono de Satanás” sob pressão do culto imperial. Embora retivessem o nome de Cristo, toleravam ensinos comprometedores (Balaão e Nicolaítas). A espada da boca de Cristo aponta para o julgamento direto pela Sua palavra contra essa heresia."
  },
  tiatira: {
    nome: "Tiatira",
    apresentacao: "“Estas coisas diz o Filho de Deus, que tem os olhos como chama de fogo e os pés semelhantes ao bronze polido”",
    teofania: "Ap 1:14–15: “Os seus olhos eram como chama de fogo; os seus pés, semelhantes ao bronze polido no forno ardente...”",
    situacao: "A igreja crescia em obras, amor e fé, mas tolerava a falsa profetiza (“Jezabel”), que induzia à imoralidade e à idolatria (participação em banquetes das guildas comerciais). Os olhos de fogo penetram as intenções ocultas e os pés de bronze indicam juízo inflexível."
  },
  sardes: {
    nome: "Sardes",
    apresentacao: "“Estas coisas diz aquele que tem os sete Espíritos de Deus e as sete estrelas”",
    teofania: "Ap 1:4, 16, 20: “Dos sete Espíritos que estão diante do seu trono” e “tinha na mão direita sete estrelas”.",
    situacao: "Tinham reputação exterior de estarem vivos, mas espiritualmente estavam mortos ou moribundos em conformismo e apatia. Cristo se apresenta com a plenitude do Espírito Santo para renovar e ressuscitar a vida espiritual da comunidade."
  },
  filadelfia: {
    nome: "Filadélfia",
    apresentacao: "“Estas coisas diz o santo, o verdadeiro, aquele que tem a chave de Davi, que abre, e ninguém fechará, e que fecha, e ninguém abrirá”",
    teofania: "Ap 1:18: “...e tenho as chaves da morte e do inferno” (ampliado com Isaías 22:22 para expressar a autoridade régia messiânica).",
    situacao: "Comunidade de pouca força terrena, mas fiel à palavra, que sofria oposição da “sinagoga de Satanás”. Cristo lhes garante uma “porta aberta” que ninguém pode fechar, legitimando sua entrada e posição no Reino eterno."
  },
  laodiceia: {
    nome: "Laodiceia",
    apresentacao: "“Estas coisas diz o Amém, a testemunha fiel e verdadeira, o princípio da criação de Deus”",
    teofania: "Ap 1:5: “Jesus Cristo, a Fiel Testemunha, o Primogênito dos mortos e o Soberano dos reis da terra”.",
    situacao: "Viviam em autoilusão de autossuficiência e riqueza material, mas eram espiritualmente cegos, nus, pobres e mornos. O Cristo “Amém” e “Testemunha Fiel” confronta a farsa de sua prosperidade com o padrão absoluto da verdade divina."
  }
};
```

### 4.3. `historyData` (Tela 2: Contexto Histórico das Igrejas)
```javascript
const historyData = {
  efeso: {
    nome: "Éfeso",
    cidadeTitulo: "Centro Religioso & Culto a Ártemis (Diana)",
    cidadeDesc: "Metrópole cosmopolita e intelectualmente ativa da Ásia Menor, famosa mundialmente por abrigar o suntuoso Templo de Ártemis (uma das Sete Maravilhas da Antiguidade) e um vasto mercado de feitiçaria e magia.",
    desafioTitulo: "Ambiente Intelectualmente Ativo e Espiritualmente Perigoso",
    desafioDesc: "Os discípulos precisavam manter vigilância contínua contra influências pagãs, charlatões religiosos e a constante infiltração de falsos mestres que tentavam deturpar a verdade apostólica.",
    conexaoTitulo: "Elogio de Cristo pela Vigilância Doutrinária",
    conexaoRef: "Apocalipse 2:2",
    conexaoDesc: "Cristo elogia a congregação: “puseste à prova os que a si mesmos se declaram apóstolos e não são, e os achaste mentirosos”. O louvor demonstra o discernimento rigoroso necessário numa cidade tão desafiadora."
  },
  esmirna: {
    nome: "Esmirna",
    cidadeTitulo: "Lealdade a Roma & Culto Imperial",
    cidadeDesc: "Grande e rica cidade portuária, celebrada pela sua estrita fidelidade a Roma e pioneira na construção de templos dedicados à deusa Roma e ao culto do imperador, ostentando com orgulho sua célebre 'coroa cívica' (sua acrópole e anel de edifícios).",
    desafioTitulo: "Pobreza Extrema e Perseguição Sangrenta",
    desafioDesc: "A recusa obstinada dos cristãos em adorar César como deus ('Kyrios Kaisar') os privava de direitos civis, gerando boicote econômico, miséria material e risco constante de prisão e martírio público.",
    conexaoTitulo: "Promessa da 'Coroa da Vida' Confrontando a Coroa Cívica",
    conexaoRef: "Apocalipse 2:9-10",
    conexaoDesc: "Cristo conforta a igreja sofredora: “Sê fiel até à morte, e dar-te-ei a coroa da vida”. O galardão celestial prometido por Cristo supera e confronta diretamente a coroa cívica e terrena que a cidade orgulhosamente ostentava."
  },
  pergamo: {
    nome: "Pérgamo",
    cidadeTitulo: "Capital Política e o Principal 'Trono de Satanás'",
    cidadeDesc: "Centro administrativo e religioso supremo da província romana da Ásia, célebre pela sua monumental acrópole, templo do deus da medicina Asclépio (da serpente) e o colossal Altar de Zeus erguido no cume da montanha.",
    desafioTitulo: "Pressão Extrema pelo Culto Imperial e Sincretismo Pagão",
    desafioDesc: "Viver no próprio centro onde 'está o trono de Satanás' exigia coragem heróica. O perigo residia tanto no terror da perseguição estatal quanto na sedução de ceder ao compromisso cultural com festivais idólatras (doutrina de Balaão e dos nicolaítas).",
    conexaoTitulo: "Permanência na Fé sem Concessões Culturais",
    conexaoRef: "Apocalipse 2:13-14",
    conexaoDesc: "Cristo reconhece: “Sei onde habitas, onde está o trono de Satanás, e que conservas o meu nome e não negaste a minha fé”, ordenando firmeza inegociável contra qualquer sincretismo com a cultura pagã."
  },
  tiatira: {
    nome: "Tiatira",
    cidadeTitulo: "Polo Fabril e Fortes Guildas Comerciais",
    cidadeDesc: "Cidade próspera do vale de Lico, famosa pelo seu intenso comércio de tecidos (tintureiros de púrpura, como a convertida Lídia), curtumes, forjas de bronze e associações corporativas de ofícios (guildas).",
    desafioTitulo: "Dilema Econômico e Tentação de Concessão a 'Jezabel'",
    desafioDesc: "Para trabalhar e prosperar, os artesãos eram coagidos a pertencer a guildas que realizavam banquetes dedicados a deuses tutelares, envolvendo imoralidade e carnes consagradas. A falsa profetisa ('Jezabel') ensinava que era aceitável ceder para preservar o sustento.",
    conexaoTitulo: "Repreensão à Tolerância com o Erro para Ganho Financeiro",
    conexaoRef: "Apocalipse 2:20",
    conexaoDesc: "Cristo repreende: “Tenho contra ti que toleras essa mulher, Jezabel, que se diz profetisa... induzindo os meus servos à prostituição e a comerem das coisas sacrificadas aos ídolos”, exigindo integridade incondicional dos crentes."
  },
  sardes: {
    nome: "Sardes",
    cidadeTitulo: "Antiga Fortaleza Militar e Capital da Lídia",
    cidadeDesc: "Antiga e riquíssima capital do rei Creso, protegida por uma cidadela construída no alto de penhascos quase verticais, considerada uma fortaleza praticamente inexpugnável pelos seus governantes.",
    desafioTitulo: "Complacência, Sono Espiritual e Falsa Reputação",
    desafioDesc: "A segurança ilusória de sua história gerou negligência; a comunidade cristã foi contaminada pela mesma apatia da cidade, mantendo um nome e uma reputação de estar viva, mas estando interiormente morta e adormecida perante Deus.",
    conexaoTitulo: "O Imperativo de Vigiar diante da Memória Histórica de Invasão",
    conexaoRef: "Apocalipse 3:2-3",
    conexaoDesc: "Historicamente, a cidadela de Sardes fora conquistada de surpresa por Ciro da Pérsia e depois por Antíoco porque as sentinelas dormiram. Cristo resgata essa memória: “Sê vigilante... lembra-te, pois, do que tens recebido e ouvido, guarda-o e arrepende-te. Se não vigiares, virei como ladrão”."
  },
  filadelfia: {
    nome: "Filadélfia",
    cidadeTitulo: "Centro de Difusão Cultural Abalado por Terremotos",
    cidadeDesc: "Fundada estrategicamente como posto avançado para helenizar a região ('porta de entrada' da Ásia), localizada numa falha geológica vulcânica de solo fértil, porém assolada por terremotos violentos e contínuos que forçavam a população a fugir para os campos.",
    desafioTitulo: "Comunidade Frágil, Pouca Força e Hostilidade Local",
    desafioDesc: "Igreja de poucos recursos terrenos e sob perseguição da 'sinagoga de Satanás', mas que guardou fielmente a palavra de Cristo com perseverança exemplar.",
    conexaoTitulo: "Porta Aberta e Segurança Eterna como Colunas Inabaláveis",
    conexaoRef: "Apocalipse 3:8, 12",
    conexaoDesc: "Cristo promete: “Pus diante de ti uma porta aberta que ninguém pode fechar” e “Ao vencedor, fá-lo-ei coluna no santuário do meu Deus, e daí jamais sairá”. Em contraste com os templos terrenos que ruíam nos abalos sísmicos forçando os cidadãos a fugir, o fiel terá segurança e permanência eterna."
  },
  laodiceia: {
    nome: "Laodiceia",
    cidadeTitulo: "Metrópole Bancária, Têxtil e Escola de Medicina",
    cidadeDesc: "Cidade de fabulosa riqueza financeira (recusou ajuda do imperador Nero para reconstruir-se após o terremoto de 60 d.C.), polo industrial de túnicas e tecidos de lã negra brilhante e sede de renomada faculdade médica que fabricava a famosa pomada frígia (colírio) para os olhos.",
    desafioTitulo: "Mornidão e Ilusão de Autossuficiência Material",
    desafioDesc: "A prosperidade material embriagou a igreja em orgulho e autoconfiança ('estou rico, abastado e de nada tenho falta'), cegando-os para sua deplorável miséria espiritual e fazendo com que não sentissem necessidade de Deus.",
    conexaoTitulo: "Contraste entre a Riqueza Terrena e os Recursos Divinos",
    conexaoRef: "Apocalipse 3:17-18",
    conexaoDesc: "Cristo usa os 3 pilares da cidade para desmascará-la: “Aconselho-te que de mim compres ouro refinado pelo fogo para te enriqueceres [bancos], vestiduras brancas para te vestires [indústria têxtil] e colírio para ungires os olhos, a fim de que vejas [escola médica]”."
  }
};
```

### 4.4. `promisesData` (Tela 3: Promessas ao Vencedor)
```javascript
const promisesData = {
  efeso: {
    nome: "Éfeso",
    problema: "Perdeu o primeiro amor",
    problemaRef: "Apoc 2:4",
    promessa: "Comer da <strong class='highlight-gold'>Árvore da Vida</strong> no Paraíso de Deus.",
    promessaRaw: "Comer da Árvore da Vida no Paraíso de Deus.",
    significado: "Restauração da vida eterna perdida no Éden.",
    significadoRef: "Apoc 22:2, 14"
  },
  esmirna: {
    nome: "Esmirna",
    problema: "Pobreza e Perseguição",
    problemaRef: "Apoc 2:9-10",
    promessa: "Receber a <strong class='highlight-gold'>Coroa da Vida</strong> e não sofrer a Segunda Morte.",
    promessaRaw: "Receber a Coroa da Vida e não sofrer a Segunda Morte.",
    significado: "Garantia de imortalidade e triunfo final.",
    significadoRef: "Apoc 20:6, 14; 21:8"
  },
  pergamo: {
    nome: "Pérgamo",
    problema: "Comprometimento e Heresias",
    problemaRef: "Apoc 2:14-15",
    promessa: "Receber o <strong class='highlight-gold'>Maná Escondido</strong> e uma <strong class='highlight-gold'>Pedrinha Branca</strong> com um novo nome.",
    promessaRaw: "Receber o Maná Escondido e uma Pedrinha Branca com um novo nome.",
    significado: "Sustento divino e aceitação pessoal de Cristo.",
    significadoRef: "Apoc 7:16-17; 19:9"
  },
  tiatira: {
    nome: "Tiatira",
    problema: "Imoralidade e Falsas Doutrinas",
    problemaRef: "Apoc 2:20-21",
    promessa: "Receber <strong class='highlight-gold'>Autoridade sobre as Nações</strong> e a <strong class='highlight-gold'>Estrela da Manhã</strong>.",
    promessaRaw: "Receber Autoridade sobre as Nações e a Estrela da Manhã.",
    significado: "Participação no Reino Messias e na Sua glória.",
    significadoRef: "Apoc 20:4; 22:16"
  },
  sardes: {
    nome: "Sardes",
    problema: "Apatia e Aparência de vida",
    problemaRef: "Apoc 3:1-2",
    promessa: "Ser vestido de <strong class='highlight-gold'>vestes brancas</strong> e ter o nome no <strong class='highlight-gold'>Livro da Vida</strong>.",
    promessaRaw: "Ser vestido de vestes brancas e ter o nome no Livro da Vida.",
    significado: "Pureza, justificação e salvação garantida.",
    significadoRef: "Apoc 7:9, 13-14; 19:8; 20:12, 15; 21:27"
  },
  filadelfia: {
    nome: "Filadélfia",
    problema: "Fidelidade em Pouca Força",
    problemaRef: "Apoc 3:8",
    promessa: "Ser feito <strong class='highlight-gold'>Coluna no Templo de Deus</strong> e ter os nomes de Deus e da Nova Jerusalém escritos sobre si.",
    promessaRaw: "Ser feito Coluna no Templo de Deus e ter os nomes de Deus e da Nova Jerusalém escritos sobre si.",
    significado: "Posição de permanência, segurança e cidadania celestial.",
    significadoRef: "Apoc 7:15; 14:1; 21:2, 22; 22:4"
  },
  laodiceia: {
    nome: "Laodiceia",
    problema: "Mornidão e Auto-Suficiência",
    problemaRef: "Apoc 3:15-17",
    promessa: "<strong class='highlight-gold'>Assentar-se com Ele no Seu Trono</strong>, como Ele venceu e Se assentou no Trono do Pai.",
    promessaRaw: "Assentar-se com Ele no Seu Trono, como Ele venceu e Se assentou no Trono do Pai.",
    significado: "Plena comunhão, glória e participação na Sua realeza.",
    significadoRef: "Apocalipse 20:4; 22:3-5"
  }
};
```

### 4.5. `denunciationData` (Tela 4: Denúncia & Juízo Legal)
```javascript
const denunciationData = {
  efeso: {
    nome: "Éfeso",
    diagnosticoTitulo: "Abandono do primeiro amor",
    diagnosticoRef: "Ap 2:4",
    diagnosticoDesc: "Ortodoxia fria e perda da lealdade relacional/afetiva.",
    sentencaTitulo: "Remoção do candeeiro",
    sentencaRef: "Ap 2:5",
    sentencaDesc: "Perda do status e da função sacerdotal no santuário.",
    exigencia: "Lembrar de onde caiu, arrepender-se (teshuvah) e praticar as primeiras obras."
  },
  esmirna: {
    nome: "Esmirna",
    diagnosticoTitulo: "Nenhuma repreensão formal",
    diagnosticoRef: "Ap 2:9-10",
    diagnosticoDesc: "Atestada como fiel em extrema pobreza e perseguição.",
    sentencaTitulo: "Apenas aviso de provação",
    sentencaRef: "Ap 2:10",
    sentencaDesc: "Prisão temporária (dez dias) pela sinagoga de Satanás e risco de morte.",
    exigencia: "Ser fiel até a morte; não temer o sofrimento iminente."
  },
  pergamo: {
    nome: "Pérgamo",
    diagnosticoTitulo: "Tolerância com o sincretismo",
    diagnosticoRef: "Ap 2:14-15",
    diagnosticoDesc: "Convivência com os ensinos de Balaão e dos nicolaítas (idolatria e prostituição).",
    sentencaTitulo: "Guerra judicial com a espada da boca",
    sentencaRef: "Ap 2:16",
    sentencaDesc: "Juízo direto e combate pela palavra divina contra os infratores.",
    exigencia: "Arrepender-se imediatamente da cumplicidade ideológica e moral."
  },
  tiatira: {
    nome: "Tiatira",
    diagnosticoTitulo: "Concessão à falsa profetisa (\"Jezabel\")",
    diagnosticoRef: "Ap 2:20-21",
    diagnosticoDesc: "Sedução para práticas imorais e banquetes sacrificiais idolátricos.",
    sentencaTitulo: "Leito de dor, grande tribulação e morte de seus filhos",
    sentencaRef: "Ap 2:22-23",
    sentencaDesc: "Retribuição a cada um conforme as suas obras.",
    exigencia: "Julgar o erro interno e reter com firmeza o que já têm até a vinda do Senhor."
  },
  sardes: {
    nome: "Sardes",
    diagnosticoTitulo: "Hipocrisia e morte espiritual",
    diagnosticoRef: "Ap 3:1-2",
    diagnosticoDesc: "Fama externa de comunidade viva, mas com obras imperfeitas perante Deus.",
    sentencaTitulo: "Visita judicial de surpresa",
    sentencaRef: "Ap 3:3",
    sentencaDesc: "Sobressalto como por um ladrão, sem tempo hábil de defesa.",
    exigencia: "Vigiar, consolidar o que resta antes que morra, lembrar o que recebeu e arrepender-se."
  },
  filadelfia: {
    nome: "Filadélfia",
    diagnosticoTitulo: "Nenhuma repreensão formal",
    diagnosticoRef: "Ap 3:8-10",
    diagnosticoDesc: "Atestada por guardar a palavra e não negar o nome, mesmo com pouca força.",
    sentencaTitulo: "Nenhuma sanção punitiva",
    sentencaRef: "Ap 3:9",
    sentencaDesc: "Promessa de humilhação pública dos opositores aos seus pés.",
    exigencia: "Guardar com firmeza o que possui para que ninguém tome a sua coroa."
  },
  laodiceia: {
    nome: "Laodiceia",
    diagnosticoTitulo: "Mornidão, cegueira e autossuficiência",
    diagnosticoRef: "Ap 3:15-17",
    diagnosticoDesc: "Ilusão de riqueza material encobrindo miséria, nudez e impotência espiritual.",
    sentencaTitulo: "Vômito e rejeição sumária da boca",
    sentencaRef: "Ap 3:16",
    sentencaDesc: "Repulsa total da corte celestial à postura ambígua e acomodada.",
    exigencia: "Ser zeloso e arrepender-se; comprar d'Ele ouro provado no fogo, vestes brancas e colírio."
  }
};
```

### 4.6. `fulfillmentData` (Tela 5: Cumprimento Profético na Nova Jerusalém)
```javascript
const fulfillmentData = {
  efeso: {
    nome: "Éfeso",
    promessaTitulo: "Comer da Árvore da Vida",
    promessaRef: "Ap 2:7",
    promessaTexto: "Ter pleno acesso ao fruto da Árvore da Vida que está no meio do paraíso de Deus.",
    versiculos: [
      { ref: "Apocalipse 22:2", texto: "No meio da sua praça, de uma e outra margem do rio, estava a árvore da vida, que produz doze frutos... e as folhas da árvore são para a cura dos povos." },
      { ref: "Apocalipse 22:14", texto: "Bem-aventurados aqueles que lavam as suas vestiduras no sangue do Cordeiro, para que tenham direito à árvore da vida e possam entrar na cidade." }
    ],
    concretizacao: "O acesso cortado na queda do Éden (Gênesis 3) é plenamente restaurado na consumação da Nova Jerusalém para todos os remidos."
  },
  esmirna: {
    nome: "Esmirna",
    promessaTitulo: "Coroa da Vida & Imunidade da 2ª Morte",
    promessaRef: "Ap 2:10-11",
    promessaTexto: "Receber a coroa da vida e não sofrer o dano da segunda morte (condenação eterna).",
    versiculos: [
      { ref: "Apocalipse 20:6", texto: "Bem-aventurado e santo aquele que tem parte na primeira ressurreição; sobre estes não tem poder a segunda morte; serão sacerdotes e reinarão com Cristo." },
      { ref: "Apocalipse 20:14; 21:8", texto: "O lago de fogo é a segunda morte; o destino do remido é totalmente preservado e separado desse juízo definitivo." }
    ],
    concretizacao: "Os que enfrentam perseguição e martírio terreno são preservados da morte eterna e recebem a vida imortal com Cristo."
  },
  pergamo: {
    nome: "Pérgamo",
    promessaTitulo: "Maná Escondido & Pedrinha Branca com Novo Nome",
    promessaRef: "Ap 2:17",
    promessaTexto: "Sustento celestial secreto (maná escondido) e absolvição/identidade íntima através de uma pedrinha branca com novo nome.",
    versiculos: [
      { ref: "Apocalipse 7:16-17", texto: "Jamais terão fome, nunca mais terão sede... o Cordeiro que está no meio do trono os guiará para as fontes da água da vida." },
      { ref: "Apocalipse 19:9, 12", texto: "O banquete das Bodas do Cordeiro e a revelação do nome exclusivo de Cristo, estendendo essa aliança sagrada e íntima aos santos." }
    ],
    concretizacao: "Em contraste com a comida oferecida a ídolos terrenos, o povo de Deus é plenamente nutrido e acolhido na intimidade de Cristo."
  },
  tiatira: {
    nome: "Tiatira",
    promessaTitulo: "Autoridade sobre as Nações & Estrela da Manhã",
    promessaRef: "Ap 2:26-28",
    promessaTexto: "Governar com autoridade sobre os povos e receber a resplandecente Estrela da Manhã.",
    versiculos: [
      { ref: "Apocalipse 20:4", texto: "Vi tronos, e nestes sentaram-se aqueles aos quais foi dada autoridade de julgar... viveram e reinaram com Cristo durante mil anos." },
      { ref: "Apocalipse 22:16", texto: "Jesus declara: “Eu sou a Raiz e a Geração de Davi, a resplandecente Estrela da Manhã” — concedendo Sua própria presença aos santos." }
    ],
    concretizacao: "Os fiéis participam ativamente do reino messiânico de Cristo e desfrutam da presença e glória deslumbrante do próprio Senhor."
  },
  sardes: {
    nome: "Sardes",
    promessaTitulo: "Vestes Brancas & Nome no Livro da Vida",
    promessaRef: "Ap 3:5",
    promessaTexto: "Trajes de pureza e a confissão pública do nome perante o Pai e os anjos.",
    versiculos: [
      { ref: "Apocalipse 7:9, 13-14; 19:8", texto: "A grande multidão em pé diante do trono com vestiduras brancas alvejadas no sangue do Cordeiro (atos de justiça dos santos)." },
      { ref: "Apocalipse 20:12, 15; 21:27", texto: "O Livro da Vida é o critério decisivo na entrada da Nova Jerusalém, onde entram apenas os inscritos no Livro da Vida do Cordeiro." }
    ],
    concretizacao: "A aparência morta de Sardes é substituída pela pureza duradoura e pela segurança indelével da salvação eterna."
  },
  filadelfia: {
    nome: "Filadélfia",
    promessaTitulo: "Coluna no Templo & Nomes Santos Gravados",
    promessaRef: "Ap 3:12",
    promessaTexto: "Tornar-se coluna inabalável no santuário e receber gravados o Nome de Deus, da Nova Jerusalém e de Cristo.",
    versiculos: [
      { ref: "Apocalipse 7:15; 21:2, 22", texto: "Servem diante do trono de Deus em Seu tabernáculo; o próprio Senhor e o Cordeiro são o santuário da Nova Jerusalém." },
      { ref: "Apocalipse 14:1; 22:4", texto: "O povo remido traz na fronte o nome de Deus e do Cordeiro e contemplará Sua face face a face." }
    ],
    concretizacao: "A fraqueza terrena da congregação é transformada em permanência eterna, imutável e totalmente identificada com a presença de Deus."
  },
  laodiceia: {
    nome: "Laodiceia",
    promessaTitulo: "Assentar-se no Trono de Cristo",
    promessaRef: "Ap 3:21",
    promessaTexto: "Compartilhar o trono e a soberania régia com o próprio Cristo vencedor.",
    versiculos: [
      { ref: "Apocalipse 20:4", texto: "Os santos tomam seus lugares nos tronos para reinar com o Senhor durante o milênio." },
      { ref: "Apocalipse 22:3-5", texto: "O trono de Deus e do Cordeiro estará nela... e os Seus servos reinarão pelos séculos dos séculos." }
    ],
    concretizacao: "Aqueles que superam a cegueira e a mornidão espiritual são coroados na mais alta posição de honra, governando como coerdeiros com Cristo na glória eterna."
  }
};
```

---

## 5. Regras de Lógica e Interação (JavaScript)

### 5.1. Sincronização Global de Seleção (`syncAllSelects`)
- Quando o usuário altera a igreja em qualquer um dos 5 comboboxes (`#churchSelect1` a `#churchSelect5`), a função `syncAllSelects(val)` atualiza imediatamente o valor de todos os outros seletores.
- Ao navegar entre telas, a congregação sob análise permanece rigorosamente a mesma.

### 5.2. Botões de Avanço Cíclico ("Próxima")
- Cada seletor possui um botão "Próxima" (`#btnNextChurch1` a `#btnNextChurch5`) que avança circularmente para a igreja seguinte:
  ```javascript
  const nextIndex = (select.selectedIndex + 1) % select.options.length;
  select.selectedIndex = nextIndex;
  syncAllSelects(select.value);
  renderCurrentScreen(select.value);
  ```

### 5.3. Navegação entre Telas (`switchScreen`)
- Remove a classe `.active` de todas as `.screen-view` (`#screen1` a `#screen8`).
- Adiciona `.active` na tela alvo correspondente.
- Executa a função de renderização apropriada para a igreja ativa.
- Realiza scroll suave automático para o topo: `window.scrollTo({ top: 0, behavior: 'smooth' })`.

### 5.4. Navegação Direta a partir da Galeria (`navigateToChurch`)
- Ao clicar em um card da galeria na Tela 8:
  ```javascript
  function navigateToChurch(screenNumber, churchKey) {
    if (churchKey) {
      syncAllSelects(churchKey);
    }
    switchScreen(screenNumber);
  }
  ```
- Garante que a igreja correspondente à foto já seja pré-selecionada em todos os seletores e renderizada imediatamente na tela destino (ex: Tela 2).

### 5.5. Alternância das Tabelas Comparativas (Toggle)
- As Telas 2, 3, 4 e 5 possuem botões para expandir/recolher tabelas comparativas completas (`#btnToggleTable2`, `#btnToggleTable3`, `#btnToggleTable4`, `#btnToggleTable5`).
- Alternam a classe `.active` no container (`#fullTableContainer2`, `#fullTableContainer3`, `#fullTableContainer4`, `#fullTableContainer5`).
- Atualizam dinamicamente o texto do botão (`"Ver Tabela Completa..."` <-> `"Ocultar Tabela Completa"`).
- Aplicam rolagem suave com `scrollIntoView({ behavior: 'smooth', block: 'nearest' })`.

### 5.6. Modal Lightbox Dinâmico para Imagens
- Clicar na imagem de Jesus (Tela 1), na foto da ruína arqueológica da igreja (Tela 2) ou no botão de zoom de qualquer miniatura na Galeria (Tela 8) abre o `#imageModal` exibindo a imagem correspondente em alta resolução e sua legenda histórica/teológica.
- O modal pode ser fechado de três formas:
  1. Clicando no botão `X` (`#modalCloseBtn`).
  2. Clicando fora da imagem (no backdrop escuro).
  3. Pressionando a tecla `Escape` no teclado.

### 5.7. Abertura de Containers em Janela Pop-up em Tela Cheia (Duplo Clique / `dblclick`)
- Ao dar **duplo clique** (`dblclick`) em qualquer container de conteúdo (`.card-container`, `.summary-card-item`, `.top-side-card`, `.top-image-card`, `.universal-content-wrapper`, `.table-container`, `.biblio-card`), a função `openContainerInNewWindow(targetContainer)` é executada.
- **Especificações da Janela Pop-up**:
  - Abre uma nova janela do navegador (`window.open`) preenchendo as dimensões completas do monitor (`fullscreen=yes`, `availWidth` e `availHeight`).
  - **Isolamento de Segurança**: Aplica `newWin.opener = null;` para isolar completamente o processo da janela popup da janela principal.
  - Herda integralmente o **tema escuro imersivo original** (`--bg: #0f172a` e `--card-bg: #1e293b`).
  - Exibe o **cabeçalho do container (`.info-title`) em amarelo/dourado** em destaque no topo.
  - Aplica **escala 2x (textos e ícones dobrados de tamanho)** para projeção ou leitura confortável.
  - Contém **exclusivamente um botão de rodapé centralizado "✖ Fechar Janela"**, com suporte nativo ao fechamento ao pressionar a tecla `Escape`.

### 5.8. Navegação Global por Teclado (Atalhos)
- A aplicação oferece navegação completa através do teclado para facilitar estudos bíblicos, aulas e apresentações em projetores:
  - **Seta para a Direita (`ArrowRight`)** ou **`PageDown`**: Avança imediatamente para a próxima tela (`1` → `8`).
  - **Seta para a Esquerda (`ArrowLeft`)** ou **`PageUp`**: Retorna para a tela anterior (`8` → `1`).
  - **Tecla `Home`**: Retorna diretamente para a Tela 1 (Início).
  - *Inteligência de Foco*: O listener global ignora atalhos quando o foco estiver dentro de elementos interativos de formulário (`<select>`, `<input>`, `<textarea>`) ou quando o modal de imagem estiver ativo.

### 5.9. Otimizações de Desempenho e Segurança
- **Carregamento Otimizado de Imagens**:
  - A imagem de abertura da Tela 1 possui `fetchpriority="high"` e `decoding="async"`.
  - As fotos das ruínas e miniaturas bibliográficas possuem `loading="lazy"` e `decoding="async"` para não bloquear a thread de renderização principal.
- **Proteção de Links Externos**:
  - Todos os links para Wikimedia Commons e Wikipedia contam com `target="_blank"` e `rel="noopener noreferrer"` para mitigar riscos de *reverse tabnabbing*.

---

## 6. Mapeamento de IDs e Seletores do DOM

| Elemento | Seletor ID / Classe | Função / Responsabilidade |
| :--- | :--- | :--- |
| **Telas Principais** | `#screen1` até `#screen8` | Containers de cada uma das 8 visualizações da SPA |
| **Watermarks** | `.page-watermark-number` | Numeração de fundo vazada (1 a 8) com traço colorido e neon |
| **Comboboxes** | `#churchSelect1` a `#churchSelect5` | Seletores das 7 igrejas em cada tela de estudo |
| **Botões Próxima Igreja** | `#btnNextChurch1` a `#btnNextChurch5` | Avanço circular de igrejas |
| **Setas de Telas** | `.btn-next-screen-arrow` | Navegação direta para a próxima tela ou tela anterior |
| **Thumb de Imagem Tela 1** | `#headerThumbImg` | Imagem da visão de Jesus no Apocalipse |
| **Card de Foto Tela 2** | `#historyImageCard`, `#churchHistoryImg` | Card dinâmico com foto das ruínas da cidade |
| **Modal Lightbox** | `#imageModal`, `#modalCloseBtn` | Modal de ampliação em alta resolução para qualquer imagem |
| **Cards Dinâmicos** | `#resultContainer1` a `#resultContainer5` | Grid com os 3 cards preenchidos dinamicamente por JS |
| **Botões Toggle Tabela** | `#btnToggleTable2` a `#btnToggleTable5` | Expande/recolhe a tabela completa da respectiva tela |
| **Tabelas Completas** | `#fullTableContainer2` a `#fullTableContainer5` | Containers colapsáveis com tabelas comparativas |
| **Botão Bibliografia Tela 7** | `#btnGoToGallery7` | Navega da Tela 7 para a Tela 8 (Bibliografia & Fontes) |
| **Botão Home Telas 7 e 8** | `#btnHomeArrow7`, `#btnHomeArrow8` | Retorna para a Tela 1 (Início) |
| **Botões Reiniciar** | `#btnRestartStudy`, `#btnRestartStudyFromGallery` | Retorna para a Tela 1 no topo |
| **Bibliografia Iconográfica** | `.biblio-list`, `.biblio-card`, `.btn-external-link` | Lista de referências bibliográficas com miniaturas e links externos |

---

## 7. Checklist de Reprodução e Fidelidade Técnica

- [x] Arquivo autossuficiente único (`.html`) contendo todas as tags `<style>`, `<body>` e `<script>`.
- [x] Pasta `assets/` contendo fotos reais das 7 igrejas (`efeso.jpg`, `esmirna.jpg`, `pergamo.jpg`, `tiatira.jpg`, `sardes.jpg`, `filadelfia.jpg`, `laodiceia.jpg`) e imagem teofânica (`04 - Jesus no Apocalipse.png`).
- [x] Paleta Dark Theme completa com variáveis CSS em `:root`.
- [x] Efeito de marca d'água numérica gigante vazada (1 a 8, `50vh`, `-webkit-text-stroke: 4px`, glow suave).
- [x] Estrutura modular de 8 telas com alternância por classe `.screen-view.active`.
- [x] Tela 2 com card lateral dinâmico que troca a imagem das ruínas conforme a igreja selecionada no combobox.
- [x] Tabela comparativa histórica completa alternável na Tela 2.
- [x] Tela 8 em formato de Bibliografia Iconográfica com miniaturas fotográficas (`.biblio-thumb-wrapper`), citações completas e links externos diretos para Wikipedia e Wikimedia Commons.
- [x] Botões de navegação por setas SVG transparentes com efeito hover neon.
- [x] Navegação por teclado global (`ArrowLeft`, `ArrowRight`, `PageUp`, `PageDown`, `Home`).
- [x] Otimizações de renderização assíncrona (`loading="lazy"` e `decoding="async"`).
- [x] Sincronização bidirecional dos 5 comboboxes e avanço cíclico com `syncAllSelects()`.
- [x] Preenchimento dinâmico de cards individuais e tabelas comparativas completas.
- [x] Modal lightbox responsivo para visualização ampliada da imagem de Jesus e das ruínas arqueológicas.
- [x] Sistema de pop-up em tela cheia via duplo clique (`dblclick`) com isolamento seguro de janela (`newWin.opener = null`).
- [x] Design 100% responsivo para smartphones, tablets e desktops de alta resolução.
