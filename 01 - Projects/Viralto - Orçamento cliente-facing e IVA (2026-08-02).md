---
title: "Viralto — Orçamento cliente-facing e tratamento de IVA"
date: 2026-08-02
tags: [viralto, orcamento, precos, iva]
status: developing
area: ai-dev
related: []
summary: "Orçamento publicado cliente-facing, IVA +23%"
---

# Viralto — Orçamento cliente-facing e tratamento de IVA (2026-08-02)

## Contexto

Sequência da decisão de posicionamento em 3 fases (Presença → Automação → Crescimento, ver nota de posicionamento). Depois de fechar a estratégia de preços interna (com mecanismo de "vaga de lançamento" para os primeiros 3 clientes de cada fase, preço reduzido 6 meses em troca de testemunho), foi construído o documento que é efectivamente enviado a prospects.

## O que foi construído

`viralto-orcamento.html` — página única, não o formato slide-deck usado na proposta da OsteoJP (esse exige diagnóstico específico por cliente que a Viralto não tem para prospects genéricos). Reutiliza o sistema de tokens visuais já validado (Space Grotesk / JetBrains Mono / Inter, carvão `#151515` + laranja `#FF7A3D`).

Estrutura da página:
1. Hero + banner explicando a condição de vaga de lançamento (transparente, não escondida)
2. 3 cards de pacotes por fase — preço standard riscado, preço de lançamento em destaque, CTA WhatsApp por fase
3. Nota: investimento em anúncios pago directamente à plataforma (Google/Meta), fora da mensalidade
4. Secção à la carte — deliberadamente secundária/discreta, mais abaixo da página, só com preços standard
5. **Secção Pagamento** (nova) — métodos aceites, termos do setup, termos das mensalidades
6. 3 passos "Como começamos"
7. Caixa de contacto WhatsApp

Publicado como Artifact: https://claude.ai/code/artifact/a23152e4-b6ab-4e1d-ac40-6bdf2c3c10d6

## Decisão sobre IVA (confirmada pelo utilizador)

Perguntei explicitamente porque é um detalhe legal/fiscal que não posso assumir. Resposta: **regime normal de IVA, acresce 23%** — não o regime de isenção do Artigo 53º CIVA. Todos os preços mostrados no orçamento são valores base (pré-IVA); o IVA é acrescentado na factura.

Adicionei uma nota explícita junto aos pacotes: *"Preços sem IVA. Acresce IVA à taxa legal em vigor (actualmente 23%), incluído na factura."* — e repetida na intro da secção à la carte.

## Métodos de pagamento

Não confirmados explicitamente pelo utilizador — assumi um default razoável para o mercado português (mesmo padrão usado na proposta da OsteoJP, adaptado):
- MB Way, transferência bancária, Multibanco
- Setup: 50% no arranque, 50% na entrega
- Mensalidades: facturadas no início de cada mês

Se o utilizador quiser alterar (ex. métodos diferentes, split diferente do setup), é só pedir — foi sinalizado como assumpção, não como facto confirmado.

## Em aberto

- Se quer gerar uma versão pré-preenchida do orçamento para um cliente/prospect específico (o documento tem placeholders `[Nome do Negócio]` / `[Data]`)
- Confirmar se `viraltoagencia@gmail.com` continua a ser o email de contacto correcto a usar no documento
