# Tool-Prompt — Actualizar Indexado

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Actualizar-Indexado.md de {proyecto}`
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Actualizar-Indexado.md del workspace` (ia-db federada en `/ia-db`)

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{ia-db}` | Ubicación de la base de conocimiento a sincronizar | Buscar en orden: `/ia-db` (workspace federado) → `<proyecto>/ia-db` → glob `*/ia-db/README.md` |
| `{proyectos}` | Subconjunto de proyectos a sincronizar (solo modo federado) | Todos los proyectos listados en el manifiesto de la ia-db |

---

# Contexto

La ia-db dispone de un **manifiesto de generación** (sección final de su `README.md`) que registra alcance, fuentes, fecha y versión. Desde esa fecha los proyectos pudieron haber cambiado, y los índices pueden contener información desactualizada u obsoleta.

---

# Objetivo

Sincronizar la ia-db con el estado actual del proyecto mediante una actualización **incremental**: actualizar solo lo afectado por los cambios, sin reconstruir la base completa.

---

# Solicitudes

- Leer `{ia-db}/README.md` y su manifiesto: alcance (proyectos), fuentes, fecha y versión vigentes.
- Detectar los cambios de cada proyecto del alcance desde esa fecha (historial git, fechas de modificación, changelog), ignorando las carpetas excluidas por el Profile (`.git`, dependencias, artefactos de build, binarios). En modo federado con varios proyectos afectados, verificar en paralelo con subagentes.
- Determinar qué índices temáticos resultan afectados.
- Actualizar únicamente los índices afectados, eliminando referencias obsoletas.
- Actualizar la tabla de navegación del punto de entrada si aparecieron o desaparecieron dominios o proyectos.
- Incrementar la versión y actualizar la fecha en el manifiesto.
- Informar un resumen de lo actualizado: índices tocados, entradas agregadas, corregidas y eliminadas.

---

# Restricciones

- No modificar el código fuente ni la documentación de los proyectos: solo archivos dentro de `{ia-db}`.
- Si la ia-db no tiene manifiesto (formato previo), reconstruir la sección de manifiesto a partir de lo observable e informarlo.
- No hacer commit, push ni pull request.
- No reconstruir índices sin cambios detectados.
- Ante contradicción entre índice y evidencia actual, prevalece siempre la evidencia.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Knowledge-Indexing.md`

---

# Verificación de finalización

- [ ] Ningún índice contradice el estado actual de los proyectos.
- [ ] Los índices no afectados no fueron modificados.
- [ ] El manifiesto refleja la nueva fecha y versión.
