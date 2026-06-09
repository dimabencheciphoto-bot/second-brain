---
type: synthesis
title: "Claude Skills Inventory"
created: 2026-06-09
updated: 2026-06-09
tags:
  - claude
  - skills
  - inventory
  - reference
status: developing
related:
  - "[[AI Development]]"
  - "[[Obsidian Skills]]"
---

# Claude Skills Inventory

Inventário completo dos skills disponíveis para o agente Claude Code neste workspace (~160 skills únicos). Categorizado por origem e função.

---

## 1. Skills Locais do Projecto (`/`)

No diretório `.agents/skills/` — 43 skills. Invocam-se com `/nome`.

### Pipeline e Automação
| Skill | Descrição |
|-------|-----------|
| `/morning` | Daily startup — lê logs overnight engine + pipeline UGC + mercado; envia summary Telegram |
| `/musa-status` | Full pipeline status check (engine, UGC, market, real estate); envia Telegram |

### Core Workflow
| Skill | Descrição |
|-------|-----------|
| `/brainstorming` | Obrigatório antes de qualquer trabalho criativo — explora intenção e requisitos |
| `/writing-plans` | Criar plano de implementação multi-passo antes de codificar |
| `/executing-plans` | Executar planos de implementação em sessão separada com checkpoints |
| `/dispatching-parallel-agents` | Disparar 2+ tarefas independentes em paralelo |
| `/subagent-driven-development` | Executar planos com subagentes independentes na sessão actual |
| `/systematic-debugging` | Debug estruturado para bugs e testes falhados |
| `/test-driven-development` | TDD antes de implementar |
| `/verification-before-completion` | Verificar com comandos antes de declarar trabalho completo |
| `/code-review` | Revisar diff por bugs e oportunidades de simplificação |
| `/receiving-code-review` | Processar feedback de code review com rigor técnico |
| `/requesting-code-review` | Solicitar review antes de merge |
| `/finishing-a-development-branch` | Finalizar branch: merge, PR, cleanup |
| `/using-git-worktrees` | Isolar trabalho em worktree git |
| `/writing-skills` | Criar/editar/verificar skills |

### Python
| Skill | Descrição |
|-------|-----------|
| `/python-code-style` | Linting, formatação, naming conventions |
| `/python-design-patterns` | KISS, SoC, Single Responsibility, composição sobre herança |
| `/python-performance-optimization` | Profiling cProfile, memory profilers |
| `/python-testing-patterns` | pytest, fixtures, mocking, TDD |

### Comunicação
| Skill | Descrição |
|-------|-----------|
| `/caveman` | Modo ultra-comprimido (~75% menos tokens) |
| `/caveman-commit` | Git commits em modo caveman |
| `/caveman-compress` | Comprimir texto em caveman |
| `/caveman-help` | Quick reference card de caveman |
| `/caveman-review` | Code review em caveman |
| `/caveman-stats` | Estatísticas caveman |
| `/cavecrew` | Gestão de equipa caveman |

### Obsidian
| Skill | Descrição |
|-------|-----------|
| `/obsidian-markdown` | Escrever Obsidian Flavored Markdown (wikilinks, callouts, etc.) |
| `/obsidian-bases` | Criar/editar Obsidian Bases (.base files) |
| `/obsidian-cli` | Interagir com vault Obsidian via CLI |
| `/json-canvas` | Criar/editar ficheiros .canvas (mind maps, flowcharts) |

### Documentos
| Skill | Descrição |
|-------|-----------|
| `/docx` | Criar/editar Word documents (.docx) |
| `/pdf` | Ler, combinar, dividir, criar PDFs |
| `/pptx` | Criar/editar PowerPoint (.pptx) |
| `/xlsx` | Criar/editar Excel (.xlsx, .csv) |

### Outros
| Skill | Descrição |
|-------|-----------|
| `/agent-browser` | Automação de browser para agents AI |
| `/playwright-best-practices` | Playwright E2E, Page Object Model, CI/CD |
| `/playwright-cli` | Automação de browser com Playwright |
| `/content-creation` | Draft de marketing content (blog, social, email, landing pages) |
| `/defuddle` | Extrair markdown limpo de páginas web |
| `/documentation` | Escrever documentação técnica (READMEs, runbooks, API docs) |
| `/find-skills` | Descobrir e instalar skills do ecossistema |
| `/canvas-design` | Criar arte visual em PNG/PDF |

---

## 2. Skills Globais (Superpowers)

No diretório `~/.claude/skills/` — 82 skills instalados globalmente.

