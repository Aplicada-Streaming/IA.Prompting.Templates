# Tool-Prompts

## Objetivo

Prompts-herramienta de invocación directa: se ejecutan con **una sola línea** en el chat, sin copiar ni completar plantillas. Cada uno declara su invocación en una cabecera `> **Invocación**` y sus parámetros `{entre llaves}`.

Todos siguen el núcleo de 5 secciones del framework (Contexto · Objetivo · Solicitudes · Restricciones · Framework/Profile) y reutilizan un Profile, salvo `Iniciar-Contexto` (autónomo por diseño).

---

## Invocación

Forma completa:

```
Ejecuta /IA/IA.Prompts/Tool-Prompts/Iniciar-Contexto.md en <tema>
```

Forma corta (equivalente — el agente resuelve la base `/IA/IA.Prompts` desde el workspace):

```
Ejecuta /Tool-Prompts/Iniciar-Contexto en <tema>
```

Los valores entre `{llaves}` son parámetros: se completan con lo indicado en la línea de invocación; cada Tool-Prompt declara qué hacer cuando un parámetro no se indica.

---

## Prompts disponibles

| Tool-Prompt | Cuándo usarlo | Profile | Ejemplo de invocación |
|-------------|---------------|---------|-----------------------|
| [Iniciar-Contexto.md](Iniciar-Contexto.md) | Arrancar un chat cargando solo el contexto necesario de un tema | — (autónomo) | `Ejecuta /Tool-Prompts/Iniciar-Contexto en <tema>` |
| [Iniciar-Indexado.md](Iniciar-Indexado.md) | Crear (o regenerar) la `ia-db` de uno o más proyectos | Knowledge-Indexing | `Lee y ejecuta /Tool-Prompts/Iniciar-Indexado en <proyecto>` |
| [Actualizar-Indexado.md](Actualizar-Indexado.md) | Sincronizar una `ia-db` existente con los cambios de sus proyectos | Knowledge-Indexing | `Lee y ejecuta /Tool-Prompts/Actualizar-Indexado de <proyecto>` |
| [Documentar-Servidor.md](Documentar-Servidor.md) | Documentar un servidor Linux | Infrastructure-Documentation | `Lee y ejecuta /Tool-Prompts/Documentar-Servidor en <servidor>` |
| [Documentar-Docker.md](Documentar-Docker.md) | Documentar una infraestructura Docker | Docker-Documentation | `Lee y ejecuta /Tool-Prompts/Documentar-Docker en <proyecto>` |
| [Documentar-BaseDatos.md](Documentar-BaseDatos.md) | Documentar la estructura de una base de datos (diccionario + ER en dbml) | Database-Documentation | `Lee y ejecuta /Tool-Prompts/Documentar-BaseDatos en <proyecto>` |
| [Derivar-Casos-Prueba.md](Derivar-Casos-Prueba.md) | Derivar casos y datos de prueba (QA) desde el modelo de datos | QA-Test-Design | `Lee y ejecuta /Tool-Prompts/Derivar-Casos-Prueba en <proyecto>` |
| [Documentar-Fuentes-Software.md](Documentar-Fuentes-Software.md) | Evaluar y documentar una solución, proyecto o workspace completo conforme al Marco de Documentación (ia-db + conjunto documental) | Solution-Documentation | `Lee y ejecuta /Tool-Prompts/Documentar-Fuentes-Software en la solución <origen> y deja en: <destino>` |
| [Actualizar-Documentacion.md](Actualizar-Documentacion.md) | Actualizar documentación existente de un proyecto | Repository-Documentation | `Lee y ejecuta /Tool-Prompts/Actualizar-Documentacion en <proyecto>` |
| [Revisar-Seguridad.md](Revisar-Seguridad.md) | Revisión de seguridad (solo lectura) | Infrastructure-Audit | `Lee y ejecuta /Tool-Prompts/Revisar-Seguridad en <sistema>` |

### Modos de indexado

- **Modo proyecto** — `... Iniciar-Indexado en Discord.Bot.Moderador.Core` → genera `/Discord.Bot.Moderador.Core/ia-db`.
- **Modo workspace (federado)** — `... Iniciar-Indexado de Discord.Bot.Moderador.Core y IA.Prompts y deja la indexación en la raíz /` → genera `/ia-db` en la raíz del workspace, con un índice por proyecto (sirve también para proyectos no versionados).

Toda ia-db generada incluye un **manifiesto de generación** (alcance, fuentes, fecha, versión y prompt generador), de modo que la base es regenerable y actualizable a partir de sí misma.

---

## Diseño y consumo de tokens

- Los Tool-Prompts de documentación/auditoría (`Documentar-*`, `Actualizar-Documentacion`, `Revisar-Seguridad`, indexado) aplican el Profile correspondiente, que resuelve la cadena `Profile → RuleSet → Rules`.
- `Iniciar-Contexto` es **autónomo por diseño**: no carga Profiles ni RuleSets, porque su única función es arrancar una conversación con el mínimo de tokens posible. Es la excepción documentada a la jerarquía del framework.

Ver `/IA/IA.Prompts/PromptFramework/Guides/Token-Optimization.md` para el racional completo.
