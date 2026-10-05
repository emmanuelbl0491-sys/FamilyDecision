# datos/ejemplos/ — Ejemplos de referencia (EJEMPLO FICTICIO)

| Archivo | Para qué |
|---|---|
| `decision-ejemplo.md` | Plantilla de decisión llenada por un humano |
| `decision-ejemplo-puntuada.md` | Salida esperada de la skill `puntuar-decision` (criterio CA-01 de la spec 001) |
| `decision-ejemplo-poliza.md` | Decisión con límite duro: una rama no recomendable (prueba del tablero) |

Estos archivos son la **prueba de regresión** del sistema. Si una skill cambia, su salida debe seguir coincidiendo con estos ejemplos.

## Plantilla para agregar un ejemplo
```markdown
# EJEMPLO FICTICIO — <qué muestra>
> Entrada: <archivo> · Salida esperada: <archivo>
```

## Ejemplo
`decision-ejemplo-error-suma.md`: la misma decisión con una rama cuyos porcentajes suman 90%. Salida esperada: un informe con 1 BLOQUEANTE.
