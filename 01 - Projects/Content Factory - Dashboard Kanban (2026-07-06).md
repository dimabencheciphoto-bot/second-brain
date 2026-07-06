---
type: session
title: "Content Factory - Dashboard Kanban"
created: 2026-07-06
updated: 2026-07-06
tags:
  - content-factory
  - dashboard
  - code-review
status: developing
related:
  - "[[Content Factory - Fase 1 Ideacao (2026-07-05)]]"
---

## O que é

`content_factory_dashboard/` — kanban de 5 colunas (RAW → LEGENDADO → COM_BROLL → PRONTO → PUBLICADO) sobre o pipeline `content_factory/`. Implementado via subagent-driven-development (8 tasks, spec em `Docs/superpowers/specs/2026-07-05-content-factory-dashboard-design.md`).

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

## Pendente

- Itens #1, #2, #3 da revisão acima — não implementados, aguardam pedido explícito.
- `actions.py` importa `publish` de `publish_variants.py` a nível de módulo — se o dashboard estiver a correr, precisa de reiniciar para apanhar a correcção do #4.
- Roadmap de fases seguintes do content_factory (variações A/B, publicação) continua por fazer — ver [[Content Factory - Fase 1 Ideacao (2026-07-05)]].
