# 🧠 Second Brain — AI Developer

> *"Your mind is for having ideas, not holding them."* — David Allen

---

## ⚡ Quick Capture

→ `Ctrl+Shift+D` para Daily Note de hoje · `Ctrl+N` para nota rápida em [[06 - Fleeting]]

---

## 🔥 Foco Atual

```
AGORA     →  vamos compear o dashboard
HOJE      →  trabalhar no ucg agency
SEMANA    →  novos competencias
```

---

## 🚀 Projetos Ativos

```dataview
TABLE WITHOUT ID
  file.link AS "Projeto",
  status AS "Estado"
FROM "01 - Projects"
WHERE contains(tags, "project") AND contains(tags, "status/active")
SORT file.name ASC
```

---

## ✅ Tasks em Aberto

```dataview
TASK
FROM "01 - Projects"
WHERE !completed
LIMIT 10
```

---

## 🎬 Últimas Runs do Engine

```dataview
TABLE WITHOUT ID
  file.link AS "Data",
  file.mtime AS "Hora"
FROM "01 - Projects/Engine Runs"
SORT file.name DESC
LIMIT 7
```

---

## 📝 Daily Notes Recentes

```dataview
LIST
FROM "06 - Fleeting"
WHERE file.name != "Business" AND file.name != "Learning"
SORT file.name DESC
LIMIT 5
```

---

## 📁 Sistema PARA

| Área | Link |
|------|------|
| 🚀 Projects | [[_MOC Projects]] |
| 🌐 Areas | [[_MOC Areas]] |
| 📚 Resources | [[_MOC Resources]] |
| 🗄️ Archive | [[04 - Archive]] |
| 👤 Perfil | [[Sobre Mim]] |
| 📖 Como usar | [[Como Usar Este Vault]] |

---

## 🤖 AI Toolkit Rápido

- **Modelos** → [[Claude Models]] · [[Model Comparison]]
- **Prompts** → [[Prompt Library]]
- **Padrões** → [[AI Patterns]] · [[Agentic Patterns]]
- **Mercados** → [[Market Agent]] · [[Market Analysis]]

---

## 🗓️ Ritual Semanal

- [ ] Processar [[06 - Fleeting]] → mover para PARA
- [ ] Atualizar estado dos projetos ativos
- [ ] Registar aprendizagem em [[Learning Log]]
- [ ] Rever métricas de custo/tokens

---

*Vault: [dimabencheciphoto-bot/second-brain](https://github.com/dimabencheciphoto-bot/second-brain) · Criado: 2026-06-05*
