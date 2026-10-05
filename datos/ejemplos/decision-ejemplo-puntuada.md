# EJEMPLO FICTICIO — Salida de la skill `puntuar-decision` para DEC-001

**Entrada:** `datos/ejemplos/decision-ejemplo.md` · **Sin pesos:** todas las notas cuentan igual.

## Veredicto
- **Rama 1 · Quedarnos como estamos** · nota **6.67** · punto más débil 3 · riesgo de límite 0% · recomendable: sí
- **Rama 2 · Cambiar a escuela bilingüe** · nota **6.50** · punto más débil 4 · riesgo de límite 0% · recomendable: sí

## Lectura
La diferencia es de 0.17 puntos: es un **empate técnico** (menos de 0.5). La rama 1 gana en dinero y familia; la rama 2 gana en educación. La Junta debe decidir con valores, no con decimales.

## Cálculo
- Rama 1: (8 + 9 + 3) ÷ 3 = 20 ÷ 3 = **6.67**
  - Por pilar: dinero 8 · familia 9 · educación 3
- Rama 2: (9 + 8 + 4 + 5) ÷ 4 = 26 ÷ 4 = **6.50**
  - Por pilar: educación 8.5 · dinero 4 · familia 5
- Porcentajes: rama 1 = 80 + 20 = 100% ✔ · rama 2 = 60 + 30 + 10 = 100% ✔

## ¿Qué cambiaría el resultado?
- Si la escuela bilingüe tiene transporte escolar (PENDIENTE) y "25 minutos de traslado" sube de 5 a 8, la rama 2 sube a 29 ÷ 4 = **7.25** y gana por 0.58.
- Si "Inglés limitado" se califica con 1 en lugar de 3, la rama 1 baja a 18 ÷ 3 = **6.00** y la rama 2 pasa al frente por 0.50: ya no es empate técnico, pero por muy poco.
- Padre-B estima "Le cuesta un año" en 55% (Padre-A: 30%). No cambia las notas, pero es un desacuerdo de 25 puntos: **discutir en la junta**.

## Banderas
- Ninguna rama rompe un límite duro.
- Punto bajo: "Inglés limitado" (3) en la rama 1.
- PENDIENTE abierto: transporte escolar (afecta el pilar familia de la rama 2).
