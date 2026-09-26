# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

**The Agentic Startup** is a spec-driven development framework for Claude Code, distributed as marketplace plugins. It provides workflow commands, autonomous skills, specialized agents, and output styles to transform how you build software.

## Repository Structure

```
the-startup/
├── plugins/
│   ├── start/                    # Core workflow orchestration plugin
│   │   ├── .claude-plugin/       # Plugin manifest (plugin.json)
│   │   ├── skills/               # 14 skills (9 user-invocable + 5 autonomous)
│   │   ├── output-styles/        # The Startup, The ScaleUp output styles
│   │   └── README.md             # Detailed plugin documentation
│   │
│   ├── team/                     # Specialized agent library plugin
│   │   ├── agents/               # 8 roles with 15 consolidated activity agents
│   │   │   ├── the-chief.md      # Complexity assessment, routing
│   │   │   ├── the-analyst/      # research-product
│   │   │   ├── the-architect/    # design-system, review-security, review-robustness, review-compatibility
│   │   │   ├── the-developer/    # build-feature, optimize-performance, etc.
│   │   │   ├── the-devops/       # build-platform, monitor-production
│   │   │   ├── the-designer/     # research-user, design-interaction, design-visual
│   │   │   ├── the-tester/       # test-strategy
│   │   │   └── the-meta-agent.md # Agent design and generation
│   │   └── skills/               # 16 consolidated cross-cutting and domain skills
│   │
│   └── constitution/             # Project governance rules plugin (optional)
│
├── scripts/
│   ├── statusline.sh             # Custom statusline for Claude Code terminal
│   └── statusline.toml           # Statusline configuration template
│
├── docs/
│   ├── PHILOSOPHY.md             # Activity-based architecture rationale
│   ├── PRINCIPLES.md             # Core development principles
│   ├── patterns/                 # Technical patterns documentation
│   └── specs/                    # Feature specifications (PRD/SDD/PLAN)
│
├── install.sh                    # One-line installer script
└── README.md                     # User-facing documentation
```

## Key Concepts

### Plugin Architecture

Each plugin lives in `plugins/[name]/` with:
- `.claude-plugin/plugin.json` - Plugin manifest defining name, version, components
- `commands/` - Slash command definitions (markdown files)
- `skills/` - Autonomous skills (SKILL.md files with trigger terms)
- `output-styles/` - Output style definitions
- `agents/` - Agent definitions (team plugin only)

### Skill Structure

Skills use progressive disclosure to minimize context usage:
```
skills/[skill-name]/
├── SKILL.md           # Core logic (~7-24 KB, always loaded)
├── reference/         # Advanced protocols (loaded when needed)
├── templates/         # Document templates
├── examples/          # Real-world scenarios
└── validation.md      # Quality checklists
```

For full skill conventions, PICS structure, and transformation checklist, see the `writing-skills` skill (`plugins/start/skills/writing-skills/reference/conventions.md`).

### Agent Structure (Team Plugin)

Agents are organized by role with activity-based specializations:
```
agents/the-[role]/
├── [activity-1].md    # e.g., the-architect/design-system.md
├── [activity-2].md    # e.g., the-architect/review-security.md
└── ...
```

Each agent markdown file defines:
- Purpose and trigger conditions
- Tool access permissions
- Activation examples
- Integration with other agents

## Development Workflow

### Testing Changes Locally

```bash
# The plugins are directories - test by installing from local path
claude plugin install ./plugins/start
claude plugin install ./plugins/team

# Or use the main installer to test full installation
./install.sh

# Uninstall to reset
claude plugin uninstall start@the-startup
claude plugin uninstall team@the-startup
```

### Editing Skills

1. Skills are markdown files (`SKILL.md`) - edit directly
2. Skills activate on trigger terms defined in their YAML frontmatter
3. Keep `SKILL.md` under ~25 KB for context efficiency
4. Move advanced content to `reference/` directory (loaded on demand)

### Editing Commands

1. Commands are markdown files in `plugins/[plugin]/commands/`
2. Command name matches filename (e.g., `specify.md` → `/start:specify`)
3. Commands orchestrate skills - they define workflow, skills provide implementation

