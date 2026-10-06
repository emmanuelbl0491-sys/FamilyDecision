# Spec 003 — Guía paso a paso y entrevista para llenar archivos

**Estado:** en_revision · **Autor:** Claude, a pedido del Arquitecto · **Fecha:** 2026-10-05 · **Aprobada por:** _(pendiente)_ · **Depende de:** ADR-002

## 1. Problema
Aun con frases simples, el Vibe Coder (no técnico, usa Claude Code en la terminal) tenía que:
- abrir archivos, copiarlos a `mis-datos/` y llenarlos a mano;
- recordar en qué paso iba;
- saber qué datos faltaban.

Era fácil omitir datos o repetir pasos de una sola vez.

## 2. Usuarios y objetivo
| Usuario | Quiere… | Para… |
|---|---|---|
| Vibe Coder / Junta | Escribir `/empezar` y contestar preguntas | No abrir archivos ni recordar pasos |
| Arquitecto | Que cualquier plantilla nueva se pueda llenar sin programar nada | Agregar funciones futuras con solo escribir una plantilla |

## 3. Alcance
**Incluye:**
- Skills de proyecto en `.claude/skills/`: `empezar`, `llenar`, `revisar` y `junta`.
- `.claude/settings.json` con:
  - bloqueo de lectura y edición de `privado/`;
  - permiso para escribir en `mis-datos/` sin preguntar;
  - saludo al iniciar.
- Estructura de `mis-datos/` y `mis-datos/progreso.md`.

**No incluye:** claude.ai web (el Vibe Coder usa Claude Code), scripts, API ni servicios externos.

## 4. Requisitos funcionales
| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | `/llenar` usa la plantilla como lista de preguntas. No se salta ninguna y no inventa preguntas | Debe |
| RF-02 | Pregunta una cosa a la vez, con ejemplo, y con botones cuando hay opciones | Debe |
| RF-03 | Revisa en el momento: privacidad, calificación del 1 al 10, que cada camino sume 10 de 10, ideas mezcladas y contradicciones | Debe |
| RF-04 | Muestra un resumen y no guarda sin un "Sí" | Debe |
| RF-05 | Guarda en `mis-datos/<carpeta>/` con nombre fijo y registra en `progreso.md` | Debe |
| RF-06 | Permite pausar (borrador) y continuar | Debe |
| RF-07 | Edita o borra solo si se pide explícitamente. Borrar pide doble confirmación. `lo-que-decidimos` nunca se borra | Debe |
| RF-08 | `/empezar` detecta el avance por los archivos existentes y `progreso.md`, salta los pasos de una vez ya hechos y propone un solo siguiente paso | Debe |
| RF-09 | Funciona con plantillas nuevas sin cambiar las skills (regla genérica de destino) | Debe |
| RF-10 | `privado/` está bloqueado por configuración. El paso 2 lo hace la persona sola | Debe |
| RF-11 | En "mi opinión a solas", Claude no muestra la opinión del otro padre. Las compara solo si ambos terminaron | Debe |
| RF-12 | Recordatorio mensual de respaldo de `mis-datos/` (la copia la hace la persona) | Debería |
| RF-13 | `/junta` prepara el resumen del domingo y registra lo decidido | Debería |
| RF-14 | Al abrir `claude` en la carpeta aparece "Hola 👋 Escribe /empezar para continuar." | Debería |

## 6. Criterios de aceptación
- [ ] CA-01 Con `mis-datos/` vacío, `/empezar` muestra los 7 pasos con ⬜ y propone el paso 1.
- [ ] CA-02 Si existe `mis-datos/familia/3-quienes-somos.md`, `/empezar` lo muestra con ✅ y no lo vuelve a preguntar.
- [ ] CA-03 En `/llenar nueva decisión`, si un camino suma 9 de 10, Claude pregunta cuál ajustar antes de seguir.
- [ ] CA-04 Si se escribe un nombre propio, Claude no lo guarda ni lo repite.
- [ ] CA-05 `Read(privado/...)` es rechazado por la configuración (prueba del Arquitecto).
- [ ] CA-06 Una plantilla nueva `familia/6-prueba.md` se puede llenar con `/llenar` sin cambiar ninguna skill.
- [ ] CA-07 El Vibe Coder completa los pasos 3 a 7 sin ayuda técnica (prueba con usuario).

## 8. Preguntas abiertas
- PENDIENTE: el bloqueo de `privado/` cubre las herramientas de lectura y los comandos más comunes (`cat`, `head`, `grep`…), pero no cualquier comando posible. ¿Se activa el sandbox de Claude Code para un bloqueo total?

## 9. Puerta P1
- [ ] Sin PENDIENTE críticos · [ ] Cumple la constitución (depende del ADR-002) · [x] Criterios verificables
