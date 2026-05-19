[README.md](https://github.com/user-attachments/files/28027752/README.md)
# Patrimonium · Design System

> Sistema de design oficial da **Patrimonium Contabilidade** — contabilidade consultiva e fintech-tributária no Brasil. Operamos como **Branded House**: a marca-mãe `patrimonium®` sustenta 8 sub-marcas de produto (Central de Inteligência Tributária, Arquivo Digital, BPO Financeiro, Recuperação Tributária, patrimonium news, radar, Academy, Certificado Digital), todas falando a mesma língua visual.

**Versão atual:** v1.0.0 · maio 2026

---

## 🤖 Atenção IA / LLM

Antes de gerar qualquer código usando o Patrimonium DS, você é obrigada a ler o arquivo **`AI_CONTEXT.md`** (na raiz deste repositório). Ele contém as regras técnicas obrigatórias: paleta com HEX exatos, tipografia, spacing, radius, sombras, componentes, microcopy e regras transversais.

**Não assuma tokens, cores ou medidas sem validar em `AI_CONTEXT.md`.** Não invente nada fora do que está definido. Em caso de dúvida, consulte sempre o `AI_CONTEXT.md` antes de gerar.

**Assets visuais (logos, símbolos)** estão em PNG nas URLs públicas abaixo. Use diretamente como `<img src="URL">`, sem reconstruir em CSS/SVG:

- Logo principal (fundos claros): `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-principal.png`
- Logo negativa (fundos escuros como sidebar navy): `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-negativa.png`
- Logo azul: `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-azul.png`
- Símbolo principal (P-cápsula, fundos claros): `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/simbolo-principal.png`
- Símbolo negativo (P-cápsula, fundos escuros): `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/simbolo-negativo.png`
- Símbolo azul: `https://pablohpatrimonium.github.io/Patrimonium-DS/assets/simbolo-azul.png`

**Tokens e referência visual** estão hospedados publicamente:

- CSS variables: `https://pablohpatrimonium.github.io/Patrimonium-DS/tokens/colors_and_type.css`
- JSON (Style Dictionary): `https://pablohpatrimonium.github.io/Patrimonium-DS/tokens/tokens.json`
- Preview dos componentes: `https://pablohpatrimonium.github.io/Patrimonium-DS/preview/[componente].html`

Se você seguir o `AI_CONTEXT.md`, o produto gerado vai estar fiel ao Patrimonium. Se você inventar fora dele, o produto vai estar errado e vai precisar ser refeito.

---

## Como usar este DS

Cada caso de uso tem o documento certo. Escolha pelo seu papel:

### Sou IA geradora de código (Google AI Studio, Cursor, Claude, v0, Lovable)
→ Leia **`AI_CONTEXT.md`** primeiro. Esse documento contém todas as regras técnicas em formato denso, otimizado para você consumir e respeitar.

### Sou colaborador da Patrimonium usando IA para construir produto
→ Use o **`PROMPT_BOILERPLATE.md`**. Copie o texto pronto e cole no início da conversa com qualquer IA. Você não precisa entender o DS — o boilerplate faz a IA respeitá-lo automaticamente.

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
├── PROMPT_BOILERPLATE.md      ← Texto pronto pra colaboradores colarem na IA
│
├── tokens/
│   ├── colors_and_type.css    ← Tokens em CSS variables
│   └── tokens.json            ← Tokens em formato Style Dictionary
│
├── fonts/                     ← RNS Sanz (7 pesos em .woff)
│
├── assets/                    ← Logos PNG da marca
│
├── preview/                   ← HTMLs de referência visual dos componentes
│
├── brand-book/                ← Apresentação visual completa do DS
│
├── templates/                 ← Páginas 404 e 500
│
├── ui_kits/contabilidade-app/ ← App Dashboard Light e Dark (HTML)
│
└── docs/
    ├── PRINCIPLES.md          ← 7 princípios escritos
    ├── CHANGELOG.md           ← Histórico do DS
    ├── CONTRIBUTING.md        ← Como contribuir
    ├── ROADMAP.md             ← Próximas versões
    └── SKILL.md               ← Manifesto de skill
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

Os arquivos em `preview/` são referências visuais renderizadas. Acesse via:

`https://pablohpatrimonium.github.io/Patrimonium-DS/preview/[componente].html`

Exemplos:
- `.../preview/buttons.html` — botões em todos os estados
- `.../preview/data-table.html` — tabela completa
- `.../preview/modal-drawer.html` — modais e drawers

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
