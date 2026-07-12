# Rule — Agents

## Objetivo

Definir cómo asignar subagentes, ajustando la estructura de delegación al tamaño y la naturaleza real de la tarea.

Los límites (usar subagentes, paralelismo máximo) pueden indicarse en el propio prompt; en su ausencia, ajustarlos a la naturaleza de la tarea.

---

# Cuándo delegar

Delegar en subagentes cuando:

- la tarea se descompone en partes **independientes** ejecutables en paralelo (varios repos, varios dominios, varios documentos);
- una exploración amplia produciría más contexto del que la conversación necesita conservar (el subagente lee mucho, devuelve poco);
- se requieren perspectivas independientes (revisión, verificación adversarial).

No delegar cuando la tarea es secuencial, pequeña o depende del contexto ya cargado en la conversación: el costo de traspasar contexto superaría el beneficio.

---

# Autoajuste al tamaño de la tarea

Dimensionar la delegación según el trabajo real, no según un número fijo:

| Tarea | Asignación |
|-------|------------|
| Puntual o secuencial | Sin subagentes; ejecutar en la conversación |
| Pocas unidades independientes (2–4) | Un subagente por unidad |
| Muchas unidades homogéneas | Lotes por subagente, respetando el paralelismo máximo configurado |
| Resultado crítico | Agregar un subagente verificador independiente |

Cada subagente recibe **una única responsabilidad** y el contexto mínimo autocontenido para cumplirla: objetivo, alcance, restricciones, rutas exactas y formato del resultado esperado.

---

# Especialización

Cuando las subtareas requieran conocimientos distintos (arquitectura, seguridad, redes, documentación, etc.), formular cada prompt de subagente desde la especialidad correspondiente.

---

# Agregación de resultados

El agente principal:

- consolida los resultados verificando consistencia entre sí y con el objetivo;
- no acepta resultados sin evidencia (aplica `Rule-Evidences.md`);
- resuelve o reporta los conflictos entre resultados;
- integra todo en el reporte final según `Rule-Workflow.md`.
