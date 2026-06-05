# 🤖 Claude Models — Referência Rápida

*Atualizado: 2026-06-05 | Fonte: Anthropic docs*

---

## Modelos Atuais (Família Claude 4.x)

| Model ID | Alias | Uso Ideal | Velocidade | Custo |
|----------|-------|-----------|-----------|-------|
| `claude-opus-4-8` | Opus 4.8 | Raciocínio complexo, código difícil | Lento | Alto |
| `claude-sonnet-4-6` | Sonnet 4.6 | Análise, geração de qualidade, tool use | Médio | Médio |
| `claude-haiku-4-5-20251001` | Haiku 4.5 | Volume alto, tasks simples, speed-critical | Rápido | Baixo |

---

## Regra de Ouro (este projeto)

```python
# Análise e raciocínio → Sonnet
model = "claude-sonnet-4-6"

# Volume, emails, scripts rápidos → Haiku
model = "claude-haiku-4-5-20251001"

# Problemas difíceis, arquitetura → Opus
model = "claude-opus-4-8"
```

---

## Context Windows

| Modelo | Context | Output máx |
|--------|---------|------------|
| Opus 4.8 | 200k tokens | 32k |
| Sonnet 4.6 | 200k tokens | 16k |
| Haiku 4.5 | 200k tokens | 8k |

---

## Features Importantes

- **Extended Thinking** — disponível em Opus e Sonnet; ativa raciocínio interno
- **Tool Use** — todos os modelos suportam function calling
- **Prompt Caching** — reduz custo em prompts repetidos longos (prefixes)
- **Batch API** — 50% desconto para tasks não urgentes

---

## Padrão de uso (MonitoredAnthropic)

```python
import sys
sys.path.insert(0, r"C:\Users\DIMA\Documents\Dima Claude")
from token_monitor import MonitoredAnthropic

client = MonitoredAnthropic()
response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=2048,
    messages=[{"role": "user", "content": "..."}]
)
```

---

## Ver também

- [[Model Comparison]] — benchmarks e casos práticos
- [[Cost Optimization]] — estratégias de redução de custo
- [[Prompt Library]] — prompts testados por modelo
