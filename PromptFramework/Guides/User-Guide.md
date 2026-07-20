# Guía de Usuario — Prompt Framework

## Tabla de contenidos

- [Introducción](#introducción)
- [Inicio rápido](#inicio-rápido)
- [Usar un Tool-Prompt](#usar-un-tool-prompt)
- [Construir un Prompt nuevo](#construir-un-prompt-nuevo)
- [Seleccionar el Profile correcto](#seleccionar-el-profile-correcto)
- [Ejemplos completos](#ejemplos-completos)
- [Errores comunes](#errores-comunes)
- [Buenas prácticas](#buenas-prácticas)
- [Uso por agentes automáticos](#uso-por-agentes-automáticos)

---

## Introducción

Esta guía explica cómo utilizar el Prompt Framework para construir y ejecutar prompts con un agente de inteligencia artificial.

El framework permite describir un problema de forma estructurada y delegar el comportamiento del agente a componentes reutilizables, evitando repetir instrucciones en cada prompt.

Para comprender la arquitectura del framework antes de comenzar, consultar la [Guía Conceptual](Readme.md).

---

## Inicio rápido

### Opción A — Invocar un Tool-Prompt

Para tareas recurrentes (documentar, indexar, auditar, iniciar contexto) no hace falta construir nada: se invocan con una sola línea.

```
Ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Iniciar-Contexto.md en <tema>
Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado-Documentado/Iniciar-Indexado.md en <proyecto>
Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Infra/Crear-Documentacion-Server.md en <servidor>
Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Infra/Revisar-Seguridad-Server.md en <sistema>
Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Seguridad/Auditoria-Seguridad.md en <URL> con Usuario:<Usuario> y Clave:<Clave> y deja el informe en <Destino>
```

Ver el catálogo en `/IA/IA.Prompts/Tool-Prompts/README.md` y la [Guía de Optimización de Tokens](Token-Optimization.md).

### Opción B — Construir un Prompt nuevo

1. Identificar el tipo de tarea y seleccionar el Profile apropiado.
2. Abrir el Template adecuado en `/IA/IA.Prompts/PromptFramework/Templates/`.
3. Completar el núcleo de 5 secciones (ver [How-To](How-To.md)).
4. Referenciar el Profile.

### Opción C — Partir de un Example

Buscar un escenario parecido en `/IA/IA.Prompts/PromptFramework/Examples/`, copiarlo, reemplazar los datos concretos y ejecutar.

---

## Usar un Tool-Prompt

Los Tool-Prompts están en `/IA/IA.Prompts/Tool-Prompts/` y se invocan en una línea. Cada uno declara su invocación y sus parámetros en su cabecera.

El catálogo — cuándo usar cada uno, qué Profile aplica y su ejemplo de invocación — vive en un solo lugar: [`Tool-Prompts/README.md`](../../Tool-Prompts/README.md).

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
- `/IA/IA.Prompts/PromptFramework/Profiles/[Profile].md`
```

Los entregables van dentro de `# Solicitudes`, como tareas verificables con su ruta; no existe una sección «Resultado esperado» separada. Cómo completar cada sección: [How-To](How-To.md).

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

---

## Seleccionar el Profile correcto

El Profile determina **cómo** se comporta el agente durante la ejecución.

### Catálogo de selección

La tabla de selección — para qué sirve cada Profile, qué RuleSet aplica y cuándo elegirlo — vive en un solo lugar: el catálogo [`/IA/IA.Prompts/PromptFramework/Profiles/README.md`](../Profiles/README.md).

### Cuando no existe un Profile adecuado

Si ningún Profile se adapta exactamente a la tarea:

1. Identificar el RuleSet más apropiado.
2. Utilizar `Prompt-Template.md` como base.
3. Referenciar el RuleSet directamente.
4. Considerar si la tarea justifica crear un nuevo Profile (ver [Guía de Desarrollo](Develop-Guide.md)).

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
- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

### Ejemplo 2 — Auditoría de infraestructura

Consultar `/IA/IA.Prompts/PromptFramework/Examples/Example-Auditoria.md` para un ejemplo completo de auditoría de servidor Linux.

---

## Errores comunes

### Referenciar Rules directamente

**Incorrecto:**
```markdown
## Reglas
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-All.md`
- `/IA/IA.Prompts/PromptFramework/Rules/Rule-Workflow.md`
```

**Correcto:**
```markdown
## Profile
Aplicar:
- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

Los Profiles encapsulan los RuleSets que a su vez incluyen las Rules. Referenciar Rules directamente rompe la jerarquía del framework y duplica configuración.

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

2. **Definir restricciones explícitas.**
   Especialmente para tareas que involucren modificaciones en sistemas reales.

3. **Usar los Tool-Prompts cuando sea posible.**
   Ahorran tiempo y garantizan consistencia con el framework.

4. **Consultar los Examples antes de construir un Prompt nuevo.**
   Los Examples muestran patrones probados y funcionales.

5. **Describir el contexto con suficiente detalle.**
   No asumir que el agente conoce el proyecto. Proporcionar toda la información relevante.

6. **Verificar la consistencia antes de ejecutar.**
   El Profile y las solicitudes deben ser coherentes entre sí.

7. **Minimizar el consumo de tokens.**
   Iniciar las conversaciones con `Tool-Prompts/Indexado-Documentado/Iniciar-Contexto.md` y recuperar contexto desde la ia-db en lugar de releer el repositorio. Ver la [Guía de Optimización de Tokens](Token-Optimization.md).

---

## Uso por agentes automáticos

Al recibir un prompt para ejecutar, el agente valida su estructura antes de resolver la capa de comportamiento:

| Verificación | Criterio |
|--------------|----------|
| Núcleo de 5 secciones | El prompt contiene `# Contexto`, `# Objetivo`, `# Solicitudes`, `# Restricciones` y `# Framework` |
| Entregables | Van dentro de `# Solicitudes` como tareas verificables con su ruta; no hay sección «Resultado esperado» separada |
| Capa de comportamiento | `# Framework` referencia un Profile (caso general) o un RuleSet directo (`RuleSet-Lean` para análisis simple) |
| Jerarquía | El prompt no referencia Rules directamente (ver [Errores comunes](#errores-comunes)) |
| Restricciones | Explícitas cuando la tarea toca sistemas reales: modificación de archivos, commit/push, alcance |

Con la estructura validada:

1. Resolver la cadena `Profile → RuleSet → Rules` según la [Guía Conceptual](Readme.md#uso-por-agentes-automáticos).
2. Si `# Framework` está vacío o el componente referenciado no encaja con la tarea, seleccionar el Profile con el catálogo `/IA/IA.Prompts/PromptFramework/Profiles/README.md` y señalarlo al usuario.
3. Señalar las secciones faltantes o inconsistencias detectadas antes de ejecutar; no completar con suposiciones lo que el prompt no dice.
4. Aplicar por defecto las prácticas de la [Guía de Optimización de Tokens](Token-Optimization.md#uso-por-agentes-automáticos).
