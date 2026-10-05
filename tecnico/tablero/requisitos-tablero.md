# Requisitos del tablero (contrato para Claude)

**Spec:** `tecnico/specs/002-tablero-decisiones/spec.md` · **Versión:** 2.0 (ADR-001, propuesto) · **Fecha:** 2026-10-05

## Principio
El tablero **muestra**, no captura. Los humanos escriben listas en Markdown. Al final, el subagente `generador-json` produce el JSON que lee el tablero (contrato v2.0 dentro de `tecnico/subagentes/generador-json.md`). Ningún humano edita JSON.

## Requisitos
- **RT-01 (Debe)** Cargar datos pegando el JSON generado en un área de texto (botón "Cargar"). Abrir con los ejemplos precargados y marcados "EJEMPLO FICTICIO".
- **RT-02 (Debe)** **Árbol** por decisión: pregunta → ramas → resultados, con el porcentaje en cada resultado y la nota (1–10) en cada rama.
- **RT-03 (Debe)** **Veredicto** por rama: nota, punto más débil y riesgo de límite. Resaltar la mejor rama sin riesgo mayor al 10%. Mostrar "empate técnico" si la diferencia es menor a 0.5.
- **RT-04 (Debe)** **Pros y contras de cada rama** como lista con su nota, y la nota por pilar en barras del 1 al 10 con una línea en 6 (aprobado).
- **RT-05 (Debe)** **Pros y contras de la vida actual**, con la nota por pilar y el pilar más débil resaltado.
- **RT-06 (Debe)** **Estado** de cada decisión como etiqueta. Las que no están `aprobada` o posterior aparecen como "No apta para votar".
- **RT-07 (Debería)** **Fechas límite**: lista ordenada con las próximas 4 semanas resaltadas.
- **RT-08 (Debería)** **¿Y si…?**: permitir mover la nota de un punto y ver cómo cambia la nota de la rama en vivo, sin guardar.
- **RT-09 (Podría)** **Bitácora**: muestra las decisiones votadas y su criterio de salida.
- **RT-10 (Debe)** **Privacidad**: sin `localStorage`, sin red, sin conectores ni capacidades de servidor.
- **RT-11 (Debe)** Español en toda la interfaz; formato de fecha AAAA-MM-DD.
- **RT-12 (Debe)** Funciona en un teléfono de 400 px y en tema claro y oscuro.

## Cálculos (deben coincidir con `tecnico/docs/03-metodo-probabilistico.md`)
- `nota de la rama = promedio simple de las notas de pros y contras`
- `nota por pilar = promedio de los puntos de ese pilar`
- `punto más débil = nota mínima` · `riesgo = suma de probabilidades con rompe_limite`

## Prueba de aceptación
Con el JSON generado a partir de `decisiones/ejemplos/`:
- DEC-001 muestra rama 1 = 6.67 y rama 2 = 6.50 (empate técnico).
- DEC-002 muestra rama 1 con riesgo de límite del 60%, marcada como no recomendable, y rama 2 = 7.00 con riesgo del 10% y bandera "justo en el máximo".

## Ejemplo de vista esperada (texto)
```
DEC-001 · aprobada · fecha límite 2027-01-31
¿Cambiamos a Hijo-1 a una escuela bilingüe en 2027-08?
  ├─ Quedarnos como estamos ........ nota 6.67 · más débil 3 · riesgo 0%
  │    ├─ 80% Sigue igual de bien
  │    └─ 20% Rezago en inglés
  └─ Escuela bilingüe .............. nota 6.50 · más débil 4 · riesgo 0%
       ├─ 60% Se adapta bien
       ├─ 30% Le cuesta un año
       └─ 10% No es admitido
Veredicto: empate técnico (diferencia 0.17). Se decide por valores.
```
