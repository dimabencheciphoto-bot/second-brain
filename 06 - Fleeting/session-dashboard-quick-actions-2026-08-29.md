---
title: "Sessão — Dashboard: strip do overnight-engine + Quick Actions"
date: 2026-08-29
tags: [dashboard, quick-actions, overnight-engine, fleeting, session]
---

# Sessão — Dashboard: strip do overnight-engine + Quick Actions
**Data:** 2026-08-29
**Repo:** `dima visual claude` · branch `master` · 2 commits, sem push

## Contexto
O dashboard local ("JARVIS — Control Interface", `dashboard/server.py` na porta 7842) ainda tinha
toda a UI do overnight-engine, que foi apagado como projecto mais cedo neste dia. Objectivo da
sessão: deixar o dashboard coerente com o que existe hoje e enriquecer as Quick Actions.

## O que foi feito

### 1. `fix(market_agent)` — commit `3ec1114`
- `message.content[0].text` rebentava quando o primeiro bloco era um `ThinkingBlock` (sem `.text`).
  Agora itera até ao primeiro bloco `type == "text"`. Era a causa real de "o botão Market Report
  não faz nada".
- Import corrigido: `from vault_market` → `from scripts.vault.vault_market` (só o root do repo
  está no `sys.path`).

### 2. `feat(dashboard)` — commit `46d9e0d`

**Limpeza do overnight-engine (UI):**
- Fora de `server.py`: `activity_feed()`, `pipeline_steps()`, `next_run_info()` e o dict `engine`
  em `build_stats()`. Fora também `renderProcs` no cliente (rebentava a cada poll — DOM
  inexistente — e bloqueava os cards seguintes).
- Fora de `index.html`: cards Activity Feed / Pipeline / Engine Log, botão "Run Overnight Engine",
  entrada de navegação "Logs", com CSS/JS associado.
- `/api/stats` agora devolve `tokens / system / processes / business / focus`.

**Generalização do `/api/run`:**
Passou de "só `python script.py`" para um dict `ACTIONS`. Cada entrada é uma de:
| forma | efeito |
|---|---|
| `{"script": "<path>"}` | `python <path>` detached |
| `{"cmd": [...], "cwd": ...}` | comando arbitrário (ex. `npm run dev`), `shell=True` no Windows |
| `{"open_file": "<path>"}` | abre ficheiro local no browser, sem subprocess |
| `+ "open": "<url>"` | opcional — abre o URL ~4s depois (helper `run_action()`, `threading.Timer`) |

Paths relativos a `ROOT` (root do repo). Flag `CREATE_NO_WINDOW` no Windows.

**11 Quick Actions no `index.html`, em 3 grupos:**
- **Correr:** Market Report · Custos → Telegram · UGC → Vault · Ideação Content Factory ·
  Atualizar Finanças · Lint do Vault
- **Abrir ferramenta:** Editor de Vídeos — Viralto (Remotion Studio :3000) ·
  Content Factory Dashboard (:7843) · Viralto Content Kanban (:7844)
- **Abrir relatório:** Ver Relatório de Mercado · Ver Dashboard Financeiro

**Fora de propósito (não são botões):** `publish_*`, `send_instagram_dms`,
`nightly_outreach --auto` — publicam / enviam ao vivo, perigoso num clique. Documentado em
`dashboard/CLAUDE.md`.

### 3. Verificação
9/11 acções corridas end-to-end com sucesso. `market` e `ideation` **não disparadas** de
propósito (custo Claude API + minutos de runtime) — entrypoints no-arg confirmados. Nota: o timer
de 4s abre o browser antes de o Remotion Studio (~20s) estar pronto → refrescar a página.

## Em aberto
- **Reiniciar o servidor na porta 7842** para ver as mudanças ao vivo.
- `finance/gerar_dashboard.py` continua untracked no git (pré-existente, não commitado nesta ronda).
- `business_stats()` UGC ainda lê `ugc_system/pipeline.csv` (inexistente; o real é
  `ugc_system/output/deals.csv`, com colunas diferentes) → tiles UGC a 0. Fix à parte.
- Findings do hook `impeccable` em `index.html` (transições de `width` L124/199/394, `.grid-bg`
  L496, glow em `.sidebar-logo` L142) classificados como estética JARVIS intencional; não
  suprimidos.

## Relacionado
- [[Overnight Engine]] (projecto apagado 2026-08-29)
