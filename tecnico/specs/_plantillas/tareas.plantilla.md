# Tareas — Spec NNN <Título>

Cada tarea es una **tarjeta** de máximo 2 horas. El detalle de cada una usa `tecnico/flujo-trabajo/tarjeta-tarea.plantilla.md`.

| ID | Tarea | Depende de | Responsable | Estado | Revisión IA | Aprobada |
|---|---|---|---|---|---|---|
| T-NNN-01 | | — | Vibe Coder | pendiente / en_curso / en_revision / aprobada | | ☐ |

## Puerta P3
- [ ] Cada tarea tiene "TERMINADO CUANDO" · [ ] Ninguna tarea dura más de 2 h · [ ] Las dependencias no forman ciclos

---

## Ejemplo (EJEMPLO FICTICIO) — Tareas de la spec 003

| ID | Tarea | Depende de | Responsable | Estado | Revisión IA | Aprobada |
|---|---|---|---|---|---|---|
| T-003-01 | Crear `presupuesto.plantilla.md` en listas | — | Vibe Coder | aprobada | revisor-decisiones ✔ | ☑ |
| T-003-02 | Crear plantilla de presupuesto con ejemplo | T-003-01 | Vibe Coder | en_revision | revisor-gramatical ⏳ | ☐ |
| T-003-03 | Agregar el cálculo de colchón a la skill `cfo` | T-003-01 | Vibe Coder | pendiente | — | ☐ |
