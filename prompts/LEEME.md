# prompts/ — Prompts del sistema

| Tipo | Quién lo escribe | Dónde vive | Frecuencia de cambio |
|---|---|---|---|
| **Sistema** | Arquitecto | Instrucciones del Proyecto o `CLAUDE.md` | Rara vez, con versión |
| **Humano** | Cualquier integrante de la Junta o Vibe Coder | El mensaje del chat | Cada petición |
| **Agente** | Claude (o tú, al pedir un subagente) | Dentro de la tarea entregada a un subagente | Cada tarea |

| Subcarpeta | Archivos |
|---|---|
| `sistema/` | `prompt-sistema-family-inc.md` (para la Junta) · `prompt-sistema-vibe-coder.md` (para quien construye) |
| `humanos/` | `plantilla-prompt-humano.md` · `ejemplos-por-rol.md` |
| `agentes/` | `plantilla-prompt-agente.md` · `patrones-agentes.md` |

## Regla de oro
Un prompt bueno dice **rol, tarea, contexto, restricciones, formato de salida y cuándo terminar**. Si falta uno, la IA lo inventa.

## Ejemplo: de malo a bueno
- ❌ "¿Qué hacemos con la escuela?"
- ✅ "Rol: VP de Producto. Tarea: hoja de ruta de Hijo-1. Contexto: perfil-familia y DEC-001. Restricción: alias y bandas. Salida: la tabla de la skill. Termina con la siguiente acción, su dueño y la fecha."
