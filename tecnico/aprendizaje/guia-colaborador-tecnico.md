# Guía del colaborador técnico: trabajar con IA a su máximo potencial

> **Nota (ADR-002):** el colaborador técnico de este proyecto **no es técnico** y no usa esta guía; su entrada es `EMPIEZA-AQUI.md`. Esta guía es para el Arquitecto o para futuros colaboradores técnicos que reciban tarjetas.

**Para:** personas que construyen con Claude bajo la guía del Arquitecto. **Tiempo de lectura:** 15 min.

## 1. Lo que cambia cuando trabajas con IA
| Antes (sin IA) | Ahora (con IA) |
|---|---|
| Escribir es lo caro | **Especificar y verificar** es lo caro |
| El error típico es no saber hacerlo | El error típico es **hacer algo que nadie pidió** |
| Revisas tu propio trabajo | Una **IA independiente** revisa y un **humano** aprueba |
| El contexto está en tu cabeza | El contexto debe estar **escrito** (la IA no lo adivina) |

## 2. Los 8 principios
1. **Contexto explícito.** La IA solo sabe lo que le das. Pega la tarjeta completa.
2. **Alcance cerrado.** Haz lo de la tarjeta y nada más. Las ideas extra van a una nota para el Arquitecto.
3. **Plan antes de código.** Pide 3 viñetas de plan y apruébalas antes de que la IA escriba.
4. **Verificar en vez de confiar.** Compara contra el resultado esperado (`decisiones/ejemplos/`). Si hay números, que la IA los calcule con código.
5. **Revisión independiente.** Un subagente que no vio el trabajo encuentra lo que tú y tu IA dejaron pasar.
6. **Privacidad por diseño.** Solo datos ficticios. Si dudas de un dato, no lo uses.
7. **Iterar en pasos pequeños.** Una tarjeta ≤ 2 h. Si crece, se divide.
8. **Dejar rastro.** Registra lo que se revisó y por qué se aprobó o rechazó.

## 3. Tu flujo con una tarjeta
```
1. Lee la tarjeta y pregunta tus dudas al Arquitecto (no a la IA)
2. Abre una conversación nueva y pega la tarjeta y el contexto técnico que te dé el Arquitecto
3. Pide el plan (3 viñetas) y apruébalo
4. Deja que Claude escriba; tú lees cada archivo
5. Verifica cada TERMINADO CUANDO con evidencia
6. Ejecuta revisor-entregable → auditor-privacidad → revisor-gramatical
7. Corrige lo BLOQUEANTE e IMPORTANTE
8. Entrega al Arquitecto con la bitácora de revisiones
```

## 4. Señales de alerta
| Si la IA… | Haz esto |
|---|---|
| Agrega librerías, servicios o almacenamiento | Detenla: viola el Artículo 8 |
| "Arregla" datos para que el ejemplo coincida | Rechaza: oculta el error real |
| Responde en inglés o mezcla idiomas | Recuérdale CLAUDE.md |
| Dice "listo" sin evidencia | Pide la verificación línea por línea |
| Inventa un dato | Exige `PENDIENTE: ¿…?` |

## 5. Cómo pedir ayuda a Claude (bien)
- ❌ "Haz la plantilla de transporte."
- ✅ "Con la tarjeta T-003-02 pegada abajo: plan en 3 viñetas; después crea solo `familia/6-nuestros-autos.md` con un ejemplo ficticio; al final muestra cómo se cumple cada TERMINADO CUANDO."

## 6. Autochequeo antes de entregar (puerta P4)
- [ ] Cumplí cada TERMINADO CUANDO y tengo evidencia
- [ ] No toqué archivos fuera de SALIDA
- [ ] Todo ejemplo dice EJEMPLO FICTICIO
- [ ] Corrí los 3 revisores y los registré
- [ ] Puedo explicar con mis palabras qué hace lo que entregué

## Ejemplo (EJEMPLO FICTICIO)
Un colaborador técnico recibe T-001-03. Claude propone "ajustar la skill para que la nota coincida con el ejemplo". El colaborador técnico lo rechaza (señal de alerta 2), registra la diferencia y la entrega. El Arquitecto corrige la skill en otra tarjeta. **Resultado:** el error se arregló en su origen y no en el síntoma.
