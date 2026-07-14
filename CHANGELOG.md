# Changelog

Registro de cambios del framework de prompting. Formato basado en [Keep a Changelog](https://keepachangelog.com/es/); versionado semántico.

---

## [1.6.0] — 2026-07-14

### Agregado

- **Sección `## Uso por agentes automáticos` en las cinco guías**, adaptada al rol de cada una:
  - `Readme.md` (Guía Conceptual) — cómo el agente resuelve la cadena `Profile → RuleSet → Rules` al recibir un prompt y cuándo consultar la Referencia rápida.
  - `How-To.md` — flujo «De una idea a un Tool-Prompt» en 5 pasos (elegir capa de comportamiento → núcleo de 5 secciones → forma de Tool-Prompt → dónde guardarlo → actualizar artefactos).
  - `User-Guide.md` — validaciones de estructura que el agente aplica antes de ejecutar un prompt (núcleo de 5 secciones, entregables en `Solicitudes`, jerarquía, restricciones explícitas).
  - `Develop-Guide.md` — **checklist único de actualización** por pieza (Rule, RuleSet, Profile, Template, Example, Tool-Prompt): archivo + catálogos + tablas de la Guía Conceptual. Los «Después:» del How-To y los procesos de la propia guía ahora remiten acá.
  - `Token-Optimization.md` — prácticas que el agente aplica por defecto (carga proporcional, ia-db antes que el repositorio, recuperación incremental, sincronización al cierre).
- **`Examples/Example-Mantener-Guias.md`** — prompt de mantenimiento de las guías (agregar las secciones de agentes automáticos y revisar coherencia); referencia `RuleSet-Documentation` directo. Registrado en el catálogo de Examples y en la Guía Conceptual.
- **Carpeta `Referencias/`** — documentación de referencia externa al framework, fuente de características para prompts (no define comportamiento del agente). Incluye su `README.md` de catálogo y `Marco-Documentacion-Software-v1.md` (marco de documentación de soluciones de software multi-proyecto). Enlazada desde el README raíz.

### Cambiado

- **Deduplicación de catálogos**: la tabla de selección de Profiles (duplicada en `How-To.md` y `User-Guide.md`, con descripciones extensas en esta última) y la tabla de Tool-Prompts de `User-Guide.md` se reemplazan por referencias a sus catálogos (`Profiles/README.md` y `Tool-Prompts/README.md`) — un dato vive en un solo lugar.
- `Token-Optimization.md` ya no cita la ia-db de `Discord.Bot.Moderador.Core` como implementación de referencia (ruta externa al repositorio); la resolución es genérica: `<proyecto>/ia-db` o `/ia-db` según `Rule-Indexing.md`.
- Guía Conceptual: descripción de Examples ampliada (distingue `Example-*` pulidos de prompts reales) con enlace al catálogo completo.

### Corregido

- **Restos de «Resultado esperado»** en `User-Guide.md`: la estructura de prompt y los ejemplos completos aún mostraban la sección eliminada en 1.5.0; los entregables quedan dentro de `# Solicitudes`.

---

## [1.5.0] — 2026-07-14

### Cambiado

- **Núcleo de 5 secciones** como estructura canónica de todo prompt: `Contexto · Objetivo · Solicitudes · Restricciones · Framework (Profile)`. Se elimina la sección «Resultado esperado» (los entregables pasan a `Solicitudes` como tareas verificables con ruta) y «Observaciones» queda como nota opcional. Propagado a `Templates/` (con **pregunta guía embebida** por sección), `Tool-Prompts/` y `Examples/`.
- **RuleSets reorganizados como pura lista de Rules**: se quitan las secciones `## Énfasis` y `## Criterios de calidad` (su intención vive en los Profiles). Cada RuleSet carga **solo las Rules que su dominio necesita**, para que el consumo de tokens sea proporcional a la tarea. Nueva composición: Default = `All, Workflow, Evidences, Markdown`; Documentation = Default + `Documentation, Indexing, Agents`; Development = Default + `Agents`; Audit = Default + `Indexing, Agents`.
- **Tool-Prompts normalizados**: los cuatro «clásicos» (`Documentar-Servidor`, `Documentar-Docker`, `Actualizar-Documentacion`, `Revisar-Seguridad`) adoptan la cabecera `> **Invocación**` + tabla de parámetros y el núcleo de 5 secciones, igualando a los operativos de indexado.
- **Examples**: cabecera `> **Uso**` en todos; los `Example-*` reutilizan Profile; los prompts reales de análisis simple pasan a referenciar `RuleSet-Lean`.
- **Guía `Guides/Quick-User-Guide.md` renombrada a `Guides/How-To.md`** y generalizada: además de las frases por sección, incorpora una parte «Extender el framework» con esqueletos copy-paste para crear Rules, RuleSets, Profiles y Tool-Prompts.
- **README raíz** reescrito con el método de trabajo **idea → Tool-Prompt**.

### Agregado

- **`RuleSets/RuleSet-Lean.md`** — tier liviano (`Rule-All` + `Rule-Workflow`) para tareas simples o de análisis rápido.
- **`Templates/README.md`** (antes vacío) y **`Examples/README.md`** — catálogos de sus carpetas.

### Corregido

- **Carpeta fantasma `PromptFramework/Prompts/`**: no existía, pero README, Guía Conceptual y User-Guide la citaban. Se elimina toda referencia; los prompts predefinidos son Tool-Prompts en `/Tool-Prompts/`.

---

## [1.4.0] — 2026-07-12

### Agregado

- **Guía `Guides/Quick-User-Guide.md`** — guía rápida para escribir un prompt leyendo de arriba hacia abajo, sección por sección (`Contexto` → `Objetivo` → `Solicitudes` → `Restricciones` → `Framework` → `Resultado esperado` → `Observaciones`). Cada sección incluye definición, pregunta guía y frases de ejemplo para copiar y adaptar.
- `Templates/README.md` — placeholder de catálogo de la carpeta de Templates.

---

## [1.3.0] — 2026-07-12

### Agregado

- **READMEs de catálogo por carpeta** con tabla de selección rápida (jerarquía `Prompt → Profile → RuleSet → Rules`):
  - `Profiles/README.md` — catálogo de los 7 Profiles con RuleSet asociado y criterio de elección.
  - `RuleSets/Readme.md` — catálogo de los 4 RuleSets, qué extienden y cuándo usarlos.
  - `Rules/README.md` — catálogo de las 7 Rules atómicas y su ámbito de aplicación.
  - `Prompts/README.md` — placeholder de la carpeta de Prompts.
- **Ejemplos** (`/Examples/`):
  - `Consulta-Ciclo-Inicio-Server.md` — comportamiento de Docker ante ciclos de apagado/encendido del host y propuesta de servicio de energía ininterrumpida (UPS/SAI).
  - `Reconfiguracion-IP-Host.md` — reconfiguración de IP propia del contenedor `portainer` siguiendo el modelo de `discord-bot-moderador`.

---

## [1.2.0] — 2026-07-11

### Eliminado

- **`Parameters/`** (`Parameters.md`, `Repositories.md`, `Paths.md`, `Variables.md`): se elimina el sistema de parámetros. El contexto específico de cada proyecto se aporta ahora en el propio prompt; la jerarquía queda en `Prompt → Profile → RuleSet → Rules`.

### Cambiado

- Documentación, Profiles, Templates, Prompts, Examples y Tool-Prompts actualizados: removidas las secciones `## Parameters`/`## Parámetros` y toda referencia a la carpeta `Parameters/` (orden de búsqueda de la ia-db, límites de agentes y exclusiones de indexado ya no la citan).

---

## [1.1.0] — 2026-07-11

### Agregado

- **Tool-Prompts** (`/Tool-Prompts/`): prompts-herramienta de invocación en una línea.
  - `Iniciar-Indexado.md` — genera la base de conocimiento `ia-db` de uno o más proyectos. Modo proyecto (`<proyecto>/ia-db`) y modo workspace federado (`/ia-db` en la raíz, un índice por proyecto, subagentes en paralelo).
  - `Actualizar-Indexado.md` — sincronización incremental de una ia-db a partir de su manifiesto (solo índices afectados).
  - `Iniciar-Contexto.md` — arranque de chat con contexto mínimo (entrada + 1–2 índices del tema); autónomo: no carga Profiles ni RuleSets.
- **Profile `Knowledge-Indexing.md`**: formaliza la técnica ia-db (génesis: ia-db de Discord.Bot.Moderador.Core) con mejoras: entrada única, manifiesto de generación (alcance, fuentes, fecha, versión, prompt generador → base regenerable), federación multi-proyecto, presupuestos de tamaño por índice y exclusiones de escaneo (`.git`, dependencias, artefactos de build, binarios, la propia ia-db, patrones de `.gitignore`).
- **Rule `Rule-Workflow.md`**: ciclo diagnosticar → planificar → ejecutar → validar → reportar, con estructura fija de reporteo (Diagnóstico / Plan / Decisiones / Resultado / Pendientes).
- **Rule `Rule-Agents.md`**: asignación de subagentes autoajustada a la tarea (tabla de dimensionamiento, una responsabilidad por subagente, agregación con verificación).
- **Guía `Guides/Token-Optimization.md`**: principios y prácticas de optimización de consumo de tokens; racional de la técnica ia-db.
- `Parameters/Paths.md`: sección «Framework» con la base parametrizada y campo de exclusiones de indexado adicionales.
- `CHANGELOG.md` (este archivo).

### Cambiado

- **Referencias**: todas las citas de componentes usan rutas absolutas desde la raíz del workspace con base `/IA.Prompting.Templates` (88 referencias en 23 archivos). Convención documentada en `Develop-Guide.md`.
- **Rules condensadas** (1.172 → 309 líneas, −74 %): eliminadas secciones «Principios» redundantes y solapamientos entre reglas; cada concepto vive en una sola regla.
- **Profiles condensados** (1.008 → 327 líneas, −68 %): removido lo ya impuesto por las Rules (evidencias, base de conocimiento, generalidades de diagramas); listas convertidas en tablas por dimensión.
- La cadena por prompt (Profile + RuleSet + Rules) baja de ~1.430 a ~415 líneas (−71 %).
- READMEs y guías actualizados: Tool-Prompts, nuevo Profile, nueva guía y tablas de componentes.

### Eliminado

- `Rules/Rule-Tasks.md` y `Rules/Rule-Execution.md` — fusionadas en `Rule-Workflow.md` (RuleSets y guías actualizados).

---

## [1.0.0] — inicial

- Framework base: Parameters, Rules (7), RuleSets (4), Profiles (6), Templates, Prompts y Examples, con jerarquía Prompt → Profile → RuleSet → Rules.
