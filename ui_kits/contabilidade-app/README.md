# Patrimonium · UI kit · Contabilidade (app interno)

Recriação de alta fidelidade do app web Patrimonium para clientes (empresas) — autenticação, dashboard, documentos, NFe, obrigações e produtos.

## Telas cobertas

- **Dashboard** — KPI row + tabela de documentos + side panel de obrigações + card "Radar" (`index.html`)

## Componentes (vistos em index.html)

- Sidebar navy com selo P‑cápsula, grupos "Principal" e "Produtos", chip de contador verde
- Topbar com search, ícones (notificações com dot verde), avatar circular
- KPI card (overline + display + sub + delta badge)
- Tabela com header em overline, badges status, hover row
- Filter chips (toggle)
- Doc card (icon-box info-bg)
- Listagem de "próximas obrigações" com dia/mês big
- CTA card invertido (navy-deep) com botão verde
- Modal (backdrop com blur, form com label uppercase)
- Toast bottom-right

## Tokens
Todos os valores vêm de `colors_and_type.css`. Nenhum hex hardcoded fora dos tokens.

## Faltam (pedido para o usuário)
- Login / signup screens
- Tela de Notas fiscais (listagem completa)
- Tela do produto Radar (deep dive)
- Empty states com ilustração
- Dark mode (não está no PDR)
