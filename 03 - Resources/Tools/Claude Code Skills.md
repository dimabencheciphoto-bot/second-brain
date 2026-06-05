# 🛠️ Claude Code — Skills Instalados

> Skills são guias de referência que o Claude Code carrega automaticamente quando o contexto é relevante. Vivem em `~/.claude/skills/`.

*Atualizado: 2026-06-05*

---

## Skills de Superpowers (Sistema Base)

| Skill | Quando é usado |
|-------|---------------|
| `superpowers:brainstorming` | Antes de qualquer implementação criativa |
| `superpowers:writing-plans` | Tarefas multi-passo antes de tocar no código |
| `superpowers:executing-plans` | Execução de planos com checkpoints |
| `superpowers:systematic-debugging` | Qualquer bug ou comportamento inesperado |
| `superpowers:test-driven-development` | Antes de escrever código de implementação |
| `superpowers:verification-before-completion` | Antes de declarar trabalho concluído |
| `superpowers:dispatching-parallel-agents` | 2+ tarefas independentes em paralelo |
| `superpowers:subagent-driven-development` | Planos com agentes independentes |
| `superpowers:using-git-worktrees` | Isolar trabalho em branches |
| `superpowers:finishing-a-development-branch` | Finalizar branches (merge, PR, cleanup) |
| `superpowers:requesting-code-review` | Antes de fazer merge |
| `superpowers:receiving-code-review` | Ao receber feedback de code review |

---

## Skills de Desenvolvimento

| Skill | Quando é usado |
|-------|---------------|
| `karpathy-guidelines` | Ao escrever, rever ou refatorar código |
| `frontend-design` | Componentes UI, layouts, CSS, UX, responsive |
| `database` | SQL, schemas, migrações, otimização de queries |
| `docker-deploy` | Dockerfiles, docker-compose, CI/CD, deploy |
| `performance` | Otimização, profiling, bottlenecks, memória |

---

## Skills de Revisão & Qualidade

| Skill | Quando é usado |
|-------|---------------|
| `code-review` | Revisão de diffs por bugs e melhorias |
| `simplify` | Simplificar código alterado |
| `security-review` | Revisão de segurança das alterações |
| `verify` | Confirmar que uma alteração funciona |

---

## Skills de Automação & Agendamento

| Skill | Quando é usado |
|-------|---------------|
| `loop` | Tarefas recorrentes em intervalos |
| `schedule` | Agentes remotos com cron |

---

## Skills de Configuração

| Skill | Quando é usado |
|-------|---------------|
| `update-config` | Configurar settings.json, hooks, permissões |
| `keybindings-help` | Personalizar atalhos de teclado |
| `fewer-permission-prompts` | Reduzir prompts de permissão |
| `init` | Gerar CLAUDE.md para um projeto |
| `run` | Lançar e testar a app |

---

## Skills de Referência

| Skill | Quando é usado |
|-------|---------------|
| `claude-api` | API Anthropic — modelos, preços, streaming, tool use |
| `skill-creator` | Criar e otimizar novos skills |

---

## Skills Telegram

| Skill | Quando é usado |
|-------|---------------|
| `telegram:configure` | Configurar o canal Telegram |
| `telegram:access` | Gerir quem pode aceder ao canal |

---

## Como Criar um Novo Skill

1. Criar pasta em `~/.claude/skills/<nome-do-skill>/`
2. Criar ficheiro `SKILL.md` com frontmatter:
```yaml
---
name: nome-do-skill
description: Use when [condições de trigger específicas]
---
```
3. O skill é carregado automaticamente na próxima sessão

---

## Skills a Considerar no Futuro

- `ci-cd` — GitHub Actions, pipelines automatizados
- `env-setup` — Ambientes virtuais, .env, dependências
