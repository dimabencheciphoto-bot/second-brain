# Second Brain: LLM Wiki

Mode: Domain Wiki (Mode A — espelho técnico do vault PARA)
Purpose: Knowledge base técnica de AI automation builder (pipelines, UGC agency, análise financeira)
Owner: Dima
Created: 2026-06-08

## Structure

```
Second Brain/
├── 00 - Home/          → Dashboard + guia do vault
├── 01 - Projects/      → Projectos activos (deadline definida)
├── 02 - Areas/         → Responsabilidades contínuas
├── 03 - Resources/     → Conhecimento atemporal
├── 04 - Archive/       → Concluídos
├── 05 - Templates/     → Templates Obsidian
├── 06 - Fleeting/      → Captura rápida + Daily Notes
├── wiki/               → LLM Knowledge Base (este layer)
│   ├── index.md        → catálogo master
│   ├── log.md          → log de operações (append-only)
│   ├── hot.md          → contexto recente (~500 palavras)
│   ├── overview.md     → resumo executivo
│   ├── domains/        → 4 domínios: ai-automation, markets-finance, content-ugc, business
│   ├── concepts/       → conceitos sintetizados
│   ├── entities/       → pessoas, orgs, produtos
│   ├── sources/        → resumos de fontes ingested
│   ├── comparisons/    → análises side-by-side
│   ├── questions/      → perguntas respondidas e arquivadas
│   └── meta/           → lint reports, dashboards
└── .raw/               → fontes imutáveis (papers, docs)
```

## Conventions

- Todas as notas têm YAML frontmatter: type, status, created, updated, tags (mínimo)
- Wikilinks usam `[[Nome da Nota]]` — filenames são únicos, sem paths
- `.raw/` contém documentos fonte — nunca modificar
- `wiki/index.md` é o catálogo master — actualizar em cada ingest
- `wiki/log.md` é append-only — novas entradas no TOPO

## Operations

- **Ingest:** largar fonte em `.raw/`, dizer "ingest [ficheiro]"
- **Query:** fazer qualquer pergunta — Claude lê hot.md → index.md → drill-in
- **Lint:** dizer "lint o wiki" para health check
- **Save:** `/save` para guardar contexto da sessão
- **Research:** `/autoresearch [tópico]` para research autónomo

## Wiki Context for Other Projects

Em `dima visual claude/CLAUDE.md`, adicionar:

```markdown
## Second Brain Wiki
Path: C:\Users\DIMA\Documents\Second Brain

Quando precisares de contexto não presente no projecto:
1. Ler wiki/hot.md (contexto recente, ~500 palavras)
2. Se não chegar, ler wiki/index.md (catálogo completo)
3. Se precisares de domínio específico, ler wiki/domains/[domínio]/_index.md
```
