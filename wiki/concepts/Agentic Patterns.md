---
type: concept
title: "Agentic Patterns"
created: 2026-06-08
updated: 2026-06-08
tags: [ai, agents, patterns, autonomous]
status: active
---

# Agentic Patterns

Patterns for building autonomous multi-step AI systems. Used in `autonomous_agent.py`, `project_agent.py`, real estate pipeline.

## Code-Execute-Autocorrect loop

Core pattern in `autonomous_agent.py`:

```python
while attempts < max_attempts:
    code = claude_generate(task, error_history)
    result = execute(code)
    if result.success:
        break
    error_history.append(result.error)
    # Claude sees its own error and self-corrects
```

## Tool use pattern

Give Claude a set of tools; it decides which to call:

```python
tools = [
    {"name": "search", "description": "Search the web", "input_schema": {...}},
    {"name": "write_file", "description": "Write to a file", "input_schema": {...}},
]
response = client.messages.create(model=..., tools=tools, messages=[...])

if response.stop_reason == "tool_use":
    tool_call = next(b for b in response.content if b.type == "tool_use")
    result = dispatch_tool(tool_call.name, tool_call.input)
    # Feed result back into messages
```

## Sub-agent pattern (project_agent.py)

Orchestrator decomposes task → spawns specialised sub-calls:

```
1. Planner call → list of files to create
2. For each file: Writer call → file content
3. Validator call → review and fix
```

## Pipeline agent (real estate)

Each agent is a module with a single `run(input) -> output` function. Orchestrator chains them:

```python
listings = scraper.run(config)
analysis = analyst.run(listings)
reporter.run(analysis)
```

## Memory between steps

Pass structured context forward explicitly — agents are stateless:

```python
context = {"topic": topic, "script": script, "video_path": path}
# Each stage receives and enriches context
```

## When to use Haiku vs Sonnet in agents

- **Haiku**: leaf tasks (generate one email, write one script section)
- **Sonnet**: planning, decomposition, validation
- **Opus**: architecture decisions, complex reasoning chains

## Related

- [[AI Patterns]] — foundational pipeline patterns
- [[Anthropic SDK]] — API calls
- [[Prompt Engineering]] — prompts for each agent role
