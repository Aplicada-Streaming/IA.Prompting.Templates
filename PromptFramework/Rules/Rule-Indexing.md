# Rule — Indexing

## Objetivo

Reglas para usar y mantener la base de conocimiento (`ia-db`): recuperar solo el contexto necesario, minimizar tokens y mantener la memoria sincronizada con la documentación.

La ubicación de la ia-db se resuelve desde `Parameters/Paths.md`; nunca se codifica fija.

---

# Recuperación incremental

Antes de una tarea que pueda beneficiarse de contexto documentado:

1. consultar el punto de entrada de la ia-db;
2. identificar los índices relevantes con su tabla de navegación;
3. cargar únicamente esos índices;
4. ampliar a documentos fuente solo ante insuficiencia comprobada.

Nunca recorrer el repositorio completo ni cargar toda la documentación cuando existe información indexada.

---

# Sincronización

- Si la ejecución genera documentos nuevos, cambios estructurales o nuevas relaciones, actualizar la ia-db antes de finalizar.
- Si la evidencia contradice el índice, prevalece la evidencia: corregir el índice y eliminar referencias obsoletas.
- Actualizar de forma **incremental**: solo lo afectado por cambios reales; no reconstruir la base cuando alcanza una actualización parcial.
- No duplicar conocimiento entre índices: reutilizar y referenciar.

---

# Principio rector

La ia-db es un punto de entrada al conocimiento, no una copia de la documentación: recuperar antes que volver a inferir, actualizar antes que reconstruir.
