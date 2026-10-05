# ADR-001 — Listas con notas del 1 al 10, sin pesos y sin JSON escrito por humanos
Fecha: 2026-10-05 · Estado: **propuesto** · Autor: Claude, a pedido del Arquitecto
Firmas requeridas: Arquitecto + Junta (toca la constitución, artículos 2.2, 2.3, 4.2, 4.3, 4.4 y 6.2)

- Arquitecto (Padre-A): Aprovado · Fecha: 2026-10-05
- Junta (Padre-B): Aprovado · Fecha: 2026-10-05

## Contexto
Las plantillas eran difíciles para humanos, en especial para un Vibe Coder:
- Había archivos JSON que se esperaba que los humanos revisaran o mantuvieran.
- Había tablas de 5 a 11 columnas con puntajes de 0 a 10 por pilar y una tabla de pesos que debía sumar 100%.
- Las cuentas (valor ponderado × probabilidad) no se podían verificar a ojo.

## Decisión
1. **Sin JSON para humanos.** Se borran los esquemas y los JSON de ejemplo. El subagente nuevo `generador-json` produce el JSON del tablero **al final** (F7), a partir del Markdown aprobado.
2. **Sin pesos ni tablas de puntuación.** Se borra `pesos-pilares.plantilla.md` y las tablas de puntaje por pilar.
3. **Listas con notas del 1 al 10.** Cada rama tiene pros y contras con este formato: `- qué · pilar · nota`. Escala: 1 = muy malo (reprobado al máximo), 6 = apenas aprobado, 10 = más que excelente.
4. **Nota de la rama = promedio simple.** Empate técnico si la diferencia es menor a 0.5.
5. **Se mantienen** los porcentajes de los resultados (suman 100% por rama) y la regla del límite duro (riesgo mayor al 10% = no recomendable).
6. Todas las plantillas que llenan humanos en `familia/ y decisiones/` pasan de tablas a listas.

## Alternativas consideradas
- **Mantener pesos, pero en lista.** Pro: conserva prioridades. Contra: sigue pidiendo que sumen 100%, y esa es la parte difícil.
- **Nota también en cada resultado (valor esperado sin pesos).** Pro: une porcentajes y notas. Contra: duplica el trabajo humano. Se puede agregar después con otro ADR.
- **Promedio simple, sin pesos (elegida).** Pro: cualquiera lo entiende y lo verifica a mano. Contra: todos los pilares valen igual; la Junta compensa escribiendo más puntos sobre lo que le importa.

## Consecuencias
- Archivos borrados (hay respaldo en `../family-decision-board-respaldo-2026-10-05.tar.gz`): `datos/esquemas/*.json`, `decisiones/ejemplos/decision-ejemplo.json`, `tecnico/tablero/entrada-ejemplo.json`, `tecnico/tablero/entrada.schema.md`, `familia/ y decisiones/pesos-pilares.plantilla.md` y `tecnico/skills/capturar-decision/`.
- Archivos nuevos: `tecnico/subagentes/generador-json.md`, `decisiones/ejemplos/seguro-medico.md` y este ADR.
- Archivos reescritos: el método (`tecnico/docs/03`), todas las plantillas de `familia/ y decisiones/`, los ejemplos, `puntuar-decision`, `revisor-decisiones`, los requisitos del tablero y las specs 001 y 002.
- El estado `capturada` desaparece: la decisión pasa de `borrador` a `en_revision`.
- **Cómo se revierte:** descomprimir el respaldo sobre la carpeta del proyecto.
- PENDIENTE: ¿la Junta quiere un mínimo de puntos por pilar (por ejemplo, al menos 1 por pilar afectado) para compensar que no hay pesos? Si
    