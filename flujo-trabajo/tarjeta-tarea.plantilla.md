# Plantilla — Tarjeta de tarea

> La escribe el Arquitecto y la recibe el Vibe Coder. Se pega como contexto en la sesión con `prompts/sistema/prompt-sistema-vibe-coder.md`. Duración máxima: 2 horas.

```markdown
TARJETA: T-NNN-NN — <título>
SPEC: specs/NNN-*/spec.md (RF-xx, CA-xx)
POR QUÉ: <qué necesidad humana resuelve>
ENTRADA: <archivos que se leen>
SALIDA: <archivos que se crean o modifican; nada más>
DEBE:
- <regla verificable>
NO DEBE:
- Usar datos reales
- Agregar red, almacenamiento, librerías o servicios
- Tocar archivos fuera de SALIDA
TERMINADO CUANDO:
1. <criterio verificable>
REVISIÓN IA: revisor-entregable → auditor-privacidad → revisor-gramatical
APRUEBA: Arquitecto (checklist-arquitecto.md)
APRENDIZAJE: <qué principio de trabajo con IA practica el Vibe Coder>
```

---

## Ejemplo (EJEMPLO FICTICIO)
```markdown
TARJETA: T-001-03 — Probar la skill puntuar-decision con el ejemplo
SPEC: specs/001-captura-humana-decisiones/spec.md (RF-02, RF-08, CA-01)
POR QUÉ: la Junta necesita confiar en que las notas de sus listas se promedian bien.
ENTRADA: datos/ejemplos/decision-ejemplo.md, skills/puntuar-decision/SKILL.md
SALIDA: flujo-trabajo/registros/2026-10-16-prueba-T-001-03.md
DEBE:
- Ejecutar la skill en una conversación nueva con solo esos dos archivos.
- Comparar el resultado línea por línea con datos/ejemplos/decision-ejemplo-puntuada.md.
NO DEBE:
- Editar la skill ni el ejemplo para que "coincidan".
- Usar datos reales.
TERMINADO CUANDO:
1. El registro muestra la salida de la skill y la comparación.
2. Rama 1 = 6.67, rama 2 = 6.50, "empate técnico" y 1 PENDIENTE.
3. Toda diferencia queda listada con la línea exacta.
REVISIÓN IA: revisor-entregable → auditor-privacidad → revisor-gramatical
APRUEBA: Arquitecto
APRENDIZAJE: "verificar en vez de confiar": la salida de la IA se compara contra un resultado esperado.
```
