---
title: "OsteoJP — Consultoria de Marketing Digital 2026"
date: 2026-06-29
tags: [cliente, osteopatia, consultoria, marketing-digital]
status: active
area: ai-dev
related: []
summary: "Clínica de osteopatia — proposta, site, brand guidelines"
---

# OsteoJP — Consultoria de Marketing Digital 2026

**Data:** 2026-06-29
**Estado:** Proposta enviada (pendente aprovação)
**Tags:** #cliente #osteopatia #consultoria #marketing-digital

---

## Cliente

- **Nome:** OsteoJP
- **Morada:** Linda-a-Velha (principal) + Castelo Branco
- **Fundação:** 2012
- **Google Rating:** 4.9★ / 104 avaliações (melhor do mercado Lisboa)
- **Diferenciais:** NESA (Neuro-Estimulação por Acupunctura), osteopatia pediátrica

---

## Diagnóstico (auditoria Junho 2026)

**Pontos fortes**
- Reputação online excecional (4.9★)
- 14 anos de experiência, especialização NESA única no mercado
- Clientes fiéis com altas taxas de retorno

**Lacunas críticas**
- Sem email profissional (usa Gmail genérico)
- Sem preços online
- Sem WhatsApp Business
- Instagram sem Reels, apenas posts estáticos
- Sem sistema de marcação online

---

## Benchmark — Concorrentes Lisboa

| Clínica | Preço/sessão | Destaque digital |
|---------|-------------|-----------------|
| Thrust Clinic | €50–60 (público) | Únicos com preços visíveis |
| Osteoparque | n/d | WhatsApp clicável, Zappy booking |
| MQ Osteopatia Moderna | €75+ | Website bilíngue, Doctoralia |
| **OsteoJP** | **n/d** | **Melhor Google Rating (4.9★)** |

---

## Proposta

**Ficheiro:** `Clients/osteojp-proposta.html` (9 slides, tema claro)

### Pacote Starter — €497
- Email profissional + assinatura
- WhatsApp Business configurado
- Preços + FAQs no website
- 1 Reel de arranque

### Pacote Growth — €897
- Tudo do Starter
- Auditoria e redesign website
- Sistema de marcação online
- 4 Reels/mês (1 mês)
- Google Business optimizado

### Pacote Full — €1.497
- Tudo do Growth
- 3 meses de gestão redes sociais (4 Reels + 8 stories/mês)
- Email marketing mensal
- Relatório mensal de métricas

---

## Plano de acção (3 fases)

**Fase 1 — Fundação (semanas 1–2)**
Email profissional, WhatsApp Business, Google Business, preços online

**Fase 2 — Presença (semanas 3–6)**
Instagram Reels, newsletter, sistema de marcação

**Fase 3 — Crescimento (mês 2–3)**
Conteúdo regular, email marketing, tracking de métricas

---

## Notas

- Proposta criada com design light theme (Figtree + Noto Sans)
- Páginas de entidade criadas na Wiki de ficheiros do projecto (não no Second Brain): `Wiki/entities/OsteoJP.md`, `Wiki/entities/Thrust-Clinic.md`, `Wiki/entities/Osteoparque.md`, `Wiki/entities/MQ-Osteopatia-Moderna.md`
- Research completo em `Wiki/questions/Research-OsteoJP-*.md`

---

## Actualização — Agosto 2026

A proposta evoluiu para um deck de **10 slides em tema escuro** ("Carvão", accent laranja `#FF7A3D`) — `Clients/osteojp-proposta.html` é agora a fonte de verdade. Pacotes deixaram de ter preço fixo publicado (Starter/Growth/Full Scale → "Personalizado", orçamento à medida após kick-off), mantendo a estrutura de 3 fases.

**Publicações ao vivo:**
- Deploy público (Vercel): https://osteojp-proposta.vercel.app
- Claude Artifact (privado): https://claude.ai/code/artifact/4f6d06a3-f0d7-4e3d-8288-3aeb7e781957
- PDF: `Clients/osteojp-proposta.pdf`

**2026-08-06 — Fix mobile-responsive:** o deck não tinha nenhuma `@media` query (100% desktop-fixo, `100vw`/`100vh`). Adicionado bloco `@media (max-width: 768px)` que: transforma os slides de posicionamento absoluto+transição para scroll de página normal; colapsa todos os grids (2–6 colunas) para 1 coluna; torna a tabela de benchmark scrollável horizontalmente; empilha steps e caixa de contacto. Verificado via Playwright a 390×844 nos 10 slides, depois propagado às 3 cópias (fonte → deploy Vercel → Artifact) e redeploy/republish de ambas.

---

## Actualização — 2026-08-07/08: site real em produção (`OsteoJP-Site/`)

