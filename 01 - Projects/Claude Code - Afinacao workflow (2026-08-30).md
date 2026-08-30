---
title: "Claude Code — Afinação do workflow"
date: 2026-08-30
tags: [project]
status: active
area: ai-dev
related: ["[[Workspace — Estado Geral 2026-06-14]]", "[[AI Development]]"]
---

# Claude Code — Afinação do workflow

## Goal
Setup do Claude Code (subagentes, hooks, skills, tooling, contexto de arranque) alinhado com as best practices de 2026 e enxuto de ruído.

## Why
7 rondas de research (29–30 Ago) sobre novidades do Claude Code + workflows de praticantes. Fonte de verdade: `dima visual claude/Wiki/questions/Research-Claude-Code-Uso-Profissional-2026.md`.

## Feito (30 Ago 2026)

### Subagentes
- `test-writer` e `code-reviewer` → ambos `model: sonnet` (antes haiku / opus). Haiku falha raciocínio subtil em testes; Opus para review "is often overkill" (docs).
- `description` dos dois começa por "Usar PROACTIVAMENTE" (a auto-delegação do Claude lê a description).
- Linha de **Delegação** do `CLAUDE.md` reescrita: subagente `sonnet` por defeito (qualquer raciocínio); `haiku-4-5` só trabalho mecânico de alto volume.

### Tooling Python
- `ruff` instalado (`uv tool install`, em `~/.local/bin/`). Adoção **incremental, zero diff agora**:
  - `pyproject.toml` novo — só `[tool.ruff]`, `select = E,F,I,UP,B,SIM`, vários `ignore`, exclui skills/vendor/generated_carousels.
  - `.claude/hooks/ruff_autofix.py` — hook `PostToolUse` que corre `ruff check --fix` + `ruff format` **só no ficheiro que o Claude acabou de editar**. Nunca bloqueia.
- `fd` (v10.5.0) e `jq` (v1.8.2) instalados via winget.

### Hooks
- `.claude/hooks/block_sensitive_edits.py` — hook **`PreToolUse`** (`Edit|Write|MultiEdit`), exit 2 = bloqueia. Alvos: `.env` e `.env.*` (menos `.env.example`), `vendor/**`, `*.pdf`. Testado com 5 payloads.
- Array `PreToolUse` novo em `.claude/settings.local.json` (antes só PostToolUse + Stop).

### Statusline
- `~/.claude/statusline-command.sh` reescrita: `modelo | branch | N% ctx` (antes só `branch | N% context used`).

### Contexto de arranque
- CLAUDE.md **não** é o problema (~2k tok). Peso real = skills.
- 20 skills globais movidas `~/.claude/skills/` → `~/.claude/skills-disabled/` (`cf-*` 9, `figma-*` 9, `azure-kusto`, `algorithmic-art`). Global 164 → 144. Reversível.
- `ckm-*` e `higgsfield-*` mantidas (workspace faz brand kits + geração de imagem).

### context7
- Plugin **instalado mas desligado** (`~/.claude/settings.json` → `enabledPlugins`). MCP HTTP remoto de docs de libs actualizadas.
- Regra: ligar **à peça** quando houver trabalho não trivial com Next.js / Remotion / FastAPI-Pydantic v2 / SDK Anthropic, ou erro de "método não existe" numa lib de terceiros. Não ligar para scripts internos / stdlib / design.

### /doctor (30 Ago 2026)
Corrido o comando `/doctor` (health-check checks 0–9). Janela: 36 sessões / 29,5 dias.
- **Limpo:** versão == latest (2.1.251); native install sem restos npm; `defaultMode` já `auto`; hooks rápidos; nada a pré-aprovar.
- **Aplicado — `~/.claude/settings.json`:** +19 skills em `skillOverrides: "off"` (131→150). Todas frias na janela; ~2,2k tok est. a menos no arranque. Lista: canvas, canvas-design, ckm-design, ckm-design-system, frontend-design, higgsfield-generate, internal-comms, pptx, remotion, think, ralph-loop-workflow, seo-audit, wiki, wiki-ingest, wiki-lint, wiki-mode, wiki-query, save, obsidian-markdown. Undo: apagar chaves / pôr `"on"` + reiniciar.
- **Aplicado — 4 CLAUDE.md aninhados** (working tree, NÃO commitado): `Wiki/`, `Clients/OsteoJP/site/`, `viralto/site/`, `tendas-eventos/`. −178 linhas: árvores de rotas/componentes + comandos `npm` padrão (derivam de `ls` + `package.json`). Mantido contactos, IDs de deploy Vercel, cores de marca, métricas de sucesso, gotchas. Undo: `git checkout --` dos 4.
- **NÃO aplicado** (Dima não escolheu): desligar `context7` + 5 conectores claude.ai — mesma acção que a task manual abaixo.

## Tasks — acção manual do Dima
- [ ] `/mcp` → desligar Higgsfield / NexLev / VIDIQ (~255 tool defs que não se usam a programar). Manter telegram, playwright, chrome-devtools.
- [ ] Reiniciar o Claude Code (activa: 20 skills movidas, 3 hooks novos, linha de delegação).
- [ ] `/plugin` → enable `context7` quando cair num caso de uso (ver acima).
- [ ] Commit dos 8 ficheiros (3 agents + CLAUDE.md + pyproject.toml + 2 hooks + settings.local.json) — pathspecs explícitos, working tree tem deletions pendentes.

## Notes
- Rondas 1–4 documentadas na nota de memória `project_claude_code_workflow_adaptation` e no research doc do workspace.
- Decisões deixadas em aberto por opção: `CLAUDE_CODE_ENABLE_TODO_TOOLS` (não ligar); big-bang do ruff (rejeitado — solo, sem CI, working tree sujo).

## Outcome
(preencher quando as 4 acções manuais estiverem feitas)
