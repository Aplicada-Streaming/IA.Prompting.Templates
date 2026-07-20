# Tool-Prompt — Iniciar Contexto

> **Invocación**: `Ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado/Iniciar-Contexto.md en {tema}`
>
> **Nota de diseño**: este prompt es autónomo — no cargar Profiles, RuleSets ni Rules. Su única función es arrancar la conversación con el mínimo consumo de tokens. Es la excepción documentada a la jerarquía del framework.

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{tema}` | Tema o dominio sobre el que tratará la conversación (p. ej. «arquitectura del bot», «despliegue», «pruebas E2E») | Solicitarlo al usuario |
| `{proyecto}` | Proyecto al que pertenece el tema | Inferirlo del tema; si es ambiguo, preguntar |

---

# Objetivo

Cargar en la conversación el contexto mínimo suficiente sobre `{tema}`, usando la base de conocimiento `ia-db` del proyecto, y quedar listo para recibir la tarea del usuario.

---

# Procedimiento

1. **Localizar la ia-db**, en este orden: `<proyecto>/ia-db` del proyecto del tema → `/ia-db` en la raíz del workspace (federada) → glob `*/ia-db/README.md`. En una ia-db federada, usar la tabla por proyecto para bajar a los índices del proyecto del tema.
2. **Leer solo el punto de entrada**: `ia-db/README.md`.
3. **Seleccionar índices**: con la tabla de navegación del punto de entrada, elegir los índices temáticos que cubren `{tema}` (habitualmente 1–2, más `00_MASTER-INDEX.md` solo si el tema es transversal).
4. **Cargar únicamente esos índices**. Ampliar a un índice adicional solo si el contexto resulta insuficiente.
5. **Confirmar el contexto**: responder al usuario con un resumen de no más de 10 líneas indicando proyecto, tema, índices cargados, vigencia del índice (fecha/versión) y los 3–5 puntos clave del tema. Finalizar preguntando cuál es la tarea.

---

# Restricciones

- No leer código fuente ni documentación completa en esta fase: solo la ia-db.
- No cargar todos los índices «por las dudas»: la recuperación es incremental.
- No ejecutar ninguna tarea todavía: este prompt solo prepara el contexto.
- No modificar ningún archivo.
- Si el proyecto no tiene ia-db, informarlo y proponer ejecutar `/IA/IA.Prompts/Tool-Prompts/Indexado/Iniciar-Indexado.md` — no improvisar un barrido del repositorio.

El paso 5 del procedimiento es la condición de finalización: un mensaje breve de confirmación de contexto, con el agente a la espera de la tarea y habiendo consumido solo el punto de entrada más los índices estrictamente necesarios.
