# Patrimonium Design System · AI Context

> Documento técnico denso · otimizado para consumo por IAs geradoras de código (Google AI Studio, Cursor, Claude, v0, Lovable, etc.).
> Cole este arquivo no contexto inicial do prompt ao pedir geração de UI Patrimonium.
> Versão 2.0.1 · maio 2026.

---

## INSTRUÇÃO DE USO PARA IA

Você está construindo interfaces para **Patrimonium Contabilidade**, uma empresa brasileira de contabilidade consultiva e inteligência tributária. Toda interface produzida deve respeitar este sistema sem exceção. Quando uma decisão de design não estiver coberta abaixo, decida pelos princípios da seção 1. Nunca invente cor, token, tamanho ou regra fora do sistema.

Recursos complementares neste repositório:
- `tokens/colors_and_type.css` — tokens em CSS variables (importar no projeto)
- `tokens/tokens.json` — tokens em formato Style Dictionary
- `fonts/` — RNS Sanz, 7 pesos em .woff
- `assets/logos/` — logos PNG da marca
- `preview/*.html` — referência visual renderizada de cada componente
- `docs/PRINCIPLES.md` — princípios escritos
- `docs/CHANGELOG.md` — histórico do DS
- `docs/CONTRIBUTING.md` — processo de mudança

---

## 1. PRINCÍPIOS (tiebreaker quando em dúvida)

1. **Solidez antes de virtuosismo** — Patrimonium é parceiro fiscal, não SaaS divertido. Confiança > criatividade. Convencional bem feito > novo arriscado.
2. **O miolo é sagrado** — selo P-cápsula com miolo verde é o motivo central. Toda sub-marca herda; nenhuma reinventa. Verde só como acento, nunca como cor de texto sobre claro nem em headline.
3. **Discreet, low-spread** — sombras sutis, cor-base `rgba(15,23,42,X)`, alpha máximo 0.12. Sem offset horizontal. Sem neon, sem glow.
4. **Paleta restrita por escolha** — 3 cores principais + 6 de apoio. Sem subtons funcionais (sem `green-100`, `green-500`). Se precisa de tom intermediário, repense antes de inventar.
5. **Saltos grandes, não gradação fina** — radius dobra a cada degrau (8/16/32/999). Pequenas diferenças confundem hierarquia. Cada valor tem função.
6. **Affirmative ≠ Save** — botão verde pill (affirmative) é reservado para ganho do cliente (recuperar, aprovar crédito). "Salvar/Enviar/Confirmar" é primary azul.
7. **Branded House, não Casa de Marcas** — toda sub-marca herda sistema visual da matriz. Sem variação de paleta/tipografia/voz por vertical. Diferencia pelo nome, não por cor.

---

## 2. PALETA DE CORES (HEX exatos, sem subtons)

### Brand principais (sagradas)
- `--brand-blue` `#1A3375` — Patrimonium Blue, primária, headlines, botões padrão, links, ícones institucionais
- `--brand-green` `#00FCA8` — Patrimonium Green, acento, P-cápsula, affirmative, status "ativo/positivo"
- `--brand-white` `#FFFFFF` — Branco, fundo principal do produto

### Brand apoio (6, sem subtons)
- `--brand-navy-deep` `#0B1B3F` — Navy escuríssimo, fundo invertido, dark mode, hero
- `--brand-navy-soft` `#3059AF` — Navy médio, raro
- `--brand-teal` `#0C998F` — Teal, data viz, accents secundários
- `--brand-cyan` `#1AFFFF` — Ciano luminoso, raro
- `--brand-neutral-dark` `#3D3D3D` — Neutro escuro, texto corpo

### Neutros canônicos (3, consolidados)
- `--neutral-surface` `#F7F8FB` — fundo de página, header de tabela, áreas neutras
- `--neutral-light` `#C8C8CC` — borders, dividers, disabled fill, placeholders
- `--neutral-strong` `#3D3D3D` — texto corpo, ícones, labels

### Semânticas (6 tokens, cada um com versão `-bg` clara para light e par `-dark` / `-bg-dark` para dark mode)
- `--success` `#1F8F5C` / `--success-bg` `#E6F7EF` / `--success-dark` `#4FCB87` / `--success-bg-dark` `#1A6E48`
- `--warning` `#F5A623` / `--warning-bg` `#FEF3C7` / `--warning-dark` `#FFB84D` / `--warning-bg-dark` `#8C5A0F`
- `--danger` `#B91C1C` / `--danger-bg` `#FEE2E2` / `--danger-dark` `#F08080` / `--danger-bg-dark` `#8B2828`
- `--info` `#1A3375` (reusa brand-blue) / `--info-bg` `#E0E7FF` / `--info-dark` `#95ADE3` / `--info-bg-dark` `#2A4FA0`
- `--neutral` `#475569` / `--neutral-bg` `#EEF2F6` / `--neutral-dark` `#8A95A8` / `--neutral-bg-dark` `#3B4555`
- `--pending` `#3730A3` / `--pending-bg` `#E0E7FF` / `--pending-dark` `#A99DEC` / `--pending-bg-dark` `#4A3DA0`

**Quando usar cada par:**
- `{semantic}` + `{semantic}-bg` — light mode, do jeito que sempre foi
- `{semantic}-dark` + `{semantic}-bg-dark` — dark mode. `-dark` (cor cheia clareada) serve como borda, ícone, dot, badge solid. `-bg-dark` (fundo escuro) recebe texto branco.
- Todos os pares passam WCAG: texto branco sobre `-bg-dark` ≥ AA · `-dark` sobre `-bg-dark` ≥ 3.0 (mínimo WCAG 1.4.11 para elementos não-texto).

### Foreground (texto)
- `--fg-1` (headings on light) — usar `--brand-blue` (`#1A3375`). **Mudança na v1.0.1: heading em light deixou de usar navy-deep para liberar navy-deep ao seu papel de cor invertida. Ver "Hierarquia de uso da paleta" abaixo.**
- `--fg-2` (body) — usar `--neutral-strong`
- `--fg-3` (secondary, metadados) — usar `--neutral-light`
- `--fg-on-brand` (texto sobre azul/verde) — usar `#FFFFFF`
- `--fg-link` — usar `--brand-blue`

### Transparências autorizadas (não inventar outras)
- `--backdrop-modal` `rgba(15,23,42,0.45)` — fundo de modal/drawer
- `--focus-ring` `0 0 0 4px rgba(26,51,117,0.18)` — anel de foco
- `--menu-hover-on-light` `rgba(26,51,117,0.06)` — hover sobre fundo claro
- `--menu-hover-on-dark` `rgba(255,255,255,0.08)` — hover sobre fundo escuro
- `--menu-active-on-dark` `rgba(255,255,255,0.12)` — ativo sobre fundo escuro

### Hierarquia de uso da paleta (prescritivo — tiebreaker em dúvida)

Toda cor declarada tem tarefa específica. Não há "cor decorativa" no sistema. Aplicação fora do papel descaracteriza a marca. Esta seção existe porque IAs geradoras tendem a aplicar paleta por convenção de mercado ("SaaS financeiro = navy escuríssimo em tudo + um pouco de azul + verde") em vez de aplicar por intenção da marca Patrimonium.

#### Principais (sagradas)

**`--brand-blue` `#1A3375` carrega a interface.** Cor "default escura" do sistema Patrimonium. Tudo que precisa de cor de marca sem ser acento usa brand-blue: headings em light, botões primary, links, ícones institucionais, focus ring, eyebrows, borda destacada, fill checked em checkbox/radio/switch, camada elevada em dark mode (cards, modais, banners, painéis).

