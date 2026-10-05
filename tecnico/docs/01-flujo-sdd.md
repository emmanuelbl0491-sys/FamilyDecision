# 01 — Flujo SDD (Spec-Driven Development)

**Alcance (ADR-002):** este flujo es para el **trabajo técnico** del Arquitecto. La familia y el Vibe Coder no lo usan: llenan sus archivos y piden "Revisa mi decisión".

**Propósito:** que todo lo que se construya pase por especificación, plan, tareas, implementación y revisión, con humanos en cada puerta.
**Dueño:** Arquitecto de Soluciones IA · **Última revisión:** 2026-10-05

## Fases y puertas

```
  F0 Constitución ─► F1 Spec ─► F2 Plan ─► F3 Tareas ─► F4 Implementación ─► F5 Revisión IA ─► F6 Aprobación ─► F7 Entrega
        │              │           │           │               │                    │                 │
     Arquitecto     Arquitecto  Arquitecto  Arquitecto     Arquitecto         Subagentes         Arquitecto
                    + Junta                                + Claude          (informe, no         (+ Junta si
                                                                              aprueban)          cambia datos)
  PUERTA:          P1          P2          P3              P4                   P5                 P6
```

| Fase | Entregable | Plantilla | Quién escribe | Puerta para avanzar |
|---|---|---|---|---|
| F0 Constitución | Reglas del proyecto | `tecnico/specs/000-constitucion.md` | Arquitecto | Firmada |
| F1 Spec | Qué y por qué, criterios de aceptación | `tecnico/specs/_plantillas/spec.plantilla.md` | Arquitecto (+ Junta para datos) | **P1:** sin "PENDIENTE" críticos |
| F2 Plan | Cómo: archivos, formatos de lista, riesgos | `tecnico/specs/_plantillas/plan.plantilla.md` | Arquitecto | **P2:** respeta la constitución |
| F3 Tareas | Tarjetas pequeñas (≤ 2 h cada una) | `tecnico/specs/_plantillas/tareas.plantilla.md` + `tecnico/flujo-trabajo/tarjeta-tarea.plantilla.md` | Arquitecto | **P3:** cada tarjeta tiene "TERMINADO CUANDO" |
| F4 Implementación | Archivos o código técnico | Según tarjeta | Arquitecto (o colaborador técnico) con Claude | **P4:** pasa su autochequeo |
| F5 Revisión IA | Informe de revisión | `tecnico/flujo-trabajo/bitacora-revisiones.plantilla.md` | Subagentes | **P5:** cero hallazgos BLOQUEANTES |
| F6 Aprobación | Firma | `tecnico/flujo-trabajo/checklist-arquitecto.md` | Arquitecto | **P6:** checklist completo |
| F7 Entrega | JSON generado por `generador-json` + tablero actualizado | `tecnico/tablero/prompt-generar-tablero.md` | Claude, a pedido humano | Junta lo usa en la junta |

## Reglas del flujo
1. **Sin spec no hay tarjeta. Sin tarjeta no hay trabajo técnico.** Llenar datos de la familia no necesita spec.
2. Si una fase revela un error en una fase anterior, **se vuelve atrás**: se corrige la spec, no se parcha el código.
3. Los subagentes **nunca aprueban**. Su informe clasifica hallazgos: `BLOQUEANTE`, `IMPORTANTE` o `SUGERENCIA`.
4. En las decisiones de la familia, la revisión gramatical va **antes** de revisar el contenido: pule las ideas sin cambiar números. En archivos técnicos o plantillas nuevas para personas, va **al final**, como revisión de lenguaje simple.
5. Cada spec tiene un número (`001`, `002`…) y una carpeta propia en `tecnico/specs/`.

## Orden de revisión de una decisión (skill `revisar-decision`)
1. `auditor-privacidad`. Va primero: si hay un dato ROJO, se detiene todo.
2. `revisor-gramatical` (pulir ideas): ordena y aclara sin cambiar el sentido ni los números.
3. Organizar: la IA asigna DEC-NNN, pilares, quién lo cuida, límites y fechas.
4. `revisor-decisiones`: "de cada 10" que suma 10, calificaciones del 1 al 10 y límites.
5. `puntuar-decision` y respuesta en palabras simples.

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
- F1: el Arquitecto crea `tecnico/specs/002-comparar-escuelas/spec.md` con criterios como "muestra el costo por banda y la fecha de admisión".
- F2: el plan define que se reutiliza `decisiones/nueva-decision.md` sin cambios.
- F3: tarjeta T-002-01, "Plantilla de escuela con 3 ejemplos ficticios".
- F4: el Arquitecto la crea con Claude. El Vibe Coder recibe un encargo sencillo para probarla con la familia.
- F5: `revisor-gramatical` marca IMPORTANTE: "colegiatura" y "mensualidad" se usan como sinónimos; se elige uno.
- F6: el Arquitecto firma. F7: `generador-json` arma el JSON y el tablero muestra la nueva decisión.
