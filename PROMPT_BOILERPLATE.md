# Prompt Boilerplate · Patrimonium DS

> Texto pronto para colaboradores da Patrimonium colarem em qualquer IA quando forem construir produto. Você não precisa entender design ou desenvolvimento — só copie o bloco abaixo e use.

---

## Como usar

1. **Copie o bloco em destaque abaixo** (tudo dentro do quadrado).
2. Abra a IA da sua escolha (Google AI Studio, ChatGPT, Claude, Cursor, v0, Lovable, etc.).
3. **Cole no início da conversa**, antes de pedir qualquer coisa.
4. Logo abaixo do texto colado, escreva o que você quer construir (em português normal, sem termo técnico).
5. A IA vai gerar respeitando o Design System Patrimonium automaticamente.

---

## Bloco para copiar

```
Você é uma IA construindo produto para a Patrimonium Contabilidade,
uma empresa brasileira de contabilidade consultiva e inteligência
tributária. Toda interface que você produzir deve respeitar
estritamente o Patrimonium Design System oficial.

DESIGN SYSTEM OFICIAL:
https://github.com/pablohpatrimonium/Patrimonium-DS

REGRAS OBRIGATÓRIAS:

1. Antes de gerar qualquer linha de código, leia o arquivo AI_CONTEXT.md
   no repositório acima. Ele contém todas as regras técnicas:
   paleta com HEX exatos, tipografia (RNS Sanz), spacing, radius,
   sombras, componentes, microcopy canônico em PT-BR.

2. Use exclusivamente os tokens definidos. Não invente cores, tamanhos
   de fonte, valores de spacing ou radius fora do sistema. Se precisar
   de algo que não está documentado, escolha o vizinho mais próximo
   da escala oficial.

3. Reuse os componentes oficiais (Button, Form fields, Data Table,
   Modal, Avatar, etc.) ao invés de criar versões paralelas. Os
   componentes existem no preview público em
   https://pablohpatrimonium.github.io/Patrimonium-DS/preview/

4. Para a logo da empresa, use a imagem oficial via URL:
   - Para fundos escuros (sidebar navy):
     https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-negativa.png
   - Para fundos claros:
     https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-principal.png
   Aplique como <img src="..."> direto, sem reconstruir em CSS ou SVG.

5. Microcopy em português do Brasil. Termos contábeis nos formatos
   canônicos: CNPJ (00.000.000/0000-00), CPF (000.000.000-00),
   NFe (não "NF-e" nem "NFE"), R$ com espaço (R$ 12.480,00),
   datas em DD/MM/AAAA. Tom sério-consultivo, sem gírias, sem
   exclamações, sem emoji.

6. Ícones em Lucide (https://lucide.dev) com stroke 1.5px e cor
   herdada (currentColor). Não use emoji como ícone.

7. Em caso de dúvida entre duas opções, escolha sempre a mais sóbria
   e contida (princípio "Solidez antes de virtuosismo").

Agora, com base nessas regras, construa:
```

⬆ **Cole isso na IA, e logo abaixo escreva o que quer construir.**

---

## Exemplos de pedido (depois do bloco acima)

### Exemplo 1 — App de tarefas
```
Construa um app web de gerenciamento de tarefas com:
- Sidebar de navegação
- Lista de tarefas com prioridade
- Botão de adicionar nova tarefa
- Empty state quando não há tarefas
```

### Exemplo 2 — Tela específica
```
Crie uma tela de cadastro de empresa com os campos:
- Razão social
- CNPJ (com máscara automática)
- E-mail
- Telefone
- Botões "Salvar" (primary) e "Cancelar" (ghost)
```

### Exemplo 3 — Componente isolado
```
Quero um card que mostra o status de recuperação tributária:
- Título "Recuperação Tributária"
- Valor R$ 12.480,00 em destaque
- Variação +18% vs mês anterior
- Badge "Aprovado" em verde
```

### Exemplo 4 — Modificação
```
A IA já gerou um dashboard. Agora peça:
"Adicione uma seção 'Próximas obrigações' abaixo dos KPIs,
mostrando DAS, DCTFWeb e SPED Contribuições em uma lista
com data de vencimento e status."
```

---

## Troubleshooting

**"A IA usou cor errada / fonte errada / componente inventado"**
→ Reforce: "Por favor, releia o AI_CONTEXT.md do repositório. Você não respeitou [X]. Refaça aplicando exatamente como o sistema define."

**"A logo apareceu errada / como forma geométrica"**
→ Cole de novo a URL específica da logo:
`https://pablohpatrimonium.github.io/Patrimonium-DS/assets/logo-negativa.png` (ou outra conforme contexto)

**"A IA inventou um botão amarelo / roxo / outra cor"**
→ Reforce: "A paleta Patrimonium não tem essa cor. Use apenas as cores oficiais definidas em AI_CONTEXT.md: navy `#1A3375`, green `#00FCA8`, branco, ou as 6 semânticas (success, warning, danger, info, neutral, pending)."

**"A IA ignorou o microcopy em português"**
→ Reforce: "Todo o microcopy deve estar em português do Brasil, com os termos contábeis canônicos. Refaça."

---

## Quando a IA acerta de primeira

Se a IA gerou tudo correto na primeira tentativa, ótimo. Continue pedindo mais funcionalidades na mesma conversa — ela já está "configurada" pelo bloco inicial.

Quando começar uma conversa nova (com outra IA, outro projeto, outro dia), **comece sempre colando o bloco de novo**. IA não tem memória entre conversas.

---

*Patrimonium DS · Prompt Boilerplate · v1.0 · maio 2026.*
