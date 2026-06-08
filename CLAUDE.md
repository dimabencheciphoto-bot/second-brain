# Second Brain

System: PARA + AI Agent (Claude Code)
Purpose: Compounding personal knowledge base — pipelines, UGC, markets, tools.
Owner: Dima
Updated: 2026-06-09

## Structure

```
Second Brain/
├── AGENTS.md           ← instruction manual for Claude (READ THIS FIRST)
├── index.md            ← master catalogue of all notes
├── log.md              ← append-only operation log
├── 00-inbox/           ← capture zone (no organization needed)
├── 01-projects/        ← active work with outcomes + deadlines
├── 02-areas/           ← ongoing responsibilities (no end date)
├── 03-resources/       ← reference material
│   ├── concepts/       ← 12 technical knowledge pages
│   ├── sources/        ← summaries of ingested external material
│   └── entities/       ← people, orgs, products
├── 04-archive/         ← completed projects (never delete)
├── templates/          ← standardized note formats
└── .raw/               ← immutable source documents (never modify)
    ├── web/
    ├── pdf/
    ├── notes/
    └── transcripts/
```

## Operations

- **Capture:** drop anything in `00-inbox/`, say "process my inbox" later
- **Ingest source:** drop in `.raw/[type]/`, say `ingest [file]`
- **Save session:** `/save` or "guarda isto"
- **Query:** "o que sabes sobre X" — Claude lê index.md → drill-in
- **New project:** "start project: [name]" → 01-projects/
- **New area note:** "create area: [name]" → 02-areas/

## Second Brain Context for Other Projects

Add to any other project's CLAUDE.md:

```markdown
## Second Brain
Path: C:\Users\DIMA\Documents\Second Brain

Para contexto não presente neste projecto:
1. Ler index.md (catálogo completo)
2. Ler 02-areas/AI Development.md (estado actual dos pipelines)
3. Ler 03-resources/concepts/[Conceito].md (conhecimento técnico)
```

## Quick Reference

| Quero... | Ficheiro |
|---------|---------|
| Contexto recente | `index.md` |
| Estado dos pipelines | `02-areas/AI Development.md` |
| Estado Viralto | `02-areas/Viralto UGC Agency.md` |
| Conhecimento técnico | `03-resources/concepts/[nome].md` |
| Research Viralto | `01-projects/Research - Viralto UGC Agency Setup.md` |
| Instruções para Claude | `AGENTS.md` |
