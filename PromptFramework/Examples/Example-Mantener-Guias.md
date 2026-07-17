# Mantenimiento de las guías del framework

> **Uso**: ejecutá este prompt tal cual para agregar las secciones de uso por agentes automáticos a las guías y revisar su coherencia. Si las guías cambian de composición, actualizá las viñetas de la segunda solicitud.

---

# Contexto

El repositorio `/IA/IA.Prompts` contiene un framework de ingeniería de prompts con jerarquía `Prompt → Profile → RuleSet → Rules`. Las cinco guías de `/IA/IA.Prompts/PromptFramework/Guides/` documentan el framework:

| Guía | Rol actual |
|------|-----------|
| `Readme.md` | Guía conceptual: arquitectura, filosofía y componentes |
| `How-To.md` | Copy-paste: escribir prompts y extender el framework |
| `User-Guide.md` | Cómo usar el framework |
| `Develop-Guide.md` | Cómo extender y mantener el framework |
| `Token-Optimization.md` | Minimizar el consumo de contexto (técnica ia-db) |

Las guías están escritas para lectura humana (trabajo manual). No declaran de forma explícita cómo un agente automático debe servirse de cada una como marco de ejecución, y presentan inconsistencias menores entre sí (p. ej., `User-Guide.md` muestra una estructura de prompt con sección `# Resultado esperado` separada, mientras `How-To.md` y `Develop-Guide.md` establecen que los entregables van dentro de `# Solicitudes`).

---

# Objetivo

Que cada guía sirva simultáneamente como marco operativo para agentes automáticos y como referencia de trabajo manual, y que las cinco guías y el `README.md` raíz sean coherentes entre sí en estructura, terminología y referencias cruzadas.

---

# Solicitudes

- Leer las cinco guías de `/IA/IA.Prompts/PromptFramework/Guides/` y el `README.md` raíz del repositorio.
- Agregar a cada guía una sección `## Uso por agentes automáticos`, integrada al tono y formato del documento (tablas sobre prosa), adaptada a su rol:
  - `Readme.md`: cómo un agente resuelve la cadena `Profile → RuleSet → Rules` al recibir un prompt y cuándo consultar la referencia rápida.
  - `How-To.md`: cómo un agente construye un Tool-Prompt a partir de una idea del usuario (flujo «De una idea a un Tool-Prompt» del `README.md` raíz).
  - `User-Guide.md`: cómo un agente que recibe un prompt valida el núcleo de 5 secciones y selecciona Profile o RuleSet antes de ejecutar.
  - `Develop-Guide.md`: checklist verificable que un agente debe completar al crear o modificar una pieza (archivo nuevo + RuleSets afectados + catálogos + tablas de la Guía Conceptual).
  - `Token-Optimization.md`: qué prácticas debe aplicar el agente por defecto (carga proporcional a la tarea, ia-db antes de explorar el repositorio) sin que el usuario las pida.
- Revisar la coherencia entre las cinco guías y el `README.md` raíz, y corregir:
  - Estructura del prompt: unificar en el núcleo de 5 secciones — entregables dentro de `# Solicitudes`; eliminar `# Resultado esperado` de la estructura y de los ejemplos de `User-Guide.md`.
  - Contenido duplicado (tablas de selección de Profile, catálogos de componentes): un dato vive en un solo lugar; el resto lo referencia.
  - Proceso de actualización al extender el framework: alinear lo que dicen `How-To.md` (catálogos por carpeta) y `Develop-Guide.md` (tablas de la Guía Conceptual), definiendo una única lista de artefactos a actualizar.
  - Referencias cruzadas: verificar que todos los enlaces y rutas (relativas y absolutas con base `/IA/IA.Prompts`) apunten a archivos existentes, incluyendo mayúsculas (`README.md` vs `Readme.md`).
- Reportar al final un resumen por archivo: qué sección se agregó y qué inconsistencias se corrigieron.

---

# Restricciones

- Modificar únicamente los documentos de `PromptFramework/Guides/` y, solo si una corrección de coherencia lo exige, el `README.md` raíz. No modificar Rules, RuleSets, Profiles, Templates, Examples ni Tool-Prompts.
- Principio de mínima intervención: no reescribir contenido correcto ni cambiar la estructura general de cada guía.
- Respetar las convenciones del framework: contenido en español, separadores `---` entre secciones principales, tabla de contenidos actualizada si el documento supera tres secciones, rutas absolutas con base `/IA/IA.Prompts` en las referencias destinadas a agentes.
- No duplicar contenido entre guías: si la sección nueva necesita material que ya existe en otra guía, referenciarlo.
- No inventar comportamiento del framework: toda afirmación de las secciones nuevas debe derivarse de los documentos existentes.
- No realizar commit, push ni pull request.

---

# Framework

## Rule Set

Aplicar:

- `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-Documentation.md`

> Nota: se referencia el RuleSet directo porque ningún Profile existente cubre el mantenimiento de la documentación del propio framework.
