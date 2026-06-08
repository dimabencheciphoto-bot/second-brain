# 🎯 Musa 1.0 — Dominar o Ecossistema Claude

---
tags: project status/active
created: 2026-06-06
deadline: —
---

## Objetivo
Aprender fazendo — dominar todas as ferramentas do ecossistema Claude para optimizar o trabalho diário e abrir novas fontes de rendimento.

## Critério de Sucesso
- [ ] Completar os 7 módulos com pelo menos 1 projecto prático por módulo
- [ ] Ter um sistema de trabalho pessoal documentado e optimizado
- [ ] Identificar 1 oportunidade concreta de monetização nova

---

## 📋 Módulos

### Módulo 1 — Claude Code CLI ✅ 2026-06-06
- [x] Comandos essenciais e flags úteis
- [x] Como funciona o CLAUDE.md e para que serve
- [x] Hooks — automatizar acções antes/depois de tarefas (Telegram activo)
- [x] Permissões e modos de execução

### Módulo 2 — Claude Desktop + MCP ✅ 2026-06-08
- [x] O que é MCP (Model Context Protocol)
- [x] Ligar servidores MCP ao Claude Desktop
- [x] MCP úteis: filesystem, Gmail, Telegram, browser
- [ ] Criar o teu próprio servidor MCP simples

### Módulo 3 — Claude no VS Code ✅ 2026-06-08
- [x] Instalar e configurar a extensão
- [x] Workflow de desenvolvimento integrado
- [x] Usar Claude para review, refactor e debug em contexto

### Módulo 4 — Telegram + Telemóvel ✅ 2026-06-08
- [x] Como o bot está ligado a esta sessão
- [x] Enviar comandos ao Claude pelo telemóvel
- [x] Receber notificações de scripts e pipelines (notify_failure.py)
- [x] Enviar ficheiros (HTML reports) directamente pelo Telegram via `reply` + `files`

### Módulo 5 — Projectos & Agentes ✅ 2026-06-08
- [x] Criar subagentes para tarefas paralelas ✅
- [x] Worktrees — trabalhar em branches isoladas ✅
- [x] Sessões e contexto — como gerir conversas longas ✅
- [x] Skills — criar e usar skills personalizadas ✅ (`/musa-status` criada em `.agents/skills/musa-status/`)

### Módulo 6 — Optimizar Tarefas ✅ 2026-06-08
- [x] Hooks automáticos para tarefas recorrentes — notify_failure.py activo ✅ 2026-06-08
- [x] Loops e schedules — tarefas periódicas ✅ 2026-06-08
- [x] Memory — fazer o Claude lembrar preferências ✅ 2026-06-08
- [x] Construir o teu workflow pessoal ideal ✅ 2026-06-08

### Módulo 7 — Monetizar 🔄 em curso
- [x] UGC Agency — nome escolhido: **Viralto** ✅ 2026-06-08
- [ ] Viralto — registar domínio + handles sociais
- [ ] Viralto — portfolio mínimo (Carrd/Notion + 2-3 vídeos demo)
- [ ] Viralto — primeiro batch de outreach com 20 leads
- [ ] Overnight Engine — corrigir crash ffmpeg + verificar YouTube
- [ ] Automatização de serviços para clientes
- [ ] Produtos digitais (prompts, templates, sistemas)

---

## 🗒️ Log de Progresso

### 2026-06-08 (cont. 3)

**Módulo 6D completo — Workflow Pessoal.**

O workflow pessoal documentado e implementado como skill `/morning`:

**Rotina diária:**
1. `/morning` → briefing completo de todos os pipelines + agenda → Telegram
2. Hooks activos em background (notify_failure.py detecta crashes)
3. Loop de monitorização: engine.log (erros) + output/*.mp4 (aprovação antes de publicar)
4. `/musa-status` para check manual a qualquer hora

**Ciclo de trabalho:**
- Claude Code no VS Code para desenvolvimento
- Telegram como interface móvel (comandos + notificações)
- Memory garante continuidade entre sessões
- Skills (`/morning`, `/musa-status`) como shortcuts para tarefas recorrentes

**Automações sempre activas (Task Scheduler):**
- 02:00 — Overnight Engine (trends → vídeo → publicar)
- On error — Telegram notification via hook

**Skills criadas:** `/musa-status`, `/morning`

### 2026-06-08 (cont. 2)
**Módulo 2 completo.** Explorada a hierarquia de config MCP: Claude Desktop (`claude_desktop_config.json`) tem filesystem/fetch/memory; plugins Claude Code (global settings.json) têm Telegram/superpowers/context7; MCPs cloud (Gmail, Drive, Playwright) carregados automaticamente. Usado Gmail MCP ao vivo para buscar emails.

**Módulo 6A completo.** Hook `notify_failure.py` construído e activo. Descoberta chave: `tool_response` do Bash não tem `exit_code` — tracebacks vão para `stdout`. Detecção por presença de "Traceback" no output combinado. Notificação Telegram a funcionar.

**Módulo 6B completo.** Sistema de memória explorado: MEMORY.md como índice, ficheiros `.md` por tópico, sincronização automática em SessionStart/Stop via `auto-memory-hook.mjs`.

**Módulo 7 em curso — Viralto.** Nome escolhido para a agência UGC. Posicionamento: performance UGC para e-commerce EN/EU. Tagline: "We make brands impossible to ignore." Próximos passos: domínio + handles → portfolio mínimo → outreach batch 20 leads. `viralto.com` e `@viralto` parecem livres.

**Módulo 6C completo — Loops.** `/loop` em modo dinâmico: Monitor como sinal primário (event-driven), ScheduleWakeup como heartbeat de segurança. Dois loops activos: engine.log (erros + auto-fix) e output/*.mp4 (aprovação humana antes de publicar). 10 exemplos de loops úteis documentados.

**Módulo 5D completo — Skills.** Skill `/musa-status` criada em `.agents/skills/musa-status/SKILL.md`. Executa briefing de todos os pipelines e envia para Telegram. Skills são invocadas pelo utilizador com `/nome`.

**Módulo 5A completo — Subagentes.** Agent tool lançado ao vivo: subagente leu os 3 pipelines (engine crash ffmpeg, 5 leads UGC sem status, market report up-to-date) e voltou com resumo em <2min. Contexto principal ficou limpo.

**Módulo 5B completo — Worktrees.** Git inicializado no projecto. `git worktree add` cria sandbox numa branch separada. `isolation: "worktree"` no Agent tool faz isto automaticamente. Projecto em `master`, worktree em branch própria, merge só se resultar.

**Módulo 5C completo — Sessões.** Session ID persiste no JSONL. `/compact` comprime e liberta contexto. Memória (`MEMORY.md` + ficheiros `.md`) carregada em cada `SessionStart` — garante continuidade entre sessões. Hook `auto-memory-hook.mjs` sincroniza em `SessionStart` e `PreCompact`.

**Módulo 4 completo.** Canal Telegram bidirecional confirmado. `reply` com `files:[]` envia qualquer ficheiro (HTML, CSV) directamente para o telemóvel. market_report.html enviado ao vivo como teste.

### 2026-06-06
**Início do projecto.** Estrutura definida, 7 módulos identificados. Módulo 4 (Telegram) e Módulo 7 (UGC/Engine) já têm base construída.

---

## 🔗 Recursos

- [[Business Overview]]
- [[UGC Agency]]
- [[Content Engine KPIs]]
- [[AI Development]]
- [[Prompt Library]]

---

*Tags: #project #musa #claude #learning*
