# 01 — Flujo SDD (Spec-Driven Development)

**Propósito:** que todo lo que se construya pase por especificación, plan, tareas, implementación y revisión, con humanos en cada puerta.
**Dueño:** Arquitecto de Soluciones IA · **Última revisión:** 2026-10-05

## Fases y puertas

```
  F0 Constitución ─► F1 Spec ─► F2 Plan ─► F3 Tareas ─► F4 Implementación ─► F5 Revisión IA ─► F6 Aprobación ─► F7 Entrega
        │              │           │           │               │                    │                 │
     Arquitecto     Arquitecto  Arquitecto  Arquitecto     Vibe Coder         Subagentes         Arquitecto
                    + Junta                                + Claude          (informe, no         (+ Junta si
                                                                              aprueban)          cambia datos)
  PUERTA:          P1          P2          P3              P4                   P5                 P6
```

| Fase | Entregable | Plantilla | Quién escribe | Puerta para avanzar |
|---|---|---|---|---|
| F0 Constitución | Reglas del proyecto | `specs/000-constitucion.md` | Arquitecto | Firmada |
| F1 Spec | Qué y por qué, criterios de aceptación | `specs/_plantillas/spec.plantilla.md` | Arquitecto (+ Junta para datos) | **P1:** sin "PENDIENTE" críticos |
| F2 Plan | Cómo: archivos, formatos de lista, riesgos | `specs/_plantillas/plan.plantilla.md` | Arquitecto | **P2:** respeta la constitución |
| F3 Tareas | Tarjetas pequeñas (≤ 2 h cada una) | `specs/_plantillas/tareas.plantilla.md` + `flujo-trabajo/tarjeta-tarea.plantilla.md` | Arquitecto | **P3:** cada tarjeta tiene "TERMINADO CUANDO" |
| F4 Implementación | Archivos, datos o código | Según tarjeta | Vibe Coder con Claude | **P4:** el Vibe Coder pasa su autochequeo |
| F5 Revisión IA | Informe de revisión | `flujo-trabajo/bitacora-revisiones.plantilla.md` | Subagentes | **P5:** cero hallazgos BLOQUEANTES |
| F6 Aprobación | Firma | `flujo-trabajo/checklist-arquitecto.md` | Arquitecto | **P6:** checklist completo |
| F7 Entrega | JSON generado por `generador-json` + tablero actualizado | `tablero/prompt-generar-tablero.md` | Claude, a pedido humano | Junta lo usa en la junta |

## Reglas del flujo
1. **Sin spec no hay tarjeta. Sin tarjeta no hay trabajo.**
2. Si una fase revela un error en una fase anterior, **se vuelve atrás**: se corrige la spec, no se parcha el código.
3. Los subagentes **nunca aprueban**. Su informe clasifica hallazgos: `BLOQUEANTE`, `IMPORTANTE` o `SUGERENCIA`.
4. La revisión gramatical (español) es la **última** revisión IA, porque los cambios de contenido la invalidan.
5. Cada spec tiene un número (`001`, `002`…) y una carpeta propia en `specs/`.

## Orden de los subagentes en F5
1. `auditor-privacidad`. Va primero: si hay un dato ROJO, se detiene todo.
2. `revisor-decisiones`: porcentajes, notas del 1 al 10 y límites.
3. `revisor-gramatical`: español claro, consistente con el glosario.

## Ciclo de vida de una decisión (datos)

| Estado (`estado`) | Significado | Quién lo cambia |
|---|---|---|
| `borrador` | La Junta está llenando la plantilla | Humano |
| `en_revision` | Los subagentes la revisan | IA (subagente) |
| `corregida` | Los humanos atendieron los hallazgos | Humano |
| `aprobada` | El Arquitecto confirmó su calidad | Arquitecto |
| `decidida` | La Junta votó | Junta |
| `en_ejecucion` | Hay plan de acción fechado | COO humano |
| `cerrada` | Se cumplió o se activó el criterio de salida | Junta |

## Ejemplo (EJEMPLO FICTICIO)
**Necesidad:** "Queremos comparar escuelas para Hijo-1."
- F1: el Arquitecto crea `specs/002-comparar-escuelas/spec.md` con criterios como "muestra el costo por banda y la fecha de admisión".
- F2: el plan define que se reutiliza `decision.plantilla.md` sin cambios (listas con notas).
- F3: tarjeta T-002-01, "Plantilla de escuela con 3 ejemplos ficticios".
- F4: el Vibe Coder la crea con Claude.
- F5: `revisor-gramatical` marca IMPORTANTE: "colegiatura" y "mensualidad" se usan como sinónimos; se elige uno.
- F6: el Arquitecto firma. F7: `generador-json` arma el JSON y el tablero muestra la nueva decisión.
