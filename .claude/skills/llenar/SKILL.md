---
name: llenar
description: Entrevista a una persona no técnica para llenar cualquier archivo de Family Decision Board (familia/, decisiones/, juntas/). Hace las preguntas de la plantilla una por una, revisa las respuestas, muestra un resumen y guarda el archivo en mis-datos/. También edita o borra un archivo ya llenado si se pide explícitamente. Úsala con /llenar, "ayúdame a llenar…", "quiero agregar…", "editar…" o "borrar…".
argument-hint: "[qué llenar, por ejemplo: nueva decisión | editar quiénes somos]"
---

# /llenar — Llenar un archivo haciendo preguntas

La persona **no es técnica**. Habla con frases cortas y palabras de todos los días. Nunca uses con ella: JSON, ID, pilar, spec, skill, subagente, archivo Markdown, BLOQUEANTE. Las reglas generales están en `CLAUDE.md`.

## 1. ¿Qué vamos a llenar?
Si no lo dijo, pregúntalo con la herramienta **AskUserQuestion** (máximo 4 opciones; "Otro" aparece solo).

| Lo que dice la persona | Plantilla (preguntas) | Dónde se guarda | Tipo |
|---|---|---|---|
| lo que nunca aceptamos | `familia/1-lo-que-nunca-aceptamos.md` | `mis-datos/familia/1-lo-que-nunca-aceptamos.md` | una vez |
| dinero / rangos | `familia/2-dinero-en-rangos.md` | `mis-datos/familia/2-dinero-en-rangos.md` | una vez |
| quiénes somos | `familia/3-quienes-somos.md` | `mis-datos/familia/3-quienes-somos.md` | una vez |
| cómo estamos hoy | `familia/4-como-estamos-hoy.md` | `mis-datos/familia/4-como-estamos-hoy.md` | una vez |
| fechas importantes | `familia/5-fechas-importantes.md` | `mis-datos/familia/5-fechas-importantes.md` | una vez (se agregan fechas) |
| nueva decisión | `decisiones/nueva-decision.md` | `mis-datos/decisiones/AAAA-MM-DD-<tema-corto>.md` | cada vez |
| mi opinión a solas | `decisiones/mi-opinion-a-solas.md` | `mis-datos/decisiones/opinion-<tema-corto>-<padre-a o padre-b>.md` | cada vez |
| notas de la junta | `juntas/notas-de-la-junta.md` | `mis-datos/juntas/notas-AAAA-MM-DD.md` | cada domingo |
| lo que decidimos | `juntas/lo-que-decidimos.md` | `mis-datos/juntas/lo-que-decidimos.md` | solo se agregan líneas |
| cómo nos sentimos | `juntas/como-nos-sentimos.md` | `mis-datos/juntas/como-nos-sentimos-AAAA-MM.md` | cada mes |
| cualquier otro archivo nuevo de `familia/`, `decisiones/` o `juntas/` | ese archivo | `mis-datos/<misma carpeta>/<mismo nombre>.md` | según diga "Cómo llenarlo" |

**Si el archivo de destino ya existe** y es de "una vez": no lo vuelvas a llenar. Di "Esto ya lo llenaron el <fecha>" y pregunta `[ Verlo ] [ Editar algo ] [ Dejarlo así ]`.

**Si hay un borrador** en `mis-datos/borradores/` del mismo archivo: pregunta `[ Seguir donde me quedé ] [ Empezar de nuevo ]`.

## 2. Leer la plantilla y armar la lista de preguntas
1. Lee la plantilla completa. Sus secciones (`##` y `###`), sus preguntas en negritas y su "Cómo llenarlo" **son** la lista de preguntas. No inventes preguntas que no estén ahí y no te saltes ninguna.
2. Usa el EJEMPLO FICTICIO de la plantilla para dar un ejemplo corto en cada pregunta.
3. No leas `privado/` nunca. Está bloqueado y no hace falta.
4. Si hay copias ya llenadas que sirven de contexto (por ejemplo, `mis-datos/familia/1-lo-que-nunca-aceptamos.md` al llenar una decisión), puedes leerlas. **Excepción:** al llenar "mi opinión a solas", **nunca** leas ni menciones la opinión del otro padre.

## 3. Preguntar
- **Una pregunta a la vez.** Encabezado: "Pregunta N de M", el texto de la plantilla en palabras simples y un ejemplo.
- **Con opciones (AskUserQuestion)** cuando las haya:
  - "¿Quién lo llena?" → Padre-A / Padre-B
  - "¿Agregamos otra?" → Sí / No, con esto basta
  - Confirmaciones → Sí / Quiero cambiar algo
  - Qué tan seguro estás → Poco / Más o menos / Muy seguro
  - Calificaciones → muestra la escala: 1 = muy mal, 5 = regular, 6 = apenas bien, 10 = más que excelente
- **Texto libre** para todo lo demás.
- **Listas:** pregunta "¿Agregamos otra?" hasta que diga que no.
  - Lo bueno y lo malo: al menos 1 de cada uno por camino.
  - Lo que podría pasar: de 2 a 4 cosas por camino.
  - Caminos: de 2 a 4, y el primero siempre es "Seguir como estamos". Créalo tú y solo pregunta sus detalles.