**`--brand-green` `#00FCA8` é o miolo da marca, aplicado.** Acento substancial e recorrente — aparece em múltiplas superfícies da mesma tela, não restrito a um único elemento. Usos canônicos:
- Botão affirmative (recuperar, aprovar crédito, ativar)
- Dots e badges de status "ativo / online / aprovado / positivo"
- Variação positiva em KPI (`+18%`)
- Indicador de item ativo em sidebar (faixa lateral 3px)
- Highlight de progresso concluído
- Avatar do usuário no menu (variante green)
- Accent em hero/landing (separador, número grande)

Se uma tela não tem verde em nenhum lugar, ela não está Patrimonium. Se tem verde em um único elemento isolado no canto, também não — falta presença.

**`--brand-white` `#FFFFFF`** — fundo principal em light. Texto sobre fundos escuros (brand-blue, navy-deep, `-bg-dark`).

#### Apoio (papéis funcionais precisos, sem decoração)

**`--brand-navy-deep` `#0B1B3F` é cor invertida, não default escura.** Aparece apenas em:
- Fundo do dark mode (shell da aplicação)
- Hero institucional, dark banner global
- Texto sobre `--brand-green` (contraste WCAG do affirmative)
- Fundo de sidebar/topbar quando o produto opta pelo dark navigation
- Fundo de tooltip

Não usar navy-deep como cor "default escura" em light. **Headings em light usam `--brand-blue`.** O erro mais comum de IA é interpretar produto financeiro = "navy quase preto em tudo" — isso é convenção de mercado, não Patrimonium.

**`--brand-navy-soft` `#3059AF` — hierarquia visual secundária.** Onde brand-blue é o elemento principal e algo subordinado precisa existir: sub-links, sub-nav, série secundária em gráfico (quando a primária é brand-blue), fundo de painel/seção que precisa se diferenciar do principal, border de input no hover (alternativa ao escurecimento). Nunca como heading/texto principal — fere a hierarquia.

**`--brand-teal` `#0C998F` — categoria temática e data viz primária.** Cor para diferenciar conceitos não-semânticos:
- Ícones de categoria de produto (Arquivo Digital, BPO, etc.) quando precisam de diferenciação visual além do nome
- Série principal em gráfico de área/linha
- Tag/chip de categoria de produto ou tipo de documento
- Ilustração em empty state
- Status "em consultoria/em revisão" quando precisa diferenciar de pending

Libera o `--brand-green` pra ser identidade de marca, não cor de categoria.

**`--brand-cyan` `#1AFFFF` — acento de destaque excepcional sobre fundo escuro.** Pensar como "fósforo": acende, não preenche.
- Badge "Novo", "Beta"
- Glow em CTA de hero dark
- Ponto de atenção em landing
- Linha de progresso em loading dark

Saturado demais para light — em light, preferir `--brand-blue` ou `--brand-green`.

**`--brand-neutral-dark` `#3D3D3D`** — equivalente a `--neutral-strong` (texto corpo). Há sobreposição de naming entre brand de apoio e neutros canônicos — alinhar em v1.1.

#### Por modo (resumo aplicado)

**Light mode (fundo `--brand-white`):**
- Headings: `--brand-blue`
- Body: `--neutral-strong`
- Botões primary, links, ícones de marca: `--brand-blue`
- Sub-links, hierarquia secundária: `--brand-navy-soft`
- Affirmative, status positivo, dot ativo, KPI positivo: `--brand-green`
- Categorias temáticas, data viz, chips de tipo: `--brand-teal`
- Banner global, hero: fundo `--brand-navy-deep` com texto branco

**Dark mode (fundo `--brand-navy-deep`):**
- Fundo da aplicação (shell): `--brand-navy-deep`
- Camada elevada (card, modal, banner, painel): `--brand-blue`
- Texto principal: `--brand-white`
- Sub-hierarquia, série secundária: `--brand-navy-soft`
- Affirmative, status positivo, dot ativo, KPI positivo: `--brand-green`
- Categorias temáticas, data viz: `--brand-teal`
- Acento de destaque excepcional ("Novo", glow): `--brand-cyan`
- Estados semânticos: pares `-dark` (cor cheia) + `-bg-dark` (fundo), texto branco

#### Teste de cinco segundos (auto-diagnóstico antes de entregar)
Olhe a tela em miniatura, sem ler. Três checagens:
1. Tem verde em mais de um lugar? Se não, falta verde.
2. Identifica como Patrimonium em 5 segundos pela combinação verde + navy/azul? Se não, falta presença de marca.
3. Parece "qualquer SaaS financeiro profissional"? Se sim, a paleta foi aplicada por convenção, não por intenção.

---

### Regras de cor
- **Sem subtons.** Não criar `green-100`, `blue-50`, etc.
- **Para "versão clara" de semântica:** usar o token `-bg` existente.
- **Verde nunca como texto sobre branco.** Para verde texto-safe, usar `--success` (`#1F8F5C`).
- **Sem opacidade em texto/ícones para "atenuar".** Usar token de cor correto.

---

## 3. TIPOGRAFIA

**Família:** RNS Sanz (7 pesos disponíveis em `fonts/`: Light 300, Normal 400, Medium 500, SemiBold 600, Bold 700, ExtraBold 800, Black 900).

**Fallback stack:** `"RNS Sanz", "Inter", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`

**Mono (CNPJ, valores tabulares):** `ui-monospace, "SF Mono", Menlo, Consolas, monospace`. Sempre ativar `font-variant-numeric: tabular-nums` em colunas de valor.

### Escala (10 estilos oficiais)

| Token | Tamanho | Peso | Line-height | Letter-spacing | Caixa |
|---|---|---|---|---|---|
| `--fs-display` | 56px | 800 ExtraBold | 1.1 | -0.02em | sentence |
| `--fs-h1` | 40px | 700 Bold | 1.1 | -0.01em | sentence |
| `--fs-h2` | 32px | 700 Bold | 1.25 | -0.01em | sentence |
| `--fs-h3` | 24px | 600 SemiBold | 1.25 | 0 | sentence |
| `--fs-h4` | 20px | 500 Medium | 1.4 | 0 | sentence |
| `--fs-lg` (body lg) | 18px | 400 Normal | 1.5 | 0 | sentence |
| `--fs-md` (body) | 16px | 400 Normal | 1.5 | 0 | sentence |
| `--fs-sm` (body sm) | 14px | 400 Normal | 1.5 | 0 | sentence |
| `--fs-eyebrow` | 12px | 700 Bold | 1.2 | +0.12em | UPPER |
| `--fs-caption` | 12px | 600 SemiBold | 1.3 | +0.02em | UPPER |

### Regras tipográficas
- **Display** é voz da marca em volume máximo. Usar em hero, landing, capas. **Não usar dentro do produto.**
- **H1** único por tela. Sem exceção.
- **Eyebrow** sempre UPPER com letter-spacing positivo. Usar acima de seção, em labels de tabela (`DOCUMENTO`, `EMPRESA`, `STATUS`).
- **Caption** sempre UPPER. Usar em timestamps, metadados.
- **Sentence case** em botões, labels de form, títulos (`E-mail`, `Razão social`, "Atoms - Botões").
- **lowercase intencional** em `patrimonium®` e nos nomes de sub-marca quando ancorados ao símbolo (`patrimonium news`, `radar`).
- **Sem ponto final** em labels e badges. Ponto final só em texto corrido.

---

## 4. SPACING (base 4px · 11 níveis)

```
--space-1: 4px     preferencial
--space-2: 8px     preferencial
--space-3: 12px    exceção (gaps internos finos)
--space-4: 16px    preferencial
--space-5: 20px    raro (evitar)
--space-6: 24px    preferencial
--space-7: 32px    preferencial (gap entre seções)
--space-8: 40px    raro (evitar)
--space-9: 48px    exceção
--space-10: 64px   preferencial (separação grande)
--space-11: 80px   exceção (hero, landing)
```

