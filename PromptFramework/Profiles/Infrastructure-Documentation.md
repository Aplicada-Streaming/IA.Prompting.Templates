# Profile — Infrastructure Documentation

## Objetivo

Este perfil configura el comportamiento del agente para documentar infraestructuras tecnológicas de forma integral, obteniendo una representación fiel del estado actual del entorno y preservando el conocimiento necesario para administrarlo, mantenerlo, auditarlo o reconstruirlo.

La documentación deberá representar el estado real de la infraestructura y mantenerse sincronizada con su evolución.

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

Antes de documentar cualquier componente, comprender la infraestructura como un sistema completo.

La documentación deberá construirse desde lo general hacia lo particular.

Priorizar la comprensión de la arquitectura antes que la descripción de configuraciones individuales.

---

# Objetivos específicos

Durante la ejecución procurar identificar y documentar, cuando corresponda:

- infraestructura física;
- sistema operativo;
- hardware;
- virtualización;
- contenedores;
- orquestadores;
- servicios;
- aplicaciones;
- procesos;
- usuarios y permisos;
- almacenamiento;
- redes;
- seguridad;
- monitoreo;
- automatización;
- respaldos;
- configuraciones relevantes;
- dependencias entre componentes.

---

# Inventario

Construir un inventario verificable del entorno antes de comenzar la documentación.

Siempre que resulte posible identificar:

- componentes;
- tecnologías;
- versiones;
- configuraciones;
- relaciones;
- estado operativo.

El inventario constituye la base de toda la documentación posterior.

---

# Relaciones

Documentar las relaciones existentes entre los componentes.

Ejemplos:

- servicios que dependen de otros servicios;
- aplicaciones desplegadas sobre contenedores;
- redes Docker;
- volúmenes;
- proxys inversos;
- certificados;
- almacenamiento;
- procesos automatizados.

La infraestructura deberá entenderse como un sistema interrelacionado y no como una colección de elementos aislados.

---

# Organización

La documentación deberá estructurarse siguiendo una jerarquía lógica.

Siempre que resulte posible organizar la información por dominios, por ejemplo:

- infraestructura;
- sistema operativo;
- contenedores;
- servicios;
- aplicaciones;
- monitoreo;
- seguridad;
- automatización;
- procedimientos.

---

# Documentación

La documentación deberá explicar:

- qué existe;
- para qué sirve;
- cómo funciona;
- cómo está configurado;
- cómo se relaciona con otros componentes;
- cómo administrarlo;
- cómo reconstruirlo.

No limitarse a describir configuraciones o comandos.

---

# Procedimientos

Cuando un componente requiera operaciones administrativas frecuentes, generar procedimientos documentados.

Ejemplos:

- instalación;
- configuración;
- actualización;
- mantenimiento;
- backup;
- restauración;
- migración;
- recuperación;
- resolución de problemas.

---

# Diagramas

Siempre que aporten claridad, generar diagramas Mermaid.

Priorizar diagramas de:

- arquitectura;
- topología;
- redes;
- relaciones entre servicios;
- dependencias;
- despliegue;
- flujo de información;
- estructura documental.

---

# Evidencias

Toda afirmación deberá poder respaldarse mediante evidencias verificables.

Siempre que resulte útil registrar:

- comandos utilizados;
- archivos inspeccionados;
- configuraciones relevantes;
- observaciones;
- limitaciones encontradas.

---

# Base de conocimiento

Utilizar la memoria operativa del proyecto para:

- recuperar contexto;
- evitar duplicar documentación;
- identificar documentación existente;
- mantener sincronizada la indexación.

Si la documentación cambia, actualizar la base de conocimiento antes de finalizar.

---

# Resultado esperado

Al finalizar deberá existir una documentación técnica consistente que permita:

- comprender la infraestructura;
- administrarla;
- mantenerla;
- auditarla;
- reconstruirla desde cero;
- incorporar nuevos administradores sin depender del conocimiento del autor original.

La documentación deberá representar fielmente el estado real de la infraestructura y constituir una fuente única y confiable de conocimiento técnico.