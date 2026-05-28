# PDR · Patrimonium DS · Patch v2.0.1

> **PDR = Patch Description Record.** Documento de instruções para que outras instâncias de IA apliquem coerentemente as alterações da v2.0.1 em todos os ambientes onde o DS é consumido (Figma, Claude Code, Claude Design, Google AI Studio, e qualquer IA com o repositório no contexto).
>
> **Quem deve ler este documento:** qualquer IA que receba a tarefa de atualizar o Patrimonium DS para v2.0.1, ou aplicar produtos com base na v2.0.1.
>
> **Premissa:** este é um patch **corretivo** da v2.0.0. Adiciona variantes light de gradient e glass, e afrouxa restrições que estavam tornando a aplicação incompleta. Retro-compatível em quase tudo (apenas o token CSS `--glass-*` muda nome — ver seção 4.3).

---

## 1. Sumário executivo

A v2.0.0 entregou fundação de identidade visual (camadas, gradients, glass, lockups). Em uso real, expôs dois problemas estruturais:

1. **Bias dark-mode.** Os 3 gradients e o glass tinham tinta navy escura. Sobre produto Patrimonium (majoritariamente light), criavam contraste agressivo. Não funcionavam como linguagem light-mode-first.
2. **Restrições restritivas demais.** "Uma única ocorrência por tela" do brand-accent e os 3 cenários do glass tornavam a aplicação **parcial**. Telas ficavam incompletas — nem com identidade aplicada nem com sobriedade plena.

A v2.0.1 corrige isso com 3 mudanças:

1. **2 gradients novos light-mode-first** (`soft-hero`, `accent-soft`)
2. **2 variantes de glass** (dark com opacidade ajustada + nova light)
3. **Regra-mãe do glass reescrita** — agora aplicada por **densidade de texto**, não por lista de cenários

---

## 2. Lista exaustiva de mudanças

### 2.1 Tokens adicionados

**Gradients (2):**
```
--gradient-soft-hero      linear-gradient(135deg, #F7F8FB 0%, #E0E7FF 100%)
--gradient-accent-soft    linear-gradient(135deg, #E0E7FF 0%, #E6F7EF 100%)
```

**Glass — variante light (4 variáveis):**
```
--glass-light-blur     blur(20px)
--glass-light-bg       rgba(255, 255, 255, 0.68)
--glass-light-border   0.5px solid rgba(15, 23, 42, 0.06)
--glass-light-shadow   0 4px 8px rgba(15, 23, 42, 0.04), 0 16px 40px rgba(15, 23, 42, 0.06)
```

### 2.2 Tokens alterados

**Glass dark — opacidade ajustada:**
```
--glass-dark-bg:     rgba(11, 27, 63, 0.78)  →  rgba(11, 27, 63, 0.72)
--glass-dark-border: 0.5px solid rgba(255, 255, 255, 0.08) → 0.10
```

**Glass dark — renome:** variáveis CSS `--glass-blur`, `--glass-bg`, `--glass-border`, `--glass-shadow` da v2.0.0 passam a ser `--glass-dark-blur`, `--glass-dark-bg`, `--glass-dark-border`, `--glass-dark-shadow`. Em tokens.json, o token `glass.patrimonium` da v2.0.0 vira `glass.dark` na v2.0.1.

### 2.3 Regras alteradas

**`gradient-brand-accent` — restrição de frequência REMOVIDA.** A regra "uma única ocorrência por tela" da v2.0.0 não existe mais. Pode aparecer múltiplas vezes na mesma tela. Restrição técnica de tamanho mantida (ícone 48-96px, texto via background-clip ≥40px, fundo de card ≥120px).

**`gradient-brand-accent` — uso "fundo de KPI card destaque" agora explícito.** Estava implícito antes; agora é caso de uso prescritivo na seção 16.3 do AI_CONTEXT.

**Glass — escopo reescrito.** A v2.0.0 listava 3 cenários (modal sobre dados, header sticky, sidebar institucional). A v2.0.1 substitui por **regra-mãe de densidade de texto**:

> Container que carrega estrutura visual → glass.
> Container denso em informação textual → sem glass.

Onde glass agora pode aparecer: sidebar de navegação, banner institucional de página, KPI cards limpos, cards de destaque, painéis com chart, modais, header sticky, cards de hub. Onde continua proibido: conteúdo de tabela, cards densos em texto, botões, inputs, atomic, tooltip, empty state, elementos <120px.

### 2.4 Documento `AI_CONTEXT.md` — alterações estruturais

| Local | Mudança |
|---|---|
| Cabeçalho | Versão `v2.0.0` → `v2.0.1` |
| Seções 1–15 | Sem mudança |
| Seção 16 (Gradients) | Reescrita: 5 gradients no catálogo (era 3). Restrição de frequência do brand-accent removida. Casos de uso de cada gradient atualizados. |
| Seção 17 (Glassmorphism) | Reescrita: regra-mãe de densidade de texto. 2 variantes (dark e light). Listas atualizadas de onde usar e onde não. |
| Seção 18 (Lockups) | Sem mudança |
| Rodapé | Versão `v2.0.0` → `v2.0.1` |

