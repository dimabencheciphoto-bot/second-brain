---
title: "Content Factory — Pipeline"
date: 2026-07-06
tags: [content-factory, overnight-engine, instagram, ai-automation, dashboard]
status: developing
summary: "Pipeline de conteúdo pessoal (ideação → raw cut → legendas → B-roll) + dashboard Kanban"
related: []
---

# Content Factory — Pipeline

Consolida 2 notas de sessão (Fase 1 Ideação, 2026-07-05; Dashboard Kanban, 2026-07-06). Pacote `content_factory/` no workspace, irmão de `overnight_engine/` — fábrica de conteúdo pessoal para a marca do Dima (nicho AI tools/automação), inspirada no pipeline de Emil Faschang, mas com gravação humana em lote em vez de 100% sintético.

## Estado actual

Fase 1 (Ideação) completa e mergeada em master (`ef64911`): `competitor_scraper.py` (Playwright), `pattern_analyzer.py` (Claude Sonnet), `brief_generator.py` (Claude Haiku), `run_ideation.py`. 19/19 testes; verificação end-to-end com scraping real de `@growithalex` (12 reels) → 10 briefs em português + resumo Telegram.

Dashboard Kanban (`content_factory/dashboard/`, porta 7843, sem framework) — 5 colunas RAW → LEGENDADO → COM_BROLL → PRONTO → PUBLICADO. Construído via subagent-driven-development (8 tasks). Todos os achados de revisão de código (path traversal em `/api/video`, falta de HTTP Range, jobs duplicados, fallback `anthropic.Anthropic()` directo em 4 ficheiros) foram corrigidos e testados.

## Pendentes

- Roadmap de fases seguintes: gravação em lote → `/raw-cut` → edição Remotion (legendas, B-roll, variações A/B) → publicação Instagram via Meta Graph API. Próximo passo real depende de o Dima já ter gravado com os 10 briefs da Fase 1.
- `clip_001` em `content_factory/data/publish_log.json` está marcado PUBLICADO mas nunca teve a fase final renderizada (só existe `captioned/`, não `final/`) — **dado de teste intencional, confirmado 2× pelo Dima para deixar como está. Não sugerir corrigir.**

## Histórico de sessões

### 2026-07-05 — Fase 1 (Ideação) concluída

Componentes implementados via Subagent-Driven Development (7 tasks + revisão final). Detalhe técnico completo em `wiki/meta/Content-Factory-Fase1-Ideacao-Concluida.md` no wiki do projecto.

### 2026-07-06 — Dashboard Kanban: visualização, bugs, revisão de código, consolidação de pastas

1. Botão "Visualizar" adicionado — endpoint `GET /api/video` carrega o clip inline.
2. Bug de vídeo não aparecer: 3 processos `python.exe` duplicados na mesma porta (Windows permite sem erro), pedidos roteados para processos antigos sem o endpoint novo — corrigido matando os PIDs.
3. Metadados de data/duração reaproveitados do `manifest.json` já escrito por `raw_cut.py`, em vez de invocar `ffprobe` de novo.
4. Revisão profissional do código, 4 achados: **corrigido** de imediato o fallback `except ImportError: from anthropic import Anthropic` copiado em 4 ficheiros (`publish_variants.py`, `add_hook_variant.py`, `pattern_analyzer.py`, `brief_generator.py`) — violava a convenção "nunca usar `anthropic.Anthropic()` directamente"; substituído por import directo de `MonitoredAnthropic`. Os outros 3 (path traversal, falta de HTTP Range, jobs duplicados) resolvidos mais tarde na mesma sessão.
5. `content_factory_dashboard/` consolidado via `git mv` para `content_factory/dashboard/` (pedido do Dima: "ficar tudo junto num projecto só") — imports e `sys.path` ajustados nos 3 ficheiros de teste + `server.py`/`actions.py`.
6. Os 3 achados de revisão pendentes implementados e testados: sanitização de `column`/`clip`/`batch` contra path traversal; `jobs.start_job` rejeita jobs duplicados; `/api/video` passou a suportar HTTP Range (206 Partial Content).
7. Botão "Visualizar" estendido à coluna PUBLICADO — `resolve_clip_path` trata `"PUBLICADO"` como `"COM_BROLL"`/`"PRONTO"`, já que `publish()` nunca move o ficheiro fisicamente.
8. UX de erro de vídeo: 404 mostra "Vídeo não encontrado." em vez de ficar silenciosamente vazio.
9. `clip_001` identificado como dado de teste sem fase final renderizada — Dima confirmou 2× para deixar como está.
