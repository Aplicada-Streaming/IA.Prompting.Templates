# Profile — Docker Documentation

## Objetivo

Configurar el agente para analizar, comprender y documentar una infraestructura Docker de forma integral, preservando el conocimiento necesario para administrarla, mantenerla y reconstruirla.

---

# Framework

## Rule Set

- `/IA.Prompting.Templates/PromptFramework/RuleSets/RuleSet-Documentation.md`

---

# Enfoque

Comprender la infraestructura de contenedores como un sistema completo antes de documentar componentes individuales; de lo general a lo particular. Partir de un **inventario verificable**: imágenes y versiones, contenedores y su estado, redes, volúmenes y archivos de configuración (Compose, Dockerfiles).

---

# Objetivos específicos

Identificar y documentar, cuando corresponda:

| Aspecto | Contenido |
|---------|-----------|
| Contenedores | En ejecución y detenidos, imágenes y versiones, registros utilizados, estrategias de reinicio, recursos asignados |
| Red y almacenamiento | Redes Docker y configuraciones, volúmenes y puntos de montaje, puertos expuestos |
| Configuración | Archivos Compose, Dockerfiles, variables de entorno relevantes |
| Relaciones | Dependencias entre contenedores, servicios que comparten redes o volúmenes, proxys inversos, bases de datos y sus consumidores |
| Operación | Monitoreo, procesos de despliegue |

---

# Procedimientos

Cuando corresponda: despliegue de la infraestructura, actualización de contenedores, backup y restauración de volúmenes, resolución de problemas comunes.

---

# Diagramas típicos

Topología de contenedores, redes Docker, dependencias entre servicios, flujo de tráfico, arquitectura de despliegue.

---

# Resultado esperado

Documentación completa de la infraestructura Docker que permita comprender la arquitectura de contenedores, identificar los servicios y sus relaciones, administrarla y **reproducir el entorno**.
