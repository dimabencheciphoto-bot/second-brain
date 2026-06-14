---
title: "Overnight Engine — Credentials Setup"
date: 2026-06-09
tags: [project, overnight-engine, ai-dev]
status: active
area: ai-dev
related: ["[[AI Development]]", "[[AI Patterns]]", "[[MoviePy v2 Patterns]]"]
---

# Overnight Engine — Credentials Setup

## Goal
Engine configurado end-to-end com todas as credenciais, primeiro run automático às 2AM completo.

## Why
Código 100% completo e testado (vídeo 26.7s gerado OK). Único bloqueador = credenciais `.env`.

## Engine Status
- Código: **PRONTO** — todos os bugs corrigidos (2026-06-08)
- Visual: redesenhado (OLED black, Impact font, Ken Burns, flash-in)
- ffmpeg: instalado via winget
- Task Scheduler: configurado para 2AM

## Credentials Needed (.env)

```env
# YouTube
YOUTUBE_CLIENT_ID=
YOUTUBE_CLIENT_SECRET=
# (YouTube também precisa de OAuth2 flow → youtube_token.pkl)

# Meta (Facebook + Instagram)
META_ACCESS_TOKEN=
META_PAGE_ID=
META_IG_USER_ID=

# TikTok (Content Posting API — aprovação developer pendente)
TIKTOK_CLIENT_KEY=
TIKTOK_CLIENT_SECRET=
TIKTOK_ACCESS_TOKEN=

# Telegram
TELEGRAM_BOT_TOKEN=
TELEGRAM_CHAT_ID=1200880993
```

## Tasks
- [ ] Obter YouTube OAuth2 credentials (Google Cloud Console)
- [ ] Correr OAuth flow → gerar `youtube_token.pkl`
- [ ] Obter Meta access token (Facebook Developer → Graph API)
- [ ] Encontrar META_PAGE_ID e META_IG_USER_ID
- [ ] TikTok: aguardar aprovação developer access (bloqueador externo)
- [ ] Configurar Telegram bot token (BotFather)
- [ ] Testar end-to-end com `python overnight_engine/run_engine.py`

## Run Command
```powershell
$env:PATH = "C:\Users\DIMA\AppData\Local\Microsoft\WinGet\Packages\Gyan.FFmpeg_Microsoft.Winget.Source_8wekyb3d8bbwe\ffmpeg-8.1.1-full_build\bin;$env:PATH"
python overnight_engine/run_engine.py
```

## Path
`C:\Users\DIMA\Documents\dima visual claude\overnight_engine\`
