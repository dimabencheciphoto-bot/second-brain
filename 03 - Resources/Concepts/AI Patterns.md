# 🏗️ AI Patterns — Padrões Arquiteturais

> Padrões reutilizáveis para sistemas de AI. Copiar, adaptar, não reinventar.

---

## 1. Pipeline Linear

```
Input → Step1 → Step2 → Step3 → Output
```

**Quando usar:** tasks sequenciais onde cada step depende do anterior.  
**Exemplo:** `trend_scout → script_writer → video_builder → publisher`  
**Cuidado:** sem paralelismo; erro num step para tudo.

---

## 2. Fan-Out / Fan-In

```
Input → [Worker1, Worker2, Worker3] → Aggregator → Output
```

**Quando usar:** processar N items independentes em paralelo.  
**Exemplo:** processar 20 listings imobiliários em paralelo com `asyncio.gather`.  
**Implementação:**
```python
import asyncio

async def process_all(items):
    tasks = [process_one(item) for item in items]
    results = await asyncio.gather(*tasks, return_exceptions=True)
    return [r for r in results if not isinstance(r, Exception)]
```

---

## 3. Agentic Loop (ReAct)

```
[Thought → Action → Observation] × N → Final Answer
```

**Quando usar:** tasks abertas onde o modelo decide os próximos steps.  
**Exemplo:** agente de pesquisa que navega na web autonomamente.  
**Cuidado:** definir `max_iterations` para evitar loops infinitos.

---

## 4. Structured Output

```python
# Sempre pedir JSON com schema explícito
prompt = """
Responde APENAS com JSON válido:
{
  "field1": "...",
  "field2": 0,
  "field3": ["..."]
}
"""

import json
raw = client.messages.create(...).content[0].text
data = json.loads(raw.strip().lstrip("```json").rstrip("```"))
```

**Quando usar:** sempre que precisas de parsear o output programaticamente.

---

## 5. Fallback Chain

```python
models = ["claude-haiku-4-5-20251001", "claude-sonnet-4-6"]

for model in models:
    try:
        result = call_claude(model, prompt)
        if quality_check(result):
            break
    except Exception:
        continue
```

**Quando usar:** sistemas de produção onde disponibilidade > custo.

---

## 6. Prompt Caching

```python
# Cache o system prompt longo (>1024 tokens)
response = client.messages.create(
    model="claude-sonnet-4-6",
    system=[{
        "type": "text",
        "text": long_system_prompt,
        "cache_control": {"type": "ephemeral"}
    }],
    messages=[{"role": "user", "content": user_msg}]
)
```

**Quando usar:** system prompts longos repetidos em muitas chamadas. Reduz custo ~90% no input cacheado.

---

## 7. Classificador → Especialista

```
Input → Classifier (Haiku) → Router → Specialist Agent (Sonnet/Opus)
```

**Quando usar:** inputs variados que precisam de handling diferente.  
**Exemplo:** classificar intent do utilizador antes de invocar o agente certo.

---

## 8. Self-Critique Loop

```python
draft = generate(prompt)
critique = evaluate(draft, rubric)
if critique["score"] < threshold:
    final = refine(draft, critique["feedback"])
else:
    final = draft
```

**Quando usar:** outputs onde qualidade é crítica (emails, copy, análise).

---

## Ver também

- [[Agentic Patterns]] — multi-agent específico
- [[Prompt Library]] — prompts para cada padrão
- [[Overnight Engine]] — pipeline linear em produção
