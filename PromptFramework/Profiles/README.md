# Profiles

Perfiles de comportamiento del agente. Cada Profile configura al agente para un tipo de trabajo concreto (revisión, documentación, auditoría, indexado), fijando enfoque, objetivos, aspectos a evaluar y resultado esperado, y apoyándose en un RuleSet según la jerarquía `Prompt → Profile → RuleSet → Rules`.

Referencia: [Guía conceptual](../Guides/Readme.md) · [README del framework](../README.md)

---

## Catálogo de selección rápida

| Profile | Para qué sirve | RuleSet | Elegir cuando la tarea… |
|---------|----------------|---------|-------------------------|
| [Repository-Documentation](Repository-Documentation.md) | Documentar un repositorio de software: organización, arquitectura, componentes, convenciones, procesos y relaciones. | Documentation | …necesita entender y documentar un repo completo para mantenerlo y evolucionarlo. |
| [Architecture-Review](Architecture-Review.md) | Analizar y documentar la arquitectura de un sistema: estructura, responsabilidades, dependencias y decisiones de diseño, con visión global. | Documentation | …busca comprender el diseño de alto nivel más que la implementación. |
| [Code-Review](Code-Review.md) | Revisar código fuente en calidad, arquitectura, seguridad, rendimiento y mantenibilidad, separando hechos, inferencias y propuestas. | Development | …requiere una revisión técnica del código con recomendaciones fundadas. |
| [Infrastructure-Documentation](Infrastructure-Documentation.md) | Documentar una infraestructura tecnológica de forma integral para administrarla, auditarla y reconstruirla desde cero. | Documentation | …necesita preservar el conocimiento operativo de un entorno tecnológico. |
| [Docker-Documentation](Docker-Documentation.md) | Documentar una infraestructura Docker (contenedores, redes, volúmenes, Compose/Dockerfiles) y reproducir el entorno. | Documentation | …se centra específicamente en contenedores Docker. |
| [Infrastructure-Audit](Infrastructure-Audit.md) | Auditar una infraestructura **sin modificarla**: inventario verificable, inconsistencias y evidencia por hallazgo (solo lectura). | Audit | …exige inspeccionar un entorno y reportar hallazgos sin alterar su estado. |
| [Knowledge-Indexing](Knowledge-Indexing.md) | Construir y mantener la base de conocimiento `ia-db`: índices semánticos que reducen tokens y aceleran el arranque de contexto. | Documentation | …crea o actualiza la memoria operativa del proyecto (indexado). |

---

## Cómo elegir

- **Documentar software**: `Repository-Documentation` (repo completo) o `Architecture-Review` (solo diseño de alto nivel).
- **Revisar código**: `Code-Review`.
- **Documentar infraestructura**: `Infrastructure-Documentation` (general) o `Docker-Documentation` (contenedores Docker).
- **Auditar sin tocar**: `Infrastructure-Audit` (único de solo lectura, RuleSet Audit).
- **Construir/actualizar la ia-db**: `Knowledge-Indexing`.

Los Profiles no se combinan entre sí: cada ejecución adopta uno. Si el trabajo abarca varios enfoques, delegar cada uno en un subagente con su Profile (ver [Rule-Agents](../Rules/Rule-Agents.md)). Todos, salvo `Code-Review` (Development) e `Infrastructure-Audit` (Audit), se apoyan en el RuleSet Documentation.
