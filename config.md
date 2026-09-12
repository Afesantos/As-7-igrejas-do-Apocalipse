# CONFIGURAÇÃO E ESPECIFICAÇÃO TÉCNICA DO PROJETO
## Aplicação: As 7 Igrejas do Apocalipse - Estudo Bíblico Interativo

Este documento contém toda a estrutura, lógica, modelos de dados, arquitetura visual e regras de negócio necessárias para que qualquer IA ou desenvolvedor possa reproduzir ou evoluir esta aplicação web completa do zero com 100% de fidelidade.

---

## 1. Visão Geral e Propósito

- **Tipo de Aplicação**: Single Page Application (SPA) em arquivo único independente (`.html`), sem necessidade de build tools, servidores Node ou dependências externas.
- **Objetivo**: Proporcionar uma experiência rica, imersiva e didática de estudo bíblico expositivo sobre as 7 cartas às igrejas da Ásia Menor (Apocalipse caps. 1 a 3 e consumação nos caps. 7 a 22).
- **Linguagem / Stack**: HTML5 Semântico, CSS3 Moderno (Custom Properties, Flexbox, CSS Grid, Animações, Glassmorphism, Dark Theme) e Vanilla JavaScript (ES6+).
- **Recursos Locais**:
  - Imagem de destaque: `04 - Jesus no Apocalipse.png` (usada no card da Tela 1 e no modal de ampliação lightbox).

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
  --border: #334155;           /* Borda sutil de componentes */
  --badge-bg: rgba(245, 158, 11, 0.15); /* Fundo de badges de referências */
}
```

### 2.2. Tematização por Tela
- **Tela 1 (Teofania)**: Tons de Ouro/Âmbar (`#f59e0b`, `#fbbf24`) simbolizando a realeza e divindade de Cristo.
- **Tela 2 (Promessas)**: Tons de Azul Celeste (`#38bdf8`) com destaques em Ouro para recompensas ao vencedor.
- **Tela 3 (Denúncia & Juízo)**: Tons de Laranja e Vermelho (`#fb923c`, `#f43f5e`, `#fda4af`) simbolizando o tribunal divino e discernimento.
- **Tela 4 (Cumprimento Profético)**: Tons de Verde Esmeralda (`#34d399`, `#10b981`) e Ouro simbolizando a Nova Jerusalém e vida eterna.
- **Tela 5 (Alcance Coletivo)**: Tons de Roxo e Dourado (`#c084fc`, `#fbbf24`) para a proclamação universal do Espírito.
- **Tela 6 (Síntese & Lembretes)**: Combinação multicor harmoniosa em cards verticais com barras laterais em gradiente.

---

## 3. Arquitetura das Telas (6 Views)

A aplicação alterna entre 6 telas principais gerenciadas via classes `.screen-view` e `.screen-view.active`:

```
[ Tela 1: Teofania & Apresentação ]
              │ (Avançar / Seta >)
              ▼
[ Tela 2: Promessas ao Vencedor ] ─── [ Tabela Completa Alternável ]
              │ (Avançar / Voltar)
              ▼
[ Tela 3: Denúncia & Juízo Legal ] ─── [ Tabela Completa Alternável ]
              │ (Avançar / Voltar)
              ▼
[ Tela 4: Cumprimento na Nova Jerusalém ] ─── [ Tabela Completa Alternável ]
              │ (Avançar / Voltar)
              ▼
[ Tela 5: Alcance Coletivo & Universal ]
              │ (Avançar / Voltar)
              ▼
[ Tela 6: Síntese e Lembretes ao Aluno ] ─── (Botão Reiniciar Estudo -> Tela 1)
```

### Detalhamento dos Componentes por Tela:

### **Tela 1: Apresentação & Teofania**
- **Cabeçalho**: Título `As 7 Igrejas do Apocalipse` e subtítulo teológico.
- **Combobox Compacto + Botão Próxima**: Seleção entre as 7 igrejas.
- **Card Lateral de Imagem com Zoom**: Thumbnail da imagem `04 - Jesus no Apocalipse.png` com hover scale, badge e clique que abre modal lightbox.
- **Seta de Navegação**: Botão transparente com ícone SVG `>` (56px) com brilho neon.
- **Área de Cards Dinâmicos (3 containers em grid)**:
  1. *Apresentação de Cristo para a Igreja* (citação formatada).
  2. *Correspondência no Cap. 1, sua Teofania* (referência e citação direta).
  3. *Situação / Desafio dos Irmãos na Época* (análise contextual histórica).

