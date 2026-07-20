# Changelog

Registro de cambios del framework de prompting. Formato basado en [Keep a Changelog](https://keepachangelog.com/es/); versionado semántico.

---

## [1.11.1] — 2026-07-19

### Corregido

- **Actualización de rutas pendiente de 1.11.0**: se reescriben todas las referencias a las rutas anteriores en 13 archivos — cabeceras `> **Invocación**` de los cinco Tool-Prompts movidos, `Tool-Prompts/README.md`, `README.md` raíz, `PromptFramework/README.md`, las cuatro guías de `PromptFramework/Guides/` y `Profiles/Knowledge-Indexing.md`. `Tool-Prompts/Indexado/` pasa a `Tool-Prompts/Indexado-Documentado/`, `Software/Documentar-Fuentes-Software.md` a `Indexado-Documentado/Crear-Documentacion-Fuente-Software.md`, `Software/Actualizar-Documentacion.md` a `Indexado-Documentado/Actualizar-Documentacion.md`, `Infra/Documentar-Servidor.md` a `Infra/Crear-Documentacion-Server.md` e `Infra/Revisar-Seguridad.md` a `Infra/Revisar-Seguridad-Server.md`. El repositorio queda sin referencias rotas.
- **Títulos de los archivos renombrados**: el `#` de nivel 1 de `Crear-Documentacion-Fuente-Software.md`, `Crear-Documentacion-Server.md` y `Revisar-Seguridad-Server.md` seguía nombrando el archivo viejo; ahora coincide con el nombre del archivo.

### Cambiado

- **Catálogo `Tool-Prompts/README.md`**: la sección «Indexado» pasa a «Indexado y documentación» y absorbe las filas de `Crear-Documentacion-Fuente-Software` y `Actualizar-Documentacion`, que estaban listadas bajo «Software» pese a haberse movido de carpeta. «Software» queda con `Derivar-Casos-Prueba`. Se redefinen los dominios de ambas carpetas en la tabla de organización y en el árbol de estructura de `PromptFramework/README.md`.
- **Tabla de Tool-Prompts de la Guía Conceptual** (`Guides/Readme.md`): suma la fila de `Infra/Actualizar-Documentacion-Server.md`, que faltaba desde su alta en 1.11.0.

---

## [1.11.0] — 2026-07-19

### Agregado

- **Tool-Prompt `Tool-Prompts/Infra/Actualizar-Documentacion-Server.md`** — sincronizar la documentación existente de un servidor con su estado real: corregir lo que cambió, completar lo que falta, retirar lo que ya no existe y preservar lo válido. Cierra el par crear/actualizar en `Infra/`, en línea con el par ya existente de indexado. Parámetros: `{destino}` (ubicación de la documentación) y `{servidor}` (deducible de la propia documentación). Profile: Infrastructure-Documentation.

### Cambiado

- **Nomenclatura de los Tool-Prompts de `Infra/` por verbo explícito y objeto acotado**: `Documentar-Servidor.md` → `Crear-Documentacion-Server.md` (la invocación pasa a `de {servidor} en {destino}`) y `Revisar-Seguridad.md` → `Revisar-Seguridad-Server.md`. El sufijo `-Server` deja explícito el objeto auditado y evita la ambigüedad con `Seguridad/Auditoria-Seguridad.md`, que audita un portal web desde su URL.
- **Fusión de `Indexado/` y la rama documental de `Software/` en `Tool-Prompts/Indexado-Documentado/`**: la carpeta agrupa el ciclo completo de indexar y documentar fuentes — `Iniciar-Contexto.md`, `Iniciar-Indexado.md`, `Actualizar-Indexado.md`, `Actualizar-Documentacion.md` y `Crear-Documentacion-Fuente-Software.md` (antes `Software/Documentar-Fuentes-Software.md`). `Software/` queda con `Derivar-Casos-Prueba.md`. La carpeta forma parte de la ruta de invocación, que pasa a `/Tool-Prompts/Indexado-Documentado/...`.
- **Catálogo `Tool-Prompts/README.md`**: la tabla de la categoría Infraestructura refleja los nombres nuevos y suma `Actualizar-Documentacion-Server`.

### Pendiente

- El rebase de rutas de esta reorganización quedó incompleto: las cabeceras `> **Invocación**` de los archivos movidos, la tabla de carpetas y las secciones Indexado/Software de `Tool-Prompts/README.md`, el `README.md` raíz, las guías de `PromptFramework/Guides/` y `Profiles/Knowledge-Indexing.md` siguen citando las rutas anteriores. Se resuelve en una entrada posterior.

---

## [1.10.0] — 2026-07-18

### Agregado

- **Profile `Profiles/Study-Guide-Documentation.md`** — construir guías de estudio: cuerpos documentales formativos sobre una temática, organizados como recorrido de aprendizaje y no como colección de fichas. Fija primero el **marco de referencia** en tres ejes (escenarios, contextos y actores) que el Prompt instancia según el tema, y recién después desarrolla un documento por unidad temática, todos con la misma estructura interna (definición → aplicación por escenario → ejemplos → preguntas guía → criterios de calidad → plantilla comentada). Completan el entregable el mapa conceptual de entrada («estoy acá → qué aplico»), los métodos y marcos alternativos del dominio, los anexos y un README con la ruta de lectura sugerida. La temática, el alcance y el destino los aporta el Prompt.
- **RuleSet `RuleSets/RuleSet-Study-Guide.md`** — Documentation + `Rule-Dual-Audience` + `Rule-Narrative-Voice`: el entregable es prosa extensa destinada a que el lector forme criterio, de modo que suma la doble audiencia (humana y de agentes) y la voz de autoría a las reglas de documentación.
- Alta en los tres catálogos: `Profiles/README.md` (tabla, guía de elección y nota de RuleSets), `RuleSets/Readme.md` (tabla y guía de elección) y las tablas de RuleSets y Profiles de la Guía Conceptual (`Guides/Readme.md`).

---

## [1.9.0] — 2026-07-17

### Agregado

- **Rule `Rules/Rule-Narrative-Voice.md`** — regla atómica y reutilizable que ajusta la voz de la prosa de los entregables: técnica y formal, con ritmo y criterio de autoría humana, eliminando los patrones que delatan texto generado en serie (muletillas de relleno, conectores decorativos encadenados, ritmo de frase uniforme, listas donde va prosa, cierres genéricos, restatear el título de la sección). Aplica solo a las zonas de prosa; las zonas estructuradas (frontmatter, IDs, tablas, matrices, anclas) se mantienen rígidas por `Rule-Dual-Audience` / `Rule-Markdown`. Se suma a `RuleSet-Security-Audit`, con alta en `Rules/README.md`, la Guía Conceptual y la sección «Voz y redacción» del Profile `Web-Security-Audit`.
- **Tool-Prompt `Tool-Prompts/Seguridad/Auditoria-Seguridad.md`** — auditoría de seguridad de un sistema web autenticado **desde su URL pública**, no desde el código fuente: reconocimiento de superficie expuesta, mapeo de funcionalidades y controles de acceso con una cuenta autorizada, pruebas por categoría del catálogo OWASP (Top 10 / WSTG) priorizando técnicas pasivas y de solo lectura, análisis de riesgo (severidad, CVSS, impacto) e informe técnico como **un único archivo Markdown** en `{destino}`, con tabla de contenidos al inicio y anexos embebidos al final del mismo documento. Parámetros: `{URL}`, `{Usuario}`, `{Clave}`, `{destino}` (ruta del `.md`).
- **Cadena de framework para auditoría web**: `Rules/Rule-Security-Testing.md` → `RuleSets/RuleSet-Security-Audit.md` → `Profiles/Web-Security-Audit.md`, con alta en los tres catálogos y en la Guía Conceptual. Las restricciones de autorización (alcance, no destructividad, enmascarado de credenciales, no inventar hallazgos) las fija el Profile.

### Cambiado

- **Agrupación de `Tool-Prompts/` en carpetas por dominio**: `Indexado/`, `Software/`, `BasesDatos/`, `Docker/`, `Infra/` y `Seguridad/`. La carpeta pasa a formar parte de la ruta de invocación (`/Tool-Prompts/Indexado/Iniciar-Contexto.md`); se rebasan las cabeceras `> **Invocación**` de los 10 Tool-Prompts movidos y todas las referencias en READMEs, guías y `Profiles/Knowledge-Indexing.md`. La convención de nombres pasa a `[Categoria]/[Verbo]-[Objeto].md` en `Guides/Develop-Guide.md` y `Guides/How-To.md`.
- **`Infra/` y `Seguridad/` se separan por objeto auditado, no por disciplina**: `Infra/Revisar-Seguridad.md` revisa la postura de un servidor o red desde adentro (Infrastructure-Audit); `Seguridad/Auditoria-Seguridad.md` audita un portal web autenticado desde su URL (Web-Security-Audit). Criterio documentado en `Tool-Prompts/README.md`.
- **Catálogo `Tool-Prompts/README.md`**: la tabla única pasa a una tabla por categoría, más una tabla de carpetas con su dominio.

---

## [1.8.1] — 2026-07-16

### Cambiado

- **Base de rutas del framework**: el repositorio se renombró a `IA.Prompts` y se movió bajo `/IA`, por lo que todas las referencias absolutas pasan de `/IA.Prompting.Templates` a `/IA/IA.Prompts` (165 referencias en 41 archivos). La convención sigue siendo la misma: rutas absolutas desde la raíz del workspace, documentada en `Guides/Develop-Guide.md`.
- `PromptFramework/README.md`: la raíz del árbol de estructura y `Tool-Prompts/README.md`: el ejemplo de indexado federado, ambos usan el nombre nuevo `IA.Prompts`.

### Corregido

- **Catálogo de Examples**: `Examples/README.md` listaba 12 ejemplos de los que sólo 2 existían en el repositorio (los prompts reales migraron a los repositorios de su dominio). Se eliminan las 10 filas rotas y el catálogo queda en `Example-Auditoria` y `Example-Mantener-Guias`. Se sincronizan la tabla de Examples de `Guides/Readme.md` y el «Ejemplo 3» de `Guides/User-Guide.md`, que citaban `Example-Documentar-Infra.md` (inexistente). El repositorio queda sin referencias rotas.

---

## [1.8.0] — 2026-07-14

### Agregado

- **Tool-Prompt `Tool-Prompts/Documentar-Fuentes-Software.md`** — evalúa y documenta una pieza de software de cualquier escala (proyecto, solución multi-proyecto, workspace o conjunto de soluciones: librerías, webs, REST APIs, apps móviles, bases de datos, batch) conforme al Marco de Documentación. Estrategia en 5 fases: indexar (`{destino}/ia-db` vía Knowledge-Indexing) → clasificar (`system-map` + `docs-manifest.yaml` con `type` por pieza, Marco §7) → documentar por pieza con subagentes → nivel solución (C4, runtime views, ADRs reconstruidos) → consolidar (gap documental + sincronización de la ia-db). Parámetros: `{origen}`, `{destino}` (default `<origen>.Documentacion`), `{conexiones}` (solo lectura) y `{énfasis}` (flujos QA con datos, snippets/SDD, guías de implementación).
- **Profile `Profiles/Solution-Documentation.md`** (RuleSet Solution-Documentation) — orquestador documental: aplica el Marco como **política raíz** (§2.2), define la estructura de destino (`{destino}/ia-db` + `<nombre>-docs/` según §5.2, con adaptación declarada: la doc de pieza se espeja en `pieces/<pieza>/` porque el origen no se modifica), delega por `type` de pieza en los Profiles especializados (`Knowledge-Indexing`, `Database-Documentation`, `QA-Test-Design`) y fija puntos de control de deriva por fase.
- **Rule `Rules/Rule-Dual-Audience.md`** — documentación de doble audiencia: cara humana (resumen ejecutivo, narrativa de flujos de punta a punta con datos sintéticos, analogías, preguntas guía) y cara agente (frontmatter YAML, IDs estables, anclas predecibles, diagramas como código, bloques `entradas/salidas/validaciones`, snippets con procedencia), con coherencia entre caras (única fuente de verdad).
- **Rule `Rules/Rule-Drift-Control.md`** — control de deriva de agentes: contrato de ejecución (objetivo, alcance, rutas de escritura, presupuesto), **sensores de deriva** (alcance, escritura, objetivo, invención, presupuesto, profundidad) con acción por señal, puntos de control por fase, re-anclaje/corte y reporte de derivas.
- **RuleSet `RuleSets/RuleSet-Solution-Documentation.md`** — Documentation + `Rule-Dual-Audience` + `Rule-Drift-Control`; mantiene el consumo de tokens proporcional (las tareas de documentación simples siguen usando Documentation).
- Todo registrado en `Rules/README.md`, `RuleSets/Readme.md`, `Profiles/README.md`, `Tool-Prompts/README.md`, las tablas de la Guía Conceptual y el uso rápido del README raíz.

### Cambiado

- `Profiles/README.md`: la nota final sobre RuleSets reconoce la excepción de `Solution-Documentation` y su rol de orquestación formalizada.

### Corregido

- `RuleSets/RuleSet-Documentation.md`: la enumeración de Profiles que aplican el RuleSet estaba desactualizada desde 1.7.0 — se agregan `Database-Documentation` y `QA-Test-Design`, y se referencia `RuleSet-Solution-Documentation` como extensión para documentación orquestada.

---

## [1.7.0] — 2026-07-14

### Agregado

- **Profile `Profiles/Database-Documentation.md`** (RuleSet Documentation) — documenta una base de datos de forma regenerable: introspección del esquema real (`information_schema` / catálogo) → diccionario de datos + modelo ER como código dbml, enriquecidos con semántica de negocio, con PII y retención marcadas, **solo lectura y sin credenciales ni datos**. Instancia los `doc_type` `data-dictionary` y `er-model` del manifiesto (Marco §12.2).
- **Profile `Profiles/QA-Test-Design.md`** (RuleSet Documentation) — deriva **casos y datos de prueba desde el modelo de datos**: a partir del diccionario + ER genera una matriz de casos `TC-` trazables a `RF-`/`RNF-` (equivalencia, valores de borde, integridad referencial, casos negativos) y **fixtures sintéticos PII-safe**, con reporte de gaps de cobertura. Consume `Database-Documentation` como fuente; instancia el `doc_type` `test-data-matrix` (Marco §12.2).
- **Tool-Prompts `Tool-Prompts/Documentar-BaseDatos.md` y `Tool-Prompts/Derivar-Casos-Prueba.md`** — invocación de una línea que reutilizan los Profiles anteriores; siguen el núcleo de 5 secciones y la cabecera `> **Invocación**`.
- Los dos Profiles y los dos Tool-Prompts quedan registrados en `Profiles/README.md`, `Tool-Prompts/README.md` y las tablas de la Guía Conceptual.

### Cambiado

- **`Referencias/Marco-Documentacion-Software-v1.md` → v2.2.0** (desde 2.0.0): añade §13 (extracción de piezas de código representativas: transclusión / copia verificada con procedencia), §14 (documentación de BD → diccionario + ER en dbml) y §15 (derivación de casos y datos de prueba desde el modelo de datos, para QA); fichas `A.18 dbml` y `A.19 ISO/IEC/IEEE 29119`; nuevos `doc_type` (`data-dictionary`, `er-model`, `test-data-matrix`) y artefactos en `03-data/`; validaciones de CI (dbml renderizable, frescura de snippets). El checklist operativo pasa a §16. Los Profiles y Tool-Prompts nuevos operacionalizan §14 y §15.

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
