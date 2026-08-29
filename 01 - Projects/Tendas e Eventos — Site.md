---
title: "Tendas e Eventos — Site"
date: 2026-07-30
tags: [projecto, web, next-js, cliente, seo, deploy]
status: developing
summary: "Site tendaseeventos.com (Next.js) — dev, WIG/acessibilidade, SEO, deploy Vercel"
related: ["[[Workspace — Estado Geral 2026-06-14]]"]
---

# Tendas e Eventos — Site

Site do cliente `tendaseeventos.com` em **Next.js 16.2.9** (App Router) + **Tailwind v4**, projecto em `dima visual claude/tendas-eventos/`. Esta nota consolida as 4 sessões de trabalho (2026-06-14 manhã e tarde, 2026-07-29, 2026-07-30).

## Estado actual

- **App real ao vivo:** https://tendas-eventos.vercel.app — deploy de produção feito a 2026-07-30 via `npx vercel --prod` (publicou o directório local, todos os fixes de 07-29 + 07-30 incluídos mesmo sem commit git). Hero, botão WhatsApp e tipografia confirmados visualmente.
- **Domínio custom partido:** `www.tendaseeventos.com` **não serve esta app** — serve um site legado Apache antigo (`/robots.txt` e `/sitemap.xml` a devolver 404 estilo Apache, meta tags keyword-stuffed, sem `lang`). Problema de DNS/routing no painel Vercel — só o utilizador consegue resolver.
- **Lighthouse local** (`localhost:3000`, app real): 100/100/100/100, 1 nit menor de acessibilidade (`label-content-name-mismatch`).
- **Páginas implementadas:** `/`, `/servicos`, `/galeria`, `/sobre-nos`, `/faq`, `/contacto`, `/orcamento`, `/termos-condicoes`, `/politica-privacidade` + 5 páginas SEO locais (`tendas-lisboa/sintra/cascais/setubal/porto`).
- **`prefers-reduced-motion`** tratado centralmente em `app/layout.tsx` via `<MotionConfig reducedMotion="user">` — propaga-se a todo o Framer Motion do site.
- **Sem commits git** — as alterações de 07-29 e 07-30 continuam por commitar; o deploy Vercel publicou directamente do directório local.

## Pendentes

1. **DNS/routing** — apontar `www.tendaseeventos.com` para esta app em vez do site legado. Acção do utilizador no painel Vercel (`projectId: prj_VvIMcCCAgmE7veW0SyTaM6AlYzte`, `team_VUOvW3XRKaHZYxEZs5IuU9pA`).
2. **Git** — commitar as alterações de 07-29 (`OrcamentoForm.tsx`, `FadeIn.tsx`, `Header.tsx`) e 07-30 (`opengraph-image.tsx`, `layout.tsx`, `lib/schema.ts`, `sitemap.ts`) quando o utilizador pedir.
3. **`.env` / Resend** — `RESEND_API_KEY` no `.env.local` + verificação do domínio `tendaseeventos.com` no Resend (formulários de contacto e orçamento).
4. **Revisão WIG pendente** — `AudienceTabs.tsx`, `TestimonialsCarousel.tsx`, `ContactoForm.tsx`, `HeroSection.tsx` ainda por rever contra as Web Interface Guidelines.
5. **Fixes menores** — alvo de toque do botão hamburger em `Header.tsx` (~40px → 44px); contraste dos labels secundários no `OrcamentoForm.tsx` (`rgba(255,255,255,0.35)` ≈ 3:1, abaixo do AA).
6. **Unificar JSON-LD** — as 5 páginas SEO locais injectam cada uma o seu `LocalBusiness` inline via `<Script>` em `components/local/LocalPage.tsx`, mais fino que `lib/schema.ts::localBusinessSchema()`. Unificar.
7. **Testemunhos** — o utilizador ainda não validou o redesign do `TestimonialsCarousel` (Opção B) no browser.

## Lições a reter

- **`app/opengraph-image.tsx` (ou qualquer rota `next/og`)** tem de ser verificada com `npx next build`, não só `next dev` — os erros do renderizador **Satori** só aparecem no prerender. Satori aceita um subconjunto restrito de CSS: `display: 'flex'` (não `inline-flex`); `display` explícito em qualquer `<div>` com mais de um filho; `backgroundClip` + `backgroundImage` sem prefixo `-webkit-` para gradiente em texto (não `WebkitBackgroundClip` nem `background` shorthand).
- **Deploy para infra partilhada** — o Vercel CLI publica o directório de trabalho local, independentemente do estado do git. Confirmar sempre antes de correr `vercel --prod`.

---

## Histórico de sessões

### 2026-06-14 (manhã) — UX, performance, nova secção, /contacto

- **Header:** removido o dropdown "Serviços" (conflituava com a sub-nav sticky da `/servicos`); passou a link directo. Sub-nav sticky da página de serviços mantida (mais útil em scroll).
- **Hero image:** `background-image` CSS → `next/image` com `fill` + `priority`. WebP/AVIF automático, preload do LCP, sem layout shift.
- **Nova secção Climatização:** adicionada ao array `servicos` em `/servicos/page.tsx` (sub-nav gera-se do mesmo array); card na homepage `ServicesGrid.tsx` → âncora `/servicos#climatizacao`; `scrollMarginTop: '128px'` em todos os `<article>`.
- **`/contacto` — 8 melhorias UX/acessibilidade:** reescrita completa do `ContactoForm.tsx` (labels `htmlFor`+`id`, `aria-required/invalid/describedby`, `role="alert"` por campo, focus ring dourado, validação `onBlur` com `touched`, campo "Assunto" → `<select>` com 5 opções, fix TS React 19). Página: mapa Google Maps real (iframe + `filter: invert(90%) hue-rotate(180deg)` para dark mode), link para abrir morada, card WhatsApp na sidebar.

