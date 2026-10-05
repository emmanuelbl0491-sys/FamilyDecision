# Ejemplos de prompts humanos por rol (EJEMPLO FICTICIO)

Todos siguen `plantilla-prompt-humano.md`.

## Junta → CEO (memo del domingo)
```
Rol: CEO
Tarea: Redacta el memo de la junta del 2026-10-25.
Contexto: decisiones puntuadas DEC-001 y DEC-002, fechas-importantes.
Restricciones: una sola decisión a votar; incluye los temas en ROJO.
Salida: el formato MEMO CEO de la skill.
Termina cuando: el memo tenga criterio de salida y siguiente acción.
```

## Junta → COO (miércoles)
```
Rol: COO
Tarea: Lista las acciones de los próximos 7 días.
Contexto: acta de la junta del 2026-10-25, fechas-importantes.
Restricciones: máximo 5 acciones; dueños humanos.
Salida: lista de la skill COO.
Termina cuando: no queden acciones sin dueño.
```

## Junta → VP de Producto
```
Rol: VP de Producto
Tarea: Actualiza la hoja de ruta de Hijo-1 con el pulso de octubre.
Contexto: quienes-somos, pulso 2026-10, DEC-001.
Restricciones: incluye la voz de Hijo-1.
Salida: tabla de la skill.
Termina cuando: cada hito tenga una decisión conectada o una propuesta.
```

## Junta → Jefe de Atención
```
Rol: Jefe de Atención
Tarea: Detecta brechas de cobertura para 2027.
Contexto: quienes-somos (seguro, embarazo), lo-que-nunca-aceptamos.
Restricciones: sin detalles médicos; solo etiquetas generales.
Salida: tabla de brechas + alertas.
Termina cuando: cada brecha tenga una acción y una fecha.
```

## Junta → Captura y revisión
```
Rol: Revisor
Tarea: Revisa mis-datos/decision-poliza.md y puntúala.
Contexto: subagentes auditor-privacidad, revisor-decisiones, revisor-gramatical; skill puntuar-decision.
Restricciones: no corrijas mis datos; solo repórtalos. No uses tablas ni JSON.
Salida: un informe combinado de ≤ 25 líneas + la nota de cada rama.
Termina cuando: el veredicto sea LISTO o tenga hallazgos concretos.
```

## Arquitecto → Claude (diseño)
```
Rol: Asistente del Arquitecto
Tarea: Propón el plan de la spec 003-presupuesto-mensual.
Contexto: tecnico/specs/_plantillas/plan.plantilla.md, constitución, spec 003.
Restricciones: sin infraestructura nueva; plantillas en listas con notas 1–10; sin pesos ni JSON para humanos.
Salida: plan.md completo.
Termina cuando: cada RF tenga archivo y verificación.
```
