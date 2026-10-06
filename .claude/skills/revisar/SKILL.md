---
name: revisar
description: Revisa una decisión que llenó la familia y la califica, contestando en palabras simples. Úsala con /revisar, "revisa mi decisión" o al terminar /llenar nueva decisión. Compara también las opiniones a solas de los dos padres.
argument-hint: "[nombre de la decisión o archivo de mis-datos/decisiones/]"
---

# /revisar — Revisar una decisión

1. **Encuentra la decisión.**
   - Si no se indicó, lista las de `mis-datos/decisiones/` (sin las `opinion-*`) y pregunta cuál con AskUserQuestion. Muestra la pregunta de cada una, no el nombre del archivo.
   - Si no hay ninguna, ofrece `/llenar nueva decisión`.
2. **Sigue al pie de la letra** `tecnico/skills/revisar-decision/SKILL.md`:
   1. privacidad
   2. pulir la redacción
   3. organizar (número, quién lo cuida, límites)
   4. buscar errores
   5. calificar
   6. responder en palabras simples
3. **Opiniones a solas.** Si existen `mis-datos/decisiones/opinion-<tema>-padre-a.md` y `…-padre-b.md`, pregunta: "¿Ya terminaron los dos su opinión a solas?". Compáralas solo si dicen que sí. Muestra solo las diferencias grandes: 2 o más de 10, o más de 3 puntos en una calificación.
4. **Guarda lo que asignaste.** Escribe el número de la decisión y "quién lo cuida" al inicio del archivo de la decisión, en una línea: `**Número:** DEC-NNN · **La vigila:** <encargado> y <Padre-X>`. **No cambies** nada más de lo que escribió la familia: las correcciones las hace la persona, con `/llenar editar`.
5. **Guarda el informe técnico** para el Arquitecto en `mis-datos/revisiones/AAAA-MM-DD-DEC-NNN.md`. A la persona no se lo muestres, salvo que lo pida.
6. **Cierra** con: `[ Arreglar lo que falta ahora ] [ Después ]`. Si elige ahora, usa `/llenar editar <decisión>`.

Nunca uses palabras técnicas con la persona y nunca marques la decisión como aprobada: eso lo hace el Arquitecto.
