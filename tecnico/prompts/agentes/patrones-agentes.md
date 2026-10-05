# Patrones de agentes

Empieza siempre por el patrón más simple que funcione. La mayoría de las decisiones familiares solo necesitan los dos primeros.

| Patrón | Cómo funciona | Úsalo para | Costo |
|---|---|---|---|
| Agente único + skill | Un chat, una skill de rol | Números semanales del CFO, fechas del COO | Bajo |
| Cadena de prompts | Enmarcar → ramas → resultados → pros y contras con nota → memo, un paso por mensaje y tú revisas cada uno | Decisiones grandes | Bajo |
| Orquestador–trabajadores | El CEO divide, los subagentes investigan en paralelo y el CEO une | Comparar 3 países, 3 escuelas o 3 pólizas | Medio |
| Evaluador–optimizador | Un agente redacta, otro critica con una rúbrica; 2 rondas | Revisar probabilidades y puntos ciegos | Medio |
| Debate / equipo rojo | Un subagente "a favor" y otro "en contra"; el CEO resume | Decisiones emocionales (segundo hijo, mudarse lejos de los abuelos) | Medio |
| Enrutador | Una instrucción envía cada pregunta a la skill correcta | Uso diario con todas las skills instaladas | Bajo |

**Prohibido:** agentes autónomos que actúen sobre cuentas (pagar, solicitar, reservar). Toda acción en el mundo exterior la hace un humano.

---

## Ejemplo 1: orquestador–trabajadores (EJEMPLO FICTICIO)
```
Usa 3 subagentes en paralelo con la plantilla de tecnico/prompts/agentes/plantilla-prompt-agente.md:
- Subagente 1: costo y periodo de espera de pólizas con maternidad, tipo A.
- Subagente 2: lo mismo para el tipo B.
- Subagente 3: lo mismo para el tipo C.
Cada uno devuelve: | Póliza | Banda de costo | Espera (meses) | Fuente |.
Después, como Jefe de Atención, une las 3 tablas y marca cuál cumple LD-02 para 2027-H2.
```

## Ejemplo 2: evaluador independiente (EJEMPLO FICTICIO)
```
Lanza un subagente que NO haya visto este análisis, con el prompt de
tecnico/subagentes/revisor-decisiones.md, y pásale solo el Markdown de DEC-001.
Que me devuelva su informe sin mi interpretación.
```

## Ejemplo 3: debate (EJEMPLO FICTICIO)
```
Dos subagentes sobre DEC-004 "¿Nos mudamos a otra ciudad en 2028?":
- A FAVOR: el mejor caso posible con datos del perfil.
- EN CONTRA: el mejor caso para quedarnos.
Cada uno: 5 argumentos en lista con formato "qué · pilar · nota del 1 al 10". Como CEO, resume en
una tabla de acuerdos y desacuerdos. No recomiendes: la Junta decide.
```
