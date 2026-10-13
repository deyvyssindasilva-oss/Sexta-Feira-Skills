---
name: sexta-feira
description: >
  Complete SEXTA FEIRA ecosystem orchestrator. Fires on: sexta-feira, sexta feira,
  swarm, agent, orchestrate, decide, brainstorm, review, plan, squad, spawn,
  delegate, quality, goal, project, recruit, forge, atlas, memory, beast, cap,
  obsidian, Carlos, MCP, connect, database, integration, company, org, hire,
  CEO, graph, team, department, analyze, document, PDF, CSV, XLSX, engineering,
  mentor, study, professor, analisar, documento, security, audit, scan, inject,
  malware, vulnerability, test, deploy, CI/CD, pipeline, QA, release,
  externo, external, plugin, composio.
  Central hub routing to 15 specialized sub-skills.
  Auto-detects environment and adapts routing. All output in PT-BR.
compatibility:
  requires: []
  optional:
    - All 12 sub-skills (each optional — degrades gracefully)
---

# SEXTA FEIRA Ecosystem v3.4

**Criador:** Takamura  
**Idioma:** Skills in English | All output in PT-BR

---

## Dashboard de Ativação

Ao ativar, executar na ordem:

```
1. Detectar ambiente (CLI + MCP tools + modelo)
2. Verificar skills disponíveis (ls .sextafeira/*/SKILL.md)
3. Mostrar dashboard
4. Se sessão anterior existir → sugerir continuidade
```

### Template do Dashboard

```
╔══════════════════════════════════════════════╗
║         SEXTA FEIRA ECOSYSTEM v3.3            ║
╠══════════════════════════════════════════════╣
║  📡 Ambiente: [CLI detectado]                ║
║  🤖 Modelo:   [modelo ativo]                 ║
║  👤 Usuário:  [nome detectado]               ║
║                                              ║
║  📦 Skills:   [X]/15 disponíveis             ║
║  🔌 MCP Tools: [sim | não | parcial]         ║
║  🐝 Swarm:    [nativo | descritivo | ausente]║
║  💾 Missões:  [N] ativas                     ║
╚══════════════════════════════════════════════╝
```

### Fallback por Disponibilidade

| Skill | Sem a pasta | Sem MCP tools | Degrada pra |
|-------|------------|---------------|-------------|
| Swarm | Usa archive/ templates | Modo descritivo | Planejamento manual |
| Company | Alerta "não disponível" | mission_* indisponível | Tracking manual |
| Obsidian | Alerta | mission_* indisponível | Arquivos .md simples |
| Cap | Pula verificação | Verificação conceitual | Aviso sem enforcement |
| MCP | Não bloqueia | Não aplicável | Apenas referência |
| Analytica | Leitura direta arquivo | Leitura direta | Sem enhancement |
| SecurityAudit | Aviso | Apenas git diff manual | Verificação superficial |
| Demais | Aviso não crítico | Usa sem tools externas | Funcionalidade base |

---

## Roteamento de Comandos

**Regra de resolução de conflitos:** Quando comando dispara múltiplas skills, a primeira da lista vence.

