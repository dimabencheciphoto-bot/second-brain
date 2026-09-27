---
title: "Log"
updated: 2026-09-27
tags: [meta, log]
---

# Log

Append-only. Novas entradas no TOPO. Nunca editar entradas passadas.

---

## 2026-09-27 — refactor | Consolidação Viralto + Content Factory (replicação do piloto de 2026-08-29) + auditoria de saúde do vault

- **11 notas soltas da Viralto fundidas.** `Viralto - Criação de Contas Sociais (2026-07-07)`, `...Semana 1-2 e posicionamento (2026-07-13)`, `...Animação do logótipo (2026-07-21)`, `...Demo IA Clínica do Marquês (2026-07-26)`, `...Site landing page ao vivo (2026-08-01)`, `...Auditoria final e deploy (2026-08-02)`, `...Orçamento cliente-facing e IVA (2026-08-02)`, `...Redesign lote-03 video-generator (2026-08-04)`, `...Plano publicacao 10 dias e correcao YouTube (2026-08-07)`, `...Recepcionista IA WhatsApp, pivot no-code (2026-08-30)`, `...Posts single IG e publish_post.py (2026-08-31)` → `01 - Projects/Viralto - Execução e Conteúdo.md`. Estrutura igual ao piloto: `## Estado actual` + `## Pendentes` + `## Lições a reter` + `## Histórico de sessões` (11 subsecções cronológicas). `[[Research - Viralto Nicho AI Portugal 2026]]` (nota de research) e `[[Viralto - Agência AI]]` (Area, estratégia/posicionamento) deixados intocados — só as notas de execução datadas foram fundidas.
- **2 notas do Content Factory fundidas.** `Content Factory - Fase 1 Ideacao (2026-07-05)` + `...Dashboard Kanban (2026-07-06)` → `01 - Projects/Content Factory - Pipeline.md`, mesma estrutura.
- **13 originais apagados.**
- **Wikilinks externos corrigidos (3):** `02 - Areas/Viralto - Agência AI.md` (`related`, 4 links → 1), `01 - Projects/Modelos de ganhar dinheiro — série Artifacts (2026-08-31).md` e `03 - Resources/sources/faceless-content-accounts-2026.md` (ambos apontavam a `[[Content Factory - Fase 1 Ideacao (2026-07-05)]]` → `[[Content Factory - Pipeline]]`).
- `vault_lint.py`: 0 problemas depois da consolidação.
- **Backstop de backup git** (`scripts/vault/vault_git_backup.py`, repo `dima visual claude`) — cobre o gap do plugin Obsidian Git só correr com a app aberta (aconteceu 2026-08-29 → 2026-09-27 sem ninguém notar). Testado, commitado no repo de código; falta o Dima registar a Task Scheduler `VaultGitBackup` (bloqueado para o Claude por classifier de auto-mode).
- **`index.md`:** secções `04 - Archive` e `06 - Fleeting` convertidas de tabela estática para Dataview (estavam desactualizadas — Fleeting tinha 2 notas em falta).
- **Hook pre-commit tornado tracked:** fonte de verdade em `_meta/hooks/pre-commit`, com instrução de instalação num clone novo (o `.git/hooks/pre-commit` real nunca pode ser tracked — limitação do git).
- 7 links partidos + 2 frontmatter em falta da auditoria inicial desta sessão, todos corrigidos antes desta consolidação (não registados em entrada própria — pequenos, ver `_meta/lint-report-latest.md` histórico).

---

## 2026-09-19 — update | Verificação NexLev do nicho faceless ("guarda tudo")

- **`03 - Resources/sources/faceless-content-accounts-2026.md`** — nova secção 10: método NexLev (6 sinais de veredicto), veredito real dos 3 nichos candidatos (Finanças aberto / IA fechado / Estoicismo saturado, com números), lista de nichos novos a bombar Ago-Set 2026 (mega-engenharia, gaming narrado, história militar ES/DE/FR, comics "What If", psicologia estética-sombria, comparação de equipamento) e nota de risco copyright/desmonetização. `key_claims` do frontmatter alargados com os 2 achados principais.
- **`01 - Projects/Modelos de ganhar dinheiro — série Artifacts (2026-08-31).md`** — acrescentado parágrafo a registar a verificação NexLev e link para a secção 10 da fonte.
- **Espelho em auto-memória:** `project_money_models_artifact_series.md` actualizado com o mesmo veredicto; `MEMORY.md` actualizado.