### ☁️ Cloudflare (9)
`cf-agents-sdk` (Agents SDK Workers), `cf-cloudflare` (plataforma completa Workers/Pages/KV/D1/R2/AI), `cf-cloudflare-email-service` (email transaccional), `durable-objects`, `sandbox-sdk` (Vercel), `turnstile-spin`, `web-perf`, `workers-best-practices`, `wrangler` (CLI)

### 🎨 Figma (9)
`figma-code-connect`, `figma-create-new-file`, `figma-generate-design`, `figma-generate-diagram`, `figma-generate-library`, `figma-swiftui`, `figma-use`, `figma-use-figjam`, `figma-use-slides`

### 🏷️ Sentry (28)
Pacote completo de desenvolvimento Sentry: `agents-md`, `blog-writing-guide`, `brand-guidelines`, `claude-settings-audit`, `code-review`, `code-simplifier`, `commit`, `create-branch`, `django-access-review`, `django-perf-review`, `doc-coauthoring`, `document-api-endpoint`, `find-bugs`, `gha-security-review`, `gh-review-requests`, `iterate-pr`, `presentation-creator`, `pr-link-issue`, `prompt-optimizer`, `pr-writer`, `replay-ux-research`, `security-review`, `skill-scanner`, `skill-writer`, `sred-project-organizer`, `sred-work-summary`, `triage-frontend-issues`, `typing-exclusion-worker`

### ▲ Vercel (9)
`vercel-add-function-examples`, `add-provider-package`, `adr-skill`, `capture-api-response-test-fixture`, `develop-ai-functions-example`, `list-npm-package-content`, `major-version-mode`, `update-provider-models`, `use-ai-sdk`

### 💳 Stripe (3)
`stripe-best-practices`, `stripe-projects`, `upgrade-stripe`

### 🗄️ Supabase (2)
`supabase-safe-sql-execution`, `supabase-studio-best-practices`

### 🧰 Outros Globais (19)
`algorithmic-art` (p5.js generativo), `brand-guidelines` (cores Anthropic), `canvas-design`, `claude-api` (referência API), `database` (SQL/queries/migrations), `doc-coauthoring`, `docker-deploy` (Dockerfiles/compose/CI-CD), `frontend-design` (UI/components/layouts), `internal-comms`, `karpathy-guidelines` (boas práticas LLM), `mcp-builder` (MCP servers), `performance`, `remotion` (vídeo em React), `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx`

---

## 3. Skills Plugin/Sistema

Carregados dinamicamente pelo runtime.

### 📡 Telegram & Utilidades Core
`telegram:access`, `telegram:configure`, `verify`, `code-review`, `security-review`, `simplify`, `fewer-permission-prompts`, `loop`, `run`, `init`, `update-config`, `keybindings-help`, `review`, `claude-api`

### 🔬 Deep Research
`deep-research` — Harness de pesquisa com múltiplas fontes, verificação adversária, relatório citado

### 🧪 Higgsfield AI (imagens/vídeo)
`higgsfield-generate`, `higgsfield-marketplace-cards`, `higgsfield-product-photoshoot`, `higgsfield-soul-id`

### 🖌️ CKM Design
`ckm-banner-design` (22 estilos sociais/ads/print), `ckm-brand` (voz de marca), `ckm-design` (logos/mockups/ícones), `ckm-design-system` (tokens/componentes), `ckm-slides` (HTML+Chart.js), `ckm-ui-styling` (shadcn/ui + Tailwind)

### 🎨 UI/UX
`ui-ux-pro-max` — 50+ estilos, 161 paletas, 57 font pairings, 161 product types

### 🤖 AgentDB
`agentdb-advanced`, `agentdb-learning`, `agentdb-memory-patterns`, `agentdb-optimization`, `agentdb-vector-search`

### 🧩 Obsidian / Wiki
`wiki` (setup), `wiki-cli`, `wiki-fold`, `wiki-ingest` (ingerir fontes no vault), `wiki-lint` (health check), `wiki-mode` (LYT/PARA/Zettelkasten), `wiki-query`, `wiki-retrieve`, `obsidian-bases`, `obsidian-markdown`

### 🎬 YouTube
`youtube-automation`

---

## 4. Skills de Arquitectura Multi-Agente

