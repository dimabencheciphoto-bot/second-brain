---
type: session
title: "Skills + Wiki Obsidian Setup"
created: 2026-06-08
updated: 2026-06-08
tags: [session, skills, obsidian, wiki, viralto]
status: developing
related:
  - "[[Research - Viralto UGC Agency Setup]]"
  - "[[UGC Agency Launch]]"
  - "[[Overnight Engine]]"
  - "[[Musa 1.0]]"
  - "[[UGC Cold Outreach]]"
  - "[[UGC Pricing]]"
  - "[[UGC Portfolio]]"
  - "[[UGC Agency Business Model]]"
---

# Session: Skills + Wiki Obsidian Setup — 2026-06-08

## O que foi feito

### 1. Skills instalados

| Skill | Fonte | Installs | Uso |
|-------|-------|----------|-----|
| `youtube-automation` | claude-office-skills | 2.8K | Automação de workflow YouTube |
| `claude-obsidian` (15 skills) | AgriciDaniel/claude-obsidian | — | Wiki + Second Brain management |

**Skills claude-obsidian disponíveis:**
- `/wiki` — scaffold + router principal
- `/wiki-lint` — health check do vault (orphans, dead links, frontmatter)
- `/wiki-ingest` — ingerir documentos em `.raw/` e sintetizar
- `/wiki-query` — query do vault com contexto acumulado
- `/autoresearch` — research autónomo em 3 rondas → wiki
- `/save` — guardar contexto de sessão no vault
- `/think` — framework de decisão 10 princípios
- `/defuddle` — simplificar texto/conceito
- `/canvas` — layer visual (imagens, PDFs, canvas Obsidian)
- `/obsidian-markdown`, `/obsidian-bases` — referências de sintaxe

### 2. Vault lint — 26 issues corrigidos

Primeiro `/wiki-lint` do vault. Issues encontrados e corrigidos:

**Prioridade alta (corrigido):**
- 4 stubs criados: [[Anthropic SDK]], [[MoviePy v2 Patterns]], [[Playwright Guide]], [[Prompt Engineering]]
- Frontmatter corrigido: [[Market Agent]], [[Musa 1.0]], [[Overnight Engine]], [[UGC Agency Launch]]
- Engine Runs ligadas ao [[Overnight Engine]] via tabela

**Prioridade média (corrigido):**
- [[Second Brain Cleanup]] e carousel adicionados ao `_MOC Projects`
- Placeholders de template identificados como falsos positivos (dentro de code blocks)

**Prioridade baixa (corrigido):**
- `CPI-consumer-price-index.md` renomeado para [[CPI Consumer Price Index]] (Title Case)
- 3 wikilinks actualizados: `_MOC Resources`, `Market Agent`, `Fleeting/2026-06-07`

### 3. Wiki layer scaffolded

Wiki layer criado sobre o vault PARA existente em modo **Generic**:

```
wiki/
├── index.md, log.md, hot.md, overview.md
├── domains/
│   ├── ai-automation/_index.md
│   ├── markets-finance/_index.md
│   ├── content-ugc/_index.md
│   └── business/_index.md
├── concepts/_index.md (8 conceitos)
├── entities/_index.md
├── sources/, questions/, sessions/, comparisons/
└── meta/ (lint reports)
```

**CLAUDE.md criado** no vault root com instruções para cross-project referencing.

### 4. Autoresearch — Viralto UGC Agency Setup

Research de 2 rondas (7 searches). Páginas criadas:
- [[Research - Viralto UGC Agency Setup]] — síntese com plano de acção semanal
- [[UGC Agency Business Model]] — modelo intermediário + margem 30-50%
- [[UGC Cold Outreach]] — sequência 3 emails / 10 dias
- [[UGC Portfolio]] — spec content sem clientes, Carrd recomendado
- [[UGC Pricing]] — €40-80/vídeo entrada, pacotes Starter/Growth/Retainer

### 5. Wiki mode configurado

Modo **Generic** confirmado (default). PARA seria redundante com a estrutura do vault principal. Sem `mode.json` criado — absence = generic.

---

## Decisões tomadas

| Decisão | Racional |
|---------|---------|
| Wiki mode: Generic | PARA duplicaria estrutura do vault principal |
| Portfolio Viralto: Carrd | Simplicidade, look profissional, ~€19/ano |
| Pricing entrada: €40-80/vídeo | Mercado PT/EU = -15-20% sobre USD |
| Target inicial: Beauty/Wellness DTC | Maior RPM, mais abertos a testar |
| Outreach: cold email directo + plataformas | Plataformas para primeiros 3 clientes, depois directo |

---

## Open Questions activas

- `viralto.com` disponível? Verificar antes de avançar outreach
- Contrato simples para primeiros clientes (usage rights, revisões, entrega)
- Pricing ajustado PT/EU vs USD com dados reais do mercado europeu

---

## Próximos passos Viralto

1. Filmar 3-5 spec videos (skincare/wellness com produtos próprios)
2. Criar Carrd page: bio + 3 vídeos + 2 pacotes + contacto
3. Registar viralto.com + handles @viralto
4. Identificar 20-30 brands DTC Beauty/Wellness no Instagram/Shopify
5. Lançar Email 1 personalizado com sinal específico

---

## Commits desta sessão

| Repo | Hash | Descrição |
|------|------|-----------|
| second-brain | fbefa86 | wiki scaffold + vault lint |
| second-brain | bd621c6 | autoresearch Viralto + concepts + lint 2nd pass |
| dima visual claude | 3fc4729 | reorganise scripts/ + skills + overnight_engine |
