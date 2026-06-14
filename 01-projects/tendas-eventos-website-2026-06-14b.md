---
tags: [projecto, web, next-js, cliente, design]
created: 2026-06-14
status: em-curso
---

# Site Tendas e Eventos — Sessão 2026-06-14 (tarde)

Continuação da sessão da manhã. Foco em: hero desktop, redesign testemunhos, organização de ficheiros.

## O que foi feito

### Morada na página /termos-condicoes
- Actualizada para: `Rua Maria Helena Vieira da Silva nº19 - 4Dtº, Tapada das Mercês, 2725-558 Mem-Martins, Portugal`

### Hero Section — card de foto (desktop)
- Identificado espaço vazio no lado direito do hero no desktop
- Implementado card fotográfico: `w-[380px] xl:w-[460px]`, `height: min(72vh, 600px)`, rounded-3xl
- Foto obtida do Pexels (Ken Mwaura, licença free) — casamento elegante com tenda branca, 149KB
- Guardada em `/public/images/gallery/hero-card.jpg` (local, sem dependência externa)
- Card com: badge "Casamento · Sintra" no topo, overlay com ★★★★★ 4.9, quote, "Ver galeria →"
- Hover: zoom 105% com transição 700ms; link para /galeria
- Escondido no mobile (`hidden lg:block`)
- Opções rejeitadas: stats card (repetia StatsBar), booking widget, logo grande

### TestimonialsCarousel — redesign completo (Opção B)
- Problema: marquee de 2 linhas rejeitado pelo utilizador ("demasiado grande", difícil de ler)
- Análise profissional: marquee inadequado para decisões de alto valor (casamentos/eventos)
- **Solução escolhida:** grande citação única rotativa com progressão automática
- Implementação:
  - 4 testemunhos (Casamento / Corporativo / Municipal / Parceira)
  - Auto-rotação a 5500ms com fade+slide (opacity + translateY 10px)
  - Aspas decorativas `"` em dourado 18% opacidade (text-8xl/9xl, Georgia serif)
  - Texto da citação em `font-display` xl/2xl
  - Barra de progresso dourada: `@keyframes progressFill` em globals.css, reiniciada via `key={progressKey}`
  - Dots expansivos: activo=24px pill dourado, inactivo=8px circle semi-transparente
  - Setas circular esq/dir com hover:scale-105
  - `aria-live="polite"` + lista `.sr-only` para screen readers
  - `resetTimer()` ao navegar manualmente (restart do intervalo)

### Organização de ficheiros
- Criada pasta `tendas-eventos/design/` com sub-pastas:
  - `competitive-analysis/` — 5 JPEGs de análise competitiva (eurotendas, hbcv, tendaseeventos, tendasoeste)
  - `screenshots/` — 17 PNGs de screenshots do site (mobile + desktop)
  - Logo files, scripts Python, previews HTML
- Removido ficheiro inválido `(,` da raiz do projecto
- Raiz do workspace limpa de ficheiros dispersos

## Ficheiros modificados

| Ficheiro | Alteração |
|---|---|
| `app/termos-condicoes/page.tsx` | Nova morada completa |
| `components/home/HeroSection.tsx` | Card foto lado direito desktop |
| `components/home/TestimonialsCarousel.tsx` | Reescrita completa (Opção B) |
| `app/globals.css` | `@keyframes progressFill` adicionado |
| `public/images/gallery/hero-card.jpg` | Nova foto (Pexels, 149KB) |
| `tendas-eventos/design/` | Pasta criada, ficheiros organizados |

## Pendentes

1. Deploy Vercel (`vercel login` + `vercel --prod` dentro de `tendas-eventos/`)
2. `RESEND_API_KEY` no `.env.local` — formulários de contacto e orçamento
3. Domain verification no Resend para `tendaseeventos.com`
4. Utilizador não reviu ainda a nova secção de testemunhos no browser