### ⚙️ SPARC (33 skills)
Metodologia Spec→Pseudo→Arch→Refine→Code:
- **Core**: `sparc:sparc`, `sparc:sparc-modes`
- **Design**: `sparc:architect`, `sparc:designer`
- **Implementação**: `sparc:coder`, `sparc:code`, `sparc:tdd`
- **Qualidade**: `sparc:reviewer`, `sparc:tester`, `sparc:debugger`, `sparc:debug`
- **Coordenação**: `sparc:orchestrator`, `sparc:swarm-coordinator`, `sparc:workflow-manager`
- **Pesquisa**: `sparc:researcher`, `sparc:analyzer`, `sparc:ask`
- **Documentação**: `sparc:docs-writer`, `sparc:documenter`, `sparc:tutorial`
- **DevOps**: `sparc:devops`, `sparc:security-review`, `sparc:supabase-admin`
- **Optimização**: `sparc:optimizer`, `sparc:refinement-optimization-mode`
- **Outros**: `sparc:spec-pseudocode`, `sparc:batch-executor`, `sparc:innovator`, `sparc:mcp`, `sparc:memory-manager`, `sparc:integration`, `sparc:post-deployment-monitoring-mode`

### 🐝 Swarm (16 skills)
`swarm:swarm`, `swarm:swarm-init`, `swarm:swarm-spawn`, `swarm:swarm-modes`, `swarm:swarm-monitor`, `swarm:swarm-analysis`, `swarm:swarm-strategies`, `swarm:swarm-background`, `swarm:development`, `swarm:research`, `swarm:testing`, `swarm:analysis`, `swarm:optimization`, `swarm:maintenance`, `swarm:examples`

### 🧠 Hive-Mind (14 skills)
`hive-mind:hive-mind`, `hive-mind:hive-mind-init`, `hive-mind:hive-mind-spawn`, `hive-mind:hive-mind-consensus` (BFT), `hive-mind:hive-mind-memory`, `hive-mind:hive-mind-metrics`, `hive-mind:hive-mind-wizard`, `hive-mind:hive-mind-status`, `hive-mind:hive-mind-sessions`, `hive-mind:hive-mind-resume`, `hive-mind:hive-mind-stop`

### 🔧 Hooks (8 skills)
`hooks:setup`, `hooks:overview`, `hooks:pre-task`, `hooks:post-task`, `hooks:pre-edit`, `hooks:post-edit`, `hooks:session-end`

### 💾 Memory (4 skills)
`memory:memory-persist`, `memory:memory-search`, `memory:memory-usage`, `memory:neural`

### 🔄 Coordination (6)
`coordination:init`, `coordination:orchestrate`, `coordination:spawn`, `coordination:swarm-init`, `coordination:task-orchestrate`, `coordination:agent-spawn`

### 🤖 Agents (12)
`agents:spawn`, `agents:list`, `agents:status`, `agents:stop`, `agents:pool`, `agents:health`, `agents:metrics`, `agents:logs`, `agents:agent-types`, `agents:agent-capabilities`, `agents:agent-coordination`, `agents:agent-spawning`

### 📊 Analysis (5)
`analysis:performance-report`, `analysis:bottleneck-detect`, `analysis:token-efficiency`, `analysis:token-usage`, `analysis:performance-bottlenecks`

### 🐙 GitHub (18)
`github:code-review`, `github:code-review-swarm`, `github:pr-manager`, `github:pr-enhance`, `github:swarm-pr`, `github:swarm-issue`, `github:issue-tracker`, `github:issue-triage`, `github:repo-analyze`, `github:repo-architect`, `github:release-manager`, `github:release-swarm`, `github:workflow-automation`, `github:project-board-sync`, `github:sync-coordinator`, `github:multi-repo-swarm`, `github:github-modes`, `github:github-swarm`

### ⚡ Optimization (5)
`optimization:parallel-execute`, `optimization:parallel-execution`, `optimization:cache-manage`, `optimization:topology-optimize`, `optimization:auto-topology`

### 👁️ Monitoring (5)
`monitoring:status`, `monitoring:agents`, `monitoring:agent-metrics`, `monitoring:swarm-monitor`, `monitoring:real-time-view`

### 🔁 Workflows (5)
`workflows:development`, `workflows:research`, `workflows:workflow-create`, `workflows:workflow-execute`, `workflows:workflow-export`

### 🤖 Automation (6)
`automation:auto-agent`, `automation:self-healing`, `automation:session-memory`, `automation:smart-agents`, `automation:smart-spawn`, `automation:workflow-select`

---

## Notas

- Skills locais (`.agents/skills/`) sobrepõem-se a globais com o mesmo nome
- Skills plugin são carregados pelo runtime Claude Code, não estão em disco
- SPARC, Swarm, Hive-Mind são frameworks de orquestração multi-agente
- Os skills mais usados neste workspace: `/morning`, `/musa-status`, `/brainstorming`, `/wiki-ingest`, `/wiki-mode`, `/save`, `/caveman`, `/writing-plans`, `/verify` , `/code-review`, `/deep-research`, `/dispatching-parallel-agents`
