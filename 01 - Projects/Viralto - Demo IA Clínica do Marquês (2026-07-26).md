---
title: "Viralto — Demo IA Clínica do Marquês"
date: 2026-07-26
tags: [viralto, demo, ia, clinicas-dentarias]
status: active
area: ai-dev
related: ["[[Research - Viralto Nicho AI Portugal 2026]]", "[[Viralto - Semana 1-2 e posicionamento (2026-07-13)]]"]
---

## Contexto

Demo de assistente de IA para o lead real **Clínica Dentária do Marquês** (Marquês de Pombal, Lisboa, 4.9★, 827 avaliações Google), no âmbito da oferta Viralto para clínicas dentárias (`viralto/oferta/clinicas-dentarias/`).

## Estado (2026-07-26)

**Demo pronta e testada — chat com IA real 100% funcional.**

### Componentes construídos

- `demo.html` — página de demo com dados reais da clínica (serviços/preços, 8 especialistas da equipa, horários, contactos, financiamento até 48 meses a 0% juros).
- `base-conhecimento.md` — base de conhecimento estruturada, usada tanto no HTML como no system prompt do backend.
- Backend serverless na Vercel (`demo-chat-api/api/chat.js`) — recebe pergunta + histórico, injeta a base de conhecimento como system prompt, chama `claude-haiku-4-5-20251001`. Deploy: `https://demo-chat-api-indol.vercel.app/api/chat`.
- CRM (`crm-prospeccao.csv`) — lead marcado como `demo_pronto`.

### Decisão de arquitectura

O primeiro protótipo tinha chat estático (keyword-matching). Rejeitado por "demasiado básico" — optámos por function serverless + Claude Haiku em vez de alternativas mais simples, para ter respostas reais e não guionizadas.

### Bug encontrado e resolvido

O chat mostrava sempre mensagem de erro apesar do backend responder correctamente (200 + JSON válido). Causa: a variável `history` no JavaScript colidia com o objecto nativo `window.history` do browser (só leitura) — `history.push()` lançava excepção, apanhada pelo `catch`, que devolvia sempre o fallback de erro. Corrigido renomeando para `chatHistory`.

**Lição a reter:** evitar nomes de variáveis globais que colidam com propriedades nativas de `window` (`history`, `location`, `name`, `top`, `parent`, etc.) em qualquer JS solto (não-modular) no browser — falham silenciosamente em vez de dar erro óbvio.

Verificado ao vivo com Chrome DevTools: duas perguntas reais devolveram respostas correctas, em português limpo, sem markdown nem emojis.

## Próximos passos

1. Decidir hospedagem pública do `demo.html` (ex: GitHub Pages) para obter link partilhável.
2. Enviar a primeira mensagem de outreach real (`scripts-outreach.md`).
3. Se resultar, repetir o processo para os outros 14 leads já no CRM.

## Relacionado

- [[Research - Viralto Nicho AI Portugal 2026]]
- [[Viralto - Semana 1-2 e posicionamento (2026-07-13)]]
