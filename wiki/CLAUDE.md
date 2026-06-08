# Second Brain: LLM Wiki

Mode: Personal Second Brain (mixed-source)
Purpose: Compounding personal knowledge base fed from web, local files, video transcripts, and manual notes.
Owner: Dima
Created: 2026-06-08

---

## Structure

```
Second Brain/
├── CLAUDE.md           ← root schema
├── wiki/               ← processed knowledge base
│   ├── CLAUDE.md       ← this file (wiki routing rules)
│   ├── index.md        ← master catalog of all pages
│   ├── log.md          ← append-only operations log
│   ├── hot.md          ← hot cache (~500 words recent context)
│   ├── overview.md     ← executive summary
│   ├── sources/        ← one summary page per ingested source
│   ├── entities/       ← people, orgs, tools, products
│   │   └── _index.md
│   ├── concepts/       ← ideas, frameworks, mental models
│   │   └── _index.md
│   ├── domains/        ← top-level topic areas
│   │   └── _index.md
│   ├── comparisons/    ← side-by-side analyses
│   ├── questions/      ← filed answers to queries
│   └── meta/           ← dashboards, lint reports
└── .raw/               ← immutable source documents (never modify)
    ├── web/
    ├── pdf/
    ├── notes/
    └── transcripts/
```

---

## Conventions

- All notes use YAML frontmatter: `type`, `status`, `created`, `updated`, `tags` (minimum)
- Wikilinks use `[[Note Name]]` — filenames are unique, no paths needed
- `.raw/` contains source documents: never modify them after ingestion
- `wiki/index.md` is the master catalog: update on every ingest
- `wiki/log.md` is append-only: new entries at the TOP
- `wiki/hot.md` is overwritten completely after every session (~500 words max)
- Tags: lowercase, hyphenated (`ai-tools`, `content-strategy`, `mental-model`)

### Frontmatter template

```yaml
---
type: concept | entity | domain | source | comparison | question
status: draft | active | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [tag1, tag2]
source: "[[Source Page]]"
---
```

---

## Source Types & Ingestion

| Source type | Drop in | Command |
|-------------|---------|---------|
| Web article / URL | `.raw/web/` | `ingest [url or filename]` |
| PDF | `.raw/pdf/` | `ingest [filename.pdf]` |
| Markdown / Obsidian note | `.raw/notes/` | `ingest [filename.md]` |
| YouTube / video transcript | `.raw/transcripts/` | `ingest [transcript.txt]` |
| Manual note | type directly | `/save` or `ingest this:` |

---

## Operations

| User says | Skill |
|-----------|-------|
| `ingest [source]` | `/wiki-ingest` |
| `query:` or question | `/wiki-query` |
| `lint` / `health check` | `/wiki-lint` |
| `/save` | `/save` |
| `research [topic]` | `/autoresearch` |
| `scaffold` / `rebuild` | `/wiki` |
