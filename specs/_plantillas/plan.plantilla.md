# Plan — Spec NNN <Título>

**Autor:** Arquitecto · **Fecha:** AAAA-MM-DD · **Spec:** `specs/NNN-*/spec.md`

## 1. Enfoque técnico
<Cómo se resolverá, en 3–6 frases.>

## 2. Archivos que se crean o modifican
| Archivo | Acción (crear / modificar) | Motivo |
|---|---|---|

## 3. Esquemas y contratos
<Qué formato de lista se usa o cambia. El JSON solo lo genera `generador-json` al final. Si cambia su contrato, enlaza el ADR.>

## 4. Skills, subagentes y prompts involucrados
| Pieza | Uso |
|---|---|

## 5. Riesgos y mitigación
| Riesgo | Probabilidad (baja/media/alta) | Mitigación |
|---|---|---|

## 6. Verificación
<Cómo se probará cada criterio de aceptación.>

## 7. Puerta P2
- [ ] Respeta la constitución · [ ] Sin infraestructura nueva (o con ADR) · [ ] Cada RF tiene archivo y verificación

---

## Ejemplo (EJEMPLO FICTICIO) — Plan de la spec 003

## 1. Enfoque técnico
Se crea una plantilla Markdown de presupuesto. La skill `cfo` la lee y calcula el colchón con la fórmula `colchon = ahorro_liquido / gasto_mensual` en los 3 escenarios.

## 2. Archivos
| Archivo | Acción | Motivo |
|---|---|---|
| `datos/plantillas/presupuesto.plantilla.md` | crear | RF-01 |
| `subagentes/generador-json.md` | modificar | Agrega el presupuesto al JSON del tablero |
| `skills/cfo/SKILL.md` | modificar | Agregar el paso de colchón |

## 5. Riesgos
| Riesgo | Prob. | Mitigación |
|---|---|---|
| Alguien escribe cifras exactas | media | `auditor-privacidad` bloquea cifras en archivos VERDES |

## 6. Verificación
CA-01: usar `datos/ejemplos/presupuesto-ejemplo.md` y comprobar que el colchón probable sea 7.5.
