# Profile — Docker Documentation

## Objetivo

Este perfil configura el comportamiento del agente para analizar, comprender y documentar una infraestructura Docker de forma integral.

La documentación deberá representar el estado real de la infraestructura de contenedores y preservar el conocimiento necesario para administrarla, mantenerla y reconstruirla.

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

Antes de documentar componentes individuales, comprender la infraestructura Docker como un sistema completo.

La documentación deberá construirse desde lo general hacia lo particular.

Priorizar la comprensión de la arquitectura de contenedores antes que la descripción de configuraciones individuales.

---

# Objetivos específicos

Durante la ejecución procurar identificar y documentar, cuando corresponda:

- imágenes Docker utilizadas y versiones;
- contenedores en ejecución;
- contenedores detenidos;
- redes Docker y sus configuraciones;
- volúmenes y puntos de montaje;
- archivos Docker Compose;
- variables de entorno relevantes;
- configuraciones de puertos expuestos;
- dependencias entre contenedores;
- registros de imágenes utilizados;
- estrategias de reinicio;
- recursos asignados;
- mecanismos de monitoreo;
- procesos de despliegue.

---

# Inventario

Construir un inventario verificable de la infraestructura Docker antes de documentar.

Identificar:

- imágenes y versiones;
- contenedores y su estado;
- redes y configuraciones;
- volúmenes y puntos de montaje;
- archivos de configuración (docker-compose, Dockerfiles).

---

# Relaciones

Documentar las relaciones existentes entre componentes.

Ejemplos:

- contenedores que dependen de otros contenedores;
- servicios que comparten redes;
- volúmenes compartidos;
- proxys inversos y servicios expuestos;
- bases de datos y aplicaciones que las utilizan.

---

# Diagramas

Generar diagramas Mermaid cuando aporten claridad.

Ejemplos:

- topología de contenedores;
- redes Docker;
- dependencias entre servicios;
- flujo de tráfico;
- arquitectura de despliegue.

---

# Procedimientos

Cuando corresponda, documentar procedimientos para:

- despliegue de la infraestructura;
- actualización de contenedores;
- backup de volúmenes;
- restauración;
- resolución de problemas comunes.

---

# Resultado esperado

Al finalizar deberá existir documentación completa de la infraestructura Docker que permita:

- comprender la arquitectura de contenedores;
- identificar todos los servicios y sus relaciones;
- administrar la infraestructura;
- reproducir el entorno.