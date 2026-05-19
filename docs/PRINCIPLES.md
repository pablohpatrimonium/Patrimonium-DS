# Princípios · Patrimonium Design System

Os 7 princípios que guiam decisões de design. Quando algo não estiver no sistema, decida com base aqui — não invente padrão novo se um princípio resolve.

---

## 1. Solidez antes de virtuosismo

Patrimonium é parceiro fiscal, não SaaS divertido. Confiança lê melhor que criatividade. Quando em dúvida entre **convencional bem feito** e **novo e arriscado**, escolha o convencional. Inovação se reserva para problemas onde o padrão falha — não para diferenciação visual.

**Decide isto:** sem animação decorativa · sem gradientes diagonais · sem texturas/grain · sem emoji.

---

## 2. O miolo é sagrado

O selo P‑cápsula com miolo verde é o motivo central da marca. Toda sub‑marca o herda; nenhuma o reinventa. O verde `#00FCA8` só aparece como **acento ou como fundo de texto escuro** — nunca como cor de texto sobre claro, nunca em headline.

**Decide isto:** uma nova sub‑marca se diferencia pelo nome, não por cor. Verde nunca carrega texto.

---

## 3. Discreet, low‑spread

Sombras simulam luz vinda de cima, sem offset horizontal. Cor‑base é `rgba(15,23,42,X)` com alpha ≤ 0.12. Tudo é discreto — quem precisa "gritar" é o conteúdo, não a interface.

**Decide isto:** sombra colorida → não · spread alto → não · neon glow → não.

---

## 4. Paleta restrita por escolha

3 cores principais + 6 de apoio. **Não existem subtons funcionais** (nada de `green-50`, `green-100`...). Se uma situação precisa de tom que não está na paleta, ela está sendo mal resolvida — repense antes de inventar cor.

**Decide isto:** cor nova que "parece da marca" precisa ser justificada e aprovada — não é decisão de uma pessoa.

---

## 5. Saltos grandes, não gradação fina

Escala de radius dobra a cada degrau (8 · 16 · 32 · 999). Spacing tem 11 valores mas só 6 são preferenciais. Tipografia salta entre níveis. Pequenas diferenças (`10` vs `14`, `20` vs `24`) confundem hierarquia em vez de enriquecê‑la — cada valor tem função designada.

**Decide isto:** se você precisa de "entre o md e o lg", está usando o valor errado em algum lado.

---

## 6. Affirmative ≠ Save

A variant `affirmative` (botão verde pill) é reservada para **ganho explícito do cliente** — recuperação de crédito, identificação de oportunidade, aprovação. Não é sinônimo de "salvar". Não é a variant default para CTAs.

**Decide isto:** "Salvar", "Enviar", "Confirmar" → primary (azul). "Recuperar", "Habilitar", "Aprovar crédito" → affirmative (verde).

---

## 7. Branded House, não Casa de Marcas

Toda sub‑marca herda o sistema visual da matriz. Não existe variação de paleta, tipografia ou voz por vertical. O que diferencia uma sub‑marca da outra é apenas o **nome** e o **escopo** — visualmente, todas falam a mesma língua.

**Decide isto:** se uma vertical pede "uma cor própria", recuse. Patrimonium tem uma identidade — não nove.

---

## Adendo · Opacidade não é foundation

**Opacidade nunca é usada para alterar a aparência de conteúdo significativo** (texto, ícones, cores de marca). Para atenuar elementos, use o token certo:

| Caso | ❌ Não use | ✓ Use |
|---|---|---|
| Texto secundário | `opacity: 0.6` | `--neutral-light` |
| Placeholder | `opacity: 0.5` | `--neutral-light` |
| Ícone disabled | `opacity: 0.4` | `--neutral-light` ou token de cor |
| Cor de marca atenuada | `rgba(brand, 0.2)` | tokens semânticos `*-bg` (`--success-bg`, `--info-bg`) |
| "Desligar" um botão | `opacity: 0.5` | variant `disabled` |

Opacidade só aparece em **camadas sobrepostas com transparência funcional**, e sempre embutida no token do componente — nunca como token solto:

- **Sombras** — já incluídas em `--shadow-1/2/3`
- **Backdrop de modal/drawer** — `--backdrop-modal` (navy `#0F172A` @ 45%)
- **Anel de foco** — `--focus-ring` (navy @ 18%, 4px spread)
- **Hover de item de menu invertido** — `--menu-hover-on-dark` / `--menu-active-on-dark` (branco @ 8% / 12%)
- **Hover de item de menu sobre claro** — `--menu-hover-on-light` (navy @ 6%)

**Decide isto:** se você está prestes a escrever `opacity:` em CSS, está usando o token errado em outro lugar.
