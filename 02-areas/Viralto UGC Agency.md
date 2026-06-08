---
title: "Viralto UGC Agency"
date: 2026-06-09
tags: [area, ugc, viralto]
status: active
related: ["[[UGC Agency Business Model]]", "[[UGC Cold Outreach]]", "[[UGC Pricing]]", "[[UGC Portfolio]]"]
---

# Viralto UGC Agency

## Purpose
Agência UGC portuguesa/europeia para marcas e-commerce. Nome: **Viralto**. Modelo: spec videos → cold outreach → clientes recorrentes.

## Standard
Pipeline de outreach activo, pelo menos 1 cliente activo, portfolio online visível.

## Current State (2026-06-09)

Nome decidido: **Viralto**

**Pendente (por ordem de prioridade):**
1. Filmar spec videos (1-2 nichos: Beauty/Wellness + Tech)
2. Criar portfolio no Carrd (viralto.carrd.co ou similar)
3. Registar viralto.com (verificar disponibilidade)
4. Lançar batch de cold outreach (20+ marcas)
5. Primeiro cliente → contrato simples → entregar

## Pricing (entrada)

| Tier | Preço | Inclui |
|------|-------|--------|
| Por vídeo | €40-80 | Entrada / testes |
| Starter Pack | €250-300 | 3 vídeos UGC |
| Growth | €450-500 | 6 vídeos UGC |
| Retainer | €350/mês | 4 vídeos/mês (recorrente) |

**Multiplicadores:** Usage rights +30-50% · Rush delivery +25-50%

→ Detalhes completos: [[UGC Pricing]]

## Target Brands
- DTC Beauty/Wellness (Shopify)
- Marcas PT/EU com presença Instagram/TikTok
- Orçamento marketing €1k-10k/mês

## Pipeline Tools
- `ugc_system/prospect_hunter.py` — encontra marcas via Claude
- `ugc_system/cold_outreach.py` — email cold personalized (Haiku)
- `ugc_system/nightly_outreach.py` — envio automático Gmail SMTP
- `ugc_system/deal_tracker.py` — CRM flat-file CSV

## Key Resources
- [[Research - Viralto UGC Agency Setup]] — research completo (01-projects/)
- [[UGC Agency Business Model]] — modelo de negócio detalhado
- [[UGC Cold Outreach]] — sequência emails 3-step
- [[UGC Portfolio]] — como construir portfolio sem clientes
- [[UGC Pricing]] — tabela de preços PT/EU

## Notes
- 2026-06-08: autoresearch completo via /autoresearch skill
- Cold email 3-step: primeiro email curto + follow-up + último
- Sem clientes iniciais: spec videos para nichos target como portfolio
