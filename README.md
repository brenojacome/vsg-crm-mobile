# Especificação de Wireframe — CRM Mobile Web Visagio

> **Instrução para o designer:** Este documento é a fonte única de verdade para o wireframe do CRM mobile web da Visagio. Siga a identidade visual, a tipografia e os tokens de cor definidos abaixo. Não há logomarca nas telas — apenas as cores e a tipografia da marca. O wireframe deve representar fielmente a estrutura, hierarquia e comportamento de cada tela.

---

## 1. Parâmetros Gerais

### 1.1 Viewport de Referência
- **Dispositivo-alvo:** smartphone (iOS e Android)
- **Largura de referência:** 390px (iPhone 14 Pro)
- **Orientação:** somente portrait (vertical)
- **Safe area:** respeitar notch superior e barra inferior do sistema operacional

### 1.2 Tipografia

| Uso | Família | Peso | Tamanho |
|---|---|---|---|
| Títulos de tela | Titillium Web | Bold (700) | 22px |
| Subtítulos / rótulos de seção | Titillium Web | SemiBold (600) | 16px |
| Corpo de texto / labels de campo | Open Sans Condensed | Regular (400) | 14px |
| Texto auxiliar / metadata | Open Sans Condensed | Regular (400) | 12px |
| Labels de botão primário | Titillium Web | SemiBold (600) | 15px — **caixa baixa** |
| Tags de status | Titillium Web | Regular (400) | 11px — **caixa alta, tracking 0.12em** |

> **Nota:** Use Open Sans Condensed via Google Fonts: `https://fonts.googleapis.com/css2?family=Open+Sans+Condensed:wght@300;400;700&display=swap`. Titillium Web também disponível via Google Fonts.

### 1.3 Paleta de Cores

| Token | Hex | Uso |
|---|---|---|
| `--gv-teal` | `#00363D` | Cor principal — headers, botões primários, ícones ativos, texto em superfície clara |
| `--gv-mint` | `#A9FDAC` | Destaque — acento em tags, dot de status ativo, highlight pontual |
| `--gv-sand` | `#D6D5C9` | Superfície secundária — fundo de cards, divisores, inputs desabilitados |
| `--gv-offwhite` | `#F7F3F5` | Fundo de página (background padrão) |
| `--gv-fg-muted` | `#4D6066` | Texto secundário — empresa, metadata |
| `--gv-fg-subtle` | `#7D8B8F` | Texto terciário — placeholder, caption |
| `--gv-border` | `rgba(0,54,61,0.12)` | Bordas de cards e inputs |

**Regras de uso:**
- `#00363D` é a única cor de preenchimento sólido para componentes de ação (botões, header, ícones ativos)
- `#A9FDAC` aparece **em doses pequenas** — nunca como fundo de área grande
- Fundo de página sempre `#F7F3F5`
- **Nunca usar cantos vivos.** Raio padrão de cards: `16px`. Botões e tags: `9999px` (pill)

### 1.4 Sombras

| Nível | Valor |
|---|---|
| Cards | `0 2px 4px rgba(0,54,61,0.04), 0 12px 32px rgba(0,54,61,0.08)` |
| Botão flutuante (FAB) | `0 8px 24px rgba(0,54,61,0.20)` |
| Barra de navegação inferior | `0 -2px 12px rgba(0,54,61,0.08)` |

### 1.5 Espaçamento (base 4px)

```
4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48
```

Margem lateral padrão das telas: **20px** de cada lado.

---

## 2. Componentes Globais

### 2.1 Header de Tela

Presente em todas as telas, exceto Login.

```
┌─────────────────────────────────────────┐
│  ← [ícone voltar]   TÍTULO DA TELA      │
│  bg: #00363D · texto: #F7F3F5           │
│  altura: 56px · padding horizontal: 20px│
└─────────────────────────────────────────┘
```

- Fundo: `#00363D`
- Título: Titillium Web Bold 22px, cor `#F7F3F5`, centralizado ou à esquerda
- Ícone de voltar: outline, 24px, cor `#A9FDAC` — **aparece somente quando há tela anterior**
- Ícone de perfil/logout: canto direito, outline 24px, cor `#D6D5C9` — **somente na Home**

