---
type: area
title: "Viralto — Organização de Ficheiros do Workspace"
created: 2026-07-07
updated: 2026-07-07
tags: [viralto, organizacao, workspace]
related:
  - "[[Viralto - Agência AI]]"
---

# Viralto — Organização de Ficheiros do Workspace

## Workspace VS Code

`DIMA.code-workspace` revertido em 2026-07-07 para lista plana alfabética (comportamento standard do VS Code) — sem secções decorativas nem emojis. Tinha existido uma versão agrupada por categorias (PROJECTOS / CLIENTES & CONTEÚDO / OUTRAS CATEGORIAS) entre 2026-06-14 e 2026-07-07, mas o utilizador preferiu voltar ao "convencional".

## Índice de trabalhos de clientes

Criado `viralto/clientes.md` — uma tabela que lista os projectos entregues a clientes (Tendas e Eventos, OsteoJP, configs UGC), com links para as pastas reais. Decisão: **não mover** as pastas físicas dos projectos para dentro de `viralto/`, porque isso arriscava partir deploys (Vercel), git e paths hardcoded em scripts (ex: `content_factory/config.py`). Um índice/manifesto dá a visão consolidada sem esse risco.

`portfolio-casamento/` e `portfolio-deploy/` são explicitamente pessoais, não trabalho de cliente — marcados como tal no índice para não gerar confusão.

---

> Ver também `viralto/clientes.md` no repositório do projecto para a tabela actualizada.
