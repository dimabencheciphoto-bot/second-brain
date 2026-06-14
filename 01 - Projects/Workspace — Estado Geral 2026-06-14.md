---
tags: [workspace, overview, sistemas, estado]
created: 2026-06-14
status: activo
---

# Workspace — Estado Geral (2026-06-14)

Visão geral de todos os sistemas e projectos activos em `Documents\dima visual claude\`. Stack principal: Python + Anthropic API (`MonitoredAnthropic`), Next.js, Playwright, PIL.

---

## 1. Micro-Agência de Conteúdo Social

**Estado: ACTIVO — lead quente em curso**

Negócio solo de gestão de redes sociais para PME portuguesas. Pacotes €150/€280/€480/mês.

- **Lead quente:** @its.raquelsilva (Raquel | Skincare & Lifestyle, 1.110 seguidores) — respondeu "Sim estou interessada" a 2026-06-11
- Config em `clients/its-raquelsilva.json`; 2 carrosséis de exemplo em `generated_carousels/its-raquelsilva/2026-06-11/`
- **Próximo passo:** enviar exemplos à Raquel + fechar pacote
- Follow-ups dos outros leads: a partir de 2026-06-14
- 5 leads qualificados em `ugc_system/leads_qualificados.csv`

**Pipeline técnico:** `client_config.py` → `client_carousel.py` → `generate_monthly_content.py` → `social_outreach_batch.py`

Ver nota detalhada: [[Micro-Agência de Conteúdo — Estado 2026-06-11]]

---

## 2. Site Tendas e Eventos

**Estado: IMPLEMENTADO — pendente deploy**

Site `tendaseeventos.com` em Next.js 16.2.9 + Tailwind v4. Servidor dev em `http://localhost:3000`.

**Páginas completas:** `/` · `/servicos` · `/galeria` · `/sobre-nos` · `/faq` · `/contacto` · `/orcamento`

**Últimas melhorias (2026-06-14):**
- Header sem dropdown (sub-nav sticky na /servicos)
- Hero com `next/image` + `priority` (LCP optimizado)
- Secção Climatização adicionada
- Página contacto: mapa Google Maps, WhatsApp card, acessibilidade WAI-ARIA completa

**Pendentes:**
1. `vercel login` + `vercel --prod` (dentro de `tendas-eventos/`)
2. `RESEND_API_KEY` no `.env.local`
3. Domain verification no Resend

Ver nota detalhada: [[tendas-eventos-website-2026-06-14]]

---

## 3. Overnight Content Engine

**Estado: ACTIVO — corre diariamente às 2h via Task Scheduler**

Pipeline automático: Reddit/HN trends → script Claude Haiku → vídeo MP4 (TTS + PIL) → YouTube / Facebook / Instagram → Telegram summary → Obsidian vault.

- Entry: `overnight_engine/run_engine.py`
- Config: `overnight_engine/config.py` (niche: "AI tools and automation", voz: "en-US-GuyNeural")
- Logs: `overnight_engine/engine.log`
- **Testar manualmente:** `python overnight_engine/run_engine.py`

---

## 4. Startup Toma

**Estado: SPEC APROVADO — plano de implementação por escrever**

AI medication manager para famílias com pais idosos. Telegram bot + visão Claude para extrair horários de receitas.

- Spec: `docs/superpowers/specs/2026-06-10-toma-design.md` (commit a2a99ba)
- **Próximo passo:** `/writing-plans` com a spec → implementar `prescription_reader.py` primeiro
- Stack: `python-telegram-bot`, SQLite, APScheduler, MonitoredAnthropic, Claude Sonnet

Ver nota: [[toma-medication-manager]]

---

## 5. Startup Reciba

**Estado: PARKED — cedeu lugar ao Toma**

AI fiscal inbox bot para freelancers PT. Design aprovado 2026-06-10.
- Spec: `docs/superpowers/specs/2026-06-10-reciba-design.md`
- Não morto — pode retomar após Toma ganhar tração

---

## 6. UGC System (outreach B2B)

**Estado: ACTIVO — pipeline automatizado**

Prospeção de marcas e-commerce para parcerias UGC. Ferramentas:
- `ugc_system/prospect_hunter.py` — encontrar marcas
- `ugc_system/cold_outreach.py` — emails personalizados (batch mode)
- `ugc_system/nightly_outreach.py` — envio automático via Gmail SMTP
- `ugc_system/deal_tracker.py` — CRM flat-file CSV
- CRM: `ugc_system/pipeline.csv`

---

## 7. Market Agent

**Estado: ACTIVO — execução manual**

EUR/USD + ETFs europeus → análise Claude → HTML report + nota Obsidian.

- `python scripts/market_agent.py`
- Report: `data/reports/`

---

## 8. Dashboard JARVIS

**Estado: ACTIVO — acesso local**

UI web local que agrega: custos de tokens, stats do sistema (CPU/RAM/disco via psutil), feed do engine.log.

- `python dashboard/server.py` (porta 7842)
- Abrir `dashboard/index.html` no browser

---

## 9. Real Estate Agent

**Estado: DISPONÍVEL — execução manual**

Scraper Idealista.pt → análise Claude Haiku → HTML report.

- `python scripts/main.py --location lisboa --operation arrendar --pages 2`

---

## Stack & chaves

| Variável | Uso |
|---|---|
| `ANTHROPIC_API_KEY` | Todos os scripts Claude |
| `GMAIL_USER` / `GMAIL_APP_PASSWORD` | SMTP outreach (dimabencheciphoto@gmail.com) |
| `RESEND_API_KEY` | Formulários web (tendas-eventos) |
| `TELEGRAM_BOT_TOKEN` | Engine reports + Toma |
| Facebook / Instagram / YouTube tokens | Publishers overnight engine |

Modelos em uso: `claude-sonnet-4-6` (análise), `claude-haiku-4-5-20251001` (velocidade), `claude-opus-4-8` (raciocínio complexo).