---

### **Tela 2: Promessas ao Vencedor**
- **Cabeçalho**: `PROMESSAS ao vencedor` (Laranja/Azul).
- **Combobox Temático Azul + Botão Próxima**.
- **Card Lateral**: Ícone 👑 "Ao Vencedor" com pergunta reflexiva em destaque amarelado.
- **Setas de Navegação**: `<` (Voltar Tela 1) e `>` (Avançar Tela 3).
- **Área de Cards Dinâmicos (3 containers)**:
  1. *⚠️ Problema Principal* (com badge de referência bíblica).
  2. *🌟 Promessa de Esperança (Ao Vencedor)* (destaque dourado).
  3. *💎 Significado do Incentivo* (teologia e referências de apoio).
- **Tabela Completa de Promessas**: Tabela oculta com botão de alternar visualização (todas as 7 igrejas ao mesmo tempo).

---

### **Tela 3: Denúncia e Juízo Legal**
- **Cabeçalho**: `DENÚNCIA e Juízo` com subtítulo *Tribunal Divino*.
- **Combobox Temático Laranja + Botão Próxima**.
- **Card Lateral**: Ícone ⚖️ "Tribunal Divino" (Juízo, discernimento e Teshuvah).
- **Setas de Navegação**: `<` (Voltar Tela 2) e `>` (Avançar Tela 4).
- **Área de Cards Dinâmicos (3 containers)**:
  1. *🔍 Diagnóstico / Repreensão* (com distinção para igrejas sem repreensão formal como Esmirna e Filadélfia).
  2. *⚖️ Sentença / Advertência Judicial* (sanções ou avisos de provação).
  3. *📜 Exigência Legal de Correção* (chamado ao arrependimento prático).
- **Tabela Completa de Juízo**: Tabela detalhada comparativa das 7 igrejas.

---

### **Tela 4: Cumprimento Profético na Nova Jerusalém**
- **Cabeçalho**: `CUMPRIMENTO Profético` com destaque em Esmeralda/Ouro.
- **Combobox Temático Esmeralda + Botão Próxima**.
- **Card Lateral**: Ícone 🏛️ "Nova Jerusalém".
- **Setas de Navegação**: `<` (Voltar Tela 3) e `>` (Avançar Tela 5).
- **Área de Cards Dinâmicos (3 containers)**:
  1. *👑 Promessa em Apocalipse 2–3* (resumo da promessa original).
  2. *📖 Cumprimento em Apocalipse 7–22* (lista de versículos citados na íntegra com referências).
  3. *✨ Concretização na Nova Jerusalém* (síntese escatológica).
- **Tabela Completa de Cumprimento Profético**.

---

### **Tela 5: Alcance Coletivo & Mensagem Universal**
- **Cabeçalho**: `ALCANCE Coletivo` (Roxo/Dourado).
- **Setas de Navegação**: `<` (Voltar Tela 4) e `>` (Avançar Tela 6).
- **Design de Destaque Tipográfico**:
  - Frase introdutória: *"A mensagem para cada igreja serve para todos os cristãos."*
  - Citação em grande formato: *“Quem tem ouvidos, ouça o que o Espírito diz às igrejas”* (palavra "Espírito" em dourado, "igrejas" em azul-ciano brilhante).
  - Nota de ênfase: *(no plural, não apenas à igreja endereçada individualmente).*

---

### **Tela 6: Síntese e Lembretes ao Aluno**
- **Cabeçalho**: `SÍNTESE e Lembretes` (Dourado/Azul).
- **Setas de Navegação**: `<` (Voltar Tela 5) e 🏠 Ícone Home (Voltar Tela 1).
- **5 Cards Verticais Estruturados**:
  1. 👁️ *A Revelação de Cristo e Sua Teofania* (Borda Dourada | Badge: Soberania & Presença).
  2. 👑 *As Promessas e Recompensas ao Vencedor* (Borda Azul | Badge: Esperança & Triunfo).
  3. ⚖️ *O Discernimento do Tribunal Divino e Chamado à Correção* (Borda Laranja | Badge: Juízo & Teshuvah).
  4. 🏛️ *A Consumação Profética na Glória Eterna* (Borda Esmeralda | Badge: Nova Jerusalém).
  5. 📢 *O Alcance Universal e Contínuo a Todas as Igrejas* (Borda Roxa | Badge: Voz do Espírito).
