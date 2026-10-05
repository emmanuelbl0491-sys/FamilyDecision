# Prompt para generar el tablero

> Úsalo **cuando el proyecto esté completo** (spec 001 cerrada y spec 002 aprobada). Antes, pide a `generador-json` el JSON de los ejemplos de `datos/ejemplos/`. Adjunta o pega los archivos indicados. **Nunca adjuntes datos reales**: el tablero se prueba con el ejemplo y los datos reales se pegan después, dentro del tablero.

---

```markdown
Rol: desarrollador frontend del proyecto Family Decision Board.
Tarea: crea el tablero de decisiones como un artifact HTML de una sola página.

Contexto (adjunto):
- tablero/requisitos-tablero.md      ← contrato; cumple RT-01 a RT-12
- subagentes/generador-json.md       ← estructura del JSON (contrato v2.0)
- JSON generado por generador-json   ← datos precargados (EJEMPLO FICTICIO)
- docs/03-metodo-probabilistico.md   ← notas del 1 al 10 y reglas
- specs/000-constitucion.md          ← reglas no negociables

Restricciones:
- Español en toda la interfaz.
- Sin localStorage, sin red, sin conectores ni almacenamiento: los datos viven
  solo en la pestaña abierta.
- Solo muestra; no se capturan decisiones (eso lo hace la spec 001).
- Los cálculos deben dar exactamente los valores de la prueba de aceptación.

Salida: el artifact publicado y una lista RT-01…RT-12 con "cumple / no cumple"
y cómo verificarlo.

Termina cuando: la prueba de aceptación de requisitos-tablero.md pase con
el JSON de ejemplo.
```

---

## Después de generarlo
1. El Arquitecto revisa la lista RT y la prueba de aceptación.
2. `auditor-privacidad` revisa el código del tablero (que no use almacenamiento ni red).
3. Se registra en `flujo-trabajo/bitacora-revisiones` y se aprueba con el checklist.

## Ejemplo de respuesta esperada (fragmento)
- RT-03 · cumple · DEC-001 muestra "Empate técnico (diferencia 0.17)"
- RT-10 · cumple · el código no contiene `localStorage`, `fetch` ni `XMLHttpRequest`
