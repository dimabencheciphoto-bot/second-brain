---
type: session
title: "Micro-Agência de Conteúdo — Estado 2026-06-11"
created: 2026-06-11
updated: 2026-06-11
tags:
  - micro-agencia
  - prospecao
  - freelance
status: active
---

# Micro-Agência de Conteúdo Social — Estado a 11/06/2026

Negócio de gestão de conteúdo visual para pequenos negócios PT, operado a solo com as ferramentas de automação do workspace `dima visual claude`. Objectivo: 1 cliente pagante em 2–4 semanas; 4–5 clientes (€1.000–1.400/mês) aos 3 meses.

## Pacotes (mercado PT 2026)

| Pacote | Incluído | Preço/mês |
|--------|----------|-----------|
| Básico | 8 posts (1 rede) | €150 |
| Standard | 12 posts + 4 reels | €280 |
| Pro | 16 posts + 8 reels + copy | €480 |

Entrada: 2 carrosséis de exemplo grátis → prova de 2 semanas → pacote mensal.

## Sistema construído (6 tasks, todas concluídas)

- `ugc_system/client_config.py` — config de branding por cliente (JSON em `clients/`)
- `scripts/carousels/client_carousel.py` — carrosséis PIL adaptados ao branding
- `scripts/generate_monthly_content.py` — um comando gera o mês inteiro de um cliente
- `ugc_system/cold_outreach.py` → `generate_social_media_outreach()` — emails PT-PT via Haiku
- `ugc_system/social_outreach_batch.py` — batch a partir de `leads_social_media.csv`
- 3 clientes demo + 15 carrosséis em `generated_carousels/`

## Primeiro batch de prospeção (feito hoje)

- Google Maps scraper: 6 restaurantes + 15 ginásios de Lisboa → `ugc_system/output/deals.csv` (CRM)
- 13 leads qualificados (cadeias grandes excluídas) em `ugc_system/leads_social_media.csv`
- 13 emails + follow-ups gerados: `ugc_system/output/outreach/social_outreach_20260611_1549.md`

## Próximos passos (manuais)

1. **Verificar o Instagram de cada lead** — o campo `last_post_weeks=4` é placeholder; corrigir antes de enviar ou o email queima o lead
2. Encontrar emails de contacto (scraper só apanhou telefones/websites)
3. Registar no Zaask e Fixando com os carrosséis demo como portfólio
4. Acompanhar: `python ugc_system/deal_tracker.py --list`
5. Fase 2 (produto Gumroad) só após 1 cliente pagante

## Referências

- Spec: `docs/superpowers/specs/2026-06-11-micro-agencia-conteudo-design.md`
- Plano: `docs/superpowers/plans/2026-06-11-micro-agencia-conteudo.md`
- Commits: 9b0927c, bc50a5b, 7813d68, 0e1f914, d88d2b1, 241b88c, 2de8f69