| Comando do Usuário | Skill Primária | Skill Secundária | Critério |
|---|---|---|---|
| "crie squad / spawn agents" | [Swarm](SextaFeiraSwarm/SKILL.md) | Cap (pré-gate) | Primária executa |
| "decidir entre X e Y" | [Swarm](SextaFeiraSwarm/SKILL.md) — decision | — | — |
| "brainstorm sobre [X]" | [Swarm](SextaFeiraSwarm/SKILL.md) — brainstorm | — | — |
| "revisar [código]" | [Swarm](SextaFeiraSwarm/SKILL.md) — review | SecurityAudit (se repo) | Swarm spawna revisores |
| "criar plano" | [Obsidian](SextaFeiraObsidian/SKILL.md) | Swarm (se multi-agent) | Obsidian coordena |
| "status do projeto" | [Obsidian](SextaFeiraObsidian/SKILL.md) | Company (se empresa) | Primária vence |
| "criar empresa" | [Company](SextaFeiraCompany/SKILL.md) | Recruit | Company coordena |
| "contratar agente" | [Recruit](SextaFeiraRecruit/SKILL.md) | Company (se existir) | Recruit executa |
| "analisar documento" | [Analytica](SextaFeiraAnalytica/SKILL.md) | — | — |
| "conectar MCP" | [MCP](SextaFeiraMCP/SKILL.md) | — | — |
| "scanear segurança" | [SecurityAudit](SextaFeiraSecurityAudit/SKILL.md) | — | — |
| "testar / rodar testes" | [Test](SextaFeiraTest/SKILL.md) | — | — |
| "deploy / pipeline" | [Deploy](SextaFeiraDeploy/SKILL.md) | Test (pré-deploy) | Deploy executa |
| "skills externas / composio" | [Composio](SextaFeiraComposio/SKILL.md) | Forge (adaptar local) | Referência URL |
| "lista skills" | [Atlas](SextaFeiraAtlas/SKILL.md) | — | — |
| "criar skill" | [Forge](SextaFeiraForge/SKILL.md) | Atlas (pré-consulta) | Forge executa |
| "onde eu parei?" | [Memory](SextaFeiraMemory/SKILL.md) | Obsidian | Memory primeiro |
| "qualidade / gate" | [Cap](SextaFeiraCap/SKILL.md) | — | — |
| "sessão / modelo" | [Beast](SextaFeiraBeast/SKILL.md) | — | — |

---

## Auto-Detect de Ambiente

```
function detectEnvironment() {
  1. Detectar CLI:
     - $CLAUDE_CODE ou $TERM_PROGRAM → detectar
     - $OVERCLOCK_SESSION → Overclock
     - Tentar pane_list_providers() → se funcionar, tem MCP tools
     - Tentar mission_list() → mission APIs disponíveis
     - Nada → modo descritivo

  2. Skills disponíveis:
     ls .sextafeira/*/SKILL.md → extrair names dos frontmatter

  3. Modelo ativo:
     - Provedor: pane_list_providers() → primeiro habilitado
     - Modelo: variável de ambiente ou usuário informa

  4. Relatório final:
     console.log(dashboard)
}
```

---

## Comandos Rápidos

| Quando usuário diz... | Skill | Ação Esperada |
|---|---|---|
| "Orquestrar / spawn" | Swarm | Detectar ambiente → sugerir squad |
| "Sessão / sistema" | Beast | Mostrar dashboard de sistema |
| "Qualidade" | Cap | Executar quality gates antes de ação |
| "Memória" | Memory | Buscar último estado |
| "Criar skill" | Forge | Verificar Atlas → criar |
| "Planejar" | Obsidian | Criar/resumir missão |
| "Listar skills" | Atlas | Mostrar catálogo |
| "Contratar" | Recruit | Carlos procura candidatos |
| "Conectar MCP" | MCP | Configurar .mcp.json |
| "Empresa" | Company | Gerenciar organograma |
| "Analisar" | Analytica | Analisar documento |
| "Scanner" | SecurityAudit | Escanear repositórios |

---

## Fluxo de Erro Genérico

Quando qualquer skill falha:

```
1. Tentar skill novamente 1x (pode ser transitório)
2. Se falhar de novo → verificar fallback (ver tabela acima)
3. Se fallback existe → usar com aviso:
   "⚠️ [Skill] não disponível. Usando [fallback]."
4. Se não tem fallback → informar usuário:
   "❌ [Skill] não disponível no ambiente atual.
      Motivo: [causa]
      Solução: [ação recomendada]"
```

---

## Segurança

- Nenhum repositório externo clonado
- Nenhum arquivo de terceiros
- Skills infectadas removidas permanentemente
- Todo conteúdo local e auditado
- Ao executar comandos shell, validar antes de executar (Cap)
- Contrato worker exige handoff_submit — sem handoff, sem resultado

---

## Language Rule

**Skill files:** English.
**All user-facing output:** MUST be in **Portuguese (PT-BR)**.
