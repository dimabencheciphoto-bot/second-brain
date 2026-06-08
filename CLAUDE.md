# Second Brain: LLM Wiki

Mode: Personal Second Brain (mixed-source)
Purpose: Compounding personal knowledge base — web, local files, video transcripts, manual notes.
Owner: Dima
Created: 2026-06-08

## Structure

```
Second Brain/
├── CLAUDE.md           ← this file
├── wiki/               ← processed knowledge (see wiki/CLAUDE.md for full schema)
│   ├── CLAUDE.md
│   ├── index.md
│   ├── log.md
│   ├── hot.md
│   ├── overview.md
│   ├── sources/
│   ├── entities/
│   │   └── _index.md
│   ├── concepts/
│   │   └── _index.md
│   ├── domains/
│   │   └── _index.md
│   ├── comparisons/
│   ├── questions/
│   └── meta/
└── .raw/               ← immutable source documents (never modify)
    ├── web/
    ├── pdf/
    ├── notes/
    └── transcripts/
```

## Operations

- **Ingest:** drop source in `.raw/`, say `ingest [file]`
- **Query:** ask any question — Claude reads `hot.md` → `index.md` → drill-in
- **Lint:** `lint o wiki` for health check
- **Save:** `/save` to file current session
- **Research:** `/autoresearch [topic]` for autonomous research loop

## Wiki Context for Other Projects

Add to any other project's CLAUDE.md:

```markdown
## Second Brain Wiki
Path: C:\Users\DIMA\Documents\Second Brain

Quando precisares de contexto não presente no projecto:
1. Ler wiki/hot.md (contexto recente, ~500 palavras)
2. Se não chegar, ler wiki/index.md (catálogo completo)
3. Se precisares de domínio específico, ler wiki/domains/[domínio]/_index.md
```
