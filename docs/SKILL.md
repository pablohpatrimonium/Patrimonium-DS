---
name: patrimonium-design
description: Use this skill to generate well-branded interfaces and assets for Patrimonium Contabilidade, either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

Read the `README.md` file within this skill, and explore the other available files.

If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy assets out and create static HTML files for the user to view. Always link `colors_and_type.css` rather than redefining tokens. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.

If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions, and act as an expert designer who outputs HTML artifacts _or_ production code, depending on the need.

## Quick reference

- **Brand:** Patrimonium Contabilidade — Branded House (marca‑mãe `patrimonium®` + sub‑marcas)
- **Língua:** PT‑BR. Você. Imperativo direto. **Sem emoji.**
- **Cores:** Navy `#1A3375` + Green `#00FCA8`. Paleta deliberadamente restrita.
- **Tipo:** RNS Sanz (7 pesos em `fonts/`).
- **Ícones:** Lucide, stroke 1.5px uniforme, viewBox 24×24.
- **Cantos:** 6 / 10 / 14 / 20 / 999 px.
- **Sombras:** tinta navy (não preto).

## Files
- `colors_and_type.css` — tokens
- `fonts/` — RNS Sanz .woff
- `assets/` — logos e símbolos
- `preview/` — cards do DS (referência visual)
- `ui_kits/contabilidade-app/` — atoms + tela completa do app interno
