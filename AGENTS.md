# AGENTS.md — Second Brain Instruction Manual

**Owner:** Dima  
**Vault:** `C:\Users\DIMA\Documents\Second Brain`  
**System:** PARA + AI Agent (Claude Code)  
**Last updated:** 2026-06-09

---

## 1. Folder Meanings

### 00-inbox/
Capture zone — zero friction. Dump everything here: ideas, links, raw notes, screenshots, meeting notes. No organization needed. Process periodically with "process my inbox."

- Notes here are NOT expected to be organized
- Anything can go here
- Claude processes them on request and files to the right folder

### 01-projects/
Active work with a defined outcome and a deadline (or near-term intent).

- Each project = one note OR a subfolder with notes
- Examples: `Research - Viralto UGC Agency Setup.md`, `Overnight Engine Launch`, `Market Agent v2`
- When a project is done → move to `04-archive/`
- Projects are time-bounded. If no deadline exists, it belongs in `02-areas/`

### 02-areas/
Ongoing responsibilities with no end date. Things you maintain, not complete.

- Examples: `AI Development.md`, `Viralto UGC Agency.md`, `Financial Tracking.md`
- An area has a STANDARD to maintain, not a finish line
- Pipelines (Overnight Engine, Market Agent) live here as areas — they're ongoing

### 03-resources/
Reference material. Concepts, research, tools, patterns, sources you want to keep.

- `concepts/` — technical patterns, frameworks, knowledge pages (12 active)
- `sources/` — summaries of external material read/ingested
- `entities/` — people, orgs, products worth tracking
- Add anything worth keeping for future reference here

### 04-archive/
Completed projects, deprecated materials, old research. Never delete — archive.

- Preserves history without cluttering active areas
- Move from `01-projects/` when done: `Move-Item "01-projects/X.md" "04-archive/"`
- Searchable but not actively used

### templates/
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
- `archived` — preserved in 04-archive/

---

## 3. Request Handling

### "Process my inbox"
1. Read all files in `00-inbox/`
2. For each: determine correct folder (01/02/03/04)
3. Move + update frontmatter
4. Add to `index.md`
5. Report: "Processed N notes → X to projects, Y to areas, Z to resources"

### "Ingest [file/URL]"
1. Save source to `.raw/[web|pdf|notes|transcripts]/`
2. Extract key concepts, entities, insights
3. Create or update pages in `03-resources/concepts/`
4. Update `index.md` and `log.md`
5. Report what was created/updated

### "Save this" / "/save"
1. Identify what was discussed
2. Pick type: concept (03-resources/concepts/), project note (01-projects/), area note (02-areas/)
3. Write the page with full frontmatter
4. Update `index.md` and `log.md`
5. Update `hot.md`

### "What do I know about X" / "/wiki-query"
1. Check `index.md` for X
2. Read relevant pages in `03-resources/concepts/`
3. Answer from stored knowledge
4. Flag gaps if found

### "Start a project: [name]"
1. Use `templates/project-template.md`
2. Create in `01-projects/[name].md`
3. Add to `index.md`

### "Create area note: [name]"
1. Use `templates/area-template.md`
2. Create in `02-areas/[name].md`
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

## 5. Active Projects (01-projects/)

| Note | Topic | Status |
|------|-------|--------|
| [[Research - Viralto UGC Agency Setup]] | Setup completo Viralto + pricing + outreach | active |

---

## 6. Active Areas (02-areas/)

| Note | Responsibility | Cadência |
|------|---------------|---------|
| [[AI Development]] | Overnight Engine, Market Agent, Real Estate, Dashboard | ongoing |
| [[Viralto UGC Agency]] | Outreach, scripts, deal tracker, client pipeline | ongoing |

---

## 7. Knowledge Base Summary (03-resources/)

**Concepts activos (12):**

AI/Tech: [[Anthropic SDK]], [[AI Patterns]], [[Agentic Patterns]], [[Prompt Engineering]], [[Cost Optimization]], [[MoviePy v2 Patterns]], [[Playwright Guide]], [[CPI Consumer Price Index]]

UGC/Business: [[UGC Agency Business Model]], [[UGC Cold Outreach]], [[UGC Portfolio]], [[UGC Pricing]]

**Sources:** [[src-ugc-agency-blueprint]], [[src-ugc-cold-email-guide]], [[src-ugc-pricing-2025]]

---

## 8. Operational Procedures

### Adding a new concept
```
1. Create 03-resources/concepts/[Name].md
2. Use resource-template.md
3. Add to index.md under ## Concepts
4. Append to log.md
5. Update hot.md
```

### Closing a project
```
1. Mark status: completed in frontmatter
2. Move-Item "01-projects/X.md" "04-archive/"
3. Update index.md (move from Active Projects to Archive)
4. Append to log.md
```

### Weekly review (optional)
```
1. Process 00-inbox/
2. Review 01-projects/ — any to archive?
3. Scan 02-areas/ — anything to log?
4. Update hot.md
```

---

## 9. Key External Context

This vault is the knowledge layer for the `dima visual claude` project at `C:\Users\DIMA\Documents\dima visual claude\`.

**Active pipelines (all in dima visual claude):**
- **Overnight Engine** — Reddit trends → Claude script → MP4 → multi-platform → Telegram (runs 2AM)
- **Viralto / UGC System** — cold email outreach → deal tracker → scripts
- **Market Agent** — EUR/USD + ETFs → HTML report daily
- **Real Estate Agent** — Idealista.pt scraper → HTML report

**Stack:** Python, Claude API (MonitoredAnthropic wrapper), Windows Task Scheduler, Obsidian

**Models used:**
- `claude-haiku-4-5-20251001` — bulk generation (emails, scripts)
- `claude-sonnet-4-6` — analysis, general work
- `claude-opus-4-8` — complex reasoning

**Never use** `anthropic.Anthropic()` directly — always `MonitoredAnthropic` from `Dima Claude/token_monitor.py`.

---

## 10. Navigation Quick Reference

```
Read hot.md         → recent context (what was happening)
Read index.md       → full catalogue (what exists)
Read 02-areas/X.md  → current state of an ongoing system
Read 01-projects/X  → active project details
Read 03-resources/concepts/X.md → technical knowledge
```

**Start every session by reading:** `hot.md` → `index.md` → specific page.
