# Ruflo Setup Completo — 2026-06-09

## O que é o Ruflo
Plataforma de orquestração de agentes AI (v3.10.37) integrada no workspace dima visual claude. Camada de memória, automação e coordenação de agentes em paralelo.

## Setup feito hoje

### 1. Memória persistente (HNSW vectorial)
6 entradas indexadas com embeddings semânticos:
- overnight-engine, viralto-ugc, market-agent, second-brain, workspace conventions
- viralto:leads-skincare-research (MUSA Natural + Catarina Barbosa)

### 2. Hooks de aprendizagem
- Pretrain: 2033 ficheiros → 77 padrões
- Pre/post edit aprende com cada alteração
- Model routing automático: haiku (simples, -96% custo) vs opus (complexo)

### 3. Neural training
100 padrões — coordination, performance, optimization. MicroLoRA/WASM <1μs.

### 4. Swarm V3
Hierarchical-mesh, 15 agentes, auto-scale. Usado para research Viralto.

### 5. Autopilot activo
Max 50 iterações, 240 min timeout. Retenta falhas automaticamente.

### 6. Integrações novas
- `overnight_engine/log_watcher.py` — engine.log → Telegram em tempo real
- `/morning` skill — ruflo memory search integrado no resumo matinal

## Leads Viralto encontrados
| Marca | País | Prioridade |
|---|---|---|
| MUSA Natural Cosmetics (Fundão) | PT | Máxima |
| Catarina Barbosa Skincare (Milfontes) | PT | Alta |
| gh by Gema Herrerías (Sevilha) | ES | Média |

**Insight:** UGC 5x mais eficaz que conteúdo de marca. Foco: <10K IG + loja online + zero vídeo.

## Próximos passos
- [ ] Testar /morning com ruflo memory
- [ ] Cold emails MUSA Natural + Catarina Barbosa
- [ ] .env credentials overnight engine
- [ ] log_watcher.py em paralelo com engine

## Comandos ruflo
```bash
ruflo memory search -q "query"
ruflo analyze diff --risk
ruflo swarm start --objective "..." --strategy research --max-agents 4
ruflo hooks model-route -t "tarefa"
```

---
*Sessão Claude Code 2026-06-09*