**Hierarquia:**
- Preferenciais: 4, 8, 16, 24, 32, 64
- Exceção (com razão): 12, 48, 80
- Evitar: 20, 40

Nunca usar valores fora dessa escala (6, 10, 14, 18, 28, 36 são proibidos — sempre ajustar pro vizinho mais próximo).

---

## 5. RADIUS

| Token | Valor | Uso |
|---|---|---|
| (exceção mini-controle) | 4px | Apenas em elementos com menor dimensão ≤ 20px (checkbox indicator). Sem token nomeado. |
| `--radius-sm` | 8px | Embalagens pequenas: chips, inputs, badges, botões gerais, tooltips, dropdowns |
| `--radius-md` | 16px | Containers padrão: cards, modais, painéis, drop zones |
| `--radius-lg` | 32px | Containers grandes: hero, sheets, banners institucionais |
| `--radius-pill` | 999px | Identidade e ação: botão affirmative, dots, logo, status circular, switch track |

**Regra:** valores fora da escala (6, 10, 12, 14, 18, 20, 24) ajustar para o vizinho mais próximo, preferindo o menor.

**Híbrido em botões:**
- 8px em primary, secondary, ghost, destructive
- pill 999px em affirmative (sempre) e em primary `lg` em contexto institucional

---

## 6. SOMBRAS (3 níveis, sempre tinta navy)

Cor-base `rgba(15,23,42,X)`, nunca preto puro. Sem offset horizontal. Alpha total ≤ 0.12.

```css
--shadow-1: 0 1px 2px rgba(15, 23, 42, 0.04);
  /* repouso, cards default, divisórias sutis */

--shadow-2: 0 1px 2px rgba(15, 23, 42, 0.06),
            0 4px 12px rgba(15, 23, 42, 0.08);
  /* hover, dropdown, tooltip, popover */

--shadow-3: 0 4px 8px rgba(15, 23, 42, 0.08),
            0 16px 40px rgba(15, 23, 42, 0.12);
  /* modal, drawer, sheet, overlay */
```

**Proibido:** sombra colorida, spread alto, neon glow, sombra preta pura.

---

## 7. ICONOGRAFIA

**Sistema:** Lucide (`https://lucide.dev`). Carregamento via CDN `https://unpkg.com/lucide@latest`.

**Tamanhos:**
- `icon/sm` 16px — chips, inputs pequenos, badges
- `icon/md` 20px (default) — botões, inputs, ao lado de texto
- `icon/lg` 24px — menu lateral, topbar, navegação
- `icon/xl` 32px — empty states, hero, ilustrações

**Stroke:** **1.5px uniforme em todos os tamanhos.** O stroke NÃO escala com o ícone (decisão deliberada para consistência).

**Cor:** `currentColor` — sempre herda do contexto. Nunca cor fixa.

**Cantos:** `stroke-linecap="round"` `stroke-linejoin="round"`.

**Se ícone não existe no Lucide:** desenhar seguindo as mesmas regras (viewBox 24×24, stroke 1.5px, round caps).

**Sem emoji como ícone.** Em nenhuma superfície.

---

## 8. GRID E BREAKPOINTS

**Mobile-first.**

```
sm:  ≥ 640px    4 colunas, gutter 16, margin 16
md:  ≥ 768px    8 colunas, gutter 16, margin 24
lg:  ≥ 1024px   12 colunas, gutter 24, margin 32+
xl:  ≥ 1280px   12 colunas
2xl: ≥ 1536px   12 colunas, max-width 1280
```

**Container:** `--container-max` 1280px.
**Conteúdo de leitura:** `--content-max` 880px.

---

## 9. ESTADOS INTERATIVOS

**Regra transversal:** **Hover = Focus visualmente.** Em todo o sistema. WCAG exige focus visível, não diferente de hover. Se hover já produz mudança visual perceptível, satisfaz a regra.

### Estados padrão
- **Default** — estado base
- **Hover/Focus** — mesmo tratamento visual (escurecimento de 6-10%, ou border destacado, ou anel de foco)
- **Active/Press** — escurece mais (12-15%), escala 0.98
- **Disabled** — `--neutral-light` no fundo + `--neutral-light` no texto. **Sem `opacity: 0.5`.** Cursor `not-allowed`.
- **Loading** — spinner monocromático sobre o próprio elemento
- **Error** — border `--danger`, label em `--danger`, helper text em `--danger`

### Anel de foco
`--focus-ring` = `0 0 0 4px rgba(26,51,117,0.18)`. Navy 18%, 4px spread, mantém radius do elemento. Nunca outline preto do browser.

### Hit area mínima
**44×44px** em qualquer elemento interativo, mesmo com indicator visual menor. Vale para checkbox indicator (18×18), ícones de ação (16), kebab, close.

---

## 10. MOTION

### Durações
- `--dur-instant` 0ms — focus ring, mudança lógica imediata
- `--dur-fast` 120ms — active state, micro-feedback de clique
- `--dur-base` 200ms — hover, transições padrão
- `--dur-moderate` 250ms — entrada de tooltip, dropdown, popover
- `--dur-slow` 320ms — entrada de modal, drawer, sheet

### Easing
- `--ease-out` `cubic-bezier(0.16, 1, 0.3, 1)` — movimentos que terminam (entradas)
- `--ease-std` `cubic-bezier(0.4, 0, 0.2, 1)` — movimentos contínuos
- `linear` — apenas progress bars determinadas

### Regras
- Animação serve função, nunca decoração
- Respeitar `prefers-reduced-motion`
- Animar `transform` e `opacity`, não `width/height`
- Sem loops infinitos automáticos (exceto loaders enquanto há "carregando")
- Sem flash > 3× por segundo
- Sem bounce, spring ou parallax

---

## 11. COMPONENTES (specs operacionais)

### 11.1 Button
- **Variants:** `primary` · `secondary` · `ghost` · `destructive` · `affirmative`
- **Sizes:** `sm` 36px alt · `md` 44px alt · `lg` 52px alt
- **Estados:** default, hover/focus, active, disabled, loading, error
- **Tipografia:** Body (16px) peso 500 em `md`; sm usa 14px; lg usa 18px
- **Padding:** 12px 24px (md), proporcional nos outros
- **Radius:**
  - `primary`, `secondary`, `ghost`, `destructive`: **8px**
  - `affirmative`: **pill 999px** sempre
  - `primary lg` em contexto institucional pode usar pill
- **Cores por variant:**
  - `primary`: fundo `--brand-blue`, texto branco
  - `secondary`: fundo branco, texto `--brand-blue`, border 1.5px `--brand-blue`
  - `ghost`: fundo transparente, texto `--brand-blue`, sem border
  - `destructive`: fundo `--danger`, texto branco
  - `affirmative`: fundo `--brand-green`, texto `--brand-navy-deep` (contraste WCAG)
- **Hover:** brightness 0.94 (6% mais escuro)
- **Hit area:** mínima 44×44 (size `sm` 36 precisa de padding extra invisível)

### 11.2 Form fields (text input)
- **Altura:** 44px (`md`)
- **Radius:** 8px (`--radius-sm`)
- **Padding interno:** 12px 14px
- **Border:** 1px `--neutral-light` default, 1.5px `--brand-blue` em focus
- **Label:** Eyebrow (12px peso 700 UPPER +0.12em), cor `--brand-blue`
- **Placeholder:** cor neutra média
- **Helper text:** Body sm (14px peso 400), cor `--neutral` ou `--danger` (erro)
- **Error:** border `--danger`, label em `--danger`, helper em `--danger`
- **Disabled:** fundo `--neutral-light`, texto `--neutral-light`

