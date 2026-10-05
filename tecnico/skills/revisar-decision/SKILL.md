---
name: revisar-decision
description: Cadena completa para revisar una decisión que escribió la familia en palabras sencillas. Revisa privacidad, pule la redacción, asigna números, pilares y quién lo cuida, busca errores, califica cada camino y responde en lenguaje simple. Úsala cuando digan "Revisa mi decisión", "revisa esto" o entreguen un archivo de mis-datos/ basado en decisiones/nueva-decision.md.
---

# Revisar decisión (para la familia)

## Entrada
- Una decisión basada en `decisiones/nueva-decision.md`, normalmente en `mis-datos/`.
- `familia/1-lo-que-nunca-aceptamos.md` lleno (la copia en `mis-datos/`, si existe).
- Opcional: las copias de `decisiones/mi-opinion-a-solas.md` de cada padre.

## Pasos (en este orden)
1. **Privacidad:** aplica `tecnico/subagentes/auditor-privacidad.md`. Si el veredicto es DETENIDO, **detente**. Di en palabras simples qué tipo de dato hay que borrar y en qué línea, sin repetirlo.
2. **Redacción:** aplica `tecnico/subagentes/revisor-gramatical.md` en modo "pulir ideas". Ordena y aclara las frases sin cambiar el sentido, los números ni las calificaciones. Si una idea mezcla dos cosas, sepárala y avísalo.
3. **Organizar (lo asigna la IA):** sigue las reglas de "Lo que asigna la IA" de `tecnico/docs/03-metodo-probabilistico.md`.
   - Número: DEC-NNN (el siguiente libre según `juntas/lo-que-decidimos.md` y `mis-datos/`).
   - Pilar de cada idea.
   - Ejecutivo que la vigila.
   - Humano responsable (quien la llenó).
   - Límites duros que podrían romperse.
   - Fechas relacionadas.
4. **Errores:** aplica `tecnico/subagentes/revisor-decisiones.md`.
5. **Calificación:** si no hay nada que "hay que arreglar", aplica `tecnico/skills/puntuar-decision/SKILL.md`.
6. **Respuesta para la familia:** usa el formato de abajo. Guarda el informe técnico de los pasos 1 a 5 para el Arquitecto, pero **no lo muestres** a la familia salvo que lo pida.

## Salida para la familia (formato fijo, palabras simples)
```
Revisé tu decisión: "<pregunta>".
Le puse el número <DEC-NNN>. La vigila <ejecutivo, en palabras: "el encargado de dinero"> junto con <Padre-X>.
(Si quieren cambiar esto, díganmelo).

Hay que arreglar (<n>):
- <qué y dónde, en una frase>
Conviene revisar (<n>):
- <…>

Cómo sale cada camino:
- Camino 1, <nombre>: <x.x> de 10. Su punto más bajo: "<idea>" (<n>).
- Camino 2, …
<"Casi empate" | "Gana el camino N" | "El camino N no se recomienda porque <n> de cada 10 veces terminaría en <límite>">

Falta saber:
- <…>
```
Equivalencias para la familia:
- BLOQUEANTE → "Hay que arreglar"
- IMPORTANTE → "Conviene revisar"
- SUGERENCIA → "Una idea"
- PENDIENTE → "Falta saber"

## Nunca
- Cambiar el sentido de lo que escribió la familia ni sus números.
- Usar con la familia palabras como JSON, skill, subagente, spec, ID, pilar o BLOQUEANTE.
- Decir "deben elegir X". Di: "el camino con mejor calificación, sin riesgos graves, es X".
- Marcar la decisión como aprobada.

## Ejemplo
**Entrada:** `decisiones/ejemplos/escuela.md`.
**Salida esperada:** número DEC-001; la vigila el encargado de educación (vp-producto) junto con Padre-A; nada que arreglar; camino 1 = 6.7, camino 2 = 6.5, casi empate; falta saber si hay transporte escolar. El detalle está en `decisiones/ejemplos/escuela-resultado.md`.
