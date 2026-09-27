---
title: "PC Health"
tags: [area, pc, performance, manutenção]
---

# PC Health — Manutenção e Performance

Máquina: 13th Gen Intel Core i5-13600K (14 núcleos/20 threads), 64 GB RAM, NVIDIA RTX 4070 SUPER, SSD interno Crucial CT1000P3PSSD8 NVMe 932 GB, Windows 11 Pro. Ferramenta de diagnóstico principal: LatencyMon (DPC/ISR).

## 2026-09-19/20 — Primeira intervenção grande

**Contexto:** "o computador devia voar mas não é o caso" — investigação com LatencyMon revelou latências de DPC/ISR elevadas ligadas a GPU e Wi-Fi, mais atrito acumulado de software (arranque cheio, disco quase cheio, ferramentas "anti-performance" a correr).

**Correcções aplicadas (todas confirmadas com evidência — comandos/screenshots):**
- **NVIDIA App:** Power Management Mode → Maximum Performance. `nvlddmkm.sys` desceu de picos altos para baseline ~0,1-0,5 ms.
- **PCIe ASPM:** desligado via `powercfg` (`SUB_PCIEXPRESS`/`ASPM` = 0). Confirmado que se mantém após restart.
- **Wi-Fi (Intel Wi-Fi 6E AX211 160MHz):** MIMO Power Save Mode → No SMPS, Packet Coalescing → Disabled, U-APSD support → Disabled, "permitir que o computador desligue este dispositivo" → desmarcado. `ndis.sys` desceu de ~1117 ms total para baseline. Confirmado que se mantém após restart (via `MSPower_DeviceEnable`, `Enable=False`).
- **Disco:** desinstalado o Steam; ficou órfã a pasta do jogo Delta Force (Steam já não existia para o desinstalador o remover). Apagados manualmente `Delta Force` (116,4 GB) + `Steamworks Shared` (0,22 GB) + entrada de registo órfã `Steam App 2507950`. Disco C: passou de ~90% cheio para 25,3% livre (235 GB livres de 930 GB).
- **Arranque (`StartupApproved\Run`, método reversível via Gestor de Tarefas):** desactivados Discord, Adobe Acrobat Synchronizer, Wargaming.net Game Center, Steam, GoogleChromeAutoLaunch, Gaijin.Net Updater, Mem Reduct.
- **Suspensão automática:** `powercfg /change standby-timeout-ac 0` e `hibernate-timeout-ac 0` — o PC estava a entrar em ciclos de suspensão/hibernação sozinho ao longo do dia (confirmado no Visualizador de Eventos, múltiplos "Hibernate from Sleep - Fixed Timeout"), o que causava picos artificiais de DPC (~114 ms num caso) nos momentos de "acordar". Já não adormece sozinho ligado à corrente.
- **Pendente (precisa de admin, não resolvido):** atalho `Samsung Drive Manager Real-Time.lnk` na pasta Common Startup — acesso negado sem elevação.
- **Nota:** `OneDrive` já estava desactivado no arranque antes desta sessão (não fomos nós) — por confirmar com o Dima se é intencional. O `OneDriveStandaloneUpdater` continua a correr via Tarefa Agendada independente disso.

**Veredicto no fim da sessão:** hardware e config no ponto — CPU 7% de carga, 54 GB RAM livre em 64 GB, disco com espaço de sobra. O LatencyMon continua a acusar picos ocasionais de 10-20 ms de latência interrupt-to-process (o teste é calibrado para produção de áudio profissional, limiares extremos) sem sintomas reais reportados pelo utilizador (sem cortes de áudio audíveis) — não vale a pena perseguir mais este número.

**Ferramenta "Mem Reduct" desinstalada do arranque:** o alarme vermelho que mostrava ("System Working Set" a 74%) é comportamento normal do cache interno do Windows, não falta de RAM real (Physical memory estava a 15% de uso). Ferramentas de "limpar RAM" são contraproducentes com 64 GB disponíveis — forçam o Windows a descartar cache que depois tem de recarregar do disco.

## Baseline de referência (para comparar em futuras análises)
- CPU load ocioso: ~1-7%
- RAM livre: ~54 GB de 64 GB
- Disco C: 25,3% livre (930 GB total)
- `nvlddmkm.sys` highest DPC: ~0,1-0,5 ms (bom)
- `ndis.sys` highest DPC: ~0,3-0,7 ms (bom)
- `storport.sys` highest DPC: <0,05 ms (bom)
