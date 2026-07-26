---
tags: [projecto, financas, dashboard]
data: 2026-07-25
---

# Dashboard Financeiro Pessoal — Estado

Projecto em `finance/` (`c:\Users\DIMA\Documents\dima visual claude\finance\`): extrai transacções de extractos PDF do Millennium BCP via Claude + MarkItDown, acumula em `transacoes.csv`, gera um dashboard HTML (`report.html`) com 4 separadores. Dados cobrem Jan–Jun 2026.

## O que foi feito nesta sessão

- **Reconciliação automática de saldo**: nova função lê "SALDO INICIAL"/"SALDO FINAL" directamente do texto do extracto (regex, sem chamar o Claude) e compara com a soma das transacções extraídas — alerta se não bater certo. Validado contra os 6 extractos existentes: todos reconciliam a 0,00€. Confirmou também que o "buraco" de renda em Junho não era um bug — a renda de Junho foi paga no final de Maio.
- **Correcções de categoria**: Vinted → compras pessoais (não investimento); Generali (seguro automóvel) e mais 3 transacções (ITV, 2× Serghei Belous) → nova categoria **Megane**.
- **Nova categoria Megane**: para despesas do Renault Megane (seguro, oficina, inspecção). Regra própria no prompt de extracção, para que extractos futuros classifiquem automaticamente.
- **Separador "Análise Financeira"** (4º tab do dashboard): narrativa ao estilo "especialista de finanças pessoais", com secções "O que manter" e "O que mudar", calculada dinamicamente a partir dos dados (não são números fixos no texto).
- **Categoria "Investimentos" dividida em duas**: percebi (a pedido do utilizador) que misturava dois comportamentos diferentes —
  - **Bolsa (XTB)**: investimento activo em bolsa, valores irregulares (€100 a mais de €1000 por compra). Sinalizado como ponto de atenção: em pelo menos um mês, a percentagem investida via XTB coincidiu com um dos meses de rendimento mais baixo, sem confirmação de fundo de emergência à parte.
  - **Poupança Automática**: débito fixo de €50/mês ligado ao ordenado — hábito estável, sem necessidade de intervenção.

## Em aberto

- **Não resolvido**: a transferência `2026-01-20 TRF MB WAY P/ SERGHEI BELOUS -250.00` continua em "Transferências". Já foram movidas 2 outras transferências ao mesmo destinatário (€120 e €250, Jan) para "Megane", mas esta terceira nunca foi confirmada pelo utilizador.
- Outras ideias de melhoria já discutidas mas não iniciadas: unificar a lista de categorias num módulo partilhado (hoje duplicada entre os dois scripts), alertas automáticos de anomalia no dashboard.
