---
type: concept
title: "Prompt Engineering"
created: 2026-06-08
updated: 2026-06-08
tags: [ai, prompting, claude, patterns]
status: active
---

# Prompt Engineering

Patterns for getting reliable, structured output from Claude across all pipelines.

## JSON output (most common pattern)

Always ask for JSON in a code block. Use `parse_claude_json()` to handle markdown fences:

```python
prompt = """
Analyse this and return JSON:
{"field": "value", ...}
Return ONLY valid JSON in a ```json block.
"""
```

## Structured output template

```python
prompt = f"""
You are [role]. 

Input: {data}

Return JSON with this exact schema:
{{
  "title": "string",
  "points": ["string"],
  "score": 0-10
}}

Rules:
- [constraint 1]
- [constraint 2]
Return ONLY the JSON, no explanation.
"""
```

## System prompt separation

```python
client.messages.create(
    model=model,
    system="You are a cold email copywriter specializing in UGC...",
    messages=[{"role": "user", "content": user_prompt}]
)
```

## Haiku vs Sonnet decision

| Task | Model | Reason |
|------|-------|--------|
| Cold emails, video scripts | Haiku | Speed + cost; creative, not analytical |
| Market analysis, research | Sonnet | Depth matters |
| Complex multi-step reasoning | Opus | When cost justified |

## Few-shot examples

For consistent formatting (overnight engine script_writer), include 1-2 examples in the prompt body:

```
Example output:
{"title": "5 AI Tools That Replace Entire Teams", "hook": "Most people don't know..."}

Now generate for: {topic}
```

## Temperature

Not exposed directly in `messages.create` — Claude manages this. For more creative output use longer, more open prompts. For deterministic JSON use tight schemas with "ONLY return JSON" constraints.

## Related

- [[Anthropic SDK]] — how prompts are sent
- [[Cost Optimization]] — prompt length vs cost tradeoff
- [[Agentic Patterns]] — prompts in multi-step loops
