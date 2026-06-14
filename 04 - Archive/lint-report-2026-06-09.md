---
title: "Lint Report 2026-06-09"
type: meta
created: 2026-06-09
updated: 2026-06-09
tags: [meta, lint]
status: completed
---

# Lint Report: 2026-06-09

## Summary

- Pages scanned: 33 markdown files
- Dead links found: 7 (in active files) + ~20 (in archive, ignorados)
- Frontmatter gaps: 4 ficheiros sem `title:`
- Orphan pages: 0
- Auto-fixed: 11 issues
- Needs review: 0

---

## Issues Fixed (auto)

### Dead Links → Active Files

| Link | Ficheiro | Correcção |
|------|---------|-----------|
| `[[UGC Agency Launch]]` | UGC Agency Business Model.md | → `[[Viralto UGC Agency]]` |
| `[[UGC Agency Launch]]` | UGC Cold Outreach.md | → `[[Viralto UGC Agency]]` |
| `[[UGC Agency Launch]]` | UGC Portfolio.md | → `[[Viralto UGC Agency]]` |
| `[[UGC Agency Launch]]` | UGC Pricing.md | → `[[Viralto UGC Agency]]` |
| `[[UGC Agency Launch]]` | Research - Viralto UGC Agency Setup.md | → `[[Viralto UGC Agency]]` |
| `[[Prompt Library]]` | UGC Cold Outreach.md | → `[[AGENTS]]` (prompts via AGENTS.md) |
| `[[entities/_index]]` | index.md | → texto sem wikilink (múltiplos `_index.md`) |

### Frontmatter `title:` adicionado

- UGC Agency Business Model.md
- UGC Cold Outreach.md
- UGC Portfolio.md
- UGC Pricing.md

---

## Dead Links em Archive (ignorados — histórico)

Os ficheiros em `04-archive/wiki-meta/` referenciam estruturas antigas (01-Projects, 06-Fleeting, Engine Runs, etc.). São registos históricos — não corrigir.

---

## Template Placeholders (OK)

Links `[[Note Name]]`, `[[Related Note]]`, `[[Link 1]]`, `[[Link 2]]`, `[[Relevant Concept]]`, `[[Related Project]]` existem nos ficheiros de templates e em exemplos do AGENTS.md. São placeholders intencionais — não são dead links reais.

---

## DragonScale / Semantic Tiling

Não configurado. Scripts `scripts/allocate-address.sh` e `scripts/tiling-check.py` não existem. Checks skipped (opt-in feature).

---

## Estado pós-lint

Vault limpo. Sem dead links em ficheiros activos. Frontmatter completo. Zero orphans.
