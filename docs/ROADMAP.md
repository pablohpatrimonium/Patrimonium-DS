# Roadmap · Patrimonium Design System

Histórico de releases e próximas versões.

---

## v1.0.0 · maio 2026 · Primeira versão pública (atual)

Versão fechada. Sistema completo de Foundations + Atoms + Components + Navigation + Brand + Templates + Documentação.

Ver `CHANGELOG.md` para a lista detalhada.

---

## v1.1 · próxima minor (sem data)

Itens registrados como pendência durante a produção da v1.0. Entram quando houver tempo de produção e/ou destrava externa.

### Marca
- **Capitalização final das 8 sub-marcas** — pendente de decisão de marketing.
  - `patrimonium news` vs `Patrimonium News`
  - `radar` vs `Radar`
  - Após decisão, atualizar `PRINCIPLES.md`, `AI_CONTEXT.md`, `.fig` e Branded House Arquitetura.
- **Logos das sub-marcas exportadas** — hoje só existem como composições no `.fig`. Exportar PNG e SVG das 8 sub-marcas em fundo claro e escuro.

### Componentes
- **Loader com identidade Patrimonium** — substituir spinner genérico por elemento de marca (provavelmente derivado da P-cápsula). Manter comportamento técnico, trocar o visual.
- **Empty states adicionais** — cobrir os 3 casos faltantes:
  - "Acesso restrito" (sem permissão)
  - "Sem internet" (sem conexão)
  - Error state (falha ao carregar dados)

### Documentação
- **Exemplo visual de link clicável na Data Table** — token já documentado (`link: --brand-navy`), falta apenas mostrar uma coluna de exemplo.

---

## v1.2 · backlog (sem data)

Itens identificados durante uso real ou solicitações do time. Priorização será decidida quando se aproximar.

### Possíveis adições
- **Data viz** — paleta de gráficos derivada de Teal/Ciano/Navy médio; charts (linha, barra, donut, área); empty/loading/error de chart; tooltip e legenda.
- **Email templates** — comunicação transacional (notificação, comprovante, recuperação de senha) em HTML.
- **PDF templates** — comprovante de recuperação, relatório fiscal. Adaptação de paleta para CMYK/print.

### Possíveis refinamentos
- **Storybook ou equivalente** — preview vivo para dev, alternativa aos HTMLs estáticos.
- **Adoção em produção** — rastrear cobertura de tokens vs hex literal nos repositórios.
- **Tokens Studio sync** — sincronização bidirecional entre Figma e o `tokens.json`.

---

## v2.0 · futuro (sem data)

Mudança maior que justificaria salto major. Sem candidato definido hoje.

Possíveis cenários:
- Refatoração de naming completa
- Inversão de sistema (light-first → dark-first)
- Migração para nova família tipográfica

---

## Como esse roadmap é mantido

- Itens novos chegam via processo descrito em `CONTRIBUTING.md`.
- Owner do DS revisa quinzenalmente o que está em v1.1 e backlog.
- Quando v1.1 acumular volume suficiente, vira release planejada com data.
- Patches (v1.0.x) entram conforme correções pontuais.

---

*Roadmap atualizado em maio 2026.*
