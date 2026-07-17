# Rules

Reglas atómicas de comportamiento del framework. Cada regla define un aspecto único del comportamiento esperado del agente y se compone en RuleSets, Profiles y Prompts según la jerarquía `Prompt → Profile → RuleSet → Rules`.

Referencia: [Guía conceptual](../Guides/Readme.md) · [README del framework](../README.md)

---

## Catálogo de selección rápida

| Regla | Para qué sirve | Elegir cuando la tarea… |
|-------|----------------|-------------------------|
| [Rule-All](Rule-All.md) | Reglas transversales: comprensión del alcance, veracidad, calidad, transparencia, protección de la información y verificación de finalización. | …es cualquiera. Base aplicable siempre; incluir por defecto. |
| [Rule-Workflow](Rule-Workflow.md) | Ciclo de trabajo completo: diagnosticar → planificar → ejecutar → validar → reportar, con estructura del reporte final. | …requiere método de trabajo end-to-end o un reporte estructurado al usuario. |
| [Rule-Evidences](Rule-Evidences.md) | Trazabilidad, verificabilidad y reproducibilidad: nada como hecho sin evidencia; conclusiones que surgen de las evidencias. | …produce afirmaciones, hallazgos o conclusiones que deben poder rastrearse y reproducirse. |
| [Rule-Agents](Rule-Agents.md) | Delegación en subagentes: cuándo delegar, autoajuste al tamaño, especialización y agregación de resultados. | …se descompone en partes independientes, exige exploración amplia o perspectivas independientes. |
| [Rule-Indexing](Rule-Indexing.md) | Uso y mantenimiento de la base de conocimiento `ia-db`: recuperación incremental, sincronización y minimización de tokens. | …puede aprovechar contexto ya documentado o genera/actualiza conocimiento indexado. |
| [Rule-Documentation](Rule-Documentation.md) | Generación de documentación técnica: contenido real, procedimientos, arquitectura, única fuente de verdad. | …produce o actualiza documentación técnica del sistema. |
| [Rule-Markdown](Rule-Markdown.md) | Formato y estructura Markdown: jerarquía de encabezados, redacción, tablas/código/diagramas, validación. | …genera cualquier entregable en Markdown. |
| [Rule-Dual-Audience](Rule-Dual-Audience.md) | Documentación de doble audiencia: recursos narrativos para humanos y contrato máquina-legible (frontmatter, IDs, anclas, diagramas como código) para agentes de IA. | …genera documentación que también consumirán agentes de IA. |
| [Rule-Narrative-Voice](Rule-Narrative-Voice.md) | Voz de la prosa: técnica y formal con criterio de autor humano; elimina los patrones que delatan texto generado en serie, sin tocar las zonas estructuradas. | …produce prosa extensa (resúmenes, análisis, impacto, recomendaciones) que debe leerse con naturalidad profesional. |
| [Rule-Drift-Control](Rule-Drift-Control.md) | Control de deriva: contrato de ejecución, sensores (alcance, escritura, objetivo, invención, presupuesto, profundidad), puntos de control y re-anclaje. | …es larga, multi-fase o delega en subagentes y debe mantenerse dentro del alcance. |
| [Rule-Security-Testing](Rule-Security-Testing.md) | Pruebas de seguridad autorizadas y no destructivas: ética y alcance, metodología OWASP, clasificación de hallazgos por severidad/CVSS y manejo de credenciales. | …releva la seguridad de un sistema web/API/aplicación y reporta vulnerabilidades. |

---

## Cómo elegir

- **Siempre**: `Rule-All` (base transversal).
- **Trabajo con proceso y entrega**: sumar `Rule-Workflow`.
- **Resultado que debe sostenerse**: sumar `Rule-Evidences`.
- **Entregable escrito**: sumar `Rule-Markdown`; si es documentación técnica, además `Rule-Documentation`.
- **Contexto/memoria del proyecto**: sumar `Rule-Indexing`.
- **Tarea grande o paralelizable**: sumar `Rule-Agents`.
- **Documentación consumida también por IA**: sumar `Rule-Dual-Audience`.
- **Prosa extensa que debe leerse con naturalidad profesional**: sumar `Rule-Narrative-Voice`.
- **Ejecución larga, multi-fase o delegada**: sumar `Rule-Drift-Control`.
- **Auditoría de seguridad web/API**: sumar `Rule-Security-Testing`.

Las reglas se combinan; no son excluyentes. Un RuleSet típico agrupa las que apliquen a un dominio.
