---
title: "Viralto — Posts single IG + publisher de 1 imagem"
date: 2026-08-31
tags: [viralto, instagram, conteudo, remotion, pillow, publicacao, automacao]
status: developing
area: ai-dev
related: ["Viralto - Agência AI", "Viralto - Semana 1-2 e posicionamento (2026-07-13)", "Viralto - Plano publicacao 10 dias e correcao YouTube (2026-08-07)"]
summary: "3 posts single + 2 carrosséis educativos no sistema visual 5-sinais; scripts/publish_post.py criado; sessão IG lê como @anasau28 e o publish fica bloqueado pelo classifier — Dima corre no terminal"
---

# Viralto — Posts single IG + publisher de 1 imagem (2026-08-31)

## Contexto

Continuação da produção de conteúdo IG faceless (ver *content-mix framework*), reutilizando o sistema visual escuro do `carousel-5-sinais`: fundo gradiente curado por slide, laranja `(255,122,61)` fixo como acento, Sora 800 nos títulos com span laranja na 2ª linha, kicker (rect laranja + caps espaçadas), ghost numeral gigante a ~10% atrás do conteúdo, body a `(208,208,208)` para passar WCAG AA, barra de progresso fina no rodapé.

## Conteúdo criado (branch `viralto/wip-2026-08-30`, não commitado)

**Carrosséis educativos** — geradores clonam `viralto/content/gen_carousel_5tarefas_clinica.py`:

| Ficheiro | Output | Tema |
|---|---|---|
| `gen_carousel_7termos_ia.py` | `carousel-7-termos-ia/` (10 slides) | Glossário: prompt, LLM, agente, RAG, fine-tuning, alucinação, automação |
| `gen_carousel_5fases_automacao.py` | `carousel-5-fases-automacao/` (9 slides) | Da folha de Excel ao agente autónomo, 1 fase por slide |

**Posts single** — novo modo "single": 1 slide, sem contador/barra/corner-mark; ghost = glifo do tema; 2 blocos de headline empilhados a tamanhos diferentes + 1 sub-linha + lockup.

| Ficheiro | Output | Frase | Ghost |
|---|---|---|---|
| `gen_post_tarefa_40x.py` | `post-tarefa-40x/post.png` | "Não precisas de IA. Precisas de parar de fazer a mesma tarefa 40× por dia." | `40x` |
| `gen_post_agente_50.py` | `post-agente-50/post.png` | "Uma rececionista atende 1 chamada de cada vez. Um agente atende 50." | `50` |
| `gen_post_negocio_emprego.py` | `post-negocio-emprego/post.png` | "Se faltasses uma semana, o teu negócio parava? Então não tens um negócio, tens um emprego." | `?` |

`caption.txt` (UTF-8, hook forte na 1ª linha + corpo + 1 CTA + pergunta para comentários + 5 hashtags de nicho) em `post-agente-50/` e `post-negocio-emprego/`.

## scripts/publish_post.py (novo)

Clone de `scripts/publish_carousel.py` reduzido a **1 imagem** (aceita ficheiro ou pasta com 1 imagem). Fluxo de UI do Instagram igual ao do carrossel: recorte "Original" → Seguinte → Seguinte → legenda → Partilhar; verifica a contagem de publicações do perfil antes/depois. CLI: `--caption` / `--caption-file` / `--dry-run` / `--headed` / `--login`.

A 1ª versão recusava se a conta ativa ≠ viralto.ai, mas o selector era frágil. Substituído pela **confirmação no browser à la `publish_reel.py`**: overlay "Publicar / Cancelar" depois da legenda escrita, com a conta visível no topo do diálogo do IG — o Dima aprova olhando para o ecrã real.

## Bloqueadores

1. **Conta IG por resolver.** `publish_post.py --headed` leu a sessão `data/ig_profile` como **@anasau28** (nem @viralto.ai nem a conta pessoal "dimabencheci" da nota de Agosto). Pode ser falso positivo do detetor, mas o `--login` para @viralto.ai continua por confirmar desde 2026-08-02. **Nunca houve publicação confirmada em @viralto.ai por estes scripts.**
2. **Auto-mode classifier do Claude Code bloqueia o publish.** O comando é ação externa e não corre pelo assistente. O Dima tem de o correr no terminal dele.

## Próximo passo (Dima)

```powershell
python scripts/publish_post.py --login   # janela 3 min — entrar em @viralto.ai
echo p | python scripts/publish_post.py viralto/content/post-agente-50/post.png --caption-file viralto/content/post-agente-50/caption.txt --headed
echo p | python scripts/publish_post.py viralto/content/post-negocio-emprego/post.png --caption-file viralto/content/post-negocio-emprego/caption.txt --headed
```

Confirmar a conta no overlay antes de clicar **Publicar**. Nada commitado.
