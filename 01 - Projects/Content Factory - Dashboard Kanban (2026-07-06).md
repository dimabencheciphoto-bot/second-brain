---
type: session
title: "Content Factory - Dashboard Kanban"
date: 2026-07-06
updated: 2026-07-06
tags:
  - content-factory
  - dashboard
  - code-review
status: developing
related:
  - "[[Content Factory - Fase 1 Ideacao (2026-07-05)]]"
summary: "Dashboard de estado do pipeline Content Factory"
---

## O que é

`content_factory/dashboard/` (renomeado de `content_factory_dashboard/` nesta sessão para consolidar tudo num só projecto) — kanban de 5 colunas (RAW → LEGENDADO → COM_BROLL → PRONTO → PUBLICADO) sobre o pipeline `content_factory/`. Implementado via subagent-driven-development (8 tasks, spec em `Docs/superpowers/specs/2026-07-05-content-factory-dashboard-design.md`).

Ficheiros principais: `server.py` (HTTP API, porta 7843, sem framework), `pipeline_state.py` (classificação pura por coluna), `jobs.py` (tracker de jobs em background), `actions.py` (dispatch das acções por coluna), `index.html` (front-end).

## Trabalho desta sessão (2026-07-06)

1. **Botão "Visualizar"** adicionado junto aos botões amarelos de acção — carrega o vídeo do clip inline via novo endpoint `GET /api/video?column=&clip=&batch=`, usando `actions.resolve_clip_path`.
2. **Bug de vídeo não aparecer** — causa raiz: 3 processos `python.exe` duplicados todos a escutar na porta 7843 (Windows permite isto sem erro), pedidos a serem roteados de forma não determinística para processos antigos sem o endpoint novo. Corrigido matando os 3 PIDs e arrancando um único processo fresco.
3. **Metadados de data/duração** por clip — reaproveitado o `manifest.json` já escrito por `raw_cut.py` (tem `duration` por clip) em vez de invocar `ffprobe` de novo; data de criação usa `Path.stat().st_mtime` (não existe timestamp de gravação real no modelo de dados).
4. **Revisão profissional do código** (`content_factory/` + `content_factory_dashboard/`) — achados por prioridade:
   - #1 `/api/video` não sanitiza `column`/`clip`/`batch` → risco de path traversal (por fazer)
   - #2 `/api/video` sem suporte a HTTP Range → quebra scrubbing de vídeo, carrega ficheiro inteiro em memória (por fazer)
   - #3 `jobs.start_job` sobrescreve `_jobs[clip]` sem verificar se já há um job a correr para o mesmo clip → jobs concorrentes duplicados (por fazer)
   - **#4 CORRIGIDO**: fallback silencioso `except ImportError: from anthropic import Anthropic` estava copiado em 4 ficheiros (`publish_variants.py`, `add_hook_variant.py`, `pattern_analyzer.py`, `brief_generator.py`), violando a convenção do projecto ("nunca usar `anthropic.Anthropic()` directamente"). Substituído por import directo de `MonitoredAnthropic` — falha alto e claro se não disponível. 26 testes continuam a passar.

## Continuação (mesma sessão, mais tarde a 2026-07-06)

5. **Consolidação de pastas**: `content_factory_dashboard/` movido via `git mv` para `content_factory/dashboard/` (pedido do Dima: "ficar tudo junto num projecto só"). Ajustados `sys.path.insert` (mais um `.parent`) e imports (`from content_factory_dashboard import X` → `from content_factory.dashboard import X`) em `server.py`, `actions.py` e nos 3 ficheiros de teste. Suite completa a passar depois da mudança.
6. **Itens #1, #2, #3 da revisão anterior — todos implementados e testados**: sanitização de `column`/`clip`/`batch` contra path traversal (`_validate_component` em `actions.py`); `jobs.start_job` agora rejeita jobs duplicados para o mesmo clip (`RuntimeError`); `/api/video` passou a suportar HTTP Range (206 Partial Content) para scrubbing de vídeo. 22 testes a passar.
7. **Botão "Visualizar" na coluna PUBLICADO**: antes só existia nas colunas activas. Adicionado o botão + elemento `<video>` também ao card de PUBLICADO; `resolve_clip_path` (`actions.py`) passou a tratar `"PUBLICADO"` como `"COM_BROLL"`/`"PRONTO"` (aponta para `final_dir`), já que `publish()` nunca move o ficheiro fisicamente — fica sempre em `final_dir`.
8. **UX de erro de vídeo**: quando `/api/video` devolve 404 (ficheiro final em falta), a interface agora mostra "Vídeo não encontrado." em vez de ficar silenciosamente vazia — adicionado `video.onerror` + `div.video-error` em todos os cards.
9. **Dado de teste conhecido, intencionalmente não corrigido**: `clip_001` em `content_factory/data/publish_log.json` está marcado como PUBLICADO mas nunca teve a fase final renderizada (só existe `captioned/clip_001.mp4`, não `final/clip_001.mp4`) — por isso o Visualizar mostra "não encontrado" para este clip específico. O Dima confirmou explicitamente **duas vezes** para deixar como está; não voltar a sugerir "corrigir" isto.

## Pendente

- Roadmap de fases seguintes do content_factory (variações A/B, publicação) continua por fazer — ver [[Content Factory - Fase 1 Ideacao (2026-07-05)]].
- Nenhum item de revisão em aberto neste momento (os 3 anteriores foram todos resolvidos).
