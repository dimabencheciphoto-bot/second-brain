---
title: "Viralto — Site landing page ao vivo"
date: 2026-08-01
tags: [viralto, site, deploy, vercel]
status: completed
area: ai-dev
related: ["[[Viralto - Semana 1-2 e posicionamento (2026-07-13)]]", "[[Research - Viralto Nicho AI Portugal 2026]]"]
summary: "Deploy do site Viralto no Vercel"
---

## Contexto

Landing page da Viralto (`viralto/site`, Next.js + Tailwind v4 + framer-motion, tema escuro, cores `--color-carvao`/`--color-laranja`/`--color-branco-quente`) recebeu um lote de afinações de conteúdo e foi publicada em produção via Vercel.

## Estado (2026-08-01)

**Site ao vivo:** https://site-iota-gules-11.vercel.app

### Deploy

- Publicado via `vercel` CLI directamente a partir da pasta local (`vercel --yes`), sem passar por git — o repositório principal não tem remoto configurado (`git remote -v` vazio), por isso não há CI/CD ligado a commits.
- Primeiro deploy do projecto: criou automaticamente o projecto Vercel `dimabencheciphoto-2122s-projects/site` e foi direto para produção (sem repositório git ligado, o CLI trata o primeiro deploy como produção).
- **Importante para deploys futuros:** repetir `vercel --yes` (ou `vercel --prod`) dentro de `viralto/site` publica imediatamente em produção — não existe passo de preview/aprovação automático porque não há integração git.
- Domínio próprio (ex. `viralto.pt`) ainda não associado — usar `vercel domains add` se/quando o utilizador quiser.
- Build verificado: Next.js 16.2.9, 7 páginas estáticas, sem erros. Confirmado visualmente com Chrome DevTools no ambiente de produção.

### Conteúdo afinado nesta sessão

- **Prova social** (`components/ProvaSocial.tsx`): título "Negócios que já confiam na Viralto" ampliado e a laranja (mesmo estilo tipográfico do heading principal); testemunhos alargados de 2 para 4 (placeholders fictícios coerentes com o nicho — clínica dentária, salão, ginásio, espaço de estética); cards de testemunho compactados.
- **FAQ** (`components/FAQ.tsx`): secção reformulada de um acordeão simples de 5 perguntas para 10 perguntas numeradas, com hierarquia visual (índice mono a laranja, chevron animado, primeira pergunta aberta por defeito) e depois compactada em densidade (menos padding/espaçamento) mantendo as 10 perguntas.

### Estado do git (não resolvido)

O repositório principal continua com um volume grande de alterações não commitadas — incluindo todos os ficheiros editados nesta sessão em `viralto/site` (`ProvaSocial.tsx`, `FAQ.tsx`, `app/page.tsx`, etc.) e alterações não relacionadas noutros projectos (`tendas-eventos/`). O deploy Vercel **não depende disto** (é feito por upload directo da pasta), mas o histórico git ainda não reflecte o estado publicado — decidir com o utilizador se/quando commitar.

## Próximos passos

1. Decidir sobre domínio próprio para a Viralto (ex. `viralto.pt`) e associar via `vercel domains add`.
2. Resolver o volume de alterações não commitadas no repositório (fora do âmbito desta tarefa, mas relevante para não perder o histórico do trabalho feito).
3. Considerar ligar o projecto Vercel a um repositório git (precisaria de criar remoto primeiro) para obter deploys de preview automáticos em vez de publicação directa para produção.

## Relacionado

- [[Viralto - Semana 1-2 e posicionamento (2026-07-13)]]
- [[Research - Viralto Nicho AI Portugal 2026]]