### 11.3 Form controls (Checkbox, Radio, Switch)
- **Checkbox indicator:** 18×18px, **radius 4px** (exceção mini-controle)
- **Radio indicator:** 18×18px, radius pill 999px
- **Switch:** track 36×20px radius pill, knob 16×16 radius pill
- **Border default:** 1.5px `--neutral-light`
- **Fill checked/on:** `--brand-blue`
- **Estados:** default, selected, hover/foco, hover/foco + selected, erro, erro + selected, desativado, desativado + selected
- Checkbox tem também: indeterminado
- **Hit area:** 44×44 obrigatório
- **Gap controle → label:** 8px (`--space-2`)

### 11.4 Badge & Pills
- **Radius:** pill 999px (badges) ou 8px (chips de filtro)
- **Padding:** 4px 8px (sm), 6px 12px (md)
- **Tipografia:** Body sm (14px) ou Caption (12px UPPER)
- **Variantes:** success, warning, danger, info, neutral, pending — cada uma com versão solid e light (light usa `-bg` como fundo + cor cheia no texto/dot)
- **Dot status:** círculo 6-8px de cor semântica à esquerda do texto

### 11.5 Avatar
- **Tamanhos:** 24 · 32 · 40 · 48 · 64px
- **Radius:** pill 999px
- **Fonte das iniciais (peso 700):** 10/12/14/16/22px respectivamente
- **Fundo default:** `--brand-blue`, iniciais brancas
- **Variantes de cor:** opcional, a critério (green para "você no menu", neutro escuro para outros). Sempre da paleta oficial. Nunca cor fora.
- **Foto sempre que disponível.** Iniciais só fallback.
- **Status dot:** posição bottom-right, escala com avatar (6/8/10/12/16px), border branco 1.5-2px
- **Cores de status:** online `--success`, offline `--neutral-light`, ocupado `--danger`

### 11.6 Tooltip
- **Fundo:** `--brand-navy-deep` ou `--brand-blue`
- **Texto:** branco
- **Padding:** 8px 12px
- **Radius:** 8px (`--radius-sm`)
- **Tipografia:** Body sm (14px) peso 400 ou 500
- **Sombra:** `--shadow-2`
- **Seta:** 5px, mesma cor do fundo
- **Posições:** top, right, bottom, left
- **Delay:** 200ms entrada, 0ms saída
- **Microcopy:** curto e funcional, sem ponto final ("Copiar CNPJ", "Exportar PDF")

### 11.7 Card
- **Radius:** 16px (`--radius-md`)
- **Padding:** 24px (`--space-6`)
- **Border:** 1px `--neutral-light` ou sem border (usar sombra)
- **Sombra:** `--shadow-1` repouso, `--shadow-2` hover
- **Fundo:** branco
- **Tipos:** KPI (eyebrow + display/h1 + suporte + badge) · Documento (título + meta + badge)

### 11.8 Tabs
- **Variantes:** underline (navegação interna de página) · pill/segmented (alternar visualização)
- **Underline:**
  - Item ativo: texto `--brand-blue` peso 600, sublinhado 2px `--brand-blue`
  - Item inativo: texto `--neutral` peso 400
  - Counter integrado (ex: `Notas fiscais 348`) em cinza
- **Pill/segmented:**
  - Container fundo `--neutral-surface`, radius 8px, padding 4px
  - Item ativo: fundo branco, texto `--brand-blue`, sombra `--shadow-1`
  - Item inativo: transparente, texto `--neutral`

### 11.9 Pagination
- **Botões:** 32×32px ou 36×36px, radius 8px
- **Ativo:** fundo `--brand-blue`, texto branco
- **Inativo:** fundo branco, border 1px `--neutral-light`, texto `--brand-blue`
- **Setas prev/next** isoladas, mesma altura
- **Truncation com `...`** quando > N páginas
- **Info "Mostrando 1-20 de 248":** Body sm, números em bold

### 11.10 Loading states
- **Skeleton:** fundo `--neutral-light`, shimmer com gradient em loop (1400ms ease-in-out)
- **Spinner:** arc parcial em `--brand-blue` rotacionando (linear loop)
- **Tamanhos spinner:** 16 / 24 / 40px
- **Progress determinada:** bar 4px altura, fill `--brand-blue`, fundo `--neutral-light`, radius pill
- **Progress indeterminada:** gradient em loop

### 11.11 Empty state
- **Estrutura:** ícone `icon/xl` 32px em círculo `--info-bg` + título H4 ou H3 + descrição Body sm + CTA opcional
- **Variantes:** first-run (com CTA primary), sem resultados (com link ghost), sem permissão, sem conexão, error
- **Microcopy:** ver seção 12 (Voice)

### 11.12 Alerts & Banners
- **Inline:**
  - Fundo: `-bg` da semântica (`--success-bg`, `--warning-bg`, `--danger-bg`, `--info-bg`)
  - Ícone à esquerda em cor cheia da semântica
  - Título peso 700 + descrição peso 400 em cor escura derivada
  - Close X à direita (todos podem ser dispensáveis)
  - Radius 8px, padding 12px 16px
- **Banner global:** largura total, fundo `--brand-navy-deep`, ícone + texto + 2 CTAs à direita
- **Toast:**
  - Fundo `--brand-navy-deep`, texto branco
  - Dot colorido da semântica + texto único
  - Tempo: 5s simples, 8s com ação, pausa ao hover, X sempre
  - 4 variantes: success, warning, danger, info

### 11.13 Data Table
- **Densidades:**
  - Compact: row 40px, padding horizontal 16px
  - Default: row 52px, padding horizontal 20px
  - Comfortable: row 64px, padding horizontal 24px
- **Header:** Eyebrow, alinhamento por tipo (texto esquerda, número direita, status centro)
- **Body:** Body sm (14px), border-bottom 1px `--neutral-light`
- **Estados row:** default, hover (fundo `--menu-hover-on-light`), selected (fundo `--info-bg`), selected + hover
- **Tipos de célula:** texto, número/currency (R$ tabular-nums), data BR, status badge, avatar+nome, action kebab, link clicável (texto `--brand-blue`), checkbox seleção (radius 4px exceção)
- **Sort:** seta cima/baixo ao lado do header, ativa em `--brand-blue`
- **Estados especiais:** empty, loading (skeleton rows), error

### 11.14 Modal & Drawer
- **Modal sizes:** sm 400 · md 560 · lg 720 · xl 920
- **Estrutura:** header (título H3 + close X) + body + footer (ações à direita, secondary + primary)
- **Backdrop:** `--backdrop-modal` (navy 45%)
- **Sombra:** `--shadow-3`
- **Radius:** 16px (`--radius-md`)
- **Padding interno:** 24px (`--space-6`)
- **Confirm dialog:** 400px fixo, ícone xl semântico no topo, footer com `[Cancelar secondary] [Verbo concreto destructive]`. **Nunca "Sim/OK" em ação destrutiva.**
- **Drawer:** sm 360 · md 480 · lg 640. Right (padrão) ou Left. Full-height. Radius só nos cantos internos.
- **Sheet (mobile):** sobe pela base, radius 16 nos cantos superiores, handle bar 40×5px `--neutral-light` no topo, max-h 80vh.
- **Comportamentos:** Escape fecha · backdrop click fecha (configurável) · focus trap interno · foco volta ao elemento que abriu.

