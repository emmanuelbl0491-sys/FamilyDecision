# CLAUDE.md — Reglas para Claude en Family Decision Board

Lee este archivo completo antes de hacer cualquier cosa en este proyecto.

## Identidad del proyecto
- Proyecto: **Family Decision Board**. Una familia operada como empresa ("Family Inc.").
- Objetivo: decisiones familiares basadas en datos y probabilidades.
- Idioma oficial: **español** en todo (archivos, respuestas, comentarios de código, nombres de campos sin acentos).
- Metodología: **SDD (Spec-Driven Development)**. Ningún código ni dato nuevo sin una spec aprobada.

## Reglas no negociables
1. **Privacidad primero.** Usa solo alias (Padre-A, Padre-B, Hijo-1…) y bandas (Banda C, 6–9 meses). Si ves un dato de zona ROJA, detente: no lo repitas y pide que lo eliminen. Zona ROJA = identificaciones (CURP, RFC, NSS, SSN, pasaporte), números de cuenta o tarjeta, direcciones, expedientes médicos o nombres reales.
2. **Los humanos crean y deciden. La IA recomienda y revisa.** Nunca marques algo como aprobado. Solo el Arquitecto aprueba cambios y solo la Junta decide.
3. **Respeta la constitución** (`specs/000-constitucion.md`). Si una petición la contradice, dilo y propón una alternativa.
4. **No inventes datos.** Si falta un dato, escríbelo como pregunta abierta: `PENDIENTE: ¿…?`.
5. **Probabilidades:** los porcentajes de cada rama suman 100%. Cada uno lleva su porqué y su fuente o tasa base.
6. **Listas, no tablas.** Lo que llenan los humanos va en listas `- qué · pilar · nota` con notas del 1 (muy malo) al 10 (más que excelente). Sin pesos ni tablas de puntuación. Los humanos nunca escriben JSON: solo lo genera `generador-json` al final.
7. **Separa hechos (con fuente) de estimaciones (con razón).**
8. **Sin diagnósticos médicos ni recomendaciones de inversión específicas.**
9. **Ejemplos:** todo ejemplo debe decir `EJEMPLO FICTICIO`. Nunca uses las decisiones del Playbook original como datos reales.

## Cómo trabajar
- Antes de implementar, busca la spec en `specs/NNN-*/`. Si no existe, propón crearla con `specs/_plantillas/spec.plantilla.md`.
- Cada tarea llega como **tarjeta** (`flujo-trabajo/tarjeta-tarea.plantilla.md`). Cumple su sección "DEBE / NO DEBE / TERMINADO CUANDO".
- Después de generar datos o documentos, sugiere ejecutar:
  1. `revisor-decisiones` (consistencia y matemáticas),
  2. `auditor-privacidad` (zona ROJA),
  3. `revisor-gramatical` (español claro).
- Registra cada revisión en `flujo-trabajo/bitacora-revisiones.plantilla.md` (copia del formato).

## Archivos clave
| Necesito… | Archivo |
|---|---|
| Principios | `docs/00-principios.md` |
| Flujo SDD y puertas | `docs/01-flujo-sdd.md` |
| Plantilla de decisión | `datos/plantillas/decision.plantilla.md` |
| Estructura del JSON (solo IA) | `subagentes/generador-json.md` |
| Método y notas 1–10 | `docs/03-metodo-probabilistico.md` |
| Roles ejecutivos | `docs/04-roles-family-inc.md` |
| Requisitos del tablero | `tablero/requisitos-tablero.md` |

## Cuándo avisar a los humanos
Avisa explícitamente, con una línea que empiece por `AVISO AL ARQUITECTO:`, si detectas que el proyecto necesita RAG, memoria persistente, historial de conversación o logs más allá de lo descrito en `docs/05-rag-memoria-logs.md`. Incluye el motivo y el umbral que se superó.
