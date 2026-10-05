# 04 — Family Inc.: roles ejecutivos

**Propósito:** asignar a cada dominio un ejecutivo IA que recomienda y un humano que responde.
**Dueño:** Junta · **Última revisión:** 2026-10-05

## Regla principal
La **Junta** (Padre-A, Padre-B) toma las decisiones finales. Cada ejecutivo es una **skill** con una misión, una entrada y una salida. Cada ejecutivo tiene además un **humano responsable** que lee y firma su salida.

| Rol | Skill | Misión | Dominios | Salida semanal | Nunca hace |
|---|---|---|---|---|---|
| CEO | `ceo` | Estrategia y balance entre pilares | Migración, ubicación, ranking final | Memo de decisión con la nota de cada rama | Decidir solo u omitir "quedarse igual" |
| COO | `coo` | Convertir decisiones en acciones fechadas | Transporte, vivienda, fechas límite | Lista maestra de fechas + acciones de 7 días | Cambiar probabilidades |
| CFO | `cfo` | La verdad del dinero y los límites de riesgo | Ingresos, patrimonio, inversiones, presupuesto | Flujo de caja bajo/probable/alto, meses de colchón | Recomendar inversiones específicas |
| VP de Producto | `vp-producto` | El "producto" es el bienestar de cada integrante | Educación, desarrollo de los hijos, nuevos integrantes | Hoja de ruta por hijo | Planear sin escuchar a los hijos |
| Jefe de Atención | `jefe-atencion` | Salud, cuidado y experiencia de la familia | Seguro médico, embarazo, carga mental | Brechas de cobertura + pulso de satisfacción | Dar diagnósticos médicos |

## Ritmo de operación
| Cuándo | Duración | Qué pasa | Plantilla |
|---|---|---|---|
| Domingo | 30 min | Junta: memo CEO, números CFO, se vota una decisión | `juntas/notas-de-la-junta.md` |
| Miércoles | 10 min | Revisión de acciones (COO) | `juntas/notas-de-la-junta.md` (sección 4) |
| Mensual | 15 min | Pulso de satisfacción (1–10) de cada integrante | `juntas/como-nos-sentimos.md` |

## Escalamiento
Cualquier ejecutivo puede marcar una decisión en **ROJO** si un límite duro está en riesgo. Los temas en rojo se tratan primero en la siguiente junta.

## Ejemplo (EJEMPLO FICTICIO)
Domingo 2026-10-11: el CFO marca en ROJO "Seguro sin cobertura de maternidad" porque la Junta planea a Hijo-2 en 2027-H2. La junta lo trata primero. El Jefe de Atención entrega 3 opciones de póliza y el COO fija la fecha 2026-11-15 para elegir.
