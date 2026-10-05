# tecnico/ — Solo para el Arquitecto y Claude

> La familia y el Vibe Coder **no abren esta carpeta**. Su punto de entrada es `EMPIEZA-AQUI.md`.

## Tu papel como Arquitecto
Eres el **puente** entre lo humano y lo técnico:
1. **Traduces.** Cuando la familia o el Vibe Coder piden algo, lo conviertes en spec y tarjeta aquí. A ellos les respondes con un encargo en palabras sencillas (`encargos-del-arquitecto.md`).
2. **Revisas al final.** Lo que la familia llena lo revisa primero Claude con `revisar-decision`. Tú revisas el resultado completo y apruebas.
3. **Eres dueño de las mejoras.** Specs, ADR, skills, subagentes, prompts y el tablero son tuyos.
4. **Cuidas el lenguaje.** Cualquier archivo nuevo para personas pasa por `revisor-gramatical` en modo de revisión final antes de publicarse.

## Cómo fluye una decisión
```
Familia (frases simples en mis-datos/)
  → "Revisa mi decisión" (skill revisar-decision)
      1. auditor-privacidad
      2. revisor-gramatical (pulir ideas)
      3. organizar: DEC-NNN, pilares, quién lo cuida, límites, fechas
      4. revisor-decisiones
      5. puntuar-decision
      6. respuesta en palabras simples (informe técnico guardado para ti)
  → la familia corrige → Arquitecto revisa y aprueba → la Junta decide
  → al final: generador-json → tablero
```

## Qué hay aquí
| Carpeta | Contenido |
|---|---|
| `docs/` | Principios, flujo SDD, privacidad, método 1–10, roles, RAG/memoria/logs, glosario |
| `specs/` | Constitución + specs 001 (captura) y 002 (tablero) + plantillas SDD |
| `skills/` | `revisar-decision` (cadena completa), `puntuar-decision` y los 5 ejecutivos |
| `subagentes/` | `auditor-privacidad`, `revisor-gramatical`, `revisor-decisiones`, `revisor-entregable`, `investigador`, `generador-json` |
| `prompts/` | Prompts de sistema (familia y Vibe Coder), humanos y de agente |
| `flujo-trabajo/` | Tarjetas, checklist, bitácora de revisiones, ADR, estado del proyecto y `registros/` |
| `tablero/` | Requisitos y prompt para generar el dashboard |
| `aprendizaje/` | Ejercicios del Arquitecto y guía para futuros colaboradores técnicos |
| `PROMPT_CONTINUIDAD.md` | Para continuar el proyecto en otra conversación o con otra IA |

## Equivalencias (ADR-002)
| Antes | Ahora (para personas) |
|---|---|
| `datos/plantillas/limites-duros.plantilla.md` | `familia/1-lo-que-nunca-aceptamos.md` |
| `datos/plantillas/bandas.plantilla.md` | `familia/2-dinero-en-rangos.md` |
| `datos/plantillas/perfil-familia.plantilla.md` | `familia/3-quienes-somos.md` |
| `datos/plantillas/pros-contras-vida-actual.plantilla.md` | `familia/4-como-estamos-hoy.md` |
| `datos/plantillas/fechas-limite.plantilla.md` | `familia/5-fechas-importantes.md` |
| `datos/plantillas/decision.plantilla.md` | `decisiones/nueva-decision.md` |
| `datos/plantillas/estimacion-individual.plantilla.md` | `decisiones/mi-opinion-a-solas.md` |
| `datos/ejemplos/decision-ejemplo*.md` | `decisiones/ejemplos/escuela*.md` y `seguro-medico.md` |
| `datos/plantillas/pulso-satisfaccion.plantilla.md` | `juntas/como-nos-sentimos.md` |
| `flujo-trabajo/acta-junta.plantilla.md` | `juntas/notas-de-la-junta.md` |
| `flujo-trabajo/bitacora-decisiones.plantilla.md` | `juntas/lo-que-decidimos.md` |
| `datos/reales/` | `mis-datos/` (no se sube a GitHub) |
| Tarjeta de tarea (para el Vibe Coder) | `encargos-del-arquitecto.md` (las tarjetas quedan para trabajo técnico) |

## Vocabulario: persona ↔ técnico
| La familia dice | En lo técnico |
|---|---|
| camino | rama / opción (`R-NN`) |
| "6 de 10 veces" | probabilidad 0.6 |
| lo bueno / lo malo | pros / contras |
| calificación | nota 1–10 |
| lo que nunca aceptamos | límite duro (`LD-NN`) |
| el número de la decisión | `DEC-NNN` |
| el encargado de dinero / salud / escuela / casa / rumbo | `cfo` / `jefe-atencion` / `vp-producto` / `coo` / `ceo` |
| hay que arreglar / conviene revisar / una idea / falta saber | BLOQUEANTE / IMPORTANTE / SUGERENCIA / PENDIENTE |
| dinero, salud, familia, aprender, seguridad | pilares `riqueza`, `salud`, `tiempo_familia`, `educacion`, `seguridad` |

## Regla para archivos nuevos para personas
Antes de agregar un archivo a `familia/`, `decisiones/`, `juntas/` o a la raíz:
- [ ] Solo hace preguntas en frases simples. Sin IDs, pilares, porcentajes ni separadores especiales.
- [ ] Tiene "¿Qué es esto?", "Cómo llenarlo" y un ejemplo que dice EJEMPLO FICTICIO.
- [ ] Pasó por `revisor-gramatical` (revisión final) sin hallazgos IMPORTANTES.
- [ ] Lo que la IA debe asignar está documentado en `docs/03-metodo-probabilistico.md` o en `skills/revisar-decision/SKILL.md`.
