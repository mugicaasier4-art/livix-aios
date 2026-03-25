# Guia de Onboarding — Claude Code para Livix

---

## 1. Que es esto

Claude Code es un copiloto de IA que vive en tu terminal. Entiende tu proyecto, escribe codigo, ejecuta comandos y te ayuda a tomar decisiones. Este repo ya tiene todo configurado para que trabajes en Livix con contexto completo.

Lo que hace por ti:
- Conoce el modelo de negocio de Livix, tu rol, la estrategia y los objetivos
- Puede escribir codigo, debuggear, hacer reviews y crear specs
- Tiene agentes especializados (analista, arquitecto, developer, tester, designer)
- Sabe que tu foco es: captacion de propietarios + estudiantes en Zaragoza

---

## 2. Setup rapido (5 minutos)

1. Instalar Claude Code: `npm install -g @anthropic-ai/claude-code` (necesitas Node.js 18+)
2. Clonar este repo: `git clone https://github.com/rsmdt/the-startup.git`
3. Entrar al repo: `cd the-startup`
4. Instalar plugins del framework: `./install.sh`
5. Abrir Claude Code: `claude`
6. Primer comando siempre: `/prime`

---

## 3. Tu primer dia

Haz estos 5 ejercicios en orden para familiarizarte con Claude Code.

**Ejercicio 1: Cargar contexto**
```
/prime
```
Esto carga todo el contexto de Livix. Claude ahora sabe quien eres, que es Livix y cuales son los objetivos.

**Ejercicio 2: Pedir orientacion**
```
Dame las 3 acciones mas importantes que deberia hacer hoy para avanzar con Livix
```

**Ejercicio 3: Crear una spec**
```
/start:specify
Quiero crear una pagina de landing para propietarios que explique por que publicar en Livix
```

**Ejercicio 4: Brainstorm**
```
/start:brainstorm
Como podemos conseguir los primeros 15 propietarios en Zaragoza en 30 dias?
```

**Ejercicio 5: Analizar un problema**
```
/start:analyze
Por que un propietario elegiria Livix sobre Idealista?
```

---

## 4. Comandos que mas vas a usar

| Comando | Que hace | Cuando usarlo |
|---|---|---|
| `/prime` | Carga contexto Livix | Siempre al empezar sesion |
| `/start:specify` | Crea PRD de una feature | Antes de construir algo nuevo |
| `/start:implement` | Ejecuta implementacion | Despues de aprobar una spec |
| `/start:review` | Revisa codigo | Antes de hacer merge |
| `/start:brainstorm` | Genera ideas | Cuando necesitas creatividad |
| `/start:analyze` | Analiza problema | Cuando necesitas perspectiva |
| `/start:validate` | Valida una spec | Para verificar que la spec esta completa |
| `/start:test` | Genera tests | Para asegurar calidad del codigo |
| `/start:debug` | Diagnostica bugs | Cuando algo no funciona |
| `/start:refactor` | Mejora codigo | Para limpiar codigo existente |

---

## 5. Agentes especializados

Este repo incluye un equipo de agentes especializados a los que Claude puede delegar trabajo:

| Agente | Especialidad | Ejemplo de uso |
|---|---|---|
| the-chief | Evalua complejidad y decide quien trabaja | "Es mejor hacer X o Y?" |
| the-analyst | Investigacion de producto | "Investiga como funcionan otros marketplaces de housing" |
| the-architect | Diseno de sistema + reviews | "Disena la arquitectura para el sistema de mensajeria" |
| the-developer | Construye features | "Implementa el formulario de registro de propietarios" |
| the-designer | UX/UI research + diseno | "Disena la experiencia de publicar un anuncio" |
| the-tester | Estrategia de testing | "Crea tests para el flujo de registro" |
| the-devops | Infraestructura + deploy | "Configura el deploy automatico a Vercel" |

Para activarlos, simplemente describe lo que necesitas y Claude delegara al agente adecuado.

---

## 6. Tips y trucos

- **Siempre /prime primero.** Sin contexto, Claude da respuestas genericas.
- **Se especifico.** "Necesito una landing para propietarios en Zaragoza" > "hazme una pagina"
- **Pide que compare opciones.** Claude puede debatir entre alternativas con multiples perspectivas.
- **Usa plan mode.** Si una tarea es compleja, Claude entrara en modo planificacion antes de ejecutar.
- **Revisa antes de hacer push.** Usa `/start:review` siempre antes de mergear a main.

---

## 7. Que NO hacer

- No empezar sin `/prime` — sin contexto, las respuestas son genericas
- No hacer `git push --force` — puede destruir trabajo de Asier
- No compartir el contenido de `.env` con nadie ni pegarlo en el chat
- No aprobar cambios que no entiendas — pide explicacion primero
- No asumir que Claude tiene razon siempre — verifica datos criticos

---

## 8. Donde esta cada cosa

| Archivo | Que contiene |
|---|---|
| `CLAUDE.md` | System prompt — como se comporta Claude contigo |
| `AGENTS.md` | Definicion del framework de agentes |
| `context/business.md` | Modelo de negocio de Livix |
| `context/role.md` | Tu rol y division con Asier |
| `context/strategy.md` | Estrategia Q1/Q2 2026 |
| `context/founder_notes.md` | Tu voz y estilo (rellenalo!) |
| `goals.yaml` | Objetivos 90 dias |
| `my-tasks.yaml` | Tus tareas activas |
| `plugins/` | Framework de desarrollo (no tocar) |
| `.claude/rules/` | Reglas de formato y seguridad |

---

## 9. Necesitas ayuda?

- Escribe `/help` en Claude Code para ver todos los comandos disponibles
- Pregunta a Asier por WhatsApp si algo no funciona
- Lee `docs/PHILOSOPHY.md` para entender la filosofia del framework
