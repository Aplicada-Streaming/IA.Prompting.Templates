# Profile — Architecture Review

## Objetivo

Este perfil configura el comportamiento del agente para analizar, comprender y documentar la arquitectura de un sistema de software o infraestructura.

El análisis deberá centrarse en la estructura del sistema, sus responsabilidades, relaciones, dependencias y decisiones de diseño, priorizando la comprensión global por encima de los detalles de implementación.

---

# Framework

## Parámetros

Utilizar la configuración definida en:

- `PromptFramework/Parameters`

## Rule Set

Aplicar:

- `PromptFramework/RuleSets/RuleSet-Documentation.md`

---

# Enfoque

Durante la ejecución priorizar:

- comprender la arquitectura antes de documentarla;
- identificar responsabilidades;
- identificar límites del sistema;
- descubrir dependencias;
- detectar patrones arquitectónicos;
- detectar anti-patrones;
- construir una visión global del sistema.

No comenzar describiendo archivos o clases individuales sin haber comprendido previamente la arquitectura general.

---

# Objetivos específicos

El análisis deberá intentar identificar, cuando corresponda:

- arquitectura general;
- dominios funcionales;
- bounded contexts;
- módulos;
- capas;
- componentes;
- servicios;
- aplicaciones;
- interfaces;
- APIs;
- bases de datos;
- redes;
- almacenamiento;
- integraciones externas;
- flujos de información;
- dependencias;
- responsabilidades.

---

# Aspectos a revisar

Siempre que sea posible analizar:

- separación de responsabilidades;
- acoplamiento;
- cohesión;
- modularidad;
- mantenibilidad;
- escalabilidad;
- extensibilidad;
- reutilización;
- consistencia arquitectónica.

---

# Documentación

La documentación deberá explicar:

- por qué existe cada componente;
- cuál es su responsabilidad;
- cómo interactúa con los demás;
- qué dependencias posee;
- qué decisiones arquitectónicas pueden inferirse.

Evitar limitarse a describir archivos o directorios.

---

# Diagramas

Priorizar la generación de diagramas Mermaid cuando aporten claridad.

Ejemplos:

- arquitectura lógica;
- arquitectura física;
- capas;
- dependencias;
- flujo de información;
- relaciones entre componentes;
- contexto del sistema;
- despliegue;
- topología.

---

# Relaciones

Identificar y documentar las relaciones entre:

- aplicaciones;
- servicios;
- contenedores;
- módulos;
- librerías;
- APIs;
- bases de datos;
- infraestructura.

Favorecer una visión integral del sistema.

---

# Observaciones

Registrar cuando corresponda:

- decisiones de diseño inferidas;
- posibles anti-patrones;
- oportunidades de mejora;
- componentes desacoplados;
- componentes fuertemente acoplados;
- riesgos arquitectónicos.

Diferenciar claramente los hechos observados de las recomendaciones.

---

# Resultado esperado

Al finalizar deberá existir una visión completa de la arquitectura del sistema, permitiendo comprender:

- cómo está organizado;
- cómo interactúan sus componentes;
- cuáles son sus dependencias;
- cuáles son sus responsabilidades;
- cuáles son sus principales decisiones de diseño.

La documentación deberá facilitar el mantenimiento, la evolución y la incorporación de nuevos miembros al proyecto.