### 2.5 Documento `tokens.json` — alterações

- `version`: `"2.0.0"` → `"2.0.1"`
- Bloco `gradient`: 2 entradas novas (`soft-hero`, `accent-soft`). Descrições das entradas existentes atualizadas com nova regra do brand-accent.
- Bloco `glass`: reorganizado de `{patrimonium: {...}}` para `{dark: {...}, light: {...}}`. Opacidade do dark ajustada.

### 2.6 Documento `colors_and_type.css` — alterações

- 2 variáveis CSS novas de gradient
- 4 variáveis CSS novas de glass light
- 4 variáveis CSS de glass dark **renomeadas** (era genérico `--glass-*`, vira `--glass-dark-*`)
- Bloco `@supports not` atualizado com fallback de ambas as variantes
- Ver `colors_and_type.v2.0.1.patch.css` para o trecho exato

### 2.7 Documentos não tocados

- README.md, PROMPT_BOILERPLATE.md, docs/PRINCIPLES.md, docs/CONTRIBUTING.md — sem mudança
- Os 16 PNGs de lockup já uploaded na v2.0.0 continuam válidos

---

## 3. Instruções por ambiente

### 3.1 Para IA atualizando o Figma / Claude Design — `.fig` da Patrimonium

1. **Adicionar 2 styles novos de gradient** com os valores exatos da seção 2.1. Nomes: `gradient-soft-hero` e `gradient-accent-soft`.
2. **Atualizar o style de glass.** Remover o style `patrimonium-glass` antigo. Criar dois styles novos: `patrimonium-glass-dark` (com a opacidade ajustada de 0.72) e `patrimonium-glass-light`. Documentar a regra-mãe de densidade de texto no description de cada.
3. **Atualizar componentes que usam glass:** sidebar, banners institucionais, KPI cards de destaque, cards de hub. Trocar o estilo antigo pelo apropriado (dark ou light conforme o contexto da tela).
4. **Aplicar glass em mais componentes do que a v2.0.0 permitia.** Especificamente: sidebar de navegação operacional, KPI cards limpos, banner institucional de página. Esses agora têm glass por padrão.
5. **Refazer os swatches da página de Gradients no `.fig`.** Mostrar cada gradient na **escala de uso real**: brand-accent em círculo de 80px e em número grande com background-clip, não em retângulo 600×170px. Os swatches grandes da v2.0.0 estavam ensinando a IA aplicar errado. Cada swatch deve incluir o nome do gradient, valor HEX dos stops, ângulo, **e exemplo de aplicação em escala correta**.
6. **Atualizar capa do `.fig`** com versão v2.0.1.

### 3.2 Para IA refatorando produtos existentes (Claude Code, AI Studio)

1. **Atualizar `colors_and_type.css`** com as variáveis novas + renomes (ver `colors_and_type.v2.0.1.patch.css` seção "Migração").
2. **Buscar no codebase por uso de `--glass-blur`, `--glass-bg`, `--glass-border`, `--glass-shadow`** (sem sufixo `-dark`). Para cada ocorrência, decidir:
   - É sobre fundo escuro? → renomear para `--glass-dark-*`
   - É sobre fundo claro? → renomear para `--glass-light-*` E ajustar para a fórmula light (cores diferentes)
   - Em dúvida pelo contexto? → adicionar aliases temporários conforme a seção "Migração" do patch CSS, e refatorar gradualmente
3. **Atualizar `tokens.json`** com os 2 gradients novos e o bloco glass reorganizado.
4. **NÃO refatorar componentes existentes para usar variantes light de glass de forma agressiva.** Patch é aditivo nesse sentido — se um produto está funcionando com sólido em vez de glass, não force a mudança. Aplicar glass deliberadamente onde a v2.0.1 prescreve, não em retrofit massivo.
5. **Atualizar telas que tinham brand-accent aplicado em apenas 1 lugar "por restrição da v2.0.0"** — se fizer sentido visualmente, agora pode aparecer em múltiplos KPIs principais.

### 3.3 Para IA gerando produto novo (Google AI Studio, Cursor, v0, Lovable)

Sem ação especial. A próxima vez que a IA ler o repositório atualizado:

- Pegará AI_CONTEXT.md v2.0.1 com seções 16 e 17 reescritas
- Pegará tokens.json v2.0.1 com 5 gradients e 2 variantes de glass
- Saberá aplicar variante light de glass em produto light mode
- Saberá aplicar `brand-accent` em múltiplos KPIs principais na mesma tela quando fizer sentido
- Saberá aplicar glass em sidebar, banner, KPI card limpo (não só em 3 cenários restritos)

