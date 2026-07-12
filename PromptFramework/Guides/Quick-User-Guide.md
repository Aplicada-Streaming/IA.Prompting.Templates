# Guía Rápida — Cómo escribir cada sección del Prompt

Esta guía sirve para escribir un prompt leyendo de arriba hacia abajo. Cada sección incluye:

- **Definición** — qué representa la sección.
- **Pregunta guía** — la pregunta que tenés que responder al escribirla.
- **Frases de ejemplo** — plantillas de arranque para copiar y adaptar.

La estructura completa está en [`Prompt-Template.md`](../Templates/Prompt-Template.md). Para el detalle conceptual, ver la [Guía de Usuario](User-Guide.md).

Orden de las secciones:

`Contexto` → `Objetivo` → `Solicitudes` → `Restricciones` → `Framework (Profile)` → `Resultado esperado` → `Observaciones`

---

## 1. Contexto

**Definición:** describe la situación actual y la información que el agente necesita para entender el pedido. No dice qué hacer, dice *dónde estamos parados*.

**Pregunta guía:** ¿Qué necesita saber el agente sobre el estado actual para no asumir nada?

**Frases de ejemplo:**

- «El proyecto administra un servidor Linux que aloja múltiples servicios Docker.»
- «La documentación actual está desactualizada y no refleja el estado real del servidor.»
- «El repositorio contiene la infraestructura de red del host, gestionada mediante `netplan`.»
- «Actualmente el servidor tiene un UPS conectado por USB con 20 minutos de autonomía.»

> **Tip:** empezá por el sujeto (el proyecto / el servidor / el repositorio) y describí el estado en presente. Evitá verbos de acción como «configurar» o «generar»: esos van en Objetivo.


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

# Resultado esperado
[Entregables esperados al finalizar]
```

---

## 2. Objetivo

**Definición:** el resultado esperado al finalizar. Una o dos frases que resumen *a dónde queremos llegar*.

**Pregunta guía:** ¿Qué debería ser verdad cuando el agente termine?

**Frases de ejemplo:**

- «Generar documentación técnica actualizada que represente fielmente el estado actual del servidor.»
- «Actualizar la documentación de la infraestructura para que refleje el estado real.»
- «Conocer cómo responde Docker ante ciclos de apagado y encendido del servidor.»
- «Analizar y proponer un mecanismo de respuesta ante fallos de suministro de energía.»

> **Tip:** un buen objetivo es **específico, verificable y acotado**. Arrancá con un verbo en infinitivo (Documentar, Analizar, Actualizar, Generar).

---

## 3. Solicitudes

**Definición:** la lista de tareas concretas a realizar. Es el «qué hacer», paso a paso.

**Pregunta guía:** ¿Qué acciones concretas hay que ejecutar para cumplir el objetivo?

**Frases de ejemplo:**

- «Construir un inventario del servidor.»
- «Identificar los servicios Docker en ejecución.»
- «Documentar la infraestructura existente.»
- «Actualizar la base de conocimiento.»
- «Generar un informe en `Repos-Hosts/Host.Infra/Temas-Estudio/Contenedores-Ciclos.md`.»

> **Tip:** una tarea por viñeta, **atómica y verificable**. Si una viñeta tiene varios «y», probablemente sean varias solicitudes. Cuando el resultado deba guardarse, indicá la ruta exacta del archivo.

---

## 4. Restricciones

**Definición:** todo lo que el agente **no** debe hacer. Es el límite de seguridad del prompt.

**Pregunta guía:** ¿Qué podría hacer el agente que yo NO quiero que haga?

**Frases de ejemplo:**

- «No modificar el estado del servidor.»
- «Ejecutar únicamente comandos de lectura.»
- «No realizar commit, push ni pull request.»
- «No inventar información; toda afirmación debe estar respaldada por evidencias verificables.»
- «No realizar cambios sobre proyectos de software.»

> **Tip:** son críticas cuando el agente toca sistemas reales. Definí siempre: si puede modificar archivos, si puede hacer commit/push, y qué queda fuera de alcance.

---

## 5. Framework → Profile

**Definición:** indica *cómo* debe comportarse el agente. En lugar de repetir reglas, se referencia un **Profile** que ya encapsula el conjunto correcto.

**Pregunta guía:** ¿De qué tipo es esta tarea, y qué Profile la representa?

**Frases de ejemplo:**

```markdown
## Profile

Aplicar:
- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`
```

Guía rápida de selección:

| Si la tarea es… | Profile |
|-----------------|---------|
| Documentar un repositorio de software | `Repository-Documentation.md` |
| Documentar infraestructura | `Infrastructure-Documentation.md` |
| Auditar (solo lectura) | `Infrastructure-Audit.md` |
| Documentar Docker | `Docker-Documentation.md` |
| Analizar arquitectura | `Architecture-Review.md` |
| Revisar código | `Code-Review.md` |

> **Tip:** referenciá el **Profile**, no las Rules directamente. Ver [Seleccionar el Profile correcto](User-Guide.md#seleccionar-el-profile-correcto).

---

## 6. Resultado esperado

**Definición:** los **entregables** que deben existir al finalizar. La diferencia con el Objetivo: el objetivo es la meta, esto es la lista concreta de lo que quedará producido.

**Pregunta guía:** ¿Qué archivos o artefactos voy a poder revisar cuando termine?

**Frases de ejemplo:**

- «Inventario de infraestructura actualizado.»
- «Documentación técnica y procedimientos.»
- «Diagramas de arquitectura.»
- «Índices y changelog actualizados.»
- «Toda la documentación debe ser consistente con el resto del repositorio.»

> **Tip:** si un entregable no puede señalarse como un archivo o resultado verificable, revisá si en realidad es parte del Objetivo.

---

## 7. Observaciones

**Definición:** aclaraciones puntuales de *esta* ejecución que no forman parte del Profile ni de las reglas generales.

**Pregunta guía:** ¿Hay algo especial de este caso que el agente no puede deducir del resto?

**Frases de ejemplo:**

- «El UPS está conectado ahora; podés revisarlo y relevar datos.»
- «Pedí los permisos de root que necesites.»
- «Priorizar la sección de red por sobre el resto de la documentación.»
- «Si un dato no puede verificarse, indicarlo explícitamente en vez de omitirlo.»

> **Tip:** sección opcional. Usala solo para lo específico de esta corrida; lo reutilizable va en el Profile.

---

## Ejemplo mínimo completo

Cómo se ven las frases una vez ensambladas:

```markdown
# Contexto
El proyecto administra un servidor Linux con servicios Docker. La documentación
está desactualizada y no refleja el estado real.

# Objetivo
Generar documentación técnica que represente fielmente el estado actual del servidor.

# Solicitudes
- Construir un inventario del servidor.
- Identificar los servicios Docker en ejecución.
- Documentar la infraestructura.

# Restricciones
- No modificar el servidor.
- Ejecutar únicamente comandos de lectura.
- No inventar información.

# Framework

## Profile
Aplicar:
- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`

# Resultado esperado
- Inventario actualizado.
- Documentación técnica y diagramas.
- Índices actualizados.
```

---

**Ver también:** [Guía de Usuario](User-Guide.md) · [Template](../Templates/Prompt-Template.md) · [Ejemplos](../Examples/)
