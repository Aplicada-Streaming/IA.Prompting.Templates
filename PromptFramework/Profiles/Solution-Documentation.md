# Profile — Solution Documentation

## Objetivo

Configurar el agente para **evaluar y documentar una pieza de software de cualquier escala** —un proyecto, una solución multi-proyecto o un workspace con varias soluciones (librerías, webs, REST APIs, apps móviles, bases de datos, batch, o combinaciones)— aplicando el Marco de Documentación de Software como **política raíz** y orquestando subagentes documentadores por tipo de pieza. La documentación resultante sirve a dos audiencias: humanos que comprenden y agentes de IA que extraen y razonan.

---

# Framework

## Rule Set

- `/IA.Prompting.Templates/PromptFramework/RuleSets/RuleSet-Solution-Documentation.md`

## Referencia de dominio (política raíz)

- `/IA.Prompting.Templates/Referencias/Marco-Documentacion-Software-v1.md` — los agentes documentadores lo tratan como su política raíz (§2.2): estructura documental (§5), perfiles por tipo de pieza (§7), relevamiento legacy (§9), contrato máquina-legible (§12), snippets con procedencia (§13), base de datos (§14), casos de prueba (§15). Cada documento generado cumple el bloque «🤖 Para agentes» de la sección del Marco que lo gobierna.

## Profiles delegados

Para las piezas que lo requieran, los subagentes adoptan el Profile especializado:

| Trabajo | Profile |
|---------|---------|
| Indexado del origen (ia-db) | `/IA.Prompting.Templates/PromptFramework/Profiles/Knowledge-Indexing.md` |
| Base de datos: diccionario + ER dbml (§14) | `/IA.Prompting.Templates/PromptFramework/Profiles/Database-Documentation.md` |
| Casos y datos de prueba (§15) | `/IA.Prompting.Templates/PromptFramework/Profiles/QA-Test-Design.md` |
| Piezas restantes (según su `type`, §7) | Este Profile, con el perfil documental del Marco §7.1 |

---

# Enfoque

**Indexar → clasificar → documentar por pieza → consolidar.** La ia-db del origen se genera primero y guía todo el análisis: los agentes recuperan contexto desde los índices antes de releer fuentes (`Rule-Indexing.md`). La solución se documenta en dos niveles (Marco §5.1): el nivel solución responde *«cómo encaja todo y por qué»*; el nivel pieza, *«qué hace esto y cómo se usa»*. Todo lo generado nace en `status: draft` con `origin` y `confidence` declarados (Marco §9/§12); la promoción a `approved` es humana.

---

# Estructura de destino

Todo lo generado vive en `{destino}`; el origen nunca se toca:

```
{destino}/                        ← p. ej. <origen>.Documentacion
├── ia-db/                        ← indexación del origen (estructura del Profile Knowledge-Indexing)
└── <nombre>-docs/                ← conjunto documental (Marco §5.2, adaptado)
    ├── README.md                 ← índice maestro: mapa, navegación, estado del gap documental
    ├── GLOSSARY.md               ← vocabulario controlado (§12.3)
    ├── docs-manifest.yaml        ← manifiesto máquina-legible (§12.2): piezas, types, required_docs
    └── docs/
        ├── 00-overview/          ← vision.md, system-map.md (inventario de piezas)
        ├── 01-architecture/      ← C4/arc42: contexto, contenedores, vistas de runtime
        ├── 02-requirements/      ← solo lo reconstruible con evidencia
        ├── 03-data/              ← diccionario, er-diagrams/*.dbml, test-data-matrix, fixtures/
        ├── 04-decisions/         ← ADRs (origin: reverse-engineered)
        ├── 05-apis/              ← catálogo + openapi.yaml inferidos
        ├── 07-operations/        ← runbooks reconstruibles
        ├── 08-onboarding/        ← developer-setup.md
        └── pieces/<pieza>/       ← doc de nivel pieza: README, perfil §7, snippets §13
```

> **Adaptación declarada:** el Marco ubica la doc de pieza dentro de cada proyecto (§5.3); como este Profile **prohíbe modificar el origen**, esa doc se genera espejada en `pieces/<pieza>/`, lista para moverse al repositorio de la pieza cuando un humano la apruebe. Las carpetas numeradas sin contenido reconstruible se omiten explícitamente en el índice maestro (omisión al estilo arc42), no se crean vacías.

---

# Orquestación

