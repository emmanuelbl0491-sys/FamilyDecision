# tablero/ — Insumos para que Claude genere el dashboard

El tablero **no se construye a mano**. Cuando el resto del proyecto está aprobado, Claude lo genera a partir de estos archivos. Los humanos nunca escriben JSON: lo genera el subagente `generador-json` al final.

- `requisitos-tablero.md`: contrato del dashboard (RT-01 a RT-12), aprobado por la spec 002.
- `prompt-generar-tablero.md`: prompt exacto para pedirle a Claude el tablero.
- La estructura del JSON vive en `subagentes/generador-json.md` (solo para la IA).

## Flujo
1. El Arquitecto junta las decisiones en estado `aprobada` o posterior, los límites duros, la vida actual y las fechas límite (todo en Markdown).
2. Pide a `generador-json` que arme el JSON. Primero con `datos/ejemplos/` (sin datos reales).
3. Pide el tablero con `prompt-generar-tablero.md` usando ese JSON de ejemplo.
4. Revisa el tablero con los criterios de la spec 002.
5. En la junta, genera el JSON real con `generador-json` y lo **pega** dentro del tablero (se queda solo en la pestaña abierta). El JSON real se guarda en `datos/reales/`, nunca en la nube.

## Referencia
El tablero v0 (prototipo) existe como artifact privado. Sirve como inspiración visual, pero **su captura de datos queda obsoleta** por la spec 001.
