---
title: "Second Brain Index"
updated: 2026-08-25
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

### 01 - Projects/Engine Runs
Runs diárias do overnight engine: `2026-06-10` a `2026-06-14`, `2026-07-04`.

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

[[src-ugc-agency-blueprint]], [[src-ugc-cold-email-guide]], [[src-ugc-pricing-2025]], [[src-claude-prompts-10-every-day]], [[src-claude-prompts-50-steal]], [[src-automate-instagram-carousels]], [[ciela-ai-agency-niches-2026]]¹, [[prr-ia-nas-pme-2025]]¹

¹ Stub — conteúdo completo em `Wiki/sources/` (repo `dima visual claude`).

## 03 - Resources/entities

[[Chetan Pujari]], [[Kiran Grewal]], [[Ryan Frizelle]], [[MAIS AI Agency]]¹

¹ Stub — conteúdo completo em `Wiki/entities/MAIS-AI-Agency.md` (repo `dima visual claude`).

---

## 04 - Archive

| Note | Tópico |
|------|--------|
| [[Claude Skills Inventory]] | Inventário de skills Claude Code — desactualizado desde 2026-06-09, ver aviso na nota |
| [[Market Analysis]] | Análise de mercado arquivada |
| [[Micro-Agência de Conteúdo — Estado 2026-06-11]] | Estado do projecto micro-agência de conteúdo |
| [[Research - Viralto UGC Agency Setup]] | Setup original Viralto UGC (pré-pivot para AI) |
| [[UGC Agency Launch]] | Launch da agência UGC |
| [[_MOC Projects]] | Map of Content — projectos arquivados |
| [[reciba-ai-fiscal-inbox]] | Nota arquivada sobre recibos/fiscal |
| [[lint-report-2026-06-09]] | Relatório de lint do vault, 2026-06-09 |
| `wiki-meta/lint-report-2026-06-08.md`, `...08b.md` | Relatórios de lint anteriores à reorganização de 2026-06-09 |

---

## 06 - Fleeting

| Note | Tópico |
|------|--------|
| [[session-agente-ugc-2026-07-02]] | Sessão de trabalho no agente de prospecção UGC |
| [[agente-ugc-2026-07-03]] | Continuação do agente de prospecção UGC |
| [[session-ugc-engine-2026-07-03]] | Sessão engine + UGC |

---

## Meta

- `_meta/AGENTS.md` — instruções para o Claude operar este vault
- `_meta/CLAUDE.md` — estrutura e quick reference
- `_meta/hot.md` — cache de contexto recente
- `_meta/log.md` — log append-only de operações
