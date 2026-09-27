---
title: "Viralto — Execução e Conteúdo"
date: 2026-08-31
tags: [viralto, projeto, execucao, conteudo, site, redes-sociais]
status: developing
summary: "Histórico de execução da Viralto: contas sociais, site, conteúdo IG, demo IA, whatsapp agent"
related: ["[[Viralto - Agência AI]]"]
---

# Viralto — Execução e Conteúdo

Consolida 11 notas de sessão soltas (2026-07-07 → 2026-08-31) sobre a execução operacional da Viralto — contas sociais, site, pipeline de conteúdo IG, demo de IA para leads, recepcionista WhatsApp. A estratégia/posicionamento de fundo fica em [[Viralto - Agência AI]] (Area); esta nota é o registo de "o que foi construído e o que está pendente".

## Estado actual (2026-08-31)

- **Site:** ao vivo em https://site-iota-gules-11.vercel.app, deploy directo por CLI (sem git remote/CI) — repetir `vercel --prod` publica imediatamente em produção, sem preview. Domínio próprio (`viralto.pt`) ainda não associado. Auditoria de conversão fechada (hierarquia CTAs corrigida, preços deliberadamente não mostrados).
- **Contas sociais:** Instagram (@viralto.ai) e Facebook activos e a publicar; LinkedIn com Company Page criada; TikTok (@viralto.ai) criado mas conversão para conta comercial pendente; YouTube (@viraltoai, handle corrigido) criado mas sem conteúdo.
- **Conteúdo IG:** vários carrosséis/reels/posts single produzidos (branch `viralto/wip-2026-08-30`, não commitados). `guião1` duplicado no feed, não corrigido. Sessão `data/ig_profile` não confirmada como @viralto.ai (leu como @anasau28 na última verificação) — **nunca houve publicação confirmada em @viralto.ai pelos scripts de automação**; publish continua bloqueado pelo auto-mode classifier, o Dima corre no terminal dele.
- **video-generator:** design do lote-03 (guiões 7-9) com decisão pendente entre blend C+F (aplicado a sério ao Hook 8) e Opção F pura (testada no Guião 7, reacção mais forte do Dima). `LogoBumper.tsx` (intro/outro) validado no Studio, não commitado nem renderizado.
- **Demo IA (Clínica do Marquês):** funcional, chat real com Claude Haiku, testado end-to-end. Falta hospedagem pública + outreach.
- **Recepcionista IA WhatsApp:** pivot para no-code decidido; Landbot revelou-se pago (~100€/mês) para WhatsApp+IA — decisão de plataforma (Landbot Pro vs n8n vs FastAPI custom) pendente. Migração do número pessoal +351 961 274 850 para a Cloud API decidida mas não executada.
- **Orçamento cliente-facing:** publicado como Artifact, IVA 23% confirmado, métodos de pagamento assumidos (MB Way/transferência/Multibanco, 50/50 setup) — a confirmar se o Dima quiser alterar.
- **Git:** repositório principal continua com grande volume de alterações não commitadas (site, video-generator, conteúdo IG); nenhum destes trabalhos foi commitado nesta fase.

## Pendentes

1. Decidir plataforma da recepcionista WhatsApp (Landbot Pro / n8n / FastAPI) e avançar migração do número.
2. Fechar decisão de design do lote-03 (C+F vs F pura) antes de publicar guiões 7-9.
3. Resolver a sessão IG (`--login` real para @viralto.ai) e publicar os posts/carrosséis já produzidos.
4. TikTok → conta comercial; YouTube → primeiro conteúdo; LinkedIn → confirmar publicação.
5. `guião1` duplicado no IG — decidir apagar ou deixar.
6. Domínio `viralto.pt` — associar ao site Vercel quando decidido.
7. Hospedar publicamente a demo da Clínica do Marquês e enviar outreach real.
8. Decidir sobre commit/push do volume de trabalho não versionado.

## Lições a reter

