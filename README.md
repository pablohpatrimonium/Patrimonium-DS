# Patrimonium · Design System

> Sistema de design oficial da **Patrimonium Contabilidade** — contabilidade consultiva e fintech-tributária no Brasil. Operamos como **Branded House**: a marca-mãe `patrimonium®` sustenta 8 sub-marcas de produto (Central de Inteligência Tributária, Arquivo Digital, BPO Financeiro, Recuperação Tributária, patrimonium news, radar, Academy, Certificado Digital), todas falando a mesma língua visual.

**Versão atual:** v1.0.0 · maio 2026

---

## Como usar este DS

Cada caso de uso tem o documento certo. Escolha pelo seu papel:

### Sou IA geradora de código (Google AI Studio, Cursor, Claude, v0, Lovable)
→ Leia **`AI_CONTEXT.md`** primeiro. Esse documento contém todas as regras técnicas em formato denso, otimizado para você consumir e respeitar.

### Sou desenvolvedor
→ Importe **`tokens/colors_and_type.css`** no projeto (CSS variables prontas). Ou **`tokens/tokens.json`** se usar Style Dictionary / Tokens Studio. Consulte `AI_CONTEXT.md` para regras de aplicação.

### Sou designer
→ Use os componentes do `.fig` no Figma. Para regras escritas, leia `docs/PRINCIPLES.md`, `docs/CHANGELOG.md` e o próprio `AI_CONTEXT.md`.

### Sou novo no time
→ Comece pelo `docs/PRINCIPLES.md` para entender a filosofia. Depois `AI_CONTEXT.md` para mergulhar nas decisões técnicas. `docs/CHANGELOG.md` mostra a história.

### Quero contribuir com o DS
→ Leia `docs/CONTRIBUTING.md`.

---

## Estrutura do repositório

```
patrimonium-design-system/
│
├── README.md                  ← Este arquivo (capa)
├── AI_CONTEXT.md              ← Documento técnico denso (regras completas)
│
├── tokens/
│   ├── colors_and_type.css    ← Tokens em CSS variables
│   └── tokens.json            ← Tokens em formato Style Dictionary
│
├── fonts/                     ← RNS Sanz (7 pesos em .woff)
│
├── assets/
│   └── logos/                 ← Logos PNG da marca
│
├── preview/                   ← HTMLs de referência visual (30 componentes)
│
└── docs/
    ├── PRINCIPLES.md          ← 7 princípios escritos
    ├── CHANGELOG.md           ← Histórico do DS
    ├── CONTRIBUTING.md        ← Como contribuir
    └── ROADMAP.md             ← Próximas versões
```

---

## Resumo rápido do sistema

Apenas para situar. Todo o detalhe técnico está em `AI_CONTEXT.md`.

**Paleta:**
- Patrimonium Blue `#1A3375` (primária)
- Patrimonium Green `#00FCA8` (acento)
- Branco `#FFFFFF` (primária)
- 6 cores de apoio sem subtons
- 6 cores semânticas com pares `-bg`

**Tipografia:** RNS Sanz, 10 estilos (Display 56px, H1–H4, Body lg/md/sm, Eyebrow, Caption).

**Spacing:** base 4px, 11 níveis.

**Radius:** 4 oficiais (4 mini-controle, 8, 16, 32, 999 pill).

**Sombras:** 3 níveis com tinta navy.

**Iconografia:** Lucide, stroke 1.5px uniforme, `currentColor`.

**Grid:** mobile-first, 5 breakpoints (sm/md/lg/xl/2xl).

---

## Componentes prontos (v1.0)

19 componentes oficiais cobrem o produto contábil de ponta a ponta:

**Atoms:** Button (5 variants × 3 sizes), Form fields, Form controls (Checkbox/Radio/Switch), Badge & Pills, Avatar, Tooltip.

**Components:** Card, Tabs, Pagination, Loading states, Empty state, Alerts & Banners, Data Table.

**Componentes especializados:** Modal & Drawer, Page Header, Search Input, Date picker, File upload.

**Navigation:** Sidebar, Topbar, Notification dropdown, Avatar dropdown.

**Brand:** Logo, P-cápsula, Branded House Arquitetura.

**Templates:** App Dashboard (Light + Dark), 404, 500.

---

## Princípios em uma linha

1. **Solidez antes de virtuosismo** — confiança > criatividade.
2. **O miolo é sagrado** — verde do P é identidade central.
3. **Discreet, low-spread** — sombras e efeitos contidos.
4. **Paleta restrita por escolha** — sem subtons.
5. **Saltos grandes, não gradação fina** — escalas com saltos claros.
6. **Affirmative ≠ Save** — botão verde pill é para ganho do cliente.
7. **Branded House, não Casa de Marcas** — sub-marcas dividem o sistema.

Detalhe em `docs/PRINCIPLES.md`.

---

## Tom de voz

- **Idioma:** português do Brasil. Termos contábeis em PT-BR (CNPJ, NFe, DAS, SPED).
- **Pessoa:** "você". Imperativo direto em CTAs ("Iniciar", "Entrar").
- **Tom:** sério-consultivo, humano. Confiança > simpatia, clareza > criatividade.
- **Sem gírias, sem exclamações, sem emoji.**

---

## Hospedagem dos HTMLs de preview

Os arquivos em `preview/` são referências visuais renderizadas. Para vê-los:

- **GitHub Pages** (recomendado): ative em Settings → Pages e os HTMLs ficam acessíveis via `https://[org].github.io/patrimonium-design-system/preview/`. Tudo funciona normalmente.
- **Servidor local:** `python3 -m http.server 8080` na raiz do repo, depois acesse `http://localhost:8080/preview/`.
- **Abrir direto do disco:** o browser bloqueia carregamento de fontes locais por segurança — os HTMLs aparecem sem estilo. Use uma das opções acima.

---

## Pendências registradas para v1.1

- Capitalização das 8 sub-marcas pendente de decisão de marketing (`patrimonium news` vs `Patrimonium News`, `radar` vs `Radar`).
- Loader com identidade Patrimonium — substituir spinner genérico por elemento de marca.
- Empty states adicionais — sem permissão, sem conexão, error state.
- Logos das sub-marcas exportadas como PNG/SVG (atualmente só existem como composições no `.fig`).

---

## Licença e propriedade

Este Design System é propriedade da **Patrimonium Contabilidade**. Uso restrito a colaboradores, parceiros autorizados e produtos da marca.

---

*Patrimonium Design System · v1.0.0 · maio 2026 · Mantido pelo time de Design.*
