# FluigSpec  
Um único agente de IA revisando sua criação de processos, certamente deixará passar algumas coisas. ? agentes especializados com ? domínios de conhecimento não deixarão.  
  
[Instalação](https://github.com/lorduakiti/fluigspec#instalação) · [Quick Start](https://github.com/lorduakiti/fluigspec#quick-start) · [Commandos](https://github.com/lorduakiti/fluigspec#como-funciona) · [Agentes](https://github.com/lorduakiti/fluigspec#agentes-e-categorias) · [Docs](https://github.com/lorduakiti/fluigspec/blob/main/docs)  

   
## Por que o FluigSpec?  
Toda vez que você pede a uma IA para construir um pipeline de dados, ela começa do zero — sem memória de estratégias de particionamento, sem conhecimento de padrões SCD, sem compreensão dos seus contratos de dados. 
O resultado são SQLs alucinados, estratégias incrementais incorretas e pipelines que funcionam em desenvolvimento, mas falham em produção. 
O FluigSpec resolve isso com a Engenharia de Desenvolvimento Orientada a Especificações: um fluxo de trabalho de ? fases onde cada fase tem acesso a ? domínios da base de conhecimento, cada agente conhece seus limites e cada decisão é avaliada com base em documentação real — e não em palpites.

## Instalação   
### Instalação do Pluguim (one-time)   
```bash
claude plugin marketplace add lorduakiti/fluigspec
claude plugin install fluigspec
```
Concluído. Cada sessão do Claude Code agora possui ? agentes, ? comandos e ? domínios da base de conhecimento.   

### Atualização  
Atualize com um único comando:
```bash
claude plugin update fluigspec
```  
  
> Override any agent locally — drop a file in `.claude/agents/<category>/<agent-name>.md` and it takes precedence over the plugin version. See Agent Overrides.

### Métodos de Instalação Alternativa  
#### Teste Local (sem necessidade de instalação)  
```bash
git clone https://github.com/lorduakiti/fluigspec.git
claude --plugin-dir ./fluigspec/plugin
```

#### Legacy copy (pre-plugin, still works)  
```bash
git clone https://github.com/lorduakiti/fluigspec.git
cp -r fluigspec/.claude your-project/.claude
```

<br/>

## Quick Start  

### Construa um processos de dados em ? fases  

```bash
/fluigspec:brainstorm "Daily orders Process from Fluig star BPMN"
/fluigspec:define ORDERS_PROCESS
/fluigspec:design ORDERS_PROCESS
/fluigspec:build ORDERS_PROCESS
/fluigspec:deploy ORDERS_PROCESS
```

### Ou vá direto ao que você precisa  

```bash
/fluigspec:schema "Star schema for Fluig developers"
/fluigspec:pipeline "Daily orders Process with Fluig"
/fluigspec:data-quality models/staging/stg_orders.sql
/fluigspec:sql-review models/marts/
/fluigspec:data-contract "Contract between orders team and developers"
```

<br/>

# Qual comando eu preciso usar?  

<br/>

### Analista de Negócios  

| Necessidade... | Commando | Agente |
|:--|:--|:--|
| Design a data pipeline / DAG | `/fluigspec:pipeline` | `pipeline-architect` |
| Design a star schema / data model | `/fluigspec:schema` | `schema-designer` |
| Add data quality checks | `/fluigspec:data-quality` | `data-quality-analyst` |
| Optimize slow SQL | `/fluigspec:sql-review` | `sql-optimizer` |
| Choose Iceberg vs Delta Lake | `/fluigspec:lakehouse` | `lakehouse-architect` |
| Build a RAG / embedding pipeline | `/fluigspec:ai-pipeline` | `ai-data-engineer` |
| Create a data contract | `/fluigspec:data-contract` | `data-contracts-engineer` |
| Migrate legacy SSIS / Informatica | `/fluigspec:migrate` | `dbt-specialist` + `spark-engineer` |

### SDD Workflow  

| Necessidade... | Commando | Ação |
|:--|:--|:--|
| Explore an idea | `/fluigspec:brainstorm` | Compare approaches, discovery questions, YAGNI filter |
| Capture requirements | `/fluigspec:define` | Structured requirements with clarity score (min 12/15) |
| Design architecture | `/fluigspec:design` | File manifest + pipeline architecture + ADRs |
| Implement the feature | `/fluigspec:build` | Auto-delegates to specialist agents per file type |
| Archive completed work | `/fluigspec:deploy` | Lessons learned + KB updates |
| Update after changes | `/fluigspec:iterate` | Cascade-aware updates across all phase documents |

### Visual & Arquitetura  

| Necessidade... | Commando |
|:--|:--|
| Generate architecture diagrams | `/fluigspec:generate-web-diagram` |
| Create presentation slides | `/fluigspec:generate-slides` |
| Visual implementation plan | `/fluigspec:generate-visual-plan` |
| Review code changes visually | `/fluigspec:diff-review` |
| Review code | `/fluigspec:review` |
| Analyze meeting transcripts | `/fluigspec:meeting` |
| Create a new KB domain | `/fluigspec:create-kb` |
| Share HTML page via Vercel | `/fluigspec:share` |

<br/>

# Como funciona

```
  BRAINSTORM ──► DEFINE ──► DESIGN ──► BUILD ──► DEPLOY
  Explore ideas   Scope &    File       Agent      Archive &
  & approaches    contracts  manifest   delegation lessons

                                │
          ┌─────────────────────┼──────────────────────┐
          ▼                     ▼                      ▼
    ┌─────────────┐        ┌───────────┐          ┌───────────┐
    │ fluig-spec  │        │ dev-eng   │          │ process   │
    │ Models      │        │ Jobs      │          │ BPMNs     │
    └─────┬───────┘        └─────┬─────┘          └─────┬─────┘
          └────────────────────┼──────────────────────┘
                               ▼
                         DEPLOY PROCESS
                         Tests + Quality Gates

                          ↻ /iterate
                    Cascade-aware updates
```

**Agent matching:** Seu documento DESIGN especifica modelos de formulário do processo, uma task do Fluig — o FluigSpec delega automaticamente para `fluig-specialist`, `dev-engineer` e `process-architect`.  
  
**Requirements changed?** `/fluigspec:iterate` atualiza qualquer processo de fase com detecção automática em cascata em todos os processos subsequentes.  

<br/>

# Agentes e Categorias  
? agentes em ? categorias

| Category | Count | Focus |
|:--|:--|:--|
| **Architect** | ? | Schema design, pipeline architecture, medallion layers, GenAI systems |
| **Fluig Analyst** | ? | ... |
| **Business Analyst** | ? | ... |
| **Cloud** | ? | AWS Lambda, GCP Cloud Run, Supabase, CI/CD, Terraform |
| **Data Engineering** | ? | Data base, SQL optimization |
| **Developer Engineering** | ? | TDD, ... |
| **Platform** | ? | Microsoft Fabric end-to-end (architecture, pipelines, security, AI, logging, CI/CD) |
| **Javascript** | ? | Code review, documentation, cleaning, prompt engineering |
| **Workflow** | ? | Brainstorm, define, design, build, ship, iterate |
| **Dev** | ? | Codebase exploration, shell scripting, meeting analysis, prompt crafting |
| **Test** | ? | Test generation, data quality analysis, data contract authoring |

Todos os agentes seguem a mesma estrutura cognitiva:

1. **KB-first** — Consulte a base de conhecimento local antes de recorrer a fontes externas
2. **Confidence-scored** — Calcule a confiança a partir de evidências, nunca faça autoavaliação
3. **Escalation-aware** — Transfira para o especialista correto quando estiver fora do domínio
4. **Quality-gated** — Lista de verificação pré-ação antes de cada resposta substancial

<br/>

# Bases de Conhecimento  
? Knowledge Base Domains (KB)

| Category | Domains |
|:--|:--|
| **Core Data Engenieer** | `my-sql` · `sql-server` · `sql-patterns` · `data-base` |
| **Data Design** | `data-modeling` · `data-quality` · `medallion` |
| **Infrastructure** | `lakehouse` · `lakeflow` · `cloud-platforms` · `terraform` |
| **Cloud** | `aws` · `gcp` · `microsoft-fabric` · `supabase` |
| **AI & Modern** | `ai-data-engineering` · `modern-stack` · `genai` · `prompt-engineering` |
| **Foundations** | `ecmascript-6` · `javascript` · `testing` · `shared` |

Cada domínio contém um arquivo `index.md`, um arquivo `quick-reference.md`, uma pasta `concepts/` (com ? a ? arquivos) e uma pasta `patterns/` (com ? a ? arquivos contendo o código de produção). Os agentes carregam os domínios sob demanda, não antecipadamente.

<br/>

# Fluxo de trabalho  
? Fluxo de trabalho por fases com portões de qualidade.  

| Phase | Command | Output | Gate |
|:--|:--|:--|:--|
| **0. Brainstorm** | `/fluigspec:brainstorm` | `BRAINSTORM_{FEATURE}.md` | ?+ questions, ?+ approaches |
| **1. Define** | `/fluigspec:define` | `DEFINE_{FEATURE}.md` | Clarity Score >= 12/15 |
| **2. Design** | `/fluigspec:design` | `DESIGN_{FEATURE}.md` | Complete manifest + schema plan |
| **3. Build** | `/fluigspec:build` | Code + `BUILD_REPORT.md` | All tests pass |
| **4. Ship** | `/fluigspec:ship` | `SHIPPED_{DATE}.md` | Acceptance verified |

<br/>

## Phase Workflow  

## Quality Gates   

# Project Structure  
```
fluigspec/
├── .claude/                 # Source of truth (development)
│   ├── agents/              # ? agents across ? categories
│   ├── commands/            # ? slash commands
│   ├── skills/              # ? source skills (SDD phases, GitHub workflow, authoring, KB, visuals…)
│   ├── kb/                  # ? knowledge base domains
│   └── sdd/                 # Templates, contracts, features, archive
│
├── plugin/                  # Distributable Claude Code plugin
│   ├── .claude-plugin/      # Manifest + marketplace config
│   ├── agents/              # Path-rewritten agents
│   ├── skills/              # ? skills (? from .claude/ + ? plugin-only)
│   ├── hooks/               # SessionStart workspace init
│   └── ...                  # commands, kb, sdd, scripts
│
├── plugin-extras/           # Plugin-only content (merged by build)
├── build-plugin.sh          # Packages .claude/ → plugin/
└── docs/                    # Getting started, concepts, tutorials, reference
```

<br/>

# Documentation  

| Guia | O que você aprenderá |
|:--|:--|
| [Começando](docs/getting-started/) | Instale e crie seu primeiro processo |
| [Conceitos Chave](docs/concepts/) | Pilares do SDD sob a perspectiva da engenharia de desenvolvimento |
| [Tutoriais](docs/tutorials/) | dbt, star schema, data quality, data base, process, RAG |
| [Referências](docs/reference/) | Todo Catálogo: ? agents, ? commands, ? KB domains |

<br/>

# Contribuindo 

Agradecemos contribuições.  
Consulte o arquivo [CONTRIBUTING.md](https://github.com/lorduakiti/fluigspec//blob/main/CONTRIBUTING.md) para obter diretrizes.  
**Agentes · Domínios da Base de Conhecimento · Comandos · Desenvolvimento de Plugins · Documentação**  
  
# License  
MIT — [LICENSE](https://github.com/lorduakiti/fluigspec//blob/main/LICENSE).
