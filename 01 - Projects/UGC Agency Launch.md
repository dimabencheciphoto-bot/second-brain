---
tags: project status/active
created: 2026-06-05
---

# 📱 UGC Agency Launch

## Objetivo
Sistema end-to-end para encontrar marcas e-commerce, enviar cold outreach automatizado, e gerir deals num CRM flat-file.

## Critério de Sucesso
- [ ] Pipeline de outreach a funcionar para batch de 20+ brands
- [ ] 1 cliente fechado
- [ ] Deal tracker actualizado com histórico

---

## Pipeline

```
prospect_hunter.py (Claude-assisted)
    ↓ leads CSV
cold_outreach.py (Haiku — batch mode)
    ↓ emails personalizados
deal_tracker.py
    ↓ CRM flat-file CSV
ugc_scripter.py
    ↓ scripts de vídeo para clientes
```

## Comandos

```powershell
python ugc_system/prospect_hunter.py --niche "pet products" --count 20
python ugc_system/cold_outreach.py --batch ugc_system/sample_leads.csv
python ugc_system/ugc_scripter.py --brand "Name" --product "description"
python ugc_system/deal_tracker.py --list
python ugc_system/deal_tracker.py --add
```

## Niches em Teste

| Niche | Status | Leads | Replies |
|-------|--------|-------|---------|
| Pet products | — | — | — |
| Skincare | — | — | — |

---

## Prompts em Uso

- [[Prompt Library#cold-email-personalizado]]
- [[Prompt Library#script-ugc-video]]

---

## Log de Decisões

### 2026-06-05
**Decisão:** CRM em CSV flat-file em vez de base de dados  
**Porquê:** Simplicidade; fácil de editar manualmente; sem dependências  
**Alternativa rejeitada:** SQLite (overhead desnecessário nesta fase)
