# IA.Prompting.Templates

Framework reutilizable para ingeniería de prompts.

Construye prompts complejos componiendo piezas independientes y reutilizables. Los prompts describen **qué** hay que hacer; los Profiles determinan **cómo** se comporta el agente. Jerarquía: `Prompt → Profile → RuleSet → Rules`.

---

## De una idea a un Tool-Prompt

El flujo de trabajo recomendado: en vez de escribir el prompt a mano, le pedís al agente que lo construya a partir de tu idea, siguiendo la estructura del framework.

1. **Planteá la idea** en lenguaje natural (qué querés lograr, sobre qué proyecto, con qué límites).
2. **Pedile al agente que la estructure** con este pedido:

   ```
   A partir de esta idea, construí un Tool-Prompt siguiendo el framework de
   /IA.Prompting.Templates: elegí el Profile (o RuleSet Lean si es análisis simple),
   completá el núcleo de 5 secciones (Contexto, Objetivo, Solicitudes, Restricciones,
   Framework) y proponé dónde guardarlo.

   Idea: <describí tu idea acá>
   ```
3. **El agente elige la capa de comportamiento** (Profile que corresponda; catálogo en [`PromptFramework/Profiles/README.md`](PromptFramework/Profiles/README.md)) y **completa las 5 secciones** usando un [Template](PromptFramework/Templates/README.md).
4. **Guardás el resultado** como Tool-Prompt reutilizable en [`Tool-Prompts/`](Tool-Prompts/README.md) (invocable en una línea) o como [Example](PromptFramework/Examples/README.md) si es un caso puntual que quedó funcionando.

Guía de escritura y esqueletos copy-paste: [`How-To.md`](PromptFramework/Guides/How-To.md).

---

## Uso rápido — Tool-Prompts

Prompts-herramienta invocables en una línea (catálogo en [Tool-Prompts/README.md](Tool-Prompts/README.md)):

```
Ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Contexto.md en <tema>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md en <proyecto>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Documentar-Servidor.md en <servidor>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Actualizar-Indexado.md de <proyecto>
```

---

## Documentación

Empezá por la [documentación del framework](PromptFramework/README.md).

| Documento | Para qué |
|-----------|----------|
| [Guía conceptual](PromptFramework/Guides/Readme.md) | Arquitectura, filosofía y componentes |
| [How-To](PromptFramework/Guides/How-To.md) | Escribir prompts y extender el framework (copy-paste) |
| [Guía de usuario](PromptFramework/Guides/User-Guide.md) | Cómo usar el framework |
| [Guía de desarrollo](PromptFramework/Guides/Develop-Guide.md) | Cómo extender y mantener el framework |
| [Optimización de tokens](PromptFramework/Guides/Token-Optimization.md) | Minimizar el consumo de contexto (ia-db) |
| [Referencias](Referencias/README.md) | Documentación de referencia externa al framework, fuente de características para prompts |

---

## Nota sobre referencias

Las referencias internas de los prompts usan rutas absolutas desde la raíz del workspace, con base `/IA.Prompting.Templates`.
