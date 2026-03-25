# Guia de Onboarding — Claude Code para Livix

---

## 1. Que es esto

Claude Code es un copiloto de IA que vive en tu terminal. Entiende tu proyecto, escribe codigo, ejecuta comandos y te ayuda a tomar decisiones. Este repo ya tiene todo configurado para que trabajes en Livix con contexto completo.

Lo que hace por ti:
- Conoce el modelo de negocio de Livix, tu rol, la estrategia y los objetivos
- Puede escribir codigo, debuggear, hacer reviews y crear specs
- Tiene agentes especializados (analista, arquitecto, developer, tester, designer)
- Sabe que tu foco es: captacion de propietarios + estudiantes en Zaragoza

**No necesitas memorizar comandos.** Claude detecta automaticamente lo que necesitas y activa las herramientas correctas. Solo habla con el en lenguaje natural.

---

## 2. Setup rapido (5 minutos)

1. Instalar Claude Code: `npm install -g @anthropic-ai/claude-code` (necesitas Node.js 18+)
2. Clonar este repo: `git clone https://github.com/mugicaasier4-art/livix-aios.git`
3. Entrar al repo: `cd livix-aios`
4. Instalar plugins del framework: `./install.sh`
5. Abrir Claude Code: `claude`
6. Empieza a hablar — Claude carga el contexto de Livix automaticamente

---

## 3. Tu primer dia

Haz estos 5 ejercicios en orden para familiarizarte con Claude Code. Solo escribe lo que necesitas en lenguaje natural.

**Ejercicio 1: Verificar que Claude te conoce**
```
Quien soy y cual es mi rol en Livix?
```
Claude deberia responder con tu nombre, tu rol y los objetivos actuales. Si no lo hace, algo fallo en la configuracion.

**Ejercicio 2: Pedir orientacion**
```
Dame las 3 acciones mas importantes que deberia hacer hoy para avanzar con Livix
```

**Ejercicio 3: Crear una spec**
```
Quiero crear una pagina de landing para propietarios que explique por que publicar en Livix
```
Claude activara automaticamente el proceso de especificacion (PRD, diseno tecnico, plan).

**Ejercicio 4: Brainstorm**
```
Como podemos conseguir los primeros 15 propietarios en Zaragoza en 30 dias?
```
Claude activara automaticamente el modo brainstorm con multiples perspectivas.

**Ejercicio 5: Analizar un problema**
```
Por que un propietario elegiria Livix sobre Idealista?
```
Claude activara automaticamente el analisis con agentes especializados.

---

## 4. Lo que puedes pedir (y Claude activa automaticamente)

No necesitas recordar comandos. Simplemente describe lo que necesitas:

| Tu dices algo como... | Claude activa | Resultado |
|---|---|---|
| "Quiero construir X" / "Necesito una feature para Y" | Brainstorm + Especificacion | PRD, diseno tecnico y plan |
| "Como captamos mas estudiantes?" / "Que opciones tenemos?" | Brainstorm | Ideas estructuradas con pros/contras |
| "Implementa esto" / "Hazlo" / "Construyelo" | Implementacion | Codigo funcionando |
| "Revisa este codigo" / "Mira estos cambios" | Review | Feedback con sugerencias |
| "Como funciona X?" / "Explicame el sistema de Y" | Analisis | Documentacion clara |
| "Testea esto" / "Verifica que funciona" | Testing | Tests automatizados |
| "Esto no funciona" / "Hay un bug en X" | Debug | Diagnostico y solucion |
| "Limpia este codigo" / "Mejora esto" | Refactor | Codigo mejorado |
| "Es mejor A o B?" / "Compara estas opciones" | Debate multi-perspectiva | Decision informada |

---

## 5. Agentes especializados

Claude tiene un equipo de agentes que se activan automaticamente segun lo que necesites:

| Agente | Especialidad | Se activa cuando... |
|---|---|---|
| the-chief | Evalua complejidad y coordina | La tarea toca 2+ areas del sistema |
| the-analyst | Investigacion de mercado/producto | Necesitas datos o investigacion |
| the-architect | Diseno de sistema + APIs | Necesitas arquitectura o diseno tecnico |
| the-developer | Construye features | Hay codigo que escribir |
| the-designer | UX/UI | Necesitas diseno de interfaz |
| the-tester | Testing y QA | Necesitas tests o verificacion |
| the-devops | Infra y deploy | Necesitas deploy o configuracion |

No necesitas invocarlos. Claude decide cual usar segun tu peticion.

---

## 6. Tips

- **Se especifico.** "Necesito una landing para propietarios en Zaragoza" > "hazme una pagina"
- **Pide que compare opciones.** Claude puede debatir entre alternativas con multiples perspectivas.
- **Si la tarea es compleja**, Claude entrara en modo planificacion antes de ejecutar.
- **Pide explicaciones.** Si no entiendes algo, pregunta antes de aprobar cambios.

---

## 7. Que NO hacer

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

- Pregunta a Claude directamente — "como hago X?" funciona
- Pregunta a Asier por WhatsApp si algo no funciona
- Lee `docs/PHILOSOPHY.md` para entender la filosofia del framework
