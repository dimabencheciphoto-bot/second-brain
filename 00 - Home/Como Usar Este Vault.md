# 📖 Como Usar Este Vault

## Princípios Base

### 1. Capture Tudo, Processa Depois
- Ideia → nota em [[06 - Fleeting]] (sem organizar)
- Semanal → processar fleeting → mover para PARA

### 2. Linkar Agressivamente
- `[[Nome da nota]]` para criar links
- Obsidian mostra o graph view — o valor está nas conexões

### 3. Um Único Local para Cada Coisa
- Prompt testado → [[Prompt Library]]
- Padrão de código → [[AI Patterns]] ou [[Agentic Patterns]]
- Aprendizagem → [[Learning Log]]
- Paper → `03 - Resources/Papers/`

---

## Fluxo de Trabalho Diário

```
Morning  → Abrir Daily Note (Cmd+Shift+D)
           → Definir 3 prioridades
           → Ligar ao projeto ativo

Durante  → Ideias → Fleeting
           → Experimentos → Experiment Log template
           → Descobertas → nota em Resources

Evening  → Preencher End of Day no Daily Note
           → Processar Fleeting se houver tempo
```

---

## Fluxo Semanal (30 min)

1. Processar [[06 - Fleeting]] → mover/linkar
2. Actualizar tabelas em [[_MOC Projects]]
3. Adicionar entrada em [[Learning Log]]
4. Actualizar métricas no [[Dashboard]]

---

## Templates Disponíveis

| Template | Atalho | Usar quando |
|----------|--------|-------------|
| [[Daily Note]] | Cmd+Shift+D | Todo os dias |
| [[Project Template]] | Duplicar | Novo projeto |
| [[Experiment Log]] | Duplicar | Testar hipótese de AI |
| [[Paper Note]] | Duplicar | Ler paper de research |
| [[Prompt Template]] | Duplicar | Documentar prompt novo |

---

## Plugins Recomendados (instalar em Obsidian)

1. **Templater** — templates com lógica (substitui o core Templates)
2. **Dataview** — queries dinâmicas (tipo SQL para as tuas notas)
3. **Calendar** — navegação de daily notes
4. **Obsidian Git** — backup automático para GitHub
5. **Kanban** — board de projetos visual

---

## Atalhos Úteis

| Ação | Atalho |
|------|--------|
| Nova nota | `Cmd+N` |
| Abrir nota | `Cmd+O` |
| Daily note | `Cmd+Shift+D` |
| Graph view | `Cmd+Shift+G` |
| Toggle preview | `Cmd+E` |
| Inserir link | `[[` |
| Inserir tag | `#` |

---

## Estrutura de Pastas

```
Second Brain/
├── 00 - Home/          → Dashboard + este guia
├── 01 - Projects/      → Trabalho ativo com deadline
├── 02 - Areas/         → Responsabilidades contínuas
│   ├── AI Development/
│   ├── Learning/
│   └── Business/
├── 03 - Resources/     → Conhecimento atemporal
│   ├── Models/         → Claude, comparações
│   ├── Frameworks/     → SDKs, ferramentas
│   ├── Papers/         → Research papers
│   ├── Prompts/        → Prompt Library
│   └── Concepts/       → Padrões, conceitos
├── 04 - Archive/       → Projetos concluídos
├── 05 - Templates/     → Templates (não editar directamente)
└── 06 - Fleeting/      → Captura rápida + Daily Notes
```
