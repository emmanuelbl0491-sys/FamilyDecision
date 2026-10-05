# Family Decision Board

> Sistema para que una familia tome decisiones con datos y probabilidades, no con corazonadas.
> **Lo crean humanos. La IA lo potencia.**

Versión del marco: `v0.1.0` · Fecha: 2026-10-05 · Idioma oficial: **español**

---

## 1. ¿Qué es esto?

Family Decision Board es un **marco de trabajo en carpetas**. Contiene todo lo que hace falta para operar el tablero de decisiones de "Family Inc.":

- **Especificaciones (SDD):** qué se construye y por qué, antes de escribir código.
- **Plantillas de datos:** listas en Markdown que **llenan los humanos**, con notas del 1 (muy malo) al 10 (más que excelente). Sin tablas, sin pesos y sin JSON.
- **Skills:** los cinco ejecutivos (CEO, COO, CFO, VP de Producto, Jefe de Atención) y la skill que puntúa decisiones.
- **Subagentes:** revisores de IA que revisan lo que escriben los humanos (datos, gramática y privacidad), y `generador-json`, que arma el JSON del tablero al final.
- **Prompts:** de sistema, humanos y de agente.
- **Flujo de trabajo:** tarjetas de tarea, checklists del Arquitecto, actas y bitácoras.
- **Requisitos del tablero:** lo que Claude necesita para generar el dashboard final.

Este proyecto **hereda los principios** del *Family Inc. — Probabilistic Life Plan Playbook* (privacidad, método probabilístico, roles). **No hereda sus decisiones**: aquellas eran imaginarias. Todos los ejemplos de esta carpeta dicen `EJEMPLO FICTICIO`.

## 2. Roles del proyecto

| Rol | Quién | Responsabilidad | Nunca hace |
|---|---|---|---|
| **Arquitecto de Soluciones IA** | Humano (dueño técnico) | Constitución, specs, planes, aprobación final | Aprobar algo sin pasar el checklist |
| **Vibe Coder** | Humano nuevo, guiado por IA | Implementa tarjetas de tarea con ayuda de Claude | Cambiar el formato de las plantillas, la privacidad o el alcance |
| **Junta (Padre-A, Padre-B)** | Humanos | Llenan plantillas de datos y votan decisiones | Delegar la decisión final a la IA |
| **Subagentes revisores** | IA | Revisan datos, gramática y privacidad; emiten un informe | Aprobar o fusionar cambios |
| **Ejecutivos (Skills)** | IA | Recomiendan dentro de su dominio | Decidir |

## 3. Estructura de carpetas

```
family-decision-board/
├── README.md                    ← este archivo
├── EMPIEZA-AQUI.md              ← paso a paso para los humanos
├── CLAUDE.md                    ← reglas que Claude lee al abrir el proyecto
├── PROMPT_CONTINUIDAD.md        ← prompt para que otra IA/conversación continúe alineada
├── .gitignore                   ← bloquea /privado y datos reales
├── docs/                        ← principios, SDD, privacidad, método, roles, RAG/memoria/logs
├── specs/                       ← constitución + plantillas SDD + spec de ejemplo
├── datos/                       ← plantillas en listas que llenan los humanos + ejemplos
├── skills/                      ← 6 skills (5 ejecutivos + puntuación)
├── subagentes/                  ← revisores, investigador y generador-json
├── prompts/                     ← sistema / humanos / agentes
├── flujo-trabajo/               ← tarjetas, checklists, actas, bitácoras, ADR
├── tablero/                     ← requisitos y datos de entrada para que Claude cree el dashboard
├── aprendizaje/                 ← guía del Vibe Coder + ejercicios del Arquitecto
└── privado/                     ← zona ROJA local. Nunca se sube a ningún lado
```

Cada subcarpeta tiene un `LEEME.md` que explica qué contiene y en qué orden se usa.

## 4. Flujo en una línea

