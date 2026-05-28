# Changelog · Patrimonium Design System

Formato: [keep a changelog](https://keepachangelog.com/pt-BR/1.1.0/) · versão SemVer.

---

## v2.0.1 — 25 de maio de 2026

Patch corretivo da v2.0.0. A v2.0 mostrou dois problemas em uso real: bias dark-mode (gradients e glass com tinta navy criavam contraste agressivo sobre produto majoritariamente light) e restrições restritivas demais (a regra "uma ocorrência por tela" do brand-accent e os 3 cenários de glass faziam aplicação parcial).

### Added

**2 gradients novos light-mode-first:**

| Token | Valor | Uso |
|---|---|---|
| `--gradient-soft-hero` | `linear-gradient(135deg, #F7F8FB 0%, #E0E7FF 100%)` | Banner institucional em light, hero de produto, faixa de landing |
| `--gradient-accent-soft` | `linear-gradient(135deg, #E0E7FF 0%, #E6F7EF 100%)` | Equivalente "diet" do brand-accent: callout, banner "Beta/Novo", card destaque em light |

**Variante light de glass (4 vars):** `--glass-light-blur` (`blur(20px)`), `--glass-light-bg` (`rgba(255,255,255,0.68)`), `--glass-light-border` (`0.5px solid rgba(15,23,42,0.06)`), `--glass-light-shadow`. Fallback `@supports not` cobrindo ambas variantes.

**Regra-mãe explícita do glass: densidade de texto.** Containers estruturais → glass. Containers densos em texto → sólido. Substitui a lista de 3 cenários da v2.0.0.

### Changed

**Glass dark — opacidade ajustada:**
- `--glass-dark-bg` `rgba(11,27,63,0.78)` → `rgba(11,27,63,0.72)` (mais transparência)
- `--glass-dark-border` alpha `0.08` → `0.10` (mais visível)

**Glass dark — renome:** `--glass-blur`, `--glass-bg`, `--glass-border`, `--glass-shadow` da v2.0.0 → `--glass-dark-*` na v2.0.1. Aliases temporários mantidos no `:root` apontando para a variante dark para não quebrar código que importou v2.0.0.

**Glass — escopo expandido.** Agora cobre sidebar de navegação, banner institucional, KPI cards limpos, cards de destaque, painéis com chart, modais, headers sticky, cards de hub. Continua proibido em conteúdo de tabela, cards densos em texto, atomic, tooltip, empty state, elementos <120px.

**`--gradient-brand-accent` — restrição de frequência removida.** A regra "uma ocorrência por tela" da v2.0.0 saiu. Pode aparecer múltiplas vezes em KPIs principais, ícones de hero, círculos de destaque. Restrição técnica de tamanho mantida (ícone 48-96px, texto via background-clip ≥40px, fundo de card ≥120px).

**`--gradient-brand-accent` — uso "fundo de KPI card destaque" agora explícito.**

### Migration notes

- **Retro-compatível com v2.0.0.** Nenhum token removido. Aliases mantidos.
- Quem usa variáveis genéricas `--glass-*` continua funcionando (aliases mapeiam para dark). Refatorar gradualmente para `--glass-dark-*` ou `--glass-light-*` conforme contexto.
- `tokens.json` atualizado para v2.0.1: bloco `glass` reorganizado de `{patrimonium: {...}}` para `{dark: {...}, light: {...}}`. Quem usa Style Dictionary precisa atualizar referências.

### Issues levantados em uso e respostas

| Issue | Resposta |
|---|---|
| "Gradients pareciam dark-only" | Adicionados `soft-hero` e `accent-soft` |
| "Glass nunca aparecia em produto operacional" | Regra reescrita por densidade de texto |
| "KPI cards com brand-accent ficavam isolados" | Restrição de frequência removida |
| "Glass formulado em tinta escura ficava agressivo sobre fundo claro" | Variante `glass-light` |

---

## v2.0.0 — 25 de maio de 2026 · Fundação da identidade visual

Patch retro-compatível que fecha a fase de fundação da identidade visual Patrimonium. v1.0 entregou regras técnicas; v2.0 entrega os ativos que tornam o sistema visualmente reconhecível.

### Added

**3 gradients oficiais** com regras prescritivas de uso, tamanho e frequência:
- `--gradient-hero` (`#0B1B3F → #1A3375`) — hero institucional, banner global
- `--gradient-brand-accent` (`#1A3375 → #00FCA8`) — KPI institucional 48–96px, CTA hero, uma vez por tela
- `--gradient-data-accent` (`#1A3375 → #0C998F`) — chart e data viz

**Glassmorphism com fórmula fixa** (5 variáveis):
- `--glass-blur` `blur(20px)`, `--glass-bg` `rgba(11,27,63,0.78)`, `--glass-border`, `--glass-shadow`
- Fallback obrigatório em `@supports not (backdrop-filter)`: bg sólido `#1A3375`, border `#3059AF`

**Camadas de superfície** (11 variáveis), 3 níveis em cada modo:
- Light: `page → card-bg → elevated-bg` (`F7F8FB → #FFF → #FFF` com `shadow-1 → shadow-3`)
- Dark: `shell → painel-bg → elevated-bg` (`#0B1B3F → #1A3375 → #1A3375` com border sutil)

**16 lockups de sub-marca** catalogados em `/assets/lockups/` e expostos como tokens `asset.lockup.*` em `tokens.json`. URLs GitHub Pages prontas para consumo por IA geradora.

### Resolvido

**Capitalização das 8 sub-marcas** cravada conforme os lockups oficiais (Central de Inteligência Tributária, Arquivo Digital, BPO Financeiro, Recuperação Tributária, patrimonium news, radar, Academy, Certificado Digital). Pendência v1.1 fechada.

### Not in scope

- **Refactor do Dashboard atual** — não faz parte do DS. Quando for refeito, será aplicação prática da v2.0, não mudança no DS.
- **Motif curva P, pattern abstrato, gradient blue+cyan, mesh/radial gradients** — descartados após avaliação. Não candidatos.
- **Ícones individuais das sub-marcas** (extração dos lockups), **tratamento de KPI distintivo**, **padrão de chart próprio**, **loader Patrimonium**, **empty states adicionais** — registrados para v2.1.

### Migration notes

- Nenhuma variável existente foi removida ou alterada — patch é puramente aditivo. Sem breaking.
- Componentes existentes (Card, Modal, Drawer) podem **opcionalmente** migrar para usar `var(--surface-*)` sem mudança visual — apenas alinha nomenclatura entre Figma e código.
- IAs geradoras devem consumir lockups pelas URLs GitHub Pages em `tokens.json`, não reconstruir em CSS/SVG.

---

## v1.0.1 — 25 de maio de 2026

Patch que finaliza a v1.0 com três ajustes identificados em uso real do sistema com IAs geradoras.

### Added

**12 tokens de cor novos para suporte ao dark mode.** Cada cor semântica passa a ter um par `-dark` (cor cheia clareada para borda/ícone/dot) e `-bg-dark` (fundo escuro para alerts e banners no dark mode). Texto sobre `-bg-dark` é sempre branco.

| Par | `-dark` | `-bg-dark` |
|---|---|---|
| success | `#4FCB87` | `#1A6E48` |
| warning | `#FFB84D` | `#8C5A0F` |
| danger  | `#F08080` | `#8B2828` |
| info    | `#95ADE3` | `#2A4FA0` |
| neutral | `#8A95A8` | `#3B4555` |
| pending | `#A99DEC` | `#4A3DA0` |

Todos passam WCAG: texto branco sobre `-bg-dark` ≥ AA em todos os pares (AAA em 4 deles), e `{semantic}-dark` sobre `{semantic}-bg-dark` ≥ 3.0 (mínimo WCAG 1.4.11 para elementos não-texto).

### Changed

**Headings em light mode agora usam `--brand-blue` `#1A3375`** em vez de `--brand-navy-deep` `#0B1B3F`. Navy-deep fica reservado ao seu papel de cor invertida (fundo do dark mode, hero, banner global, fundo de tooltip, texto sobre verde). Contraste sobre branco cai de 16.90 para 11.84 — ambos AAA, sem regressão de acessibilidade.

**Token `--fg-1`** agora referencia `--brand-blue`.

### Out of scope (movido para v2.0)

O Dashboard atual ficou genérico em uso real — diagnóstico de que falta linguagem visual de identidade no DS, não apenas regras de aplicação. Trabalho de identidade visual (motif gráfico, KPI distintivo, padrão de chart próprio, ícones autorais de sub-marca, camadas de superfície) será o tema central da v2.0.

### Pendências para v1.1

- Sobreposição de naming `--brand-neutral-dark` × `--neutral-strong`
- Capitalização das 8 sub-marcas (decisão de marketing)
- Loader com identidade Patrimonium
- Empty states adicionais (sem permissão, sem conexão, error)
- Logos de sub-marca exportadas

### Migration notes

- Quem importa `colors_and_type.css` ganha as 12 variáveis novas automaticamente. Sem breaking nas variáveis existentes.
- Quem usa `--fg-1` em CSS verá heading mudar de cor automaticamente — comportamento esperado.
- Quem referencia `#0B1B3F` literal em código de heading deve trocar para `#1A3375` ou `var(--fg-1)`. Em fundos (sidebar dark, hero, tooltip), `#0B1B3F` continua válido.

---

## v0.2.1 — 18 de maio de 2026 · Auditoria de conformidade

### Consolidados
- **Neutros** — `--neutral-line`, `--neutral-muted` e `--brand-neutral-light` deixam de existir como nomes oficiais e viram aliases para `--neutral-light` (`#C8C8CC`). Tokens canônicos passam a ser **3**: `--neutral-surface`, `--neutral-light`, `--neutral-strong`.
- **Radius** — varredura global. Valores fora da escala (6, 10, 12, 14, 18, 20px) corrigidos para o vizinho na escala oficial (8 / 16 / 32 / pill). Ajustes pontuais aplicados nos frames afetados.
- **Tokens** — substituições aplicadas em 23 arquivos (139 ocorrências de nomes legados → `--neutral-light`).
- **PRINCIPLES.md** — adendo "Opacidade não é foundation" atualizado com `--neutral-light`.
- **README** — referência a `--neutral-300`/`--fg-muted` em estados disabled trocada para `--neutral-light`.
- **Colors · Neutrals card** — regenerado para mostrar os 3 tokens canônicos + nota de deprecation.
- **Buttons · Variants card** — subtítulo corrigido para refletir as 5 variants atuais (primary, secondary, ghost, destructive, affirmative) e 6 estados.

### Mantidos como cravados (não revisados nesta rodada)
- Paleta (3 principais + 6 apoio)
- 10 estilos tipográficos
- Escala de spacing
- Iconografia Lucide stroke 1.5px
- Princípios e governança

---



### Foundations
- **Cores** — 3 principais (Patrimonium Blue `#1A3375`, Patrimonium Green `#00FCA8`, Branco) + 6 de apoio (Navy escuríssimo `#0B1B3F`, Navy médio `#3059AF`, Teal `#0C998F`, Ciano luminoso `#1AFFFF`, Neutro escuro `#3D3D3D`, Neutro claro `#C8C8CC`)
- **Neutros** — 4 tons canônicos: `neutral/surface` `#F7F8FB`, `neutral/line` `#E2E6F1`, `neutral/muted` `#94A3B8`, `neutral/strong` `#3D3D3D`
- **Semânticas** — 6 tokens (success, warning, danger, info, neutral, pending) com pares `*-bg`
- **Acessibilidade** — tabela WCAG validada: 11 pares AAA + 5 pares AA + 4 don'ts FAIL documentados
- **Tipografia** — RNS Sanz, 7 pesos. Display único (56px ExtraBold), h1–h4, body lg/md/sm, eyebrow, caption. Mono ativada com `tabular-nums` em colunas de valor.
- **Spacing** — 11 tokens (4 → 80px), preferenciais marcados
- **Radius** — 4 valores derivados de 15% da menor dimensão do logo (8 / 16 / 32 / 999)
- **Elevation** — 3 níveis, sombras compostas, cor‑base `rgba(15,23,42,X)`, alpha ≤ 0.12
- **Opacidade** — 6 níveis autorizados; nunca em tipografia
- **Grid** — 12 / 8 / 4 colunas em desktop / tablet / mobile, breakpoints `sm 640 · md 768 · lg 1024 · xl 1280 · 2xl 1536`
- **Iconografia** — Lucide, stroke 1.5px uniforme, currentColor

### Atoms
- **Button** — 5 variants (primary, secondary, ghost, destructive, affirmative) × 3 sizes (sm 36, md 44, lg 52) × 6 states. Affirmative usa pill; demais usam radius 8px.
- **Form fields** — input com label uppercase, foco navy, erro inline
- **Form controls** — checkbox, radio, switch · estados default/checked/focus/disabled
- **Badge** — 5 status (success, warning, danger, info, muted) + variantes solid/pill
- **Avatar** — 5 tamanhos · iniciais / ícone / status dot / stack
- **Tooltip** — 4 posições (top/right/bottom/left), fundo navy

### Molecules
- **Card** — KPI + documento
- **Data table** — header eyebrow, badges status, hover, filter chips
- **Tabs** — underline padrão + pill/segmented
- **Pagination** — números + prev/next + info "Mostrando X de Y"
- **Loading states** — skeleton (linha, card, row), spinner sm/md/lg, progress determinada e indeterminada
- **Empty state** — ilustração circular + título + p + CTA
- **Alerts & Banners** — alert inline (4 estados), banner global, toast

### Brand
- **Logos** — principal, azul, negativa (PNG)
- **Símbolo** — P‑cápsula principal, azul, negativo
- **Arquitetura Branded House** — marca‑mãe + 8 sub‑marcas documentadas
- **Voice & microcopy** — tom Patrimonium, ✓/✗

### Templates
- **App interno · Dashboard** — sidebar navy + topbar + KPIs + tabela + radar card + modal + toast

### Governança
- `PRINCIPLES.md` — 7 princípios
- `CONTRIBUTING.md` — processo, critérios, governança
- `ROADMAP.md` — próximas versões
- `SKILL.md` — uso como skill para Claude Code

---

## Próximas versões

Ver `ROADMAP.md`.
