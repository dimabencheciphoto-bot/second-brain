---
tags: [viralto, projeto, video, brand]
date: 2026-07-21
---

# Viralto — Animação do logótipo (intro/outro para Reels)

## O que foi feito

Criado `viralto/video-generator/src/LogoBumper.tsx` — componente Remotion reutilizável (`variant: "intro" | "outro"`) com o V-mark a desenhar-se a traço, seguido do wordmark "Viralto." Registado como duas novas composições em `Composition.tsx`: `LogoIntro` (36 frames, ~1.2s) e `LogoOutro` (50 frames, ~1.7s), 1080×1920 @30fps, fundo carvão sólido `#151515` para casar com os 6 vídeos de guiões já renderizados.

Fiel ao spec de `viralto/brand/logo_kit.py`: path do V exacto (`(6,6)→(20,34)→(34,6)`, viewBox 40×40, traço 8, pontas quadradas), gradiente do selo (`155deg, #1E1E1E→#0D0D0D`), cantos arredondados a 24% do lado, tipografia Sora 800, ponto final sempre laranja `#FF7A3D`.

## Coreografia de movimento (2ª iteração, após feedback "faz como um grande animador de logos")

A primeira versão era um fade/spring genérico. Reescrita para ter intenção de motion design:

- **V construído, não traçado único:** as duas diagonais desenham-se a partir de pontas opostas e convergem no vértice, com um pequeno flash de impacto (círculo branco que expande e desvanece) no momento do "contacto".
- **Entrada tipo câmara:** o conjunto entra com leve zoom-settle (`Easing.bezier(0.16,1,0.3,1)`, expo-out) em vez de aparecer estático em escala 1:1.
- **Selo com peso físico:** overshoot ligeiro (`Easing.back`) antes de assentar no tamanho final, com sombra dinâmica que cresce com a opacidade.
- **Wordmark em cascata:** cada letra tem o seu próprio `spring()`, stagger de ~2 frames, em vez de aparecer em bloco. Ponto final laranja tem "pop" elástico próprio, separado das letras.
- **Saída do outro não é espelho da entrada:** colapso rápido e confiante (`Easing.in(Easing.cubic)`) — entrada e saída são animações distintas.

## Estado

Implementado e validado no Remotion Studio (`npm run dev`, localhost:3000) — compila sem erros, hot-reload confirmado. **Ainda não commitado** (o projeto `video-generator/` inteiro continua untracked no git, incluindo este componente). **Ainda não renderizado para `.mp4` final** nem colado aos 6 vídeos de guiões existentes.

## Próximos passos

- Validar timing (impacto no vértice, stagger das letras) a olho depois de o utilizador ver no Studio
- Renderizar `LogoIntro`/`LogoOutro` para `.mp4`/`.webm` (idealmente com alpha, para colar aos vídeos existentes sem re-renderizar tudo)
- Decidir sobre o commit de `viralto/video-generator/` para o git (com `.gitignore` a excluir `node_modules/`)
