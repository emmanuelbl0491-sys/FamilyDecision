# 000 — Constitución de Family Decision Board

**Versión:** 1.1 (propuesta) · **Fecha:** 2026-10-05 · **Dueño:** Arquitecto de Soluciones IA

> **Cambio pendiente de firma:** los artículos 2.2, 4.2, 4.3, 4.4 y 6.2 cambian según `flujo-trabajo/registros/2026-10-05-adr-001-listas-y-notas.md` (estado: propuesto). No están vigentes hasta que firmen el Arquitecto y la Junta.

> La constitución está por encima de cualquier spec, plan, tarjeta o prompt. Para cambiarla hace falta un ADR (`flujo-trabajo/adr.plantilla.md`) firmado por el Arquitecto y la Junta.

## Artículo 1 — Propósito
El sistema ayuda a la familia a decidir con datos y probabilidades, y a convertir cada decisión en acciones fechadas.

## Artículo 2 — Humanos e IA
2.1 Los humanos **crean** los datos (plantillas), **aprueban** los cambios (Arquitecto) y **deciden** (Junta).
2.2 La IA **calcula**, **revisa**, **recomienda** y, al final, **genera el JSON** del tablero. No aprueba, no decide y no actúa sobre cuentas externas.
2.3 Los humanos escriben **solo listas en Markdown**. Nunca escriben ni editan JSON, tablas de puntuación ni pesos.

## Artículo 3 — Privacidad
3.1 Zona ROJA: nunca entra a la IA. 3.2 Zona ÁMBAR: solo como bandas. 3.3 Zona VERDE: alias y bandas.
3.4 Todo archivo nuevo pasa por `auditor-privacidad` antes de subirse a Claude.

## Artículo 4 — Método
4.1 Toda decisión incluye la opción "quedarse igual".
4.2 Los porcentajes de los resultados de cada rama (opción) suman 100%. Cada uno tiene su porqué.
4.3 Cada rama tiene pros y contras en lista, con pilar y una nota del 1 (muy malo) al 10 (más que excelente). La nota de la rama es el promedio simple. No hay pesos.
4.4 Una rama con riesgo de límite duro mayor al 10% no puede recomendarse.

## Artículo 5 — Proceso
5.1 SDD: Constitución → Spec → Plan → Tareas → Implementación → Revisión IA → Aprobación → Entrega.
5.2 Sin spec no hay tarjeta. Sin tarjeta no hay trabajo.
5.3 Toda decisión y toda revisión se registran en una bitácora.

## Artículo 6 — Idioma y estilo
6.1 Idioma oficial: español. 6.2 El JSON lo genera solo la IA (`subagentes/generador-json.md`) con claves en español, minúsculas, sin acentos y con guion bajo.
6.3 Se usan los términos del glosario (`docs/glosario.md`).

## Artículo 7 — Ejemplos
Todo ejemplo dice `EJEMPLO FICTICIO`. Las decisiones del Playbook original no se usan como datos.

## Artículo 8 — Infraestructura
No hay RAG, backend ni base de datos mientras no se supere un umbral de `docs/05-rag-memoria-logs.md`, y en ese caso hace falta un ADR.

## Firmas
| Rol | Alias | Fecha | Firma |
|---|---|---|---|
| Arquitecto de Soluciones IA | Padre-A | | |
| Junta | Padre-B | | |

## Ejemplo de aplicación (EJEMPLO FICTICIO)
Un Vibe Coder propone "guardar las decisiones en Firebase para verlas en el celular". El Artículo 8 lo bloquea: no se superó ningún umbral. La respuesta correcta es pedir a `generador-json` el JSON y abrirlo en el teléfono, o abrir un ADR si la necesidad persiste.