O boilerplate em `PROMPT_BOILERPLATE.md` continua válido sem alteração.

---

## 4. Validação

### 4.1 Checklist de migração

- [ ] AI_CONTEXT.md v2.0.1 publicado no repositório
- [ ] tokens.json v2.0.1 publicado e válido (JSON válido)
- [ ] colors_and_type.css atualizado com 6 vars novas + 4 renomes + fallback atualizado
- [ ] CHANGELOG.md tem entrada v2.0.1 prepended
- [ ] ROADMAP.md tem entrada v2.1 atualizada
- [ ] Figma `.fig` tem styles `gradient-soft-hero`, `gradient-accent-soft`, `patrimonium-glass-light` criados
- [ ] Swatches de gradient no `.fig` refeitos em escala de uso real
- [ ] Componentes que usam glass (sidebar, banner, KPI card de destaque, modal) revisados
- [ ] Buscar e renomear `--glass-*` em codebase de produto existente

### 4.2 Teste prático sugerido

Refazer o teste do hub central que estava previsto para a v2.0.0, agora com a v2.0.1 aplicada:

> "Crie uma tela de dashboard Patrimonium em light mode, com sidebar de navegação, banner institucional de topo 'Visão geral · maio 2026', 4 KPI cards (sendo um destacado com brand-accent), um painel de chart e um card destaque de oportunidade Radar."

Critérios de sucesso:
- Sidebar aplica `glass-light` corretamente sobre fundo claro
- Banner institucional usa `gradient-soft-hero` (não `gradient-hero` que é dark)
- KPI card destacado usa `gradient-brand-accent` como fundo
- Demais KPI cards usam camada `surface-light-card` (sólida)
- Glass não aparece em conteúdo de tabela, botões, search bar
- Capitalização correta de sub-marcas

Se algum desses falhar, registrar o caso e ajustar a redação no AI_CONTEXT para v2.0.2.

### 4.3 Breaking changes a observar

O único breaking change real desta versão é o **rename das variáveis CSS de glass**. Em código que importou v2.0.0:

| v2.0.0 | v2.0.1 |
|---|---|
| `--glass-blur` | `--glass-dark-blur` |
| `--glass-bg` | `--glass-dark-bg` |
| `--glass-border` | `--glass-dark-border` |
| `--glass-shadow` | `--glass-dark-shadow` |

Solução de transição: adicionar aliases temporários no `:root` (ver patch CSS seção "Migração") até que todo o código seja refatorado.

---

## 5. O que NÃO faz parte deste patch

- Ícones individuais das sub-marcas (pendente v2.1)
- Tratamento de KPI distintivo formalizado (pendente v2.1 — mas brand-accent já pode ser aplicado em fundo de KPI)
- Padrão de chart próprio (pendente v2.1)
- Loader Patrimonium (pendente v2.1)
- Empty states adicionais (pendente v2.1)
- Mudança em camadas de superfície (seção 15 mantida da v2.0.0)
- Mudança em lockups de sub-marca (seção 18 mantida da v2.0.0)

---

## 6. Filosofia desta versão (para IAs interpretarem decisões futuras com coerência)

Três decisões de design embutidas neste patch:

**Restrição prescritiva tem limite — o ponto onde restringir vira sub-aplicar.** A v2.0.0 caiu nesse limite com brand-accent ("uma vez por tela") e glass ("3 cenários"). Eram tentativas de prevenir papagaio, mas o efeito real foi produto que parecia incompleto. A v2.0.1 ajusta o equilíbrio: restrição técnica fica (não dá pra aplicar gradient em texto pequeno demais — não vai ler), restrição estética sai (não importa quantas vezes aparece desde que cada aplicação seja em elemento de destaque). Quando uma restrição prescritiva criar mais problema que resolve, removê-la é honesto.

**Bias do contexto da conversa pode envenenar a entrega.** A v2.0.0 ficou dark-only não por decisão consciente, mas porque a conversa que originou a versão (paleta dark da v1.0.1) deixou o pensamento enviesado pra dark. A v2.0.1 corrige isso adicionando pares light. Sempre que uma nova versão for trabalhada, vale perguntar: o produto Patrimonium é majoritariamente em qual modo? A linguagem visual proposta funciona nesse modo? Se a resposta for "não testei nesse modo", reabrir.

**Regra-mãe > lista de casos.** A v2.0.0 do glass tinha lista de 3 cenários onde aplicar. Cada produto novo gerado pela IA precisava conferir se caía exatamente em um dos 3 — qualquer caso novo (KPI card limpo, sidebar operacional) não estava na lista e a IA não aplicava. A v2.0.1 substitui a lista por uma heurística aplicável: "container estrutural sim, container denso em texto não". Listas são úteis como exemplos, mas a regra principal precisa ser uma heurística geral que cobre casos não previstos.

---

*Patrimonium DS · PDR v2.0.1 · maio 2026.*
