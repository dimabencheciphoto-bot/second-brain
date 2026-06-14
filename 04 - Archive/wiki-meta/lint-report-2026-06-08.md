---
type: meta
title: "Lint Report 2026-06-08"
created: 2026-06-08
updated: 2026-06-08
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-06-08

## Summary
- Pages scanned: 54
- Issues found: 26
- Auto-fixed: 0
- Needs review: 26

---

## Dead Links (7)

Links que apontam para páginas que não existem.

| Link | Tipo | Ação sugerida |
|---|---|---|
| `[[Anthropic SDK]]` | Conceito em falta | Criar stub em `03 - Resources/Concepts/` |
| `[[MoviePy v2 Patterns]]` | Conceito em falta | Criar stub em `03 - Resources/Concepts/` |
| `[[Playwright Guide]]` | Conceito em falta | Criar stub em `03 - Resources/Concepts/` |
| `[[Prompt Engineering]]` | Conceito em falta | Criar stub em `03 - Resources/Concepts/` |
| `[[01 - Projects]]` | Referência a pasta | Substituir por `[[_MOC Projects]]` |
| `[[Nome da nota]]` | Placeholder de template | Remover do template |
| `[[nota completa se existir]]` | Placeholder de template | Remover do template |

---

## Orphan Pages (12)

Páginas sem nenhum link de entrada — nada aponta para elas.

### Engine Runs (esperado, mas fixável)
- `[[2026-06-05]]` (Engine Runs/) → link a partir de `[[Overnight Engine]]`
- `[[2026-06-06]]` (Engine Runs/) → link a partir de `[[Overnight Engine]]`
- `[[2026-06-07]]` (Engine Runs/) → link a partir de `[[Overnight Engine]]`
- `[[2026-06-08]]` (Engine Runs/) → link a partir de `[[Overnight Engine]]`

### UGC / Market
- `[[2026-06-07]]` (UGC Outreach Runs/) → link a partir de `[[UGC Agency Launch]]`
- `[[2026-06-08]]` (Market Analysis/) → link a partir de `[[Market Analysis]]`

### Fleeting (normal — são notas efémeras)
- `[[2026-06-05]]`, `[[2026-06-06]]`, `[[2026-06-07]]`, `[[2026-06-08]]` (06 - Fleeting/)

### Projetos
- `[[Second Brain Cleanup]]` → link a partir de `[[_MOC Projects]]`
- `[[carousel-claude-code-2026-06-08]]` → link a partir de `[[_MOC Projects]]` ou criar `[[Carousel Generator]]`

---

## Missing Pages — Conceitos mencionados sem página própria (4)

Mencionados em múltiplas notas mas sem página dedicada. Alta prioridade.

- **Anthropic SDK** — mencionado em Claude Models, AI Development
- **MoviePy v2 Patterns** — mencionado em Overnight Engine
- **Playwright Guide** — mencionado em Overnight Engine / AI Development
- **Prompt Engineering** — mencionado em Prompt Library, AI Patterns

---

## Frontmatter Gaps

### Notas-chave SEM frontmatter (BLOCKER)
Estas são notas centrais do vault sem qualquer metadata:

- `Como Usar Este Vault` — hub do vault, devia ter frontmatter
- `Dashboard` — idem
- `Sobre Mim` — perfil pessoal
- `Market Agent` — projeto ativo
- `Musa 1.0` — projeto ativo
- `AI Development` — área ativa
- `Business Overview`, `Content Engine KPIs`, `Weekly Business Review`, `UGC Agency`
- `Market Analysis`, `AI Patterns`, `Agentic Patterns`, `Cost Optimization`
- `Claude Models`, `Model Comparison`, `Prompt Library`, `Claude Code Skills`
- `_MOC Projects`, `_MOC Areas`, `_MOC Resources`

### Notas com frontmatter incompleto
- `Overnight Engine` — faltam: type, status, tags, created, updated
- `UGC Agency Launch` — faltam: type, status, tags, created, updated
- `Token Usage` — faltam: type, status, tags, created, updated

### Templates sem frontmatter completo (baixa prioridade)
- `Experiment Log`, `Paper Note`, `Project Template`, `Prompt Template`

---

## Naming Conventions

Encontrado: `CPI-consumer-price-index.md` — lowercase com hífens, inconsistente com o padrão Title Case do resto do vault.
Sugestão: renomear para `CPI Consumer Price Index.md`.

---

## Ações Recomendadas (por prioridade)

### Alta prioridade
1. **Criar 4 stubs** em `03 - Resources/Concepts/`: Anthropic SDK, MoviePy v2 Patterns, Playwright Guide, Prompt Engineering
2. **Adicionar frontmatter** às notas-chave: Market Agent, Musa 1.0, Overnight Engine, UGC Agency Launch
3. **Ligar orphans** de Engine Runs a partir de `[[Overnight Engine]]`

### Média prioridade
4. Substituir `[[01 - Projects]]` por `[[_MOC Projects]]` onde aparece
5. Adicionar `[[Second Brain Cleanup]]` e `[[carousel-claude-code-2026-06-08]]` ao `_MOC Projects`
6. Limpar placeholders `[[Nome da nota]]` e `[[nota completa se existir]]` nos templates

### Baixa prioridade
7. Renomear `CPI-consumer-price-index.md` para Title Case
8. Frontmatter nas notas Fleeting (opcional — são efémeras por design)

---

*Gerado por `/wiki-lint` via claude-obsidian skill — 2026-06-08*
