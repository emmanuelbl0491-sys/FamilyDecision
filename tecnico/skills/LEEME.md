# tecnico/skills/ — Skills de Claude

> Los comandos para personas (`/empezar`, `/llenar`, `/revisar`, `/junta`) viven en `/.claude/skills/`, donde Claude Code los reconoce. Las skills de esta carpeta son de referencia técnica; para usarlas con un comando, cópialas a `.claude/skills/`.

Una **skill** es una carpeta con un `SKILL.md`. Su `description` le dice a Claude **cuándo** usarla y el cuerpo le dice **cómo**.

| Skill | Tipo | Se usa cuando… |
|---|---|---|
| `revisar-decision` | Proceso | La familia dice "Revisa mi decisión": privacidad → redacción → organizar → errores → calificación → respuesta simple |
| `puntuar-decision` | Proceso | Hay que calcular la nota de cada rama (promedio de notas 1–10), el punto más débil y el riesgo |
| `ceo` | Ejecutivo | Estrategia, migración, ubicación, ranking de decisiones |
| `coo` | Ejecutivo | Acciones fechadas, transporte, vivienda, fechas límite |
| `cfo` | Ejecutivo | Dinero, bandas, presupuesto, colchón, deuda |
| `vp-producto` | Ejecutivo | Educación, desarrollo de los hijos, nuevos integrantes |
| `jefe-atencion` | Ejecutivo | Seguro médico, embarazo, pulso de satisfacción |

## Instalación
- **claude.ai:** comprime cada carpeta (por ejemplo `cfo.zip`) y súbela desde la configuración de Skills.
- **Claude Code:** copia cada carpeta a `.claude/skills/`.

## Plantilla de SKILL.md
```markdown
---
name: <nombre-en-minusculas>
description: <Qué hace y CUÁNDO usarla, en una o dos frases. Incluye palabras que dirá el usuario.>
---
# <Nombre>
## Entrada
## Pasos
## Salida (formato fijo)
## Nunca
## Ejemplo
```

## Ejemplo de invocación
> "CFO: con `quienes-somos` y la DEC-003, ¿la compra del auto rompe el límite de colchón?"
