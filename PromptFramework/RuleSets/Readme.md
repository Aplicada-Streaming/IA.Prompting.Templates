# RuleSets

Conjuntos de reglas por dominio. Un RuleSet agrupa las Rules que aplican a un tipo de trabajo; el `Default` es la base y los especializados lo extienden añadiendo énfasis y restricciones. Los Profiles referencian un RuleSet según la jerarquía `Prompt → Profile → RuleSet → Rules`.

Referencia: [Guía conceptual](../Guides/Readme.md) · [README del framework](../README.md) · [Catálogo de Rules](../Rules/README.md)

---

## Catálogo de selección rápida

| RuleSet | Para qué sirve | Extiende | Elegir cuando la tarea… |
|---------|----------------|----------|-------------------------|
| [RuleSet-Default](RuleSet-Default.md) | Conjunto base aplicado en toda operación: las 7 Rules del framework. Los demás RuleSets parten de aquí. | — (es la base) | …es genérica o no encaja en un dominio especializado. |
| [RuleSet-Documentation](RuleSet-Documentation.md) | Documentación técnica: comprender el sistema, ir de lo general a lo particular, diagramas Mermaid, sincronizar la base de conocimiento. | Default | …genera o mantiene documentación técnica de calidad. |
| [RuleSet-Development](RuleSet-Development.md) | Desarrollo de software: revisión de código, análisis de arquitectura y evaluación técnica, con recomendaciones justificadas. | Default | …analiza o revisa código y arquitectura. |
| [RuleSet-Audit](RuleSet-Audit.md) | Auditoría técnica **solo lectura**: inventario, inconsistencias y evidencia verificable sin modificar el entorno. | Default | …inspecciona un entorno y reporta hallazgos sin alterar su estado. |

Los cuatro aplican las mismas 7 Rules del framework; se diferencian por el **énfasis** y, en Audit, por **restricciones adicionales** (solo mecanismos de inspección y lectura).

---

## Cómo elegir

- **Tarea genérica**: `RuleSet-Default`.
- **Documentar**: `RuleSet-Documentation`.
- **Revisar/analizar código**: `RuleSet-Development`.
- **Auditar sin tocar el entorno**: `RuleSet-Audit`.

Un RuleSet no se elige directamente en el prompt: lo fija el [Profile](../Profiles/README.md) que uses. Consultá el catálogo de Profiles para ver qué RuleSet aplica cada uno.