### 2026-06-14 (tarde) — hero desktop, testemunhos, organização

- **Morada** actualizada em `/termos-condicoes`: `Rua Maria Helena Vieira da Silva nº19 - 4Dtº, Tapada das Mercês, 2725-558 Mem-Martins`.
- **Hero desktop:** card fotográfico no espaço vazio à direita (`w-[380px] xl:w-[460px]`, `min(72vh, 600px)`, rounded-3xl). Foto do Pexels (Ken Mwaura, licença free, 149KB) guardada local em `/public/images/gallery/hero-card.jpg` — badge "Casamento · Sintra", ★★★★★ 4.9, quote, hover zoom 105%/700ms, link `/galeria`, `hidden lg:block`. Rejeitados: stats card, booking widget, logo grande.
- **`TestimonialsCarousel` — redesign completo (Opção B):** marquee de 2 linhas rejeitado pelo utilizador ("demasiado grande"). Solução: citação única rotativa. 4 testemunhos (Casamento/Corporativo/Municipal/Parceira), auto-rotação 5500ms com fade+slide, aspas decorativas douradas 18% (Georgia serif), barra de progresso (`@keyframes progressFill` em `globals.css`, reiniciada via `key`), dots expansivos (activo=24px pill), setas circulares, `aria-live="polite"` + lista `.sr-only`, `resetTimer()` ao navegar.
- **Organização de ficheiros:** criada `tendas-eventos/design/` com `competitive-analysis/` (5 JPEGs: eurotendas, hbcv, tendaseeventos, tendasoeste) e `screenshots/` (17 PNGs mobile+desktop) + logos, scripts Python, previews HTML. Removido ficheiro inválido `(,` da raiz.

### 2026-07-29 — revisão Web Interface Guidelines (Vercel)

Revisão do site contra as *Web Interface Guidelines* da Vercel (formulários, foco, animação, imagens).

| Ficheiro | Resultado |
|---|---|
| `app/page.tsx` | ✓ pass — só composição, skip link correcto, JSON-LD válido |
| `components/home/GallerySection.tsx` | ✓ pass — `next/image` com `sizes`, alt descritivo |
| `components/layout/Header.tsx` | ⚠ menor — botão de menu mobile ~40×40px (< alvo 44×44px) |
| `components/ui/FadeIn.tsx` | ✗ → corrigido — nenhuma animação respeitava `prefers-reduced-motion` |
| `components/orcamento/OrcamentoForm.tsx` | ✗ (5 problemas) → todos corrigidos |

**Correcções no `OrcamentoForm.tsx`:**
1. **Sem `<form>`** — botões eram `type="button"` com `onClick`, Enter não fazia nada. Envolvido em `<form onSubmit={handleFormSubmit} noValidate>`, botões "Seguinte"/"Enviar" → `type="submit"`, `handleFormSubmit` decide `next()` vs `submit()` pelo `step`.
2. **Labels sem associação** — sem `htmlFor`/`id`. Corrigido em todos os campos + grupos de botões via `role="group"` + `aria-labelledby`.
3. **Botões de selecção sem estado programático** — só a cor indicava selecção. Adicionado `aria-pressed`.
4. **Erros não ligados aos campos** — adicionado `aria-invalid`/`aria-describedby` nos 3 campos validados + grupo "tipo de evento".
5. **Sem gestão de foco** — `fieldRefs` + `FIELD_ORDER` focam o primeiro campo inválido; heading de confirmação com `ref` + `tabIndex={-1}` recebe foco via `useEffect`; container de sucesso com `role="status" aria-live="polite"`.

**`prefers-reduced-motion`:** corrigido centralmente em `app/layout.tsx` com `<MotionConfig reducedMotion="user">`. Confirmado em runtime.

**Verificação:** `npx tsc --noEmit` limpo; `npm run lint` com 1 erro pré-existente não relacionado (`tailwind.config.ts`, `no-require-imports`).

### 2026-07-30 — auditoria SEO, fix opengraph-image, deploy

- **Auditoria SEO manual** (metadata das 14 rotas, `robots.ts`, `sitemap.ts`, `lib/schema.ts`, Lighthouse). **Achado crítico:** domínio de produção serve site legado Apache, não a app (ver Estado actual).
  - Corrigido: `/og-image.jpg` (404) referenciado em `layout.tsx` e `lib/schema.ts` → removidas referências estáticas, passa a usar o gerador dinâmico `app/opengraph-image.tsx`. `app/sitemap.ts` — adicionadas `/politica-privacidade` e `/termos-condicoes`.
  - Não corrigido (fora do âmbito): JSON-LD `LocalBusiness` das 5 páginas locais (ver Pendentes #6).
- **Bug em cascata — `app/opengraph-image.tsx` estava partido:** ao remover a referência estática descobriu-se que o gerador dinâmico também rebentava (`net::ERR_EMPTY_RESPONSE` em dev, `next build` falhava a prerenderizar). 3 violações de CSS do Satori corrigidas uma a uma (cada fix revelava a seguinte): `inline-flex` → `flex` + `alignSelf`; `display` explícito no `<div>` do título com múltiplos filhos; `WebkitBackgroundClip` → `backgroundClip` + `backgroundImage` sem prefixo. `next build` termina limpo, `/opengraph-image` prerenderiza como rota estática. (Ver Lições a reter.)
- **Deploy:** `npx vercel --prod` publicou o estado local em produção. Alias https://tendas-eventos.vercel.app confirmado a carregar.
