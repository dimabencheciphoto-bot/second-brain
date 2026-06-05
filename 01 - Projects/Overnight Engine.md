---
tags: project status/active
created: 2026-06-05
---

# 🎬 Overnight Engine

## Objetivo
Pipeline totalmente automatizado: Reddit trends → script → vídeo MP4 → publicação multi-plataforma → Telegram summary. Corre diariamente às 2h via Task Scheduler.

## Estado atual (2026-06-05)
✅ Agendado no Task Scheduler (2AM diário)
✅ API key configurada no .env
✅ vault_reporter.py ligado — vault atualiza após cada run
✅ script_writer com 15 fórmulas de título SEO
⚠️ YouTube OAuth não configurado
❌ TikTok pendente aprovação developer

## Critério de Sucesso
- [ ] Vídeo publicado com sucesso em ≥2 plataformas por noite
- [ ] Custo por vídeo < $0.05 em tokens
- [ ] 0 crashes não tratados em 7 dias consecutivos

---

## Pipeline

```
trend_scout.py
    ↓ top 5 tópicos
script_writer.py (Haiku)
    ↓ {title, hook, points[], cta, hashtags, thumbnail_text}
video_builder.py (PIL + edge-tts + moviepy v2)
    ↓ 1080×1920 MP4, ~75s
publishers/
    ├── youtube.py   (OAuth2)
    ├── facebook.py  (Graph API)
    ├── instagram.py (Graph API)
    └── tiktok.py    (Content Posting API)
        ↓
telegram_reporter.py
```

## Localização

```
C:\Users\DIMA\Documents\dima visual claude\overnight_engine\
```

## Config Principal

```python
# overnight_engine/config.py
NICHE = "AI tools and automation"
VOICE = "en-US-GuyNeural"
TARGET_DURATION = 75  # segundos
SUBREDDITS = [...]  # 5 AI-focused
```

## Comandos

```powershell
# Run manual
python overnight_engine/run_engine.py

# Scheduler
python overnight_engine/setup_scheduler.py
python overnight_engine/setup_scheduler.py --run
python overnight_engine/setup_scheduler.py --delete
```

---

## Log de Decisões

### 2026-06-05 — Fórmulas de título YouTube SEO
**Decisão:** Banco de 15 fórmulas no prompt do script_writer em vez de instrução genérica  
**Porquê:** Haiku é bom a preencher templates, mau a inventar estruturas; SEO previsível  
**Alternativa rejeitada:** instrução keyword-first simples (menos controlo)

### 2026-06-05 — vault_reporter.py
**Decisão:** Script separado que escreve nota no Obsidian após cada run  
**Porquê:** Second Brain atualiza automaticamente sem intervenção manual  
**Alternativa rejeitada:** atualização manual (não escala)

### 2026-06-05 — edge-tts em vez de ElevenLabs
**Decisão:** Usar edge-tts  
**Porquê:** Gratuito, offline, qualidade aceitável para conteúdo de volume  
**Alternativa rejeitada:** ElevenLabs (custo por caracter)

---

## Issues Conhecidos

- [ ] TikTok requer aprovação de developer access
- [ ] YouTube token expira — rever refresh logic

---

## Métricas

| Data | Plataformas OK | Erros | Custo tokens |
|------|---------------|-------|--------------|
| — | — | — | — |

---

## Ver também

- [[AI Patterns#pipeline-linear]]
- [[Prompt Library#análise-de-tendências]]
- [[Claude Models#haiku]]