- **LinkedIn** exige conexões mínimas na conta pessoal para criar uma Company Page — usar sempre uma conta pessoal já estabelecida como administradora.
- **TikTok** bloqueia registos novos via browser desktop com verificação QR; criar como conta adicional dentro da app do telemóvel evita o bloqueio.
- **Nomes de variáveis JS que colidem com propriedades de `window`** (`history`, `location`, etc.) falham silenciosamente em scripts não-modulares — usar nomes distintos (`chatHistory`).
- **Vercel CLI publica o directório local independentemente do git** — confirmar sempre o estado antes de `vercel --prod`.
- **"Grátis" em automação no-code raramente inclui WhatsApp+IA** — validar o plano exacto antes de desenhar a solução (Landbot: só o Pro ~100€/mês tem AI Agent + WhatsApp).

---

## Histórico de sessões

### 2026-07-07 — Criação de contas sociais

Contas criadas nas 4 plataformas a partir do brand kit (`viralto/brand/social_profiles.md`). Handle final consistente: **@viralto.ai** (Instagram, TikTok). Instagram, Facebook, Meta Business Suite e LinkedIn concluídos; TikTok em progresso (bloqueado por verificação QR no browser, resolvido criando como conta adicional na app); YouTube ainda não iniciado. Email inicial: `viraltoagencia@gmail.com` (Gmail), a migrar depois para domínio próprio.

### 2026-07-13 — Semana 1/2 de conteúdo + posicionamento em discussão

Calendário de conteúdo Dia 1-7 e Dia 8-14 escrito (`semana1-plano-confianca.md`, `semana2-plano.md`). Pipeline `publish_reel.py` validado em dry-run; falta `--login` real e a landing page em viralto.pt (bloqueador). Pesquisa de concorrência (Meta Ad Library) esgotada — nenhum concorrente PT com anúncios activos. **Posicionamento em discussão:** o Dima queria alargar o âmbito além de "automação com IA" (sites, redes, CRM, faturação) — recomendação dada foi estruturar em fases (Presença → Automação → Crescimento) em vez de lista plana; decisão fechada depois em [[Viralto - Agência AI]].

### 2026-07-21 — Animação do logótipo

`LogoBumper.tsx` (Remotion, intro/outro) criado fiel ao spec de `logo_kit.py`. Coreografia refeita numa 2ª iteração após feedback "faz como um grande animador de logos": V construído por duas diagonais convergentes com flash de impacto, entrada com zoom-settle, selo com overshoot físico, wordmark em cascata letra a letra, saída assimétrica à entrada. Validado no Remotion Studio, não commitado nem renderizado para mp4.

### 2026-07-26 — Demo IA Clínica do Marquês

Demo de assistente IA para lead real (Clínica Dentária do Marquês, 4.9★/827 avaliações) — `demo.html` + `base-conhecimento.md` + backend serverless Vercel (`claude-haiku-4-5-20251001`). Rejeitado protótipo estático inicial por "demasiado básico" a favor de respostas reais via Haiku. Bug: variável `history` colidia com `window.history`, corrigido renomeando para `chatHistory`. Verificado ao vivo com Chrome DevTools. Pendente: hospedagem pública + outreach real.

### 2026-08-01 — Site landing page ao vivo

Site (`viralto/site`, Next.js + Tailwind v4 + framer-motion) publicado via `vercel --yes` a partir da pasta local, sem repositório git ligado — primeiro deploy tratado como produção automaticamente. Prova social ampliada (2→4 testemunhos placeholder) e FAQ reformulada (5→10 perguntas). Estado do git não resolvido: alterações desta sessão e de outros projectos continuam por commitar.

### 2026-08-02 — Auditoria final de conversão + deploy

Auditoria completa (desktop+mobile) focada em conversão. Hierarquia de CTAs corrigida (WhatsApp primário, Cal.com secundário — WhatsApp exige ~2 toques, Cal.com ~6 passos). Botão WhatsApp flutuante ganhou halo (`ring-4`) para não sobrepor conteúdo em mobile. Preço nos cards "As 3 fases": decisão explícita de não mostrar. Seta "voltar ao topo" recusada (competiria com o CTA final). `vercel --prod --yes` corrido, site confirmado ao vivo.

