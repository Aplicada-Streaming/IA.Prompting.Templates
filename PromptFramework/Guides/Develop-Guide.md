# Guía de Desarrollo — Prompt Framework

## Tabla de contenidos

- [Introducción](#introducción)
- [Principios arquitectónicos](#principios-arquitectónicos)
- [Cómo agregar nuevas Rules](#cómo-agregar-nuevas-rules)
- [Cómo crear nuevos RuleSets](#cómo-crear-nuevos-rulesets)
- [Cómo diseñar nuevos Profiles](#cómo-diseñar-nuevos-profiles)
- [Cómo construir Templates](#cómo-construir-templates)
- [Cómo escribir Examples](#cómo-escribir-examples)
- [Convenciones](#convenciones)
- [Organización recomendada](#organización-recomendada)
- [Criterios de diseño](#criterios-de-diseño)
- [Uso por agentes automáticos](#uso-por-agentes-automáticos)

---

## Introducción

Esta guía explica cómo extender y mantener el Prompt Framework.

Está orientada a quienes necesiten agregar nuevas reglas, crear nuevos RuleSets, diseñar nuevos Profiles, construir Templates o escribir Examples.

Antes de extender el framework, comprender su arquitectura consultando la [Guía Conceptual](Readme.md).

---

## Principios arquitectónicos

Todo nuevo componente deberá respetar los siguientes principios.

### Responsabilidad única

Cada componente tiene una única responsabilidad.

- Una Rule define el comportamiento para un dominio específico.
- Un RuleSet agrupa reglas relacionadas para un tipo de tarea.
- Un Profile configura el comportamiento completo del agente para un rol específico.

### Composición sobre duplicación

No duplicar instrucciones. Componer componentes existentes.

Si una instrucción ya existe en una Rule, referenciarla. No copiarla en otro componente.

### Independencia del proyecto

Las Rules, RuleSets y Profiles no deben contener referencias a proyectos específicos.

El contexto específico de cada proyecto se aporta en el propio Prompt.

### Jerarquía de composición

Respetar siempre la jerarquía: Prompt → Profile → RuleSet → Rules.

No saltar niveles. No referenciar Rules directamente desde Prompts.

---

## Cómo agregar nuevas Rules

### Cuándo crear una nueva Rule

Crear una nueva Rule cuando:

- exista un dominio de comportamiento claramente diferenciado;
- el dominio sea transversal a múltiples Profiles;
- las instrucciones existentes no cubran el comportamiento necesario.

No crear una Rule cuando:

- el comportamiento pueda expresarse en una Rule existente;
- el comportamiento sea específico de un solo Profile;
- el dominio sea demasiado pequeño para justificar un archivo separado.

### Estructura de una Rule

```markdown
# Rule — [Nombre]

## Objetivo

[Descripción del dominio que cubre esta regla]

---

# [Sección principal 1]

[Instrucciones para este dominio]

---

# [Sección principal 2]

[Instrucciones adicionales]
```

Escribir las Rules de forma compacta: bullets y tablas sobre prosa, sin sección final de «Principios» que repita el cuerpo, y sin duplicar instrucciones ya presentes en otra Rule (referenciarla).

### Convenciones de nomenclatura

- Nombre de archivo: `Rule-[Dominio].md`
- Ejemplos: `Rule-Security.md`, `Rule-Git.md`, `Rule-Testing.md`
- El nombre del dominio debe ser en inglés.
- El título del documento debe estar en español.

### Proceso

1. Verificar que no existe una Rule equivalente.
2. Crear el archivo en `/IA/IA.Prompts/PromptFramework/Rules/`.
3. Documentar la Rule con estructura completa.
4. Completar el [checklist de actualización](#uso-por-agentes-automáticos) de la fila **Rule**.

---

## Cómo crear nuevos RuleSets

### Cuándo crear un nuevo RuleSet

Crear un nuevo RuleSet cuando:

- exista un tipo de tarea con requisitos de comportamiento claramente diferenciados;
- el RuleSet requiera un conjunto de reglas distinto al de los RuleSets existentes.

No crear un nuevo RuleSet cuando:

- un RuleSet existente cubra suficientemente el caso de uso;
- la diferencia sea solo de énfasis y no de reglas.

### Estructura de un RuleSet

Un RuleSet es **solo una lista de Rules** (sin `## Énfasis` ni `## Criterios de calidad`: eso lo define el Profile). Carga solo las Rules que su dominio necesita.

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

Composición actual de los RuleSets: ver [`RuleSets/Readme.md`](../RuleSets/Readme.md).

### Convenciones de nomenclatura

- Nombre de archivo: `RuleSet-[Dominio].md`
- Ejemplos: `RuleSet-Security.md`, `RuleSet-Testing.md`
- El nombre del dominio debe ser en inglés.

### Proceso

1. Identificar las Rules que aplican para este dominio.
2. Crear el archivo en `/IA/IA.Prompts/PromptFramework/RuleSets/`.
3. Documentar el RuleSet referenciando todas las Rules aplicables.
4. Completar el [checklist de actualización](#uso-por-agentes-automáticos) de la fila **RuleSet**.

---

## Cómo diseñar nuevos Profiles

### Cuándo crear un nuevo Profile

Crear un nuevo Profile cuando:

- exista un rol o tipo de trabajo claramente diferenciado;
- el Profile requiera un comportamiento específico que no cubra ningún Profile existente;
- el Profile vaya a reutilizarse en múltiples Prompts.

No crear un nuevo Profile cuando:

- un Profile existente cubra suficientemente el caso de uso;
- el comportamiento sea específico de un único Prompt.

### Estructura de un Profile

```markdown
# Profile — [Nombre]

## Objetivo

[Descripción del rol o tipo de trabajo que configura este Profile]

---

# Framework

## Rule Set

Aplicar:

- `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-[Nombre].md`

---

# Enfoque

[Descripción del enfoque de trabajo del agente con este Profile]

---

# Objetivos específicos

[Lista de objetivos que el agente deberá perseguir]

---

# [Secciones específicas del dominio]

[Instrucciones específicas para este tipo de trabajo]

---

# Resultado esperado

[Descripción de los entregables esperados al finalizar]
```

### Convenciones de nomenclatura

- Nombre de archivo: `[Dominio]-[Tipo].md`
- Ejemplos: `Infrastructure-Security.md`, `Repository-Analysis.md`
- El nombre debe reflejar claramente el dominio y el tipo de trabajo.

### Proceso

1. Identificar el RuleSet más apropiado para el Profile.
2. Crear el archivo en `/IA/IA.Prompts/PromptFramework/Profiles/`.
3. Documentar todas las secciones del Profile.
4. Completar el [checklist de actualización](#uso-por-agentes-automáticos) de la fila **Profile**.

---

## Cómo construir Templates

### Propósito de los Templates

Los Templates son estructuras vacías que guían la construcción de nuevos Prompts.

Un Template debe:

- mostrar todos los campos necesarios;
- incluir instrucciones sobre cómo completar cada campo;
- referenciar Profiles (no Rules directamente);
- ser fácil de copiar y completar.

### Estructura de un Template

Núcleo de **5 secciones**. Los entregables van dentro de `# Solicitudes` (no hay sección «Resultado esperado» separada). Cómo completar cada sección: [How-To](How-To.md).

```markdown
# Contexto

[Estado actual del problema, en presente.]

---

# Objetivo

[Qué debe ser verdad al terminar.]

---

# Solicitudes

- [Tarea atómica y verificable.]
- [Entregable con su ruta: «Generar el informe en `<ruta>`.»]

---

# Restricciones

- [Qué no debe hacer el agente.]

---

# Framework

## Profile

Aplicar:
- `/IA/IA.Prompts/PromptFramework/Profiles/[Profile].md`
```

### Convenciones

- Nombre de archivo: `Prompt-[Nombre].md`
- El nombre debe describir el propósito del Template.

---

## Cómo escribir Examples

### Propósito de los Examples

Los Examples son Prompts completos y funcionales que demuestran el uso del framework en escenarios reales.

Un Example debe:

- ser un Prompt listo para ejecutar (con mínimas modificaciones);
- utilizar correctamente la jerarquía del framework;
- demostrar un caso de uso representativo;
- incluir valores concretos.

### Diferencia entre Template y Example

| | Template | Example |
|-|----------|---------|
| Propósito | Estructura vacía para construir prompts | Prompt funcional completo |
| Contenido | Campos vacíos con instrucciones | Valores concretos |
| Audiencia | Usuarios que construyen prompts | Usuarios que aprenden el framework |

### Convenciones

- Nombre de archivo: `Example-[Descripción].md`
- El nombre debe describir el escenario documentado.
- Siempre incluir el contexto completo del escenario.

---

## Convenciones

### Nomenclatura

| Componente | Convención | Ejemplo |
|------------|------------|---------|
| Rule | `Rule-[Dominio].md` | `Rule-Security.md` |
| RuleSet | `RuleSet-[Dominio].md` | `RuleSet-Audit.md` |
| Profile | `[Dominio]-[Tipo].md` | `Infrastructure-Audit.md` |
| Template | `Prompt-[Nombre].md` | `Prompt-Template.md` |
| Tool-Prompt | `[Verbo]-[Objeto].md` (en `/IA/IA.Prompts/Tool-Prompts/[Categoria]/`) | `Indexado/Iniciar-Contexto.md` |
| Example | `Example-[Descripción].md` | `Example-Auditoria.md` |

### Idioma

- Nombres de archivos: español para Tool-Prompts y Examples, inglés para Rules y RuleSets.
- Contenido de todos los documentos: español.
- Títulos: español.

### Estructura de documentos

Todo documento debe:

- comenzar con un título de nivel `#`;
- incluir una sección `## Objetivo`;
- utilizar separadores `---` entre secciones principales;
- incluir una tabla de contenidos cuando el documento supere tres secciones principales.

### Referencias cruzadas

Al referenciar componentes del framework desde prompts, perfiles o reglas, utilizar siempre rutas absolutas desde la raíz del workspace. La base de la URL incluye el repositorio `/IA/IA.Prompts`:

```
`/IA/IA.Prompts/PromptFramework/Rules/Rule-All.md`
`/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-Documentation.md`
`/IA/IA.Prompts/PromptFramework/Profiles/Repository-Documentation.md`
`/IA/IA.Prompts/Tool-Prompts/Indexado/Iniciar-Contexto.md`
```

Si el repositorio cambia de ubicación, actualizar las referencias de los documentos.

Los enlaces Markdown de navegación (`[texto](ruta relativa)`) dentro de un mismo repositorio pueden permanecer relativos: están destinados a la lectura humana, no a la resolución del agente.

---

## Organización recomendada

```
PromptFramework/
├── Rules/                  # Reglas atómicas (una por dominio)
├── RuleSets/               # Listas de reglas (Lean + Default + especializados)
├── Profiles/               # Configuraciones de comportamiento del agente
├── Templates/              # Estructuras para construir prompts
├── Examples/               # Prompts funcionales completos
└── Guides/                 # Documentación del framework

Tool-Prompts/               # (raíz del repositorio) Prompts-herramienta de invocación directa
├── Indexado/               # ia-db y arranque de contexto
├── Software/               # Código fuente: documentación de soluciones y QA
├── BasesDatos/             # Estructura de bases de datos
├── Docker/                 # Infraestructura de contenedores
├── Infra/                  # Servidores y redes (documentación y seguridad de infraestructura)
└── Seguridad/              # Auditoría de seguridad de sistemas web expuestos
```

Los Tool-Prompts deben ser parametrizables mediante placeholders `{parametro}`, invocables en una línea y declarar qué hacer cuando un parámetro no se indica. Cada uno vive en la carpeta de su dominio, y esa carpeta forma parte de la ruta de invocación.

### Principio de mínima intervención

Al extender el framework:

- modificar únicamente los archivos necesarios;
- no alterar componentes que no requieran cambios;
- actualizar siempre la documentación afectada.

---

## Criterios de diseño

### Atomicidad

Las Rules deben ser atómicas: una Rule, un dominio, una responsabilidad.

Si una Rule cubre demasiados temas, dividirla.

### Cohesión

Los RuleSets deben agrupar reglas relacionadas.

No mezclar dominios no relacionados en un mismo RuleSet.

### Extensibilidad

El framework está diseñado para crecer.

Diseñar cada componente de forma que pueda extenderse sin modificar los existentes.

### Verificabilidad

Todo componente debe tener un propósito claro y verificable.

Un componente bien diseñado permite responder: ¿Cómo sabemos que este componente cumple su propósito?

### Consistencia

Todos los componentes del framework deben seguir las mismas convenciones, estructuras y estilos.

Un framework inconsistente es difícil de usar y mantener.

---

## Uso por agentes automáticos

Checklist verificable que el agente completa al crear o modificar una pieza del framework. Es la **lista única de artefactos a actualizar**: los «Después:» del [How-To](How-To.md) y los procesos de esta guía remiten acá.

| Pieza | Archivo | Además actualizar |
|-------|---------|-------------------|
| Rule | `/IA/IA.Prompts/PromptFramework/Rules/Rule-[Dominio].md` | RuleSets que la necesiten · catálogo `Rules/README.md` · tabla de Rules de la [Guía Conceptual](Readme.md) |
| RuleSet | `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-[Dominio].md` | Catálogo `RuleSets/Readme.md` · tabla de RuleSets de la Guía Conceptual |
| Profile | `/IA/IA.Prompts/PromptFramework/Profiles/[Dominio]-[Tipo].md` | Catálogo `Profiles/README.md` · tabla de Profiles de la Guía Conceptual |
| Template | `/IA/IA.Prompts/PromptFramework/Templates/Prompt-[Nombre].md` | Catálogo `Templates/README.md` · tabla de Templates de la Guía Conceptual |
| Example | `/IA/IA.Prompts/PromptFramework/Examples/Example-[Descripción].md` | Catálogo `Examples/README.md` · tabla de Examples de la Guía Conceptual |
| Tool-Prompt | `/IA/IA.Prompts/Tool-Prompts/[Categoria]/[Verbo]-[Objeto].md` | Catálogo `Tool-Prompts/README.md` (tabla de su categoría) · tabla de Tool-Prompts de la Guía Conceptual |

Las rutas de los catálogos son relativas a `/IA/IA.Prompts/PromptFramework/`, salvo `Tool-Prompts/`, que está en la raíz del repositorio.

Verificación final antes de dar por terminada la pieza:

- [ ] La pieza respeta las [convenciones](#convenciones): nomenclatura, idioma, separadores `---` y rutas absolutas con base `/IA/IA.Prompts`.
- [ ] Todos los artefactos de la fila correspondiente quedaron actualizados y sus enlaces apuntan a archivos existentes.
- [ ] No se duplicó contenido: si otra pieza ya lo dice, se referencia (ver [Composición sobre duplicación](#principios-arquitectónicos)).
