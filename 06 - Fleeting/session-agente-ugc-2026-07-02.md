---
title: "Sessão — Agente de Prospecção UGC"
date: 2026-07-02
tags: [ugc, fleeting, session]
---

# Sessão — Agente de Prospecção UGC
**Data:** 2026-07-02

## O que foi construído

Agente AI interactivo de prospecção UGC: `ugc_system/agente_ugc.py`

O agente conversa com o utilizador, pesquisa marcas na web via Google Search, qualifica-as com score 1-10 usando Claude Haiku, e para as que pontuam ≥7 adiciona ao pipeline CSV e gera email de outreach personalizado em PT.

## Arquitectura (tool_use API)

4 ferramentas:
- `pesquisar_marca` — Google + BeautifulSoup
- `qualificar_marca` — Claude Haiku → score + razão + observação
- `adicionar_pipeline` — guarda em deals.csv (guard score < 7)
- `gerar_email` — email PT + follow-ups → output/outreach/

Modelo: claude-haiku-4-5-20251001 para tudo.

## Ficheiros criados
- `ugc_system/agente_ugc.py`
- `tests/test_agente_ugc.py` (12 testes)
- `conftest.py` (stub token_monitor + Utils alias)

## Para usar
```powershell
python ugc_system/agente_ugc.py
```

## Aprendizagens técnicas
- Padrão `stop_reason == "tool_use"` para loop de agente
- DISPATCHER dict para routing de ferramentas
- Imports ao nível do módulo (não lazy) para serem patcháveis em testes
- `conftest.py` para stub de dependências externas ao projecto
