# 000 — Constitución de Family Decision Board

**Versión:** 1.2 (propuesta) · **Fecha:** 2026-10-05 · **Dueño:** Arquitecto de Soluciones IA

> **Cambios:**
> - ADR-001 (`tecnico/flujo-trabajo/registros/2026-10-05-adr-001-listas-y-notas.md`): firmado por el Arquitecto y la Junta. Falta cambiar su estado a "aceptado".
> - ADR-002 (`tecnico/flujo-trabajo/registros/2026-10-05-adr-002-proyecto-para-no-tecnicos.md`): **propuesto**. Cambia los artículos 2, 4.2 y 5.2. No está vigente hasta que lo firmen el Arquitecto y la Junta.

> La constitución está por encima de cualquier spec, plan, tarjeta o prompt. Para cambiarla hace falta un ADR (`tecnico/flujo-trabajo/adr.plantilla.md`) firmado por el Arquitecto y la Junta.

## Artículo 1 — Propósito
El sistema ayuda a la familia a decidir con datos y probabilidades, y a convertir cada decisión en acciones fechadas.

## Artículo 2 — Humanos e IA
2.1 Los humanos **crean** los datos contestando preguntas en frases simples, **aprueban** los cambios (Arquitecto) y **deciden** (Junta).
2.2 La IA **ordena la redacción**, **asigna** números, pilares y quién vigila cada cosa, **calcula**, **revisa**, **recomienda** y, al final, **genera el JSON** del tablero. No aprueba, no decide, no cambia el sentido de lo que escriben los humanos y no actúa sobre cuentas externas. La Junta puede cambiar cualquier asignación.
2.3 Los humanos escriben **solo frases simples y listas**. Nunca escriben ni editan JSON, IDs, tablas de puntuación ni pesos, y nunca necesitan abrir `tecnico/`.
2.4 El Arquitecto es el puente entre lo humano y lo técnico: traduce las necesidades, revisa al final y es dueño de las mejoras futuras. El Vibe Coder es un ayudante no técnico.

## Artículo 3 — Privacidad
3.1 Zona ROJA: nunca entra a la IA. 3.2 Zona ÁMBAR: solo como bandas. 3.3 Zona VERDE: alias y bandas.
3.4 Todo archivo nuevo pasa por `auditor-privacidad` antes de subirse a Claude.

## Artículo 4 — Método
4.1 Toda decisión incluye el camino "seguir como estamos".
4.2 En cada camino, lo que podría pasar se expresa "de cada 10 veces" y suma 10. Cada cosa tiene su porqué.
4.3 Cada camino tiene lo bueno y lo malo en lista, con una nota del 1 (muy malo) al 10 (más que excelente). La IA asigna el pilar. La nota del camino es el promedio simple. No hay pesos.
4.4 Un camino con más de 1 de cada 10 posibilidades de romper un límite duro ("lo que nunca aceptamos") no puede recomendarse.

## Artículo 5 — Proceso
5.1 SDD: Constitución → Spec → Plan → Tareas → Implementación → Revisión IA → Aprobación → Entrega.
5.2 Para el trabajo técnico: sin spec no hay tarjeta y sin tarjeta no hay trabajo. Llenar datos de la familia y los encargos del Vibe Coder no requieren spec ni tarjeta.
5.3 Toda decisión y toda revisión se registran en una bitácora.

## Artículo 6 — Idioma y estilo
6.1 Idioma oficial: español. 6.2 El JSON lo genera solo la IA (`tecnico/subagentes/generador-json.md`) con claves en español, minúsculas, sin acentos y con guion bajo.
6.3 Se usan los términos del glosario (`tecnico/docs/glosario.md`).

## Artículo 7 — Ejemplos
Todo ejemplo dice `EJEMPLO FICTICIO`. Las decisiones del Playbook original no se usan como datos.

## Artículo 8 — Infraestructura
No hay RAG, backend ni base de datos mientras no se supere un umbral de `tecnico/docs/05-rag-memoria-logs.md`, y en ese caso hace falta un ADR.

## Firmas
| Rol | Alias | Fecha | Firma |
|---|---|---|---|
| Arquitecto de Soluciones IA | Padre-A | | |
| Junta | Padre-B | | |

## Ejemplo de aplicación (EJEMPLO FICTICIO)
Un Vibe Coder propone "guardar las decisiones en Firebase para verlas en el celular". El Artículo 8 lo bloquea: no se superó ningún umbral. La respuesta correcta es pedir a `generador-json` el JSON y abrirlo en el teléfono, o abrir un ADR si la necesidad persiste.