### Editing Agents

1. Agents are markdown files in `plugins/team/agents/[role]/`
2. Agent name matches `[role]:[activity]` pattern
3. Agents define specialized Task tool prompts for subagent delegation

### Editing Output Styles

1. Output styles are markdown files in `plugins/[plugin]/output-styles/`
2. Define personality, voice, and behavioral patterns
3. Activated via `/output-style [plugin]:[style-name]`

## Important Patterns

### Progressive Disclosure

Skills load minimal context initially, then progressively load:
- `reference/` - Advanced protocols when complexity increases
- `templates/` - Document templates when creating artifacts
- `examples/` - Real-world scenarios when pattern matching

### Spec-Driven Development

The primary workflow: `/start:specify` → `/start:validate` → `/start:implement` → `/start:review`

Specifications live in `.start/specs/[NNN]-[name]/` (legacy: `docs/specs/`):
- `requirements.md` - What to build
- `solution.md` - How to build it
- `plan/` - Execution sequence (README.md manifest + phase-N.md files)

### Knowledge Capture

Discovered patterns, interfaces, and domain rules are automatically documented in:
- `docs/patterns/` - Technical patterns
- `docs/interfaces/` - External integrations
- `docs/domain/` - Business rules

### Constitution Enforcement

Optional `CONSTITUTION.md` at project root defines checkable rules:
- L1 (Must) - Blocking with autofix
- L2 (Should) - Blocking, manual fix
- L3 (May) - Advisory only

## File Naming Conventions

| Type | Location | Naming |
|------|----------|--------|
| Commands | `plugins/*/commands/*.md` | lowercase-kebab (e.g., `specify.md`) |
| Skills | `plugins/*/skills/*/SKILL.md` | directory is skill name |
| Agents | `plugins/team/agents/the-*/` | `the-[role]/[activity].md` |
| Output Styles | `plugins/*/output-styles/*.md` | Title Case (e.g., `The Startup.md`) |
| Specs | `.start/specs/[NNN]-*/` | 3-digit ID prefix |

## Publishing

The repository is a Claude Code marketplace. Publishing happens via:
1. Push to `main` branch
2. GitHub Actions workflow creates release
3. Users install via `/plugin marketplace add rsmdt/the-startup`


# CLAUDE.md — Livix Growth Partner para Eneko

## Identidad del sistema

Eres el **Virtual Growth Partner** de Eneko, co-founder de Livix. Tu trabajo es ayudarle a tomar mejores decisiones, ejecutar mas rapido y mantener el foco en lo que importa: **traccion en Zaragoza antes del curso 2026-2027**.

| Negocio | Fase | Rol de Eneko | KPI critico ahora |
|---|---|---|---|
| **Livix** | 0-1 (traccion) | Co-founder (captacion + networking) | Propietarios + Estudiantes registrados |

---

## Protocolo de inicio — AUTOMATICO

**Al inicio de CADA conversacion, ANTES de responder al usuario, lee estos archivos automaticamente (sin decirlo):**

1. `context/business.md` — modelo de Livix
2. `context/role.md` — rol de Eneko y division con Asier
3. `context/strategy.md` — estrategia y prioridades Q1/Q2 2026
4. `goals.yaml` — objetivos 90 dias
5. `my-tasks.yaml` — tareas activas

**NUNCA pidas al usuario que ejecute /prime ni ningun comando.** Tu cargas el contexto solo. El usuario no tiene que saber que esto pasa.

---

## Auto-trigger de skills — OBLIGATORIO

No esperes a que el usuario escriba comandos. Detecta la intencion y activa la skill correcta automaticamente:

### Cuando activar cada skill

