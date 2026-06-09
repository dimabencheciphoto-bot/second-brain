---
title: "Overnight Engine"
created: 2026-06-09
tags: [area, automation, content]
status: active
---

# Overnight Engine

Pipeline automatizado de conteúdo que corre diariamente às 2AM via Windows Task Scheduler.

## Pipeline

```
trend_scout.py → script_writer.py → video_builder.py → publishers/* → telegram_reporter.py → vault_reporter.py
```

Ver [[Overnight Engine - Credentials Setup]] para configuração de credenciais.

## Tech Stack

- **Trend scout:** Reddit JSON API + HackerNews Algolia API → fallback EVERGREEN list
- **Script writer:** Claude Haiku → structured JSON (title, hook, points, cta)
- **Video builder:** 1080×1920 PIL slides + edge-tts TTS + moviepy v2
- **Publishers:** YouTube (OAuth2), Facebook/Instagram (Meta Graph), TikTok (Content Posting API)
- **Reporter:** Telegram + Obsidian vault

## Histórico de Runs

- [[2026-06-09 - Engine Run]] — broken pipe, ffmpeg permission denied

## Config

- Niche: AI tools and automation
- Voice: en-US-GuyNeural
- Target length: 75s
