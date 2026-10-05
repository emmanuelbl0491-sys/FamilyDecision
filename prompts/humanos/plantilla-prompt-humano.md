# Plantilla — Prompt humano

Copia, llena y pega en el chat. Las seis líneas evitan que la IA adivine.

```markdown
Rol: <CEO | COO | CFO | VP de Producto | Jefe de Atención | Revisor>
Tarea: <qué quieres, con un verbo: calcula, compara, redacta, revisa>
Contexto: <qué archivos o datos usar (ej. perfil-familia, DEC-001)>
Restricciones: <límites: bandas, fecha, presupuesto, qué no hacer>
Salida: <formato: tabla, memo, lista de 5 viñetas>
Termina cuando: <condición clara (ej. "cuando tengas la nota de cada rama")>
```

## Checklist antes de enviar
- [ ] ¿Usé solo alias y bandas?
- [ ] ¿Nombré el archivo de contexto?
- [ ] ¿Pedí un formato concreto?

---

## Ejemplo (EJEMPLO FICTICIO)
```markdown
Rol: CFO
Tarea: Compara mantener Auto-1 contra comprar Auto-2 en 2027-03.
Contexto: perfil-familia (transporte, ingresos), limites-duros, bandas.
Restricciones: pago mensual máximo G2; colchón de al menos 6 meses en el escenario probable.
Salida: la tabla de escenarios de la skill CFO + 3 líneas para la Junta.
Termina cuando: sepamos si alguna opción rompe LD-01 o LD-03.
```
