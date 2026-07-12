# Rule — Workflow

## Objetivo

Definir el ciclo de trabajo de toda ejecución: **diagnosticar → planificar → ejecutar → validar → reportar**.

Unifica las antiguas reglas de planificación y ejecución (`Rule-Tasks`, `Rule-Execution`) en un único ciclo.

---

# 1. Diagnóstico

Antes de planificar:

- identificar el objetivo real (principal y secundarios), el alcance, las restricciones y las dependencias;
- relevar el estado actual: qué existe, qué falta, qué contradice la solicitud;
- recuperar contexto previo desde la base de conocimiento antes de explorar fuentes completas (ver `Rule-Indexing.md`).

El diagnóstico ordena las ideas: primero qué pasa, después qué hacer.

---

# 2. Planificación

- Descomponer el trabajo en tareas con objetivo claro, única responsabilidad y resultado verificable.
- Identificar dependencias (técnicas, documentales, temporales) y respetar su orden.
- Priorizar: bloqueantes → mayor impacto → menos dependencias → menor riesgo.
- Reutilizar trabajo y documentación existentes antes de crear.
- Evaluar la asignación de subagentes según `Rule-Agents.md`.
- Validar el plan: toda tarea aporta al objetivo, sin redundancias ni dependencias circulares.

Si existe una estrategia mejor que la planteada por el usuario, reorganizar internamente el trabajo sin alterar el objetivo.

---

# 3. Ejecución

- Ejecutar conforme al plan; no improvisar habiendo planificación.
- Adaptar el plan solo cuando mejore el resultado o resuelva dependencias detectadas, siempre dentro del alcance.
- Usar solo los recursos necesarios: evitar consultas redundantes y recuperación excesiva de contexto.
- Ante un error: identificar la causa, documentar la limitación y su impacto, y continuar solo si es seguro. No ocultar errores ni propagarlos a tareas posteriores.

---

# 4. Validación

Cada tarea se verifica antes de considerarse terminada: cumple su objetivo, sin errores evidentes ni contradicciones, con dependencias satisfechas. Al cierre aplicar la verificación de finalización de `Rule-All.md`.

---

# 5. Reporteo

Todo trabajo finaliza con un reporte al usuario que siga esta estructura, omitiendo las secciones que no apliquen:

| Sección | Contenido |
|---------|-----------|
| Diagnóstico | Qué se encontró; estado inicial relevante |
| Plan | Qué se decidió hacer y en qué orden |
| Decisiones | Elecciones tomadas, criterios y alternativas descartadas |
| Resultado | Qué se hizo, con evidencias verificables |
| Pendientes y propuestas | Lo fuera de alcance, mejoras sugeridas, riesgos |

El reporte comienza por el resultado o hallazgo principal, y diferencia hechos de interpretaciones.
