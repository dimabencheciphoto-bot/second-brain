---
type: concept
status: seed
tags: [ai, anthropic, sdk, python]
created: 2026-06-08
updated: 2026-06-08
---

# Anthropic SDK

SDK Python oficial para aceder à API Claude da Anthropic.

## Instalação

```bash
pip install anthropic
```

## Uso básico

```python
import anthropic
client = anthropic.Anthropic()
message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello"}]
)
```

## Neste projecto

Usado via `MonitoredAnthropic` (wrapper em `Dima Claude/token_monitor.py`) para tracking automático de custos.

## Ver também

- [[Claude Models]] — modelos disponíveis
- [[Cost Optimization]] — controlo de custos
- [[AI Patterns]] — padrões de uso
