---
title: "Agente UGC — Sessão 2026-07-03"
date: 2026-07-03
tags: [ugc, fleeting, session]
---

# Agente UGC — Sessão 2026-07-03

## O que é

Agente interactivo de prospecção UGC em `ugc_system/agente_ugc.py`. Loop Claude com 4 ferramentas encadeadas:

1. **pesquisar_marca** — Google Search + scrape da marca
2. **qualificar_marca** — score 1-10 com Haiku (mín. 7 para aprovação)
3. **adicionar_pipeline** — adiciona ao `deals.csv`
4. **gerar_email** — gera outreach completo (email + LinkedIn DM + follow-ups) em `ugc_system/output/outreach/`

Envia resumo Telegram no fim da sessão.

## Bugs corrigidos

| Bug | Causa | Solução |
|-----|-------|---------|
| `ModuleNotFoundError: token_monitor` | Ficheiro não existia | Criado stub em `C:\Users\DIMA\Documents\Dima Claude\token_monitor.py` |
| `ModuleNotFoundError: utils` | Pasta chamava-se `Utils` (maiúscula); Python import é case-sensitive | Renomeada `Utils` → `utils` |
| `ModuleNotFoundError: utils` (persistia) | `Path(__file__).parent.parent` devolvia `"."` relativo | Corrigido para `.resolve().parent.parent` |

## Para correr

```powershell
cd "C:\Users\DIMA\Documents\dima visual claude"
python ugc_system/agente_ugc.py
```

O agente pergunta o nicho, depois pede marcas uma a uma. Diz `fim` para terminar a sessão.
