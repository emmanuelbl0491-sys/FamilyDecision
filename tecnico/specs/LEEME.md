# tecnico/specs/ — Especificaciones SDD

| Archivo / carpeta | Qué es |
|---|---|
| `000-constitucion.md` | Reglas del proyecto. Toda spec debe cumplirlas |
| `_plantillas/` | `spec`, `plan` y `tareas` para copiar |
| `001-captura-humana-decisiones/` | **Spec real:** cómo capturan decisiones los humanos y cómo las revisa la IA |
| `002-tablero-decisiones/` | **Spec real:** qué debe hacer el dashboard que Claude generará |

## Cómo crear una spec nueva
1. Copia `_plantillas/` a `tecnico/specs/NNN-nombre-corto/` (el siguiente número libre).
2. Renombra `spec.plantilla.md` → `spec.md`, `plan.plantilla.md` → `plan.md` y `tareas.plantilla.md` → `tareas.md`.
3. Llena `spec.md`. Pasa la puerta P1 con el Arquitecto.
4. Llena `plan.md` (P2) y `tareas.md` (P3).

## Ejemplo
`tecnico/specs/003-presupuesto-mensual/` → spec: "La Junta ve su flujo de caja bajo/probable/alto a 24 meses" (dueño: CFO humano).
