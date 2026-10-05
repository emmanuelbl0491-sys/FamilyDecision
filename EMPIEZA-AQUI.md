# Empieza aquí — Paso a paso para los humanos

> Para la Junta (Padre-A, Padre-B) y para el Vibe Coder. No necesitas saber programar.
> Sigue los pasos en orden. Cada paso dice **qué archivo usar**, **dónde está su ejemplo** y **para qué sirve**.

## Reglas de oro (léelas una vez)
- **Escribe en listas, no en tablas.** Una idea por línea, separada con ` · `.
- **Notas del 1 al 10:** 1 = muy malo · 5 = regular, no alcanza · 6 = apenas aprobado · 10 = más que excelente.
- **Pilares:** dinero · salud · familia · educación · seguridad.
- **Sin pesos y sin JSON.** La IA hace las cuentas y, al final, genera el JSON.
- **Solo alias y bandas.** Escribe "Padre-A" y "Banda C", nunca nombres reales ni cifras exactas.
- **Si no sabes algo**, escribe `PENDIENTE: ¿…?`. No adivines.
- **Cómo usar una plantilla:** cópiala a `datos/reales/` con un nombre claro (por ejemplo `decision-escuela-hijo1.md`), borra la sección "Ejemplo" de tu copia y llénala.

Línea de ejemplo: `- Mudanza a ciudad natal · dinero · 10`

---

## Preparación (una sola vez)

1.- **Configuración de Claude:** empieza aquí, antes de abrir cualquier archivo.
- Qué hacer: en Claude, entra a Settings > Privacy y apaga "Help improve Claude".
- Más información en `docs/02-privacidad-zonas.md`.
- Úsalo para: que lo que escribas sobre tu familia no se use para entrenar modelos.

2.- **`privado/LEEME.md`:** sigue con este archivo.
- Qué hacer: en tu computadora, crea `privado/clave-alias.md` (quién es Padre-A, Padre-B, Hijo-1…) y `privado/datos-familia.xlsx` con las cifras exactas.
- El ejemplo está en `privado/LEEME.md` (sección "Ejemplo").
- Úsalo para: guardar lo que **nunca** se le da a Claude (nombres reales, identificaciones, cuentas, cifras exactas). Esta carpeta no se sube a ningún lado.

---

## Datos de la familia (la primera vez; después solo se actualizan)

3.- **`datos/plantillas/bandas.plantilla.md`**
- Qué hacer: define rangos de dinero (Banda A, B, C… para el ingreso y G1, G2… para el gasto).
- El ejemplo está al final del mismo archivo.
- Úsalo para: hablar de dinero sin cifras exactas, por ejemplo "la escuela nueva cuesta una banda más".

4.- **`datos/plantillas/limites-duros.plantilla.md`**
- Qué hacer: escribe lo que la familia **nunca** aceptaría, por ejemplo "colchón de emergencia menor a 3 meses".
- El ejemplo está al final del mismo archivo.
- Úsalo para: que la IA descarte automáticamente una rama que ponga en riesgo algo innegociable.

5.- **`datos/plantillas/perfil-familia.plantilla.md`**
- Qué hacer: anota quiénes son, quién viene en camino y los datos por tema (ingresos, seguro, escuela, auto…). Cada dato lleva bajo / probable / alto y una confianza baja, media o alta.
- El ejemplo está al final del mismo archivo.
- Úsalo para: que la IA conozca la situación de la familia sin datos privados.

6.- **`datos/plantillas/pros-contras-vida-actual.plantilla.md`**
- Qué hacer: haz una lista de lo bueno y lo malo de la vida de hoy, con pilar y nota.
- El ejemplo está al final del mismo archivo.
- Úsalo para: descubrir **qué decisión conviene abrir primero**. El pilar con la nota más baja suele señalarla.

7.- **`datos/plantillas/fechas-limite.plantilla.md`**
- Qué hacer: lista todo lo que vence (admisiones, pólizas, trámites), de lo más próximo a lo más lejano.
- El ejemplo está al final del mismo archivo.
- Úsalo para: no perder una fecha que cierra una opción (por ejemplo, la admisión escolar).

---

## Cada vez que haya una decisión

