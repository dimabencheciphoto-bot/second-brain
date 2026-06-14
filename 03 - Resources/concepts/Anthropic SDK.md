---
type: concept
title: "Anthropic SDK"
created: 2026-06-08
updated: 2026-06-08
tags: [ai, anthropic, sdk, python, api]
status: active
---

# Anthropic SDK

Python client library for the Claude API. All projects use `MonitoredAnthropic` wrapper (from `Dima Claude/token_monitor.py`) instead of `anthropic.Anthropic()` directly — this records token usage automatically.

## Setup

```python
import sys
sys.path.insert(0, r"C:\Users\DIMA\Documents\Dima Claude")
from token_monitor import MonitoredAnthropic

client = MonitoredAnthropic()
```

## Models in use

| Model | ID | Use case |
|-------|----|----------|
| Sonnet 4.6 | `claude-sonnet-4-6` | Analysis, complex tasks |
| Haiku 4.5 | `claude-haiku-4-5-20251001` | Speed-sensitive: cold emails, scripts |
| Opus 4.8 | `claude-opus-4-8` | Complex reasoning |

## Basic call

```python
response = client.messages.create(
    model="claude-haiku-4-5-20251001",
    max_tokens=1024,
    messages=[{"role": "user", "content": "your prompt"}]
)
text = response.content[0].text
```

## JSON output pattern

Wrap prompt in `parse_claude_json()` from `utils/claude_json.py` — strips markdown fences before `json.loads()`.

## Streaming

```python
with client.messages.stream(model=..., max_tokens=..., messages=[...]) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

## Key limits

- Context window: 200k tokens (Sonnet/Opus), 200k (Haiku)
- Max output: 8192 tokens default, up to 64k with extended thinking
- Rate limits vary by tier

## Related

- [[Cost Optimization]] — token cost management
- [[Prompt Engineering]] — prompt patterns
- [[Agentic Patterns]] — multi-step agent loops
