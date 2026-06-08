---
type: concept
title: "Playwright Guide"
created: 2026-06-08
updated: 2026-06-08
tags: [python, playwright, scraping, automation]
status: active
---

# Playwright Guide

Browser automation library used for scraping Idealista.pt (real estate agent) and TikTok hashtag trends.

## Setup

```python
from playwright.async_api import async_playwright

async with async_playwright() as p:
    browser = await p.chromium.launch(headless=False)  # non-headless for CAPTCHAs
    page = await browser.new_page()
    await page.goto(url)
```

## Patterns used in this project

### Cookie consent

```python
try:
    await page.click("button#acceptCookies", timeout=3000)
except:
    pass  # not always present
```

### Pagination (Idealista pattern)

```python
# URL pattern: /pagina-N.htm
for page_num in range(1, max_pages + 1):
    url = f"{base_url}/pagina-{page_num}.htm"
    await page.goto(url)
    listings = await page.query_selector_all(".item-info-container")
```

### Extract text

```python
title = await element.query_selector(".item-title")
text = await title.inner_text() if title else ""
```

### Wait for element

```python
await page.wait_for_selector(".listings", timeout=10000)
```

### CAPTCHA handling

Real estate agent pauses and waits for manual CAPTCHA solve:
```python
input("Solve CAPTCHA then press Enter...")
```

## Async TikTok scraper

`tiktok/scraper.py` uses async Playwright to scrape hashtag pages with Portuguese locale:
```python
await page.set_extra_http_headers({"Accept-Language": "pt-PT,pt;q=0.9"})
```

## Key notes

- Always use `headless=False` for sites with bot detection
- `playwright install chromium` required on first run
- Timeout defaults: 30s page load, adjust per site speed

## Related

- [[AI Patterns]] — how scraper output feeds Claude analysis
- [[Agentic Patterns]] — scraper as agent tool
