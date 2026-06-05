# 📚 Prompt Library

> Prompts testados, prontos a copiar. Documentar o que funciona.

---

## Como usar esta biblioteca

1. Copia o prompt
2. Substitui `{{variável}}` pelo valor real
3. Se melhorares → atualiza aqui
4. Regista o modelo que deu melhor resultado

---

## 🎯 Prompts de Análise

### Análise de Tendências (Overnight Engine)
**Modelo:** Haiku | **Testado:** ✅
```
Analisa estes tópicos de Reddit sobre {{niche}}:

{{topics_json}}

Classifica por potencial viral (1-10) considerando:
- Relevância atual
- Apelo emocional
- Originalidade do ângulo

Responde em JSON: [{title, score, angle, hook}]
```

---

### Análise de Mercado (EUR/USD + ETFs)
**Modelo:** Sonnet | **Testado:** ✅
```
És um analista financeiro experiente. Analisa os seguintes dados:

EURUSD: {{price_data}}
ETFs Europeus: {{etf_data}}

Fornece:
1. Tendência principal (bull/bear/lateral)
2. Níveis chave de suporte/resistência  
3. 3 insights acionáveis para investidor de longo prazo
4. Risco principal a monitorar

Formato: HTML estruturado com secções claras.
```

---

## ✍️ Prompts de Geração de Conteúdo

### Script UGC (Video)
**Modelo:** Haiku | **Testado:** ✅
```
Cria um script UGC de 30-45 segundos para {{brand}}.

Produto: {{product_description}}
Tom: autêntico, conversacional, não parece anúncio
Estrutura: hook (3s) → problema → solução → prova → CTA

Output JSON:
{
  "hook": "...",
  "body": "...",
  "cta": "...",
  "b_roll_suggestions": [...]
}
```

---

### Cold Email Personalizado
**Modelo:** Haiku | **Testado:** ✅
```
Escreve um cold email para {{brand_name}} ({{niche}}).

Observação específica sobre a marca: {{observation}}
Meu serviço: criação de vídeos UGC autênticos
Objetivo: reunião de 15 minutos

Regras:
- Máximo 5 frases
- Primeira frase não começa com "I" ou "Eu"  
- Menciona a observação específica naturalmente
- CTA claro mas sem pressão

Assunto (3 opções) + corpo do email.
```

---

## 🔍 Prompts de Extração / Estruturação

### Extrair Dados de Listings (Imobiliário)
**Modelo:** Haiku | **Testado:** ✅
```
Extrai informação estruturada deste listing imobiliário:

{{raw_text}}

Output JSON:
{
  "price": number,
  "area_m2": number,
  "rooms": number,
  "location": string,
  "highlights": [string],
  "red_flags": [string],
  "value_score": 1-10
}

Se informação não disponível → null.
```

---

### Resumo de Paper de AI
**Modelo:** Sonnet | **Testado:** ⬜
```
Lê este paper de AI e cria um resumo para programador experiente:

{{paper_abstract_or_sections}}

Formato:
## TL;DR (2 frases)
## Contribuição Principal
## Como funciona (técnico, sem simplificar demais)
## Limitações
## Aplicar no meu trabalho: {{my_context}}
```

---

## 🤖 Prompts de Sistema (Agentes)

### System Prompt — Agente Generalista
**Modelo:** Sonnet/Opus
```
És um assistente técnico especializado em {{domain}}.

Sempre que receberes uma task:
1. Confirma o que foi pedido em 1 frase
2. Lista o teu plano antes de executar
3. Executa step by step
4. Verifica o resultado contra o objetivo original

Quando incerto → pergunta antes de assumir.
Output em {{format}}.
```

---

## 📊 Avaliação de Prompts

| Prompt | Modelo | Score (1-5) | Data | Notas |
|--------|--------|-------------|------|-------|
| Análise Tendências | Haiku | 4 | 2026-06-05 | Bom mas às vezes genérico |
| Cold Email | Haiku | 5 | 2026-06-05 | Excelente resultado |

---

## Ver também

- [[Agentic Patterns]] — prompts para sistemas multi-agente
- [[Prompt Engineering]] — teoria por detrás