```
Humano escribe listas con notas 1–10 → Subagentes revisan → Humano corrige
→ Arquitecto aprueba → IA puntúa → Junta vota → generador-json arma el JSON → Claude genera el tablero
```

El flujo detallado (con sus puertas de control) está en [`docs/01-flujo-sdd.md`](docs/01-flujo-sdd.md).

## 5. Inicio rápido (primer día)

> ¿Eres de la Junta o Vibe Coder? Sigue el paso a paso de [`EMPIEZA-AQUI.md`](EMPIEZA-AQUI.md).

1. **Privacidad:** en Claude, Settings > Privacy > "Help improve Claude" en **OFF**. Lee [`docs/02-privacidad-zonas.md`](docs/02-privacidad-zonas.md).
2. **Constitución:** el Arquitecto lee y firma [`specs/000-constitucion.md`](specs/000-constitucion.md).
3. **Proyecto Claude:** crea un Proyecto "Family Decision Board". Pega [`prompts/sistema/prompt-sistema-family-inc.md`](prompts/sistema/prompt-sistema-family-inc.md) en las instrucciones. Sube **solo** archivos de zona VERDE.
4. **Skills:** sube las carpetas de [`skills/`](skills/) desde la configuración de Skills de Claude (o cópialas a `.claude/skills/` si usas Claude Code).
5. **Subagentes:** en Claude Code, copia [`subagentes/`](subagentes/) a `.claude/agents/`. En claude.ai, usa su contenido como "prompt de agente" cuando pidas un subagente.
6. **Datos:** la Junta llena [`datos/plantillas/`](datos/plantillas/) empezando por `bandas`, `limites-duros` y `perfil-familia`.
7. **Primera decisión:** llena `datos/plantillas/decision.plantilla.md` y pide: *"Revisa esta decisión con auditor-privacidad y revisor-decisiones, y luego usa la skill puntuar-decision"*.

## 6. Cómo se instala cada pieza

| Pieza | claude.ai (interfaz) | Claude Code |
|---|---|---|
| Prompt de sistema | Instrucciones del Proyecto | `CLAUDE.md` (ya incluido) |
| Skills | Configuración > Skills (subir carpeta comprimida) | `.claude/skills/<nombre>/SKILL.md` |
| Subagentes | Pegar el archivo como prompt al pedir un subagente | `.claude/agents/<nombre>.md` |
| Datos VERDES | Conocimiento del Proyecto | Carpeta `datos/` |
| Tablero | Artifact generado por Claude | Artifact o archivo HTML local |

> Las rutas exactas de los menús pueden cambiar. Verifícalas en [support.claude.com](https://support.claude.com).

## 7. ¿Necesita RAG, memoria, historial o logs?

Resumen. El detalle y los umbrales están en [`docs/05-rag-memoria-logs.md`](docs/05-rag-memoria-logs.md).

| Componente | ¿Se necesita hoy? | Motivo |
|---|---|---|
| RAG | **No** | Los datos de una familia caben en el conocimiento del Proyecto |
| Memoria de Claude | **Limitada** | Solo memoria del Proyecto, separada de la cuenta general |
| Historial de conversación | **No como fuente de verdad** | Se pierde y no se audita. La verdad vive en `datos/` y en las bitácoras |
| Logs | **Sí** | Bitácora de decisiones y de revisiones en Markdown (`flujo-trabajo/`) |

## 8. Entrega final

Cuando todas las tarjetas estén aprobadas, entrega la carpeta completa a Claude con el prompt de [`tablero/prompt-generar-tablero.md`](tablero/prompt-generar-tablero.md). Primero, el subagente `generador-json` arma el JSON con las decisiones aprobadas. Después, Claude genera el dashboard a partir de `tablero/requisitos-tablero.md` y de ese JSON. Ningún humano escribe JSON.

Para continuar en otra conversación o con otra IA, usa [`PROMPT_CONTINUIDAD.md`](PROMPT_CONTINUIDAD.md).
