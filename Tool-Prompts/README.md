# Tool-Prompts

## Objetivo

Prompts-herramienta de invocación directa: se ejecutan con **una sola línea** en el chat, sin copiar ni completar plantillas. Cada uno declara su invocación en una cabecera `> **Invocación**` y sus parámetros `{entre llaves}`.

Todos siguen el núcleo de 5 secciones del framework (Contexto · Objetivo · Solicitudes · Restricciones · Framework/Profile) y reutilizan un Profile, salvo `Iniciar-Contexto` (autónomo por diseño).

---

## Invocación

Forma completa:

```
Ejecuta /IA/IA.Prompts/Tool-Prompts/Indexado/Iniciar-Contexto.md en <tema>
```

Forma corta (equivalente — el agente resuelve la base `/IA/IA.Prompts` desde el workspace):

```
Ejecuta /Tool-Prompts/Indexado/Iniciar-Contexto en <tema>
```

Los valores entre `{llaves}` son parámetros: se completan con lo indicado en la línea de invocación; cada Tool-Prompt declara qué hacer cuando un parámetro no se indica.

---

## Organización

Los Tool-Prompts se agrupan en carpetas por dominio. La carpeta forma parte de la ruta de invocación.

| Carpeta | Dominio |
|---------|---------|
| [`Indexado/`](Indexado/) | ia-db y arranque de contexto |
| [`Software/`](Software/) | Código fuente: documentación de soluciones y QA |
| [`BasesDatos/`](BasesDatos/) | Estructura de bases de datos |
| [`Docker/`](Docker/) | Infraestructura de contenedores |
| [`Infra/`](Infra/) | Servidores y redes (documentación y seguridad de infraestructura) |
| [`Seguridad/`](Seguridad/) | Auditoría de seguridad de sistemas web expuestos |

`Infra/` y `Seguridad/` se separan por objeto auditado, no por disciplina: `Infra/Revisar-Seguridad.md` revisa la postura de un servidor o red desde adentro; `Seguridad/Auditoria-Seguridad.md` audita un portal web autenticado desde su URL pública.

---

## Prompts disponibles

### Indexado

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Iniciar-Contexto.md](Indexado/Iniciar-Contexto.md) | Arrancar un chat cargando solo el contexto necesario de un tema | — (autónomo) | `Ejecuta /Tool-Prompts/Indexado/Iniciar-Contexto en <tema>` |
| [Iniciar-Indexado.md](Indexado/Iniciar-Indexado.md) | Crear (o regenerar) la `ia-db` de uno o más proyectos | Knowledge-Indexing | `Lee y ejecuta /Tool-Prompts/Indexado/Iniciar-Indexado en <proyecto>` |
| [Actualizar-Indexado.md](Indexado/Actualizar-Indexado.md) | Sincronizar una `ia-db` existente con los cambios de sus proyectos | Knowledge-Indexing | `Lee y ejecuta /Tool-Prompts/Indexado/Actualizar-Indexado de <proyecto>` |

### Software

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Documentar-Fuentes-Software.md](Software/Documentar-Fuentes-Software.md) | Evaluar y documentar una solución, proyecto o workspace completo conforme al Marco de Documentación (ia-db + conjunto documental) | Solution-Documentation | `Lee y ejecuta /Tool-Prompts/Software/Documentar-Fuentes-Software en la solución <origen> y deja en: <destino>` |
| [Actualizar-Documentacion.md](Software/Actualizar-Documentacion.md) | Actualizar documentación existente de un proyecto | Repository-Documentation | `Lee y ejecuta /Tool-Prompts/Software/Actualizar-Documentacion en <proyecto>` |
| [Derivar-Casos-Prueba.md](Software/Derivar-Casos-Prueba.md) | Derivar casos y datos de prueba (QA) desde el modelo de datos | QA-Test-Design | `Lee y ejecuta /Tool-Prompts/Software/Derivar-Casos-Prueba en <proyecto>` |

### Bases de datos

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Documentar-BaseDatos.md](BasesDatos/Documentar-BaseDatos.md) | Documentar la estructura de una base de datos (diccionario + ER en dbml) | Database-Documentation | `Lee y ejecuta /Tool-Prompts/BasesDatos/Documentar-BaseDatos en <proyecto>` |

### Docker

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Documentar-Docker.md](Docker/Documentar-Docker.md) | Documentar una infraestructura Docker | Docker-Documentation | `Lee y ejecuta /Tool-Prompts/Docker/Documentar-Docker en <proyecto>` |

### Infraestructura

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Documentar-Servidor.md](Infra/Documentar-Servidor.md) | Documentar un servidor Linux | Infrastructure-Documentation | `Lee y ejecuta /Tool-Prompts/Infra/Documentar-Servidor en <servidor>` |
| [Revisar-Seguridad.md](Infra/Revisar-Seguridad.md) | Revisar la seguridad de un servidor o red (solo lectura) | Infrastructure-Audit | `Lee y ejecuta /Tool-Prompts/Infra/Revisar-Seguridad en <sistema>` |

### Seguridad

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Auditoria-Seguridad.md](Seguridad/Auditoria-Seguridad.md) | Auditar un sistema web autenticado desde su URL, con pruebas autorizadas y no destructivas (OWASP) | Web-Security-Audit | `Lee y ejecuta /Tool-Prompts/Seguridad/Auditoria-Seguridad en <URL> con Usuario:<Usuario> y Clave:<Clave> y deja el informe en <Destino>` |

### Modos de indexado

- **Modo proyecto** — `... Iniciar-Indexado en Discord.Bot.Moderador.Core` → genera `/Discord.Bot.Moderador.Core/ia-db`.
- **Modo workspace (federado)** — `... Iniciar-Indexado de Discord.Bot.Moderador.Core y IA.Prompts y deja la indexación en la raíz /` → genera `/ia-db` en la raíz del workspace, con un índice por proyecto (sirve también para proyectos no versionados).

Toda ia-db generada incluye un **manifiesto de generación** (alcance, fuentes, fecha, versión y prompt generador), de modo que la base es regenerable y actualizable a partir de sí misma.

---

## Diseño y consumo de tokens

- Los Tool-Prompts de documentación/auditoría (`Documentar-*`, `Actualizar-Documentacion`, `Revisar-Seguridad`, `Auditoria-Seguridad`, indexado) aplican el Profile correspondiente, que resuelve la cadena `Profile → RuleSet → Rules`.
- `Iniciar-Contexto` es **autónomo por diseño**: no carga Profiles ni RuleSets, porque su única función es arrancar una conversación con el mínimo de tokens posible. Es la excepción documentada a la jerarquía del framework.

Ver `/IA/IA.Prompts/PromptFramework/Guides/Token-Optimization.md` para el racional completo.