### 11.15 Page Header
- **Estrutura vertical:** breadcrumb → título H1 → descrição Body sm → ações à direita
- **Padding vertical:** 32px top/bottom (`--space-7`)
- **Gap breadcrumb → título:** 8px (`--space-2`)
- **Gap título → descrição:** 4px (`--space-1`)
- **Gap header → conteúdo:** 32px
- **Variantes:** simples (só título) · com descrição · com ações · com tabs (underline abaixo) · com avatar/logo (ícone xl antes do título)
- **Responsivo:** desktop lado a lado, tablet descrição abaixo, mobile empilhado com kebab
- **Breadcrumb:** separator `/` em `--neutral-light`, último item `--brand-blue` peso 600, anteriores `--neutral-strong` peso 400, Body sm

### 11.16 Search Input
- **Altura:** 44px
- **Radius:** 8px
- **Ícone leading:** lupa `icon/md` em `--neutral-strong`
- **Placeholder:** "Buscar..." ou contextual ("Buscar CNPJ, nota fiscal, certificado...")
- **Trailing:** X (limpar) quando há texto, spinner em loading
- **Variantes:** inline (sempre expandida) · minimal (só ícone, expande ao clicar — topbar) · command ⌘K (modal global)
- **Estados:** default, hover/foco, filled, loading, disabled, error
- **Dropdown de resultados:**
  - Largura igual ao input
  - Agrupamento por categoria (EMPRESAS, DOCUMENTOS) em eyebrow
  - Cada resultado: ícone leading + título Body bold (termo buscado em **bold**) + descrição Body sm `--neutral`
  - Sombra `--shadow-2`, radius 8px
  - Atalhos teclado: ↑↓ navegar, ↵ selecionar, esc fechar
- **Empty:** "Nenhum resultado para '{termo}' · Tente buscar por CNPJ completo, razão social ou número da nota."

### 11.17 Navigation organisms

**Sidebar:**
- Larguras: expandida 240px · colapsada 64px · mobile drawer overlay
- Fundo `--brand-navy-deep`
- Logo no topo, seções com eyebrow (`OPERAÇÃO`, `PRODUTOS`, `CONTA`)
- Item: ícone `icon/lg` 24px + label, counter à direita
- Ativo: faixa `--brand-green` 3px à esquerda, fundo mais claro
- Hover sobre fundo escuro: `--menu-hover-on-dark`

**Topbar:**
- Altura 64px
- Search inline + spacer + sino notificação (badge `--danger`) + help + avatar
- Borda inferior 1px `--neutral-light`

**Notification dropdown:**
- Largura 360px
- Header: "Notificações · X não lidas" + "Marcar todas como lidas"
- Cada item: ícone semântico + título Body bold + descrição Body sm + timestamp Caption UPPER
- Não lidas: fundo `--info-bg`
- Footer: "Ver todas as notificações" centralizado
- Sombra `--shadow-2`, radius 8px

**Avatar dropdown:**
- Largura 280px
- Header: avatar md + nome Body bold + email Body sm `--neutral`
- Itens: ícone + label (Perfil, Configurações, Ajuda)
- Separator + Sair em `--neutral-strong` (não em danger)
- Sombra `--shadow-2`, radius 8px

### 11.18 Date picker
- **Input:** igual Form field, ícone calendar trailing, formato BR `DD/MM/AAAA`, máscara automática (`150520` → `15/05/20__`)
- **Calendar popover:**
  - Largura 320px
  - Header: `< Maio 2026 ▼ >` (seta abre seletor de mês/ano)
  - Grid 7×6 (D S T Q Q S S)
  - Cell 40×40px
  - Hoje: border 1px `--brand-blue`
  - Selecionado: fundo `--brand-blue`, texto branco peso 600
  - Adjacente: cor `--neutral-light`
- **Date range:** 2 inputs lado a lado com seta entre, calendar único, range entre datas em `--info-bg`, endpoints em `--brand-blue` cheio
- **Presets opcionais** (só em range, à esquerda do calendário): Hoje, Ontem, Últimos 7 dias, Este mês, Mês passado, Este trimestre

### 11.19 File upload
- **Dropzone:**
  - Border 1.5px tracejado `--neutral-light`, radius 16px (`--radius-md`), padding 32px vertical 24px horizontal
  - Conteúdo centralizado: ícone xl em círculo `--info-bg` + título peso 700 + descrição secondary
  - Estados: default, drag-over (border `--brand-blue` + fundo `--info-bg`), disabled
- **Upload progress (lista):**
  - Cada arquivo: ícone tipo + nome + tamanho Caption + progress 4px `--brand-blue` + X cancelar
  - Success: check `--success` no lugar do X
  - Error: progress `--danger` + texto "Falha · tentar novamente" + ícone retry
- **Validação:** alerts inline danger ("Tipo não suportado. Aceitos: PDF, XML, JPG." / "Excede 10MB.")
- **Variantes:** single (avatar, certificado A1) · multiple (NFes lote) · compacta inline (linha única para forms)

---

## 12. VOICE & MICROCOPY

### Tom geral
- **Idioma:** português do Brasil. Termos contábeis em PT-BR (CNPJ, NFe, DAS, DCTF, SPED).
- **Pessoa:** "você". Imperativo direto em CTAs ("Iniciar", "Entrar", "Exportar"). Primeira plural em comunicação institucional ("nossa equipe").
- **Tom:** sério-consultivo, humano. Confiança > simpatia. Clareza > criatividade.
- **Sem gírias, sem exclamações, sem emoji.**

### Caixa
- **Sentence case:** botões e labels (`E-mail`, `Empresa`, `Razão social`)
- **UPPERCASE:** eyebrows e labels de tabela (`DOCUMENTO`, `EMPRESA`, `STATUS`, `RECUPERAÇÃO TRIBUTÁRIA`)
- **lowercase intencional:** `patrimonium®`, `patrimonium news`, `radar`
- **Title Case parcial:** títulos de seção ("Atoms - Botões")

### Formato numérico
- **Moeda BR:** `R$ 12.480,00` (sempre com espaço entre R$ e número, ponto separador de milhar, vírgula decimal)
- **Data BR:** `28/04/2027`
- **CNPJ:** `00.000.000/0000-00`
- **CPF:** `000.000.000-00`
- **Variação:** `+18% vs Q3` (sinal explícito)
- **Datas em UI evitar** formato "abril/27" (exceto em estatísticas resumidas)

### Mensagens de erro canônicas
- CNPJ malformado: "CNPJ inválido. Verifique os dígitos."
- E-mail malformado: "E-mail em formato inválido."
- Senha errada: "Senha incorreta."
- Senha curta: "Mínimo 8 caracteres."
- Campo vazio obrigatório: "Este campo é obrigatório."
- Conexão: "Não foi possível conectar. Tente novamente."
- Timeout: "Tempo esgotado. Recarregue a página."

### Empty states canônicos
- Sem documentos (first-run): "Você ainda não tem documentos" / "Importe seu primeiro CNPJ ou cole uma NFe para começar a acompanhar obrigações fiscais."
- Sem resultados de busca: "Sem resultados para '{termo}'" / "Tente buscar por CNPJ completo, razão social ou número da nota fiscal."
- Sem permissão: "Acesso restrito" / "Solicite ao administrador da conta para liberar essa área."
- Sem conexão: "Sem internet" / "Reconectaremos automaticamente quando a conexão voltar."

### Botões canônicos
- **Confirmação:** "Salvar" (nunca "Submeter", "OK", "Aplicar")
- **Cancelar:** "Cancelar" (nunca "Voltar", "Fechar")
- **Continuar:** "Continuar" (multi-step)
- **Destrutivo:** verbo da ação ("Excluir nota fiscal", "Remover", "Cancelar assinatura") — nunca "Sim" ou "OK"

