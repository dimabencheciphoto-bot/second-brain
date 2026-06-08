---
type: concept
title: "CPI Consumer Price Index"
created: 2026-06-08
updated: 2026-06-08
tags: [markets, economics, macro, inflation]
status: active
---

# CPI — Consumer Price Index

Key macroeconomic indicator tracked by the market agent. Measures inflation by tracking the price of a basket of consumer goods.

## What it measures

- **Headline CPI**: all items including food and energy (volatile)
- **Core CPI**: excludes food and energy — preferred by central banks for policy decisions
- Published monthly by national statistics agencies (Eurostat for EU, BLS for US)

## Why it matters for the market agent

CPI releases move markets significantly:
- **Higher than expected** → EUR/USD drops (ECB may hike), equities often fall
- **Lower than expected** → EUR/USD rallies, equities often rise
- **In-line** → minimal reaction

The market agent fetches EUR/USD + EU ETF data via yfinance and analyses them in context of macro indicators including CPI.

## Key EU/US CPI data sources

| Source | Frequency | Focus |
|--------|-----------|-------|
| Eurostat HICP | Monthly | EU harmonised inflation |
| Eurostat flash CPI | Monthly (advance) | Early EU estimate |
| US BLS CPI-U | Monthly | US consumer inflation |

## Relationship to other indicators

- **PPI** (Producer Price Index) — upstream of CPI; PPI rises often lead CPI rises by 1-2 months
- **PCE** (Personal Consumption Expenditures) — Fed's preferred inflation gauge, slightly lower than CPI
- **ECB target**: 2% HICP over medium term

## Claude analysis context

When the market agent sends CPI data to Claude for analysis:
```
Include: current reading, previous reading, consensus estimate, YoY change
Ask: implications for EUR/USD and EU ETF holdings
```

## Related

- [[AI Patterns]] — market agent pipeline
- [[Cost Optimization]] — Sonnet used for market analysis (worth the cost)
