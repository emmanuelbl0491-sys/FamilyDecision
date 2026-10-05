# 03 — Método probabilístico (notas del 1 al 10)

**Propósito:** que cada decisión se compare con la misma regla, sin tablas ni pesos.
**Dueño:** CFO (rol) + Arquitecto · **Última revisión:** 2026-10-05 · **Cambio:** ADR-001 (propuesto)

## La idea en una frase
Cada **rama** (opción) de la decisión tiene una lista de pros y contras. Cada punto lleva una **nota del 1 al 10**. La IA saca el promedio. Los humanos solo escriben listas.

## La escala de notas
- **1** = muy malo (reprobado al máximo)
- **2–3** = malo
- **4–5** = regular, no alcanza (reprobado)
- **6** = apenas aprobado
- **7–8** = bien, muy bien
- **9** = excelente
- **10** = más que excelente

Regla práctica: un **pro** suele llevar de 6 a 10 y un **contra** de 1 a 5.

## Los 6 pasos (lo que hacen los humanos)
1. **Pregunta:** una frase y una fecha límite.
2. **Ramas:** de 2 a 4. La primera siempre es "Quedarnos como estamos".
3. **Qué puede pasar:** de 2 a 4 resultados por rama, cada uno con su porcentaje. Los porcentajes de una rama suman 100%.
4. **Pros y contras:** una lista por rama. Formato: `- qué · pilar · nota`.
5. **La IA calcula** (ver abajo). Los humanos no hacen cuentas.
6. **Decidir y fechar:** dueño, fecha de revisión y criterio de salida.

Formato de cada línea:
```
- Mudanza a ciudad natal · dinero · 10
- Se adapta bien · 60% · porque la mayoría se adapta en un semestre · fuente: plática con la escuela · límite duro: no
```

## Los 5 pilares (escríbelos con palabras sencillas)
- **dinero** (riqueza): ingresos, ahorro, vivienda, auto, gastos
- **salud**: física y mental, seguro médico, embarazo
- **familia** (tiempo en familia): presencia con los hijos, traslados, horas de trabajo
- **educación**: escuela de los hijos, carrera de los padres
- **seguridad**: tranquilidad, estatus legal, poder dar marcha atrás

Si escribes otra palabra ("financieramente", "el trabajo", "la casa"), la IA la acomoda en el pilar más cercano y te lo dice en su informe.

## Lo que calcula la IA
- **Nota de la rama** = promedio simple de todas las notas de sus pros y contras.
- **Nota por pilar** = promedio de los puntos de ese pilar dentro de la rama.
- **Punto más débil** = la nota más baja de la rama.
- **Riesgo de límite duro** = suma de los porcentajes de los resultados marcados "límite duro: sí".

No hay pesos. Si un pilar les importa más, escriban más puntos sobre ese pilar o díganlo en la junta.

## Reglas de decisión
- **Límite duro:** si el riesgo es mayor al 10%, la rama **no puede ser recomendada**.
- **Empate técnico:** si dos ramas están a menos de **0.5** puntos, la IA lo dice y la Junta decide por valores.
- **Rama reprobada:** nota de la rama menor a 6 → bandera "¿por qué la seguimos considerando?".
- **Punto muy malo:** cualquier nota de 1 o 2 → bandera "¿podemos vivir con esto 12 meses?".
- **Porcentajes:** si una rama no suma 100% → **BLOQUEANTE** en la revisión.
- **Nota fuera de rango:** si no está entre 1 y 10 → **BLOQUEANTE**.
- **Desacuerdo entre padres:** diferencia mayor a 20 puntos en un porcentaje, o mayor a 3 en una nota → se discute antes de aprobar.

## Límites duros por defecto (la Junta puede editarlos en `datos/plantillas/limites-duros.plantilla.md`)
- Colchón de emergencia menor a 3 meses.
- Embarazo sin cobertura médica.
- Pagos de deuda mayores al 35% del ingreso.

## Cómo obtener porcentajes honestos
1. Empieza por una **tasa base** (estadística oficial, promedio del mercado) y anota la fuente.
2. Ajusta con la situación propia y **escribe el porqué**.
3. Cada padre estima **a solas**; la IA compara y marca diferencias mayores a 20 puntos.

## Ejemplo calculado (EJEMPLO FICTICIO)
**Rama 2:** "Cambiar a Hijo-1 a escuela bilingüe en 2027-08"

Pros:
- Bilingüe desde primaria · educación · 9
- Más opciones de escuela y universidad a futuro · educación · 8

Contras:
- Una banda más de gasto mensual · dinero · 4
- 25 minutos de traslado · familia · 5

Cálculo de la IA:
- Nota de la rama = (9 + 8 + 4 + 5) ÷ 4 = 26 ÷ 4 = **6.50**
- Por pilar: educación 8.5 · dinero 4 · familia 5
- Punto más débil: "Una banda más de gasto mensual" (4)
- Riesgo de límite duro: 0%

> Error intencional para el ejercicio: un resumen viejo dice "nota 6.75". El `revisor-decisiones` debe detectar que 26 ÷ 4 = **6.50**.
