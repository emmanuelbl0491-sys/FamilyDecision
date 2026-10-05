# Plantilla — ADR (Registro de Decisión de Arquitectura)

> Se usa cuando cambia el diseño, un esquema, un prompt de sistema, la constitución o la infraestructura (RAG, base de datos, servicios).

```markdown
# ADR-NNN — <título>
Fecha: AAAA-MM-DD · Estado: propuesto | aceptado | rechazado | reemplazado por ADR-NNN
Autor: Arquitecto · Firmas requeridas: Arquitecto (+ Junta si toca la constitución o la privacidad)

## Contexto
<Qué pasó y qué umbral o problema lo motiva.>
## Decisión
<Qué se hará.>
## Alternativas consideradas
| Alternativa | Pros | Contras |
## Consecuencias
<Qué cambia, qué archivos se tocan, cómo se revierte.>
```

---

## Ejemplo (EJEMPLO FICTICIO)
# ADR-001 — Agregar el campo `fuente` obligatorio en las probabilidades extremas
Fecha: 2026-10-20 · Estado: aceptado · Autor: Padre-A

## Contexto
En dos revisiones aparecieron probabilidades de 0.95 sin fuente que resultaron corazonadas.
## Decisión
`revisor-decisiones` marcará IMPORTANTE toda probabilidad ≥ 0.95 o ≤ 0.05 sin `fuente`.
## Alternativas
| Alternativa | Pros | Contras |
|---|---|---|
| Hacer `fuente` obligatoria siempre | Rigor máximo | Frena la captura humana |
| Solo en extremos (elegida) | Equilibrio | Algunas corazonadas medias pasan |
## Consecuencias
Se modifica la regla 9 de `tecnico/subagentes/revisor-decisiones.md`. Para revertir, basta quitar la regla.