### 2026-08-02 — Orçamento cliente-facing e IVA

`viralto-orcamento.html` construído — página única (não slide-deck), reutiliza tokens visuais da marca. 3 pacotes por fase com preço de "vaga de lançamento" para os primeiros 3 clientes. IVA confirmado pelo Dima: regime normal, +23% (não isenção Art. 53º CIVA), nota explícita adicionada. Métodos de pagamento assumidos (MB Way/transferência/Multibanco, 50/50 setup) — sinalizado como assumpção, não facto confirmado. Publicado como Artifact.

### 2026-08-04 — Redesign visual do lote-03 (guiões 7-9)

6 direcções de design mockadas; Dima escolheu C (manchete/stamp, caps) e F (bloco sólido, split duotone). Blend C+F aplicado a sério ao Hook 8 (produção). Testados isoladamente (sem tocar produção): mockup de pesquisa Google, tratamento foto duotone/silhueta (placeholder — sem foto real do cliente), animação de pin de mapa. Sinal de preferência forte: ao rever a Opção F **pura** isolada, reacção "GOSTO MESMO DESTE ESTILO" — visualmente diferente do blend já aplicado ao Hook 8. Testada a Opção F pura num guião completo (`Guiao7FullTestF.tsx`, só localhost). **Decisão entre C+F e F pura ainda pendente** antes de fechar o lote-03; Guião 7 e 9 continuam com o design antigo.

### 2026-08-07 — Plano de publicação 10 dias + correcção YouTube

Calendário de 10 dias reconstruído por verificação real via Playwright (não assumida): Instagram com 9 publicações reais desde 3 Ago (`guião1` duplicado 2×, não corrigido); Facebook quase vazio; **YouTube handle documentado estava errado** (`@viralto` apontava para canal alheio "woodpunk") — corrigido para `@viraltoai` (canal correcto, zero conteúdo); TikTok bloqueado por captcha; LinkedIn sem sessão verificável. Plano publicado como Artifact navegável com tokens de marca reais.

### 2026-08-30 — Recepcionista IA WhatsApp: pivot para no-code

Esqueleto FastAPI+WhatsApp Cloud API abandonado a favor de no-code ("tenho Landbot"). Decisão não óbvia: **o cliente-piloto é a própria Viralto** — bot no WhatsApp da agência, qualifica prospects, explica a oferta em 3 fases, marca call, handoff ao Dima. Design completo versionado em `viralto/whatsapp-agent/landbot/` (knowledge-base, payloads Telegram, blocos copy-paste, SETUP.md, README). Google Sheet de leads criada via conector. Regra fixada: bot nunca dá preços, mesmo sob insistência. **Bloqueio descoberto:** Landbot só tem WhatsApp+AI Agent no plano Pro (~100€/mês) — Starter tem WhatsApp sem IA, gratuito não tem WhatsApp. 3 caminhos avaliados (Landbot Pro / n8n self-hosted / FastAPI custom) — n8n recomendado ("Landbot mas grátis"), decisão pendente do Dima. Migração do número pessoal +351 961 274 850 para a Cloud API decidida (consequência aceite: deixa de funcionar na app normal).

### 2026-08-31 — Posts single IG + publish_post.py

3 posts single (`gen_post_tarefa_40x`, `gen_post_agente_50`, `gen_post_negocio_emprego`) + 2 carrosséis educativos (7 termos IA, 5 fases automação) produzidos no sistema visual "5-sinais" (branch `viralto/wip-2026-08-30`, não commitado). `scripts/publish_post.py` criado (clone de `publish_carousel.py` para 1 imagem) com confirmação no browser à la `publish_reel.py`. **Bloqueadores:** sessão `data/ig_profile` leu como @anasau28 (nem @viralto.ai nem conta pessoal) — nunca houve publicação confirmada em @viralto.ai; publish bloqueado pelo auto-mode classifier, o Dima corre os comandos no terminal dele.
