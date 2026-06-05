# ⚖️ Model Comparison — Decisão Prática

> Quando não sabes qual modelo usar, lê isto primeiro.

---

## Árvore de Decisão

```
Preciso de velocidade máxima + custo baixo?
  └─ SIM → Haiku 4.5
  └─ NÃO → É um problema difícil / multi-step reasoning?
              └─ SIM → Opus 4.8
              └─ NÃO → Sonnet 4.6 ✅ (default)
```

---

## Casos Práticos

| Task | Modelo | Porquê |
|------|--------|--------|
| Cold email (batch) | Haiku | Volume, template-like, rápido |
| Video script UGC | Haiku | Criativo mas não complexo |
| Análise de mercado | Sonnet | Qualidade + custo razoável |
| Scrape + análise imóveis | Haiku | 20 listings, task clara |
| Arquitectura de sistema | Opus | Raciocínio profundo necessário |
| Code review complexo | Opus | Bugs subtis, contexto grande |
| Trend scout + ranking | Sonnet | Julgamento + nuance |
| Telegram summary | Haiku | Formatação simples |

---

## Experiências Pessoais

| Data | Task | Modelo testado | Resultado | Notas |
|------|------|---------------|-----------|-------|
| — | — | — | — | — |

---

## Regra Anti-Overengineering

> Começa sempre com Haiku. Sobe para Sonnet se a qualidade não chegar. Opus é o último recurso.
