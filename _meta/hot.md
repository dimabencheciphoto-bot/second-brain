---
title: "Hot Cache"
updated: 2026-08-25
tags: [meta, cache]
---

# Recent Context

## Last Updated
2026-08-25 (2ª passagem). Segunda ronda da auditoria de qualidade — 8 itens executados (ver `_meta/log.md` para detalhe completo): `status: activo`→`active` corrigido; frontmatter completado em mais 26 notas (scan fino por tipo de nota, evitando falsos positivos de `created` vs `date`); 3 ficheiros lixo apagados; `Claude Skills Inventory.md` arquivada (desactualizada, framework claude-flow inteiro já não existe); bug de case-sensitivity `Concepts`→`concepts` corrigido em `vault_session.py`; `templates/`→`05 - Templates` renomeada (alinhado com config dos plugins Obsidian, que já apontavam para lá); `VaultTokenSummary` (Task Scheduler) tinha caminho errado e estava desactivada — corrigida e activada; `VaultUGCSummary` criada de raiz, mesmo padrão; aviso de staleness do `hot.md` construído no `/morning` (>7 dias). **Achado importante:** `~/.anthropic_usage.json` não tem calls novas desde 2026-06-14 — o `VaultTokenSummary` vai continuar a reportar "sem calls" até isso ser investigado (fora do âmbito desta auditoria).

## Key Recent Facts
- **Estrutura:** PARA (`00 - Inbox` → `01 - Projects` → `02 - Areas` → `03 - Resources` → `04 - Archive`), mais `06 - Fleeting/`, `05 - Templates/` (renomeada de `templates/` 2026-08-25) e `.raw/`.
- **OsteoJP:** homepage redesenhada ("Percurso do paciente") promovida a `app/page.tsx` 2026-08-08; **deploy ao Vercel confirmado feito** (corrigido 2026-08-25 — a nota anterior aqui estava errada)
- **Viralto:** plano de publicação de 10 dias reconstruído por plataforma (2026-08-07); **lote-04 e lote-05 de guiões já existem** no repo (9 e 21 Ago) — mas qual direcção de design venceu (C+F blend vs. Opção F pura, ver nota de redesign lote-03) não foi reverificada nesta passagem; as 4 decisões de publicação de 07-08 (TikTok, LinkedIn, guião duplicado) continuam por confirmar; site ao vivo em vercel.app
- **tendas-eventos:** site Next.js ao vivo, deploy Vercel desactualizado; domínio custom ainda a servir site legado
- **Packs Workflows Make PT/BR:** produto digital €97/pack; retomar na Secção 3 (newsletter) + writing-plans
- **Content Factory:** fases 1, 2, 3a, 3b concluídas; próximo passo = variações A/B + publicação IG
- **Dashboard Financeiro Pessoal:** aberto — mover transacção Serghei Belous 2026-01-20 para categoria Megane?
- **Portfolio Casamento:** curadoria concluída — 217 fotos analisadas, 191 aprovadas, portfolio final de 28 fotos seleccionado; próximo passo = edição/exportação e envio de candidaturas
- **Instagram pessoal (@dimabencheci):** reposicionado para "conteúdo + IA para PMEs", pausado antes do guião do 1º Reel
- **Automação vault→Obsidian (repo `dima visual claude`, `scripts/vault/`):** `vault_market.py` (via `scripts/market_agent.py`), `vault_tokens.py` (Task Scheduler `VaultTokenSummary`, segundas 09:00) e `vault_ugc.py` (Task Scheduler `VaultUGCSummary`, segundas 09:05) estão todos ligados e activos desde 2026-08-25. `vault_tokens.py` vai reportar "sem calls" até `~/.anthropic_usage.json` voltar a ser actualizado (parado desde 2026-06-14).
- **Conhecimento LLM-first** (sources/entities/concepts extensos de pesquisa) vive em `Wiki/` no repo `dima visual claude`, não neste vault — ver nota em `_meta/AGENTS.md` §1

## Active Threads
- Viralto: confirmar qual direcção de design venceu no lote-03/04/05 + fechar as decisões do plano de publicação de 10 dias
- tendas-eventos: resolver DNS do domínio custom + redeploy
- Portfolio Casamento: editar/exportar as 28 fotos seleccionadas, enviar candidaturas
- **token_monitor:** Sem novas calls há 72 dias (última: 2026-06-14). token_monitor pode estar partido. (detectado por `vault_tokens.py` em 2026-08-26)
- Second Brain: manter `hot.md`/`index.md` actualizados a cada operação — já falhou duas vezes antes (2 meses, depois 17 dias); agora há um aviso automático no `/morning` se `hot.md` passar de 7 dias sem actualizar, mas continua a exigir que alguém aja sobre o aviso

## Navigation
- `index.md` → catálogo completo
- `02 - Areas/AI Development.md` → estado pipelines
- `02 - Areas/Viralto - Agência AI.md` → estado agência
- `01 - Projects/` → 28 notas + 3 subpastas activas
