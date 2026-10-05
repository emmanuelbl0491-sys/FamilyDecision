# Empieza aquí

## ¿Qué es esto?
Un sistema para que la familia tome decisiones importantes con calma y con orden, no con corazonadas.
Ustedes escriben con palabras sencillas. Claude ordena, revisa y hace las cuentas. **Ustedes deciden.**

## ¿Quién hace qué?
- **Padre-A y Padre-B (la Junta):** llenan los archivos y toman todas las decisiones.
- **El Vibe Coder:** ayuda a la familia a llenar los archivos y usa las frases listas con Claude.
- **El Arquitecto:** es el puente con la parte técnica. Revisa que todo funcione y atiende las dudas técnicas.
- **Claude:** pone números, ordena la redacción, revisa errores, hace las cuentas y recomienda. **Nunca decide.**

## 4 reglas
1. **Nada de nombres reales.** Escribe Padre-A, Padre-B, Hijo-1, Hijo-2.
2. **Nada de cantidades exactas.** Usa los rangos de dinero (rango A, B, C…).
3. **Califica del 1 al 10.** 1 = muy mal · 5 = regular, no alcanza · 6 = apenas bien · 10 = más que excelente.
4. **Si no sabes algo, escribe "no sé".** No adivines.

No te preocupes por escribir bonito. Claude pule la redacción antes de revisar nada.

## Dónde guardar lo que llenas
Nunca escribas sobre los archivos originales: son el formato en blanco. Haz una copia en la carpeta `mis-datos/` y llena la copia. Esa carpeta nunca se sube a internet. También puedes pedirle a Claude: *"Ayúdame a llenar [archivo]. Hazme las preguntas una por una."*

---

## Paso a paso

### Preparación (una sola vez)

1.- **Configuración de Claude:** empieza aquí.
- En Claude, entra a Settings > Privacy y apaga "Help improve Claude".
- Sirve para que lo que escribas de tu familia no se use para entrenar a la IA.

2.- **`privado/LEEME.md`**
- Anota en tu computadora quién es quién (Padre-A = …) y las cantidades exactas de dinero.
- El ejemplo está en el mismo archivo.
- Sirve para guardar lo que **nunca** se le da a Claude.

### Conocer a la familia (la primera vez; después solo se actualiza)

3.- **`familia/1-lo-que-nunca-aceptamos.md`**
- Escribe frases que empiecen con "Nunca vamos a…".
- El ejemplo está al final del mismo archivo.
- Sirve para que Claude descarte los caminos peligrosos.

4.- **`familia/2-dinero-en-rangos.md`**
- Pon el dinero en rangos con letra.
- El ejemplo está al final del mismo archivo.
- Sirve para hablar de dinero sin cifras exactas.

5.- **`familia/3-quienes-somos.md`**
- Contesta preguntas sencillas sobre la familia.
- El ejemplo está al final del mismo archivo.
- Sirve para que Claude entienda su situación.

6.- **`familia/4-como-estamos-hoy.md`**
- Haz una lista de lo bueno y lo malo de su vida hoy, con calificación.
- El ejemplo está al final del mismo archivo.
- Sirve para descubrir qué decisión conviene tomar primero.

7.- **`familia/5-fechas-importantes.md`**
- Escribe cada fecha y qué vence ese día.
- El ejemplo está al final del mismo archivo.
- Sirve para que no se les pase una inscripción o un trámite.

### Cada vez que haya una decisión

8.- **`decisiones/nueva-decision.md`**
- Escribe la pregunta, los caminos, qué podría pasar y lo bueno y lo malo de cada camino.
- Hay dos ejemplos: `decisiones/ejemplos/escuela.md` y `decisiones/ejemplos/seguro-medico.md`.
- Sirve para cualquier decisión grande: escuela, seguro, mudanza, auto, otro hijo.

9.- **`decisiones/mi-opinion-a-solas.md`**
- Cada padre llena su copia **sin ver la del otro**.
- El ejemplo está al final del mismo archivo.
- Sirve para descubrir en qué no están de acuerdo.

10.- **Pedir la revisión:** usa `frases-para-claude.md`.
- Pega en Claude: *"Revisa mi decisión [nombre del archivo]."*
- Lo que contesta Claude se ve como `decisiones/ejemplos/escuela-resultado.md`.
- Claude te dice qué arreglar y cómo sale cada camino.

11.- **Arreglar:** corrige tu copia con lo que te dijo Claude y pide la revisión otra vez. Corriges tú; Claude no cambia tus respuestas.

### La junta (domingo, 30 minutos)

12.- **`juntas/notas-de-la-junta.md`**
- Contesta 5 preguntas: qué es urgente, cómo va el dinero, qué decidieron, qué hay que hacer y cuándo es la próxima junta.
- El ejemplo está al final del mismo archivo.

13.- **`juntas/lo-que-decidimos.md`**
- Agrega una línea por cada decisión. Nunca borres líneas.
- El ejemplo está al final del mismo archivo.

### Cada mes

14.- **`juntas/como-nos-sentimos.md`**
- Cada integrante califica del 1 al 10 cómo se siente en 5 temas.
- El ejemplo está al final del mismo archivo.

---

## Si eres el Vibe Coder
- Tus tareas están en `encargos-del-arquitecto.md`.
- Usa las frases de `frases-para-claude.md`.
- **No abras la carpeta `tecnico/`.** Es del Arquitecto y de Claude.
- Si algo se ve técnico o no se entiende, no es tu culpa: avísale al Arquitecto.

## Si te atoras
- Pídele a Claude: *"Explícamelo con palabras sencillas."*
- Si sigue sin entenderse, pregúntale al Arquitecto.
