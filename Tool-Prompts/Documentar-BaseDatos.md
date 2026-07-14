# Tool-Prompt — Documentar Base de Datos

> **Invocación**:
> - `Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Documentar-BaseDatos.md en {proyecto}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{proyecto}` | Base de datos a documentar (proyecto/servicio dueño, o cómo obtener el acceso de solo lectura) | Solicitarlo al usuario antes de comenzar |
| `{destino}` | Dónde escribir la documentación | `docs/03-data/` del repositorio del proyecto dueño de la BD |

---

# Contexto

La base de datos de `{proyecto}` requiere documentación **regenerable** de su estructura —diccionario de datos y modelo entidad-relación— que represente el esquema real y acompañe al conjunto documental de la solución, sin exponer credenciales ni datos.

---

# Objetivo

Generar `data-dictionary.md` y el modelo ER en `dbml` a partir del esquema real, enriquecidos con la semántica de negocio, con PII y retención marcadas.

---

# Solicitudes

- Obtener acceso de **solo lectura** desde el gestor de secretos y registrar quién lo autoriza.
- Introspeccionar el catálogo (`information_schema` / catálogo del motor), o usar `tbls` / SchemaSpy / `@dbml/cli`.
- Generar el modelo ER en `er-diagrams/<área>.dbml`, particionado por área si es grande, y su render.
- Generar el `data-dictionary.md` (tabla/columna, tipos, claves, descripción, PII, retención, trazas).
- Actualizar `access-policies.md` (roles→permisos, sin credenciales).
- Marcar columnas candidatas a PII; activar el perfil regulado (A.17) si la solución lo es.
- Reportar discrepancias esquema↔migraciones↔código sin resolverlas.
- Actualizar los índices/base de conocimiento en `{destino}`.

---

# Restricciones

- No modificar la base; ejecutar únicamente introspección del catálogo (sin `SELECT` de datos, sin `DDL`/`DML`).
- Nunca escribir credenciales ni filas de datos en el repositorio; los datos de ejemplo solo son sintéticos.
- No inventar información; lo inferido se marca con `origin: reverse-engineered` y `confidence`.

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/Database-Documentation.md`