### 2.2 Botão Primário

```
[ label em caixa baixa ]
bg: #00363D · texto: #F7F3F5 · border-radius: 9999px
altura: 52px · padding horizontal: 24px · largura: 100%
fonte: Titillium Web SemiBold 15px
```

### 2.3 Botão Secundário

```
[ label em caixa baixa ]
bg: transparente · borda: 1.5px solid #00363D · texto: #00363D
border-radius: 9999px · altura: 52px
```

### 2.4 Botão de Ação Flutuante (FAB — "+ Novo")

```
[ + novo contato ]
bg: #00363D · texto: #A9FDAC · border-radius: 9999px
padding: 14px 20px · fonte: Titillium Web SemiBold 14px
posição: fixo no topo direito da área de conteúdo ou como FAB inferior
sombra: shadow-md
```

### 2.5 Flashcard de Item (Contato / Empresa / Lead)

```
┌──────────────────────────────────────┐  ← border-radius: 16px
│  [ícone outline 20px]  Nome          │  ← Titillium Web SemiBold 15px, #00363D
│                        Empresa       │  ← Open Sans Condensed 13px, #4D6066
│                                 [›]  │
└──────────────────────────────────────┘
bg: #FFFFFF · sombra: shadow-card · margin-bottom: 10px
padding: 16px · altura mínima: 64px
```

Para cards de **lead**, adicionar linha extra:

```
│  [status tag pill]   última interação: 12 mai    │
```

- Tag de status: bg `#00363D`, texto `#A9FDAC`, 11px uppercase, tracking 0.12em, pill

### 2.6 Campo de Input

```
┌──────────────────────────────────────┐
│ Rótulo (Open Sans Condensed 12px)    │
│ ┌────────────────────────────────┐   │
│ │ Placeholder ou valor           │   │
│ └────────────────────────────────┘   │
└──────────────────────────────────────┘
```

- Borda do input: `1px solid rgba(0,54,61,0.24)` em repouso; `2px solid #00363D` em foco
- Border-radius: `12px`
- Altura: `48px`
- Fonte do valor: Open Sans Condensed Regular 14px, cor `#00363D`
- Placeholder: Open Sans Condensed 14px, cor `#7D8B8F`
- Rótulo acima do campo: Open Sans Condensed 12px, `#4D6066`
- Campo obrigatório: asterisco `*` em `#00363D` ao lado do rótulo

### 2.7 Campo de Busca

```
[ 🔍  Buscar... ]
bg: #D6D5C9 · border-radius: 9999px · altura: 44px
fonte: Open Sans Condensed 14px · padding horizontal: 16px
```

---

## 3. Telas

---

### TELA 1 — Login

**Objetivo:** identificar o usuário de forma rápida e segura.

**Layout:**

```
┌────────────────────────────────────┐
│                                    │
│     [área teal: 35% da altura]     │
│     bg: #00363D                    │
│                                    │
│     ┌─────────────────────────┐    │
│     │  CRM Visagio            │    │  ← Titillium Web Bold 28px, #F7F3F5
│     │  acesso mobile          │    │  ← Titillium Web Light 16px, #A9FDAC
│     └─────────────────────────┘    │
│                                    │
├────────────────────────────────────┤
│                                    │
│  [Campo] E-mail corporativo *      │
│                                    │
│  [Campo] Senha *                   │
│                                    │
│  [Botão Primário] entrar           │
│                                    │
│  [Link texto] Esqueci minha senha  │  ← Open Sans Condensed 13px, #4D6066
│               centralizado         │
│                                    │
└────────────────────────────────────┘
bg geral: #F7F3F5
```

**Comportamento:**
- Foco automático no campo e-mail ao carregar
- Botão "entrar" desabilitado até ambos os campos preenchidos (estado visual: opacidade 40%)
- Ao entrar com sucesso → redireciona para **Tela 2 – Home**

