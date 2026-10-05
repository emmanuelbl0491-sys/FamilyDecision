# 03 — Método probabilístico (calificaciones del 1 al 10)

**Propósito:** que cada decisión se compare con la misma regla, sin tablas ni pesos.
**Dueño:** CFO (rol) + Arquitecto · **Última revisión:** 2026-10-05 · **Cambios:** ADR-001 (firmado) y ADR-002 (propuesto)

## La idea en una frase
Cada **camino** (rama u opción) tiene una lista de lo bueno y lo malo. Cada idea lleva una **calificación del 1 al 10**. La IA asigna el pilar de cada idea y saca el promedio.

## Lo que escriben los humanos (`decisiones/nueva-decision.md`)
```
**¿Qué podría pasar?**
- Se adapta bien: 6 de 10 veces. Porque la escuela nos dijo que casi todos se adaptan.
**Lo bueno de este camino**
- Bilingüe desde primaria — 9
**Lo malo de este camino**
- 25 minutos de camino a la escuela — 5
```
El formato es libre. `revisor-gramatical` lo pule y la etapa de organización de `revisar-decision` lo convierte a la forma interna.

## La escala
- **1** = muy malo (reprobado al máximo)
- **2–3** = malo
- **4–5** = regular, no alcanza
- **6** = apenas aprobado
- **7–8** = bien, muy bien
- **9** = excelente
- **10** = más que excelente

Lo bueno suele llevar de 6 a 10 y lo malo de 1 a 5.

## Lo que asigna la IA
- **Número:** DEC-NNN para decisiones, LD-NN para límites duros y R-NN para caminos (en lo técnico se llaman "ramas").
- **Pilar de cada idea:**
  - `riqueza`: dinero, gastos, casa, auto
  - `salud`: física y mental, seguro, embarazo
  - `tiempo_familia`: tiempo juntos, traslados, horas de trabajo
  - `educacion`: escuela, carrera
  - `seguridad`: tranquilidad, estatus legal, poder dar marcha atrás
- **Quién lo cuida (ejecutivo):**
  - `cfo`: dinero, deudas, ahorros
  - `jefe-atencion`: salud, seguro, embarazo
  - `vp-producto`: escuela e hijos
  - `coo`: casa, auto, trámites y fechas
  - `ceo`: mudanza, ciudad o temas de varios pilares
- **Humano responsable:** quien llenó el archivo ("Lo llenó"), salvo que la Junta diga otra cosa.
- **Límite duro roto:** la IA compara cada cosa que podría pasar con `familia/1-lo-que-nunca-aceptamos.md` y la marca. Siempre lo reporta para que la familia lo confirme.

## Lo que calcula la IA
- **Probabilidad** = n ÷ 10. Por ejemplo, "6 de 10" = 0.6.
- **Nota del camino** = promedio simple de todas las calificaciones de lo bueno y lo malo.
- **Nota por pilar** = promedio de las ideas de ese pilar dentro del camino.
- **Punto más débil** = la calificación más baja del camino.
- **Riesgo de límite duro** = suma de las probabilidades de lo que rompe un límite.

## Reglas de decisión
- **Límite duro:** si el riesgo es mayor a 1 de 10 (más del 10%), el camino **no puede ser recomendado**.
- **Empate técnico:** si dos caminos están a menos de **0.5** puntos.
- **Camino reprobado:** si la nota del camino es menor a 6, bandera.
- **Punto muy malo:** cualquier calificación de 1 o 2, bandera "¿podemos vivir con esto 12 meses?".
- **"De cada 10" que no suma 10:** BLOQUEANTE en la revisión.
- **Calificación fuera de 1–10:** BLOQUEANTE.
- **Desacuerdo entre padres:** diferencia de 2 o más (de 10) en lo que podría pasar, o de más de 3 en una calificación. Se platica en la junta.

## Límites duros por defecto (la Junta puede editarlos en `familia/1-lo-que-nunca-aceptamos.md`)
- Colchón de emergencia menor a 3 meses.
- Embarazo sin cobertura médica.
- Pagos de deuda mayores al 35% del ingreso.

## Cómo obtener estimaciones honestas
1. Empieza por una **tasa base** (estadística oficial, promedio del mercado) y anota la fuente.
2. Ajusta con la situación propia y **escribe el porqué**.
3. Cada padre estima **a solas** (`decisiones/mi-opinion-a-solas.md`) y la IA compara.

## Ejemplo calculado (EJEMPLO FICTICIO)
**Camino 2:** "Cambiar a la escuela bilingüe" (`decisiones/ejemplos/escuela.md`)
- Lo bueno: Bilingüe desde primaria — 9 (educacion) · Más opciones en el futuro — 8 (educacion)
- Lo malo: Gastamos un rango más cada mes — 4 (riqueza) · 25 minutos de camino — 5 (tiempo_familia)
- **Nota del camino** = (9 + 8 + 4 + 5) ÷ 4 = 26 ÷ 4 = **6.50**
- **Por pilar:** educacion 8.5 · riqueza 4 · tiempo_familia 5
- **Riesgo de límite:** 0

> Error intencional para el ejercicio: un resumen viejo dice "nota 6.75". El `revisor-decisiones` debe detectar que 26 ÷ 4 = **6.50**.
