# Como contribuir · Patrimonium Design System

## Quem aprova o quê

| Mudança | Aprova |
|---|---|
| Token novo (cor, type, spacing, radius, shadow) | Design Lead **e** Eng Lead |
| Componente novo (atom ou molecule) | Design Lead |
| Variant nova em componente existente | Design Lead |
| Bug fix visual em componente | 1 reviewer (designer ou frontend) |
| Conteúdo de marca (logo, voz, ilustração) | Design Lead **e** Marketing Lead |
| Mudança nos 7 princípios | Design Lead **e** liderança da empresa |

---

## Processo

1. **Abra uma discussão** antes de desenhar. Descreva o problema, não a solução. Exemplo: "preciso de um indicador de status para CNPJs com risco fiscal" — não "preciso de um badge laranja".
2. **Procure o que já existe.** 70% das vezes o problema já tem componente.
3. **Se for criar componente novo**, faça primeiro como **pattern** (composição de atoms existentes em um template). Só vire um componente formal depois de 2+ telas usarem o mesmo padrão.
4. **Proponha como PR ao DS**, com:
   - 1 frame visual do componente em todos seus estados/variants
   - Tokens consumidos (listados)
   - 1 caso de uso real em template
   - Rationale: por que existe e por que componentes existentes não resolvem
5. **Review** segue critérios:
   - **Looks good** — aprovado, mergear
   - **Needs work** — razão objetiva (acessibilidade, consistência, alinhamento com princípios)
   - **Out of scope** — válido mas não pertence ao DS; resolva localmente

---

## Critérios de aceite

Um componente entra no sistema quando:

- [ ] Consome **apenas tokens** — nenhum hex literal, nenhum px solto
- [ ] Cobre estados: default, hover, focus, active, disabled, loading (quando aplicável)
- [ ] Passa em **WCAG AA** para texto normal e **AAA** quando possível
- [ ] Tem **3+ casos de uso** documentados
- [ ] Tem **regras de uso escritas** (quando usar, quando não usar)
- [ ] Tem **versão Figma como Component Set** com Variants nomeadas

---

## O que **não** entra no DS

- Soluções específicas de uma feature (vire um pattern local)
- Variações decorativas sem caso de uso ("seria legal ter…")
- Mistura de marca de terceiros (logos de bancos, integrações etc.)
- Customização one‑off para um cliente

---

## Reportar bug

Abrir issue com:
- **Componente afetado** (`Button/primary/lg`)
- **Tela onde aparece**
- **Comportamento atual** vs **esperado**
- **Screenshot ou Figma frame** com a inconsistência

Bugs visuais em produção têm SLA: P0 (acessibilidade) — 48h · P1 (marca) — 1 semana · P2 (polish) — backlog priorizado.
