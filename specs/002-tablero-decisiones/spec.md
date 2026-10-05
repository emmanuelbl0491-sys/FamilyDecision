# Spec 002 — Tablero de decisiones (dashboard)

**Estado:** borrador · **Autor:** Arquitecto · **Fecha:** 2026-10-05 · **Depende de:** Spec 001

## 1. Problema
La Junta necesita **ver** cada decisión (árbol, nota de cada rama, pros y contras) y el estado de su vida actual en una sola pantalla durante la junta del domingo. El tablero v0 mezcla captura y visualización, y la captura no funciona para humanos.

## 2. Usuarios y objetivo
| Usuario | Quiere… | Para… |
|---|---|---|
| Junta | Ver árbol, veredicto y pros y contras de cada decisión aprobada | Votar en 30 minutos |
| COO humano | Ver fechas límite y acciones | Dar seguimiento los miércoles |

## 3. Alcance
**Incluye:** visualización de solo lectura a partir del JSON que genera `generador-json` con las decisiones aprobadas: árbol, veredicto, pros y contras por rama con notas del 1 al 10, vida actual y calendario de fechas.
**Sin pesos:** la nota de cada rama es un promedio simple (ADR-001, propuesto).
**No incluye:** captura de decisiones (spec 001), almacenamiento y envío de datos.

## 4. Requisitos funcionales
El detalle completo está en `tablero/requisitos-tablero.md` (RT-01 a RT-12). Esta spec lo aprueba como contrato.

## 6. Criterios de aceptación
- [ ] CA-01 Al cargar el JSON generado con `datos/ejemplos/`, el tablero muestra 2 decisiones y las notas coinciden con los ejemplos (DEC-001: 6.67 y 6.50; DEC-002: 4.50 y 7.00).
- [ ] CA-02 Una decisión en estado `borrador` o `en_revision` no aparece (o aparece marcada "No apta para votar").
- [ ] CA-03 El tablero no usa `localStorage`, ni red, ni conectores (verificación del auditor).
- [ ] CA-04 Se lee bien en un teléfono de 400 px de ancho.

## 8. Preguntas abiertas
- PENDIENTE: ¿la Junta quiere imprimir el acta desde el tablero o desde el documento? (el artifact no puede imprimir directamente)
