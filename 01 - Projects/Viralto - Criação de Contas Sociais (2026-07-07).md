---
title: "Viralto — Criação de Contas Sociais"
date: 2026-07-07
tags: [viralto, redes-sociais, setup]
status: developing
area: ai-dev
related: ["[[Viralto - Agência AI]]"]
summary: "Criação das contas nas 4 plataformas"
---

Status: em progresso
Projecto: [[Viralto - Agência AI]]

## Contexto

Depois de terminar o brand kit (logótipo, guidelines, bios planeadas em `viralto/brand/social_profiles.md`), começámos a criação manual das contas sociais da Viralto nas 4 plataformas: Instagram, Facebook, LinkedIn, TikTok, YouTube.

**Email das contas:** começou como Gmail (`viraltoagencia@gmail.com` — `viralto@gmail.com` já estava ocupado), migra depois para email dedicado no domínio (`contacto@viralto.pt`, Google Workspace).

## Progresso por plataforma

### Instagram — concluído
- Handle final: **@viralto.ai** (mudado a meio do processo; @viralto e @viraltoagencia indisponíveis/alterados)
- Conta Comercial, ligada à Página de Facebook Viralto

### Facebook — concluído
- Página "Viralto" criada, categoria Digital Marketing Agency
- Descrição definida (variante "C" das opções propostas)
- Capa gerada de propósito: `viralto/brand/assets/facebook-cover.png` (820×312, via `banners.py`, ainda por commitar ao git)

### Meta Business Suite — concluído
- Detectou automaticamente a Página e a conta Instagram já ligadas, sem passos manuais extra

### LinkedIn — concluído
- **Obstáculo encontrado:** primeira tentativa foi criar a Página a partir de uma conta pessoal nova sem histórico (ficou com o nome corrompido "viralto undefined", 0 conexões) — o LinkedIn bloqueou com "não tens conexões suficientes para criar uma Page". Este é um requisito real da plataforma (anti-spam), não um erro de navegação.
- **Resolução:** usar a conta pessoal real do utilizador (nome próprio, conexões existentes) como administrador, via `linkedin.com/company/setup/new/`
- Página de empresa "Viralto" criada: logo (`badge-icon-dark.png`), banner (`linkedin-banner.png`), tagline "Automação e IA para o teu negócio.", secção "Sobre" numa variante orientada a resultados/vendas (sem a palavra "jargão")

### TikTok — em progresso
- Registo directo no browser (desktop) ficou bloqueado num ecrã de verificação por QR code — TikTok exige confirmação via app para contas novas sem histórico
- **Resolução:** criar a conta como segunda conta dentro da app onde o utilizador já tem a sua conta pessoal (Perfil → Adicionar conta) — este caminho passou sem bloqueios
- Handle final: **@viralto.ai** (consistente com Instagram)
- Foto de perfil e bio já colocadas
- Pendente: mudar para conta comercial (opção encontrada em Definições → "Registo comercial", não em "Gerir conta" como nas versões antigas)

### YouTube — ainda não iniciado

## Lições a reter

- **LinkedIn** exige um mínimo de conexões na conta pessoal para poder criar uma Company Page — ao criar contas de marca a partir do zero, mais vale usar desde logo uma conta pessoal já estabelecida como administradora, em vez de criar uma conta pessoal nova só para o efeito.
- **TikTok** aplica verificação anti-bot mais agressiva a registos novos feitos via browser desktop; criar a conta dentro da app do telemóvel (como conta adicional de um utilizador já verificado) evita esse bloqueio.
- Nomenclatura final ficou consistente em **@viralto.ai** no Instagram e TikTok (não @viralto simples, que estava indisponível/tomado).

## Próximos passos

1. Terminar conversão da conta TikTok para comercial
2. Criar canal YouTube (foto, banner `youtube-banner.png`, descrição)
3. Actualizar checklist final em `viralto/brand/social_profiles.md`
4. Decidir quando fazer commit do `facebook-cover.png` (ainda por decidir pelo utilizador)
5. Primeiro lote de conteúdo para as 4 plataformas