Além da proposta/deck (secção acima), existe agora um **projecto Next.js separado e já em produção**: `OsteoJP-Site/`, site completo do cliente (não é só a proposta). Ao vivo em **https://osteojp-site.vercel.app** — projecto Vercel `osteojp-site` (`prj_WW30cxh1cSOnppSK3oNSRKqqEHZw`, org `team_VUOvW3XRKaHZYxEZs5IuU9pA`), já linkado localmente (`.vercel/project.json`), pelo que o deploy é directo: `npm run build` → `vercel --prod --yes`, sem necessidade de voltar a linkar. Dima confirmou este fluxo como autorização contínua ("se tiver no futuro para alterar alteramos") — redeploys futuros não precisam de pedir permissão de novo, só seguir o mesmo padrão.

**Alterações feitas nesta sessão:**
- **Secção "Sobre Nós" (`components/home/About.tsx`):** a foto era uma estante desarrumada (produtos de limpeza, mochila NESA) — Dima não gostou. Substituída pela foto de equipa `public/images/tratamentos/Osteopatia-Equipa.jpg` (9 pessoas, batas OsteoJP, já existente no projecto, não usada em mais nenhum sítio, 1184×1479px = ratio 4:5 exacto do container — zero distorção/corte).
- **Hero mobile "fundo muito escuro" (`components/home/Hero.tsx`):** o gradiente overlay ia de 55%→35%→**92%** de opacidade preta, ficando quase preto total exactamente na zona de texto/CTAs — no mobile essa zona ocupa o primeiro ecrã inteiro. Reduzido para 40%→20%→**72%**, mantendo o texto legível sem o peso visual excessivo.
- **Investigada e descartada** uma suspeita de bug de layout (altura de página ~10956px em mobile, parecia anómalo). Confirmado via `scrollHeight` real (não só screenshot) que é genuíno e normal: soma exacta das 8 secções da homepage (a grid de tratamentos com ~6 cards stacka em 1 coluna no mobile = 3386px só essa secção). Não há duplicação de conteúdo — não precisa de correcção.

Ambas as correcções verificadas localmente (dev server + Playwright 390×844) antes de redeploy, e confirmadas ao vivo em produção depois.

**Correcção adicional — mesma sessão, causa raiz real do "fundo escuro":** o fix do Hero acima não resolveu o problema por completo — Dima reportou que continuava escuro no mobile. Diagnóstico com `chrome-devtools` (emulação de `prefers-color-scheme: dark`) revelou que o site tinha um **modo escuro automático completo**, deliberadamente construído em `app/globals.css` (CSS vars trocadas para tons quase-pretos + ~12 componentes com classes Tailwind `dark:`). Não era um bug — havia comentários no código sobre contraste WCAG pensado para dark mode. Perguntei ao Dima se queria desactivar por completo ou só suavizar; escolheu **desactivar por completo**. Fix: removido o bloco `@media (prefers-color-scheme: dark)` das CSS vars + adicionado `@custom-variant dark (&:where(.dark, .dark *));`, que neutraliza todas as classes `dark:` do projecto sem tocar em nenhum dos ficheiros de componentes. Site fica sempre no tema claro da marca, seja qual for a configuração do dispositivo do visitante. Verificado com dark mode emulado local e em produção antes de confirmar ao Dima.

**Pendente:** nada em aberto neste momento — trabalho pausado a pedido do Dima ("retomamos noutra altura"). Próximo trabalho no site (se houver) segue o mesmo fluxo de build→deploy já estabelecido.

---

## Actualização — 2026-08-08 (sessão seguinte): redesign da homepage em 3 conceitos + escolha final

Entretanto o site passou por uma auditoria `/impeccable critique` (score 11/24 "Poor") com remediação P0/P1 já deployada (H1 duplicado em Contactos, cobertura geográfica incorrecta no About, CTAs fracos, etc.) — trabalho intermédio não detalhado aqui, ver memória de sessão para o histórico completo.

Depois disso, Dima pediu 3 direcções visuais fundamentalmente diferentes para a homepage: hero com scroll-trigger e animação abstracta (placeholder CSS do futuro vídeo IA do interior da clínica, com overlays explicativos a aparecer no scroll), secções seguintes com reveal animations distintas entre si, pouco texto e muito espaço em branco, usando a paleta de `OsteoJP-Brand/brand-guidelines.md`.