- **"No sé"** siempre se vale. Anótalo como "Falta saber: ¿…?" y sigue.
- Si dice **"lo dejo aquí"**, "pausa" o "después sigo": guarda lo que va en `mis-datos/borradores/<nombre>.md` y di "Listo, guardé tu avance. Cuando quieras, escribe /llenar o /empezar".

## 4. Revisar en el momento (antes de pasar a la siguiente pregunta)
- **Privacidad:** si la respuesta trae un nombre real, una identificación, un número de cuenta o tarjeta, una dirección, un teléfono, un correo, un diagnóstico o una cantidad exacta de dinero:
  - **No la guardes ni la repitas.**
  - Di: "⚠️ Eso parece <tipo de dato>. No lo voy a guardar. ¿Cómo lo escribimos con un apodo (Hijo-1) o con un rango (rango C)?"
- **Calificación:** debe ser un número entero del 1 al 10. Si no, vuelve a preguntar.
- **De cada 10:** al terminar lo que podría pasar en un camino, suma. Si no da 10, muestra los números con AskUserQuestion: "Suman 9 y deben sumar 10. ¿Cuál ajustamos?".
- **Ideas mezcladas:** "barato pero lejos — 6" → "Eso son dos ideas: 'barato' y 'lejos'. ¿Qué calificación le das a cada una?".
- **Contradicción:** algo bueno con calificación de 5 o menos, o algo malo con 6 o más. Pregunta con cariño: "¿Seguro? Lo pusiste en lo bueno con un 3".

## 5. Resumen y guardado
1. Muestra el resumen completo con palabras simples: "Esto es lo que entendí:".
2. Muestra "Falta saber:" con todo lo que quedó en "no sé".
3. Pregunta `[ Sí, guárdalo ] [ Quiero cambiar algo ]`. **Nada se guarda sin un "Sí".**
4. Escribe el archivo en su destino:
   - Usa la estructura de la plantilla, sin la sección de EJEMPLO FICTICIO.
   - Pon arriba: `**Lo llenó:** <Padre-X> · **Fecha:** AAAA-MM-DD`.
   - Si había borrador, bórralo.
5. Actualiza `mis-datos/progreso.md` (créalo si no existe): agrega una línea `- AAAA-MM-DD — <qué se llenó> — <Padre-X>`.
6. Di: "✅ Guardado en <ruta>". Luego, según el caso:
   - **Archivo de familia:** di qué asignaste. Por ejemplo: "A 'bebé sin seguro' lo vigila el encargado de salud".
   - **Nueva decisión:** pregunta `[ Revisarla ahora ] [ Después ]`. Si dice ahora, usa `/revisar` con el archivo.
   - **Mi opinión a solas:** si ya existen las opiniones de los dos padres para ese tema, pregunta `[ Compararlas ahora ] [ Después ]`. Compáralas solo si la persona dice que **los dos ya terminaron**.
   - **Desde `/empezar`:** di "Siguiente: <paso>. ¿Seguimos o lo dejamos para otro día?".

## 6. Editar o borrar (solo si lo pide explícitamente)
- **Editar** ("editar quiénes somos", "cambiar mi decisión de la escuela"):
  1. Lee el archivo de `mis-datos/` y muestra lo que hay por secciones.
  2. Pregunta qué cambiar y pregunta solo eso.
  3. Muestra el antes y el después, y pide `[ Sí, guárdalo ] [ No ]`.
  4. Anota la edición en `progreso.md`.
- **Borrar:**
  1. Pide confirmación dos veces: "¿Seguro que quieres borrar <qué>? No se puede deshacer" y luego `[ Sí, bórralo ] [ No ]`.
  2. Anótalo en `progreso.md`.
  3. **Nunca borres** `mis-datos/juntas/lo-que-decidimos.md` ni líneas de ese archivo: es la memoria de la familia. A ese archivo solo se le agregan líneas.

## Nunca
- Guardar sin confirmación, saltarse preguntas o inventar respuestas.
- Leer `privado/` o mostrar la opinión del otro padre en "mi opinión a solas".
- Escribir fuera de `mis-datos/`.
- Usar palabras técnicas con la persona.

## Ejemplo (EJEMPLO FICTICIO)
```
Persona: /llenar nueva decisión
Claude: Vamos a escribir una decisión nueva. Son unas 10 preguntas y puedes pausar cuando quieras.
        Pregunta 1 de 10. ¿Quién la está llenando?  [ Padre-A ]  [ Padre-B ]
Persona: Padre-A
Claude: Pregunta 2 de 10. ¿Qué tenemos que decidir? Una sola pregunta.
        Ejemplo: "¿Cambiamos a Hijo-1 a una escuela bilingüe en agosto de 2027?"
...
Claude: ✅ Guardado en mis-datos/decisiones/2026-10-12-escuela-hijo1.md
        ¿La reviso ahora?  [ Revisarla ahora ]  [ Después ]
```
