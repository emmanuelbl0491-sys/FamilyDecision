# tecnico/subagentes/ — Revisores e investigadores de IA

Un **subagente** es una instancia de Claude que empieza **sin contexto**, hace una sola tarea y entrega un informe. Los subagentes **nunca aprueban**: solo informan. Aprueba el Arquitecto.

Para decisiones de la familia, no se invocan uno por uno: la skill `revisar-decision` los encadena y traduce el resultado a palabras simples.

| Subagente | Fase SDD | Orden | Revisa / hace |
|---|---|---|---|
| `auditor-privacidad` | F5 | 1º | Datos de zona ROJA, cifras exactas, nombres reales |
| `revisor-gramatical` | F5 | 2º | Pule las ideas de la familia sin cambiar el sentido. También es la revisión final de todo archivo nuevo para personas |
| `revisor-decisiones` | F5 | 3º | Matemática y consistencia, después de que la IA asignó números, pilares y quién lo cuida |
| `revisor-entregable` | F5 | trabajo técnico | Que una tarjeta técnica cumpla lo pedido y la constitución |
| `investigador` | F2 / datos | a pedido | Tasas base y fuentes para las probabilidades |
| `generador-json` | F7 | al final | Arma el JSON del tablero desde el Markdown aprobado. Los humanos nunca escriben JSON |

## Instalación
- **Claude Code:** copia cada `.md` a `.claude/agents/`. Invócalo así: *"Usa el subagente revisor-decisiones con mis-datos/decision-escuela.md"*.
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
> "Revisa `mis-datos/decision-poliza.md` con auditor-privacidad. Si no se detiene, sigue con revisor-decisiones y al final con revisor-gramatical. Junta los tres informes en uno."
