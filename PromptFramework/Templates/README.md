# Templates

Estructuras para construir prompts nuevos. Todo prompt del framework usa el **núcleo de 5 secciones**:

```
# Contexto → # Objetivo → # Solicitudes → # Restricciones → # Framework (Profile)
```

Los entregables van dentro de `# Solicitudes` (como tarea verificable con su ruta); no hay una sección "Resultado esperado" separada. Cualquier aclaración puntual de esa corrida se agrega como nota opcional al pie de `# Framework`.

Referencia: [Cómo escribir cada sección](../Guides/How-To.md) · [Guía conceptual](../Guides/Readme.md)

---

## Catálogo

| Template | Para qué sirve | Cuándo usarlo |
|----------|----------------|---------------|
| [Prompt-Template.md](Prompt-Template.md) | Estructura completa con la pregunta guía embebida en cada sección. | Al construir un prompt nuevo desde cero. |
| [Prompt-Minimal.md](Prompt-Minimal.md) | Las 5 secciones en su forma más breve. | Tareas simples o cuando ya dominás la estructura. |
| [Prompt-Example.md](Prompt-Example.md) | Un prompt completo ya redactado, como referencia. | Para ver cómo se ven las secciones ensambladas. |

---

## Cómo elegir el Profile

En `# Framework`, referenciá el **Profile** que represente la tarea (catálogo en [Profiles/README.md](../Profiles/README.md)). Si ningún Profile encaja, referenciá directamente un **RuleSet** (catálogo en [RuleSets/Readme.md](../RuleSets/Readme.md)); para tareas simples de análisis, `RuleSet-Lean`.

El Profile fija el **cómo** (comportamiento); el prompt aporta el **qué** (contexto del proyecto).
