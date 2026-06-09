---
tags:
  - ai/models
  - config
created: 2026-06-09
---

# AI Models Inventory

## Active Models (dima visual claude workspace)

| Model | ID | Used For | Cost Tier |
|-------|-----|----------|-----------|
| **Claude Sonnet 4-6** | `claude-sonnet-4-6` | Analysis, main chat, market analysis | Balanced |
| **Claude Haiku 4-5** | `claude-haiku-4-5-20251001` | Speed-sensitive generation (cold emails, video scripts, UGC) | Cheapest |
| **Claude Opus 4-8** | `claude-opus-4-8` | Complex reasoning | Most expensive |

**New (2026-06-09):** [[Claude Fable 5]] (`claude-fable-5`, $10/$50 per 1M) — Mythos-class frontier model, not yet used in pipelines; see note for benchmarks and when it's worth it.

**All API calls** go through `MonitoredAnnotated` wrapper from `C:\Users\DIMA\Documents\Dima Claude\token_monitor.py` for automatic token/cost tracking.

## Dashboard-Costed Models (not necessarily active)

The dashboard (`dashboard/server.py`) tracks costs for these model IDs:

- `claude-opus-4-7` (previous Opus, compatibility)
- Plus the 3 active models above

## Configured but Inactive (free-claude-code/)

Separate git repo at `free-claude-code/` with its own CLAUDE.md. Providers configured but **not integrated** into any production pipeline:

| Provider | Config Fields | Status |
|----------|-------------|--------|
| **DeepSeek** | `DEEPSEEK_API_KEY` | Configured, not used |
| **llama.cpp** | `LLAMACPP_BASE_URL` | Local inference, configured |
| **Ollama** | `OLLAMA_BASE_URL` | Local inference, configured |

## Summary

100% of active pipelines (Overnight Engine, UGC Agency, Market Agent, Real Estate Agent) use **Claude models only** via the Anthropic API. The free-claude-code/ experiment has alternative providers wired up but zero usage in production.
