# EJEMPLO FICTICIO — Decisión con límite duro

> Segunda decisión de prueba. Sirve para comprobar que una rama con riesgo de límite duro mayor al 10% no se recomienda.

**ID:** DEC-002 · **Estado:** aprobada

## 1. La pregunta
¿Cambiamos a una póliza con maternidad antes de 2026-12?

## 2. Fecha límite para decidir
2026-11-15

## 3. ¿Quién la lleva?
- Ejecutivo IA: jefe-atencion
- Humano responsable: Padre-B

## 4. Contexto
La póliza actual no cubre maternidad. Hijo-2 está planeado para 2027-H2 con una probabilidad del 60%. Las pólizas nuevas tienen un periodo de espera de unos 10 meses.

## 5. Ramas de la decisión

### Rama 1: Quedarnos con la póliza actual

**¿Qué puede pasar?**
- Embarazo en 2027-H2 sin cobertura · 60% · porque es la probabilidad del plan de Hijo-2 · fuente: perfil-familia · límite duro: sí, LD-02
- Se pospone Hijo-2 · 40% · porque es el resto del plan · fuente: perfil-familia · límite duro: no

**Pros**
- Sin aumento de prima · dinero · 7

**Contras**
- Sin cobertura de maternidad · salud · 2

**Primera acción si la elegimos:** revisar la póliza otra vez en 2027-03.

### Rama 2: Cambiar a póliza con maternidad

**¿Qué puede pasar?**
- Periodo de espera cumplido a tiempo · 90% · porque la espera es de 10 meses y el embarazo se planea en 12 o más · fuente: estimación de Padre-B · límite duro: no
- Embarazo antes de cumplir la espera · 10% · porque hay solo 2 meses de margen · fuente: estimación de Padre-B · límite duro: sí, LD-02

**Pros**
- Cobertura de maternidad · salud · 9
- Tranquilidad para planear a Hijo-2 · seguridad · 8

**Contras**
- Prima una banda más alta · dinero · 4

**Primera acción si la elegimos:** pedir 3 cotizaciones antes de 2026-11-08.

## 6. Lo que todavía no sabemos
- PENDIENTE: ¿el periodo de espera es de 10 o de 12 meses?

---

**Lectura esperada de la IA:**
- Rama 1: nota (7 + 2) ÷ 2 = **4.50** · riesgo de límite 60% → **no recomendable**.
- Rama 2: nota (9 + 8 + 4) ÷ 3 = **7.00** · riesgo de límite 10% → recomendable, con bandera: está justo en el máximo permitido.
