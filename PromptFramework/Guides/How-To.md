# How-To — Escribir prompts y extender el framework

Guía práctica de copiar y pegar. Dos partes:

- **Parte 1 — Escribir un prompt**: cómo completar cada sección del núcleo, con frases de arranque.
- **Parte 2 — Extender el framework**: esqueletos mínimos para crear una Rule, un RuleSet, un Profile o un Tool-Prompt.

Para el detalle conceptual, ver la [Guía de Usuario](User-Guide.md) y la [Guía de Desarrollo](Develop-Guide.md).

---

# Parte 1 — Escribir un prompt

Todo prompt usa el **núcleo de 5 secciones**, en este orden:

```
# Contexto → # Objetivo → # Solicitudes → # Restricciones → # Framework (Profile)
```

Los **entregables** no llevan sección propia: van dentro de `# Solicitudes` como tareas verificables con su ruta. Si hace falta una aclaración puntual de esa corrida, se agrega como nota al pie de `# Framework` (opcional).

Plantilla base: [`Prompt-Template.md`](../Templates/Prompt-Template.md).

## 1. Contexto

**Pregunta guía:** ¿Qué necesita saber el agente del estado actual para no asumir nada?

Empezá por el sujeto (el proyecto / el servidor / el repositorio) y describí el estado **en presente**. Evitá verbos de acción (van en Objetivo).

- «El proyecto administra un servidor Linux que aloja múltiples servicios Docker.»
- «La documentación actual está desactualizada y no refleja el estado real del servidor.»
- «El repositorio contiene la infraestructura de red del host, gestionada mediante `netplan`.»

## 2. Objetivo

**Pregunta guía:** ¿Qué debería ser verdad cuando el agente termine?

Una o dos frases. Arrancá con un verbo en infinitivo (Documentar, Analizar, Generar). Específico, verificable y acotado.

- «Generar documentación técnica actualizada que represente fielmente el estado del servidor.»
- «Conocer cómo responde Docker ante ciclos de apagado y encendido del servidor.»
- «Analizar y proponer un mecanismo de respuesta ante fallos de suministro de energía.»

## 3. Solicitudes

**Pregunta guía:** ¿Qué acciones atómicas y verificables cumplen el objetivo?

Una tarea por viñeta. Si una viñeta tiene varios «y», probablemente sean varias solicitudes. **Los entregables van acá**, con la ruta exacta cuando deban guardarse.

- «Construir un inventario del servidor.»
- «Identificar los servicios Docker en ejecución.»
- «Generar un informe en `Repos-Hosts/Host.Infra/Temas-Estudio/Contenedores-Ciclos.md`.»

## 4. Restricciones

**Pregunta guía:** ¿Qué podría hacer el agente que NO quiero que haga?

Son críticas cuando el agente toca sistemas reales. Definí siempre: si puede modificar archivos, si puede hacer commit/push, y qué queda fuera de alcance.

- «No modificar el estado del servidor; ejecutar únicamente comandos de lectura.»
- «No realizar commit, push ni pull request.»
- «No inventar información; toda afirmación debe estar respaldada por evidencias verificables.»

## 5. Framework → Profile

**Pregunta guía:** ¿De qué tipo es la tarea, y qué Profile la representa?

Referenciá un **Profile** (no las Rules directamente). Si ningún Profile encaja, referenciá un **RuleSet** (`Lean` para análisis simple).

```markdown
## Profile

Aplicar:
- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

Guía rápida de selección: la tabla — para qué sirve cada Profile y cuándo elegirlo — vive en el catálogo [`/IA/IA.Prompts/PromptFramework/Profiles/README.md`](../Profiles/README.md).

## Ejemplo mínimo completo

```markdown
# Contexto
El proyecto administra un servidor Linux con servicios Docker. La documentación
está desactualizada y no refleja el estado real.

# Objetivo
Generar documentación técnica que represente fielmente el estado actual del servidor.

# Solicitudes
- Construir un inventario del servidor.
- Identificar los servicios Docker en ejecución.
- Documentar la infraestructura y actualizar los índices.

# Restricciones
- No modificar el servidor; ejecutar únicamente comandos de lectura.
- No inventar información.

# Framework

## Profile
Aplicar:
- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

---

# Parte 2 — Extender el framework

Esqueletos mínimos para copiar y pegar. Convenciones y criterios completos: [Guía de Desarrollo](Develop-Guide.md).

## Crear una Rule

Una Rule = un dominio de comportamiento, atómica y transversal. Archivo: `Rules/Rule-[Dominio].md` (dominio en inglés, contenido en español).

```markdown
# Rule — [Nombre]

## Objetivo

[Qué comportamiento cubre esta regla, en 1–2 líneas.]

---

# [Sección principal]

- [Instrucción atómica y verificable.]
- [Otra instrucción; sin duplicar lo que ya dice otra Rule — referenciala.]
```

