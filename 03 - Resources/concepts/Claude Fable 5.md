---
tags:
  - ai/models
  - research
created: 2026-06-09
source: https://www.anthropic.com/news/claude-fable-5-mythos-5
---

# Claude Fable 5

Lançado a **9 de junho de 2026**. Versão pública da nova classe **Mythos** da Anthropic — o modelo mais capaz da empresa. Ver também [[AI Models Inventory]].

## Os dois modelos

- **Fable 5** — público, API + todos os planos pagos (Pro, Max, Team, Enterprise). Incluído sem custo extra até 22 de junho de 2026.
- **Mythos 5** — mesmo modelo, salvaguardas levantadas; restrito ao governo dos EUA (Project Glasswing), cibersegurança e investigadores biomédicos.

## Sistema de segurança (novidade estrutural)

> [!important] Fallback, não recusa
> 3 classificadores (cibersegurança ofensiva, biologia/química, destilação). Quando disparam, o pedido é **redirecionado para o Opus 4.8** em vez de recusado. +95% das sessões sem fallback. Zero respostas nocivas em 30 técnicas de jailbreak (red-teaming externo). Retenção de dados 30 dias (só monitorização de segurança).

## Benchmarks vs Opus 4.8 vs GPT-5.5

![[fable5-benchmark-table.png]]

| Benchmark | Fable 5 | Opus 4.8 | GPT-5.5 |
|---|---|---|---|
| SWE-Bench Pro | **80.3%** | 69.2% | 58.6% |
| FrontierCode Diamond (xhigh) | **29.3%** | 13.4% | 5.7% |
| Terminal Bench 2.1 | **88.0%** | 82.7% | 83.4% |
| Humanity's Last Exam (tools) | **64.5%** | 57.9% | 52.2% |
| OSWorld Verified | **85.0%** | 83.4% | 78.7% |
| ExploitBench (Cap'5) | **78.0%** | 47.0% | 34.0% |
| GDPval-AA (Elo) | **1932** | 1890 | 1769 |

Custo-eficiência em código — a curva do Fable 5 domina a do Opus 4.8 em todos os níveis de effort:

![[fable5-frontiercode-cost.png]]

## Resultados práticos

- **Stripe**: migração Ruby de 50M linhas em 1 dia (vs ~2 meses de equipa)
- **Every "Senior Engineer"**: 91/100 vs Opus 63, GPT-5.5 62
- **Hex analytics**: primeiro modelo a passar 90% (+10 pontos sobre Opus)
- Folhas de cálculo: bate o Opus em todos os efforts, 25–30% mais rápido
- Visão: reconstrói web apps de screenshots; completou Pokémon FireRed só com visão
- Mythos 5 em biologia: design de proteínas ~10x mais rápido

## Preços e quando usar

| Modelo | Input/Output $/1M | Quando usar |
|---|---|---|
| Sonnet 4.6 | $3 / $15 | 80% do trabalho diário, alto volume |
| Opus 4.8 | $5 / $25 | Profundidade: code review, análise estratégica; fallback do Fable |
| **Fable 5** | **$10 / $50** | Tarefas longas delegáveis (15+ min), runs autónomos multi-hora |

- Fable 5 = 2x Opus, 3.3x Sonnet por token — mas custo por *tarefa concluída* competitivo (resolve mais à primeira).
- Opus 4.8 vence Sonnet 4.6 em 7 de 8 benchmarks (Sonnet só ganha em Finance Agent).
- Regra: **Sonnet para volume, Opus para profundidade, Fable para delegação total.**

## Relevância para os meus pipelines

Os pipelines (Overnight Engine, UGC, Market Agent) usam Haiku/Sonnet para geração rápida e Opus para raciocínio — o Fable 5 só se justifica em tarefas agênticas longas, não em geração de volume.

## Artefactos locais

- Relatório completo: `dima visual claude/fable5_report/RELATORIO_FABLE5.md`
- Apresentação HTML (9 slides, dark OLED): `dima visual claude/fable5_report/apresentacao.html`
- 7 gráficos oficiais: `dima visual claude/fable5_report/images/`

## Fontes

- [Anúncio Anthropic](https://www.anthropic.com/news/claude-fable-5-mythos-5)
- [TechCrunch](https://techcrunch.com/2026/06/09/anthropic-released-claude-fable-5-its-most-powerful-model-publicly-days-after-warning-ai-is-getting-too-dangerous/)
- [Every — Vibe Check](https://every.to/vibe-check/anthropic-mythos-our-fable-vibe-check)
- [IT Pro — safeguards](https://www.itpro.com/technology/artificial-intelligence/anthropic-just-launched-claude-fable-5-its-first-mythos-class-ai-model-but-it-has-new-safeguards-to-prevent-misuse-and-will-fall-back-to-opus-4-8-for-high-risk-queries)
- [vanbeaumond.nl — qual modelo usar](https://vanbeaumond.nl/en/blog/claude-fable-5-opus-4-8-sonnet-4-6-which-model)
