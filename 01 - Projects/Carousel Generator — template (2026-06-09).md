# Carousel Generator — template

**Data:** 2026-06-09
**Ficheiro:** `scripts/carousels/template.py`
**Comando:** `python scripts/carousel_generator.py --style template`

---

## Tema

"The Viral Carousel Formula" — fórmula de 4 partes para fechar deals UGC (Viralto)

## 10 Slides

| # | Nome | Section Label | Conteúdo |
|---|---|---|---|
| 1 | cover | — | "...not a skill. It's a system." + 4 shadow boxes |
| 2 | hook | ONE | "90% of creators pitch wrong." |
| 3 | cold-open | TWO | Cold Open: abrir no momento mais interessante |
| 4 | spine | THREE | Spine: sequência com lógica, círculos Setup/Tension/Close |
| 5 | rhythm | FOUR | Rhythm: variar o peso visual a cada mensagem |
| 6 | turn | FIVE | Turn: admissão honesta → lição transferível |
| 7 | payoff | SIX | Payoff: flip de crença + acção específica |
| 8 | mirror | SEVEN | Mirror: dizer a frase que pensaram mas nunca admitiram |
| 9 | filter | EIGHT | Filter: resultado, não serviço |
| 10 | cta | — | "Which part will you fix first?" @viralto.agency |

## Design System

- **Paleta:** SKY, ORANGE, CREAM, DARK, BURNED, LGRAY (6 temas)
- **Regra de cores:** slide 1 sempre ORANGE; slides 1–6 todos diferentes; slides 7–10 = repetição de 1–4 com spread de 6 posições; seed diária
- **Ghost watermarks:** elemento editorial por slide (V gigante, "90", "01", "SPINE", "TURN", "05", aspas)
- **Left accent bar:** barra laranja 6px na borda esquerda em slides de secção
- **Shadow boxes:** caixas com sombra offset para elementos CTA

## Histórico de melhorias (2026-06-09)

- Removido pill N/10 de todos os slides
- Adicionados ghost watermarks por slide
- Implementada regra de cores com spread máximo
- Corrigida numeração section labels (ONE→EIGHT)
- Círculos spine alinhados geometricamente
- Texto turn dentro do slide (wrap_left + font 46)
- Caractere → substituído por — no payoff
