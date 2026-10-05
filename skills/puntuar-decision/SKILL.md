---
name: puntuar-decision
description: Calcula la nota de cada rama (promedio de notas 1–10 de sus pros y contras), el punto más débil y el riesgo de límite duro de una decisión de Family Decision Board escrita en Markdown. Úsala cuando pidan "puntúa", "califica las ramas", "¿qué opción conviene?" o antes de una junta.
---

# Puntuar decisión

## Entrada
- Una decisión en Markdown (`decision-*.md`) en estado `corregida` o `aprobada`.
- Los límites duros llenos (`limites-duros`).
- Si existen, las estimaciones individuales de cada padre.

## Pasos
1. Revisa que cada nota esté entre 1 y 10 y que los porcentajes de cada rama sumen 100%. Si no, **detente** y repórtalo.
2. Nota de la rama = **promedio simple** de todas las notas de sus pros y contras. No hay pesos.
3. Nota por pilar = promedio de los puntos de ese pilar en la rama.
4. Punto más débil = la nota más baja de la rama.
5. Riesgo de límite duro = suma de los porcentajes de los resultados con "límite duro: sí".
6. Marca como "No recomendable" toda rama con riesgo mayor al 10%.
7. Si la diferencia entre las dos mejores ramas es menor a 0.5, declara **empate técnico** y explica qué nota o qué PENDIENTE lo rompería.
8. Muestra el cálculo paso a paso. Usa una herramienta de código si está disponible para no errar en la aritmética.

## Salida (formato fijo, en listas, sin tablas)
Secciones: **Veredicto** · **Lectura** (≤ 3 frases) · **Cálculo** · **¿Qué cambiaría el resultado?** · **Banderas**.

Formato de cada línea del veredicto:
`- Rama N · <nombre> · nota X.XX · punto más débil N · riesgo de límite N% · recomendable: sí/no`

## Nunca
- Decir "deben elegir X". Di: "La rama con mejor nota sin romper límites es X".
- Esconder un empate técnico.
- Pedir pesos ni crear tablas de puntuación.

## Ejemplo
**Entrada:** `datos/ejemplos/decision-ejemplo.md`.
**Salida esperada:** `datos/ejemplos/decision-ejemplo-puntuada.md` (rama 1: 6.67 vs rama 2: 6.50 → empate técnico).
