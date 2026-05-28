# Roadmap · Patrimonium Design System

## v2.1 · Identidade visual completa

**Status:** planejada · início após acumulação de uso real da v2.0.1.

### Motivação

A v2.0 (e o patch v2.0.1) entregou a fundação cromática da identidade visual Patrimonium: camadas de superfície, 5 gradients oficiais (com pares light/dark), glassmorphism com 2 variantes e regra de densidade de texto, lockups de sub-marca. Produtos gerados a partir dela já têm sensação de profundidade própria e identidade aplicada — em ambos os modos.

Dois elementos importantes ficaram em aberto:

1. **Ícones individuais das sub-marcas.** Os lockups são compostos (ícone + texto), úteis em cabeçalhos e capas. Para sidebar, hub central, breadcrumb e outros lugares onde o produto pede apenas o elemento gráfico, precisamos extrair 8 ícones individuais em 24/32/48px.
2. **Tratamento autoral de elementos críticos do produto.** Números de KPI, charts e empty states ainda usam padrões genéricos.

### Escopo proposto

- **Ícones individuais das sub-marcas (8 SVGs em 24/32/48px)** em `/assets/icons-sub-brands/`
- **Tratamento de KPI distintivo** — formalizar quando aplicar brand-accent, combinação com mono + tabular-nums + halo sutil
- **Padrão de chart próprio** — curvas suavizadas, paleta 3 séries via data-accent, grid hairline, tooltip navy-deep
- **Loader Patrimonium** — substituir spinner genérico
- **Empty states adicionais** — sem permissão, sem conexão, error, sem resultado de busca

## v1.1 · Ajustes técnicos

- Alinhar sobreposição de naming `--brand-neutral-dark` × `--neutral-strong`

---

## v0.2 · Templates completos (Q3 2026)

- **Login / Recuperação de senha** — auth CNPJ + senha, com estados de erro
- **Tabela de NFe** — listagem com filtros aplicados, paginação, ações em linha
- **Detalhe de registro** — drawer lateral + página full para NFe
- **Form longo** — cadastro de empresa em 4 passos
- **Página de erro** — 404 e 500
- **Settings** — perfil, equipe, integrações
- **Onboarding** — primeira entrada com empty state guiado

## v0.3 · Logos das sub‑marcas (Q3 2026)

- Export PNG/SVG dos 8 logos de sub‑marca (atualmente só existem como composições no Figma):
  - Central de Inteligência Tributária
  - Arquivo Digital
  - BPO Financeiro
  - Recuperação Tributária
  - patrimonium news
  - radar
  - Academy
  - Certificado Digital
- Template para 9ª sub‑marca futura
- Do's e don'ts visuais

## v0.4 · Data viz (Q4 2026)

- Paleta de gráficos derivada das cores de apoio (Teal, Ciano, Navy médio)
- Charts: linha, barra, donut, área
- Empty/loading/error states de chart
- Tooltip de chart
- Legenda

## v0.5 · Dark mode (Q1 2027)

- Tokens espelhados em modo `dark`
- Inversão dos pares de contraste WCAG
- Componentes auditados em ambos os modos
- Switch persistido por usuário

## v0.6 · Email & PDF templates (Q2 2027)

- Templates HTML de e‑mail (notificação, comprovante, recuperação de senha)
- Templates PDF (comprovante de recuperação, relatório fiscal)
- Adaptação da paleta para CMYK/print

## v0.7 · Tokens export & dev handoff (contínuo)

- Export Style Dictionary (CSS, iOS, Android, Web)
- Tokens Studio sync
- Storybook ou equivalente para dev preview
- Adoção em produção: rastrear cobertura de tokens vs hex literal nos repositórios

## Backlog (sem data)

- Versão impressa do manual de marca
- Vídeo de motion guidelines (curvas de easing, durações)
- Acessibilidade: audit de leitores de tela em telas críticas
- Localização: regras de truncagem e quebra em PT‑BR
- Branding sonoro (jingle / ringtone do app)
