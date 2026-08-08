# Viralto — Plano de publicação 10 dias + correção do handle YouTube (7 Ago 2026)

Continuação de [[Viralto - Semana 1-2 e posicionamento (2026-07-13)]] e [[Viralto - Site landing page ao vivo (2026-08-01)]]. Depois da primeira publicação real na @viralto.ai (carrossel "5 sinais", 6 Ago), foi preciso reconstruir o calendário de 10 dias para não repetir conteúdo já publicado — a primeira versão do plano tinha sido feita sem verificar o que já estava online.

## Verificação real por plataforma (Playwright, não assumida)

- **Instagram (@viralto.ai):** 9 publicações reais desde 3 Ago (lançamento + guião1-6 + carrossel 6 Ago). `guião1` está **duplicado** (publicado 2× em 6 minutos) — decisão em aberto, não corrigido.
- **Facebook (Página Viralto):** quase vazia, só `guião1` publicado, 2 seguidores.
- **YouTube — erro corrigido:** o handle documentado antes (`@viralto`) estava errado, apontava para um canal alheio ("woodpunk", conteúdo de carros/Twitter). O utilizador corrigiu directamente: **o handle certo é `@viraltoai`**. Verificado via scraping: canal correcto (bio a bater com a marca), mas **zero conteúdo publicado** — pronto a receber.
- **TikTok:** conta @viralto.ai existe (1 seguidor, 0 gostos), verificação bloqueada por captcha — consistente com o bloqueador já conhecido (conversão para conta comercial pendente).
- **LinkedIn:** sem sessão automatizada guardada, não verificável — assumido vazio, a confirmar com o utilizador.

## Ficheiros actualizados

- `viralto/content/plano-10-dias.md` — calendário completo com 3 tabelas por plataforma (Instagram: 4 peças espalhadas pelos 10 dias, para não ficar sem conteúdo antes do lote-04; Facebook: catch-up 1/dia com 9 peças; YouTube: catch-up 1/dia com 10 peças incl. lançamento); fila TikTok/LinkedIn à espera de desbloqueio.
- `viralto/brand/social_profiles.md` — secção YouTube corrigida para `@viraltoai`.

## Plano publicado como página (Artifact)

A pedido do utilizador, o plano foi publicado como página web navegável — HTML auto-contido, tokens de marca reais (Carvão `#151515`, Laranja `#FF7A3D`, Branco-quente `#F5F5F5`, fonte Sora variável embutida via `@font-face` base64), tema claro/escuro automático.

URL: https://claude.ai/code/artifact/a06a7a2e-1bcf-439f-9279-23f8313d4a3c

## Por decidir (retomar amanhã)

1. **TikTok:** conversão para conta comercial já tratada ou ainda pendente?
2. **LinkedIn:** confirmar se já foi publicado algo lá.
3. **guião1 duplicado no Instagram** — apagar um dos dois ou deixar ficar?
4. **lote-04:** a partir do dia 11 o Instagram fica sem conteúdo novo — quando começar a escrever?

#viralto #redes-sociais #youtube #instagram #plano-conteudo
