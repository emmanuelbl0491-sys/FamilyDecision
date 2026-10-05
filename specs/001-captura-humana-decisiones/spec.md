# Spec 001 — Captura humana de decisiones con revisión IA

**Estado:** en_revision · **Versión:** 1.1 (ADR-001, propuesto) · **Autor:** Arquitecto de Soluciones IA · **Fecha:** 2026-10-05 · **Aprobada por:** _(pendiente)_

## 1. Problema
En el tablero v0, las decisiones se capturan celda por celda (probabilidad y 5 puntajes por resultado). La versión 1.0 de esta spec lo pasó a Markdown, pero seguía con tablas de puntaje, pesos que sumaban 100% y archivos JSON. Para una persona no técnica o un Vibe Coder, eso es lento, confuso y propenso a errores.

## 2. Usuarios y objetivo
| Usuario | Quiere… | Para… |
|---|---|---|
| Junta (Padre-A, Padre-B) | Escribir pros y contras en listas con una nota del 1 al 10 | No pensar en JSON, tablas ni pesos |
| Arquitecto | Recibir decisiones ya validadas y con un informe | Aprobar en menos de 10 minutos |
| Vibe Coder | Tener reglas de formato que se lean a simple vista | Mantener el sistema sin romper el tablero |

## 3. Alcance
**Incluye:** plantilla Markdown de decisión en listas, skill `puntuar-decision`, subagentes `auditor-privacidad`, `revisor-decisiones` y `revisor-gramatical`, la bitácora de revisiones y el subagente `generador-json` (solo al final, para el tablero).
**No incluye:** JSON escrito o editado por humanos, pesos, tablas de puntuación, edición dentro del tablero, servicios externos ni almacenamiento en la nube.

## 4. Requisitos funcionales
| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | La Junta llena `decision.plantilla.md` con listas: resultados (`qué · % · porque · fuente · límite duro`) y pros y contras (`qué · pilar · nota`) | Debe |
| RF-02 | Las notas van del 1 (muy malo) al 10 (más que excelente); 6 es apenas aprobado | Debe |
| RF-03 | Si falta un dato, la IA escribe `PENDIENTE` y no lo inventa | Debe |
| RF-04 | `auditor-privacidad` detiene el flujo si encuentra un dato de zona ROJA | Debe |
| RF-05 | `revisor-decisiones` valida que cada rama sume 100%, que las notas estén entre 1 y 10, que exista "quedarse igual" y que cada resultado tenga su porqué | Debe |
| RF-06 | `revisor-gramatical` revisa la claridad y el uso del glosario | Debe |
| RF-07 | Cada revisión produce un informe con hallazgos BLOQUEANTE / IMPORTANTE / SUGERENCIA | Debe |
| RF-08 | La skill `puntuar-decision` calcula la nota de cada rama (promedio simple), el punto más débil y el riesgo de límite duro | Debe |
| RF-09 | Ambos padres pueden estimar a solas y la IA compara sus diferencias | Debería |
| RF-10 | `generador-json` produce el JSON del tablero solo al final, a partir del Markdown aprobado | Debe |

## 5. Requisitos no funcionales
| ID | Requisito |
|---|---|
| RNF-01 | Privacidad: Artículo 3 de la constitución |
| RNF-02 | Una decisión típica se captura en 15 minutos o menos |
| RNF-03 | Idioma: español. Ningún archivo que llena un humano tiene tablas, pesos ni JSON |
| RNF-04 | Funciona dentro de la interfaz de Claude, sin código local obligatorio |

## 6. Criterios de aceptación
- [ ] CA-01 `puntuar-decision` aplicada a `datos/ejemplos/decision-ejemplo.md` da lo mismo que `datos/ejemplos/decision-ejemplo-puntuada.md` (6.67 vs 6.50, empate técnico).
- [ ] CA-02 Si se cambia un porcentaje para que una rama sume 90%, `revisor-decisiones` reporta un BLOQUEANTE.
- [ ] CA-03 Si se pega un CURP ficticio, `auditor-privacidad` detiene el flujo y no repite el valor.
- [ ] CA-04 El informe de revisión cabe en una pantalla (≤ 25 líneas).
- [ ] CA-05 Un padre sin experiencia técnica captura una decisión real en ≤ 15 min (prueba con usuario).
- [ ] CA-06 Ninguna plantilla de `datos/plantillas/` contiene tablas, pesos ni JSON.

## 7. Datos involucrados
| Dato | Zona | Representación |
|---|---|---|
| Pregunta, ramas, resultados, pros y contras | VERDE | Texto con alias |
| Montos | ÁMBAR → VERDE | Bandas |
| Identidad de las personas | ROJA → VERDE | Alias |

## 8. Preguntas abiertas
- PENDIENTE: ¿se exige una fuente en cada porcentaje o basta el porqué? (propuesta: fuente obligatoria solo si hay tasa base pública)
- PENDIENTE: ¿se pide al menos un punto por cada pilar afectado? (ver ADR-001)

## 9. Puerta P1
- [ ] Sin PENDIENTE críticos · [ ] Cumple la constitución (depende de la firma del ADR-001) · [x] Criterios verificables
