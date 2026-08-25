# AGENTS.md — Second Brain Instruction Manual

**Owner:** Dima  
**Vault:** `C:\Users\DIMA\Documents\Second Brain`  
**System:** PARA + AI Agent (Claude Code)  
**Last updated:** 2026-08-08

---

## 1. Folder Meanings

### 00 - Inbox/
Capture zone — zero friction. Dump everything here: ideas, links, raw notes, screenshots, meeting notes. No organization needed. Process periodically with "process my inbox."

- Notes here are NOT expected to be organized
- Anything can go here
- Claude processes them on request and files to the right folder

### 01 - Projects/
Active work with a defined outcome and a deadline (or near-term intent).

- Each project = one note OR a subfolder with notes (e.g. `Engine Runs/`, `Portfolio Casamento/`, `UGC Outreach Runs/`)
- When a project is done → move to `04 - Archive/`
- Projects are time-bounded. If no deadline exists, it belongs in `02 - Areas/`

### 02 - Areas/
Ongoing responsibilities with no end date. Things you maintain, not complete.

- Examples: `AI Development.md`, `Viralto - Agência AI.md`, `Overnight Engine.md`
- An area has a STANDARD to maintain, not a finish line
- Pipelines (Overnight Engine, Market Agent) live here as areas — they're ongoing

### 03 - Resources/
Reference material. Concepts, research, tools, patterns, sources you want to keep.

- `concepts/` — technical patterns, frameworks, knowledge pages
- `sources/` — summaries of external material read/ingested
- `entities/` — people, orgs, products worth tracking
- Add anything worth keeping for future reference here
- **Nota:** o conhecimento LLM-first (sources/entities/concepts extensos) vive agora no repo `dima visual claude\Wiki\` — ver `Wiki/CLAUDE.md`. Notas aqui que dupliquem conteúdo do Wiki devem ser stubs curtos a apontar para lá, não cópias completas.

### 04 - Archive/
Completed projects, deprecated materials, old research. Never delete — archive.

- Preserves history without cluttering active areas
- Move from `01 - Projects/` when done: `Move-Item "01 - Projects\X.md" "04 - Archive\"`
- Searchable but not actively used

### 06 - Fleeting/
Quick session snapshots not yet filed into a proper project/area note. Process periodically like the inbox.

### 05 - Templates/
Standardized note formats. Use these to create new notes with consistent frontmatter.

### .raw/
**IMMUTABLE.** Source documents dropped for ingestion. Never modify files here.
- `web/` — saved web articles
- `pdf/` — PDFs
- `notes/` — raw text notes
- `transcripts/` — video/audio transcripts

---

## 2. Note Metadata Standard

Every note uses YAML frontmatter:

```yaml
---
title: Note Title
date: YYYY-MM-DD
tags: [tag1, tag2]
status: active | developing | completed | archived
area: ai-dev | ugc | markets | tools | personal
related: ["[[Note Name]]"]
source: manual | claude | web | pdf
---
```

**Status meanings:**
- `active` — in use, maintained
- `developing` — work in progress
- `completed` — done, moving to archive
- `archived` — preserved in `04 - Archive/`

---

## 3. Request Handling

### "Process my inbox"
1. Read all files in `00 - Inbox/`
2. For each: determine correct folder (01/02/03/04)
3. Move + update frontmatter
4. Add to `index.md`
5. Report: "Processed N notes → X to projects, Y to areas, Z to resources"

### "Ingest [file/URL]"
1. Save source to `.raw/[web|pdf|notes|transcripts]/`
2. Extract key concepts, entities, insights
3. Create or update pages in `03 - Resources/concepts/`
4. Update `index.md` and `log.md`
5. Report what was created/updated

### "Save this" / "/save"
1. Identify what was discussed
2. Pick type: concept (`03 - Resources/concepts/`), project note (`01 - Projects/`), area note (`02 - Areas/`)
3. Write the page with full frontmatter
4. Update `index.md` and `log.md`
5. Update `hot.md`

### "What do I know about X" / "/wiki-query"
1. Check `index.md` for X
2. Read relevant pages in `03 - Resources/concepts/`
3. Answer from stored knowledge
4. Flag gaps if found

### "Start a project: [name]"
1. Use `05 - Templates/project-template.md`
2. Create in `01 - Projects/[name].md`
3. Add to `index.md`

### "Create area note: [name]"
1. Use `05 - Templates/area-template.md`
2. Create in `02 - Areas/[name].md`
3. Add to `index.md`

---

## 4. Formatting Standards

- All wikilinks use `[[Note Name]]` (Obsidian format)
- Tags are lowercase, hyphenated: `ugc-agency`, `ai-patterns`
- Dates: `YYYY-MM-DD`
- Headings: `##` for sections, `###` for subsections
- Code blocks: always specify language
- Tables: use markdown tables for comparisons
- Callouts: `> [!note]`, `> [!warning]`, `> [!tip]`

---

## 5. Active Projects, Areas & Knowledge Base

Não duplicado aqui — muda demasiado depressa e desalinha desta secção estática. Fonte de verdade única: **`index.md`** (catálogo completo, uma linha por nota) e **`hot.md`** (factos recentes). Actualizar esses dois ficheiros a cada operação; esta secção fica de fora.

---

## 6. Operational Procedures

### Adding a new concept
```
1. Create "03 - Resources\concepts\[Name].md"
2. Use resource-template.md
3. Add to index.md under ## Resources
4. Append to log.md
5. Update hot.md
```

### Closing a project
```
1. Mark status: completed in frontmatter
2. Move-Item "01 - Projects\X.md" "04 - Archive\"
3. Update index.md (move from Projects to Archive)
4. Append to log.md
```

### Weekly review (optional)
```
1. Process "00 - Inbox\"
2. Review "01 - Projects\" — any to archive?
3. Scan "02 - Areas\" — anything to log?
4. Update hot.md and index.md
```

---

## 7. Key External Context

This vault is the knowledge layer for the `dima visual claude` project at `C:\Users\DIMA\Documents\dima visual claude\`. See that repo's own `CLAUDE.md` for the full, current list of active systems (overnight engine, UGC agency, content factory, finance dashboard, Viralto, etc.) — not duplicated here to avoid drift.

**Stack:** Python, Claude API (MonitoredAnthropic wrapper), Windows Task Scheduler, Obsidian

**Models in use:** `claude-sonnet-5` (analysis), `claude-haiku-4-5-20251001` (speed-sensitive generation), `claude-opus-5` (complex reasoning) — verify against the repo's own CLAUDE.md, models get upgraded.

**Never use** `anthropic.Anthropic()` directly — always `MonitoredAnthropic` from `dima visual claude\token_monitor.py`.

**Conhecimento LLM-first extenso** (fontes, entidades, conceitos de pesquisa) vive no repo em `dima visual claude\Wiki\`, não aqui — ver nota em §1 sob `03 - Resources/`.

---

## 8. Navigation Quick Reference

```
Read hot.md              → recent context (what was happening)
Read index.md            → full catalogue (what exists)
Read "02 - Areas\X.md"    → current state of an ongoing system
Read "01 - Projects\X"    → active project details
Read "03 - Resources\concepts\X.md" → technical knowledge
```

**Start every session by reading:** `hot.md` → `index.md` → specific page.
