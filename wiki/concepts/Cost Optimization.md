---
type: concept
title: "Cost Optimization"
created: 2026-06-08
updated: 2026-06-08
tags: [ai, cost, tokens, optimization, anthropic]
status: active
---

# Cost Optimization

Keeping Claude API costs low across all pipelines. Tracked via `MonitoredAnthropic` → `~/.anthropic_usage.json` → Obsidian weekly summary.

## Model selection by cost

| Model | Input $/MTok | Output $/MTok | Use when |
|-------|-------------|--------------|----------|
| Haiku 4.5 | ~$0.80 | ~$4.00 | Bulk generation (emails, scripts, summaries) |
| Sonnet 4.6 | ~$3.00 | ~$15.00 | Analysis, complex structured output |
| Opus 4.8 | ~$15.00 | ~$75.00 | Only when genuinely needed |

> [!key-insight] Haiku for generation, Sonnet for analysis
> 90% of the overnight engine and UGC pipeline runs on Haiku. Sonnet only enters for market analysis and complex reasoning.

## Prompt compression

- Remove filler words from system prompts
- Use bullet lists instead of prose instructions
- Cap context passed to Claude: truncate long scraped pages to top 3000 chars
- For batch tasks, batch multiple items into one call when the schema allows

## Max tokens discipline

Set `max_tokens` to the minimum needed:
```python
# Cold email: 300 tokens max
# Video script: 800 tokens max
# Market analysis: 2000 tokens max
```

## Caching (prompt caching)

For repeated system prompts (overnight engine runs daily), Anthropic charges ~10% of normal input cost for cache hits. Automatically applies when the system prompt exceeds ~1024 tokens and stays stable.

## Token monitoring

```python
# ~/.anthropic_usage.json tracks all calls
# vault_tokens.py reads it weekly → Obsidian note
# dashboard/server.py shows live cost
```

## Cost per pipeline (rough estimates)

| Pipeline | Model | Tokens/run | Cost/run |
|----------|-------|-----------|----------|
| Overnight engine | Haiku | ~3k | ~$0.02 |
| Cold email (1 brand) | Haiku | ~600 | ~$0.003 |
| Market analysis | Sonnet | ~5k | ~$0.09 |
| Real estate (20 listings) | Haiku | ~4k | ~$0.02 |

## Related

- [[Anthropic SDK]] — MonitoredAnthropic wrapper
- [[AI Patterns]] — pipeline architecture
- [[Prompt Engineering]] — prompt length tradeoffs
