# Rule — Drift-Control

## Objetivo

Mantener al agente —y a sus subagentes— alineados con el objetivo, el alcance y el destino declarados durante ejecuciones largas, multi-fase o delegadas: fijar el contrato de ejecución, definir los sensores que detectan la deriva y las acciones de corrección.

---

# Contrato de ejecución

Antes de ejecutar, fijar por escrito el **contrato de ejecución**:

| Elemento | Contenido |
|----------|-----------|
| Objetivo | Qué debe ser verdad al terminar (tomado del prompt) |
| Alcance | Qué entra y qué queda explícitamente fuera |
| Escritura | Únicas rutas donde se permite crear o modificar archivos |
| Lectura | Fuentes a consultar, todas en modo solo lectura salvo indicación explícita del prompt |
| Presupuesto | Límite orientativo por unidad de trabajo (tamaño del entregable, profundidad, subagentes) |
| Finalización | Criterios verificables de terminado |

Todo subagente recibe su contrato dentro del prompt de delegación (complementa `Rule-Agents.md`); sin contrato no hay delegación.

---

# Sensores de deriva

Evaluar durante toda la ejecución; ante una señal, aplicar la acción:

| Sensor | Señal de deriva | Acción |
|--------|-----------------|--------|
| Alcance | Se trabaja sobre elementos que no figuran en el inventario o alcance declarado | Detener la rama; volver al contrato |
| Escritura | Se intenta escribir fuera de las rutas permitidas o modificar una fuente de solo lectura | Abortar la operación y reportarla; nunca consumarla «porque ya estaba hecha» |
| Objetivo | Lo producido no responde a ninguna solicitud del prompt | Re-anclar: releer objetivo y solicitudes antes de continuar |
| Invención | Afirmaciones sin fuente trazable (aplica `Rule-Evidences.md`) | Marcar como no verificado o eliminar |
| Presupuesto | El consumo crece sin avance proporcional del entregable | Cerrar la unidad actual con lo verificado; reportar el resto como pendiente |
| Profundidad | Detalle desproporcionado en temas menores, o superficialidad en temas críticos | Reajustar al presupuesto del artefacto |

---

# Puntos de control

- Al cerrar cada fase o unidad de trabajo, verificar contra el contrato: objetivo parcial cumplido, escritura solo en rutas permitidas, fuentes intactas, entregables trazables.
- En pipelines por fases, una fase no comienza hasta que la anterior pasó su punto de control.
- El agente principal valida el resultado de cada subagente contra el contrato **antes** de integrarlo; el resultado que no cumple se rehace o se descarta, no se «acomoda».

---

# Re-anclaje y corte

- Ante deriva detectada: suspender la unidad, releer el contrato, descartar lo producido fuera de alcance (no «aprovecharlo») y reanudar desde el último punto de control válido.
- Deriva reiterada en la misma unidad (dos o más veces): detener la unidad y registrarla como pendiente con su causa. Nunca degradar silenciosamente la calidad ni ampliar el alcance para «terminar».

---

# Reporte

El reporte final (según `Rule-Workflow.md`) incluye las derivas detectadas y cómo se resolvieron; si no las hubo, se declara.
