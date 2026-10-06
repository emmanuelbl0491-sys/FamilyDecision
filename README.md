# Family Decision Board

> Un sistema para que la familia tome decisiones importantes con orden, no con corazonadas.
> **Lo llenan personas. Claude ayuda. La familia decide.**

Versión: `v0.2.0` · Fecha: 2026-10-05 · Idioma: **español**

## ¿Por dónde empiezo?

- **¿Eres de la familia o el Vibe Coder?** Abre la terminal en esta carpeta, escribe `claude` y luego **`/empezar`**. Más detalle en [`EMPIEZA-AQUI.md`](EMPIEZA-AQUI.md).
- **¿Eres el Arquitecto?** Abre [`tecnico/LEEME.md`](tecnico/LEEME.md).

## Las carpetas

```
family-decision-board/
├── EMPIEZA-AQUI.md              ← paso a paso para la familia
├── frases-para-claude.md        ← frases listas para copiar y pegar
├── encargos-del-arquitecto.md   ← tareas para el Vibe Coder, en palabras sencillas
├── familia/                     ← quiénes somos, dinero, lo que nunca aceptamos, fechas
├── decisiones/                  ← nueva decisión, mi opinión a solas, ejemplos
├── juntas/                      ← notas de la junta, lo que decidimos, cómo nos sentimos
├── mis-datos/                   ← sus copias llenas (nunca se suben a internet)
├── privado/                     ← nombres reales y cifras exactas (nunca entran a Claude)
├── tecnico/                     ← solo para el Arquitecto y Claude
├── .claude/                     ← comandos /empezar, /llenar, /revisar, /junta y candados de privacidad
└── CLAUDE.md                    ← reglas que Claude lee al abrir el proyecto
```

## Cómo funciona, en una línea

```
/empezar → Claude pregunta y guarda en mis-datos/ → /revisar: Claude revisa, ordena, pone números y califica
→ la familia corrige → la Junta decide → el Arquitecto revisa que todo funcione
```
