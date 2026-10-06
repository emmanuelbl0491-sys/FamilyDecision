---
name: junta
description: Prepara la junta familiar del domingo en palabras simples (lo urgente, cómo va el dinero, decisiones listas para votar, fechas próximas y cómo se sienten) y después ayuda a llenar las notas y a registrar lo que decidieron. Úsala con /junta, "prepara la junta" o "junta del domingo".
---

# /junta — La junta del domingo

## 1. Preparar el resumen (lee solo `mis-datos/`, nunca `privado/`)
Muestra un resumen de máximo 15 líneas, en palabras simples:
1. **🔴 Urgente:** fechas de `mis-datos/familia/5-fechas-importantes.md` en las próximas 4 semanas, y cualquier camino que ponga en riesgo algo de "lo que nunca aceptamos".
2. **💰 Dinero:** máximo 3 frases, con rangos (nunca cifras), a partir de `quienes-somos` y `dinero-en-rangos`.
3. **🗳️ Decisión para votar:** las decisiones revisadas en `mis-datos/decisiones/` con su calificación por camino. Si alguna no se ha revisado, ofrece `/revisar`.
4. **❤️ Cómo nos sentimos:** si en el último `como-nos-sentimos-*.md` alguien bajó 2 puntos o más.
5. **⏳ Pendiente de la junta pasada:** acciones de la última `mis-datos/juntas/notas-*.md` que no dicen "listo".

Recuerda: Claude **recomienda**; la Junta **decide**. Usa frases como "el camino con mejor calificación, sin riesgos graves, es…", nunca "deben elegir…".

## 2. Después de la junta
1. Pregunta `[ Llenar las notas de la junta ] [ Después ]`. Si dice que sí, sigue `/llenar notas de la junta` (`.claude/skills/llenar/SKILL.md`). Ya traes el resumen, así que propón las respuestas y pide que las confirme o las cambie.
2. Si votaron una decisión, agrega una línea al final de `mis-datos/juntas/lo-que-decidimos.md` (créalo si no existe). Usa el formato de `juntas/lo-que-decidimos.md`: fecha, qué decidieron, calificación, cuándo cambiar de camino y los votos. **Nunca borres líneas de ese archivo.**
3. Agrega a `mis-datos/progreso.md`: `- AAAA-MM-DD — junta: listo`.
4. Cierra con: "Próxima junta: <fecha>. Escribe /junta ese día."
