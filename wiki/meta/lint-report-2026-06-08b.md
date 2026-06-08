---
type: meta
title: "Lint Report 2026-06-08 (2nd run)"
created: 2026-06-08
updated: 2026-06-08
tags: [meta, lint]
status: done
---

# Lint Report: 2026-06-08 (2ª passagem)

## Summary
- Pages scanned: ~70 (vault completo + wiki layer novo)
- Issues reais encontrados: 1
- Auto-fixed: 1
- Falsos positivos identificados: 8

---

## Issue Real — Resolvido

### Source stubs em falta (MÉDIO)
A síntese `[[Research - Viralto UGC Agency Setup]]` referenciava 3 source pages que não existiam:
- `[[src-ugc-agency-blueprint]]` → **criado** em `wiki/sources/`
- `[[src-ugc-cold-email-guide]]` → **criado** em `wiki/sources/`
- `[[src-ugc-pricing-2025]]` → **criado** em `wiki/sources/`

---

## Falsos Positivos do Scanner (ignorar)

| Link flagado | Razão — falso positivo |
|---|---|
| `[[2026-06-05\|...]]` (x4) | Escape `\|` correcto em Obsidian para pipe dentro de tabela |
| `[[carousel-claude-code-2026-06-08\|...]]` | Idem — pipe em tabela |
| `[[ai-automation/_index]]` (x4) | Links com path — válidos em Obsidian |
| `[[Carousel Generator]]` | Extraído do lint-report-2026-06-08 como sugestão textual, não link real |
| `[[`\]\]` | Backtick em bloco de código, não link |
| `[[01 - Projects]]` | Tabela histórica em Second Brain Cleanup.md |
| `[[Nome da nota]]`, `[[nota completa se existir]]` | Dentro de blocos de código — documentação |
| Frontmatter gaps wiki/ | Bug scanner PowerShell com ficheiros LF no Windows — frontmatter existe |

---

## Estado do Vault

✅ **0 dead links reais**  
✅ **0 orphans no wiki layer**  
✅ **Frontmatter completo em todas as notas-chave**  
✅ **3 source stubs criados**  
✅ **Wiki layer totalmente funcional**

---

*Gerado por `/wiki-lint` — 2026-06-08 (2ª passagem)*
