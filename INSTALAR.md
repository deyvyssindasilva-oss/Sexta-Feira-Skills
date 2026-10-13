# SEXTA FEIRA — Instalação & Autoboot Universal

Como instalar e fazer **qualquer sistema** (Claude, Gemini, Codex, Hermes) reconhecer e usar SEXTA FEIRA automaticamente.

---

## Índice

1. [Instalação Rápida](#instalação-rápida)
2. [Autoboot por CLI](#autoboot-por-cli)
3. [Boot Protocol](#boot-protocol)
4. [Verificação Pós-Instalação](#verificação-pós-instalação)
5. [Auto-Detect](#como-funciona-o-auto-detect)
6. [Exemplo: Squad UI/UX](#exemplo-squad-uiux-do-zero)
7. [Manutenção](#manutenção)
8. [Troubleshooting](#troubleshooting)
9. [Desinstalação](#desinstalação)

---

## Instalação Rápida

```bash
# 1. Copiar ecossistema pro diretório do projeto
# Linux / Mac:
cp -r ./ALEX /caminho/do/seu/projeto/.sextafeira/

# Windows (PowerShell):
Copy-Item -Recurse ./ALEX C:\caminho\projeto\.sextafeira\

# Windows (CMD):
xcopy /E /I .\ALEX C:\caminho\projeto\.sextafeira\

# 2. (Opcional) Instalar como skill global do CLI
# Claude Code:
cp -r ./ALEX ~/.claude/skills/SEXTA FEIRA/

# Hermes (Docker):
# Já incluso no bootstrap — só verificar:
ls /home/user/.sextafeira/

# 3. Verificar instalação
ls .sextafeira/
# Deve mostrar:
# SKILL.md  SextaFeiraSwarm/  SextaFeiraAtlas/  ...
```

**Zero dependências.** SEXTA FEIRA é só arquivos .md + MCP tools. Não instala pacotes, não modifica PATH, não requer npm/pip. Funciona em qualquer SO (Linux, Mac, Windows).

### Estrutura Completa

```
.sextafeira/
├── SKILL.md                     ← Orquestrador principal (ENTRADA)
├── INSTALAR.md                  ← Este arquivo
├── SextaFeiraSwarm/SKILL.md     ← Orquestração multi-agente
├── SextaFeiraAtlas/SKILL.md     ← Catálogo de skills
├── SextaFeiraCompany/SKILL.md   ← Gestão de org graph
├── SextaFeiraObsidian/SKILL.md  ← Planejamento e continuidade
├── SextaFeiraMCP/SKILL.md       ← Hub de integração MCP
├── SextaFeiraRecruit/SKILL.md   ← Recrutamento (CEO Carlos)
├── SextaFeiraAnalytica/SKILL.md ← Análise 7 lentes
├── SextaFeiraSecurityAudit/SKILL.md ← Scanner segurança
├── SextaFeiraBeast/SKILL.md     ← Gerenciamento sessão
├── SextaFeiraCap/SKILL.md       ← Quality gates
├── SextaFeiraMemory/SKILL.md    ← Memória persistente
├── SextaFeiraForge/SKILL.md     ← Criação de skills
└── SextaFeiraSwarm/archive/     ← Templates antigos
```

---

## Autoboot por CLI

Cada CLI tem mecanismo diferente de auto-load. SEXTA FEIRA se adapta.

### Claude Code / Overclock / Hermes

**Mecanismo:** `CLAUDE.md` na raiz do projeto.

```bash
# Criar CLAUDE.md pra ativação automática
cat > CLAUDE.md << 'ENDOFFILE'
# Projeto: [seu-projeto]

## Skills
Este projeto usa SEXTA FEIRA (.sextafeira/).
Output SEMPRE em PT-BR.
AO INICIAR: leia .sextafeira/SKILL.md para ativar ecossistema.

## Comandos
- "crie squad" → SextaFeiraSwarm
- "analise documento" → SextaFeiraAnalytica
- "crie plano" → SextaFeiraObsidian
- "liste skills" → SextaFeiraAtlas
- "crie empresa" → SextaFeiraCompany
ENDOFFILE

# Opcional: link simbólico
ln -s .sextafeira skills/SEXTA FEIRA
```

**Auto-load:** Claude Code lê `CLAUDE.md` na inicialização → vê referência → carrega skills.

### Claude.ai (Web)

**Mecanismo:** Project Knowledge / Custom Instructions.

```
1. Abra claude.ai
2. Vá em Settings → Project Knowledge
3. Cole o conteúdo COMPLETO de .sextafeira/SKILL.md
4. (Recomendado) Adicione no Custom Instructions:

   Sempre que eu pedir "crie squad", "analise documento",
   "liste skills", "crie empresa", "planeje projeto" ou
   qualquer comando do ecossistema SEXTA FEIRA, ative a skill
   correspondente automaticamente lendo .sextafeira/*/SKILL.md.

5. Salve. Pronto — toda nova conversa carrega SEXTA FEIRA.
```

**Limitação:** Claude.ai não executa MCP tools. SEXTA FEIRA funciona em **modo planejamento** (guia de workflow descritivo).

### Gemini

**Mecanismo:** System Instructions.

```
1. Abra Gemini → Settings → System Instructions
2. Cole:

   Você é assistido pelo ecossistema SEXTA FEIRA.
   Skills em .sextafeira/SKILL.md.
   Output SEMPRE em PT-BR.

   Ao receber comandos como "analise documento", "crie squad",
   "crie plano", ative a skill automaticamente.

3. Salve
```

### Codex

**Mecanismo:** .claude/settings.json OU project config.

```json
{
  "skills": [".sextafeira/SKILL.md"],
  "customInstructions": "Leia .sextafeira/SKILL.md para ativar SEXTA FEIRA."
}
```

### Failsafe Universal (qualquer CLI)

Se nenhum método específico funcionar:

1. Primeiro prompt manual:

```
Leia .sextafeira/SKILL.md e me responda "SEXTA FEIRA ativo".
Daqui em diante, responda em PT-BR.
```

2. Ou crie alias:

```bash
# .bashrc / .zshrc (Linux/Mac)
alias alex="cat .sextafeira/SKILL.md"

# PowerShell (Windows)
function alex { Get-Content .sextafeira/SKILL.md }
```

---

## Boot Protocol

**Primeiro prompt que treina QUALQUER IA a usar SEXTA FEIRA.** Cole no início de qualquer sessão com modelo novo:

```
=== SEXTA FEIRA BOOT PROTOCOL ===

Você está executando o ecossistema SEXTA FEIRA.
Leia .sextafeira/SKILL.md para ativar todas as 12 sub-skills.

Regras:
1. Output SEMPRE em português (PT-BR).
2. "crie squad" → SextaFeiraSwarm (orquestração multi-agente)
3. "analise documento" → SextaFeiraAnalytica (7 lentes)
4. "crie empresa" → SextaFeiraCompany + CEO Carlos
5. "liste skills" → SextaFeiraAtlas (catálogo local)
6. "planeje projeto" → SextaFeiraObsidian (mission API)
7. "contrate agente" → SextaFeiraRecruit (Carlos recruta)
8. Skills são .md com workflow completo — SIGA o que está escrito.
9. Se ambiente tiver pane MCP → use workers reais.
10. Se não tiver → use modo planejamento descritivo.
11. ANTES de spawnar workers, DETECTE o modelo atual com
    pane_list_providers() e PERGUNTE ao usuário se quer
    usar o mesmo modelo.

=== FIM BOOT ===
```

**Após isso,** a IA sabe que tem skills e age como SEXTA FEIRA.

---

## Verificação Pós-Instalação

```bash
# 1. Skills instaladas (devem ser 12)
ls -d .sextafeira/*/ | wc -l
# → 12

# 2. SKILL.md principal existe
test -f .sextafeira/SKILL.md && echo "✅ SKILL.md OK" || echo "❌ FALTANDO"

# 3. Cada sub-skill tem SKILL.md
for dir in .sextafeira/*/; do
  name=$(basename "$dir")
  if [ -f "$dir/SKILL.md" ]; then
    echo "✅ $name"
  else
    echo "❌ $name (sem SKILL.md)"
  fi
done

# 4. Ativação no CLI
# Claude Code: CLAUDE.md deve estar na raiz
test -f CLAUDE.md && echo "✅ CLAUDE.md OK" || echo "ℹ️  CLAUDE.md não encontrado (opcional)"
```

### Checklist Visual

```
☐ Pasta .sextafeira/ existe
☐ 12 sub-pastas (SextaFeiraSwarm, Atlas, Company...)
☐ SKILL.md principal presente e legível
☐ (Opcional) CLAUDE.md na raiz
☐ (Opcional) System Instructions configuradas
☐ Boot Protocol salvo pra referência
```

---

## Como Funciona o Auto-Detect

Quando um comando chega, SEXTA FEIRA detecta automaticamente:

```
Usuário: "crie squad de agents focado em ui/ux"

0. DETECTAR MODELO (antes de tudo):
   → pane_list_providers() → qual provider habilitado
   → Qual modelo está rodando AGORA
   → PERGUNTAR: "Quer usar o mesmo pros workers?"

1. Trigger: "crie squad" → SextaFeiraSwarm
2. Swarm detecta ambiente:
   → Tem pane_spawn? → modo NATIVO (workers reais)
   → Não tem? → modo PLANEJAMENTO (descritivo)
3. Template squad-dev ativado:
   → Decompor ui/ux em módulos
   → Cada módulo = 1 worker (com modelo escolhido) ou 1 seção descritiva
4. Executa e consolida
```

### Matriz de Compatibilidade

| CLI | pane_spawn | handoff | MCP tools | Modo Swarm | Auto-load |
|---|---|---|---|---|---|
| Hermes/Overclock | ✅ Nativo | ✅ Nativo | ✅ Completo | Nativo | CLAUDE.md |
| Claude Code | ✅ | ✅ | ✅ | Nativo | CLAUDE.md |
| Claude.ai Web | ❌ | ❌ | ❌ | Planejamento | Project Knowledge |
| Gemini | ❌ | ❌ | ❌ | Planejamento | System Instructions |
| Codex | Parcial | ❌ | Parcial | Híbrido | Config |

**Resumo:**
- Com MCP → execução real (workers isolados, handoff estruturado)
- Sem MCP → planejamento descritivo (guia passo a passo, referência)

---

## Exemplo: Squad UI/UX do Zero

### Com MCP (execução real)

```
Você: "crie squad de agents focado em ui/ux para o projeto TaskFlow"

SextaFeiraSwarm ativa:

Step 0 — Detectar modelo ANTES de tudo:
  🔍 pane_list_providers() → "OmniRoute" habilitado
  Modelo atual: claude-sonnet

  ╔══════════════════════════════════════════════╗
  ║  🤖 Você está usando:                        ║
  ║    Provedor: OmniRoute                       ║
  ║    Modelo:   claude-sonnet                   ║
  ║                                              ║
  ║  Quer usar este MESMO modelo                 ║
  ║  para os workers do squad?                   ║
  ║                                              ║
  ║  → "sim"  → "quero [outro]"  → "planejamento"║
  ╚══════════════════════════════════════════════╝

Você: "sim"

🐝 Squad confirmado! Usando claude-sonnet (OmniRoute).
Template: squad-dev

Decompondo em 4 workers:
├── 🎨 Pesquisa UX       → brief: personas, jornada, dores
├── 🧩 Design System     → brief: componentes, tokens, acessibilidade
├── 🖼️ Protótipo         → brief: 3 telas, fluxo navegação
└── ✅ Testes UX         → brief: cenários, critérios de aceite

📊 Squad TaskFlow — Concluído
├── 🎨 Pesquisa UX       ✅ 3 personas, jornada mapeada, 5 dores
├── 🧩 Design System     ✅ 12 componentes, 8 tokens, contraste AA
├── 🖼️ Protótipo         ✅ 3 telas (login, dashboard, tarefas)
└── ✅ Testes UX         ✅ 8 cenários, 3 critérios por cenário

📌 Próximos passos:
  1. Implementar componentes em React
  2. Conectar protótipo com dados reais
  3. Testes de usabilidade com usuários reais
```

### Sem MCP (planejamento descritivo)

```
Você: "crie squad de agents focado em ui/ux para o projeto TaskFlow"

SEXTA FEIRA:
→ Swarm detecta: sem pane MCP → modo PLANEJAMENTO
→ Pula step 0 (sem workers pra escolher modelo)

🐝 Squad UI/UX — TaskFlow (Modo Planejamento)
(Ambiente sem workers isolados — guia descritivo)

Módulos recomendados:
├── 🎨 Pesquisa UX
│   ├── Criar 2-3 personas baseadas no público-alvo
│   ├── Mapear jornada do usuário (descoberta → uso → retenção)
│   └── Identificar dores na gestão de tarefas
│
├── 🧩 Design System
│   ├── Definir paleta de cores (primária, secundária, semântica)
│   ├── Tipografia (hierarquia: h1-h6, body, caption)
│   └── Componentes base: botão, input, card, modal, tabela
│
├── 🖼️ Protótipo (3 telas prioritárias)
│   ├── Login/onboarding
│   ├── Dashboard de tarefas (visão geral)
│   └── Detalhe da tarefa (edição, comentários, status)
│
└── ✅ Validação
    ├── Checklist de acessibilidade (contraste, navegação teclado)
    └── Critérios de aceite por tela

Quer que eu detalhe algum módulo com especificações completas?
```

---

## Manutenção

### Atualizar Skills

```bash
# 1. Skills locais — editar .md diretamente (se tracking com git)
git pull origin main

# 2. Verificar integridade (todas as 12 presentes)
ls .sextafeira/*/SKILL.md 2>/dev/null | wc -l

# 3. Verificar versão no SKILL.md principal
head -5 .sextafeira/SKILL.md | grep name
```

### Adicionar Nova Skill

```bash
# Método 1: Com usuário
# "crie uma skill para [propósito]" → SextaFeiraForge faz tudo

# Método 2: Manual
mkdir .sextafeira/MinhaNovaSkill/
cat > .sextafeira/MinhaNovaSkill/SKILL.md << 'EOF'
---
name: minha-nova-skill
description: "triggers e descrição"
---
# MinhaNovaSkill

## Propósito
[o que faz]

...
EOF

# Registrar no Atlas
echo "| 📦 | MinhaNovaSkill | [descrição](link) |" >> .sextafeira/SextaFeiraAtlas/SKILL.md
```

### Manter Atualizado

```bash
# Verificar skills órfãs (pasta existe mas SKILL.md sumiu)
for dir in .sextafeira/*/; do
  [ ! -f "$dir/SKILL.md" ] && echo "⚠️  $(basename $dir) sem SKILL.md"
done
```

---

## Troubleshooting

### Problema: CLI não carrega SEXTA FEIRA

| Causa | Solução |
|---|---|
| `CLAUDE.md` não existe | Criar na raiz do projeto (ver seção Autoboot) |
| Skills em subdiretório errado | Mover `.sextafeira/` pra raiz do projeto |
| Permissão negada | `chmod -R +r .sextafeira/` |
| Windows path com espaços | Usar aspas no path ou `~` |
| Claude.ai não executa | Modo planejamento é o esperado (sem MCP) |
| Outro CLI sem suporte | Usar Boot Protocol manual no primeiro prompt |

### Problema: Swarm não spawna agentes

| Causa | Solução |
|---|---|
| Ambiente sem `pane_spawn` | Swarm degrada pra modo planejamento (normal) |
| Provider sem MCP tools | Usar outro provider ou aceitar modo descritivo |
| Worker morre na inicialização | Verificar modelo + provider compatíveis |
| Timeout no worker | Aumentar `timeout` no template ou reduzir complexidade do brief |

### Problema: Mission APIs não funcionam

| Causa | Solução |
|---|---|
| Ambiente sem `mission_create` | Company/Obsidian operam sem — tracking manual |
| Mission não persiste entre sessões | Mission é nativa do ambiente; se não tem, dados somem |
| Erro "unknown mission" | Verificar missionId — pode ter expirado |

### Problema: Skills parecem desatualizadas

```bash
# Comparar versão local com a do repositório
head -5 .sextafeira/SKILL.md
# name: SEXTA FEIRA
# # SEXTA FEIRA Ecosystem v3.3

# Se v3.3 → mais recente
# Se anterior → git pull ou copiar nova versão
```

### Problema: Output em inglês

**Causa:** CLI não está respeitando a Language Rule.

**Solução:**

```
1. Verificar .sextafeira/SKILL.md linha "All user-facing output: PT-BR"
2. Reforçar no prompt: "Responda em português (PT-BR)"
3. Se for Boot Protocol, a regra 1 já cobre
```

---

## Desinstalação

```bash
# Completa (remove tudo)
rm -rf .sextafeira/

# Seletiva (desativar skill específica)
mv .sextafeira/SextaFeiraSwarm/SKILL.md .sextafeira/SextaFeiraSwarm/SKILL.md.disabled

# Limpar referências
rm CLAUDE.md  # se criou apenas pra SEXTA FEIRA

# Reverter (reativar)
mv .sextafeira/SextaFeiraSwarm/SKILL.md.disabled .sextafeira/SextaFeiraSwarm/SKILL.md
```

---

## Resumo

| Situação | Ação | Resultado |
|---|---|---|
| Claude Code / Hermes | Copiar + CLAUDE.md | ✅ Auto-load completo |
| Claude.ai Web | Copiar SKILL.md pro Knowledge | ✅ Modo planejamento |
| Gemini / Codex | System Instructions | ✅ Modo planejamento |
| CLI nova sem suporte | Boot Protocol manual | ✅ Guia descritivo |
| Deu erro | Troubleshooting acima | ✅ Diagnóstico rápido |
| Quer remover | rm -rf .sextafeira/ | ✅ Limpo |

SEXTA FEIRA funciona em **qualquer sistema** com **qualquer modelo**.
A diferença é só nível de automação — nunca de funcionalidade.

---

> **Criador:** Takamura  
> **Versão:** 3.3  
> **Skills:** 12 locais verificadas, zero repositórios externos  
> **Compatibilidade:** Claude, Gemini, Codex, Hermes, qualquer CLI com MCP  
> **Idioma:** Skills em Inglês | Output em PT-BR