---

### TELA 2 — Home (Menu Principal)

**Objetivo:** ponto de entrada direto para as três áreas. Zero fricção.

**Layout:**

```
┌────────────────────────────────────┐
│  Header teal                       │
│  "olá, [Nome]"  [ícone logout →]  │  ← Titillium Web SemiBold 18px, #F7F3F5
└────────────────────────────────────┘

┌────────────────────────────────────┐
│                                    │
│  ┌──────────────────────────────┐  │
│  │  [ícone pessoa outline 32px] │  │  ← botão-card grande
│  │  Contatos                    │  │  ← Titillium Web Bold 20px
│  └──────────────────────────────┘  │  bg: #FFFFFF, shadow-card, radius 16px
│                                    │  altura: 96px, largura: 100%
│  ┌──────────────────────────────┐  │
│  │  [ícone prédio outline 32px] │  │
│  │  Empresas                    │  │
│  └──────────────────────────────┘  │
│                                    │
│  ┌──────────────────────────────┐  │
│  │  [ícone gráfico outline 32px]│  │
│  │  Comercial                   │  │
│  └──────────────────────────────┘  │
│                                    │
└────────────────────────────────────┘
padding lateral: 20px · gap entre cards: 16px
bg: #F7F3F5
```

**Comportamento:**
- Cada card ocupa 100% da largura disponível
- Toque em qualquer área do card → navega para a seção correspondente
- Ícones: outline, 2px stroke, cor `#00363D`, tamanho 32px

---

### TELA 3 — Contatos (Lista)

**Objetivo:** ver meus contatos e iniciar ações rapidamente.

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "Contatos"   [+ novo →]│  ← FAB no header, pill, bg #00363D, texto mint
└────────────────────────────────────┘