- **Botão Final**: `Reiniciar Estudo Bíblico` (retorna à Tela 1 no topo da página).

---

## 4. Modelos de Dados em JavaScript

Abaixo estão os objetos de dados que alimentam a aplicação dinamicamente:

### 4.1. `churchesData` (Tela 1: Teofania)
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

### 4.2. `promisesData` (Tela 2: Promessas ao Vencedor)
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

### 4.3. `denunciationData` (Tela 3: Denúncia & Juízo)
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

### 4.4. `fulfillmentData` (Tela 4: Cumprimento Profético)
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

1. **Sincronização de Seleção de Igrejas**:
   - Quando o usuário altera a igreja em qualquer combobox (`#churchSelect1`, `#churchSelect2`, `#churchSelect3`, `#churchSelect4`), a função `syncAllSelects(value)` atualiza o valor de todos os outros comboboxes.
   - Assim, ao navegar entre telas, o estudo permanece focado na mesma igreja selecionada.

2. **Botões de Avanço Cíclico ("Próxima")**:
   - Cada combobox possui um botão "Próxima" ao lado que avança para a igreja seguinte de forma circular (`(currentIndex + 1) % options.length`), renderizando imediatamente o card da tela ativa.

3. **Troca de Telas (`switchScreen(screenNumber)`)**:
   - Remove a classe `.active` de todas as `.screen-view`.
   - Adiciona `.active` na tela destino correspondente.
   - Atualiza a renderização da igreja selecionada.
   - Executa `window.scrollTo({ top: 0, behavior: 'smooth' })`.

4. **Botões de Tabela Completa (Toggle)**:
   - Alternam a classe `.active` no container da tabela correspondente (`#fullTableContainer2`, `#fullTableContainer3`, `#fullTableContainer4`).
   - Alteram o texto do botão entre `"Ver Tabela Completa..."` e `"Ocultar Tabela Completa"`.
   - Fazem rolagem suave até a tabela (`scrollIntoView`).

5. **Modal Lightbox de Imagem**:
   - Ao clicar na imagem de capa (`#headerThumbImg`), adiciona `.active` em `#imageModal`.
   - Fecha ao clicar no botão 'X', ao clicar fora da imagem no backdrop escuro ou ao pressionar a tecla `Escape`.

6. **Abertura de Containers em Nova Janela (Duplo Clique / `dblclick`)**:
   - Ao clicar duas vezes (`dblclick`) em qualquer container (`.card-container`, `.summary-card-item`, `.top-side-card`, `.top-image-card`, `.universal-content-wrapper`, `.table-container`), a função `openContainerInNewWindow(containerElement)` é disparada.
   - Uma nova janela pop-up (`window.open`) é aberta ocupando as dimensões de tela cheia do monitor (`fullscreen=yes`), mantendo o **tema escuro imersivo original (Dark Theme: fundo `--bg` e card `--card-bg`)**, exibindo o **cabeçalho do container em amarelo/dourado (`.info-title`) em destaque no topo** com **textos ampliados em 2x (escala dobrada)** para máxima legibilidade e exclusivamente um botão de rodapé "✖ Fechar Janela" (com suporte também ao fechamento via tecla `Escape`).

---

## 6. Checklist de Reprodução para Nova IA / Desenvolvedor

- [x] Criar arquivo HTML único contendo tags `<style>`, `<body>` e `<script>`.
- [x] Aplicar paleta de cores Dark Theme com variáveis CSS globais.
- [x] Montar a estrutura de 6 telas com id `screen1` até `screen6`.
- [x] Inserir os botões de navegação por setas com SVG inline e hover glow de alta visibilidade.
- [x] Adicionar os scripts de sincronização de comboboxes e renderização via innerHTML.
- [x] Preencher as tabelas comparativas das Telas 2, 3 e 4 no carregamento inicial.
- [x] Incluir suporte ao modal lightbox para exibição da imagem `04 - Jesus no Apocalipse.png`.
- [x] Implementar ouvinte global de duplo clique (`dblclick`) para abrir containers em janela pop-up em tela cheia com tema escuro (Dark Theme), textos em escala 2x e botão único de fechar.
- [x] Garantir layout responsivo para smartphones e desktops via media queries.
