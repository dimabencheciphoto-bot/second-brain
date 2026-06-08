---
type: concept
status: seed
tags: [ai, prompts, claude, técnica]
created: 2026-06-08
updated: 2026-06-08
---

# Prompt Engineering

Técnicas de escrita de prompts para Claude usadas neste projecto.

## Princípios gerais

- **JSON estruturado**: pedir output em JSON com schema definido → menos parsing errors
- **Exemplos no prompt**: 1-2 exemplos concretos melhoram muito a consistência
- **Português europeu**: especificar explicitamente no system prompt
- **Role + Task**: "És um analista de mercados. Analisa os seguintes dados..."

## Padrões em uso

### Script writer (Haiku)
Prompt estruturado com banco de 15 fórmulas de título SEO. Haiku preenche templates melhor do que inventa estruturas.

### Cold email (Haiku)
Personalização por variáveis: `{brand}`, `{niche}`, `{observation}`. Output JSON com `subject` + `body`.

### Market analysis (Sonnet)
4 pontos fixos: DXY macro, índices, ETFs, perspectiva PT/EU. Formato markdown para render directo em HTML.

## Ver também

- [[Prompt Library]] — biblioteca de prompts activos
- [[Claude Models]] — escolha de modelo por tarefa
- [[Cost Optimization]] — impacto do modelo no custo
