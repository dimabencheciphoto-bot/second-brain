---
type: concept
title: "MoviePy v2 Patterns"
created: 2026-06-08
updated: 2026-06-08
tags: [python, video, moviepy, overnight-engine, content]
status: active
---

# MoviePy v2 Patterns

Video assembly library used by the overnight engine (`video_builder.py`) to compose PIL slides + edge-tts audio into vertical MP4 (1080×1920).

> [!key-insight] v2 breaking change
> MoviePy v2 has a different API from v1. `VideoFileClip`, `concatenate_videoclips`, and `AudioFileClip` work but some parameters changed. Always use v2-compatible patterns.

## Core pipeline (overnight engine)

```python
from moviepy import ImageClip, AudioFileClip, concatenate_videoclips

# Per slide: image + audio
clip = ImageClip(frame_array, duration=audio.duration)
clip = clip.with_audio(AudioFileClip(audio_path))
clips.append(clip)

# Assemble
final = concatenate_videoclips(clips, method="compose")
final.write_videofile(output_path, fps=24, codec="libx264", audio_codec="aac")
```

## PIL frame generation

Slides are rendered as numpy arrays from PIL Images (OLED black BG `#000000`, gold accent bars `#FFD700`, Impact/Arial Black fonts). Pass `np.array(pil_image)` to `ImageClip`.

## Audio: edge-tts

```python
import edge_tts, asyncio

async def generate_tts(text, voice, output_path):
    communicate = edge_tts.Communicate(text, voice)
    await communicate.save(output_path)

asyncio.run(generate_tts(text, "en-US-GuyNeural", "slide_0.mp3"))
```

## Common issues

| Issue | Fix |
|-------|-----|
| `ffmpeg not found` | Add ffmpeg to PATH (required) |
| Audio sync drift | Match `duration=audio.duration` exactly |
| Large file size | Use `preset="fast"` in `write_videofile` |
| Font not found | Use absolute Windows font paths (`C:/Windows/Fonts/impact.ttf`) |

## Windows fonts (overnight engine)

- `impact.ttf` → hooks text
- `ariblk.ttf` → Arial Black titles
- `arialbd.ttf` → bold body

## Related

- [[AI Patterns]] — general pipeline patterns
- [[Anthropic SDK]] — script_writer feeds into video_builder
