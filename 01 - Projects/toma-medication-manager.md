---
tags:
  - project
  - startup
  - ai
  - silver-economy
  - elder-care
created: 2026-06-10
status: spec-approved
source: Claude Code brainstorming session
---

# Toma — gestor de medicação com IA para famílias com pais idosos

> [!info] Estado
> Spec aprovada e committed em 2026-06-10 (`docs/superpowers/specs/2026-06-10-toma-design.md`, commit `a2a99ba`, repo dima visual claude). Próximo passo: plano de implementação (skill writing-plans) → MVP.
> Substituiu o [[reciba-ai-fiscal-inbox|Reciba]] como projeto ativo; o Reciba fica parqueado.

## A aposta (porquê 10–20 anos)

- **Silver economy + IA** = a tendência demográfica mais certa a 20 anos no mundo lusófono: Portugal entre os países mais envelhecidos da Europa; Brasil com 33M+ pessoas 60+ (~BRL 2 biliões/ano), a caminho da 5.ª maior população idosa do mundo
- A não-adesão à medicação é uma dor concreta, diária e mensurável
- Concorrentes PT/BR (Sanii, Cuid) são marketplaces de cuidadores — **ninguém é dono do loop diário de medicação entre o idoso e a família que vive longe** (emigrantes = cliente core)
- Wedge: dominar o loop da medicação; expandir depois para check-ins diários, resumos de consultas, relatórios de cuidadoras, WhatsApp

## Produto (MVP)

Um bot de Telegram, dois papéis ligados por código de convite:

**Lado da família (cliente):**
1. Fotografa a receita médica / guia de tratamento ou as caixas → Claude vision extrai `{medicamento, dose, frequência, horários}` com confiança por campo → **nada ativa sem confirmação da família**
2. Digest diário ("A mãe tomou 3/3 medicamentos hoje ✅") + alertas imediatos quando uma toma não é confirmada

**Lado do idoso:**
3. À hora marcada, lembrete em português simples com dois botões grandes: **✅ Tomei** / **⏰ Mais tarde** — um toque, zero escrita
4. Escalada conservadora: re-pergunta após 30 min, no máximo 2×, depois alerta a família (nunca mais de 3 contactos por toma)

**Fora do MVP:** stock/refills, farmácias, chamadas de voz, WhatsApp, vários idosos por conta, conselhos médicos (nunca — guardrail fixo).

## Arquitetura

Pasta `toma/` no workspace dima visual claude:

```
Telegram Bot API (polling, python-telegram-bot)
   └─ bot.py — router por papel de chat (família vs idoso)
        ├─ prescription_reader.py — Claude Sonnet vision → JSON + confiança
        ├─ schedule.py — SQLite (famílias, idosos, medicamentos, tomas)
        ├─ scheduler.py — APScheduler: lembretes + máquina de estados de escalada
        └─ digest.py — resumo diário (template, sem API)
```

- `MonitoredAnthropic` em tudo; Sonnet só na extração — custo de operação quase zero
- Horários no fuso do idoso (família pode estar noutro país)
- Token do bot em `.env` (`TOMA_TELEGRAM_TOKEN`)

## Ordem de construção

1. `prescription_reader.py` isolado — de-riscar a extração primeiro (a maior incerteza)
2. `schedule.py` + testes unitários
3. `bot.py` — onboarding, ligação, foto → horário confirmado (primeira demo end-to-end)
4. `scheduler.py` — lembretes, botões, escalada
5. `digest.py` + guardrails + textos PT
6. Teste real de uma semana com a própria família

**Sucesso da experiência** = fotografar uma caixa real, confirmar o horário, receber o lembrete numa segunda conta Telegram, tocar "Tomei" e vê-lo no digest da família.

## Alternativas rejeitadas

- Confirmação pela família/cuidadora em vez do idoso (dados em segunda mão)
- Lembretes por chamada de voz/Twilio (adiado, MVP mais pesado)
- Entrada manual de horários (sem diferenciação — a foto é o momento mágico)
- Outras wedges do brainstorm: check-in diário, timeline de notas de voz de saúde, companion de consultas, navegador de apoios, concierge de crise, memory keeper

## Fontes

- [Silver economy no Brasil — Agência Brasil](https://agenciabrasil.ebc.com.br/en/economia/noticia/2026-04/silver-economy-reveals-power-consumers-entrepreneurs-60)
- [Sanii levanta US$2.35M para plataforma de cuidados com IA no Brasil](https://www.latamrepublic.com/sanii-raises-us-2-35m-led-by-sororite-ventures-to-expand-its-ai-powered-platform-in-brazil/)
- [Silver Economy Market Size 2026–2035](https://www.businessresearchinsights.com/market-reports/silver-economy-market-119281)
- [Activant Global Mega Trends 2026](https://activantcapital.com/research/global-mega-trends-2026)
