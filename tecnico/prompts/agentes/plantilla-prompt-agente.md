# Plantilla — Prompt de agente (para un subagente)

Un subagente **empieza sin contexto**: no ve el Proyecto ni la conversación. Todo lo que necesita va en el prompt.

```markdown
OBJETIVO: <una frase>
ROL: <quién es (ej. "revisor escéptico que no vio el trabajo")>
ENTRADAS: <pega aquí los datos VERDES que necesita; no le digas "mira el proyecto">
REGLAS:
- Español.
- Solo alias y bandas; si ves datos ROJOS, detente.
- <reglas específicas>
NO HAGAS: <lo prohibido>
SALIDA: <formato exacto: columnas de la tabla o formato de informe>
TERMINADO CUANDO: <regla de parada>
```

## Checklist
- [ ] ¿Pegué los datos en lugar de referirme a ellos?
- [ ] ¿Tiene una regla de parada?
- [ ] ¿La salida se puede comparar con la de otros subagentes (mismo formato)?

---

## Ejemplo (EJEMPLO FICTICIO)
```markdown
OBJETIVO: Encontrar la tasa base de admisión en primarias bilingües privadas de la región.
ROL: investigador con fuentes públicas.
ENTRADAS: región = "sureste de México"; nivel = primaria; año = 2026.
REGLAS:
- Español. Ningún dato de la familia en las búsquedas.
- Solo fuentes oficiales o informes de escuelas.
NO HAGAS: inventar cifras ni enlaces; decidir la probabilidad final.
SALIDA: tabla | Dato | Valor | Año | Fuente | Confianza 1–5 | + "Cómo usarlo" en 2 frases.
TERMINADO CUANDO: tengas 2 fuentes que coincidan, o tras 5 búsquedas sin éxito (repórtalo).
```
