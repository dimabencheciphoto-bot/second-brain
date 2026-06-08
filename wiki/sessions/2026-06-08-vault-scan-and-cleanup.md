---
type: session
title: "Vault Scan + Structural Cleanup"
created: 2026-06-08
updated: 2026-06-08
tags: [session, vault, cleanup, navigation, para]
status: done
related:
  - "[[Business Overview]]"
  - "[[UGC Pricing]]"
  - "[[Market Analysis]]"
  - "[[Overnight Engine]]"
  - "[[UGC Agency Launch]]"
---

# Session: Vault Scan + Structural Cleanup — 2026-06-08

## Diagnóstico do vault

Scan completo ao Second Brain. Problemas identificados:

| Problema | Severidade | Fix |
|----------|-----------|-----|
| Pricing UGC em dois sítios com valores diferentes | 🔴 Crítico | Single source of truth → [[UGC Pricing]] |
| `04 - Archive/` referenciada mas não existia | 🔴 Crítico | Criada; [[Second Brain Cleanup]] movido para lá |
| 3 ficheiros stray em `06 - Fleeting/` | 🟡 Médio | Apagados |
| Dashboard "Foco Atual" estático e stale | 🟡 Médio | Substituído por Dataview tasks query |
| AI Development.md com placeholders `← nota a criar` | 🟢 Baixo | Substituídos por wikilinks reais |

## Consolidação de navegação

**Problema:** 10+ ficheiros de mapa/índice para 60 notas. `wiki/domains/` duplicava exactamente o PARA.

**Fix:** Eliminar `wiki/domains/` (4 ficheiros) e migrar conteúdo útil para os MOCs PARA correspondentes:

| Domain eliminado | Conteúdo migrado para |
|------------------|-----------------------|
| `wiki/domains/business/` | [[Business Overview]] |
| `wiki/domains/markets-finance/` | [[Market Analysis]] |
| `wiki/domains/content-ugc/` | [[Overnight Engine]] (já tinha tudo) |
| `wiki/domains/ai-automation/` | [[_MOC Resources]] |

**Regra estabelecida:**
- **PARA (`01-04/`)** = estado de execução (o que estás a fazer agora)
- **`wiki/`** = conhecimento processado (concepts, research, sources)

## Ficheiros de navegação finais (de 10+ para 5)

| Ficheiro | Para quê |
|----------|----------|
| `Dashboard.md` | Entrada principal |
| `_MOC Projects.md` | Projectos activos |
| `_MOC Areas.md` | Responsabilidades contínuas |
| `_MOC Resources.md` | Conhecimento de referência |
| `wiki/index.md` | Concepts, research, sources, sessions |

## Commits

| Hash | Descrição |
|------|-----------|
| `08c56e2` | vault cleanup: fix pricing, create archive, clean fleeting, fix placeholders |
| `2c2792f` | consolidate navigation: remove wiki/domains/, merge into PARA MOCs |
