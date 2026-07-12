# Changelog

Registro de cambios del framework de prompting. Formato basado en [Keep a Changelog](https://keepachangelog.com/es/); versionado semántico.

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
