# subagentes/ — Revisores e investigadores de IA

Un **subagente** es una instancia de Claude que empieza **sin contexto**, hace una sola tarea y entrega un informe. Los subagentes **nunca aprueban**: solo informan. Aprueba el Arquitecto.

| Subagente | Fase SDD | Orden | Revisa / hace |
|---|---|---|---|
| `auditor-privacidad` | F5 | 1º | Datos de zona ROJA, cifras exactas, nombres reales |
| `revisor-decisiones` | F5 | 2º | Matemática y consistencia de decisiones y datos |
| `revisor-entregable` | F5 | 2º (en paralelo) | Que el trabajo del Vibe Coder cumpla la tarjeta y la constitución |
| `revisor-gramatical` | F5 | 3º (último) | Español claro, ortografía, glosario |
| `investigador` | F2 / datos | a pedido | Tasas base y fuentes para las probabilidades |
| `generador-json` | F7 | al final | Arma el JSON del tablero desde el Markdown aprobado. Los humanos nunca escriben JSON |

## Instalación
- **Claude Code:** copia cada `.md` a `.claude/agents/`. Invócalo así: *"Usa el subagente revisor-decisiones con datos/reales/decision-escuela.md"*.
- **claude.ai:** pide *"Lanza un subagente con estas instrucciones:"* y pega el cuerpo del archivo junto con los datos que debe revisar. Recuerda que **el subagente no ve tu Proyecto**: pásale todo lo que necesita.

## Formato común del informe
```
INFORME <subagente> — <archivo revisado> — AAAA-MM-DD
Veredicto: LISTO PARA ARQUITECTO | REQUIERE CORRECCIONES | DETENIDO
BLOQUEANTE (n): …
IMPORTANTE (n): …
SUGERENCIA (n): …
```

## Plantilla para un subagente nuevo
```markdown
---
name: <nombre>
description: <cuándo usarlo>
tools: Read, Grep, Glob
---
# <Nombre>
Eres … Tu única tarea es …
## Entrada
## Revisa
## Informe (formato común)
## Nunca
## Ejemplo
```

## Ejemplo de invocación en cadena
> "Revisa `datos/reales/decision-poliza.md` con auditor-privacidad. Si no se detiene, sigue con revisor-decisiones y al final con revisor-gramatical. Junta los tres informes en uno."
