---
title: "Content Factory — Fase 1 (Ideação) concluída"
tags: [content-factory, overnight-engine, instagram, ai-automation]
created: 2026-07-05
status: active
---

# Content Factory — Fase 1 (Ideação) concluída

Pacote `content_factory/` no workspace `Documents\dima visual claude\`, irmão de `overnight_engine/`. Fábrica de conteúdo pessoal para a marca do Dima (nicho AI tools/automação), inspirada no pipeline de Emil Faschang (vídeo YouTube lh3ED0zQS0c) — mas com gravação humana em lote em vez de 100% sintético.

## Estado: Fase 1 completa e mergeada em master (commit `ef64911`)

Componentes implementados via Subagent-Driven Development (7 tasks + revisão final):
- `config.py`, `competitors.txt`
- `competitor_scraper.py` — Playwright, reutiliza sessão persistente de `scripts/send_instagram_dms.py`
- `pattern_analyzer.py` — Claude Sonnet analisa reels scrapados → hooks/tópicos/formatos
- `brief_generator.py` — Claude Haiku gera briefs de gravação
- `run_ideation.py` — orquestrador + resumo Telegram

19/19 testes automatizados. Verificação real end-to-end: scraping de `@growithalex` (12 reels reais), 10 briefs gerados em português, Telegram confirmado.

## Roadmap — fases seguintes (por implementar)

1. Gravação em lote (manual, semanal, cobrindo os briefs já gerados)
2. `/raw-cut` — dividir a gravação longa em clips por briefing
3. Edição com Remotion — legendas, B-roll, variações A/B
4. Publicação — Instagram via Meta Graph API, reutilizando `overnight_engine/publishers/instagram.py` (sem Metricool/trial reels)

**Próximo passo real:** depende de o Dima já ter gravado com os 10 briefs. Se não, a gravação vem antes de qualquer código novo.

Detalhe técnico completo: `wiki/meta/Content-Factory-Fase1-Ideacao-Concluida.md` no wiki do projecto.
