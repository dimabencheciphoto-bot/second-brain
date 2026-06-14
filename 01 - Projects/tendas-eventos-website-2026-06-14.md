---
tags: [projecto, web, next-js, cliente]
created: 2026-06-14
status: em-curso
---

# Site Tendas e Eventos — Sessão 2026-06-14

Continuação do desenvolvimento do site `tendaseeventos.com` em Next.js 16.2.9 App Router + Tailwind v4.

## O que foi feito

### UX/Navigation fix — Header
- Removido o dropdown "Serviços" do Header (conflituava com a sub-nav sticky da `/servicos`)
- "Serviços" passou a link directo no nav principal
- Padrão profissional: Apple, Stripe, Atlassian usam este modelo
- Sub-nav sticky na página de serviços é mais útil (sempre visível enquanto se faz scroll)

### Performance — Hero Image
- Substituído `background-image` CSS por `next/image` com `fill` + `priority`
- Resultado: WebP/AVIF automático, preload do LCP no `<head>`, sem layout shift

### Nova secção — Climatização
- Adicionada ao array `servicos` em `/servicos/page.tsx`
- Sub-nav inclui automaticamente (gerado do mesmo array)
- Card corrigido no `ServicesGrid.tsx` homepage → ancora `/servicos#climatizacao`
- `scrollMarginTop: '128px'` em todos os `<article>` (64px header + 48px sub-nav + 16px)

### Página /contacto — 8 melhorias de UX/acessibilidade

**Formulário (`ContactoForm.tsx` — reescrita completa):**
- Labels com `htmlFor` + inputs com `id` — semântica correcta para screen readers
- `aria-required`, `aria-invalid`, `aria-describedby`, `role="alert"` por campo
- Focus ring dourado `focus:ring-amber-500/30` — consistente com brand
- Validação `onBlur` com `touched` state — sem erros prematuros
- Campo "Assunto" → `<select>` com 5 opções predefinidas + chevron dourado
- Fix TypeScript React 19: `ev: { preventDefault(): void }` (evita tipo deprecado)

**Página (`contacto/page.tsx`):**
- Mapa Google Maps real (iframe + `filter: invert(90%) hue-rotate(180deg)` para dark mode)
- Link para abrir morada no Google Maps
- Card WhatsApp na sidebar com "Resposta imediata · +351 967 021 989"

## Estado actual

- Servidor: `http://localhost:3000` (PID 28572, a correr)
- Todas as páginas implementadas: `/`, `/servicos`, `/galeria`, `/sobre-nos`, `/faq`, `/contacto`, `/orcamento`

## Pendentes

1. Deploy Vercel (`vercel login` + `vercel --prod`)
2. `RESEND_API_KEY` no `.env.local` — formulários de contacto e orçamento
3. Domain verification no Resend para `tendaseeventos.com`