### Tom em situações específicas
- **Sucesso de recuperação** (celebrativo mas técnico): "Recuperação aprovada · R$ 12.480,00 foi creditado ao seu CNPJ"
- **Erro do sistema** (responsabilização, nós não o usuário): "Não conseguimos validar este CNPJ"
- **Aviso de vencimento** (prático, com solução): "DAS vence em 3 dias · Agende o pagamento até 12/11"
- **Confirmação destrutiva** (direto, sem ameaça): "Excluir este registro? Esta ação não pode ser desfeita."

### Status (adjetivos curtos)
- `Ativo` · `Em análise` · `Vencido` · `Vence em 7 dias` · `Arquivado` · `Rejeitado` · `Agendado` · `Pendente`
- Sem ponto final em badges, labels e status.

### Glossário
- **Patrimonium** — sempre com inicial maiúscula
- **NFe** — sempre assim (não "NF-e", "NFE" ou "Nota Fiscal Eletrônica")
- **CNPJ** — sempre CAIXA ALTA
- **CPF** — sempre CAIXA ALTA
- **Sub-marcas:** Central de Inteligência Tributária, Arquivo Digital, BPO Financeiro, Recuperação Tributária, patrimonium news, radar, Academy, Certificado Digital

---

## 13. BRANDED HOUSE

- Marca-mãe: `patrimonium®` (lowercase intencional, símbolo registrado)
- 8 sub-marcas, cada uma com produto/serviço próprio mas **mesmo chassi visual**
- Cada sub-marca tem logo própria (símbolo P-cápsula + nome)
- **Sub-marca NÃO inventa:** cor própria, tipografia própria, paleta secundária, variação de voz
- **Sub-marca diferencia por:** nome, escopo funcional, ícone da logo
- Selo P-cápsula é âncora visual: aparece em todas as composições

---

## 14. ACESSIBILIDADE

### Contraste (WCAG)
- Texto sobre branco: usar `--neutral-strong` (`#3D3D3D`) para body, `--brand-blue` (`#1A3375`) para headings — ambos AAA. (Mudança v1.0.1: headings deixaram de usar `--brand-navy-deep`; ver hierarquia de uso da paleta na seção 2.)
- Texto sobre `--brand-blue`: branco `#FFFFFF` — AAA
- Texto sobre `--brand-navy-deep` (dark mode, hero, banner): branco `#FFFFFF` — AAA
- Texto sobre `--brand-green`: `--brand-navy-deep` `#0B1B3F` — passa AA (verde claro requer texto escuro)
- Verde NUNCA como cor de texto sobre branco (falha AA)
- Texto branco sobre qualquer `{semantic}-bg-dark`: passa AA ou AAA conforme o par
- Cores `{semantic}-dark` sobre `{semantic}-bg-dark` correspondente: ≥ 3.0 (WCAG 1.4.11 não-texto, mínimo para bordas e ícones)

### Hierarquia de heading
- Um único H1 por tela (inviolável)
- H2-H4 podem se repetir
- Não pular níveis (sem H3 sem H2 antes)

### Focus order
- Tab segue ordem visual lógica (topo → baixo, esquerda → direita)
- Modais aprisionam focus (Tab não sai)
- Ao fechar modal, focus volta ao elemento que abriu

### ARIA
- Ícones isolados (sem texto) precisam de `aria-label`
- Botões icon-only com label descritivo ("Excluir registro", não "Botão")
- Inputs precisam de `<label>` associado — placeholder não substitui label

### Hit area mínima
- 44×44px em qualquer interativo (regra do sistema, ver seção 9)

### Toast timing
- 5s simples · 8s com ação · pausa ao hover · X sempre presente

### Movimento
- Respeitar `prefers-reduced-motion` (reduzir drasticamente ou desativar)
- Sem animação em loop infinito automática (exceto loaders enquanto há "carregando")
- Sem flash > 3× por segundo (epilepsia fotossensível)

---

## 15. REGRAS TRANSVERSAIS (sempre aplicáveis)

1. **Hover = Focus visualmente** em todo o sistema
2. **Sem subtons na paleta** (sem 100/300/500/700/900)
3. **Sem opacidade em texto/ícones** para atenuar — usar token de cor correto
4. **Naming técnico em EN** (`--brand-blue`, `--space-4`), microcopy em PT-BR
5. **Hit area mínima 44×44** em interativos
6. **Sem emoji** em produto e institucional
7. **Sem cor fora da paleta oficial**, mesmo "que pareça da marca"
8. **R$, CNPJ, NFe, datas** sempre nos formatos canônicos da seção 12
9. **Componente existe? Reusar.** Não desenhar paralelo.
10. **Valor fora da escala (radius, spacing, fonte)?** Corrigir pro vizinho mais próximo da escala.

---

## 16. CHECKLIST PARA GERAÇÃO DE CÓDIGO

Antes de finalizar a UI gerada, verificar:

- [ ] Todas as cores são tokens (não há HEX literal fora dos tokens da seção 2)
- [ ] Todos os spacings são da escala (4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80)
- [ ] Todos os radius são da escala (4 exceção, 8, 16, 32, 999)
- [ ] Todas as fontes são RNS Sanz com pesos da escala (300-900)
- [ ] Tamanhos tipográficos só dos 10 oficiais
- [ ] Ícones Lucide stroke 1.5px com currentColor
- [ ] Microcopy em PT-BR canônico (CNPJ, NFe, R$, datas)
- [ ] Hover e focus produzem mesma mudança visual
- [ ] Hit areas ≥ 44×44 em interativos
- [ ] H1 único por tela
- [ ] Sem emoji
- [ ] Sem opacity em texto/ícone para atenuar
- [ ] Sem cor fora da paleta
- [ ] Botão destrutivo usa verbo concreto, nunca "Sim/OK"

---

## 17. EXEMPLO DE PROMPT EFETIVO

Quando for usar este DS com uma IA geradora, o prompt deve ser direto. Exemplo:

```
Vou construir [DESCRIÇÃO DA TELA].

Use exclusivamente o Patrimonium Design System (anexo acima).
Não invente cores, tokens ou regras fora do sistema.
Aplique microcopy canônico em PT-BR.
Reuse componentes existentes (Button, Form fields, Data Table, etc.).

Específico desta tela:
- [detalhes funcionais]
- [comportamento esperado]

Entregue:
- HTML semântico
- CSS importando colors_and_type.css
- JavaScript se necessário
```

A IA deve produzir código respeitando 100% deste contexto. Se em algum momento decidir por algo fora do sistema, é falha de aplicação — não falha do sistema.

---

*Fim das regras técnicas da v1.0.1.*

---

## 15. Camadas de superfície (v2.0)

O sistema Patrimonium codifica três camadas de profundidade explícitas, tanto em light quanto em dark mode. Esse é o tratamento de profundidade oficial — usar essas camadas em vez de improvisar com shadows aleatórias ou opacity.

### Light mode

- **Page (camada 0):** `--neutral-surface` `#F7F8FB`. Fundo da página/app shell.
- **Card (camada 1):** `--brand-white` `#FFFFFF` + `--shadow-1` + sem border (ou border `0.5px solid rgba(15, 23, 42, 0.04)` se contraste estiver fraco).
- **Elevated (camada 2):** `--brand-white` `#FFFFFF` + `--shadow-3`. Modal, drawer, sheet, popover destacado.

### Dark mode

- **Shell (camada 0):** `--brand-navy-deep` `#0B1B3F`. Fundo da aplicação.
- **Painel (camada 1):** `--brand-blue` `#1A3375` + `--shadow-1` (sutil em dark, mas presente). Cards, banners, painéis principais.
- **Elevated (camada 2):** `--brand-blue` `#1A3375` + border `0.5px solid rgba(255, 255, 255, 0.08)` + `--shadow-3`. Modal, drawer, sheet, popover destacado.

