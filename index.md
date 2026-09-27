---
title: "Second Brain Index"
updated: 2026-09-27
tags: [meta, index]
---

# Second Brain — Index

Catálogo master. Uma linha por página. Actualizar em cada operação.

---

## 01 - Projects

*Tabela gerada ao vivo por Dataview a partir do frontmatter (`summary`/`status`) de cada nota — nunca fica desactualizada. Para actualizar, edita a nota, não esta tabela.*

```dataview
TABLE summary AS "Tópico", status AS "Status"
FROM "01 - Projects"
WHERE summary
SORT date DESC
```

### 01 - Projects/Portfolio Casamento
| Note | Tópico |
|------|--------|
| [[Portfolio Casamento - Curadoria]] | Curadoria de fotos para candidatura a 2º fotógrafo |
| [[Quintas Lisboa — Outreach 2026-06-28]] | Outreach a quintas de casamento na zona de Lisboa |

### 01 - Projects/UGC Outreach Runs
Run de outreach UGC: `2026-07-04`.

### 01 - Projects/UGC Agency
Snapshots semanais do pipeline UGC, gerados automaticamente por `scripts/vault/vault_ugc.py` (Task Scheduler, `VaultUGCSummary`, segundas 09:05): `pipeline-2026-08-25` em diante.

---

## 02 - Areas

```dataview
TABLE summary AS "Responsabilidade", status AS "Status"
FROM "02 - Areas"
SORT file.name ASC
```

---

## 03 - Resources/concepts

AI/Tech: [[Anthropic SDK]], [[AI Patterns]], [[Agentic Patterns]], [[Prompt Engineering]], [[Prompt Library]], [[Cost Optimization]], [[MoviePy v2 Patterns]], [[Playwright Guide]], [[CPI Consumer Price Index]], [[AI Models Inventory]], [[Claude Fable 5]], [[Obsidian Skills]], [[Carousel Generator]]

UGC/Business: [[AI-Automation-Agency]]¹, [[UGC Agency Business Model]], [[UGC Cold Outreach]], [[UGC Portfolio]], [[UGC Pricing]]

¹ Stub — conteúdo completo em `Wiki/concepts/AI-Automation-Agency.md` (repo `dima visual claude`).

## 03 - Resources/sources

[[src-ugc-agency-blueprint]], [[src-ugc-cold-email-guide]], [[src-ugc-pricing-2025]], [[src-claude-prompts-10-every-day]], [[src-claude-prompts-50-steal]], [[src-automate-instagram-carousels]], [[ciela-ai-agency-niches-2026]]¹, [[prr-ia-nas-pme-2025]]¹, [[faceless-content-accounts-2026]]

¹ Stub — conteúdo completo em `Wiki/sources/` (repo `dima visual claude`).

## 03 - Resources/entities

[[Chetan Pujari]], [[Kiran Grewal]], [[Ryan Frizelle]], [[MAIS AI Agency]]¹

¹ Stub — conteúdo completo em `Wiki/entities/MAIS-AI-Agency.md` (repo `dima visual claude`).

---

## 04 - Archive

*Tabela gerada ao vivo por Dataview a partir do frontmatter (`title`/`tags`) de cada nota.*

```dataview
TABLE tags AS "Tags"
FROM "04 - Archive"
SORT file.name ASC
```

Relatórios de lint pré-2026-06-09 (ficheiros brutos, não notas): `04 - Archive/wiki-meta/lint-report-2026-06-08.md`, `...08b.md`.

---

## 06 - Fleeting

*Tabela gerada ao vivo por Dataview a partir do frontmatter (`title`/`date`) de cada nota.*

```dataview
TABLE date AS "Data"
FROM "06 - Fleeting"
SORT date DESC
```

---

## Meta

- `_meta/AGENTS.md` — instruções para o Claude operar este vault
- `_meta/CLAUDE.md` — estrutura e quick reference
- `_meta/hot.md` — cache de contexto recente
- `_meta/log.md` — log append-only de operações
