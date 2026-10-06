# Frases para Claude

Escribe el comando o copia la frase en la terminal de Claude. Cambia lo que está entre [corchetes].

## Los comandos (lo que más vas a usar)
- `/empezar` — "¿Qué sigue?". Te lleva paso a paso.
- `/llenar nueva decisión` — escribe una decisión nueva contestando preguntas.
- `/llenar mi opinión a solas` — tu opinión sobre una decisión, sin ver la del otro padre.
- `/llenar cómo nos sentimos` — la encuesta del mes.
- `/llenar editar [quiénes somos]` — cambia algo que ya llenaron.
- `/llenar borrar [la decisión del auto]` — borra algo (te pide confirmar dos veces).
- `/revisar` — revisa una decisión y te dice cómo sale cada camino.
- `/junta` — prepara la junta del domingo y guarda lo que decidieron.

## Mientras contestas
- "No sé." → Claude lo anota como pendiente y sigue.
- "Dame un ejemplo." → te muestra uno.
- "Lo dejo aquí." → guarda tu avance para seguir otro día.
- "Regresa a la pregunta anterior." → la puedes cambiar.

## Para entender
- "Explícame este resultado con palabras sencillas."
- "¿Por qué dices que es un empate?"
- "Según cómo estamos hoy, ¿qué decisión conviene abrir primero?"
- "¿Qué fechas importantes vencen en las próximas 4 semanas?"

## Si algo se ve técnico o raro
- "Esto se ve técnico. Explícamelo como si no supiera nada de computadoras."
- Si aparece una ventana pidiendo permiso y no entiendes qué pide, elige **No** y avísale al Arquitecto.
- Si Claude te habla de JSON, specs, skills o subagentes, **no tienes que entenderlo**. Avísale al Arquitecto.

---

## EJEMPLO FICTICIO
```
Padre-A: /revisar
Claude:  ¿Cuál decisión reviso?  [ ¿Cambiamos a Hijo-1 a la escuela bilingüe? ]
Padre-A: (elige la escuela)
Claude:  Revisé tu decisión y la llamé DEC-001. La vigila el encargado de educación junto con Padre-A.
         Hay que arreglar 1 cosa: en el camino 2, "¿Qué podría pasar?" suma 9 y debe sumar 10.
         Cuando lo arregles: camino 1 = 6.7, camino 2 = 6.5. Es casi un empate.
         [ Arreglar lo que falta ahora ]  [ Después ]
```
