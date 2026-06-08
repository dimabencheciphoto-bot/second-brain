---
type: meta
title: "Arquitectura do Vault"
created: 2026-06-08
updated: 2026-06-08
tags: [meta, arquitectura, overview]
---

# Arquitectura do Second Brain

---

## Estrutura de pastas

```
Second Brain/
│
├── 00 - Home/                  ← ENTRADA PRINCIPAL
│   ├── Dashboard.md            ← hub central (Dataview queries)
│   ├── Sobre Mim.md
│   ├── Como Usar Este Vault.md
│   └── Arquitectura do Vault.md  ← este ficheiro
│
├── 01 - Projects/              ← O QUE ESTÁS A CONSTRUIR (tem deadline)
│   ├── _MOC Projects.md        ← índice de projectos
│   ├── Overnight Engine.md
│   ├── UGC Agency Launch.md
│   ├── Musa 1.0.md
│   ├── Market Agent.md
│   ├── Engine Runs/            ← logs automáticos das runs
│   ├── UGC Agency/             ← reports de pipeline
│   └── UGC Outreach Runs/
│
├── 02 - Areas/                 ← RESPONSABILIDADES CONTÍNUAS (sem deadline)
│   ├── _MOC Areas.md           ← índice de áreas
│   ├── AI Development/
│   ├── Business/               ← Business Overview, UGC Agency, KPIs
│   ├── Learning/               ← Learning Log
│   ├── Market Analysis/        ← reports diários de mercado
│   └── Token Usage/            ← custos semanais API
│
├── 03 - Resources/             ← CONHECIMENTO DE REFERÊNCIA (atemporal)
│   ├── _MOC Resources.md       ← índice de recursos
│   ├── Models/                 ← Claude Models, Model Comparison
│   ├── Concepts/               ← AI Patterns, Prompt Engineering, etc.
│   ├── Prompts/                ← Prompt Library
│   └── Tools/                  ← Claude Code Skills
│
├── 04 - Archive/               ← PROJECTOS TERMINADOS
│   └── Second Brain Cleanup.md
│
├── 05 - Templates/             ← TEMPLATES REUTILIZÁVEIS
│   ├── Project Template.md
│   ├── Daily Note.md
│   └── ...
│
├── 06 - Fleeting/              ← NOTAS DIÁRIAS (auto-geradas)
│   └── YYYY-MM-DD.md           ← 1 linha por sessão Claude
│
└── wiki/                       ← CONHECIMENTO PROCESSADO
    ├── index.md                ← catálogo do wiki
    ├── log.md                  ← log de operações (append-only)
    ├── hot.md                  ← contexto recente (~500 palavras)
    ├── overview.md             ← resumo executivo dos 4 sistemas
    ├── concepts/               ← UGC Pricing, AI Patterns, etc.
    ├── questions/              ← sínteses de research (autoresearch)
    ├── sources/                ← referências externas
    ├── sessions/               ← notas de sessão arquivadas
    └── meta/                   ← lint reports
```

---

## Diagrama de fluxo

```mermaid
graph TD
    A[🧠 Dashboard] --> B[01 Projects]
    A --> C[02 Areas]
    A --> D[03 Resources]
    A --> E[wiki/index.md]

    B --> B1[Overnight Engine]
    B --> B2[UGC Agency Launch\nViralto]
    B --> B3[Musa 1.0]
    B --> B4[Market Agent]

    C --> C1[AI Development]
    C --> C2[Business\nBusiness Overview]
    C --> C3[Market Analysis\nreports diários]
    C --> C4[Token Usage\ncustos semanais]

    D --> D1[Models]
    D --> D2[Concepts\nAI Patterns, Prompts...]
    D --> D3[Tools\nSkills Claude Code]

    E --> E1[concepts/\nUGC Pricing, Agentic Patterns...]
    E --> E2[questions/\nResearch Viralto...]
    E --> E3[sessions/\narquivo de sessões]

    style A fill:#1a1a2e,color:#ffd700,stroke:#ffd700
    style B fill:#16213e,color:#e0e0e0,stroke:#444
    style C fill:#16213e,color:#e0e0e0,stroke:#444
    style D fill:#16213e,color:#e0e0e0,stroke:#444
    style E fill:#0f3460,color:#e0e0e0,stroke:#4a90d9
```

---

## Regra de ouro — onde vai cada coisa?

| Tipo de conteúdo | Onde guardar |
|-----------------|--------------|
| Projecto com objetivo e deadline | `01 - Projects/` |
| Responsabilidade contínua | `02 - Areas/` |
| Referência atemporal (SDK, patterns) | `03 - Resources/` |
| Projecto terminado | `04 - Archive/` |
| Conceito processado, framework | `wiki/concepts/` |
| Síntese de research | `wiki/questions/` |
| Referência externa | `wiki/sources/` |
| Nota de sessão Claude | `wiki/sessions/` |

---

## Automações activas

```mermaid
graph LR
    A[Claude Code\nSession termina] -->|vault_auto_sync.py| B[06 - Fleeting\nYYYY-MM-DD.md]
    C[Overnight Engine\nrun 2AM] -->|vault_reporter.py| D[01 - Projects\nEngine Runs/]
    E[Market Agent\nrun manual] -->|vault_market.py| F[02 - Areas\nMarket Analysis/]
    G[GitHub\ndimabencheciphoto-bot] <-->|git push/pull| H[Vault local]

    style A fill:#1a1a2e,color:#ffd700
    style C fill:#1a1a2e,color:#ffd700
    style E fill:#1a1a2e,color:#ffd700
    style G fill:#0f3460,color:#4a90d9
```

---

## Como navegar

1. **Entrada** → [[Dashboard]] (sempre)
2. **Projectos activos** → [[_MOC Projects]]
3. **Estado de um sistema** → `02 - Areas/` → área relevante
4. **Referência técnica** → [[_MOC Resources]] → nota específica
5. **Conhecimento processado** → `wiki/index.md` → concept/question
6. **Contexto recente** → `wiki/hot.md` (500 palavras, actualizado após cada sessão)

---

*Actualizado: 2026-06-08 · [[Dashboard]] · [[wiki/index.md|Wiki Index]]*
