# datos/ — Datos de la familia (zona VERDE)

**Regla:** aquí solo hay alias y bandas. Las cifras exactas y los nombres reales viven en `privado/`.

| Subcarpeta | Qué contiene | Quién la usa |
|---|---|---|
| `plantillas/` | Formularios Markdown que **llenan los humanos** | Junta |
| `ejemplos/` | Plantillas llenas + su lectura esperada (EJEMPLO FICTICIO) | Vibe Coder, pruebas |
| `reales/` | _(se crea al usar el sistema; está en .gitignore)_ Copias llenas de las plantillas | Junta |

## Orden de llenado (primera vez)
1. `plantillas/bandas.plantilla.md`: define las bandas de dinero.
2. `plantillas/limites-duros.plantilla.md`: qué nunca aceptarán.
3. `plantillas/perfil-familia.plantilla.md`: los dominios de la familia.
4. `plantillas/pros-contras-vida-actual.plantilla.md`: cómo está la vida hoy.
5. `plantillas/fechas-limite.plantilla.md`: todo lo que tiene fecha.
6. `plantillas/decision.plantilla.md`: una por decisión.
7. `plantillas/estimacion-individual.plantilla.md`: cada padre, a solas, por decisión.
8. `plantillas/pulso-satisfaccion.plantilla.md`: cada mes.

## Cómo se escribe (todas las plantillas)
- **Listas, no tablas.** Una idea por línea, separada con ` · `.
- **Notas del 1 al 10:** 1 = muy malo (reprobado al máximo) · 6 = apenas aprobado · 10 = más que excelente.
- **Sin pesos y sin JSON.** La IA calcula y, al final, genera el JSON del tablero.

Ejemplo: `- Mudanza a ciudad natal · dinero · 10`

## Cómo se usa una plantilla
1. Copia la plantilla a `datos/reales/` con un nombre descriptivo (por ejemplo `decision-escuela-hijo1.md`).
2. Borra la sección "Ejemplo" de tu copia.
3. Llénala. Si no sabes un dato, escribe `PENDIENTE: ¿…?`.
4. Pide a Claude: *"Revisa este archivo con auditor-privacidad y revisor-decisiones, y luego usa la skill puntuar-decision."*

## Ejemplo
Ver `ejemplos/decision-ejemplo.md` (lo que escribe un humano) y `ejemplos/decision-ejemplo-puntuada.md` (lo que calcula la IA).
