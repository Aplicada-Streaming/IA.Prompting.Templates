# Profile — Study Guide Documentation

## Objetivo

Configurar el agente para construir una **guía de estudio**: un cuerpo documental formativo sobre una temática, organizado como recorrido de aprendizaje y no como colección de fichas sueltas. El lector debe terminar entendiendo cada tema y con criterio para intervenir en él: elegir, producir y evaluar los artefactos del dominio.

La temática, el alcance y el destino los aporta el Prompt. Este Profile define cómo se estructura, se redacta y se valida la guía, cualquiera sea el tema.

---

# Framework

## Rule Set

Aplicar:

- `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-Study-Guide.md`

---

# Enfoque

Diseñar el mapa antes de escribir las piezas. Primero se fija el **marco de referencia** de la guía —el vocabulario común que después reaparece en todos los documentos—, y recién entonces se desarrolla cada tema sobre ese marco.

El marco de referencia se compone de tres ejes que el Prompt instancia según la temática:

| Eje | Qué fija | Rol en la guía |
|-----|----------|----------------|
| Escenarios | Situaciones típicas en las que se aplica el tema | Cada documento explica qué aporta el tema en cada escenario |
| Contextos | Entornos o variantes donde cambian las respuestas | Diferencian el tratamiento dentro de un mismo escenario |
| Actores | Roles que intervienen, con responsabilidades y alcance | Ubican al lector: qué le toca decidir y qué no |

Los ejes se definen una sola vez, en documentos propios, y el resto de la guía los referencia. Un tema que no se cruza con ningún escenario ni contexto sobra o está mal delimitado.

Ir de lo general a lo particular: mapa conceptual → ejes → un documento por tema → anexos.

---

# Objetivos específicos

Producir, cuando corresponda a la temática:

| Pieza | Contenido |
|-------|-----------|
| Marco de referencia | Escenarios, contextos y actores del dominio, definidos y nombrados de forma estable |
| Mapa conceptual | Tablas de entrada por escenario, por contexto y por artefacto: «estoy acá → qué aplico» |
| Documentos por tema | Un documento por unidad temática del dominio, todos con la misma estructura interna |
| Métodos y marcos | Enfoques alternativos del dominio: en qué consiste cada uno, en qué se diferencian, criterios para elegir |
| Anexos | Plantillas comentadas, listas de verificación y glosario |
| README | Tabla de contenido de todo lo generado, con la ruta de lectura sugerida |

---

# Estructura de cada documento temático

Todos los documentos temáticos siguen el mismo patrón, para que el lector aprenda una sola forma de leer:

1. **Definición** — qué es, qué problema resuelve, qué no es.
2. **Aplicación por escenario** — qué aporta en cada escenario del marco, y qué cambia según el contexto.
3. **Ejemplos concretos** — casos reales del dominio, no descripciones abstractas.
4. **Preguntas guía** — las que el lector debe poder responder para producir o evaluar el artefacto tratado.
5. **Criterios de calidad** — cómo se distingue una versión buena de una pobre.
6. **Anexo** — plantilla comentada, con las preguntas que guían cada campo.

---

# Criterios de calidad

- **Formativo, no enciclopédico**: cada sección deja al lector en condiciones de decidir, no solo de reconocer términos.
- **Trazable**: definiciones y prácticas se anclan a estándares o fuentes de la industria; lo que es criterio propio se declara como tal (`Rule-Evidences.md`).
- **Consistente**: la misma terminología, la misma estructura y los mismos escenarios en toda la guía; una sola voz de autor (`Rule-Narrative-Voice.md`).
- **Interconectado**: cada documento enlaza con los que lo preceden y lo continúan; ningún documento queda huérfano del mapa conceptual.
- **Verificable**: al cerrar, se revisa la guía completa contra el mapa buscando huecos, solapamientos y contradicciones, y se corrigen.

---

# Diagramas típicos

Mapa conceptual del dominio, relación entre escenarios y artefactos, flujos por rol, líneas de tiempo de un proceso, taxonomías. Diagramas como código (`Rule-Dual-Audience.md`).

---

# Resultado esperado

Un conjunto documental navegable desde su README, que permita a un lector sin conocimiento previo recorrer la temática de forma ordenada, ubicarse en un escenario concreto y saber qué producir, y formar criterio suficiente para intervenir como uno de los actores del dominio.