8.- **`datos/plantillas/decision.plantilla.md`**
- Qué hacer: escribe la pregunta, la fecha límite, las ramas (la primera siempre es "Quedarnos como estamos"), qué puede pasar en cada rama con su porcentaje (deben sumar 100%) y los pros y contras con nota.
- Hay dos ejemplos completos:
  - `datos/ejemplos/decision-ejemplo.md`: decisión sencilla (escuela bilingüe).
  - `datos/ejemplos/decision-ejemplo-poliza.md`: decisión con un límite duro.
- Úsalo para: cualquier decisión importante, como cambiar de escuela, de póliza, de ciudad, de auto o tener otro hijo.

9.- **`datos/plantillas/estimacion-individual.plantilla.md`**
- Qué hacer: cada padre llena **su propia copia, a solas**, con sus porcentajes y, si quiere, sus notas.
- El ejemplo está al final del mismo archivo.
- Úsalo para: ver dónde no están de acuerdo. La IA marca las diferencias mayores a 20 puntos en un porcentaje o a 3 en una nota.

10.- **Revisión con IA:** ve a `subagentes/LEEME.md`.
- Qué hacer: pídele a Claude: *"Revisa `datos/reales/decision-escuela-hijo1.md` con auditor-privacidad, después con revisor-decisiones y al final con revisor-gramatical."*
- El ejemplo de informe está en `subagentes/revisor-decisiones.md` (sección "Ejemplo").
- Úsalo para: encontrar errores antes de la junta, como porcentajes que no suman 100%, un pro con nota baja o un dato privado.

11.- **Corrige y anota:** usa `flujo-trabajo/bitacora-revisiones.plantilla.md`.
- Qué hacer: corrige tu Markdown según el informe y anota la revisión. Corriges tú; la IA no corrige por ti.
- El ejemplo está al final del mismo archivo.
- Úsalo para: dejar rastro de qué se revisó y qué se corrigió.

12.- **Aprobación del Arquitecto:** ve a `flujo-trabajo/checklist-arquitecto.md`.
- Qué hacer: el Arquitecto revisa la lista y cambia el estado de la decisión a `aprobada`.
- El ejemplo está al final del mismo archivo.
- Úsalo para: que solo lleguen a la junta decisiones limpias.

13.- **Puntuar:** usa la skill `skills/puntuar-decision/SKILL.md`.
- Qué hacer: pídele a Claude: *"Usa la skill puntuar-decision con esta decisión."*
- El ejemplo de resultado está en `datos/ejemplos/decision-ejemplo-puntuada.md`.
- Úsalo para: ver la nota de cada rama, su punto más débil, el riesgo de límite duro y si hay empate técnico.

---

## La junta (domingo, 30 minutos)

14.- **`flujo-trabajo/acta-junta.plantilla.md`**
- Qué hacer: el COO humano anota los temas urgentes, la decisión votada, el criterio de salida y las acciones con dueño y fecha.
- El ejemplo está al final del mismo archivo.
- Úsalo para: cerrar cada junta con algo concreto y fechado.

15.- **`flujo-trabajo/bitacora-decisiones.plantilla.md`**
- Qué hacer: agrega una línea por cada decisión votada o cerrada. Nunca borres líneas.
- El ejemplo está al final del mismo archivo.
- Úsalo para: aprender con el tiempo comparando lo que estimaron con lo que pasó de verdad.

---

## Cada mes

16.- **`datos/plantillas/pulso-satisfaccion.plantilla.md`**
- Qué hacer: el Jefe de Atención pregunta a cada integrante una nota del 1 al 10 por pilar.
- El ejemplo está al final del mismo archivo.
- Úsalo para: detectar a tiempo si alguien está peor. Si una nota baja 2 puntos o más, se revisa en la junta.

---

## Al final (solo el Arquitecto)

17.- **`subagentes/generador-json.md`** y después **`tablero/prompt-generar-tablero.md`**
- Qué hacer: pídele a Claude que use `generador-json` con las decisiones aprobadas y, luego, que genere el tablero con ese prompt.
- El ejemplo para probar está en `datos/ejemplos/` (las dos decisiones).
- Úsalo para: ver todas las decisiones en un dashboard. **Nadie escribe ni edita el JSON a mano**: si algo está mal, se corrige el Markdown y se genera otra vez.

---

## Si te atoras
- ¿No entiendes una palabra? → `docs/glosario.md`
- ¿Cómo se calculan las notas? → `docs/03-metodo-probabilistico.md`
- ¿Eres Vibe Coder? → `aprendizaje/guia-vibe-coder.md`
- ¿Vas a abrir una conversación nueva con Claude? → pega `PROMPT_CONTINUIDAD.md`
