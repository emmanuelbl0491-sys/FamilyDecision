# ADR-002 — Proyecto reestructurado para personas no técnicas
Fecha: 2026-10-05 · Estado: **propuesto** · Autor: Claude, a pedido del Arquitecto
Firmas requeridas: Arquitecto + Junta (toca la constitución: artículos 2, 4.2 y 5.2, y el rol del Vibe Coder)

- Arquitecto (Padre-A): ______ · Fecha: AAAA-MM-DD
- Junta (Padre-B): ______ · Fecha: AAAA-MM-DD

## Contexto
Aun después del ADR-001 (listas con notas del 1 al 10), el proyecto seguía siendo demasiado técnico para el Vibe Coder, que no es técnico. Tenía que manejar specs, tarjetas, IDs (DEC-NNN, LD-NN), pilares, ejecutivos responsables, separadores ` · `, porcentajes y vocabulario como SDD, skill, subagente o JSON.

## Decisión
1. **Dos mundos separados:**
   - Para personas, en la raíz: `EMPIEZA-AQUI.md`, `frases-para-claude.md`, `encargos-del-arquitecto.md`, `familia/`, `decisiones/`, `juntas/`, `mis-datos/` y `privado/`.
   - Técnico: todo lo demás vive en `tecnico/` (docs, specs, skills, subagentes, prompts, flujo de trabajo, tablero y aprendizaje). Solo lo usan el Arquitecto y Claude.
2. **Los humanos contestan preguntas en frases simples.** Sin IDs, pilares, responsables, separadores ni porcentajes.
3. **La IA determina:** el número de cada cosa (DEC-NNN, LD-NN), el pilar de cada idea, el ejecutivo que la vigila ("quién lo cuida") y la relación entre fechas y decisiones. El humano responsable de una decisión es, por defecto, quien la llenó. La Junta puede cambiar cualquier asignación.
4. **"De cada 10 veces"** reemplaza a los porcentajes (suman 10 por camino). **"Camino"** reemplaza a "rama" u "opción" en los archivos para personas.
5. **Cadena de revisión** (skill `revisar-decision`):
   1. `auditor-privacidad`
   2. `revisor-gramatical`, que pule las ideas sin cambiar el sentido ni los números
   3. organización: IDs, pilares y responsables
   4. `revisor-decisiones`
   5. `puntuar-decision`
   6. respuesta a la familia en palabras simples
6. **Vibe Coder = ayudante no técnico.** Ayuda a llenar archivos y usa frases listas. Recibe "encargos" en palabras sencillas, no tarjetas. Nunca toca `tecnico/`.
7. **Arquitecto = puente.** Traduce entre lo humano y lo técnico, revisa al final y es dueño de las mejoras futuras. Las tarjetas, specs y ADR siguen existiendo, pero solo para trabajo técnico.
8. Los humanos guardan sus copias llenas en `mis-datos/`, que nunca se sube (`.gitignore`).

## Alternativas consideradas
- **Solo simplificar textos, sin mover carpetas.** Pro: menos cambios. Contra: el Vibe Coder seguiría viendo specs y skills al abrir el proyecto.
- **Que Claude entreviste siempre y los humanos no llenen archivos.** Pro: cero archivos. Contra: depende del chat, que no es registro. Se ofrece como opción ("Hazme las preguntas una por una"), no como única vía.
- **Separar en dos mundos (elegida).** Pro: el humano solo ve lo que entiende. Contra: el Arquitecto mantiene la traducción entre ambos.

## Consecuencias
- Se renombraron y movieron las plantillas (ver la tabla de equivalencias en `tecnico/LEEME.md`).
- Se borraron `datos/LEEME.md` y `datos/ejemplos/LEEME.md`. Su contenido pasó a `EMPIEZA-AQUI.md` y `mis-datos/LEEME.md`.
- La familia tenía datos reales en `datos/reales/bandas.md`. Se movieron a `mis-datos/2-dinero-en-rangos.md`, con el formato anterior.
- Los ejemplos ahora usan "de cada 10" (8/2, 6/3/1, 6/4, 9/1). Las calificaciones no cambian: 6.67 / 6.50 y 4.50 / 7.00.
- **Cómo se revierte:** `git revert` del commit que aplica este ADR.
- PENDIENTE: ¿la Junta quiere que la IA proponga al humano responsable con otra regla, distinta de "quien llenó el archivo"?
