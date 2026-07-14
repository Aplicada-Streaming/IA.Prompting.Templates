# RuleSets

Conjuntos de reglas por dominio. Un RuleSet es **solo una lista de Rules**: agrupa las que aplican a un tipo de trabajo. `Default` es la base y los especializados lo extienden agregando las Rules de su dominio; `Lean` es un tier más liviano para tareas simples. El **énfasis y los criterios de calidad los define el Profile**, no el RuleSet. Jerarquía: `Prompt → Profile → RuleSet → Rules`.

Referencia: [Guía conceptual](../Guides/Readme.md) · [README del framework](../README.md) · [Catálogo de Rules](../Rules/README.md)

---

## Catálogo de selección rápida

| RuleSet | Rules que carga | Elegir cuando la tarea… |
|---------|-----------------|-------------------------|
| [RuleSet-Lean](RuleSet-Lean.md) | All, Workflow | …es simple, puntual o de análisis rápido; no genera documentación ni toca la ia-db. |
| [RuleSet-Default](RuleSet-Default.md) | All, Workflow, Evidences, Markdown | …es genérica pero produce un entregable escrito con evidencia. |
| [RuleSet-Documentation](RuleSet-Documentation.md) | Default + Documentation, Indexing, Agents | …genera o mantiene documentación técnica de calidad. |
| [RuleSet-Solution-Documentation](RuleSet-Solution-Documentation.md) | Documentation + Dual-Audience, Drift-Control | …documenta una solución completa conforme a un marco maestro, con subagentes orquestados. |
| [RuleSet-Development](RuleSet-Development.md) | Default + Agents | …analiza o revisa código y arquitectura. |
| [RuleSet-Audit](RuleSet-Audit.md) | Default + Indexing, Agents | …inspecciona un entorno y reporta hallazgos sin alterar su estado. |

Cada RuleSet carga **solo las Rules que su dominio necesita**: una tarea simple con `Lean` paga 2 reglas, no 7. Así el consumo de tokens es proporcional a la tarea.

---

## Cómo elegir

- **Tarea simple / análisis rápido**: `RuleSet-Lean`.
- **Tarea genérica con entregable escrito**: `RuleSet-Default`.
- **Documentar**: `RuleSet-Documentation`.
- **Documentar una solución completa (marco maestro + orquestación)**: `RuleSet-Solution-Documentation`.
- **Revisar/analizar código**: `RuleSet-Development`.
- **Auditar sin tocar el entorno**: `RuleSet-Audit`.

Un RuleSet normalmente no se elige directo en el prompt: lo fija el [Profile](../Profiles/README.md) que uses. Solo se referencia un RuleSet directamente cuando ningún Profile encaja (típico de `Lean` en prompts de análisis simple). Consultá el catálogo de Profiles para ver qué RuleSet aplica cada uno.
