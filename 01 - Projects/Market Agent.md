# Market Agent

Tags: #projeto #mercados #automação #python
Data: 2026-06-08

## O que é

Script Python (`market_agent.py`) que recolhe dados de mercado em tempo real via yfinance, gera análise com Claude Sonnet em português europeu, e produz um relatório HTML + nota no Second Brain.

## Dados recolhidos

### Forex (5 pares essenciais)
- EUR/USD, USD/JPY, GBP/USD, USD/CHF, DXY (Índice Dólar)

### Índices Globais (10)
- S&P 500, NASDAQ 100, Dow Jones, EuroStoxx 50, DAX, CAC 40, FTSE 100, Nikkei 225, Hang Seng, IBEX 35

### ETFs Principais (10)
- SPY, QQQ, GLD (Ouro), TLT (Obrigações), EEM (Emergentes), VGK, EZU, XLF, XLE, USO

## Outputs

- `market_report.html` — dark theme, 3 tabelas lado a lado + análise Claude
- `market_report.json` — dados brutos + relatório
- Obsidian: `02 - Areas/Market Analysis/YYYY-MM-DD.md`

## Como correr

```powershell
python market_agent.py
```

## Análise Claude

Cobre 4 pontos em português europeu:
1. DXY e sinal macro global
2. Índices — quem sobe/cai e porquê
3. ETFs — fluxos de capital (ouro, bonds, emergentes, energia)
4. Perspectiva para investidores portugueses/europeus

## Histórico de melhorias (2026-06-08)

- Adicionados índices globais (antes só tinha ETFs europeus)
- Forex reduzido aos 5 pares mais seguidos por analistas
- Análise passada para português europeu
- 3 bugs corrigidos: encoding JSON, barra de progresso invisível, regex de headings com `#e2e8f0`
