---
name: puntuar-decision
description: Calcula la nota de cada camino (promedio de las calificaciones del 1 al 10 de lo bueno y lo malo), el punto más débil y el riesgo de límite duro de una decisión de Family Decision Board ya revisada. Es el paso 5 de revisar-decision. También se usa sola cuando piden "califica los caminos" o "¿qué camino conviene?".
---

# Puntuar decisión

## Entrada
- Una decisión ya organizada por `revisar-decision` (con pilares y límites asignados), sin nada pendiente de "hay que arreglar".
- `familia/1-lo-que-nunca-aceptamos.md` lleno.
- Si existen, las copias de `decisiones/mi-opinion-a-solas.md`.

## Pasos
1. Revisa que cada calificación esté entre 1 y 10 y que cada camino sume 10 de 10. Si no, **detente** y repórtalo.
2. Nota del camino = **promedio simple** de todas las calificaciones de lo bueno y lo malo. No hay pesos.
3. Nota por pilar = promedio de las ideas de ese pilar en el camino.
4. Punto más débil = la calificación más baja del camino.
5. Riesgo de límite duro = suma de "de cada 10" de lo que rompe un límite.
6. Si el riesgo es mayor a 1 de 10, el camino es "No recomendable".
7. Si la diferencia entre los dos mejores caminos es menor a 0.5, declara **empate técnico** y explica qué calificación o qué "falta saber" lo rompería.
8. Compara las opiniones a solas, si existen: marca diferencias de 2 o más de 10, o de más de 3 en una calificación.
9. Muestra las cuentas paso a paso. Usa una herramienta de código si está disponible para no errar en la aritmética.

## Salida (formato fijo, en listas, sin tablas)
Secciones:
- **En una frase**
- **Calificación de cada camino**
- **Por qué salen así**
- **¿Qué podría cambiar el resultado?**
- **Lo que falta**
- **Cuentas**

Redáctala para la familia, con palabras simples: muestra 1 decimal y deja 2 decimales solo en "Cuentas".

## Nunca
- Decir "deben elegir X". Di: "el camino con mejor calificación, sin riesgos graves, es X".
- Esconder un empate técnico.
- Pedir pesos ni crear tablas de puntuación.

## Ejemplo
**Entrada:** `decisiones/ejemplos/escuela.md`.
**Salida esperada:** `decisiones/ejemplos/escuela-resultado.md` (camino 1: 6.67 contra camino 2: 6.50, casi empate).
