---
tags:
  - project
  - startup
  - ai
  - fiscal
created: 2026-06-10
status: parked
source: Claude Code brainstorming session
---

# Reciba — AI fiscal inbox for Portuguese freelancers

> [!info] Estado
> Parqueado em 2026-06-10 — o projeto ativo passou a ser o [[toma-medication-manager|Toma]] (gestor de medicação, silver economy). O design do Reciba mantém-se válido para retomar mais tarde.

## A aposta (porquê 10–20 anos)

- Obrigações de **e-faturação e SAF-T** em Portugal continuam a expandir — forcing function regulatória
- Adoção de IA na contabilidade PT saltou de <30% para 74% em três anos
- Incumbentes (Cegid, Tally, Moloni) vendem a empresas com contabilistas; os **~800k+ trabalhadores independentes** que fazem o próprio IRS/IVA estão mal servidos
- Wedge: ser o sítio onde os documentos financeiros do freelancer aterram; expandir depois para declarações, previsão e WhatsApp

### Contexto da pesquisa de mercado

Megatendências mais fortes a 10–20 anos: IA, longevidade/silver economy, transição energética. Alternativas consideradas e rejeitadas:
1. **Copiloto familiar de cuidados a idosos** (silver economy PT/BR) — forte demografia, mas perdeu na escolha
2. **Copiloto de transição energética** (tarifas/subsídios) — tailwind forte mas dependente de política volátil

## Produto (âmbito do MVP)

Bot de Telegram onde um freelancer:
1. **Reencaminha recibo/fatura** (foto ou PDF) → Claude extrai fornecedor, data, valor, taxa de IVA e categoriza segundo categorias de despesa portuguesas (dedutível vs não)
2. **Faz perguntas em PT** — "quanto gastei em despesas dedutíveis este trimestre?"
3. **Recebe resumo mensal** — totais por categoria, IVA liquidado vs dedutível, formatado para a declaração trimestral de IVA

**Fora do âmbito do MVP:** integração e-fatura/AT, pagamentos, multi-utilizador, WhatsApp, submissão de declarações.

## Arquitetura

Pasta nova `reciba/` no workspace `dima visual claude`:

```
Telegram Bot API (polling)
   └─ bot.py — router de mensagens (foto / PDF / pergunta)
        ├─ extractor.py — Claude vision → JSON estruturado (padrão utils/claude_json.py)
        ├─ ledger.py — SQLite (documentos, campos extraídos, categorias)
        ├─ advisor.py — Claude + contexto do ledger responde a perguntas fiscais PT (com disclaimer)
        └─ reports.py — gerador de resumos mensais/trimestrais
```

- `MonitoredAnthropic` em todas as chamadas; **Sonnet** para extração (vision), **Haiku** para chat
- SQLite, um ficheiro — zero infra para MVP

## Confiança e erros

- Extração devolve flag de confiança; baixa confiança → bot pede confirmação em vez de guardar silenciosamente
- Disclaimer permanente nas respostas fiscais; nunca submete nada automaticamente
- Documentos não parseáveis ficam guardados em raw e marcados, nunca descartados

## Critérios de sucesso

- Testes unitários para regras de categorização e matemática do IVA (determinísticos, sem API)
- Fixture de ~10 recibos/faturas PT de exemplo → verificação de precisão de extração
- **Sucesso da experiência** = reencaminhar 5 recibos reais, perguntar "resumo do mês" e obter resposta correta e útil

## Fontes

- [Activant Global Mega Trends 2026](https://activantcapital.com/research/global-mega-trends-2026)
- [Portugal 2025 Digital Decade Country Report](https://digital-strategy.ec.europa.eu/en/factpages/portugal-2025-digital-decade-country-report)
- [AI in Accounting Portugal 2026](https://www.fedfinance.pt/en/news/ai-in-accounting-portugal-2026-the-complete-guide-to-skills-salaries-and-tools)
- [Tally launches AI accounting agent for SMEs in Portugal](https://portugalstartupnews.com/2026/03/21/tally-launches-ai-accounting-agent-with-human-oversight-for-smes-in-portugal/)
- [Silver economy no Brasil — Agência Brasil](https://agenciabrasil.ebc.com.br/en/economia/noticia/2026-04/silver-economy-reveals-power-consumers-entrepreneurs-60)
