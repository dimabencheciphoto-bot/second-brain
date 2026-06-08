---
title: "AI Development"
date: 2026-06-09
tags: [area, ai-dev]
status: active
related: ["[[Anthropic SDK]]", "[[AI Patterns]]", "[[Agentic Patterns]]"]
---

# AI Development

## Purpose
Construção e manutenção de pipelines de automação com IA — sistema de conteúdo, análise financeira, agentes autónomos.

## Standard
Todos os pipelines activos correm sem intervenção manual. Código limpo, MonitoredAnthropic em todo o lado, logs funcionam.

## Active Pipelines

### Overnight Engine
Pipeline 100% automatizado: Reddit trends → script Claude → MP4 (PIL + edge-tts + moviepy) → YouTube/Facebook/Instagram/TikTok → Telegram summary → Obsidian note. Corre às 2AM via Task Scheduler.

**Estado:** Código completo. Falta `.env` com credenciais (YouTube OAuth + TikTok API).  
**Path:** `C:\Users\DIMA\Documents\dima visual claude\overnight_engine\`

→ [[AI Patterns]] · [[MoviePy v2 Patterns]]

### Market Agent
Análise diária EUR/USD + índices globais + ETFs via yfinance + Claude Sonnet PT-EU. Output: HTML report + nota Obsidian.

**Estado:** Activo.  
**Path:** `C:\Users\DIMA\Documents\dima visual claude\scripts\market_agent.py`

→ [[CPI Consumer Price Index]]

### Real Estate Agent
Scraper Idealista.pt → análise Claude Haiku → HTML report.

**Estado:** Funcional.  
**Path:** `C:\Users\DIMA\Documents\dima visual claude\scripts\main.py`

→ [[Playwright Guide]]

### Dashboard
UI local: token costs + system stats + engine activity feed. Porta 7842.

**Estado:** Funcional.  
**Path:** `C:\Users\DIMA\Documents\dima visual claude\dashboard\`

## Key Resources
- [[Anthropic SDK]] — MonitoredAnthropic, modelos, streaming
- [[AI Patterns]] — pipeline, fetch→analyse→report, fallback lists
- [[Agentic Patterns]] — loops, tool use, sub-agents
- [[Prompt Engineering]] — JSON output, few-shot, Haiku vs Sonnet
- [[Cost Optimization]] — pricing, token discipline

## Stack
| Camada | Ferramentas |
|--------|-------------|
| LLM | Haiku 4.5 (geração) · Sonnet 4.6 (análise) · Opus 4.8 (raciocínio) |
| Automação | Windows Task Scheduler + Claude Code hooks |
| Vídeo | PIL + edge-tts + moviepy v2 |
| Dados | yfinance, Playwright, Reddit JSON API |
| Interface | Claude Code CLI + VS Code + Telegram bot |

## Pending
- [ ] Overnight Engine: configurar `.env` (YouTube OAuth, TikTok API)
- [ ] GitHub auth: `gh auth login` em dima visual claude