┌────────────────────────────────────┐
│  [ 🔍  Buscar contato...         ] │  ← campo busca, bg #D6D5C9, pill
└────────────────────────────────────┘

 Meus contatos (Open Sans Condensed 12px uppercase, #7D8B8F)
 ─────────────────────────────────────

┌────────────────────────────────────┐
│  [👤]  Ana Souza              [›]  │
│        Bradesco                    │
└────────────────────────────────────┘
┌────────────────────────────────────┐
│  [👤]  Carlos Menezes         [›]  │
│        Vale                        │
└────────────────────────────────────┘
 ... (lista rolável)

bg: #F7F3F5 · padding lateral: 20px
```

**Comportamento:**
- Lista filtrada por padrão para contatos do usuário logado
- Busca filtra em tempo real por nome ou empresa
- Toque no card → **Tela 3b – Atualizar Contato**
- Toque em "+ novo" → **Tela 3a – Novo Contato**

---

### TELA 3a — Novo Contato

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "novo contato"          │
└────────────────────────────────────┘

 ─────── Obrigatórios ───────────────
                                      ← Open Sans Condensed 11px uppercase, #7D8B8F

 [Campo] Nome completo *
 [Campo] Empresa *                    ← com busca na base ao digitar (dropdown simples)

 ─────── Opcionais ──────────────────

 [Campo] Telefone
 [Campo] E-mail
 [Campo] LinkedIn

 ┌──────────────────────────────────┐
 │ [ícone agenda] importar da agenda│  ← botão secundário outline, largura total
 └──────────────────────────────────┘

 [Botão Primário] salvar contato

 [Botão Secundário / texto] cancelar
```

**Comportamento:**
- Botão "salvar contato" desabilitado até Nome e Empresa preenchidos
- "Importar da agenda" → aciona API nativa de contatos do celular → pré-preenche Nome, Telefone e E-mail
- Ao salvar com sucesso → retorna à lista de contatos com toast de confirmação (2s, bg `#00363D`, texto `#A9FDAC`)

---

### TELA 3b — Atualizar Contato

**Layout:** idêntico ao **Novo Contato**, com:
- Campos pré-preenchidos com dados existentes
- Metadata discreta no rodapé: `criado por [nome] em [data]` — Open Sans Condensed 11px, `#7D8B8F`
- Botão primário: **salvar alterações**
- Botão destrutivo (linha de texto vermelha, alinhada ao centro, abaixo do botão primário): **excluir contato** — somente visível para o criador do registro

---

### TELA 4 — Empresas (Lista)

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "Empresas"   [+ nova →]│
└────────────────────────────────────┘

 [ 🔍  Buscar empresa...           ]

 Empresas cadastradas
 ─────────────────────

┌────────────────────────────────────┐
│  [🏢]  Bradesco               [›]  │
│        bradesco.com.br             │
└────────────────────────────────────┘
┌────────────────────────────────────┐
│  [🏢]  Vale                   [›]  │
│        vale.com                    │
└────────────────────────────────────┘
 ... (lista rolável)
```

**Comportamento:**
- Busca filtra por nome de empresa
- Site exibido como texto clicável (abre browser externo)
- Toque no card → **Tela 4b – Atualizar Empresa**
- Toque em "+ nova" → **Tela 4a – Nova Empresa**

---

### TELA 4a — Nova Empresa

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "nova empresa"          │
└────────────────────────────────────┘

 ─────── Obrigatório ────────────────

 [Campo] Nome da empresa *

 ─────── Opcionais ──────────────────

 [Campo] Site (URL)
 [Campo] Endereço

 [Botão Primário] salvar empresa
 [Botão Secundário / texto] cancelar
```

---

### TELA 4b — Atualizar Empresa

**Layout:** idêntico ao **Nova Empresa**, com:
- Campos pré-preenchidos
- Seção adicional abaixo do formulário:

```
 Contatos vinculados
 ────────────────────
 [minicard] Ana Souza — Bradesco
 [minicard] João Lima — Bradesco
```

- Minicards em leitura apenas (sem edição inline)
- Botão primário: **salvar alterações**

---

### TELA 5 — Comercial / Leads (Lista)

**Objetivo:** ver leads sob minha responsabilidade e registrar novos rapidamente.

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "Comercial"  [+ novo →]│
└────────────────────────────────────┘

 [ 🔍  Buscar lead ou empresa...   ]

 ┌────────────┐  ┌──────────────┐
 │  em aberto │  │    todos     │    ← filtro tipo tab, pill
 └────────────┘  └──────────────┘
   bg: #00363D      bg: transparent
   texto: #A9FDAC   borda: #00363D

 Últimos leads — por data de contato
 ────────────────────────────────────

┌────────────────────────────────────┐
│  [📈]  Projeto Alfa           [›]  │  ← Titillium Web SemiBold 15px
│        Bradesco                    │  ← Open Sans Condensed 13px, #4D6066
│  [PROPOSTA]           12 mai 2025  │  ← tag + data, Open Sans Condensed 12px
└────────────────────────────────────┘
┌────────────────────────────────────┐
│  [📈]  Expansão Logística     [›]  │
│        Vale                        │
│  [NEGOCIAÇÃO]          5 mai 2025  │
└────────────────────────────────────┘
 ... (lista rolável)
```

**Tags de status:**
| Status | Bg | Texto |
|---|---|---|
| PROSPECÇÃO | `#D6D5C9` | `#00363D` |
| QUALIFICAÇÃO | `#00363D` | `#D6D5C9` |
| PROPOSTA | `#00363D` | `#A9FDAC` |
| NEGOCIAÇÃO | `#004A47` | `#A9FDAC` |

---

### TELA 5a — Novo Lead

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "novo lead"             │
└────────────────────────────────────┘

 ─────── Obrigatórios ───────────────

 [Campo] Nome do lead / oportunidade *
 [Campo] Empresa *                    ← busca na base

 ─────── Opcionais ──────────────────

 [Campo] Contato principal            ← busca na base de contatos
 [Seletor] Status                     ← dropdown pill:
                                         Prospecção / Qualificação /
                                         Proposta / Negociação
 [Campo texto livre] Observação       ← multiline, placeholder:
                                         "Anotação rápida pós-reunião..."
                                         altura mínima: 100px

 [Botão Primário] salvar lead
 [Botão Secundário / texto] cancelar
```

---

### TELA 5b — Atualizar Lead

**Layout:**

```
┌────────────────────────────────────┐
│  ← Header: "Projeto Alfa"          │  ← nome do lead como título
└────────────────────────────────────┘

 ─────── Dados do lead ──────────────

 [Campo] Nome *      [Seletor] Status
 [Campo] Empresa *
 [Campo] Contato principal

 ─────── Registrar interação ────────

 [Campo texto] Nova anotação          ← multiline, placeholder:
                                         "O que aconteceu hoje?"
                                         data preenchida automaticamente
 [Botão Primário] salvar atualização

 ─────── Histórico ──────────────────
                                       ← Open Sans Condensed 12px uppercase, #7D8B8F
 ┌────────────────────────────────┐
 │ 12 mai — Apresentação realizada│   ← Open Sans Condensed 13px
 │          Cliente demonstrou... │   ← texto truncado com "ver mais"
 └────────────────────────────────┘
 ┌────────────────────────────────┐
 │  5 mai — Primeiro contato      │
 └────────────────────────────────┘
 ... (ordem cronológica inversa)
```

---

## 4. Padrões de Feedback e Microinterações

| Evento | Feedback visual |
|---|---|
| Salvar com sucesso | Toast inferior: bg `#00363D`, texto `#A9FDAC`, pill, 2 segundos |
| Erro de validação | Borda do campo fica `2px solid #C0392B`, mensagem em 12px abaixo |
| Carregando lista | Skeleton cards: retângulos `#D6D5C9` animados (shimmer suave) |
| Campo em foco | Borda `2px solid #00363D`, label sobe com animação suave (220ms ease-out) |
| Botão desabilitado | Opacidade 40%, cursor padrão |

---

## 5. Navegação e Fluxo Entre Telas

```
Login
  └─▶ Home
        ├─▶ Contatos (Lista)
        │     ├─▶ Novo Contato ──────────────▶ [volta para Lista com toast]
        │     └─▶ Atualizar Contato ──────────▶ [volta para Lista com toast]
        │
        ├─▶ Empresas (Lista)
        │     ├─▶ Nova Empresa ─────────────▶ [volta para Lista com toast]
        │     └─▶ Atualizar Empresa ─────────▶ [volta para Lista com toast]
        │
        └─▶ Comercial / Leads (Lista)
              ├─▶ Novo Lead ───────────────▶ [volta para Lista com toast]
              └─▶ Atualizar Lead ────────────▶ [volta para Lista com toast]
```

**Regras de navegação:**
- Botão "←" no header sempre retorna à tela anterior (sem perda de dados — exibe confirmação se há edição em andamento)
- Gesto de swipe-back do iOS/Android deve funcionar normalmente
- Após salvar qualquer registro → retorna automaticamente à lista (sem tela de sucesso intermediária)
- Confirmar descarte: ao tentar voltar com campos editados, modal de confirmação simples: `"Descartar alterações?"` com opções **"descartar"** (texto) e **"continuar editando"** (botão primário)

---

## 6. Checklist para o Wireframe

- [ ] Todas as telas em viewport 390px de largura
- [ ] Header teal (`#00363D`) presente em todas as telas exceto Login
- [ ] Botões primários sempre pill (`border-radius: 9999px`), fundo `#00363D`
- [ ] Cards sempre com `border-radius: 16px` e sombra shadow-card
- [ ] Nenhum canto vivo em componentes interativos
- [ ] Mint (`#A9FDAC`) usado somente como destaque — nunca como fundo de área grande
- [ ] Tags de status em pill uppercase com tracking 0.12em
- [ ] Tipografia: Titillium Web em títulos e botões; Open Sans Condensed em corpo e campos
- [ ] Espaçamento lateral de 20px em todas as telas
- [ ] Campo de busca presente em todas as listas
- [ ] Feedback de toast definido após cada ação de salvar

---

*Documento gerado para uso interno da Visagio. Confidencial — não compartilhar.*