**3 versões construídas como rotas completas** (`/conceitos/*`, com switcher flutuante para comparar lado a lado):
1. **Percurso do paciente** — scrollytelling linear pinned (dor → diagnóstico → tratamento → equipa → confiança), animação "waves".
2. **Ficha clínica modular** — bento grid, hero curto e directo, animação "orb" (versão atribuída por dado, rolo #3, conforme combinado).
3. **Sala de espera digital** — fundo animado "field" fixo full-screen atrás de toda a página, cartões de conteúdo a "chegar" por cima com scroll.

**Verificação (build + tsc + screenshots desktop/mobile)** encontrou e corrigiu 2 bugs reais antes de apresentar a comparação: sobreposição mobile entre botões/CTA e o switcher flutuante (ajuste de padding); e o fundo animado da "Sala de espera" completamente invisível (texto branco sobre fundo quase-branco), causado por um conflito de cascata Tailwind — uma classe `relative` fixa no componente partilhado `AbstractLoop` a ganhar ao `fixed` passado por quem o chamava, colapsando o elemento a `height: 0`.

**Escolha do Dima: versão 1, "Percurso do paciente".** Promovida à homepage real:
- `app/page.tsx` recompõe agora `PercursoHero → StageDor → StageDiagnostico → TreatmentsCarousel → TeamCascade → TrustStat → FinalCta`.
- Os componentes antigos da homepage (`Hero.tsx`, `About.tsx`, `TreatmentsOverview.tsx`, `WhyChooseUs.tsx`, `SocialProof.tsx`, `TeamPreview.tsx`, `Partners.tsx`) foram **apagados** — o que torna obsoletos os fixes P0/P1 aplicados a `About.tsx` (texto de cobertura) e `WhyChooseUs.tsx` ("Todos os Tratamentos Sob o Mesmo Tecto") mencionados acima: esses ficheiros já não existem.
- `/conceitos/*` e as 2 versões não escolhidas foram removidas por completo (rotas + componentes), incluindo o switcher de comparação.
- `AbstractLoop.tsx` (agora em `components/home/`) simplificado para só a variante "waves".
- Build e `tsc --noEmit` confirmados limpos; verificado localmente em produção (`npx next start -p 4173`) desktop+mobile.

**Pendente:** deploy a produção da nova homepage — a versão ao vivo em osteojp-site.vercel.app é ainda a antiga (pré-redesign). Depois do deploy, considerar re-correr `/impeccable critique` sobre a versão nova.

> **Correcção (2026-08-25):** confirmado via `vercel ls` que este deploy **já foi feito** — o deployment mais recente do projecto `osteojp-site` tem 17 dias, ou seja, coincide com esta mesma sessão de 2026-08-08. O "pendente" acima ficou desactualizado. Não confirmado se `/impeccable critique` foi re-corrido sobre a versão nova.

---

## Actualização — 2026-08-26: Orçamento comercial "Conteúdo & Redes Sociais"

Documento separado da proposta de 10 slides — um orçamento cliente-facing sob a marca **Viralto** (a agência do Dima), não sob a marca OsteoJP. Cobre o âmbito acordado após a conversa inicial: produção mensal de fotos/vídeo + edição + gestão de Instagram/Facebook.

**Ficheiros:**
- Fonte de verdade: `Clients/OsteoJP/orcamento.html`
- PDF (1 página A4): `Clients/OsteoJP/orcamento.pdf`
- Preview live: [Artifact](https://claude.ai/code/artifact/b81b27c7-d819-4d32-bf35-697879941641)

**Âmbito e preços finais:**
- **Linda-a-Velha (base):** sessão de produção mensal de 3h (fotos+vídeo), edição, gestão de Instagram (8 publicações + 2 Reels/mês) e Facebook, relatório mensal simplificado. €0 de arranque, **€450/mês**.
- **Castelo Branco (à parte):** sessão de produção de 3h por visita agendada, edição incluída no mesmo fluxo. **€165/visita**, sem custo fixo mensal.
- Mínimo de 3 meses no pacote base, renovação mensal depois.
- Pagamento: MB Way ou transferência bancária (sem Multibanco, sem menção a IVA — pedidos explícitos do Dima).

**Decisões de formato:**
- Sem botões de WhatsApp (removidos a pedido) — contacto por texto simples (telefone/email).
- Layout comprimido via CSS `@media print` dedicado (root font-size reduzido, grid de 2 colunas para os cartões de Linda-a-Velha/Castelo Branco, `break-inside:avoid`) para caber exactamente numa página A4, sem alterar a versão web/Artifact.
- Logótipo "Viralto." no cabeçalho aumentado (1.3rem→1.8rem) para ficar proporcional ao resto do cabeçalho.

**Workflow para edições futuras:** o `orcamento.html` fonte, o ficheiro preview do Artifact (scratchpad de sessão) e o PDF gerado (via script Playwright `gen_orcamento_pdf.py`) têm de ficar sempre sincronizados — qualquer alteração de conteúdo aplica-se aos 3 em conjunto, seguida de republish do Artifact (mesmo `file_path`/URL).
