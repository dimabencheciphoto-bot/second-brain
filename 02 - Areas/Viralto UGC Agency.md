---
title: "Viralto — Agência AI"
date: 2026-06-30
tags: [area, viralto, agencia-ai, pivot]
status: active
related: ["[[Research - Viralto AI Agency Pivot 2026]]", "[[AI-Automation-Agency]]"]
---

# Viralto — Agência AI

> ⚠️ **Pivot em curso (2026-06-29):** A Viralto já não é uma agência UGC. Está a ser transformada em agência AI para o mercado PT/EU.

---

## Decisão de Pivot

**De:** agência UGC para e-commerce (spec videos + cold outreach)
**Para:** agência AI de automação para PMEs portuguesas

**Razão:** UGC requer produção contínua e tem margem baixa. Mercado AI em PT tem estruturalmente aberto (8% PMEs com IA adoptada, meta UE 75% até 2030). Margem agência AI: 60-80% com < €100/mês de infra.

---

## Recomendação de Nicho (pesquisa 2026-06-29)

**Nicho 1 (recomendado):** Recepcionista IA por voz/WhatsApp para clínicas e negócios locais
- Alvos: dental, estética, fisioterapia, salões, ginásios
- Dor quantificada: clínica com 30 chamadas/dia perde ~€5.000/mês se perder 10
- Mercado PT fragmentado — sem player dominante (VoiceFleet €99/mês é o mais próximo)
- Preço de entrada: €99-300/mês
- Stack necessário: pode exigir ElevenLabs/Twilio/Vapi (a validar)

**Nicho 2 (reserva se nicho 1 não fechar em 60 dias):** Automação de leads/WhatsApp para imobiliárias sobre CRMs existentes (C2S, Imobilead, WAX)

**O que NÃO fazer:** posicionamento horizontal A+B+C (automação marketing + sistemas AI + conteúdo AI para todos os sectores) — já ocupado pela [[MAIS AI Agency]] em PT.

---

## Alternativas Exploradas (opção A do brainstorming)

1. **Automação leads imobiliárias** — TAM grande, mais saturado de ferramentas; abertura está na camada AI sobre CRMs existentes
2. **Automação e-commerce/DTC** — menor fricção porque há rede existente da fase UGC; vender automação em vez de UGC às mesmas marcas
3. **Jurídico (implementação)** — advIA existe como SaaS mas ninguém vende implementação como agência; tickets altos, mercado menor em PT
4. **Contabilidade** — hipótese não validada

---

## Estado do Brainstorming

- Skill `/brainstorming` activa, fase: clarificação
- Apresentadas recomendação principal + alternativas (opção A)
- Próximo passo ao retomar: utilizador decide entre aprofundar e-commerce/DTC ou manter foco em recepção por voz → depois: propor 2-3 abordagens → design doc → `/writing-plans`

---

## Stack Actual (Viralto/herdado do UGC)

| Componente | Ferramenta | Serve para voz? |
|---|---|---|
| LLM | claude-haiku-4-5-20251001 | Sim (scripts/respostas texto) |
| Automação | Make.com + ugc_system | Parcialmente |
| Outreach | Gmail SMTP | Sim |
| Voz | — | Não — precisa ElevenLabs/Twilio/Vapi |

---

## Open Questions

- Stack de voz: ElevenLabs + Twilio + Vapi ou alternativa mais barata?
- Preço PT: €99/mês (VoiceFleet) é tecto ou piso para clínicas/salões?
- PRR "IA nas PME" 2025 fechou — verificar ronda 2026 antes de usar em vendas
- Contabilidade PT: genuinamente sub-servida ou baixa visibilidade?

---

## Referências

- [[Research - Viralto Nicho AI Portugal 2026]] — síntese completa wiki
- [[MAIS AI Agency]] — concorrente PT a diferenciar
- [[ciela-ai-agency-niches-2026]] — 12 nichos globais rentáveis
- [[prr-ia-nas-pme-2025]] — financiamento PT (janela 2025 fechada)

---

## Histórico

- 2026-06-29: decisão de pivot UGC → AI; autoresearch concluída; brainstorming iniciado
- 2026-06-09: fase UGC — nome Viralto decidido; pendente filmar spec videos (arquivado)
