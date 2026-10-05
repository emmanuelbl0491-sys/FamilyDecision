# 05 — RAG, memoria, historial y logs

**Propósito:** informar a los humanos qué infraestructura de IA necesita el proyecto, hoy y en el futuro.
**Dueño:** Arquitecto de Soluciones IA · **Última revisión:** 2026-10-05

## Veredicto actual

| Componente | ¿Se necesita? | Decisión | Alternativa usada |
|---|---|---|---|
| **RAG** (búsqueda vectorial) | ❌ No | Los datos VERDES de una familia (< 50 páginas) caben completos en el conocimiento del Proyecto | Conocimiento del Proyecto + archivos Markdown/JSON |
| **Backend / base de datos** | ❌ No | No hay usuarios múltiples ni sincronización automática | Carpeta local versionada |
| **Memoria de Claude** | ⚠️ Limitada | Solo memoria del Proyecto, configurada como **separada** | Los hechos estables viven en `datos/` |
| **Historial de conversación** | ⚠️ No como fuente de verdad | El chat no es auditable y puede perderse | Cada conclusión se copia a una bitácora |
| **Logs** | ✅ Sí | Las decisiones y las revisiones deben dejar rastro (principio 10) | `bitacora-decisiones` y `bitacora-revisiones` en Markdown |

## ✅ Logs obligatorios
| Log | Archivo | Quién escribe | Cuándo |
|---|---|---|---|
| Bitácora de decisiones | `flujo-trabajo/bitacora-decisiones.plantilla.md` (copia) | Junta | Al votar o cerrar una decisión |
| Bitácora de revisiones | `flujo-trabajo/bitacora-revisiones.plantilla.md` (copia) | Subagente + Arquitecto | En cada revisión F5/F6 |
| Registro de arquitectura (ADR) | `flujo-trabajo/adr.plantilla.md` (copia) | Arquitecto | Cuando cambia el diseño |
| Actas de junta | `flujo-trabajo/acta-junta.plantilla.md` (copia) | COO humano | Cada domingo |

Los logs **nunca** contienen datos de zona ROJA.

## Umbrales: cuándo cambiar el veredicto
Claude debe escribir `AVISO AL ARQUITECTO:` si se cumple alguno de estos umbrales.

| Señal | Umbral | Qué se necesitaría |
|---|---|---|
| Volumen de datos VERDES | > 200 páginas o > 300 archivos | RAG o resúmenes jerárquicos |
| Decisiones activas | > 25 simultáneas | Base de datos ligera (SQLite local) |
| Actualización automática | Se pide importar datos bancarios cada mes | Script local + conversión automática a bandas |
| Simulación | > 10,000 escenarios (Monte Carlo) | Repositorio Python local con Claude Code |
| Varios hogares | Más de una familia usa el sistema | Backend con autenticación y aislamiento |
| Continuidad | Se pierde contexto entre conversaciones más de 2 veces al mes | Resumen de estado en `flujo-trabajo/estado-proyecto.md` |

## Ejemplo de aviso (EJEMPLO FICTICIO)
> AVISO AL ARQUITECTO: la carpeta `datos/` ya tiene 320 archivos (umbral: 300). El conocimiento del Proyecto empieza a recortar contexto. Opciones: (a) archivar las decisiones cerradas en un resumen trimestral, o (b) evaluar RAG local. Recomiendo (a) primero porque es reversible y no requiere infraestructura.
