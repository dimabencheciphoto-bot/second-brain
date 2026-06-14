---
title: "Carousel Generator"
date: 2026-06-09
tags: [tool, content, instagram]
status: active
area: ai-dev
source: manual
related: ["[[AI Patterns]]", "[[MoviePy v2 Patterns]]"]
---

# Carousel Generator

Gerador de carrosséis Instagram (1080×1350px, estilo editorial) via PIL.

**Path:** `C:\Users\DIMA\Documents\dima visual claude\scripts\carousel_generator.py`

## Usage

```powershell
# Preview no browser (HTML)
python scripts/carousel_generator.py

# Guardar PNGs
python scripts/carousel_generator.py --save
# Output: overnight_engine/output/carousel_*.png
```

**Keywords:** "guarda" → `--save` | "preview" → sem flags | "muda o slide X" → editar `slide_X()`

## Design System

- **Dimensões:** 1080×1350px (4:5 portrait Instagram)
- **Margem esq.:** M=160 (texto left-aligned)
- **Fonts:** Georgia Bold (headlines), Georgia (body), Arial Black (labels), Arial (body)

### 5 Temas de cor

| Tema | Hex | Uso |
|------|-----|-----|
| ORANGE | (210,72,38) | Slide 1 sempre |
| DARK | (14,16,26) | |
| CREAM | (245,241,230) | |
| NAVY | (18,28,72) | |
| FOREST | (20,58,44) | |

### Regras visuais
1. Slide 1 sempre ORANGE
2. Sem cores repetidas consecutivas
3. Todas as 5 cores aparecem (2x cada nos 10 slides) — pool balanceado com seed por dia
4. Cover: número grande em 190px + título em 96px inline ao lado

## Última Utilização
2026-06-08 — 10 slides "5 Claude Code commands you need to know", template @growithalex
