# 📖 Learning Log

> Uma aprendizagem por semana. Qualidade > quantidade.

---

## Formato

```
### YYYY-MM-DD — [Título]
**Fonte:** paper / artigo / experimento / vídeo
**Insight:** o que aprendi em 2-3 frases
**Aplicar em:** onde posso usar isto
**Link:** [[nota completa se existir]]
```

---

## 2026

### 2026-06-05 — Notepad guarda UTF-8 com BOM
**Fonte:** debug do .env hoje  
**Insight:** O Notepad do Windows guarda ficheiros UTF-8 com BOM (Byte Order Mark). A biblioteca `python-dotenv` não lê BOM, resultando em key vazia. Solução: usar PowerShell com `[System.Text.UTF8Encoding]::new($false)` para escrever sem BOM.  
**Aplicar em:** sempre que criar .env ou ficheiros de config pelo Notepad  
**Link:** [[Overnight Engine]]

### 2026-06-05 — Fórmulas de título > instrução genérica
**Fonte:** experiência com script_writer.py  
**Insight:** Dar ao LLM uma lista de templates a preencher produz resultados mais consistentes do que pedir para "ser criativo e SEO-friendly". O modelo é bom a escolher e preencher; mau a inventar estrutura de raiz.  
**Aplicar em:** qualquer prompt de geração onde consistência > criatividade  
**Link:** [[Prompt Library]]

### 2026-06-05 — Sistema PARA para AI Developers
**Fonte:** Tiago Forte + adaptação própria  
**Insight:** Separar Projects (deadline) de Areas (contínuo) elimina a culpa de não "acabar" um area. Resources são conhecimento atemporal; Archive é histórico acessível.  
**Aplicar em:** organização deste vault  
**Link:** [[Dashboard]]

---

## Fila de Leitura

- [ ] Attention Is All You Need (transformer original)
- [ ] Constitutional AI — Anthropic
- [ ] ReAct: Synergizing Reasoning and Acting in LLMs
- [ ] Chain-of-Thought Prompting Elicits Reasoning
- [ ] Toolformer: Language Models Can Teach Themselves to Use Tools
