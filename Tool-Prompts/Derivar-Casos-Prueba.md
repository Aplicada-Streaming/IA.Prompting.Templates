# Tool-Prompt — Derivar Casos de Prueba

> **Invocación**:
> - `Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Derivar-Casos-Prueba.md en {proyecto}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{proyecto}` | Proyecto/solución cuyo modelo de datos se usará como fuente (diccionario + ER) | Solicitarlo al usuario antes de comenzar |
| `{destino}` | Dónde escribir la matriz y los fixtures | `docs/03-data/` del repositorio del proyecto |

---

# Contexto

QA de `{proyecto}` necesita casos y datos de prueba **derivados del modelo de datos** —diccionario + ER (§14)— para verificar dominios, constraints, integridad referencial y reglas de negocio, sin usar datos productivos.

---

# Objetivo

Generar `test-data-matrix.md` (casos `TC-` trazables a `RF-`/`RNF-`) y fixtures sintéticos PII-safe a partir del diccionario de datos y el ER.

---

# Solicitudes

- Leer el `data-dictionary.md` + ER (dbml) y las reglas/invariantes (ADRs, `RNF-`).
- Derivar, por columna: clases de equivalencia y valores de borde; por FK: casos de integridad referencial; por regla: casos negativos.
- Asignar `TC-` a cada caso y enlazarlo a su `RF-`/`RNF-`; volcar en `test-data-matrix.md` y actualizar `traceability-matrix.md`.
- Generar fixtures sintéticos PII-safe (`seed` fijo), consistentes con las FKs, en `fixtures/`.
- Reportar gaps de cobertura (columnas/constraints/FKs sin caso) y reglas sin invariante testeable.
- Actualizar los índices/base de conocimiento en `{destino}`.

---

# Restricciones

- Nunca usar ni copiar datos productivos; los fixtures son sintéticos y la PII se sustituye por datos generados con formato válido.
- No inventar columnas ni reglas ausentes del modelo; lo inferido se marca con `origin: ai-assisted` y `confidence`.
- La IA no aprueba sus propios casos: quedan en `draft` para revisión de QA.

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/QA-Test-Design.md`
