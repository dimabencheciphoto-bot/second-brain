---
title: "Sessão — Dashboard Financeiro: correcções de categoria + painel Explorar por categoria"
date: 2026-09-06
tags: [dashboard, financas, categorias, graficos, fleeting, session]
---

# Sessão — Dashboard Financeiro: correcções de categoria + painel Explorar por categoria
**Data:** 2026-09-06
**Repo:** `dima visual claude` · `finance/gerar_dashboard.py` (untracked) + `finance/transacoes.csv` (gitignored) · **nada commitado**

## Contexto
`finance/gerar_dashboard.py` lê `finance/transacoes.csv` (405 transacções, `mes_origem` 2026-01 a 2026-08)
e escreve um `finance/report.html` auto-contido com 4 separadores. Re-correr `python gerar_dashboard.py`
sempre que o CSV é editado à mão.

## O que foi feito

### 1. 8 correcções manuais de categoria no `transacoes.csv`
Só o campo `categoria` (linhas 355/368/369/376/380/402/403/404), todas de Agosto:

| Descrição | Valor | Nova categoria |
|---|---|---|
| TRF MB WAY P/ NUNO MIGUEL VIEIRA DA SILVA | −173,46 | Viagens |
| TRF MB WAY P/ HEORHII RATSA | −20,00 | Brilha |
| TRF. P/O MARIA PENHA COUTINHO EIRAS | +1377,45 | Brilha |
| HAPPY GLAM LISBOA | −7,40 | Cigarros |
| EST SERVICO REPSOL E1154 RIO DE MOU | −7,40 | Cigarros |
| CUSTO DE SERVICO INTERNACIONAL | −0,85 | Casa Alugada |
| IMPOSTO DO SELO | −0,03 | Casa Alugada |
| EVIDENTE PRATICA LDA | −7,20 | Saúde |

### 2. Novo painel "Explorar por categoria" (separador *Visão geral*)
- Função `gerar_explorador_categoria(df)` em `gerar_dashboard.py`, inserida antes de `SUBTIPO_PATTERNS_ALUGADA`.
- Dropdown `#catExplorerSelect` (categorias ordenadas por total absoluto, desc) + um `.cat-explorer-bloco[hidden]`
  por categoria; IIFE em JS alterna `b.hidden = b.dataset.cat !== sel.value`.
- Cada bloco:
  - 3 stat tiles — saldo da categoria, nº de transacções (em N de M meses), média mensal de gasto.
  - **Gráfico de barras por mês** — reutiliza `gerar_barras_mensais(mensal_cat)`, com `mensal_cat`
    (`groupby('mes_origem')` → entradas/saidas) reindexado sobre todos os meses do período,
    `fill_value=0.0`, para que meses sem movimento apareçam como barra a zero. Legenda condicional
    (Gasto / Recebido conforme a categoria).
  - `<details class="mes-detalhe">` por mês (mais recente primeiro, o 1º `open`) com tabela
    data / descrição / valor e subtotal mensal.

### 3. Bug corrigido — `TypeError` na consola
O `<select>` do explorador tinha a classe `cat-select`, partilhada com os dropdowns de recategorização
por linha. O listener global de `change` fazia `e.target.closest('tr')` → `null` (o select não está numa
`<tr>`) → crash em `linha.classList`. Removida a classe; `.cat-explorer-select` passou a ter CSS autónomo
(font, cor, cursor, border, background, `:hover/:focus`).

## Verificação
- `python gerar_dashboard.py` re-corrido, `report.html` regenerado.
- Playwright + `browser_evaluate`: seleccionar "Casa Alugada" mostra só esse bloco; gráfico com Jan a zero
  e restantes meses proporcionais; **0 erros de consola**.

## Em aberto
- Nada commitado. `gerar_dashboard.py` continua untracked; `transacoes.csv` e `report.html` gitignored.
- Questão antiga ainda por resolver: `2026-01-20 TRF MB WAY P/ SERGHEI BELOUS −250,00` continua em "Transferências".

## Relacionado
- [[Dashboard Financeiro Pessoal - Estado (2026-07-25)]]
