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

## Automação

- **`index.md`** — as tabelas de `01 - Projects`, `02 - Areas`, `04 - Archive` e `06 - Fleeting` são geradas ao vivo por Dataview (plugin já instalado) a partir do frontmatter de cada nota, não editadas à mão. Projects/Areas requerem `summary:`; Archive/Fleeting usam só `title`/`date`/`tags`. `03 - Resources` fica manual de propósito (lista curada por categoria — concepts/entities/sources —, não um estado a acompanhar).
- **Frontmatter obrigatório por pasta** (validado por `scripts/vault/vault_lint.py`, repo `dima visual claude`):

  | Pasta | Campos obrigatórios |
  |-------|---------------------|
  | `01 - Projects/` | `title, date, tags, status` |
  | `02 - Areas/` | `title, tags` |
  | `03 - Resources/concepts\|entities/` | `title, tags` |
  | `03 - Resources/sources/` | `title` |
  | `04 - Archive/` | `title` |
  | `06 - Fleeting/` | `title, date, tags` |

  `_meta/`, `05 - Templates/` e `index.md` estão isentos.
- **Lint:** `python scripts/vault/vault_lint.py` (repo `dima visual claude`) verifica frontmatter em falta e wikilinks partidos, escreve `_meta/lint-report-latest.md`. Corre automaticamente em cada commit via `.git/hooks/pre-commit`. A fonte de verdade do hook está **tracked** em `_meta/hooks/pre-commit` (o `.git/hooks/pre-commit` real nunca pode ser tracked — limitação do git) — num clone novo: `cp "_meta/hooks/pre-commit" ".git/hooks/pre-commit"`.
- **Backup:** o plugin Obsidian Git faz auto-commit/push a cada 30 min, mas só enquanto o Obsidian está aberto. Backstop independente: `scripts/vault/vault_git_backup.py` (repo `dima visual claude`), Task Scheduler diário (`VaultGitBackup`, 22:00) — commita e faz push mesmo sem o Obsidian aberto.
- **Notas geradas automaticamente** (Task Scheduler + hooks, repo `dima visual claude/scripts/vault/`): `vault_tokens.py` (custos Claude, semanal), `vault_ugc.py` (pipeline UGC, semanal), `vault_market.py` (mercado, via `market_agent.py`), `vault_session.py`/`vault_auto_sync.py` (sessões → `06 - Fleeting/`). Todas escrevem frontmatter válido para o schema acima.

## Quick Reference

| Quero... | Ficheiro |
|---------|---------|
| Contexto recente | `index.md` |
| Estado dos pipelines | `02 - Areas/AI Development.md` |
| Estado Viralto | `02 - Areas/Viralto - Agência AI.md` |
| Conhecimento técnico | `03 - Resources/concepts/[nome].md` |
| Instruções para Claude | `_meta/AGENTS.md` |