### Regras transversais

- **Não pule camadas.** Card direto em shell (sem camada intermediária) é o padrão. Não há "camada 0.5" ou "camada 1.5".
- **Não use opacity para criar camada.** Usar opacity (`rgba` com alpha) é reservado para overlay/backdrop e para Glassmorphism (seção 17). Para profundidade, usar a combinação cor + shadow + border definida acima.
- **Não inverta a hierarquia.** Em dark mode, painel é mais claro que shell. Em light, card é mais claro que page (branco vs cinza claro). Inverter destrói a sensação de profundidade.
- **Em dúvida, fica na camada 1.** Quase tudo no produto é card sobre page. Modal/drawer/popover são exceções.

---

## 16. Gradients oficiais (v2.0.1)

Cinco gradients são canônicos no sistema. Todos lineares, ângulo `135deg`, stops `0%` e `100%` sem stop intermediário. Apenas cores da paleta oficial. Qualquer outro gradient está fora do DS.

A v2.0.1 ajustou o catálogo da v2.0.0 com duas mudanças importantes:
- **Adicionou 2 gradients light-mode-first** (`gradient-soft-hero` e `gradient-accent-soft`) porque a v2.0.0 ficou enviesada pra dark mode, e produto Patrimonium é majoritariamente light.
- **Afrouxou a restrição de frequência do `gradient-brand-accent`** — a regra de "uma única ocorrência por tela" da v2.0.0 estava tornando a aplicação parcial e incompleta. Agora pode aparecer múltiplas vezes na mesma tela em KPIs grandes, ícones de hero, círculos de destaque.

### 16.1 Hero gradient (dark)

```css
background: linear-gradient(135deg, #0B1B3F 0%, #1A3375 100%);
```

**Quando usar:** hero institucional dark, capa de relatório/PDF, login screen, background de página de marketing/institucional dark.

**Não usar em:** produto operacional em light mode, cards, botões. Para hero de página em light mode, usar `gradient-soft-hero` (16.2).

### 16.2 Soft hero (light) — **novo na v2.0.1**

```css
background: linear-gradient(135deg, #F7F8FB 0%, #E0E7FF 100%);
```

**Quando usar:**
- Banner institucional de topo de página em light mode (cabeçalho de Dashboard, Hub, página inicial logada)
- Hero de página de produto em light
- Faixa decorativa em landing light mode
- Background de seção destacada em formulário longo

É o "ar Patrimonium" sem ser dark. Sutil, identitário, light-mode-first.

**Não usar em:** cards de produto operacional, KPI cards individuais. É pra **container largo** (banner, faixa), não pra card.

### 16.3 Brand accent

```css
background: linear-gradient(135deg, #1A3375 0%, #00FCA8 100%);
```

**Quando usar:**
- Número grande de KPI institucional ou principal — aplicado via `background-clip: text` / `-webkit-background-clip: text` + `color: transparent`
- Fundo de KPI card de destaque (o KPI principal da tela, não todos)
- Ícone de hero — gradient como fundo do círculo/quadrado contendo o ícone (ícone em branco em cima)
- Key visual em campanha (capa de PDF institucional, banner de evento)
- Linha de assinatura — faixa de 3-4px sob título de seção destaque
- CTA destaque em hero (botão ou pill grande de chamada principal)

**Restrição prescritiva (apenas uma, técnica):**
- **Tamanho:** elementos entre **48px e 96px** para gradient em forma circular/ícone. Para `background-clip: text` em números grandes, mínimo de **40px de altura tipográfica**. Para fundo de KPI card, mínimo de **120px de largura**.

**Removido na v2.0.1:** a restrição de "uma única ocorrência por tela" da v2.0.0. Pode aparecer múltiplas vezes desde que cada aplicação seja em elemento de destaque, não em todo card uniforme.

**Não usar em:** botões secundários, ícones de UI (sidebar, topbar, navigation), bordas, avatares, charts (use Data accent), texto corrido, escala <32px, fundo de página inteira.

### 16.4 Accent soft (light) — **novo na v2.0.1**

```css
background: linear-gradient(135deg, #E0E7FF 0%, #E6F7EF 100%);
```

**Quando usar:**
- Fundo de card destacado em light (card de feature nova, banner de upgrade, callout de oportunidade)
- Card de KPI principal em light que precisa destacar mas sem o peso visual do `gradient-brand-accent`
- Background de banner "Novo recurso", "Beta", "Em breve"
- Cabeçalho de seção destacada dentro de painel

Sutil, identitário, light-mode-first. É o equivalente "diet" do `gradient-brand-accent`.

**Não usar em:** dark mode, hero institucional principal (use `gradient-soft-hero` ou `gradient-hero`), texto.

### 16.5 Data accent

```css
background: linear-gradient(135deg, #1A3375 0%, #0C998F 100%);
```

**Quando usar:**
- Barras de gráfico (vertical, horizontal, stacked)
- Área preenchida em gráfico de área/linha
- Ícone de categoria temática (quando precisa diferenciar de outras categorias visualmente)
- Painel onde o `--brand-green` seria demais (excesso de identidade pra contexto técnico)

**Não usar em:** botões, headings, fundo de página, status semântico (use as cores `state.*`).

### 16.6 Gradients fora do catálogo (proibidos)

- **Surface gradient** (navy-deep → navy ligeiramente mais claro): rejeitado na v2.0.0. Para profundidade no dark, usar as camadas de superfície (seção 15).
- **Blue + cyan**: combinação Patrimonium usa em peças de marketing, mas sem caso de uso prescritível para IA. Ativo de marketing humano, nunca em produto gerado.
- **Mesh gradient / Radial gradient**: ficam fora do catálogo por durabilidade questionável e sensibilidade a escala.
- **Qualquer gradient para → branco**: rouba "ar", lava a composição.
- **Qualquer gradient envolvendo semantic (success/warning/danger/info/neutral/pending)**: confunde estado com decoração.
- **Gradient em texto que não seja KPI principal grande**: fere legibilidade.

---

## 17. Glassmorphism (v2.0.1)

Glass é elemento de identidade visual da v2.0. A v2.0.0 prescrevia escopo muito restrito (3 cenários), resultando em produto sem glass aparente — perdia identidade. A v2.0.1 afrouxa o escopo e codifica a regra real de aplicação: **densidade de texto**.

### 17.1 Regra-mãe — densidade de texto

**Container que carrega estrutura visual → glass.**
**Container denso em informação textual → sem glass.**

A transparência do glass funciona quando o conteúdo do container respira (poucos elementos, hierarquia clara, espaço entre eles). Quando o conteúdo é denso (muitas linhas de texto, tabela de dados, parágrafos), a transparência prejudica leitura — usar superfície sólida das camadas (seção 15).

### 17.2 Onde usar glass

**Sim:**
- **Sidebar de navegação** — apesar de listar nomes de itens, é estrutural (navegação), não denso em texto
- **Banner institucional** (header de página, faixa de "Visão geral", banner de feature)
- **KPI cards com número grande + label + variação** (poucos elementos)
- **Card destaque com gradient ou número grande** (Recuperação Tributária, total recuperado, etc.)
- **Painel com chart** (o container, não o tooltip)
- **Modal ou drawer sobre conteúdo do produto**
- **Header sticky** em qualquer modo quando flutua sobre conteúdo
- **Card de hub central** (cards de sub-marca em página de hub)
- **Container de tabela** (o frame em volta, não as linhas)

### 17.3 Onde NÃO usar glass

