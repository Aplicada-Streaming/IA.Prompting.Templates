# Profiles

Perfiles de comportamiento del agente. Cada Profile configura al agente para un tipo de trabajo concreto (revisión, documentación, auditoría, indexado), fijando enfoque, objetivos, aspectos a evaluar y resultado esperado, y apoyándose en un RuleSet según la jerarquía `Prompt → Profile → RuleSet → Rules`.

Referencia: [Guía conceptual](../Guides/Readme.md) · [README del framework](../README.md)

---

## Catálogo de selección rápida

| Profile | Para qué sirve | RuleSet | Elegir cuando la tarea… |
|---------|----------------|---------|-------------------------|
| [Solution-Documentation](Solution-Documentation.md) | Evaluar y documentar una pieza de software de cualquier escala (proyecto, solución multi-proyecto o workspace) conforme al Marco de Documentación de Software, orquestando subagentes por tipo de pieza. | Solution-Documentation | …debe producir el conjunto documental completo de una solución, para humanos y agentes de IA. |
| [Repository-Documentation](Repository-Documentation.md) | Documentar un repositorio de software: organización, arquitectura, componentes, convenciones, procesos y relaciones. | Documentation | …necesita entender y documentar un repo completo para mantenerlo y evolucionarlo. |
| [Architecture-Review](Architecture-Review.md) | Analizar y documentar la arquitectura de un sistema: estructura, responsabilidades, dependencias y decisiones de diseño, con visión global. | Documentation | …busca comprender el diseño de alto nivel más que la implementación. |
| [Code-Review](Code-Review.md) | Revisar código fuente en calidad, arquitectura, seguridad, rendimiento y mantenibilidad, separando hechos, inferencias y propuestas. | Development | …requiere una revisión técnica del código con recomendaciones fundadas. |
| [Infrastructure-Documentation](Infrastructure-Documentation.md) | Documentar una infraestructura tecnológica de forma integral para administrarla, auditarla y reconstruirla desde cero. | Documentation | …necesita preservar el conocimiento operativo de un entorno tecnológico. |
| [Docker-Documentation](Docker-Documentation.md) | Documentar una infraestructura Docker (contenedores, redes, volúmenes, Compose/Dockerfiles) y reproducir el entorno. | Documentation | …se centra específicamente en contenedores Docker. |
| [Database-Documentation](Database-Documentation.md) | Documentar una base de datos: diccionario de datos y modelo ER en dbml desde el esquema real, sin credenciales ni datos (solo lectura). | Documentation | …necesita documentar la estructura de una base de datos de forma regenerable. |
| [QA-Test-Design](QA-Test-Design.md) | Derivar casos de prueba (`TC-` trazables) y fixtures sintéticos PII-safe desde el modelo de datos (diccionario + ER). | Documentation | …necesita construir casos y datos de prueba a partir del modelo de datos. |
| [Infrastructure-Audit](Infrastructure-Audit.md) | Auditar una infraestructura **sin modificarla**: inventario verificable, inconsistencias y evidencia por hallazgo (solo lectura). | Audit | …exige inspeccionar un entorno y reportar hallazgos sin alterar su estado. |
| [Knowledge-Indexing](Knowledge-Indexing.md) | Construir y mantener la base de conocimiento `ia-db`: índices semánticos que reducen tokens y aceleran el arranque de contexto. | Documentation | …crea o actualiza la memoria operativa del proyecto (indexado). |

---

## Cómo elegir

- **Documentar una solución completa conforme al Marco**: `Solution-Documentation` (orquesta a los demás perfiles de documentación por tipo de pieza).
- **Documentar software**: `Repository-Documentation` (repo completo) o `Architecture-Review` (solo diseño de alto nivel).
- **Revisar código**: `Code-Review`.
- **Documentar infraestructura**: `Infrastructure-Documentation` (general) o `Docker-Documentation` (contenedores Docker).
- **Documentar una base de datos**: `Database-Documentation` (diccionario + ER en dbml, solo lectura).
- **Diseñar pruebas desde el modelo de datos**: `QA-Test-Design` (casos `TC-` + fixtures sintéticos).
- **Auditar sin tocar**: `Infrastructure-Audit` (único de solo lectura, RuleSet Audit).
- **Construir/actualizar la ia-db**: `Knowledge-Indexing`.

Los Profiles no se combinan entre sí: cada ejecución adopta uno. Si el trabajo abarca varios enfoques, delegar cada uno en un subagente con su Profile (ver [Rule-Agents](../Rules/Rule-Agents.md)); `Solution-Documentation` formaliza justamente esa orquestación para documentar soluciones completas. Todos se apoyan en el RuleSet Documentation, salvo `Code-Review` (Development), `Infrastructure-Audit` (Audit) y `Solution-Documentation` (Solution-Documentation, que extiende Documentation).
