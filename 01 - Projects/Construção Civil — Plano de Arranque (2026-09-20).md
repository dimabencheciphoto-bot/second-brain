---
title: "Construção Civil — Plano de Arranque"
date: 2026-09-20
tags: [projeto, construcao-civil, negocio]
status: em-curso
created: 2026-09-20
---

# Construção Civil — Plano de Arranque (Grande Lisboa)

Negócio pessoal em arranque, a partir de zero (sem empresa, sem alvará, sem rede de subempreiteiros). Plano de negócio completo em `Docs/construcao-civil/plano-negocio.md` no repo `dima visual claude`.

## Ferramentas interactivas (Artifacts)

- **Mapa de quantidades** (residencial, T2 ~80m²) — https://claude.ai/code/artifact/3a34b640-20c5-4caa-a141-c3d363c161eb
- **Caderno de encargos** (residencial, mesmo cenário T2) — https://claude.ai/code/artifact/70a5b87e-3c53-47df-aa43-eca9c976570c
- **Mapa de quantidades — Fitout comercial** (loja/escritório, ~80m²) — https://claude.ai/code/artifact/4bc27d60-9a64-49e2-8eef-9c65ee970a41
  - Rubricas extra vs. residencial: AVAC, Dados/Redes, SCIE, Sinalética, Licenciamento e projectos.
- **Plano de negócio completo** (documento navegável, 2026-09-27) — https://claude.ai/artifact/HQZCfs1tZaPMXEsFHM9Z5d
  - TOC lateral fixa, painel-resumo (margem 15-28%, limite Certificado 40k€, salário-alvo 2.000€), checklist "dia zero" interactiva (persiste no browser do viewer), cartões de ligação para os 3 artifacts acima.
- Templates fonte em Markdown/CSV: `Docs/construcao-civil/mapa-de-quantidades.csv`, `Docs/construcao-civil/caderno-de-encargos-template.md`

**Sequência de documentos:** Caderno de encargos (o quê/como) → Mapa de quantidades (quantidades mensuráveis) → Orçamento (preço final ao cliente — mesma ferramenta que o mapa de quantidades).

## Análise de rentabilidade — fase 1 (obras pequenas residenciais)

**Margem de referência (do plano):**
- 15-20% no arranque, sem histórico.
- 22-28% (BDI) depois de 3-5 obras de referência.

**Exemplo de cálculo (T2 ~80m²):**
- Subtotal de custos: 9.830€
- Margem 18%: lucro ~1.946€
- Trabalho estimado: ~181h

**A alavanca real da fase 1: fazer tu mesmo a mão-de-obra** (pintura e montagens — não exigem certificação):
- Subcontratando tudo: só ganhas a margem → **~10,75€/h**
- Fazendo tu mesmo: margem + mão-de-obra → **~36,7€/h** (~6.646€ "para ti" por obra)

**Custos fixos da fase 1:** quase nulos — ~70-125€/mês (seguro de acidentes de trabalho ~150-300€/ano + amortização de ferramentas). Break-even contabilístico praticamente imediato — o limite real é capacidade/logística (quantas obras consegues ter em carteira e executar sozinho), não custos fixos.

**Cenários de ritmo (rendimento bruto):**
| Ritmo | Horas/mês | Bruto/mês |
|---|---|---|
| 1 obra / 6 semanas | ~120h | ~4.300€ |
| 1 obra / 4 semanas | ~180h | ~6.650€ |
| 1 obra / 3 semanas (com ajuda) | ~240h | ~8.860€ |

**Salário-alvo recomendado: 2.000€ líquidos/mês, fixo.**
A partir do 2º-3º projecto (quando já houver 1 mês de reserva à frente). No 1º projecto, o excedente fica no negócio como capital de arranque / reserva de 3 meses. Fixar um salário — não sacar "tudo o que a obra deu" — é o que dá estabilidade num negócio de ritmo irregular.

## Bug de padrão a lembrar

Ao mudar defaults no JS de um Artifact com `localStorage`, subir a versão da chave (`v1`→`v2`) — senão o estado antigo guardado no browser sobrepõe-se silenciosamente aos novos defaults no carregamento.

## Pendente

- Caderno de encargos adaptado ao cenário fitout comercial (oferecido ao Dima, ainda não confirmado).
- Trajectória de crescimento do plano: residencial (2-3 obras de referência) → obras maiores → fitout comercial (exige capital de giro + Certificado/Alvará IMPIC quando obra > 40k€).
- Acções concretas do plano ainda por executar: confirmar Certificado com IMPIC/contabilista, abrir recibos verdes, seguro de acidentes de trabalho, inscrição Cronoshare + Leroy Merlin PRO, identificar 1.º projecto-piloto.
