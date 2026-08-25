---
title: "Viralto — Auditoria final de conversão + deploy"
tags: [viralto, website, ux, deploy]
date: 2026-08-02
status: completed
---

# Viralto — Auditoria final de conversão + deploy

Auditoria completa (desktop 1440×900 + mobile 390×844) ao site `viralto/site`, com foco em conversão, ignorando testemunhos/estatísticas placeholder.

## Findings e resolução

**1. Hierarquia de CTAs (Alta) — resolvido**
WhatsApp e "Agendar reunião" tinham o mesmo peso visual, criando paralisia de decisão. WhatsApp exige ~2 toques/5s (mensagem pré-preenchida via `wa.me`); Cal.com exige ~6 passos (escolher dia/hora/dados) antes de contacto humano. Solução: WhatsApp ficou primário (sólido), `CalBookingButton.tsx` passou a outline/ghost (secundário).

**2. Botão WhatsApp flutuante sobrepondo conteúdo em mobile (Média) — resolvido**
`WhatsappFloat.tsx` ganhou `ring-4 ring-carvao` — halo que separa visualmente o botão fixo do conteúdo por baixo durante o scroll.

**3. Preço em falta nos cards "As 3 fases" (Alta) — decisão: não mostrar**
Pedido explícito do utilizador. Consistente com a FAQ ("Quanto custa?" já não dá números, remete para WhatsApp). Sem alteração de código necessária.

**Sugestão recusada:** seta "voltar ao topo". Recomendação: a última secção deve reforçar a CTA final, não convidar a voltar atrás; competiria em posição com o botão flutuante do WhatsApp. Utilizador concordou em não avançar.

## Deploy

`vercel --prod --yes` corrido 2026-08-02 (build limpo, TypeScript sem erros). Site continua ao vivo em https://site-iota-gules-11.vercel.app — deploy directo por upload local, sem git remote/CI (ver nota de 2026-08-01).

## Próximos passos em aberto
- Nenhum ponto crítico por resolver da auditoria — baseline fechada.
- Continuar sem git remote configurado; alterações locais não estão commitadas no repositório `dima visual claude`.
