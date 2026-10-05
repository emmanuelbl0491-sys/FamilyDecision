# Tareas — Spec 001 Captura humana de decisiones

| ID | Tarea | Depende de | Responsable | Estado | Revisión IA | Aprobada |
|---|---|---|---|---|---|---|
| T-001-01 | Firmar o rechazar el ADR-001 (listas con notas, sin pesos ni JSON humano) | — | Arquitecto + Junta | en_revision | — | ☐ |
| T-001-02 | Revisar `decision.plantilla.md` con la Junta (lenguaje natural) | T-001-01 | Vibe Coder + Junta | pendiente | revisor-gramatical | ☐ |
| T-001-03 | Probar la skill `puntuar-decision` con el ejemplo (CA-01) | T-001-02 | Vibe Coder | pendiente | revisor-decisiones | ☐ |
| T-001-04 | Probar los subagentes con los casos de error (CA-02, CA-03) | T-001-03 | Vibe Coder | pendiente | — | ☐ |
| T-001-05 | Prueba con usuario: captura de una decisión real (CA-05) | T-001-04 | Junta | pendiente | los 3 subagentes | ☐ |
| T-001-06 | Registrar resultados en la bitácora y cerrar la spec | T-001-05 | Arquitecto | pendiente | — | ☐ |

## Puerta P3
- [x] Cada tarea tiene "TERMINADO CUANDO" (en su tarjeta) · [x] ≤ 2 h · [x] Sin ciclos

## Tarjeta de ejemplo
Ver `flujo-trabajo/tarjeta-tarea.plantilla.md`, ejemplo T-001-03.
