# 💰 Cost Optimization — Reduzir Custo com Claude API

---

## Regra 1: Modelo Certo para a Task Certa

Ver [[Model Comparison]]. Haiku custa ~20× menos que Opus. Usar Haiku em tasks de volume.

---

## Regra 2: Prompt Caching

```python
# Activar cache no system prompt (>1024 tokens = elegível)
system=[{
    "type": "text",
    "text": long_system_prompt,
    "cache_control": {"type": "ephemeral"}  # TTL: 5 min
}]
```

**Impacto:** tokens cacheados custam ~10% do preço normal.  
**Quando usar:** mesmo system prompt em muitas chamadas seguidas.

---

## Regra 3: Batch API

```python
# Para tasks não-urgentes: 50% desconto
import anthropic
client = anthropic.Anthropic()

batch = client.beta.messages.batches.create(
    requests=[
        {"custom_id": f"req-{i}", "params": {"model": "...", "messages": [...]}}
        for i in range(100)
    ]
)
# Resultado disponível em ~1h
```

**Quando usar:** processamento de muitos items onde latência não importa.

---

## Regra 4: Controlar max_tokens

```python
# Não deixar o modelo gerar mais do que precisas
max_tokens=512   # Cold emails
max_tokens=1024  # Scripts UGC
max_tokens=2048  # Análise de mercado
max_tokens=4096  # Só se mesmo necessário
```

---

## Regra 5: Monitorar com token_monitor

```python
from token_monitor import MonitoredAnthropic
client = MonitoredAnthropic()  # Regista uso automaticamente
```

**Ficheiro:** `C:\Users\DIMA\Documents\Dima Claude\token_monitor.py`

---

## Estimativa de Custo por Pipeline

| Pipeline | Modelo | Tokens médios | Custo est. |
|---------|--------|--------------|------------|
| Overnight engine/noite | Haiku | ~3k | ~$0.002 |
| Cold email batch (20) | Haiku | ~5k | ~$0.003 |
| Market analysis | Sonnet | ~4k | ~$0.05 |
| Imobiliário (20 listings) | Haiku | ~6k | ~$0.004 |

---

## Ver também

- [[Claude Models]] — pricing por modelo
- [[Agentic Patterns]] — evitar loops desnecessários
