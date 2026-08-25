# Second Brain

System: PARA + AI Agent (Claude Code)
Purpose: Compounding personal knowledge base — pipelines, UGC, markets, tools.
Owner: Dima
Updated: 2026-08-08

## Structure

```
Second Brain/
├── _meta/
│   ├── AGENTS.md        ← instruction manual for Claude (READ THIS FIRST)
│   └── CLAUDE.md         ← this file
├── index.md              ← master catalogue of all notes
├── log.md                ← append-only operation log
├── 00 - Inbox/            ← capture zone (no organization needed)
├── 01 - Projects/         ← active work with outcomes + deadlines
├── 02 - Areas/            ← ongoing responsibilities (no end date)
├── 03 - Resources/        ← reference material
│   ├── concepts/          ← technical knowledge pages
│   ├── sources/           ← summaries of ingested external material
│   └── entities/          ← people, orgs, products
├── 04 - Archive/          ← completed projects (never delete)
├── 06 - Fleeting/         ← quick session snapshots, not yet filed
├── 05 - Templates/        ← standardized note formats
└── .raw/                  ← immutable source documents (never modify)
    ├── web/
    ├── pdf/
    ├── notes/
    └── transcripts/
```

## Operations

- **Capture:** drop anything in `00 - Inbox/`, say "process my inbox" later
- **Ingest source:** drop in `.raw/[type]/`, say `ingest [file]`
- **Save session:** `/save` or "guarda isto"
- **Query:** "o que sabes sobre X" — Claude lê index.md → drill-in
- **New project:** "start project: [name]" → `01 - Projects/`
- **New area note:** "create area: [name]" → `02 - Areas/`

## Second Brain Context for Other Projects

Add to any other project's CLAUDE.md:

```markdown
## Second Brain
Path: C:\Users\DIMA\Documents\Second Brain

Para contexto não presente neste projecto:
1. Ler index.md (catálogo completo)
2. Ler "02 - Areas/AI Development.md" (estado actual dos pipelines)
3. Ler "03 - Resources/concepts/[Conceito].md" (conhecimento técnico)
```

## Quick Reference

| Quero... | Ficheiro |
|---------|---------|
| Contexto recente | `index.md` |
| Estado dos pipelines | `02 - Areas/AI Development.md` |
| Estado Viralto | `02 - Areas/Viralto - Agência AI.md` |
| Conhecimento técnico | `03 - Resources/concepts/[nome].md` |
| Instruções para Claude | `_meta/AGENTS.md` |
