---
name: empezar
description: Guía paso a paso de Family Decision Board para personas no técnicas. Revisa qué pasos de EMPIEZA-AQUI.md ya están hechos, salta los pasos de una sola vez ya completados y lleva a la persona al siguiente paso usando /llenar, /revisar y /junta. Úsala con /empezar, "¿qué sigue?", "¿qué hago?", "ayúdame a empezar" o cuando alguien no técnico no sepa qué hacer.
---

# /empezar — Guía paso a paso

La persona **no es técnica**. Usa frases cortas, emojis ✅ ⬜ y botones (herramienta **AskUserQuestion**). Nunca uses palabras técnicas con ella. El texto para personas de cada paso está en `EMPIEZA-AQUI.md`.

## 1. Revisar el avance (sin preguntar nada todavía)
Lee `mis-datos/progreso.md` (puede no existir) y busca estos archivos. **Nunca leas `privado/`.**

| # | Paso | Cómo sé que está hecho | Tipo |
|---|---|---|---|
| 1 | Apagar "Help improve Claude" | `progreso.md` tiene la línea "privacidad de Claude: listo" | una vez |
| 2 | Guardar nombres reales en `privado/` | `progreso.md` tiene la línea "carpeta privada: listo" | una vez |
| 3 | Lo que nunca aceptamos | existe `mis-datos/familia/1-lo-que-nunca-aceptamos.md` | una vez |
| 4 | Dinero en rangos | existe `mis-datos/familia/2-dinero-en-rangos.md` | una vez |
| 5 | Quiénes somos | existe `mis-datos/familia/3-quienes-somos.md` | una vez |
| 6 | Cómo estamos hoy | existe `mis-datos/familia/4-como-estamos-hoy.md` | una vez |
| 7 | Fechas importantes | existe `mis-datos/familia/5-fechas-importantes.md` | una vez |

Pasos que se repiten (solo después del 7):
- **Nueva decisión:** cada vez que la pidan.
- **Notas de la junta:** si hoy es domingo, o si la última `mis-datos/juntas/notas-*.md` tiene más de 7 días.
- **Cómo nos sentimos:** si no existe `mis-datos/juntas/como-nos-sentimos-<AAAA-MM del mes actual>.md`.
- **Respaldo:** si `progreso.md` no tiene "respaldo: AAAA-MM-DD" de los últimos 30 días.

**Archivos sueltos de antes:** si hay archivos llenos directamente en `mis-datos/` (por ejemplo `mis-datos/2-dinero-en-rangos.md` o `mis-datos/nueva-decision.md`), di que encontraste algo que ya habían empezado. Pregunta `[ Acomodarlo en su lugar ] [ Dejarlo así ]`. Si dicen que sí, muévelo a la carpeta correcta. Si su formato es viejo, ofrece `/llenar editar` para pasarlo al formato nuevo.

## 2. Saludar y mostrar la lista
- Primera vez (nada hecho): "¡Hola! Te voy a guiar paso a paso. No necesitas saber nada técnico." Luego la lista con ⬜.
- Otras veces: "¡Qué bueno verte! Ya tienen ✅ …. Faltan: ⬜ …".
- Muestra solo los pasos de una vez que falten y, si ya están todos, la lista de pasos que se repiten.

## 3. Llevar al siguiente paso
Propón **un solo** siguiente paso y pregunta `[ Sí, vamos ] [ Otro día ]`.

- **Paso 1 (privacidad de Claude):**
  1. Explica en 3 líneas: "En el navegador, entra a claude.ai → Settings → Privacy y apaga 'Help improve Claude'. Así lo que escribas de tu familia no se usa para entrenar a la IA."
  2. Pregunta `[ Ya lo apagué ] [ Ahora no ]`.
  3. Si ya lo apagó, agrega a `progreso.md`: `- AAAA-MM-DD — privacidad de Claude: listo`.
- **Paso 2 (carpeta privada):** este paso **lo hace la persona sola; tú nunca ves ese contenido**.
  1. Explica: "Abre la carpeta `privado/` en tu computadora. Crea un archivo de texto llamado `quien-es-quien.md` y escribe ahí quién es Padre-A, Padre-B, Hijo-1… Ahí también pueden ir las cantidades exactas de dinero. Yo no puedo leer esa carpeta, y está bien así."
  2. Pregunta `[ Ya lo hice ] [ Lo hago después ]`.
  3. Si ya lo hizo, agrega a `progreso.md`: `- AAAA-MM-DD — carpeta privada: listo`.
- **Pasos 3 a 7:** di en una frase para qué sirve el paso y sigue las instrucciones de `/llenar` (`.claude/skills/llenar/SKILL.md`) con el archivo que corresponde. Al terminar, regresa aquí y propón el siguiente.
- **Cuando ya están todos los de una vez**, pregunta con AskUserQuestion qué quieren hacer:
  - `Nueva decisión` → `/llenar nueva decisión`
  - `Junta del domingo` → `/junta`
  - `Cómo nos sentimos (falta <mes>)` → solo aparece si falta → `/llenar cómo nos sentimos`
  - `Editar algo que ya llenamos` → pregunta qué y usa `/llenar editar …`
  - Si la persona escribe "mi opinión a solas", "revisar" o "fechas", usa `/llenar` o `/revisar` según corresponda.
- **Respaldo (una vez al mes):** si toca, al final de la sesión di:
  1. "💾 Sus datos solo viven en esta computadora. Una vez al mes conviene copiar la carpeta `mis-datos/` a una USB o a una carpeta cifrada."
  2. Pregunta `[ Ya lo copié ] [ Recuérdamelo después ]`.
  3. Si ya la copió, agrega a `progreso.md`: `- AAAA-MM-DD — respaldo: listo`.
  4. Tú no haces la copia: la hace la persona.

## 4. Repetir solo si lo piden
- Un paso de una vez que ya está hecho **no se vuelve a hacer**.
- Solo se edita o se borra si la persona lo pide con palabras claras ("editar…", "cambiar…", "borrar…"). En ese caso usa la sección "Editar o borrar" de `/llenar`.

## 5. Cerrar
Termina siempre con una línea: "Siguiente vez: <paso>. Solo escribe /empezar."

## Nunca
- Leer `privado/` ni pedir que te dicten lo que va ahí.
- Hacer dos pasos a la vez o saltarte la confirmación.
- Repetir un paso de una vez sin que lo pidan.
- Usar palabras técnicas con la persona.

## Ejemplo (EJEMPLO FICTICIO)
```
Persona: /empezar
Claude: ¡Qué bueno verte! Así van:
          ✅ 1. Privacidad de Claude   ✅ 2. Carpeta privada
          ✅ 3. Lo que nunca aceptamos ✅ 4. Dinero en rangos
          ⬜ 5. Quiénes somos          ⬜ 6. Cómo estamos hoy
          ⬜ 7. Fechas importantes
        Sigue el 5: "Quiénes somos". Son preguntas sencillas sobre la familia, unos 10 minutos.
        [ Sí, vamos ]  [ Otro día ]
```
