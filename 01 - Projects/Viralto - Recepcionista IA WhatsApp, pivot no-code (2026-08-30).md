---
title: "Viralto — Recepcionista IA WhatsApp: pivot para no-code e escolha de plataforma"
date: 2026-08-30
tags: [viralto, whatsapp, recepcionista-ia, automacao, landbot, n8n]
status: developing
area: ai-dev
related: ["Viralto - Agência AI", "Viralto - Semana 1-2 e posicionamento (2026-07-13)"]
summary: "Design da recepcionista IA fechado e versionado; Landbot revela-se pago (~100€/mês) para WhatsApp+IA; decisão de plataforma pendente"
---

# Viralto — Recepcionista IA WhatsApp: pivot para no-code (2026-08-30)

## Contexto

Continuação do trabalho da branch `viralto/wip-2026-08-30`, onde tinha sido criado um esqueleto **FastAPI + WhatsApp Cloud API** para a recepcionista IA (produto-âncora da fase de Automação da Viralto). O Dima disse "tenho Landbot" e decidiu-se abandonar o esqueleto custom e construir tudo em no-code.

Brainstorming clarificou uma decisão não óbvia: **o cliente-piloto é a própria Viralto**. O bot vive no WhatsApp da agência, qualifica prospects, explica a oferta em 3 fases (Presença / Automação / Crescimento), marca uma call de descoberta e passa a conversa ao Dima. Serve também de demo ao vivo do que a Viralto vende.

## O que foi construído (versionado na branch)

Pasta `viralto/whatsapp-agent/landbot/`:
- **`knowledge-base.md`** — persona + 3 fases + regras rígidas + 11 FAQ, para colar no bloco AI Agent
- **`telegram-handoff-payload.md`** — corpo exacto dos POST à Telegram Bot API (handoff + erro de bloco); token é secret, nunca em texto
- **`blocks-copypaste.md`** — texto pronto a colar de cada bloco por ordem de construção + definições do evento Google Calendar + cabeçalho da Sheet
- **`SETUP.md`** — 9 passos que só o Dima pode fazer (conta, número, evento, partilhar Sheet, secret) + scripts dos 7 testes de aceitação como mensagens prontas
- **`README.md`** — runbook de montagem

Spec: `docs/superpowers/specs/2026-08-30-viralto-whatsapp-landbot-design.md`
Plano: `docs/superpowers/plans/2026-08-30-viralto-whatsapp-landbot.md` (4 tasks, todos completos via subagent-driven-development em modo leve 1 redator + 1 revisor, já que os deliverables são Markdown e não código)

Google Sheet criada via conector: **"Viralto — Leads WhatsApp (Landbot)"** — 11 colunas (`timestamp, nome, whatsapp, sector, fase_interesse, dor, tem_site_redes, resultado, evento_gcal, motivo_handoff, transcript_url`).

Esqueleto FastAPI antigo marcado **ARQUIVADO** no seu README, mantido como referência: webhook (validação `X-Hub-Signature-256`, ACK, background), `meta.py`, `brain.py` (loop de agente com `MonitoredAnthropic`/Haiku + 3 ferramentas) e handoff Telegram funcionam. Stubs: agendamento (Cal.com, horários fixos), histórico e dedupe (em memória).

Regra de copy fixada para o bot: **nunca dá preços nem intervalos**, mesmo sob insistência — frase padrão *"Os valores dependem do que precisa — é isso que vemos na call de descoberta, sem compromisso."*

## O bloqueio: Landbot não é grátis para isto

Ao tentar ligar o número descobriu-se que:
- O plano gratuito da Landbot é só widget de site — **WhatsApp não está em nenhum plano grátis**
- O bloco **AI Agent** (o cérebro do desenho aprovado) só existe do **Pro (~100 €/mês)** para cima
- **Starter (~40 €/mês)** tem WhatsApp mas só fluxos com botões, sem IA

## Caminhos avaliados — decisão PENDENTE

| Caminho | Custo/mês | Esforço até 1º cliente | Infra |
|---|---|---|---|
| **Landbot Pro** | ~100 € + templates Meta | horas (montar blocos) | gerida pela Landbot |
| **n8n self-hosted** | ~0–5 € hosting + ~1–5 € Claude API | ~1 dia (refazer fluxo visual) | do Dima |
| **FastAPI (o esqueleto)** | igual ao n8n | 1–2 dias (falta construir clientes Google Calendar + Google Sheets) | do Dima |

"Grátis" não é 0 €: Meta Cloud API é grátis (1000 conversas/mês), mas o hosting precisa de processo sempre a correr (Render free adormece aos 15 min; Railway já não tem free) e cada mensagem gasta ≥1 chamada Haiku.

**n8n** é o "Landbot mas grátis": visual, community edition grátis, com nodes nativos de WhatsApp (Meta), AI Agent, Google Calendar, Google Sheets e HTTP (Telegram). Reaproveita todo o trabalho de design. Foi a minha recomendação.

## Migração do número (decidida)

O Dima escolheu (via pergunta explícita, ciente do trade-off) **migrar o número pessoal +351 961 274 850** — o de @dimabencheciphoto, clientes de fotografia — para a WhatsApp Business API. Consequência aceite: esse número **deixa de funcionar na app normal do WhatsApp** e passa a ser gerido pelo inbox da plataforma; o histórico não migra. Isto vale para qualquer caminho, porque a Cloud API exige sempre um número fora da app.

Não encontrou a opção "verificação em duas etapas" no WhatsApp em português. Combinou-se avançar na migração e só tratar do PIN de 6 dígitos se o Meta o pedir durante o Embedded Signup (se não pedir, é porque não estava activada).

## Próximo passo

O Dima escolhe a plataforma (Landbot Pro pago vs. n8n/FastAPI grátis com trabalho e manutenção próprios). Só depois se avança para a montagem e a migração do número.

Pós-lançamento: o Dima envia transcripts reais e a `knowledge-base.md` é afinada. Métrica-alvo do piloto: ≥ 40% das conversas terminam em call marcada ou handoff; 0 respostas erradas sobre a oferta em 2 semanas.