Después: completá el [checklist de actualización](Develop-Guide.md#uso-por-agentes-automáticos) de la fila **Rule**.

## Crear un RuleSet

Un RuleSet = **solo una lista de Rules**. El énfasis lo pone el Profile, no el RuleSet. Archivo: `RuleSets/RuleSet-[Dominio].md`.

```markdown
# RuleSet — [Nombre]

## Objetivo

[Tipo de tarea. Extiende Default con las Rules de su dominio.]

---

## Reglas

Default (`Rule-All`, `Rule-Workflow`, `Rule-Evidences`, `Rule-Markdown`) más [las que sumes]:

- `/IA/IA.Prompts/PromptFramework/Rules/Rule-All.md`
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-Workflow.md`
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-Evidences.md`
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-Markdown.md`
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-[Extra].md`
```

Después: completá el [checklist de actualización](Develop-Guide.md#uso-por-agentes-automáticos) de la fila **RuleSet**.

## Crear un Profile

Un Profile = comportamiento completo del agente para un rol. Referencia **un** RuleSet y define enfoque, objetivos y resultado esperado. Archivo: `Profiles/[Dominio]-[Tipo].md`.

```markdown
# Profile — [Nombre]

## Objetivo

[Rol o tipo de trabajo que configura este Profile.]

---

# Framework

## Rule Set

- `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-[Nombre].md`

---

# Enfoque

[Cómo debe encarar el trabajo el agente.]

---

# Objetivos específicos

[Qué debe identificar/producir; tablas por dimensión cuando ayuden.]

---

# Resultado esperado

[Entregables y estado final esperado.]
```

Después: completá el [checklist de actualización](Develop-Guide.md#uso-por-agentes-automáticos) de la fila **Profile**.

## Crear un Tool-Prompt

Un Tool-Prompt = prompt invocable en una línea, parametrizado con `{placeholders}`. Vive en `/IA/IA.Prompts/Tool-Prompts/[Categoria]/`, agrupado por dominio (`Indexado`, `Software`, `BasesDatos`, `Docker`, `Infra`, `Seguridad`; catálogo en [`Tool-Prompts/README.md`](../../Tool-Prompts/README.md)). Archivo: `[Verbo]-[Objeto].md`.

```markdown
# Tool-Prompt — [Nombre]

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/[Categoria]/[archivo].md en {parametro}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{parametro}` | [Qué representa] | [Qué hacer: pedirlo, inferirlo, valor por defecto] |

---

# Contexto
[Estado actual, usando {parametro}.]

# Objetivo
[Qué debe ser verdad al terminar.]

# Solicitudes
- [Tareas atómicas; entregables con su ruta.]

# Restricciones
- [Qué no hacer.]

# Framework

## Profile
Aplicar:
- `/IA/IA.Prompts/PromptFramework/Profiles/[Profile].md`
```

Después: completá el [checklist de actualización](Develop-Guide.md#uso-por-agentes-automáticos) de la fila **Tool-Prompt**.

---

## Uso por agentes automáticos

Flujo «De una idea a un Tool-Prompt», definido en el [README raíz](../../README.md): el usuario plantea una idea en lenguaje natural y el agente construye el prompt siguiendo esta guía.

| Paso | Acción | Fuente |
|------|--------|--------|
| 1 | Elegir la capa de comportamiento: el Profile que represente la tarea, o `RuleSet-Lean` si es un análisis simple | Catálogo `/IA/IA.Prompts/PromptFramework/Profiles/README.md` |
| 2 | Completar el núcleo de 5 secciones respondiendo la pregunta guía de cada una; los entregables van dentro de `# Solicitudes`, con su ruta | Parte 1 de esta guía |
| 3 | Si la tarea es recurrente, darle forma de Tool-Prompt: parámetros `{placeholder}`, cabecera de invocación y qué hacer cuando un parámetro no se indica | Esqueletos de la Parte 2 |
| 4 | Proponer dónde guardarlo: `/IA/IA.Prompts/Tool-Prompts/` (herramienta reutilizable) o `/IA/IA.Prompts/PromptFramework/Examples/` (caso puntual que quedó funcionando) | README raíz |
| 5 | Actualizar los artefactos de la pieza creada | [Checklist de la Guía de Desarrollo](Develop-Guide.md#uso-por-agentes-automáticos) |

No agregar secciones fuera del núcleo (en particular, ninguna sección «Resultado esperado» separada) ni referenciar Rules directamente desde el prompt.

---

**Ver también:** [Guía de Usuario](User-Guide.md) · [Guía de Desarrollo](Develop-Guide.md) · [Templates](../Templates/README.md) · [Examples](../Examples/README.md)
