# Template-Prompt

Framework reutilizable para ingeniería de prompts.

Proporciona una metodología consistente para construir prompts complejos mediante la composición de componentes independientes, reutilizables y mantenibles.

Los prompts describen **qué** se necesita hacer. Los perfiles determinan **cómo** se comporta el agente.

---

## Documentación

Consultar la [documentación del framework](PromptFramework/README.md) para comenzar.

---

## Uso rápido — Tool-Prompts

Prompts-herramienta invocables con una sola línea (ver [Tool-Prompts/README.md](Tool-Prompts/README.md)):

```
Ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Contexto.md en <tema>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md en <proyecto>
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md de <proyecto-a> y <proyecto-b> y deja la indexación en la raíz /
Lee y ejecuta /IA.Prompting.Templates/Tool-Prompts/Actualizar-Indexado.md de <proyecto>
```

---

## Nota sobre referencias

Todas las referencias internas de los prompts usan rutas absolutas desde la raíz del workspace, con base `/IA.Prompting.Templates`.

