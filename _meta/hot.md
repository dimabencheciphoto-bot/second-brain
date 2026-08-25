---
title: "Hot Cache"
updated: 2026-08-25
tags: [meta, cache]
---

# Recent Context

## Last Updated
2026-08-25. Auditoria de qualidade ao vault (ver `_meta/log.md` para detalhe): frontmatter em falta preenchido em 17 notas de `01 - Projects/`; confirmado que `vault_tokens.py`/`vault_ugc.py` (repo `dima visual claude`) nunca correram em produção — código funcional mas nunca agendado/invocado, pastas-alvo criadas apenas na primeira execução; correcção de 2 factos que estavam desactualizados desde 08-08 (ver abaixo). **Nota:** esta correcção prova, na prática, que o "Active Thread" de manter isto actualizado tinha voltado a falhar 17 dias — ver log.md para a lição.

## Key Recent Facts
- **Estrutura:** PARA (`00 - Inbox` → `01 - Projects` → `02 - Areas` → `03 - Resources` → `04 - Archive`), mais `06 - Fleeting/` e `.raw/`. Nota: `templates/` não tem número de prefixo (era `05 - Templates`, renomeada em data desconhecida) — inconsistência ainda não corrigida.
- **OsteoJP:** homepage redesenhada ("Percurso do paciente") promovida a `app/page.tsx` 2026-08-08; **deploy ao Vercel confirmado feito** (corrigido 2026-08-25 — a nota anterior aqui estava errada)
- **Viralto:** plano de publicação de 10 dias reconstruído por plataforma (2026-08-07); **lote-04 e lote-05 de guiões já existem** no repo (9 e 21 Ago) — mas qual direcção de design venceu (C+F blend vs. Opção F pura, ver nota de redesign lote-03) não foi reverificada nesta passagem; as 4 decisões de publicação de 07-08 (TikTok, LinkedIn, guião duplicado) continuam por confirmar; site ao vivo em vercel.app
- **tendas-eventos:** site Next.js ao vivo, deploy Vercel desactualizado; domínio custom ainda a servir site legado
- **Packs Workflows Make PT/BR:** produto digital €97/pack; retomar na Secção 3 (newsletter) + writing-plans
- **Content Factory:** fases 1, 2, 3a, 3b concluídas; próximo passo = variações A/B + publicação IG
- **Dashboard Financeiro Pessoal:** aberto — mover transacção Serghei Belous 2026-01-20 para categoria Megane?
- **Portfolio Casamento:** curadoria concluída — 217 fotos analisadas, 191 aprovadas, portfolio final de 28 fotos seleccionado; próximo passo = edição/exportação e envio de candidaturas
- **Instagram pessoal (@dimabencheci):** reposicionado para "conteúdo + IA para PMEs", pausado antes do guião do 1º Reel
- **Automação vault→Obsidian (repo `dima visual claude`, `scripts/vault/`):** só `vault_market.py` está realmente ligado (via `scripts/market_agent.py`); `vault_tokens.py` e `vault_ugc.py` são código funcional mas nunca agendado — não escrevem nada até serem corridos manualmente ou ligados ao Task Scheduler
- **Conhecimento LLM-first** (sources/entities/concepts extensos de pesquisa) vive em `Wiki/` no repo `dima visual claude`, não neste vault — ver nota em `_meta/AGENTS.md` §1

## Active Threads
- Viralto: confirmar qual direcção de design venceu no lote-03/04/05 + fechar as decisões do plano de publicação de 10 dias
- tendas-eventos: resolver DNS do domínio custom + redeploy
- Portfolio Casamento: editar/exportar as 28 fotos seleccionadas, enviar candidaturas
- vault_tokens.py/vault_ugc.py: decidir — agendar no Task Scheduler ou remover como código morto
- Second Brain: manter `hot.md`/`index.md` actualizados a cada operação — **já falhou duas vezes** (2 meses até 08-08, depois mais 17 dias até 08-25); não há mecanismo automático, só disciplina manual

## Navigation
- `index.md` → catálogo completo
- `02 - Areas/AI Development.md` → estado pipelines
- `02 - Areas/Viralto - Agência AI.md` → estado agência
- `01 - Projects/` → 28 notas + 3 subpastas activas
