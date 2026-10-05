# 02 — Privacidad por zonas

**Propósito:** que ningún dato sensible termine en la web ni entrenando modelos de IA.
**Dueño:** Arquitecto de Soluciones IA · **Última revisión:** 2026-10-05

## Regla principal
Si un dato puede **identificar a una persona** o **abrir una cuenta**, nunca sale de la computadora de la familia.

## Las tres zonas

| Zona | Dónde vive | Ejemplos | ¿Entra a Claude? |
|---|---|---|---|
| 🔴 ROJA | `privado/` cifrado o gestor de contraseñas | CURP, RFC, NSS, pasaporte, cuentas, tarjetas, direcciones, expedientes médicos, nombres reales | **Nunca** |
| 🟠 ÁMBAR | `privado/datos-familia.xlsx` | Ingresos exactos, saldos, edades exactas, límites de póliza | Solo como **banda** |
| 🟢 VERDE | `datos/` y conocimiento del Proyecto | Alias, bandas, metas, restricciones, decisiones, fechas | Sí |

## Bandas estándar (se ajustan una vez en `datos/plantillas/bandas.plantilla.md`)

| Banda | Ingreso anual familiar (USD) | Uso |
|---|---|---|
| A | < 30k | — |
| B | 30–60k | — |
| C | 60–80k | — |
| D | 80–120k | — |
| E | > 120k | — |

## Candados (en orden de importancia)
1. **Entrenamiento desactivado:** Settings > Privacy > "Help improve Claude" en OFF. Con el entrenamiento desactivado, los chats se conservan unos 30 días en lugar de hasta 5 años. Revísalo después de cada reinstalación.
2. **Alias, no nombres.** La clave alias ↔ nombre vive solo en `privado/clave-alias.md`.
3. **Bandas, no cifras.**
4. **Auditoría antes de subir:** el subagente `auditor-privacidad` revisa cada archivo nuevo.
5. **Modo incógnito** para preguntas sensibles aisladas. Registra solo la conclusión.
6. **Memoria del Proyecto separada** de la memoria general de la cuenta. Revisión mensual.
7. **Sin conectores a bancos ni portales de salud.** Exporta, convierte a bandas y luego comparte.
8. **El tablero no guarda ni envía datos.** Se exporta a JSON y se guarda localmente.

## Patrones que el auditor bloquea
| Patrón | Ejemplo detectado |
|---|---|
| CURP (18 caracteres) | `ABCD001122HDFXYZ09` |
| RFC (12–13) | `ABCD001122XY1` |
| Tarjeta (13–19 dígitos) | `4111 1111 1111 1111` |
| CLABE (18 dígitos) | `012180001234567890` |
| Correo o teléfono personal | `nombre@correo.com` |
| Dirección | "Calle…, número…, colonia…" |
| Cifras exactas de dinero en archivos VERDES | `74,300 USD` |

## Límite honesto
Anthropic procesa lo que envías. Los candados **reducen** lo que se envía, pero no convierten la IA en la nube en una herramienta sin conexión. La zona ROJA se maneja sin IA.

## Ejemplo (EJEMPLO FICTICIO)
**Antes (ÁMBAR):** "Padre-A gana 6,200 USD/mes en la empresa X; ahorro 41,000 USD en el banco Y."
**Después (VERDE):** "Padre-A: ingreso Banda C, estabilidad 4/5. Colchón de 7–9 meses."
