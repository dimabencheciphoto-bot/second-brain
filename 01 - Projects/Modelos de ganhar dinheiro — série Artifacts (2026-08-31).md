---
title: "Modelos de ganhar dinheiro — série de Artifacts"
date: 2026-08-31
tags: [project]
status: active
area: "02 - Areas/Negócio & Dinheiro"
summary: "Série de páginas HTML publicadas (Artifacts claude.ai), uma por pergunta de como ganhar dinheiro; sistema visual partilhado, conteúdo pt-PT com fontes de 2026"
related:
  - "[[faceless-content-accounts-2026]]"
  - "[[Instagram Personal Brand - Reposicionamento (2026-07-06)]]"
  - "[[Content Factory - Pipeline]]"
  - "[[Viralto - Agência AI]]"
---

# Modelos de ganhar dinheiro — série de Artifacts

## Goal

Uma biblioteca de páginas de referência, cada uma a responder a **uma** pergunta concreta sobre
formas de gerar rendimento. Cada nova pergunta do Dima → um Artifact novo (ficheiro novo → URL nova),
não uma edição do anterior. Servem para escolher 2-3 apostas e aprofundar depois.

## Why

O Dima está a mapear opções de rendimento (ligado ao pivot da Viralto e à marca pessoal no Instagram).
Quer material relegível, visual, em português de Portugal, com números e fontes verificáveis de 2026 —
não listas motivacionais. O formato Artifact dá URL partilhável e lê bem em claro/escuro.

## Sistema visual partilhado (todos os Artifacts da série)

- **Tipos:** Fraunces (display), IBM Plex Sans (corpo), IBM Plex Mono (dados/labels) — via Google Fonts.
- **Fundo:** `#F7F5EF` claro / `#131512` escuro. Verde de "dinheiro" `--cash` `#2F7D46` / `#63C081`.
- **Easing:** `cubic-bezier(0.16, 1, 0.3, 1)`. Medida ~65 car., `tabular-nums`, `text-wrap: balance`.
- **Tema em 3 estados:** `:root` = paleta clara completa; `@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) }`; `:root[data-theme="dark"]` — tokens repetidos, nunca cor só dentro de bloco media/data-theme.
- **Acento distinto por entrega** (ver tabela). Padrões JS reutilizados: tabela ordenável (`aria-sort`), scroll-reveal via IntersectionObserver, barras de CPM em JS, guard de `prefers-reduced-motion`.
- Ao publicar: varrer segredos com Grep antes; `favicon` emoji; `<title>` = nome curto tipo produto; `description` de uma frase.

## Feito (2026-08-31)

Cinco Artifacts publicados (por ordem):

| # | Nome | Âmbito | Acento | Favicon | URL |
|---|---|---|---|---|---|
| 1 | **Terreno Novo / Caça de Oportunidades** | Modelo mental de caça a oportunidades + 15 ideias de negócio bootstrap (PT + mundo, 10 anos) | verde | 💡 | https://claude.ai/code/artifact/1b8ec716-1850-459d-98ad-34a27ee7f29a |
| 2 | **Dinheiro Esta Semana** | Negócios provados que dão dinheiro na 1ª semana | azul-petróleo `#1D5E7A` | — | https://claude.ai/code/artifact/6029ddf7-8ed6-405d-8463-5a288a86d5bd |
| 3 | **Comprar e Vender** | Retalho comprar-barato-vender-caro | ocre/latão `#9A6A1E` | — | https://claude.ai/code/artifact/2028ac95-20bc-4182-8fb5-681024852969 |
| 4 | **Vender em Digital** | Produtos digitais + redes sociais — as 9 vias, matriz, plano de 7 dias | cerise/rosa `#A83258` / `#E8749A` | 📲 | https://claude.ai/code/artifact/f2722620-379f-4b91-9e6f-d17a0f0e2727 |
| 5 | **Playbook Faceless** | Como os profissionais criam e monetizam contas de conteúdo faceless | azul-ardósia `#3D5A98` / `#8AA9E0` | 🎭 | https://claude.ai/code/artifact/e1bc2115-a60f-4167-8228-a845f3d27b5c |

Ficheiros-fonte dos Artifacts no scratchpad da sessão (não versionados):
`vender-em-digital.html`, `playbook-faceless.html`, `comprar-e-vender.html`, `dinheiro-esta-semana.html`, `ideias-empreendedorismo.html`.

### Drill-down de conteúdo (perguntas só-texto, sem Artifact)

Depois do #5, o Dima aprofundou o tema faceless por texto:
- Exemplos de contas faceless (curiosidades, finanças, IA/tech, história, viagem, animação).
- Como procurar um nicho (4 critérios + método de 5 passos, teste dos 30 primeiros vídeos).
- Como avaliar "concorrência gerível" (6 sinais + passo a passo 30-45 min + regra ≥ 18/25).
- Nicho **Finanças pessoais & investimento**: 11 pilares de tema, sub-ângulo *finanças e impostos para quem investe a partir de Portugal*, canais de referência PT/BR, nota de compliance YMYL.

Todo esse digest de pesquisa (13 fontes, Ago 2026) está em [[faceless-content-accounts-2026]].

Em Set/2026 o Dima pediu para **verificar com dados reais** via NexLev (análise de 50k+ canais YouTube):
- Pesquisa de 3 nichos candidatos → veredito: **Finanças pessoais aberto**, IA/ferramentas fechado (RPM baixo),
  Estoicismo/self-improvement saturado (12/15 canais chamados "Stoic ___").
- Links de canais + método do veredicto (6 sinais: datas de criação, distribuição de outlierScore, gama de RPM,
  espalhamento de receita, diversidade de ângulos, densidade de canais IA) explicados ao Dima.
- Segunda ronda: nichos novos a bombar (Ago-Set 2026, outlier ≥ 2) e depois "que mais nichos podem ter sucesso"
  (lote alargado de 120 canais + 682 vídeos outlier) — mega-engenharia explicada, gaming narrado/simulação,
  história militar/negócio em ES/DE/FR, comics "What If", psicologia estética-sombria, comparação de equipamento
  de nicho. Tudo detalhado (com números e ressalvas de copyright) em [[faceless-content-accounts-2026]] §10.

## Próximo

- À espera da próxima pergunta do Dima → próximo Artifact da série.
- Candidato a aprofundar: montar de facto uma conta faceless no nicho finanças-PT (produção em lote, stack ElevenLabs + CapCut), agora com validação de dados reais NexLev.
