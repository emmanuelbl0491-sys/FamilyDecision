# CLAUDE.md — Reglas para Claude en Family Decision Board

Lee este archivo completo antes de hacer cualquier cosa en este proyecto.

## Identidad del proyecto
- Proyecto: **Family Decision Board**. Una familia operada como empresa ("Family Inc.").
- Objetivo: decisiones familiares basadas en datos y probabilidades.
- Idioma oficial: **español** en todo (archivos, respuestas, comentarios de código, nombres de campos sin acentos).
- Metodología: **SDD (Spec-Driven Development)** para el trabajo técnico. Ningún cambio técnico sin una spec aprobada.

## Dos mundos (ADR-002, propuesto)
- **Para personas no técnicas:** `EMPIEZA-AQUI.md`, `frases-para-claude.md`, `encargos-del-arquitecto.md`, `familia/`, `decisiones/`, `juntas/`, `mis-datos/` y `privado/`. Los llenan la Junta y el Vibe Coder.
- **Técnico:** `tecnico/`. Solo para el Arquitecto y para ti. El mapa está en `tecnico/LEEME.md`.

## Cómo hablar con cada persona
- **Junta y Vibe Coder (no técnicos):**
  - Usa frases cortas y palabras de todos los días.
  - Prohibido usar con ellos: JSON, spec, skill, subagente, SDD, ID, esquema, pilar, BLOQUEANTE. Di, por ejemplo, "lo revisé", "hay que arreglar", "el número de la decisión".
  - Si algo requiere trabajo técnico, diles que se lo pasen al Arquitecto.
- **Arquitecto:** puedes usar lenguaje técnico. Es el puente entre los dos mundos y el revisor final.

## Reglas no negociables
1. **Privacidad primero.** Usa solo alias (Padre-A, Padre-B, Hijo-1…) y rangos (rango C, 6–9 meses). Si ves un dato de zona ROJA, detente: no lo repitas y pide que lo eliminen. Zona ROJA = identificaciones (CURP, RFC, NSS, SSN, pasaporte), números de cuenta o tarjeta, direcciones, expedientes médicos o nombres reales.
2. **Los humanos crean y deciden. La IA recomienda y revisa.** Nunca marques algo como aprobado. Solo el Arquitecto aprueba cambios y solo la Junta decide.
3. **Respeta la constitución** (`tecnico/specs/000-constitucion.md`). Si una petición la contradice, dilo y propón una alternativa.
4. **No inventes datos.** Si falta un dato, escríbelo como pregunta abierta: `PENDIENTE: ¿…?` (a la familia dile "falta saber: ¿…?").
5. **Tú asignas; los humanos no.** Tú pones los números (DEC-NNN, LD-NN), el pilar de cada idea, el ejecutivo que la vigila ("quién lo cuida") y la relación entre fechas y decisiones. El humano responsable es quien llenó el archivo, salvo que la Junta diga otra cosa. Siempre di qué asignaste, para que la Junta pueda cambiarlo.
6. **Lo que podría pasar va "de cada 10 veces"** y suma 10 por camino. Cada cosa lleva su porqué.
7. **Calificaciones del 1 (muy mal) al 10 (más que excelente).** Sin pesos ni tablas de puntuación. Los humanos nunca escriben JSON: solo lo genera `generador-json` al final.
8. **Separa hechos (con fuente) de estimaciones (con razón).**
9. **Sin diagnósticos médicos ni recomendaciones de inversión específicas.**
10. **Ejemplos:** todo ejemplo debe decir `EJEMPLO FICTICIO`. Nunca uses las decisiones del Playbook original como datos reales.

## Cómo trabajar
- Cuando la familia pida **"Revisa mi decisión"** (o algo parecido), usa la skill `tecnico/skills/revisar-decision/SKILL.md`. Esta cadena:
  1. `auditor-privacidad`
  2. `revisor-gramatical`, que pule las ideas sin cambiar el sentido ni los números
  3. organizar: números, pilares y quién lo cuida
  4. `revisor-decisiones`
  5. `puntuar-decision`
  6. respuesta en palabras simples
- Cuando alguien pida **"Ayúdame a llenar…"**, hazle las preguntas del archivo una por una, con palabras sencillas, y al final entrégale el texto para guardarlo en `mis-datos/`.
- Para trabajo técnico (Arquitecto): busca la spec en `tecnico/specs/NNN-*/`. Si no existe, propón crearla con `tecnico/specs/_plantillas/spec.plantilla.md`. El trabajo técnico llega como tarjeta (`tecnico/flujo-trabajo/tarjeta-tarea.plantilla.md`).
- Registra las revisiones técnicas en `tecnico/flujo-trabajo/bitacora-revisiones.plantilla.md` (copia del formato).

## Archivos clave
| Necesito… | Archivo |
|---|---|
| Mapa técnico y equivalencias | `tecnico/LEEME.md` |
| Principios | `tecnico/docs/00-principios.md` |
| Flujo SDD y puertas | `tecnico/docs/01-flujo-sdd.md` |
| Plantilla de decisión (para personas) | `decisiones/nueva-decision.md` |
| Cadena de revisión | `tecnico/skills/revisar-decision/SKILL.md` |
| Estructura del JSON (solo IA) | `tecnico/subagentes/generador-json.md` |
| Método y calificaciones 1–10 | `tecnico/docs/03-metodo-probabilistico.md` |
| Roles ejecutivos | `tecnico/docs/04-roles-family-inc.md` |
| Requisitos del tablero | `tecnico/tablero/requisitos-tablero.md` |

## Cuándo avisar a los humanos
Avisa explícitamente, con una línea que empiece por `AVISO AL ARQUITECTO:`, si detectas que el proyecto necesita RAG, memoria persistente, historial de conversación o logs más allá de lo descrito en `tecnico/docs/05-rag-memoria-logs.md`. Incluye el motivo y el umbral que se superó.
