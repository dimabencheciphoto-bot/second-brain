# 🤝 Agentic Patterns — Multi-Agent & Orquestração

> Padrões específicos para sistemas com múltiplos agentes ou loops autónomos.

---

## Orquestradores vs. Subagentes

```
Orquestrador (Sonnet/Opus)
    ├── Subagente A: Pesquisa (Haiku)
    ├── Subagente B: Geração (Haiku)
    └── Subagente C: Validação (Haiku)
```

**Regra:** orquestrador pensa e coordena; subagentes executam tasks atómicas.  
O orquestrador usa modelo mais capaz; subagentes usam modelo mais rápido.

---

## Tool Use (Function Calling)

```python
tools = [
    {
        "name": "search_web",
        "description": "Pesquisa na web e retorna resultados relevantes",
        "input_schema": {
            "type": "object",
            "properties": {
                "query": {"type": "string", "description": "Query de pesquisa"},
                "num_results": {"type": "integer", "default": 5}
            },
            "required": ["query"]
        }
    }
]

response = client.messages.create(
    model="claude-sonnet-4-6",
    tools=tools,
    messages=[{"role": "user", "content": "Pesquisa as últimas notícias de AI"}]
)

# Verificar se o modelo quer usar uma tool
if response.stop_reason == "tool_use":
    tool_call = next(b for b in response.content if b.type == "tool_use")
    result = execute_tool(tool_call.name, tool_call.input)
    # Continuar conversa com resultado
```

---

## Agentic Loop Robusto

```python
MAX_ITERATIONS = 10

messages = [{"role": "user", "content": task}]

for i in range(MAX_ITERATIONS):
    response = client.messages.create(
        model="claude-sonnet-4-6",
        tools=tools,
        messages=messages
    )
    
    if response.stop_reason == "end_turn":
        break  # Agente terminou
    
    if response.stop_reason == "tool_use":
        # Executar tool e adicionar resultado
        tool_results = []
        for block in response.content:
            if block.type == "tool_use":
                result = execute_tool(block.name, block.input)
                tool_results.append({
                    "type": "tool_result",
                    "tool_use_id": block.id,
                    "content": str(result)
                })
        
        messages.append({"role": "assistant", "content": response.content})
        messages.append({"role": "user", "content": tool_results})

else:
    raise RuntimeError(f"Agente excedeu {MAX_ITERATIONS} iterações")
```

---

## Guardrails Essenciais

```python
def validate_output(output: str, schema: dict) -> bool:
    """Valida output do modelo antes de usar."""
    try:
        data = json.loads(output)
        # validar contra schema
        return True
    except json.JSONDecodeError:
        return False

def sanitize_tool_input(tool_name: str, inputs: dict) -> dict:
    """Nunca passar inputs não validados a tools com side effects."""
    SAFE_TOOLS = {"search_web", "read_file"}
    DANGEROUS_TOOLS = {"write_file", "execute_code", "send_email"}
    
    if tool_name in DANGEROUS_TOOLS:
        # Requerer confirmação ou validação adicional
        confirm = input(f"Confirmar: {tool_name}({inputs})? [y/N] ")
        if confirm.lower() != "y":
            raise PermissionError("Tool execution denied")
    
    return inputs
```

---

## Padrões de Memória

| Tipo | Implementação | Quando usar |
|------|--------------|-------------|
| **In-context** | Mensagens na conversa | Sessão única curta |
| **Ficheiro** | JSON/CSV em disco | Estado persistente simples |
| **Embedding** | Vector DB (Chroma, etc.) | Conhecimento grande |
| **Structured** | SQLite/PostgreSQL | Dados relacionais |

---

## Ver também

- [[AI Patterns]] — padrões base não-agenticos
- [[Prompt Library#system-prompts]] — system prompts para agentes
