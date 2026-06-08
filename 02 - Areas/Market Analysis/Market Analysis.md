# Market Analysis

> Área contínua — análises geradas automaticamente por `market_agent.py` + `vault_market.py`.

## Como funciona
O script `market_agent.py` corre manualmente e escreve um relatório HTML em `data/reports/`. O `vault_market.py` escreve o resumo aqui no vault.

```powershell
python market_agent.py        # relatório HTML EUR/USD + ETFs europeus
python vault_market.py        # escreve resumo no vault
```

## Instrumentos Seguidos

| Tipo | Exemplos |
|------|---------|
| Forex | EUR/USD, USD/JPY, GBP/USD, DXY |
| Índices | S&P 500, NASDAQ, EuroStoxx 50, DAX, IBEX 35 |
| ETFs | SPY, QQQ, GLD, TLT, EEM, VGK, VWCE, IWDA, EUNA |

## Conceitos Macro

- [[CPI Consumer Price Index]] — inflação, dados 2025-2026, impacto macro

## Últimas Análises

```dataview
LIST
FROM "02 - Areas/Market Analysis"
WHERE file.name != "Market Analysis"
SORT file.name DESC
LIMIT 10
```

## Notas & Observações

*Adicionar insights manuais aqui — o que os relatórios automáticos não capturam.*

- 

---

*Tags: #area #market-analysis*
