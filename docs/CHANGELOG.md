# Changelog · Patrimonium Design System

Formato: [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/) · versionamento SemVer.

**Major (1.0 → 2.0):** mudança que quebra compatibilidade (ex: renomear todos os tokens).
**Minor (1.0 → 1.1):** novo componente ou nova regra sem quebrar existente.
**Patch (1.0.0 → 1.0.1):** correção de bug ou inconsistência.

---

## v1.0.0 — maio 2026 · Primeira versão pública

Primeira versão pública do Patrimonium Design System.

### Adicionado

**Foundations**
- Cores — 3 principais (Patrimonium Blue `#1A3375`, Patrimonium Green `#00FCA8`, Branco) + 6 de apoio (Navy escuríssimo, Navy médio, Teal, Ciano, Neutro escuro, Neutro claro) + 6 semânticas (success, warning, danger, info, neutral, pending) com pares `-bg`. Sem subtons.
- Neutros canônicos — 3 tokens: `--neutral-surface` `#F7F8FB`, `--neutral-light` `#C8C8CC`, `--neutral-strong` `#3D3D3D`.
- Tipografia — RNS Sanz em 7 pesos, 10 estilos oficiais (Display, H1, H2, H3, H4, Body lg, Body, Body sm, Eyebrow, Caption).
- Spacing — 11 tokens base 4px (`--space-1` a `--space-11`).
- Radius — 4 oficiais (8, 16, 32, 999 pill) + exceção 4px para mini-controles.
- Sombras — 3 níveis, compostas, cor-base `rgba(15, 23, 42, X)`, sem offset horizontal.
- Iconografia — Lucide, stroke 1.5px uniforme, `currentColor`, 4 tamanhos.
- Grid e breakpoints — mobile-first, 5 breakpoints (sm 640, md 768, lg 1024, xl 1280, 2xl 1536), max-width 1280 em 2xl.
- Transparências autorizadas — `backdrop-modal`, `focus-ring`, `menu-hover-on-light`, `menu-hover-on-dark`, `menu-active-on-dark`.
- Motion — 5 durações (instant, fast, base, moderate, slow) + 3 easings (out, std, linear).

**Atoms**
- Button — 5 variants (primary, secondary, ghost, destructive, affirmative) × 3 sizes (sm 36, md 44, lg 52) × 6 estados.
- Form fields — text input com label eyebrow, helper text, estados completos (default, hover/foco, filled, error, disabled).
- Form controls — Checkbox (com radius 4px exceção e estado indeterminado), Radio, Switch. Estados completos incluindo erro e hover/foco unificado.
- Badge & Pills — 6 status com versão solid e light.
- Avatar — 5 tamanhos (24, 32, 40, 48, 64), status dot escalado, stack com contador.
- Tooltip — 4 posições (top, right, bottom, left), fundo navy.

**Components**
- Card — variantes KPI e Documento.
- Tabs — underline (navegação) e pill/segmented (alternar visualização).
- Pagination — números + prev/next + info "Mostrando X de Y".
- Loading states — Skeleton (linha, card, row), Spinner (sm/md/lg), Progress (determinada e indeterminada).
- Empty state — first-run e sem resultados de busca.
- Alerts & Banners — alert inline (4 estados), banner global, toast (4 variantes semânticas).
- Data Table — 3 densidades (compact, default, comfortable), 8 tipos de célula, estados de row (default, hover, selected, selected+hover), estados especiais (empty, loading, error), sort indicators, pagination integrada.

**Componentes especializados**
- Modal & Drawer — Modal (4 sizes: sm 400, md 560, lg 720, xl 920), Confirm dialog (400 fixo, ação destrutiva com verbo concreto), Drawer lateral (3 sizes, right/left), Bottom sheet (mobile com handle bar).
- Page Header — 5 variantes (simples, com descrição, com ações, com tabs, com avatar/logo) + Breadcrumb como sub-componente.
- Search Input — 3 variantes (inline, minimal topbar, command ⌘K) + 6 estados + dropdown de resultados com atalhos de teclado.
- Date picker — single date, date range, calendar popover (320px), 6 presets, máscara automática formato BR.
- File upload — Dropzone (3 estados), lista de upload com progress por arquivo (uploading, success, error), alerts de validação, 3 variantes (single, multiple, compacta).

**Navigation**
- Sidebar — 3 estados (expandida 240, colapsada 64, mobile drawer overlay), seções hierárquicas com eyebrow.
- Topbar — 64px com Search + sino notificação (badge danger) + help + avatar.
- Notification dropdown — 360px, agrupado por status, atalhos.
- Avatar dropdown — 280px com cabeçalho + itens + Sair em neutro.

**Brand**
- Logo — light & dark em PNG (principal, azul, negativa).
- Símbolo P-cápsula — principal, azul, negativo.
- Branded House Arquitetura — marca-mãe + 8 sub-marcas documentadas.
- Voice & Microcopy — tom Patrimonium, exemplos do/don't.

**Templates**
- App Dashboard Light — prova de conceito (sidebar + topbar + KPIs + tabela + radar card).
- App Dashboard Dark — variação invertida sem tokens novos.
- 404 — página não encontrada (CTAs primary + ghost).
- 500 — erro de servidor (alert com código + CTAs primary, secondary, ghost).

**Documentação**
- Motion — durações, easings, princípios escritos, exemplos de uso por componente.
- Voice & Microcopy expandido — 5 camadas (mensagens de erro padrão, empty states canônicos, botões canônicos, glossário Patrimonium, tom por contexto).
- Acessibilidade plena — 6 camadas (hierarquia de heading, focus order, ARIA labels, hit area, toast timing, motion).
- Princípios escritos — 7 princípios em cards visuais.
- Como contribuir — quando propor, quem aprova, processo, princípio orientador.
- Tokens export — formato Style Dictionary, instruções de consumo, regras de sincronização.

### Decisões fechadas

- **Hover = Focus visualmente** em todo o sistema (extensão da regra WCAG: focus precisa ser visível, não diferente de hover).
- **Paleta sem subtons** (100/300/500/700/900).
- **Naming técnico em EN**, microcopy em PT-BR.
- **Pill reservado** a affirmative + primary lg institucional.
- **Radius 4px** como exceção para mini-controles (≤ 20px), não como token nomeado.
- **Opacity removida** como foundation pública; tokens migrados para componentes (`backdrop-modal`, `focus-ring`, `menu-hover-on-light`).
- **Auditoria 0.2.1** — consolidação de `--neutral-line`, `--neutral-muted`, `--brand-neutral-light` em `--neutral-light`; ajustes pontuais de radius fora da escala aplicados nos frames afetados.
- **Fase P enxugada** — templates de DS limitados a Dashboard (Light + Dark), 404 e 500. Templates de produto (Login, Lista com filtros, Detalhe de registro, Form longo, Settings, Empty inicial/Onboarding) ficaram fora do DS por serem arranjos de componentes existentes, território de produto.
- **Empty state inicial / onboarding** considerado decisão de cada produto, não responsabilidade do DS.

### Conhecido · registrado para v1.1

- **Capitalização das 8 sub-marcas** pendente de decisão de marketing (`patrimonium news` vs `Patrimonium News`, `radar` vs `Radar`).
- **Loader com identidade Patrimonium** — substituir spinner genérico por elemento da marca.
- **Empty states adicionais** — sem permissão, sem conexão, error state.
- **Logos das sub-marcas** exportadas como PNG/SVG (hoje só composições no `.fig`).

---

## Próximas versões

Ver `ROADMAP.md` para detalhamento de v1.1, v1.2 e backlog.

---

*Changelog mantido pelo time de Design.*
