---
title: "Site Tendas e Eventos — Auditoria SEO + fix opengraph-image + estado do deploy Vercel, 2026-07-30"
tags: [projecto, web, next-js, cliente, seo, deploy]
date: 2026-07-30
status: developing
summary: "Site tendas-eventos, sessão 2026-07-30"
---

# Site Tendas e Eventos — Auditoria SEO + fix opengraph-image + estado do deploy Vercel, 2026-07-30

Continuação de [[tendas-eventos-website-2026-07-29]].

## Auditoria SEO (manual, `claude-seo` CLI indisponível)

Cobriu: metadata por página (14 rotas), `robots.ts`, `sitemap.ts`, `lib/schema.ts`, Lighthouse local.

**Achado Crítico:** o domínio de produção `www.tendaseeventos.com` **não serve esta app Next.js** — serve um site legado Apache antigo (confirmado por `document.title`/`outerHTML` sem `lang`, meta tags keyword-stuffed, `/robots.txt` e `/sitemap.xml` a devolver 404 estilo Apache). Isto é um problema de DNS/routing no Vercel, fora do meu alcance — só o utilizador consegue corrigir no painel Vercel.

**Lighthouse em `localhost:3000`** (app real): 100/100/100/100, 1 nit menor de acessibilidade (`label-content-name-mismatch`).

**Achados corrigidos nesta sessão** (aprovados pelo utilizador com "sim"):
1. `/og-image.jpg` referenciado em `layout.tsx` (openGraph + twitter) e `lib/schema.ts` não existia (404) → removidas as referências estáticas, agora usa o gerador dinâmico `app/opengraph-image.tsx` (Next.js file convention).
2. `app/sitemap.ts` — faltavam `/politica-privacidade` e `/termos-condicoes` → adicionadas.

**Achado Médio, não corrigido (fora do âmbito aprovado):** as 5 páginas SEO locais (`tendas-lisboa/sintra/cascais/setubal/porto`) injectam cada uma o seu próprio JSON-LD `LocalBusiness` inline via `<Script>` em `components/local/LocalPage.tsx`, mais fino/incompleto que `lib/schema.ts::localBusinessSchema()`. Devia ser unificado.

## Bug em cascata: `app/opengraph-image.tsx` estava partido

Ao remover a referência estática ao `/og-image.jpg`, descobri que o *fallback* (o gerador dinâmico) também estava a rebentar — `net::ERR_EMPTY_RESPONSE` em dev, e `npx next build` falhava a prerenderizar `/opengraph-image`. Causa: o renderizador Satori (usado por `next/og`'s `ImageResponse`) só aceita um subconjunto restrito de CSS.

Três violações encontradas e corrigidas, uma de cada vez (cada fix revelava a seguinte no build seguinte):

1. `display: 'inline-flex'` não é suportado pelo Satori (só `flex|block|contents|none|-webkit-box`) → mudado para `display: 'flex'` + `alignSelf: 'flex-start'` (para manter o comportamento shrink-to-content original, já que o pai tem `align-items: stretch` por defeito).
2. Satori exige `display` explícito (`flex|contents|none`) em qualquer `<div>` com mais de um nó filho — o `<div>` do título ("Tendas para " + `<span>Eventos</span>` + `<br/>` + "em Portugal") não tinha. Reestruturado em duas linhas com `display: flex` explícito em vez de usar `<br/>`.
3. Bug visual (só visível depois do build passar): a palavra "Eventos" aparecia como um bloco dourado sólido sem texto nenhum — o Satori não reconhece a propriedade `WebkitBackgroundClip` (prefixo `-webkit-`), só `backgroundClip` (sem prefixo) + `backgroundImage` (não `background` shorthand) para gradiente em texto. Corrigido e confirmado visualmente via browser (`localhost:3000/opengraph-image`) que "Eventos" agora aparece a dourado, legível.

`npx next build` termina limpo, `/opengraph-image` prerenderiza como rota estática (○).

**Lição a reter:** qualquer alteração futura a `app/opengraph-image.tsx` (ou qualquer rota `next/og`) tem de ser verificada com `npx next build` (não só `next dev`), porque erros do Satori só aparecem no prerender, não em pedidos normais do dev server.

## Estado do deploy Vercel

Utilizador perguntou "como ficava o site no Vercel?" — verificado via `npx vercel ls tendas-eventos`:

- Deployment de produção mais recente tem **46 dias** — não inclui nenhuma correcção desta sessão nem da sessão de 2026-07-29 (WIG/acessibilidade do `OrcamentoForm.tsx`, `prefers-reduced-motion`).
- URLs de preview (`tendas-eventos-*.vercel.app`) estão protegidas por **SSO do Vercel** — não é possível abri-las no browser automatizado sem sessão autenticada na conta Vercel.
- Projecto ligado: `projectId: prj_VvIMcCCAgmE7veW0SyTaM6AlYzte`, `orgId/team: team_VUOvW3XRKaHZYxEZs5IuU9pA`, `projectName: tendas-eventos`.
- Ofereci fazer `npx vercel --prod` para publicar o estado actual (que já incluiria todos os fixes locais, mesmo sem commit — o Vercel CLI publica o directório de trabalho local), mas fiquei à espera de confirmação do utilizador antes de publicar para infra partilhada.

## Nenhum commit feito

Todas as alterações desta sessão (`app/opengraph-image.tsx`, `app/layout.tsx`, `lib/schema.ts`, `app/sitemap.ts`) continuam por commitar — só se commita quando o utilizador pedir explicitamente.

## Deploy feito (2026-07-30, pedido explícito do utilizador)

`npx vercel --prod` publicou o estado local (todos os fixes de 07-29 + 07-30, mesmo sem commit git) em produção. Alias **https://tendas-eventos.vercel.app** confirmado a carregar correctamente via browser (hero, botão WhatsApp, tipografia — tudo ok visualmente).

## Pendente para a próxima sessão

1. Resolver o problema de DNS/routing do domínio `www.tendaseeventos.com` a apontar para o site legado em vez desta app — acção do utilizador no painel Vercel.
2. Unificar o JSON-LD `LocalBusiness` das 5 páginas locais com `lib/schema.ts::localBusinessSchema()`.
3. Continuar a revisão WIG pendente de 07-29: `AudienceTabs.tsx`, `TestimonialsCarousel.tsx`, `ContactoForm.tsx`, `HeroSection.tsx`; alvo de toque do hamburger; contraste de labels secundários no `OrcamentoForm.tsx`.
4. Commitar as alterações de 07-30 no git quando o utilizador pedir — o deploy Vercel publicou directamente do directório local, mas o histórico git ainda não tem estas alterações.
