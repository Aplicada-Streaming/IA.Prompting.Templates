# Profile — Repository Documentation

## Objetivo

Este perfil configura el comportamiento del agente para analizar, comprender y documentar un repositorio de software de forma integral.

La documentación deberá representar la organización del repositorio, la arquitectura del proyecto, sus componentes, convenciones, procesos y relaciones, preservando el conocimiento necesario para facilitar su mantenimiento y evolución.

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

Antes de documentar cualquier archivo, comprender el repositorio como un sistema.

Priorizar la comprensión del proyecto antes que la descripción individual de archivos o directorios.

Construir la documentación desde una visión general hacia los detalles particulares.

---

# Objetivos específicos

Durante la ejecución procurar identificar y documentar, cuando corresponda:

- propósito del repositorio;
- organización general;
- arquitectura;
- dominios funcionales;
- módulos;
- proyectos;
- librerías;
- aplicaciones;
- dependencias;
- herramientas utilizadas;
- procesos de construcción;
- procesos de despliegue;
- automatizaciones;
- convenciones;
- documentación existente.

---

# Inventario

Construir un inventario verificable del repositorio antes de comenzar la documentación.

Siempre que resulte posible identificar:

- proyectos;
- soluciones;
- módulos;
- directorios relevantes;
- configuraciones;
- scripts;
- archivos de infraestructura;
- documentación existente.

El inventario constituye el punto de partida para el resto de la documentación.

---

# Organización

Analizar la estructura del repositorio.

Identificar:

- responsabilidades de cada directorio;
- agrupaciones funcionales;
- separación de capas;
- organización del código;
- convenciones de nombres;
- organización documental.

---

# Relaciones

Documentar las relaciones existentes entre:

- proyectos;
- módulos;
- librerías;
- servicios;
- APIs;
- scripts;
- documentación;
- procesos de construcción;
- procesos de despliegue.

Favorecer una visión integrada del repositorio.

---

# Arquitectura

Cuando resulte posible documentar:

- arquitectura lógica;
- arquitectura física;
- patrones utilizados;
- responsabilidades;
- dependencias;
- límites entre componentes.

No limitarse a describir la estructura de carpetas.

---

# Documentación

La documentación deberá explicar:

- qué contiene el repositorio;
- cómo está organizado;
- por qué fue organizado de esa manera;
- cómo se construye;
- cómo se despliega;
- cómo se mantiene;
- cómo evolucionar el proyecto.

Siempre que resulte posible explicar las decisiones de diseño inferidas.

---

# Procedimientos

Cuando corresponda generar procedimientos para:

- compilación;
- ejecución;
- despliegue;
- configuración;
- mantenimiento;
- actualización;
- incorporación de nuevos desarrolladores;
- resolución de problemas frecuentes.

---

# Diagramas

Siempre que aporten claridad generar diagramas Mermaid.

Ejemplos:

- estructura del repositorio;
- dependencias;
- arquitectura;
- relaciones entre proyectos;
- flujo de build;
- flujo de despliegue;
- organización documental.

---

# Evidencias

Toda afirmación deberá poder respaldarse mediante evidencias verificables.

Siempre que resulte útil registrar:

- archivos inspeccionados;
- configuraciones encontradas;
- estructura analizada;
- documentación existente;
- observaciones relevantes.

---

# Base de conocimiento

Utilizar la memoria operativa del proyecto para:

- recuperar documentación existente;
- evitar duplicaciones;
- identificar información previamente documentada;
- mantener sincronizada la indexación.

Si durante la ejecución cambia la documentación, actualizar la base de conocimiento antes de finalizar.

---

# Resultado esperado

Al finalizar deberá existir una documentación técnica consistente que permita:

- comprender el propósito del repositorio;
- conocer su organización;
- entender su arquitectura;
- localizar rápidamente la información relevante;
- incorporar nuevos miembros al proyecto;
- mantener y evolucionar el software sin depender del conocimiento de sus autores originales.

La documentación deberá constituir una fuente única, consistente y verificable del conocimiento del repositorio.