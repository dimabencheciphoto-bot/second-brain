---
title: "Content Factory — Pipeline"
date: 2026-09-29
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

- `clip_001` em `content_factory/data/publish_log.json` está marcado PUBLICADO mas nunca teve a fase final renderizada (só existe `captioned/`, não `final/`) — **dado de teste intencional, confirmado 2× pelo Dima para deixar como está. Não sugerir corrigir.**
- **2026-09-29:** branch `worktree-content-factory-faceless` completo (15/15 tasks + fix pós-revisão, 240/240 testes) mas **por fazer merge**: checkout partilhado ocupado com WIP do Viralto sem relação, e repositório sem remoto git configurado. Ver secção de sessão abaixo.
- `content_factory/data/broll_library/` continua vazia — pré-requisito operacional antes de `run_daily.py` correr a sério (adicionar clips de stock).

## Pivot 2026-09-29 — automação "faceless" diária

O pipeline evoluiu do roadmap original (gravação humana em lote) para um pivot totalmente automatizado, sem gravação: **tendência → brief → síntese "faceless"** (TTS + B-roll + Remotion, sem câmara) **→ fila de aprovação no dashboard → publicação**. Plano completo em `docs/superpowers/plans/2026-09-29-content-factory-faceless-automation.md`, spec em `Docs/superpowers/specs/2026-09-29-content-factory-faceless-automation-design.md`.

Implementado via subagent-driven-development (15 tasks, fresh subagent + revisor por task + revisão final ao branch inteiro por um modelo mais capaz). Módulos novos: `trend_finder.py`, `tts.py`, `broll_selector.py`, `script_writer.py`, `synthesize_faceless.py` (orquestra os anteriores + composição Remotion `SynthClip`, gera variantes A/B), `run_daily.py` (orquestrador, alvo Task Scheduler), + colunas novas no dashboard (`A_AGUARDAR_APROVACAO`) com aprovação manual antes de publicar.

**Revisão final** apanhou 2 bugs Critical que tinham passado por todas as 15 revisões por task, porque cada lado testava a sua própria construção artificial dos ficheiros em vez da cadeia real: `publish()` (herdado do pipeline antigo de clips) nunca encontrava o vídeo B do pipeline diário (procurava na pasta errada), e a chave gravada no log de publicação nunca batia com a que o dashboard procura (risco real de publicar o mesmo conteúdo duas vezes a cada clique em "Aprovar"). Corrigido num único fix dispatch + re-review focada, 240/240 testes a passar.

Branch e worktree ficam intactos em `.claude/worktrees/content-factory-faceless/`, por fazer merge para `main` — decisão adiada para não mexer no WIP do Viralto no checkout partilhado nem exigir configurar um remoto git às pressas.

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
