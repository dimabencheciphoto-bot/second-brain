---
type: meta
title: "Wiki Overview"
created: 2026-06-08
updated: 2026-06-08
tags: [meta, overview]
status: active
---

# Second Brain Wiki — Overview

**Purpose:** Knowledge base técnica de um AI automation builder a construir pipelines, agência UGC e sistemas de análise financeira em tempo real.

**Owner:** Dima  
**Mode:** Domain Wiki (Mode A — espelho técnico do vault PARA)  
**Vault:** `C:\Users\DIMA\Documents\Second Brain`

---

## O que existe aqui

Este vault documenta 4 sistemas activos:

### 1. Overnight Engine
Pipeline 100% automatizado: Reddit trends → script Claude → vídeo MP4 (PIL + edge-tts + moviepy) → publicação multi-plataforma (YouTube, Facebook, Instagram, TikTok) → Telegram summary → Obsidian note. Corre às 2AM via Task Scheduler.

→ [[content-ugc/_index]] · [[Overnight Engine]] · [[AI Patterns]]

### 2. Viralto (UGC Agency)
Sistema de outreach cold email para marcas e-commerce: prospect hunter → personalised emails (Haiku) → Gmail SMTP → deal tracker CSV. Nome da agência: **Viralto**.

→ [[business/_index]] · [[UGC Agency Launch]] · [[Prompt Engineering]]

### 3. Market Agent
Análise diária EUR/USD + índices globais + ETFs via yfinance + Claude Sonnet em português europeu. Output: HTML report + nota Obsidian.

→ [[markets-finance/_index]] · [[Market Agent]] · [[CPI Consumer Price Index]]

### 4. Musa 1.0
Projecto de aprendizagem do ecossistema Claude (7 módulos). Módulos 1-6 completos. Módulo 7 (Monetizar) em curso.

→ [[business/_index]] · [[Musa 1.0]]

---

## Stack Técnica

| Camada | Ferramentas |
|--------|-------------|
| LLM | Claude Sonnet 4.6 (análise), Haiku 4.5 (geração rápida), Opus 4.8 (raciocínio) |
| Interface | Claude Code CLI + VS Code extension + Telegram bot |
| Automação | Windows Task Scheduler + hooks Claude Code |
| Vídeo | PIL + edge-tts + moviepy v2 |
| Dados | yfinance, Playwright, Reddit JSON API |
| Vault | Obsidian PARA + claude-obsidian skill |

---

## Como usar este wiki

1. `wiki/hot.md` — contexto recente (500 palavras)
2. `wiki/index.md` — catálogo completo
3. `wiki/domains/[domínio]/_index.md` — drill-down por área
4. Páginas individuais — conceitos, comparações, perguntas respondidas
