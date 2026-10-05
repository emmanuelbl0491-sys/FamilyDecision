# Ejercicios del Arquitecto de Soluciones IA

Practica sobre el propio proyecto. Cada ejercicio trae su solución esperada; resuélvelo antes de leerla.

---

### Ejercicio 1 — Escribir una tarjeta sin ambigüedad
**Practica:** descomposición · **Tiempo:** 15 min
**Enunciado:** escribe la tarjeta para que un Vibe Coder cree `datos/plantillas/transporte.plantilla.md`.
**Solución esperada:** SALIDA de un solo archivo; DEBE con columnas (vehículo con alias, antigüedad, banda de costo mensual, fecha de reemplazo, confianza); NO DEBE con marcas o placas reales; TERMINADO CUANDO con "incluye un ejemplo ficticio de 2 vehículos" y "pasa auditor-privacidad sin hallazgos".

### Ejercicio 2 — Detectar un error matemático (CA-02 de la spec 001)
**Practica:** revisión · **Tiempo:** 10 min
**Enunciado:** en `decision-ejemplo.md` cambia "Le cuesta un año" de 30% a 20%. ¿Qué debe reportar `revisor-decisiones`?
**Solución esperada:** BLOQUEANTE: la rama 2 suma 90% (60 + 20 + 10).

### Ejercicio 3 — Prueba de privacidad (CA-03)
**Practica:** seguridad · **Tiempo:** 10 min
**Enunciado:** agrega al contexto de un ejemplo el texto ficticio `CURP ABCD001122HDFXYZ09`. Ejecuta `auditor-privacidad`.
**Solución esperada:** veredicto DETENIDO; el informe dice "tipo: CURP" **sin repetir el valor**. Si lo repite, el subagente falló y hay que corregir su prompt.

### Ejercicio 4 — El error en la documentación
**Practica:** verificación · **Tiempo:** 5 min
**Enunciado:** `docs/03-metodo-probabilistico.md` tiene un valor incorrecto intencional. Encuéntralo.
**Solución esperada:** el resumen viejo dice 6.75 para la rama 2; el valor correcto es 26 ÷ 4 = 6.50.

### Ejercicio 5 — Empate técnico
**Practica:** comunicación con no técnicos · **Tiempo:** 10 min
**Enunciado:** DEC-001 da 6.67 contra 6.50. Escribe en 3 frases, para la Junta, por qué "gana" la rama 1 pero no significa que sea la mejor.
**Solución esperada:** la diferencia (0.17) es menor que el empate técnico (0.5); cambiar una sola nota (por ejemplo, el traslado de 5 a 8 si hay transporte escolar) invierte el resultado; la Junta debe decidir cuánto valora la educación frente al dinero y la familia.

### Ejercicio 6 — Decidir sobre infraestructura
**Practica:** juicio arquitectónico · **Tiempo:** 15 min
**Enunciado:** la Junta pide "que el tablero recuerde los datos al cerrarlo". Redacta un ADR.
**Solución esperada:** alternativas: (a) volver a pegar el JSON que genera `generador-json` (actual), (b) `localStorage` (viola RT-10 y deja datos en el navegador), (c) capacidad de almacenamiento del artifact (sale de la computadora). Decisión recomendada: (a). Los humanos guardan su Markdown; el JSON se regenera cuando se necesita.

### Ejercicio 7 — Prompt de agente sin contexto
**Practica:** diseño de prompts · **Tiempo:** 10 min
**Enunciado:** este prompt falla: *"Revisa la decisión del proyecto"*. Reescríbelo con `plantilla-prompt-agente.md`.
**Solución esperada:** OBJETIVO, ROL, ENTRADAS con el Markdown de la decisión pegado, REGLAS, NO HAGAS, SALIDA con el formato de informe y TERMINADO CUANDO.

### Ejercicio 8 — Continuidad
**Practica:** gestión de contexto · **Tiempo:** 10 min
**Enunciado:** abre una conversación nueva con `PROMPT_CONTINUIDAD.md` + `estado-proyecto.md`. ¿La IA identifica la fase y la siguiente acción?
**Solución esperada:** responde en español: "Fase F1/F2; siguiente acción: firmar la constitución y cerrar el PENDIENTE de la spec 001 · Arquitecto · 2026-10-11".