## 2026-09-06 — update | Dashboard Financeiro Pessoal ("guarda tudo")

- **Nota de sessão nova:** `06 - Fleeting/session-dashboard-financeiro-explorador-categoria-2026-09-06.md` — 8 correcções manuais de categoria no `transacoes.csv` (transacções de Agosto) + novo painel "Explorar por categoria" em `finance/gerar_dashboard.py` (função `gerar_explorador_categoria(df)`: dropdown → 3 stat tiles + gráfico de barras por mês via `gerar_barras_mensais(mensal_cat)` reindexado + `<details>` por mês) + fix do `TypeError` de consola (classe `cat-select` partilhada). Nada commitado.
- **Nota de projecto:** `01 - Projects/Dashboard Financeiro Pessoal - Estado (2026-07-25).md` — adicionada secção "Actualização 2026-09-06"; dados agora Jan–Ago 2026.
- **`_meta/hot.md`:** "Last Updated" + facto de Dashboard Financeiro actualizados; `updated: 2026-09-06`.
- Espelhado na auto-memória: `project_finance_dashboard.md` (secção "Sessão 2026-09-06") + linha no `MEMORY.md`.

---

## 2026-09-01 — new | Série de Artifacts "modelos de ganhar dinheiro" ("guarda tudo")

- **Nota de projecto nova:** `01 - Projects/Modelos de ganhar dinheiro — série Artifacts (2026-08-31).md` — 5 Artifacts pt-PT publicados (Caça de Oportunidades, Dinheiro Esta Semana, Comprar e Vender, Vender em Digital, Playbook Faceless), URLs, sistema visual partilhado (Fraunces + IBM Plex, tema 3 estados), regra 1-pergunta-1-Artifact.
- **Nota de fonte nova:** `03 - Resources/sources/faceless-content-accounts-2026.md` — digest de pesquisa web (13 fontes, Ago 2026): critérios e método de escolha de nicho, 6 sinais de concorrência gerível + regra ≥18/25, workflow de produção em lote (2h/5 vídeos) + stack, tabela CPM por nicho, pilha de monetização com números, 11 pilares de tema para finanças pessoais, exemplos de canais faceless + PT/BR, nota YMYL.
- **`index.md`:** adicionado `[[faceless-content-accounts-2026]]` à lista de sources; a nota de projecto entra sozinha na tabela Dataview (tem `summary`).
- Espelhado na auto-memória: `project_money_models_artifact_series.md` + linha no `MEMORY.md`.

---

## 2026-08-29 — refactor | Consolidação das notas tendas-eventos (piloto)

- **4 notas de sessão fundidas numa só.** `tendas-eventos-website-2026-06-14.md`, `...-06-14b.md`, `...-07-29.md`, `...-07-30.md` → `01 - Projects/Tendas e Eventos — Site.md`. Nova estrutura: `## Estado actual` + `## Pendentes` (consolidados e deduplicados, 7 itens) + `## Lições a reter` (Satori/`next/og`, deploy Vercel do dir local) + `## Histórico de sessões` (4 subsecções cronológicas com o conteúdo técnico preservado). Frontmatter: `date: 2026-07-30` (última actividade real), `status: developing`, `summary` para a tabela Dataview do `index.md`.
- **4 originais apagados.**
- **Wikilink externo corrigido:** `Workspace — Estado Geral 2026-06-14.md` linha 52 `[[tendas-eventos-website-2026-06-14]]` → `[[Tendas e Eventos — Site]]` (era o único link de fora; os outros eram a cadeia interna "Continua em…").
- **`index.md` não precisou de edição** — a tabela de `01 - Projects` é Dataview `FROM "01 - Projects"` e a nota nova tem `summary`, aparece sozinha.
- Piloto: se o padrão servir, replicar para Viralto (11 notas soltas) e Content Factory (2).

---

## 2026-08-25b — audit | Auditoria de qualidade, 2ª ronda (8 itens)

