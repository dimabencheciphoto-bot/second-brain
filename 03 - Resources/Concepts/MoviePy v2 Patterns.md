---
type: concept
status: seed
tags: [python, video, moviepy, overnight-engine]
created: 2026-06-08
updated: 2026-06-08
---

# MoviePy v2 Patterns

Padrões de uso do MoviePy v2 para geração de vídeo no [[Overnight Engine]].

## API v2 vs v1

MoviePy v2 quebrou a API do v1. Principais diferenças:
- `VideoFileClip` → construtor diferente
- `concatenate_videoclips` → parâmetro `method` obrigatório em alguns casos
- Audio: `AudioFileClip` e `CompositeAudioClip` têm nova interface

## Padrão usado no Overnight Engine

```python
from moviepy import *

# Criar clip de imagem com duração
clip = ImageClip(frame).with_duration(duration)

# Adicionar audio
clip = clip.with_audio(AudioFileClip(audio_path))

# Concatenar slides
final = concatenate_videoclips(clips, method="compose")
final.write_videofile(output_path, fps=24)
```

## Ver também

- [[Overnight Engine]] — pipeline que usa este padrão
- [[AI Patterns]] — padrões gerais de pipeline
