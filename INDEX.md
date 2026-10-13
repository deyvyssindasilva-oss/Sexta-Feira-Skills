---
title: SEXTA FEIRA Ecosystem
aliases:
  - SEXTA FEIRA
  - SEXTA FEIRA Ecosystem
  - SEXTA FEIRA Skills
  - SEXTA FEIRA Hub
  - Main Hub
tags:
  - SEXTA FEIRA
  - ecosystem
  - hub
  - orchestration
cssclasses: []
---

# 🌐 SEXTA FEIRA Ecosystem — Master Index

**15 skills verificadas** | Zero dependências externas | Output em PT-BR

---

## 📡 Core — Automação & Execução

- [[SextaFeiraSwarm|🐝 Swarm]] — Orquestração multi-agente adaptável. Detecta modelo, pergunta, spawna workers reais via pane_spawn. 6 templates: [[decision]], [[brainstorm]], [[review]], [[plan]], [[squad-dev]], [[custom]].
- [[SextaFeiraBeast|⚡ Beast]] — Detecção de ambiente: CLI, provedor, modelo, OS, MCP tools. 4 camadas de detecção real.
- [[SextaFeiraCap|🛡️ Cap]] — Quality gates: necessidade, clareza, alucinação, token worth, isolamento de erro. 5 gates executáveis com bypass rules.

## 🧠 Memória & Construção

- [[SextaFeiraMemory|🧠 Memory]] — Memória persistente: auto-write em `.sextafeira/.memory/`, INDEX.md, resume de sessão. "Opa me lembrei!" nativo.
- [[SextaFeiraForge|🔨 Forge]] — Criação de skills: anti-duplicata consulta [[SextaFeiraAtlas|Atlas]], teste em worker, 7 steps.

## 📋 Planejamento & Organização

- [[SextaFeiraObsidian|📓 Obsidian]] — Planejamento via Mission API + fallback `.md`. Continuidade de sessão automática.
- [[SextaFeiraCompany|🏢 Company]] — Org graph hierárquico: validação tree, anti-ciclo, anti-órfão. CEO Carlos root.
- [[SextaFeiraRecruit|🎯 Recruit]] — Recrutamento com fontes REAIS: consulta [[SextaFeiraAtlas|Atlas]] + [[SextaFeiraMemory|Memory]]. Sem pool fictício.

## 🔌 Integração & Análise

- [[SextaFeiraMCP|🔌 MCP]] — Hub MCP: 17 servers verificados (Neon, Supabase, PostgreSQL, GitHub, Stripe, etc). Comandos reais.
- [[SextaFeiraAnalytica|🔬 Analytica]] — Análise de documentos 7 lentes: engenharia, educação, financeiro, admin, científico, projeto, legal. PDF/CSV/XLSX/DOCX.
- [[SextaFeiraSecurityAudit|🛡️ SecurityAudit]] — Scanner: script bash embarcado, 5 fases (git, patterns, entropy, deps, binary). Nenhuma dependência externa.

## 🧪 QA & DevOps

- [[SextaFeiraTest|🧪 Test]] — QA: geração automática de testes (jest/pytest/go/cargo), execução, cobertura, CI pipeline.
- [[SextaFeiraDeploy|🚀 Deploy]] — CI/CD: pipelines GitHub Actions/GitLab CI, build, release semântico, rollback, checklist safe deploy.

## 🌐 Externas

- [[SextaFeiraComposio|🌐 Composio]] — Registry de skills externas: 892 skills verificadas (ComposioHQ/awesome-claude-skills). Referência segura, sem clone.

## 🔍 Catálogo

- [[SextaFeiraAtlas|🗺️ Atlas]] — Master catalog local: 15 skills, busca por keyword, redirect pra Forge quando skill não existe.

---

## 🔗 Conexões do Grafo (todas as skills)

Cada skill referencia todas as outras:

- [[SextaFeiraSwarm]] → [[SextaFeiraCap]], [[SextaFeiraMemory]], [[SextaFeiraBeast]], [[SextaFeiraAtlas]], [[SextaFeiraForge]]
- [[SextaFeiraBeast]] → [[SextaFeiraSwarm]], [[SextaFeiraMemory]], [[SextaFeiraAtlas]]
- [[SextaFeiraCap]] → [[SextaFeiraMemory]], [[SextaFeiraSwarm]], [[SextaFeiraAtlas]]
- [[SextaFeiraMemory]] → [[SextaFeiraObsidian]], [[SextaFeiraSwarm]], [[SextaFeiraCap]]
- [[SextaFeiraForge]] → [[SextaFeiraAtlas]], [[SextaFeiraCap]], [[SextaFeiraMemory]]
- [[SextaFeiraObsidian]] → [[SextaFeiraMemory]], [[SextaFeiraSwarm]], [[SextaFeiraCap]]
- [[SextaFeiraCompany]] → [[SextaFeiraRecruit]], [[SextaFeiraMemory]], [[SextaFeiraSwarm]], [[SextaFeiraAtlas]], [[SextaFeiraCap]]
- [[SextaFeiraRecruit]] → [[SextaFeiraCompany]], [[SextaFeiraAtlas]], [[SextaFeiraMemory]], [[SextaFeiraForge]], [[SextaFeiraCap]]
- [[SextaFeiraMCP]] → [[SextaFeiraAtlas]], [[SextaFeiraCap]], [[SextaFeiraSwarm]]
- [[SextaFeiraAnalytica]] → [[SextaFeiraMemory]], [[SextaFeiraCap]], [[SextaFeiraMCP]], [[SextaFeiraSwarm]], [[SextaFeiraObsidian]]
- [[SextaFeiraSecurityAudit]] → [[SextaFeiraMemory]], [[SextaFeiraCap]], [[SextaFeiraForge]]
- [[SextaFeiraTest]] → [[SextaFeiraSwarm]], [[SextaFeiraForge]], [[SextaFeiraCap]]
- [[SextaFeiraDeploy]] → [[SextaFeiraTest]], [[SextaFeiraSwarm]], [[SextaFeiraCap]]
- [[SextaFeiraComposio]] → [[SextaFeiraAtlas]], [[SextaFeiraForge]]
- [[SextaFeiraAtlas]] → [[SextaFeiraForge]], [[SextaFeiraComposio]]

---

## 🏷️ Tags por Domínio

- `#automation` → [[SextaFeiraSwarm]], [[SextaFeiraBeast]], [[SextaFeiraCap]]
- `#memory` → [[SextaFeiraMemory]]
- `#planning` → [[SextaFeiraObsidian]], [[SextaFeiraCompany]]
- `#recruitment` → [[SextaFeiraRecruit]]
- `#integration` → [[SextaFeiraMCP]], [[SextaFeiraComposio]]
- `#analysis` → [[SextaFeiraAnalytica]]
- `#security` → [[SextaFeiraSecurityAudit]]
- `#testing` → [[SextaFeiraTest]]
- `#deployment` → [[SextaFeiraDeploy]]
- `#catalog` → [[SextaFeiraAtlas]]
- `#forge` → [[SextaFeiraForge]]

---

> **Criador:** Takamura | **v3.4.1** | **Skills:** 15 locais | **Grafo:** ~225 arestas