- **`status: activo` → `active`** corrigido em `Workspace — Estado Geral 2026-06-14.md`.
- **Frontmatter completado em 26 notas genuínas** (scan fino refeito por *tipo* de nota — o scan inicial de ~57 ficheiros tinha falsos positivos: `03 - Resources/concepts|entities|sources` e `_meta/*` usam `created`/`updated` em vez de `date`, por convenção legítima, não por erro). Adicionado `title` em falta (12 notas de `01 - Projects/`, 2 `concepts/`, 3 `sources/`, 1 `04 - Archive/`); `status` em falta preenchido em 6 notas (`Dashboard Financeiro`, `Instagram Personal Brand`, `Viralto Auditoria`, `Viralto Semana 1-2`, `Workspace Cleanup`, `Viralto Animação logótipo`); 2 typos `data:`→`date:` corrigidos; `status: em-curso` (4 notas tendas-eventos) normalizado para `developing`; frontmatter completo adicionado a 3 notas de `06 - Fleeting/` que não tinham nenhum.
- **3 ficheiros lixo apagados:** `Untitled.canvas`, `06 - Fleeting/Untitled.base`, `Excalidraw/Drawing 2026-08-17 20.12.12.excalidraw.md` — todos criados por clique perdido a 17 Ago, conteúdo vazio confirmado antes de apagar.
- **`Claude Skills Inventory.md` arquivada** (`01 - Projects/` → `04 - Archive/`, `status: archived`) com aviso de staleness: as secções SPARC/Swarm/Hive-Mind/Hooks/Memory/Coordination/Agents/Analysis/GitHub/Optimization/Monitoring/Workflows/Automation (~137 skills, framework claude-flow) já não existem em `~/.claude/skills/`, que hoje tem 164 skills diferentes.
- **Bug de case-sensitivity corrigido** em `scripts/vault/vault_session.py` (repo `dima visual claude`): `RESOURCES_DIR` apontava para `03 - Resources/Concepts` (capital C), pasta real é `concepts` — funcionava por acaso no Windows, partia-se em Linux/Mac.
- **`templates/` renomeada para `05 - Templates/`** — alinhado com a config dos plugins Obsidian (`templater-obsidian/data.json`, `.obsidian/templates.json`) que já apontavam para `05 - Templates` (a pasta tinha sido despromovida em data desconhecida sem os plugins serem actualizados). Referências corrigidas em `_meta/AGENTS.md` e `_meta/CLAUDE.md`.
- **`vault_tokens.py`/`vault_ugc.py` agendados no Task Scheduler.** Descoberta importante: já existia uma task `VaultTokenSummary` (semanal, segundas 09:00) criada anteriormente, mas **desactivada e a apontar para um caminho errado** (`dima visual claude\vault_tokens.py`, ficheiro não existe aí — está em `scripts\vault\`) — nunca tinha corrido com sucesso. Corrigido o caminho e activada. Criada `VaultUGCSummary` de raiz (segundas 09:05), mesmo padrão. Ambas testadas manualmente: `vault_ugc.py` funciona e escreveu `01 - Projects/UGC Agency/pipeline-2026-08-25.md` (39 activos); `vault_tokens.py` corre sem erro mas reporta "sem calls" porque `~/.anthropic_usage.json` não tem entradas novas desde 2026-06-14 (achado, não resolvido nesta passagem — ver `hot.md` → Active Threads).
- **Aviso de staleness do `hot.md`** construído como novo passo no skill `/morning` (`.agents/skills/morning/SKILL.md`): lê o `updated:` de `hot.md`, assinala no resumo do Telegram se tiver mais de 7 dias.

---

## 2026-08-25 — audit | Auditoria de qualidade ("pensa como programador profissional")

- **Frontmatter preenchido em 17 notas de `01 - Projects/`** que não tinham YAML (título/data/tags/status/area/related), incluindo as 6 `Engine Runs/`, `UGC Outreach Runs/2026-07-04.md`, `ruflo-setup-2026-06-09.md`, `Carousel Generator — template`, `OsteoJP - Consultoria 2026`, `Portfolio Casamento/*` (2 notas), 5 notas Viralto. Conteúdo do corpo não foi tocado.
- **`index.md` — coluna Status corrigida:** ~14 células que estavam em branco (`—`) preenchidas com um dos 4 valores válidos (`active`/`developing`/`completed`/`archived`), a partir do frontmatter acabado de adicionar.
- **Investigado `scripts/vault/vault_tokens.py` e `vault_ugc.py`** (repo `dima visual claude`): código funcional e correcto (lê `~/.anthropic_usage.json` e `ugc_system/output/deals.csv`, ambos existentes), mas **nunca foram corridos em produção** — não estão no Task Scheduler nem chamados por nenhum outro script (só `vault_market.py` está ligado, via `scripts/market_agent.py`). As pastas-alvo (`02 - Areas/Token Usage/`, `01 - Projects/UGC Agency/`) não existem no vault porque nunca correram, não por bug. Decisão de agendar ou remover fica pendente (ver `hot.md` → Active Threads).
- **`hot.md` corrigido** — tinha 2 factos desactualizados desde 08-08: (1) dizia "deploy OsteoJP ao Vercel ainda pendente", já estava feito; (2) não mencionava que `lote-04`/`lote-05` do Viralto já existem (9/21 Ago). **Confirma-se que o "Active Thread" de manter `hot.md` actualizado a cada operação voltou a falhar** — desta vez só 17 dias (08-08 → 08-25), depois de já ter falhado 2 meses antes disso. Não há mecanismo automático de invalidação, só disciplina manual — continua por resolver.
- **Não alterado nesta passagem** (fora do âmbito pedido): 3 ficheiros "Untitled" criados por clique perdido a 17 Ago (`Untitled.canvas`, `06 - Fleeting/Untitled.base`, `Excalidraw/Drawing 2026-08-17 20.12.12.excalidraw.md`); numeração de pastas sem `05`/`templates` sem número; `Claude Skills Inventory.md` desactualizada desde 09 Jun.

---

## 2026-08-08 — cleanup | Limpeza geral do vault

- **Apagados:** `Untitled.canvas`, `Untitled 1.canvas` (raiz) — canvas vazios (`{}`), sem nome, criados por engano a 2 Ago
- **Corrigido:** `_meta/CLAUDE.md` e `_meta/AGENTS.md` — descreviam pastas `00-inbox/`, `01-projects/` (minúsculas, sem espaço) que já não existem; actualizados para os nomes reais (`00 - Inbox`, `01 - Projects`, etc.); removidas tabelas "Active Projects/Areas/Knowledge Base" hardcoded em `AGENTS.md` (causa da staleness — agora apontam só para `index.md`/`hot.md`); modelos e pipelines desactualizados corrigidos
- **Resolvida duplicação:** `03 - Resources/entities/MAIS AI Agency.md` tinha conteúdo integralmente duplicado de `Wiki/entities/MAIS-AI-Agency.md` (repo `dima visual claude`) sem aviso — adicionado o mesmo stub-pointer que já existia noutras 3 notas (`AI-Automation-Agency`, `ciela-ai-agency-niches-2026`, `prr-ia-nas-pme-2025`)
- **Reconstruídos do zero:** `index.md` (parado desde 2026-06-14) e `hot.md` (parado desde 2026-06-09) — ambos reflectiam menos de metade do conteúdo real do vault (38 notas em Projects vs 4 listadas)
- **Não alterado:** `04 - Archive/lint-report-2026-06-09.md` vs `04 - Archive/wiki-meta/lint-report-2026-06-08*.md` continuam em sítios diferentes — inconsistente mas inofensivo, deixado por decisão de não mexer em arquivo histórico

---

## 2026-06-09 — lint | Orphan wikilinks resolved

- **New notes created (8):**
  - `02-areas/Overnight Engine.md` — orphan referenced 6x
  - `04-archive/_MOC Projects.md` — orphan referenced 5x
  - `04-archive/UGC Agency Launch.md` — orphan referenced 6x
  - `04-archive/Market Analysis.md` — orphan referenced 1x
  - `03-resources/concepts/Prompt Library.md` — orphan linked from lint + sources
  - `03-resources/concepts/Obsidian Skills.md` — orphan linked from Claude Skills Inventory
  - `03-resources/entities/Chetan Pujari.md` — orphan linked from source
  - `03-resources/entities/Kiran Grewal.md` — orphan linked from source
  - `03-resources/entities/Ryan Frizelle.md` — orphan linked from source
- **Templates cleaned:** `area-template.md`, `resource-template.md` — placeholder links removed
- **Ignored (lint reports archived, not worth fixing):** date orphans, placeholder names, backslash artefacts
- **Result:** 0 meaningful orphans; all real references now resolve to existing notes

---

## 2026-06-09 — cleanup | Vault reorganisation

- **Cleaned:** `Clippings/` → `03-resources/sources/` (3 articles moved)
  - `src-claude-prompts-10-every-day` (Kiran Grewal, 2026-05-03)
  - `src-claude-prompts-50-steal` (Chetan Pujari, 2026-03-24)
  - `src-automate-instagram-carousels` (Ryan Frizelle, 2026-04-19)
- **Moved:** `01 - Projects/Engine Runs/2026-06-09.md` → `01-projects/`
- **Deleted:** `00-inbox/ruflo-setup-2026-06-09.md` (duplicate of 01-projects/)
- **Deleted:** `01 - Projects/` folder (empty after move)
- **Deleted:** `Clippings/` folder (empty after move)
- **Result:** PARA puro — 5 folders na raiz (00‑inbox, 01‑projects, 02‑areas, 03‑resources, 04‑archive, templates)
- **Action:** frontmatter updated on all moved files; index.md updated

---

## 2026-06-09 — save | Claude Skills Inventory

- Type: synthesis
- Location: 01-projects/Claude Skills Inventory.md
- From: conversation "quantos skills tenho. monstra" — inventário completo ~160 skills Claude Code
- Categorias: locais (43), globais (82), plugin/sistema (40+), SPARC (33), Swarm (16), Hive-Mind (14), hooks/memory/coordination/agents/github/workflows/automation

---

## 2026-06-09 — lint | Vault health check + fixes

- Pages scanned: 33
- Dead links fixed: 7 (UGC Agency Launch ×5, Prompt Library, entities/_index)
- Frontmatter fixed: 4 UGC concepts (title: adicionado)
- Orphans: 0
- Report: [[lint-report-2026-06-09]]

---

## 2026-06-09 — restructure | wiki/ + .raw/ → PARA

- Adopted: PARA system (00-inbox, 01-projects, 02-areas, 03-resources, 04-archive, templates)
- Migrated: wiki/concepts/ → 03-resources/concepts/ (12 pages)
- Migrated: wiki/sources/ → 03-resources/sources/ (3 sources)
- Migrated: wiki/entities/ → 03-resources/entities/
- Moved: wiki/questions/Research - Viralto UGC Agency Setup.md → 01-projects/
- Archived: wiki/meta/ lint reports → 04-archive/wiki-meta/
- Created: AGENTS.md (root instruction manual), index.md (root), log.md (root)
- Created: templates/ (project, area, resource, note)
- Created: 02-areas/ AI Development.md + Viralto UGC Agency.md
- Source: dreamsaicanbuy.com/blog/second-brain-obsidian-ai-karpathy

---

## 2026-06-09 — ingest | AI Concepts re-ingested (8 pages)

- Pages created: [[Anthropic SDK]], [[AI Patterns]], [[Agentic Patterns]], [[Prompt Engineering]], [[Cost Optimization]], [[MoviePy v2 Patterns]], [[Playwright Guide]], [[CPI Consumer Price Index]]
- Source: knowledge reconstruction (originals lost in PARA→wiki migration)

---

## 2026-06-08 — restructure | PARA → wiki/ + .raw/

- Deleted: 00-Home, 01-Projects, 02-Areas, 03-Resources, 04-Archive, 05-Templates, 06-Fleeting, wiki/sessions/
- Created: wiki/CLAUDE.md, wiki/domains/_index.md, .raw/web|pdf|notes|transcripts/
- Updated: CLAUDE.md root, wiki/index.md, concepts/_index.md, hot.md

---

## 2026-06-08 — autoresearch | Viralto UGC Agency Setup

- Created: [[Research - Viralto UGC Agency Setup]] (synthesis)
- Created: [[UGC Agency Business Model]], [[UGC Cold Outreach]], [[UGC Portfolio]], [[UGC Pricing]]
- Key finding: Portfolio spec em 1-2 dias → cold email 3-step → primeiro cliente em 2-4 semanas
- Pricing entrada: €40-80/vídeo

---

## 2026-06-08 — Scaffold + Lint (wiki skill)

- Scaffolded wiki/ layer over PARA vault
- Lint run: 26 issues found, all fixed
- 4 concept stubs created, frontmatter added to project pages
