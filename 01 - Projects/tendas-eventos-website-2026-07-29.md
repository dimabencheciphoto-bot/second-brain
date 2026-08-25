---
title: "Site Tendas e Eventos — Revisão Web Interface Guidelines (Vercel), 2026-07-29"
tags: [projecto, web, next-js, cliente, accessibilidade, code-review]
created: 2026-07-29
status: developing
---

# Site Tendas e Eventos — Revisão Web Interface Guidelines (Vercel), 2026-07-29

Continuação de [[tendas-eventos-website-2026-06-14b]]. Sessão focada em rever o site contra as *Web Interface Guidelines* da Vercel (formulários, foco, animação, imagens) e corrigir o que foi encontrado.

## Revisão feita

| Ficheiro | Resultado |
|---|---|
| `app/page.tsx` | ✓ pass — só composição, skip link correcto, JSON-LD válido |
| `components/home/GallerySection.tsx` | ✓ pass — `next/image` com `sizes`, alt descritivo, hover só decorativo |
| `components/layout/Header.tsx` | ⚠ menor — botão de menu mobile ~40×40px (abaixo do alvo de toque 44×44px recomendado); sem `prefers-reduced-motion` (resolvido, ver abaixo) |
| `components/ui/FadeIn.tsx` | ✗ fail → corrigido — nenhuma animação respeitava `prefers-reduced-motion` |
| `components/orcamento/OrcamentoForm.tsx` | ✗ fail (5 problemas) → todos corrigidos |

## Correcções aplicadas em `OrcamentoForm.tsx`

1. **Sem `<form>`** — todos os botões eram `type="button"` com `onClick`; Enter num campo de texto não fazia nada. Corrigido: `<form onSubmit={handleFormSubmit} noValidate>` a envolver os 3 passos; botões "Seguinte"/"Enviar Pedido" agora `type="submit"`; `handleFormSubmit` decide `next()` vs `submit()` consoante o `step`.
2. **Labels sem associação** — `<label>` nunca tinha `htmlFor`, inputs sem `id`. Corrigido em todos os campos (`dataEvento`, `localizacao`, `nome`, `telefone`, `email`, `notas`) + grupos de botões via `role="group"` + `aria-labelledby`.
3. **Botões de selecção sem estado programático** (tipo de evento, nº convidados, serviços) — só cor indicava selecção. Adicionado `aria-pressed={active}` a todos.
4. **Erros não ligados aos campos** — sem `aria-invalid`/`aria-describedby`. Adicionado nos 3 campos validados (nome, telefone, email) e no grupo "tipo de evento".
5. **Sem gestão de foco** — em erro de validação, foco não ia para o campo inválido; no ecrã de sucesso, conteúdo mudava sem `aria-live` nem foco. Corrigido: `fieldRefs` + `FIELD_ORDER` focam o primeiro campo inválido; heading de confirmação tem `ref` + `tabIndex={-1}` e recebe foco via `useEffect` quando `submitted` muda; container de sucesso tem `role="status" aria-live="polite"`.

Pendente (não corrigido, severidade menor): contraste de texto secundário (`rgba(255,255,255,0.35)` ≈ 3:1, abaixo do AA) em labels inactivos do formulário.

## `prefers-reduced-motion`

Corrigido de forma centralizada em `app/layout.tsx`: `<MotionConfig reducedMotion="user">` a envolver toda a app. Propaga-se automaticamente a todo o Framer Motion do site (`FadeIn.tsx`, indicador de nav e menu mobile do `Header.tsx`, e qualquer uso futuro) sem editar componente a componente. Confirmado a funcionar em runtime — a consola do browser reportou "You have Reduced Motion enabled on your device" ao detectar a preferência do sistema do utilizador.

## Verificação

- `npx tsc --noEmit` — limpo, zero erros nos ficheiros alterados.
- `npm run lint` — 1 erro pré-existente em `tailwind.config.ts` (`no-require-imports`), não relacionado com esta sessão, não corrigido (fora do âmbito pedido).
- Utilizador validou visualmente no browser (`localhost:3000/orcamento`) via extensão Claude in Chrome (não ligada nesta sessão — utilizador abriu manualmente).

## Pendente para a próxima sessão

1. Continuar a revisão WIG nos restantes componentes por rever: `AudienceTabs.tsx`, `TestimonialsCarousel.tsx`, `ContactoForm.tsx`, `HeroSection.tsx`.
2. Corrigir o alvo de toque do botão hamburger do `Header.tsx` (~40px → 44px).
3. Corrigir o contraste dos labels secundários no `OrcamentoForm.tsx`.
4. Deploy Vercel continua pendente (ver [[tendas-eventos-website-2026-06-14b]]).
