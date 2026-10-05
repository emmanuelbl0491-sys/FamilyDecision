# Plan — Spec 001 Captura humana de decisiones

**Autor:** Arquitecto · **Fecha:** 2026-10-05 · **Versión:** 1.1 (ADR-001, propuesto)

## 1. Enfoque técnico
Los humanos escriben **listas** en Markdown, con notas del 1 al 10. La IA revisa directamente el Markdown: tres subagentes en orden (privacidad, consistencia y gramática). La skill `puntuar-decision` calcula promedios. Solo al final, `generador-json` arma el JSON que lee el tablero.

```
decision.plantilla.md (listas)
        ▲                                                │
        │ correcciones humanas                           ▼
        └──── informe ◄── auditor-privacidad ► revisor-decisiones ► revisor-gramatical
                                                         │
                                         Arquitecto aprueba (checklist)
                                                         ▼
                              skill puntuar-decision ► generador-json (F7) ► tablero
```

## 2. Archivos
| Archivo | Acción | Motivo |
|---|---|---|
| `datos/plantillas/decision.plantilla.md` | crear | RF-01 |
| `datos/ejemplos/decision-ejemplo.md` y `decision-ejemplo-puntuada.md` | reescribir | CA-01 |
| `datos/ejemplos/decision-ejemplo-poliza.md` | crear | prueba de límite duro |
| `skills/puntuar-decision/SKILL.md` | reescribir | RF-08 |
| `subagentes/generador-json.md` | crear | RF-10 |
| `datos/plantillas/*.plantilla.md` | pasar a listas | CA-06 |
| `subagentes/auditor-privacidad.md` | crear | RF-04 |
| `subagentes/revisor-decisiones.md` | crear | RF-05 |
| `subagentes/revisor-gramatical.md` | crear | RF-06 |
| `flujo-trabajo/bitacora-revisiones.plantilla.md` | crear | RF-07 |
| `datos/plantillas/estimacion-individual.plantilla.md` | crear | RF-09 |

## 3. Contratos
- Entrada humana: Markdown con encabezados fijos y listas separadas por ` · ` (la IA depende de ellos; no se renombran).
- Salida final: JSON v2.0 definido dentro de `subagentes/generador-json.md`. Solo lo genera la IA.
- Informe: formato fijo de `flujo-trabajo/bitacora-revisiones.plantilla.md`.

## 5. Riesgos
| Riesgo | Prob. | Mitigación |
|---|---|---|
| La IA "rellena" datos faltantes | media | RF-03 + regla 4 de CLAUDE.md + revisor que busca valores sin razón |
| Sin pesos, un pilar importante queda diluido | media | La Junta escribe más puntos sobre lo que le importa; el PENDIENTE del ADR-001 lo revisa |
| Los humanos cambian encabezados de la plantilla | media | La skill avisa que no reconoce la sección y no adivina |
| El revisor gramatical cambia el significado | baja | Solo sugiere y nunca reescribe números |

## 6. Verificación
CA-01: comparar la salida de `puntuar-decision` con el ejemplo puntuado. CA-02 y CA-03: casos de prueba en `aprendizaje/ejercicios-arquitecto.md`. CA-05: prueba con usuario en la junta del 2026-10-18.
