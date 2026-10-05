# Spec 001 — Captura humana de decisiones con revisión IA

**Estado:** en_revision · **Versión:** 1.2 (ADR-001 firmado, ADR-002 propuesto) · **Autor:** Arquitecto de Soluciones IA · **Fecha:** 2026-10-05 · **Aprobada por:** _(pendiente)_

## 1. Problema
En el tablero v0, las decisiones se capturan celda por celda (probabilidad y 5 puntajes por resultado). La versión 1.0 de esta spec lo pasó a Markdown, pero seguía con tablas de puntaje, pesos que sumaban 100% y archivos JSON. Para una persona no técnica o un Vibe Coder, eso es lento, confuso y propenso a errores. La versión 1.1 quitó tablas y pesos, pero aún pedía IDs, pilares, responsables, separadores ` · ` y porcentajes.

## 2. Usuarios y objetivo
| Usuario | Quiere… | Para… |
|---|---|---|
| Junta (Padre-A, Padre-B) | Contestar preguntas con frases simples y calificar del 1 al 10 | No pensar en JSON, IDs, pilares, tablas ni pesos |
| Arquitecto | Recibir decisiones ya validadas y con un informe | Aprobar en menos de 10 minutos |
| Vibe Coder (no técnico) | Ayudar a la familia con frases listas para Claude | No tener que entender nada técnico |

## 3. Alcance
**Incluye:** archivos para personas en `familia/`, `decisiones/` y `juntas/`, skill `revisar-decision` (cadena completa), skill `puntuar-decision`, subagentes `auditor-privacidad`, `revisor-decisiones` y `revisor-gramatical`, la bitácora de revisiones y el subagente `generador-json` (solo al final, para el tablero).
**No incluye:** JSON escrito o editado por humanos, pesos, tablas de puntuación, edición dentro del tablero, servicios externos ni almacenamiento en la nube.

## 4. Requisitos funcionales
| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | La Junta llena `decisiones/nueva-decision.md` con frases simples: lo que podría pasar ("n de 10 veces, porque…") y lo bueno y lo malo ("idea — calificación") | Debe |
| RF-01b | La IA asigna DEC-NNN, pilares, ejecutivo que lo cuida, humano responsable (quien llenó), límites duros y fechas, y lo informa | Debe |
| RF-02 | Las notas van del 1 (muy malo) al 10 (más que excelente); 6 es apenas aprobado | Debe |
| RF-03 | Si falta un dato, la IA escribe `PENDIENTE` y no lo inventa | Debe |
| RF-04 | `auditor-privacidad` detiene el flujo si encuentra un dato de zona ROJA | Debe |
| RF-05 | `revisor-decisiones` valida que cada camino sume 10 de 10, que las calificaciones estén entre 1 y 10, que exista "seguir como estamos" y que cada cosa tenga su porqué | Debe |
| RF-06 | `revisor-gramatical` pule las ideas **antes** de la revisión de contenido, sin cambiar el sentido ni los números | Debe |
| RF-07 | Cada revisión produce un informe técnico (BLOQUEANTE / IMPORTANTE / SUGERENCIA) para el Arquitecto y una respuesta en palabras simples para la familia | Debe |
| RF-08 | La skill `puntuar-decision` calcula la nota de cada rama (promedio simple), el punto más débil y el riesgo de límite duro | Debe |
| RF-09 | Ambos padres pueden estimar a solas y la IA compara sus diferencias | Debería |
| RF-10 | `generador-json` produce el JSON del tablero solo al final, a partir del Markdown aprobado | Debe |

## 5. Requisitos no funcionales
| ID | Requisito |
|---|---|
| RNF-01 | Privacidad: Artículo 3 de la constitución |
| RNF-02 | Una decisión típica se captura en 15 minutos o menos |
| RNF-03 | Idioma: español sencillo. Ningún archivo para personas tiene tablas de puntuación, pesos, JSON, IDs, pilares ni porcentajes |
| RNF-04 | Funciona dentro de la interfaz de Claude, sin código local obligatorio |

## 6. Criterios de aceptación
- [ ] CA-01 `puntuar-decision` aplicada a `decisiones/ejemplos/escuela.md` da lo mismo que `decisiones/ejemplos/escuela-resultado.md` (6.67 vs 6.50, empate técnico).
- [ ] CA-02 Si un camino suma 9 de 10, `revisor-decisiones` reporta un BLOQUEANTE y la familia recibe "Hay que arreglar".
- [ ] CA-03 Si se pega un CURP ficticio, `auditor-privacidad` detiene el flujo y no repite el valor.
- [ ] CA-04 El informe de revisión cabe en una pantalla (≤ 25 líneas).
- [ ] CA-05 Un padre sin experiencia técnica captura una decisión real en ≤ 15 min (prueba con usuario).
- [ ] CA-06 Ningún archivo de `familia/`, `decisiones/` ni `juntas/` contiene tablas, pesos, JSON, IDs, pilares ni porcentajes.
- [ ] CA-07 El Vibe Coder completa el encargo de ejemplo de `encargos-del-arquitecto.md` sin pedir ayuda técnica.

## 7. Datos involucrados
| Dato | Zona | Representación |
|---|---|---|
| Pregunta, caminos, lo que podría pasar, lo bueno y lo malo | VERDE | Texto con alias |
| Montos | ÁMBAR → VERDE | Bandas |
| Identidad de las personas | ROJA → VERDE | Alias |

## 8. Preguntas abiertas
- PENDIENTE: ¿se exige una fuente en cada porcentaje o basta el porqué? (propuesta: fuente obligatoria solo si hay tasa base pública)
- PENDIENTE: ¿se pide al menos un punto por cada pilar afectado? (ver ADR-001)

## 9. Puerta P1
- [ ] Sin PENDIENTE críticos · [ ] Cumple la constitución (depende de la firma del ADR-001) · [x] Criterios verificables