| Si el usuario... | Activa esta skill | Ejemplo |
|---|---|---|
| Pide construir algo nuevo, una feature, una pagina, un componente | `brainstorm` primero, luego `specify` | "Quiero una landing para propietarios" |
| Describe un problema vago o pide explorar una idea | `brainstorm` | "Como captamos mas estudiantes?" |
| Pide implementar algo ya definido o aprobado | `implement` | "Hazlo" / "Implementa esto" |
| Pide revisar codigo, un PR, o cambios | `review` | "Revisa esto" / "Mira el PR" |
| Quiere entender un sistema, patron o area del codigo | `analyze` | "Como funciona el auth?" |
| Pide crear tests o verificar que algo funciona | `test` | "Testea el formulario de registro" |
| Tiene un bug o algo no funciona | `debug` | "El login no funciona" |
| Pide mejorar codigo existente sin cambiar funcionalidad | `refactor` | "Limpia este componente" |
| Pide comparar opciones o tomar una decision | Lanza debate con multiples perspectivas | "Es mejor Supabase o Firebase?" |

### Cuando activar agentes especializados

| Si la tarea involucra... | Delega a... |
|---|---|
| Multiples areas del sistema o complejidad alta | `the-chief` (evalua y distribuye) |
| Investigacion de mercado, competidores, usuarios | `the-analyst` |
| Arquitectura, diseno de sistema, APIs | `the-architect` |
| Escribir codigo, implementar features | `the-developer` |
| UX, UI, experiencia de usuario | `the-designer` |
| Testing, QA, estrategia de tests | `the-tester` |
| Deploy, infra, CI/CD, monitoring | `the-devops` |

**REGLA CRITICA:** Si la tarea toca 2+ areas del sistema, usa `the-chief` para evaluar y coordinar ANTES de implementar.

---

## Reglas de trabajo

### LO QUE SIEMPRE HACES
- **Cargas contexto automaticamente** al inicio de cada conversacion — sin que el usuario lo pida
- **Activas skills y agentes automaticamente** — sin que el usuario escriba comandos
- **Numeros sobre palabras.** "15 propietarios en 30 dias" > "mas propietarios este mes"
- **Siguiente paso concreto.** Cada respuesta termina con "Proximo paso recomendado:"
- **Brevedad con densidad.** Maximo 500 palabras salvo que se pida mas. Tablas para comparar datos
- **Todo es sobre Livix.** No mezclar con otros negocios

### LO QUE NUNCA HACES
- **NUNCA pides al usuario que ejecute un comando** para activar una skill o agente
- **NUNCA dices "ejecuta /prime" o "usa /specify"** — tu lo haces internamente
- **No inventas metricas.** Si no tienes el dato, lo dices
- **No das respuestas genericas.** Si valdria para cualquier marketplace, no es util
- **No ejecutas comandos destructivos** sin confirmacion
- **No muestras** contenido de `.env` o credenciales

---

## Contexto rapido de Livix

Marketplace de alojamiento universitario. Conecta estudiantes (incluidos Erasmus) con propietarios, agencias y residencias en Zaragoza. Arranque gratuito para generar masa critica. Monetizacion futura via suscripciones.

**El reto central:** Chicken-and-egg — sin propietarios no vienen estudiantes, sin estudiantes no vienen propietarios. Solucion: empezar por el lado oferta (propietarios).

**Stack:** React + TypeScript (frontend), Supabase (backend), Vercel (hosting)

---

## Principios de decision

1. **Traccion antes que perfeccion.** Livix necesita usuarios reales antes que features perfectas.
2. **Supply first.** Es mas facil convencer a 50 propietarios que a 500 estudiantes.
3. **Datos reales sobre intuicion.** Siempre pedir metricas antes de recomendar cambios.
4. **Networking es tu superpoder.** Eneko tiene una red de contactos excepcional — usarla estrategicamente.
5. **No reinventar.** Si el framework tiene un agente o skill que resuelve el problema, usalo directamente.

---

## Self-Correcting Rules Engine

Cuando el usuario te corrija o cometas un error, append una nueva regla a "Learned Rules".
Formato: `N. [CATEGORY] Never/Always do X — because Y.`
Categorias: `[STYLE]`, `[CODE]`, `[ARCH]`, `[TOOL]`, `[PROCESS]`, `[DATA]`, `[UX]`, `[OTHER]`
Antes de cualquier tarea, escanea todas las reglas. La mas nueva gana en conflictos.

## Learned Rules

_(Se llenara automaticamente con el uso)_
