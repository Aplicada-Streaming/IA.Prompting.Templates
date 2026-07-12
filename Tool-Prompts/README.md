# Tool-Prompts

## Objetivo

Prompts-herramienta de invocación directa. A diferencia de los Prompts de `PromptFramework/Prompts/`, están pensados para ejecutarse con una sola línea en el chat, sin necesidad de copiar ni completar plantillas.

---

## Invocación

Forma completa:

```
Ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Contexto.md en <tema>
```

Forma corta (equivalente — el agente resuelve la base `/IA.Prompting.Templates` desde el workspace):

```
Ejecuta /Tool-Prompts/Iniciar-Contexto en <tema>
```

Los valores entre `{llaves}` dentro de cada Tool-Prompt son parámetros: se completan con lo indicado en la línea de invocación; cada Tool-Prompt declara qué hacer cuando un parámetro no se indica.

---

## Prompts disponibles

| Tool-Prompt | Cuándo usarlo | Ejemplo de invocación |
|-------------|---------------|-----------------------|
| [Iniciar-Indexado.md](Iniciar-Indexado.md) | Crear (o regenerar) la base de conocimiento `ia-db` de uno o más proyectos | `Lee y ejecuta /Tool-Prompts/Iniciar-Indexado en <proyecto>` |
| [Actualizar-Indexado.md](Actualizar-Indexado.md) | Sincronizar una `ia-db` existente con los cambios de sus proyectos | `Lee y ejecuta /Tool-Prompts/Actualizar-Indexado de <proyecto>` |
| [Iniciar-Contexto.md](Iniciar-Contexto.md) | Arrancar un chat cargando solo el contexto necesario de un tema | `Ejecuta /Tool-Prompts/Iniciar-Contexto en <tema>` |

### Modos de indexado

- **Modo proyecto** — `... Iniciar-Indexado en Discord.Bot.Moderador.Core` → genera `/Discord.Bot.Moderador.Core/ia-db`.
- **Modo workspace (federado)** — `... Iniciar-Indexado de Discord.Bot.Moderador.Core y IA.Prompting.Templates y deja la indexación en la raíz /` → genera `/ia-db` en la raíz del workspace, con un índice por proyecto (sirve también para proyectos no versionados).

Toda ia-db generada incluye un **manifiesto de generación** (alcance, fuentes, fecha, versión y prompt generador), de modo que la base es regenerable y actualizable a partir de sí misma.

---

## Diseño y consumo de tokens

- `Iniciar-Indexado` y `Actualizar-Indexado` aplican el Profile `/IA.Prompting.Templates/PromptFramework/Profiles/Knowledge-Indexing.md` (tarea de fondo, se prioriza calidad).
- `Iniciar-Contexto` es **autónomo por diseño**: no carga Profiles ni RuleSets, porque su única función es arrancar una conversación con el mínimo de tokens posible. Es la excepción documentada a la jerarquía del framework.

Ver `/IA.Prompting.Templates/PromptFramework/Guides/Token-Optimization.md` para el racional completo.
