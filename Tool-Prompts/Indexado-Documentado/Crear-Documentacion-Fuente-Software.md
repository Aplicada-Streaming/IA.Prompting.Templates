# Tool-Prompt — Crear Documentación de Fuentes de Software

> **Invocación**:
> - Una solución o proyecto: `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Crear-Documentacion-Fuente-Software.md en la solución {origen} y deja en: {destino}`
> - Un workspace o conjunto de soluciones: `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Crear-Documentacion-Fuente-Software.md en el workspace {origen}, dejá la documentación en: {destino}`
> - Con acceso a datos: agregar a la línea dónde están las cadenas de conexión (p. ej. «en los appsettings.json de cada proyecto están las cadenas de conexión»).

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{origen}` | Qué documentar: un proyecto, una solución multi-proyecto, un workspace o un conjunto de soluciones relacionadas (librerías, webs, REST APIs, apps móviles, bases de datos, batch, o combinaciones) | Solicitarlo al usuario antes de comenzar |
| `{destino}` | Dónde generar la documentación y la ia-db | `<origen>.Documentacion`, junto al origen |
| `{conexiones}` | Dónde obtener cadenas de conexión (p. ej. `appsettings.json`) para documentar bases de datos y construir ejemplos con datos — uso exclusivo de solo lectura | Documentar sin acceso a datos; el gap se declara en el manifiesto |
| `{énfasis}` | Prioridad documental pedida: flujos de ciclo de vida con datos para QA, snippets de extensión/implementación, guía SDD, etc. | Derivarlo del `type` de cada pieza según el Marco §7 |

---

# Contexto

`{origen}` no dispone de un conjunto documental conforme al Marco de Documentación de Software (o debe reconstruirse). El conocimiento vive solo en el código y, si hay bases de datos, en sus esquemas; incorporar personas, extender funcionalidades o preparar pruebas exige releer las fuentes completas.

---

# Objetivo

Evaluar `{origen}` y generar en `{destino}` su conjunto documental conforme al Marco —comprensible para humanos y operable por agentes de IA—, junto con la ia-db que lo hace navegable y regenerable.

---

# Solicitudes

- Resolver `{origen}`, `{destino}`, `{conexiones}` y `{énfasis}`; confirmar el modo (pieza única, solución o workspace federado) y fijar el contrato de ejecución (`Rule-Drift-Control`).
- Si ya existe documentación o ia-db en `{destino}`, informarlo y preguntar si se regenera o se actualiza de forma incremental.
- **Fase 1 — Indexar**: generar `{destino}/ia-db` según el Profile `Knowledge-Indexing` (misma estructura que produce `Iniciar-Indexado.md`); si ya existe, actualizarla. La ia-db guía el resto del análisis.
- **Fase 2 — Clasificar**: producir `system-map.md` y `docs-manifest.yaml` con el `type` de cada pieza (Marco §7) y sus `required_docs`; iniciar `GLOSSARY.md`.
- **Fase 3 — Documentar por pieza**: delegar subagentes por pieza, cada uno con el perfil documental de su `type`; bases de datos con `{conexiones}` en solo lectura (Marco §14); si el énfasis lo pide, derivar matriz `TC-` y fixtures sintéticos (§15) y extraer snippets con procedencia (§13).
- **Fase 4 — Nivel solución**: arquitectura C4, vistas de runtime de los flujos clave narradas de punta a punta con datos concretos (sintéticos), ADRs reconstruidos y catálogo de APIs.
- **Fase 5 — Consolidar**: índice maestro `README.md` de `<nombre>-docs`, verificación de enlaces y frontmatter, reporte de gap documental y de derivas, y sincronización final de la ia-db.

---

# Restricciones

- **No modificar el código fuente de `{origen}`** bajo ninguna circunstancia: solo lectura; todo lo generado vive en `{destino}`.
- **No modificar las bases de datos**: solo introspección de estructura y lecturas de solo lectura; sin `DDL`/`DML`; nunca credenciales ni datos personales reales en los entregables (los ejemplos se sintetizan o seudonimizan).
- No hacer commit, push ni pull request.
- No inventar información: todo entregable trazable a la ia-db o a una fuente; lo inferido lleva `origin` y `confidence`; todo queda en `status: draft` para revisión humana.
- Respetar las exclusiones de escaneo del Profile `Knowledge-Indexing` (`.git`, dependencias, artefactos de build, binarios, la propia ia-db).

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Solution-Documentation.md`

---

# Verificación de finalización

- [ ] Un humano entiende qué es la solución y cómo navegarla leyendo solo el `README.md` de `<nombre>-docs`; un agente calcula el gap documental leyendo solo `docs-manifest.yaml` + frontmatter.
- [ ] Toda pieza del origen figura en `system-map.md` y en el manifiesto con su `type` y sus documentos generados (o su gap declarado).
- [ ] Los flujos, snippets o casos pedidos en `{énfasis}` existen, con datos sintéticos y procedencia verificable.
- [ ] El origen quedó intacto (ninguna escritura fuera de `{destino}`) y ninguna base de datos fue modificada.
- [ ] La ia-db quedó sincronizada con la documentación generada y su manifiesto permite regenerar o actualizar ambas.
