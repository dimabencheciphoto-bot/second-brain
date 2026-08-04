# Viralto — Redesign visual do lote-03 (guiões 7-9)

**Data:** 2026-08-04
**Estado:** Em curso — decisão de design pendente antes de publicar

## Contexto

O utilizador achou o design original dos vídeos do lote-03 (guiões 7, 8, 9 em `viralto/video-generator/`) pouco profissional/desactualizado e pediu opções mais "on-trend", limitado explicitamente a este lote — hooks 1-6 (já publicados) e a biblioteca de componentes partilhados (`Captions.tsx`, `fonts.ts`) não devem ser tocados.

## Progresso

1. **6 direcções de design (A-F)** mockadas em HTML (artifact `viralto-lote03-redesign-options.html`) sobre o conteúdo do Guião 7. Utilizador escolheu **C** (manchete/stamp com sombra dura, headline em caps, "mark" com bloco de cor sólida) e **F** (bloco de cor sólida no topo, split duotone).
2. Testes isolados renderizados do blend C+F e de C puro sobre o Guião 7 (`Hook7TestCF.tsx`, `Hook7TestC.tsx`) — não tocaram em produção.
3. **Mudança real aplicada**: o design C+F foi levado a sério para `Hook8WithCaptions.tsx` (ficheiro de produção), re-renderizado para `out/hook8-final.mp4`. Guião 7 e 9 continuam com o design antigo.
4. Utilizador perguntou se se podiam usar imagens/animações. Foram construídos e renderizados **3 testes adicionais**, todos sobre o Guião 7, todos isolados (não tocam produção):
   - `Hook7TestMockup.tsx` — mockup de resultados de pesquisa Google (concorrente encontrado, negócio do cliente "ghosted", não aparece).
   - `Hook7TestPhoto.tsx` — tratamento duotone/silhueta. **Nota importante:** é um placeholder ilustrativo — não existem fotos reais do cliente no projecto nem há capacidade de gerar imagens; para ficar definitivo precisa de uma foto real fornecida pelo utilizador.
   - `Hook7TestAnim.tsx` — animação de pin de mapa: ondas de radar a pulsar, pin do cliente esbate-se enquanto o pin do concorrente (laranja) entra — visualiza "encontrado por outro".

Todos os 5 testes + a mudança real do Hook 8 estão registados como composições em `Composition.tsx`.

5. **Sinal de preferência forte (2026-08-04)**: ao rever a Opção F **pura** (sem blend com C) no artifact original — split horizontal 44/56, bloco terracota `#C1501F` em cima + preto em baixo (sem gradiente em lado nenhum), ícones em silhueta sólida (não linha/emoji), headline em frase normal (não caps) — o utilizador reagiu "GOSTO MESMO DESTE ESTILO". Isto é **visualmente diferente** do blend C+F já aplicado a sério ao Hook 8 (que usa `#FF6A2E`, stamp rodado com sombra dura, headline em caps).
6. Pedido: aplicar a Opção F pura a um **guião completo existente**, como teste, e mostrar só no localhost. Construído `Guiao7FullTestF.tsx` — Guião 7 completo (hook→agitar→solução→cta) com a Opção F pura em todos os 4 segmentos (ícones: lupa / relógio com ponteiros "recortados" / estrela / balão de fala com pontos "recortados" — técnica de desenhar formas na cor do fundo por cima do ícone preto para simular recorte). Ícones aumentados de 150×150 para 300×300 a pedido do utilizador. Mostrado apenas via `npx remotion studio` (localhost:3000, hot-reload), sem renderizar mp4. Não tocou em `Guiao7Full.tsx` real.

## Pendências (retomar aqui)

- [ ] **Decisão principal em aberto:** C+F blend (já aplicado a sério no Hook 8) vs. Opção F pura (testada no Guião 7 completo, reacção mais entusiasta) — ou fundir as duas — antes de fechar o design final do lote-03.
- [ ] `out/hook8-cover.png` está desactualizada face ao novo design do Hook 8 — precisa de nova extracção de frame de capa.
- [ ] `Guiao8Full.tsx` (versão completa de 4 segmentos) NÃO foi migrado para nenhum novo design — ainda usa `IconMockup`/`PunchHeadline`/fundo pulsante antigo.
- [ ] Guião 7 e Guião 9 (hooks curtos e versões completas) ainda não redesenhados a sério — só têm ficheiros de teste isolados.
- [ ] Publicação real no Instagram (`publish_reel.py`) e Facebook (`publish_facebook_reel.py`) do lote-03 continua bloqueada até o design ficar fechado.

## Próximo passo

Confirmar com o utilizador se a Opção F pura substitui o blend C+F já aplicado ao Hook 8, ou se ficam direcções diferentes por guião; só depois tocar em ficheiros de produção. Seguir o padrão já estabelecido nesta sessão — testar isolado primeiro se o pedido for "teste", aplicar directo se o pedido for "aplica", mostrar via `remotion studio`/localhost em vez de renderizar mp4 salvo pedido explícito.
