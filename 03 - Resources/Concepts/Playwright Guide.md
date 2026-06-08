---
type: concept
status: seed
tags: [python, playwright, scraping, automation]
created: 2026-06-08
updated: 2026-06-08
---

# Playwright Guide

Guia de uso do Playwright para scraping e automação neste projecto.

## Instalação

```bash
pip install playwright
playwright install chromium
```

## Padrão async (TikTok scraper)

```python
from playwright.async_api import async_playwright

async with async_playwright() as p:
    browser = await p.chromium.launch(headless=False)
    page = await browser.new_page()
    await page.goto(url)
    await page.wait_for_selector(".item")
    content = await page.content()
```

## Padrão sync (Idealista scraper)

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=False)
    page = browser.new_page()
    # handle cookie consent
    page.click("button#accept-cookies")
```

## Notas

- `headless=False` necessário para sites com anti-bot
- Cookie consent precisa de handling explícito na maioria dos sites PT

## Ver também

- [[AI Patterns]] — onde o scraping se encaixa nos pipelines
- [[Agentic Patterns]] — agentes com Playwright