- **Conteúdo de tabela** (linhas, cabeçalho, células) — texto sobre texto translúcido vira ilegível
- **Cards de detalhe denso** (card com 3+ parágrafos, card com lista longa)
- **Botões, inputs, search bar, dropdown** — controles são interativos, glass confunde affordance
- **Atomic:** badge, tag, chip, avatar, dot — elementos pequenos não comportam blur
- **Tooltip** — continua usando `--brand-navy-deep` sólido (visibilidade crítica)
- **Empty state** — texto principal, leitura prioritária
- **Elementos <120px de largura ou altura** — glass exige superfície ampla pra ler
- **Toast/notification** — sai por cima de qualquer fundo, precisa de superfície sólida

### 17.4 Fórmula dark (`patrimonium-glass-dark`)

Para uso sobre fundos escuros — produto em dark mode, banner com gradient escuro, hero institucional.

```css
.patrimonium-glass-dark {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  background: rgba(11, 27, 63, 0.72);
  border: 0.5px solid rgba(255, 255, 255, 0.10);
  box-shadow: 0 4px 8px rgba(15, 23, 42, 0.08), 0 16px 40px rgba(15, 23, 42, 0.12);
}

@supports not ((backdrop-filter: blur(1px)) or (-webkit-backdrop-filter: blur(1px))) {
  .patrimonium-glass-dark {
    background: #1A3375;
    border: 0.5px solid #3059AF;
  }
}
```

### 17.5 Fórmula light (`patrimonium-glass-light`) — **novo na v2.0.1**

Para uso sobre fundos claros — produto em light mode (cenário majoritário do Patrimonium).

```css
.patrimonium-glass-light {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  background: rgba(255, 255, 255, 0.68);
  border: 0.5px solid rgba(15, 23, 42, 0.06);
  box-shadow: 0 4px 8px rgba(15, 23, 42, 0.04), 0 16px 40px rgba(15, 23, 42, 0.06);
}

@supports not ((backdrop-filter: blur(1px)) or (-webkit-backdrop-filter: blur(1px))) {
  .patrimonium-glass-light {
    background: #FFFFFF;
    border: 0.5px solid rgba(15, 23, 42, 0.08);
  }
}
```

### 17.6 Como escolher entre as duas fórmulas

- Container está sobre fundo claro (page em light, dentro de painel branco) → `patrimonium-glass-light`
- Container está sobre fundo escuro (shell em dark, banner com hero gradient, hero dark) → `patrimonium-glass-dark`
- Em dúvida pelo contexto, escolher pelo modo da aplicação (`prefers-color-scheme` ou tema selecionado): light → light, dark → dark

### 17.7 Fallback obrigatório

Os blocos `@supports not` em ambas as fórmulas são obrigatórios. Devices fracos ou navegadores antigos caem para superfície sólida correspondente. Sem fallback, produtos podem renderizar fundo transparente literal (invisível) em alguns browsers.

---

## 18. Lockups de sub-marca (v2.0)

A Patrimonium opera como **Branded House** (princípio 7). A marca-mãe `patrimonium®` sustenta 8 sub-marcas, cada uma com seu lockup oficial — a composição "ícone identitário + nome da sub-marca + 'patrimonium'". O lockup é o ativo de marca da sub-marca, equivalente ao que o logo principal é para a marca-mãe.

### 18.1 Lockups disponíveis (8 sub-marcas × 2 versões)

Cada sub-marca tem versão **positiva** (para fundos claros) e **negativa** (para fundos escuros).

| Sub-marca | URL positiva (fundos claros) | URL negativa (fundos escuros) |
|---|---|---|
| Central de Inteligência Tributária | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-central-inteligencia-tributaria.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-central-inteligencia-tributaria-negativo.png` |
| Arquivo Digital | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-arquivo-digital.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-arquivo-digital-negativo.png` |
| BPO Financeiro | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-bpo-financeiro.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-bpo-financeiro-negativo.png` |
| Recuperação Tributária | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-recuperacao-tributaria.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-recuperacao-tributaria-negativo.png` |
| patrimonium news | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-patrimonium-news.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-patrimonium-news-negativo.png` |
| radar | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-radar.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-radar-negativo.png` |
| Academy | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-academy.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-academy-negativo.png` |
| Certificado Digital | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-certificado-digital.png` | `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/lockups/lockup-certificado-digital-negativo.png` |

### 18.2 Capitalização oficial (cravada na v2.0)

A capitalização do nome de cada sub-marca segue exatamente o lockup. Resolve a pendência de marketing registrada na v1.0:

- **Title Case:** Central de Inteligência Tributária · Arquivo Digital · BPO Financeiro · Recuperação Tributária · Academy · Certificado Digital
- **Minúsculo:** patrimonium news · radar
- A marca-mãe sempre minúscula em copy técnico: `patrimonium®`

### 18.3 Quando usar lockup

- **Cabeçalho de página dedicada à sub-marca** — quando o produto atual é da sub-marca, o lockup aparece no topo da página/seção principal
- **Capa de PDF emitido pela sub-marca** — relatório de Recuperação Tributária usa o lockup `lockup-recuperacao-tributaria` na capa
- **Splash screen de produto da sub-marca** — login específico, splash de carregamento
- **Card destaque em hub central** — quando o produto principal lista todas as sub-marcas disponíveis, cada card mostra o lockup
- **Banner institucional da sub-marca** — comunicação direta sobre aquele produto

### 18.4 Quando NÃO usar lockup

- **Sidebar de navegação do produto** — sidebar lista produtos pelo nome textual, não pelo lockup completo (lockup é grande demais)
- **Ícone pequeno (<48px)** — lockup tem texto, não lê bem em escala pequena. Para ícone pequeno, ver seção 18.6
- **Substituindo o logo principal Patrimonium** — quando a tela é da marca-mãe (home logada, dashboard geral, configurações de conta), usar `logo-principal.png`, não lockup de sub-marca
- **Decoração** — lockup é marca, não enfeite. Não usar como background, padrão repetido, ou elemento ambiental

### 18.5 Regras de aplicação técnica

- Sempre aplicar como `<img src="..." alt="Patrimonium [Nome da sub-marca]">`. Não reconstruir em CSS/SVG.
- **Versão positiva** sobre fundos claros (`#FFFFFF`, `#F7F8FB`, etc.)
- **Versão negativa** sobre fundos escuros (`#0B1B3F`, `#1A3375`, `--brand-navy-deep` em geral)
- Largura mínima recomendada: 240px (preserva legibilidade do nome da sub-marca)
- Largura máxima recomendada: 480px (acima disso fica institucional demais)
- Não distorcer aspect ratio. Não cortar.
- Não aplicar `filter`, `mix-blend-mode`, opacity reduzida ou qualquer outro tratamento que altere a cor original do lockup.

### 18.6 Ícones individuais (pendência v2.1)

Os lockups são "ícone + texto" compostos. Em casos de uso onde o produto precisa apenas do **elemento gráfico identitário** da sub-marca (sidebar de navegação, dashboard hub compacto, breadcrumb), o ideal é ter o ícone extraído individualmente em 24/32/48px. Esse trabalho está registrado como pendência para v2.1 (requer designer para corte e padronização). **Até lá**, em situações que pedem ícone pequeno da sub-marca, usar ícones Lucide com nome aproximado:

- Central de Inteligência Tributária → `brain`
- Arquivo Digital → `folder-archive`
- BPO Financeiro → `hand-coins` ou `trending-up`
- Recuperação Tributária → `dollar-sign` ou `refresh-ccw`
- patrimonium news → `newspaper`
- radar → `radar`
- Academy → `book-open`
- Certificado Digital → `fingerprint` ou `shield-check`

---

*Fim do documento · Patrimonium Design System AI Context · v2.0.1 · maio 2026.*
