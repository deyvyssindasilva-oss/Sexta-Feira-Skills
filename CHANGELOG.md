# Changelog

## v3.4.1 (2026-06-30) — External Skill Registry + Final Cleanup
- New skill: SextaFeiraComposio v1.0 — external skill registry (no clone, verified URL)
- Verified ComposioHQ/awesome-claude-skills repo: 892 .md files, zero threats
- SKILL.md updated: 15 skills
- Atlas updated: 15 skills + search keywords
- Remaining orphan reference dirs purged (7 dirs)
- Analytica dead references removed

## v1.0.0 (2026-06-23) — Major Refactor
- All 8 sub-skills rewritten in robust format (English + PT-BR output)
- New naming: SextaFeiraUI_UX → SextaFeiraAtlas, SextaFeiraPaperclip → SextaFeiraRecruit
- Each skill now has: YAML frontmatter, trigger conditions, workflow, output template, examples, security rules, language rule
- YAML frontmatter with name, description (trigger-optimized), and compatibility
- All user-facing output standardized to PT-BR
- Language Rule appended to every skill file
- Main SKILL.md updated with 8 sub-skills and command reference
- README.md updated to reflect new structure
- SextaFeiraAtlas CATALOG.md updated with language rule

## v1.1.0 (2026-06-23) — MCP Integration Hub
- New sub-skill: SextaFeiraMCP (65+ MCP servers across 13 categories)
- 5 reference files: database, devtools, web, productivity, integration
- Main SKILL.md updated: 9 → 10 sub-skills
- SextaFeiraAtlas CATALOG.md: new 13-MCP category with 13 entries
- MCP catalog: Neon, Supabase, PostgreSQL, MySQL, MongoDB, Redis, GitHub, Stripe, Docker, Notion, Google Workspace, Web Fetch, Web Search + 50+ more

## v2.1.0 (2026-06-23) — Document Analysis & Intelligence Engine
- New sub-skill: SextaFeiraAnalytica (multi-format document analysis)
  - 7 analysis lenses: Engineering, Education, Office/Admin, Finance, Scientific, Project Mgmt, Legal
  - Mentoring mode for students and professors
  - Brainstorming mode grounded in document content
  - Cross-document comparison and memory
  - Anti-Hallucination & Precision Protocol
- 5 reference files: engineering, educational, financial, project, office
- Main SKILL.md updated: 10 → 11 sub-skills
- README.md updated to v2.1
- SextaFeiraAtlas CATALOG.md: new 17-Analytica category with 8 entries

## v3.0.0 (2026-06-23) — REAL Skills Import (3.631 skills)
- Cloned 12 Anthropic repos → 2.147 skills REAIS em arquivo
  - knowledge-work-plugins: 1.026 .md
  - financial-services: 249 .md
  - claude-for-legal: 221 .md
  - claude-plugins-official: 205 .md
  - claude-code: 102 .md
  - skills: 94 .md
  - claude-cookbooks: 87 .md
  - life-sciences: 47 .md
  - claude-agent-sdk-demos: 35 .md
  - cwc-workshops: 35 .md
  - defending-code-reference-harness: 30 .md
  - claude-quickstarts: 16 .md
- Cloned 3 PaperclipAI repos → 1.482 skills REAIS em arquivo
  - companies: 1.078 .md
  - paperclip: 259 .md
  - paperclip-docs: 145 .md
- SextaFeiraAtlas CATALOG.md atualizado com números REAIS
- Total REAL: 3.631 arquivos .md de skills
- Números corrigidos em SKILL.md, README.md e CATALOG.md

## v3.4.0 (2026-06-30) — Full Ecosystem Audit + 2 New Skills
- All 12 skills overhauled with real implementations (no more abstractions)
- New skill: SextaFeiraTest v1.0 (QA hub, generation, coverage, CI)
- New skill: SextaFeiraDeploy v1.0 (CI/CD pipelines, build, release, rollback)
- Swarm v2.3: detects model + asks user before spawning workers
- Beast v2.0: real pane_list_providers() detection, no more "24/7 agents"
- Cap v2.0: 5 gates with algorithms, bypass rules, real token costing
- Memory v2.0: persistent .md files on disk at .sextafeira/.memory/
- Forge v2.0: anti-duplicate check (Atlas) + test before delivery
- Obsidian v2.1: fallback mode if Mission API unavailable
- Company v2.1: tree validation (no orphan, no cycle), fallback .org/
- Recruit v3.0: real sources (Atlas+Memory), no fictional "agent pool"
- MCP v2.0: 65 placeholder MCPs removed → 17 verified with real commands
- SecurityAudit v2.0: scanner script embedded, no external dependencies
- Atlas v1.1: 14 skills catalog, keyword search, redirect to Forge
- SKILL.md v3.4: 14 skills, routing table, auto-detect dashboard
- INSTALAR.md: universal onboarding, troubleshooting table, Windows support
- README.md updated to v3.4
- CHANGELOG.md updated
- Removed ~70 orphaned reference files no longer referenced by any skill
- Removed "regras-invisiveis" references (never existed on disk)
- All references to "Overclock" branding removed (SEXTA FEIRA-native naming)

## v2.0.0 (2026-06-23) — Company & Graph + Anthropic/Paperclip Integration
- New sub-skill: SextaFeiraCompany (org graph management, Paperclip-inspired)
- 6 template files: COMPANY.md, .sextafeira.yaml, AGENTS.md, TEAM.md, PROJECT.md, TASK.md
- SextaFeiraRecruit overhauled to v2.0: 6-phase recruitment with Carlos as CEO root
  - Paperclip principle: strict tree, reportsTo, no orphans, chain of command
  - Carlos finds candidates → notifies user → only hires on approval
  - Internal pool search before external hire
- SextaFeiraAtlas expanded: 350 → 900+ skills
  - New 14-Company category
  - New 15-Anthropic category: 400+ skills across 12 repos
  - New 16-PaperclipAI category: 157 skills across 3 repos
- Main SKILL.md updated: 9 → 10 sub-skills
- README.md updated to v2.0

## v0.1.1 (2026-06-22)
- Estrutura inicial da SEXTA FEIRA Skills
- 6 sub-skills: Swarm, Beast, Cap, Memory, Forge, Obsidian
- Regras visíveis + invisíveis (segurança)
- Templates: Decisão, Brainstorm, Review, Plano, Squad Dev, Custom
- Docker bootstrap para Hermes
