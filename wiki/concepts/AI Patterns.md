---
type: concept
title: "AI Patterns"
created: 2026-06-08
updated: 2026-06-08
tags: [ai, patterns, architecture, python]
status: active
---

# AI Patterns

Recurring architectural patterns across all pipelines in `dima visual claude`.

## Pipeline pattern (overnight engine)

Sequential stages, each independently skippable:

```
scout → writer → builder → publishers → reporter → vault
```

Each stage returns structured data or raises a skippable exception. Missing env vars skip a publisher without crashing the pipeline.

## Fetch → Analyse → Report

Used by market agent and real estate agent:

```python
data = fetch(source)           # yfinance, Playwright
analysis = claude_analyse(data) # Claude Haiku/Sonnet
report = render_html(analysis)  # jinja2 or f-string HTML
```

## Claude JSON loop

```python
raw = client.messages.create(...).content[0].text
result = parse_claude_json(raw)  # strips fences, raises ValueError on bad JSON
```

Always validate the schema after parsing — Claude occasionally omits fields under load.

## Fallback lists

When external APIs fail, fall back to curated static lists:

```python
# trend_scout.py
topics = fetch_reddit_trends() or EVERGREEN_TOPICS
```

## Env var gating

```python
import os
if not os.getenv("YOUTUBE_CLIENT_ID"):
    logger.warning("YouTube creds missing — skipping")
    return {"status": "skipped"}
```

## Rate limiting / retry

```python
import time

for attempt in range(3):
    try:
        result = api_call()
        break
    except RateLimitError:
        time.sleep(2 ** attempt)
```

## Token counting before call

For long-context calls, estimate tokens before sending:
```python
# Rough: 1 token ≈ 4 chars
estimated = len(prompt) // 4
if estimated > 100_000:
    prompt = truncate(prompt, 100_000 * 4)
```

## Related

- [[Agentic Patterns]] — multi-step agent loops
- [[Anthropic SDK]] — API client
- [[Prompt Engineering]] — prompt design
- [[Cost Optimization]] — keeping costs low
