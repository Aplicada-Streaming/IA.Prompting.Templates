# Guía de Usuario — Prompt Framework

## Tabla de contenidos

- [Introducción](#introducción)
- [Inicio rápido](#inicio-rápido)
- [Usar un Prompt predefinido](#usar-un-prompt-predefinido)
- [Construir un Prompt nuevo](#construir-un-prompt-nuevo)
- [Seleccionar el Profile correcto](#seleccionar-el-profile-correcto)
- [Completar los Parameters](#completar-los-parameters)
- [Ejemplos completos](#ejemplos-completos)
- [Errores comunes](#errores-comunes)
- [Buenas prácticas](#buenas-prácticas)

---

## Introducción

Esta guía explica cómo utilizar el Prompt Framework para construir y ejecutar prompts con un agente de inteligencia artificial.

El framework permite describir un problema de forma estructurada y delegar el comportamiento del agente a componentes reutilizables, evitando repetir instrucciones en cada prompt.

Para comprender la arquitectura del framework antes de comenzar, consultar la [Guía Conceptual](Readme.md).

---

## Inicio rápido

### Opción A — Usar un Prompt predefinido

1. Verificar si existe un Prompt en `/IA.Prompting.Templates/PromptFramework/Prompts/` que se adapte a la tarea.
2. Copiar el contenido del Prompt.
3. Completar el contexto y los Parameters del proyecto.
4. Ejecutar con el agente.

### Opción B — Construir un Prompt nuevo

1. Identificar el tipo de tarea y seleccionar el Profile apropiado.
2. Abrir el Template adecuado en `/IA.Prompting.Templates/PromptFramework/Templates/`.
3. Completar todos los campos.
4. Referenciar el Profile y los Parameters.

### Opción C — Invocar un Tool-Prompt

Para operar la base de conocimiento (ia-db) o iniciar el contexto de un chat, no hace falta construir nada: se invoca con una sola línea.

```
Ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Contexto.md en <tema>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md en <proyecto>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md de <proyecto-a> y <proyecto-b> y deja la indexación en la raíz /
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Actualizar-Indexado.md de <proyecto>
```

Ver `/IA.Prompting.Templates/Tool-Prompts/README.md` y la [Guía de Optimización de Tokens](Token-Optimization.md).

---

## Usar un Prompt predefinido

Los Prompts predefinidos se encuentran en `/IA.Prompting.Templates/PromptFramework/Prompts/`.

| Prompt | Cuándo usarlo |
|--------|---------------|
| `Actualizar-Documentacion.md` | Actualizar documentación existente del proyecto |
| `Documentar-Docker.md` | Documentar una infraestructura Docker |
| `Documentar-Servidor.md` | Documentar un servidor Linux |
| `Revisar-Seguridad.md` | Realizar una revisión de seguridad |

Para usar un Prompt predefinido:

1. Abrir el archivo del Prompt.
2. Agregar el contexto específico del proyecto en la sección `# Contexto`.
3. Asegurarse de que los Parameters estén completos.
4. Ejecutar.

---

## Construir un Prompt nuevo

### Estructura de un Prompt

Todo Prompt deberá tener la siguiente estructura:

```markdown
# Contexto
[Descripción del problema y estado actual]

# Objetivo
[Resultado esperado al finalizar]

# Solicitudes
[Lista de tareas específicas]

# Restricciones
[Qué no debe hacer el agente]

# Framework

## Profile
Aplicar:
- `/IA.Prompting.Templates/PromptFramework/Profiles/[Profile].md`

## Parameters
Utilizar la configuración de:
- `/IA.Prompting.Templates/PromptFramework/Parameters`

# Resultado esperado
[Entregables esperados al finalizar]
```

### Paso a paso

#### 1. Describir el contexto

Explicar qué proyecto o sistema está involucrado, cuál es el estado actual y qué información es relevante para comprender la tarea.

No asumir que el agente conoce el proyecto.

#### 2. Definir el objetivo

Describir con claridad qué resultado se espera obtener al finalizar la ejecución.

Un objetivo bien definido es específico, verificable y acotado.

#### 3. Listar las solicitudes

Enumerar las tareas concretas que deberán realizarse.

Cada solicitud deberá ser atómica cuando sea posible, clara y verificable.

#### 4. Definir restricciones

Indicar explícitamente todo lo que el agente no debe hacer.

Ejemplos comunes:

- No modificar el estado del servidor.
- No realizar commit, push ni pull request.
- No inventar información.
- Ejecutar únicamente comandos de lectura.

#### 5. Seleccionar el Profile

Ver sección [Seleccionar el Profile correcto](#seleccionar-el-profile-correcto).

#### 6. Verificar los Parameters

Ver sección [Completar los Parameters](#completar-los-parameters).

---

## Seleccionar el Profile correcto

El Profile determina **cómo** se comporta el agente durante la ejecución.

### Tabla de selección

| Si la tarea es... | Profile recomendado |
|-------------------|---------------------|
| Documentar un repositorio de software | `Repository-Documentation.md` |
| Documentar infraestructura general | `Infrastructure-Documentation.md` |
| Auditar una infraestructura (solo lectura) | `Infrastructure-Audit.md` |
| Documentar infraestructura Docker | `Docker-Documentation.md` |
| Analizar la arquitectura de un sistema | `Architecture-Review.md` |
| Revisar código fuente | `Code-Review.md` |
| Crear o mantener la base de conocimiento (ia-db) | `Knowledge-Indexing.md` |

### Cuándo usar cada Profile

**Repository-Documentation** — Para proyectos de software donde se necesita documentar la organización, arquitectura, componentes y procesos del repositorio.

**Infrastructure-Documentation** — Para servidores y entornos de infraestructura donde se necesita documentar el estado completo del sistema.

**Infrastructure-Audit** — Similar a Infrastructure-Documentation pero con restricciones estrictas de solo lectura. Usar cuando el objetivo es auditar sin modificar.

**Docker-Documentation** — Especializado en infraestructuras Docker. Cubre contenedores, redes, volúmenes y archivos Compose.

**Architecture-Review** — Para analizar y documentar la arquitectura de un sistema de software, con foco en responsabilidades, dependencias y decisiones de diseño.

**Code-Review** — Para revisar código fuente con perspectiva técnica, arquitectónica y de mantenibilidad.

**Knowledge-Indexing** — Para generar o actualizar la base de conocimiento (ia-db) de un proyecto. Normalmente no se usa directamente: lo aplican los Tool-Prompts `Iniciar-Indexado.md` y `Actualizar-Indexado.md`.

### Cuando no existe un Profile adecuado

Si ningún Profile se adapta exactamente a la tarea:

1. Identificar el RuleSet más apropiado.
2. Utilizar `Prompt-Template.md` como base.
3. Referenciar el RuleSet directamente.
4. Considerar si la tarea justifica crear un nuevo Profile (ver [Guía de Desarrollo](Develop-Guide.md)).

---

## Completar los Parameters

Los Parameters contienen la configuración específica del proyecto.

Antes de ejecutar cualquier Prompt, verificar que los siguientes archivos estén completos:

### Repositories.md

Definir los repositorios del proyecto: repositorio de código fuente, de documentación y de infraestructura.

### Paths.md

Definir las rutas relevantes: carpeta de documentación, base de conocimiento, ubicación de prompts y templates.

### Variables.md

Definir las variables generales: nombre del proyecto, entorno, configuraciones de comportamiento.

### Ejemplo de configuración

```markdown
## Proyecto

- Nombre del proyecto: Mi Sistema
- Descripción: Plataforma de procesamiento de datos
- Entorno: Producción
- Versión: 2.1.0

## Documentación

- Documentación habilitada: Sí
- Actualizar índices: Sí
- Generar diagramas Mermaid: Sí
```

---

## Ejemplos completos

### Ejemplo 1 — Documentar un servidor

```markdown
# Contexto

El proyecto administra un servidor Linux que aloja múltiples servicios Docker.
La documentación actual está desactualizada y no refleja el estado real del servidor.

# Objetivo

Generar documentación técnica actualizada que represente fielmente el estado actual del servidor.

# Solicitudes

- Construir un inventario del servidor.
- Identificar servicios Docker en ejecución.
- Documentar la infraestructura.
- Actualizar la base de conocimiento.

# Restricciones

- No modificar el servidor.
- No ejecutar comandos destructivos.
- No inventar información.

# Framework

## Profile

Aplicar:
- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`

## Parameters

Utilizar la configuración de:
- `/IA.Prompting.Templates/PromptFramework/Parameters`

# Resultado esperado

- Inventario actualizado.
- Documentación técnica.
- Diagramas de arquitectura.
- Índices actualizados.
```

### Ejemplo 2 — Auditoría de infraestructura

Consultar `/IA.Prompting.Templates/PromptFramework/Examples/Example-Auditoria.md` para un ejemplo completo de auditoría de servidor Linux.

### Ejemplo 3 — Documentación de infraestructura con Docker

Consultar `/IA.Prompting.Templates/PromptFramework/Examples/Example-Documentar-Infra.md` para un ejemplo completo de documentación de infraestructura Linux con Docker.

---

## Errores comunes

### Referenciar Rules directamente

**Incorrecto:**
```markdown
## Reglas
- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-All.md`
- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-Workflow.md`
```

**Correcto:**
```markdown
## Profile
Aplicar:
- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

Los Profiles encapsulan los RuleSets que a su vez incluyen las Rules. Referenciar Rules directamente rompe la jerarquía del framework y duplica configuración.

### Omitir los Parameters

El agente no puede resolver rutas ni repositorios sin los Parameters completos.

Siempre verificar que `Repositories.md`, `Paths.md` y `Variables.md` estén correctamente configurados antes de ejecutar.

### Mezclar el contexto con el objetivo

El **contexto** describe la situación actual.
El **objetivo** describe el resultado esperado.

Mantenerlos separados facilita la comprensión y evita ambigüedades.

### No definir restricciones

Las restricciones son especialmente importantes cuando el agente tiene acceso a sistemas productivos.

Definir siempre qué comandos puede ejecutar, si puede modificar archivos, si puede hacer commit o push, y qué sistemas están fuera de alcance.

---

## Buenas prácticas

1. **Usar Profiles en lugar de referenciar reglas individualmente.**
   Los Profiles garantizan que se aplique el conjunto correcto de reglas para cada tipo de tarea.

2. **Completar los Parameters antes de ejecutar.**
   Los parámetros incompletos producen resultados de menor calidad.

3. **Definir restricciones explícitas.**
   Especialmente para tareas que involucren modificaciones en sistemas reales.

4. **Usar los Prompts predefinidos cuando sea posible.**
   Ahorran tiempo y garantizan consistencia con el framework.

5. **Consultar los Examples antes de construir un Prompt nuevo.**
   Los Examples muestran patrones probados y funcionales.

6. **Mantener los Parameters actualizados.**
   Si el proyecto cambia, actualizar los Parameters.

7. **Describir el contexto con suficiente detalle.**
   No asumir que el agente conoce el proyecto. Proporcionar toda la información relevante.

8. **Verificar la consistencia antes de ejecutar.**
   El Profile, los Parameters y las solicitudes deben ser coherentes entre sí.

9. **Minimizar el consumo de tokens.**
   Iniciar las conversaciones con `Tool-Prompts/Iniciar-Contexto.md` y recuperar contexto desde la ia-db en lugar de releer el repositorio. Ver la [Guía de Optimización de Tokens](Token-Optimization.md).
