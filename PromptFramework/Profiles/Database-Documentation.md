# Profile — Database Documentation

## Objetivo

Configurar el agente para documentar una base de datos de forma integral y **regenerable**: producir el diccionario de datos y el modelo entidad-relación como código (dbml) a partir del **esquema real**, enriquecidos con la semántica de negocio, sin exponer credenciales ni datos. Materializa el proceso §14 del Marco de Documentación de Software.

---

# Framework

## Rule Set

- `/IA.Prompting.Templates/PromptFramework/RuleSets/RuleSet-Documentation.md`

## Referencia de dominio

- `/IA.Prompting.Templates/Referencias/Marco-Documentacion-Software-v1.md` — §14 (pipeline BD → diccionario + ER), §7.1 (perfil `database`), §5.4 (reglas de oro: nunca credenciales), Anexo A.18 (dbml).

---

# Enfoque

La fuente de verdad es el **esquema real** (catálogo del motor / `information_schema`), no lo que alguien cree que hay. El agente **introspecciona estructura** (tablas, columnas, tipos, claves, índices, constraints, comentarios), la vuelca a **dbml diffeable** y la **enriquece con la semántica de negocio** que el esquema no contiene (descripciones, dominios, unidades, reglas, PII, retención), tomada del glosario y los requisitos. Nunca lee ni copia filas de datos.

---

# Objetivos específicos

Identificar y documentar, cuando corresponda:

| Dimensión | Contenido |
|-----------|-----------|
| Estructura | Tablas, columnas, tipos, `nullability`, claves primarias y foráneas, índices, constraints, comentarios (`COMMENT`) |
| Modelo ER | Relaciones y cardinalidades como código dbml, particionado por área/bounded-context si el modelo es grande |
| Semántica | Descripción de cada tabla/columna, dominio de valores, unidades, reglas de negocio |
| Sensibilidad | Columnas marcadas como PII y su política de retención |
| Acceso | Roles y permisos sobre la BD (**sin credenciales**) |
| Trazabilidad | Enlaces a ADRs, requisitos (`RF-`/`RNF-`) y plan de migraciones |

---

# Artefactos de salida

| Artefacto | Ruta (en la solución documentada) | Formato |
|-----------|-----------------------------------|---------|
| Diccionario de datos | `docs/03-data/data-dictionary.md` | Markdown (fila por tabla/columna) |
| Modelo entidad-relación | `docs/03-data/er-diagrams/<área>.dbml` (+ render SVG) | dbml (A.18) |
| Políticas de acceso | `docs/03-data/access-policies.md` | Markdown (roles→permisos) |

> Estos artefactos **instancian** los `doc_type` `data-dictionary` y `er-model` del `docs-manifest.yaml` (Marco §12.2). Emitir en `status: draft`, `origin: reverse-engineered`, con `confidence` por sección; la promoción a `approved` requiere revisión humana (Marco §12.4).

---

# Procedimientos

1. **Acceso mínimo:** obtener un rol de **solo lectura** desde el gestor de secretos; preferir réplica/no-producción; registrar quién autoriza.
2. **Introspección** determinística del catálogo (`information_schema` / `pg_catalog`), o herramienta (`tbls`, SchemaSpy, `@dbml/cli`).
3. **Generar dbml base** (`sql2dbml` desde DDL o `db2dbml` desde conexión) y particionar por área/bounded-context.
4. **Enriquecer el diccionario** con semántica, PII y retención (desde glosario y requisitos).
5. **Actualizar `access-policies.md`** (roles→permisos), sin credenciales.
6. **Reportar** discrepancias esquema↔migraciones↔código; nunca resolverlas en silencio.

---

# Restricciones

- **Solo lectura:** ejecutar únicamente introspección del catálogo; nunca `SELECT` de datos ni `DDL`/`DML`.
- **Sin credenciales en el repo:** salen del gestor de secretos; se documenta cómo obtenerlas y quién autoriza, jamás el secreto.
- **Sin datos ni PII:** no extraer, imprimir ni pegar filas; los datos de ejemplo solo son sintéticos.
- **No inventar:** toda afirmación respaldada por el esquema; lo inferido se marca con `origin` y `confidence`.
- **No promover a `approved`** sin revisión humana registrada.

---

# Diagramas típicos

Diagrama ER (dbml renderizado), flujo de generación (secretos → conexión → introspección → dbml → diccionario), mapa de relaciones entre áreas/bounded-contexts.

---

# Resultado esperado

Un diccionario de datos y un modelo ER en dbml que representan fielmente el esquema real, **regenerables** desde la propia base, enriquecidos con la semántica de negocio, con PII y retención marcadas y sin exponer credenciales ni datos — listos para revisión humana e integración al conjunto documental de la solución.