| Fase | Trabajo | Punto de control (`Rule-Drift-Control.md`) |
|------|---------|--------------------------------------------|
| 1. Indexado | Generar `{destino}/ia-db` con Knowledge-Indexing; si existe, actualizarla incrementalmente | La ia-db responde «¿qué contiene el origen y con qué stack?» |
| 2. Clasificación | Desde la ia-db: `system-map.md` + `docs-manifest.yaml` con el `type` de cada pieza (§7) y sus `required_docs`; esqueleto de `GLOSSARY.md` | Toda pieza del origen figura en el manifiesto con un `type`; el gap documental es calculable |
| 3. Documentación por pieza | Subagentes por pieza (`Rule-Agents.md`), cada uno con su contrato de ejecución y el perfil documental de su `type` | Cada documento cumple frontmatter, el bloque «🤖» de su sección del Marco y `Rule-Dual-Audience.md` |
| 4. Nivel solución | Arquitectura C4 (contexto, contenedores), vistas de runtime de los flujos clave, ADRs reconstruidos, catálogo de APIs | El nivel solución referencia a las piezas, no las duplica (§5.4) |
| 5. Consolidación | Índice maestro, verificación de enlaces y frontmatter, reporte de gap documental y de derivas; sincronizar la ia-db con la doc generada | Verificación de finalización del prompt completa |

---

# Adecuación por tipo de pieza

El `type` de cada pieza (declarado en el manifiesto) decide qué documenta su subagente, además de la base común (README de pieza, configuración, arquitectura local):

| `type` (Marco §7.1) | Énfasis documental |
|---------------------|--------------------|
| `service` (REST/eventos) | `openapi.yaml` inferido de los controladores (las divergencias contrato↔código se reportan, §6), dependencias declaradas, runbook |
| `web-portal` | Mapa de rutas/páginas, accesibilidad, gestión de contenidos |
| `mobile-app` | Estructura y procesos clave, permisos y su justificación, releases por store, snippets de extensión |
| `library` | API pública, guía de uso e implementación con snippets (§13), matriz de compatibilidad, guía de migración |
| `component-library` | Catálogo de componentes (props, ejemplos, estados), política de breaking changes |
| `batch/worker` | Disparadores, contratos de entrada/salida, reintentos e idempotencia, reproceso |
| `database` | Delegar en `Database-Documentation` (§14); su salida alimenta §15 si se piden casos de prueba |

Énfasis transversales según lo pedido en la invocación:

- **Flujos de ciclo de vida con datos concretos** → vistas de runtime (§5.2 `04-runtime-views`) narradas de punta a punta con datos sintéticos coherentes con el modelo real, y matriz `TC-` + fixtures (§15) como guía para QA.
- **Snippets y estilos para desarrollo asistido (SDD)** → corpus curado según §13: uso canónico, puntos de extensión, convenciones de estilo observadas; cada snippet con procedencia (`ruta#Lx-Ly @versión`).
- **Guía de implementación de librerías** → ejemplos de integración extraídos de los proyectos de prueba/PoC reales de la solución.

---

# Restricciones

- **No modificar el código fuente del origen**: la ejecución es de solo lectura sobre `{origen}`; todo lo generado se escribe únicamente bajo `{destino}`.
- **No modificar la base de datos**: las cadenas de conexión provistas se usan solo para introspección de estructura y lecturas acotadas destinadas a construir ejemplos; nunca `DDL`/`DML`. Ante duda sobre el efecto de un comando, no se ejecuta.
- **Nunca credenciales ni PII en la documentación**: las cadenas de conexión no se copian a ningún entregable; los datos de ejemplo se sintetizan o seudonimizan con formato válido (§14/§15).
- No hacer commit, push ni pull request.
- No inventar: toda afirmación es trazable a la ia-db o a una fuente; lo inferido lleva `origin` y `confidence`; las contradicciones entre fuentes se reportan, no se resuelven en silencio (§12.4).
- No promover documentos a `approved`: quedan en `draft` para revisión humana.

---

# Diagramas típicos

Mapa de piezas (system-map), C4 de contexto y contenedores, vistas de runtime de los flujos clave, ER (dbml renderizado), flujo del pipeline documental (ia-db → manifiesto → piezas → consolidación).

---

# Resultado esperado

Un conjunto documental en `{destino}` conforme al Marco: navegable por humanos desde el índice maestro y operable por agentes desde `docs-manifest.yaml` + frontmatter, con la ia-db sincronizada, el gap documental explícito, las derivas reportadas y el origen intacto — listo para revisión humana y promoción a `approved`.
