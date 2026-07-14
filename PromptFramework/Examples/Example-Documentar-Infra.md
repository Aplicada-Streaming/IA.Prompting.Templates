# Documentación de infraestructura Linux con Docker

> **Uso**: copiá este prompt, reemplazá los datos concretos por los de tu entorno y ejecutá.

---

# Contexto

El proyecto administra un servidor Linux de producción que aloja múltiples servicios basados en Docker.

El servidor no cuenta actualmente con documentación técnica actualizada. Se requiere generar documentación completa que permita comprender la infraestructura, administrarla y reconstruirla en caso de ser necesario.

---

# Objetivo

Generar documentación técnica completa del servidor y su infraestructura Docker, representando fielmente el estado actual del entorno.

---

# Solicitudes

- Construir un inventario del servidor.
- Documentar el sistema operativo y su configuración.
- Documentar hardware y recursos disponibles.
- Identificar aplicaciones instaladas.
- Documentar todos los servicios en ejecución.
- Documentar la infraestructura Docker (contenedores, redes, volúmenes, imágenes).
- Analizar los archivos Docker Compose presentes.
- Documentar la configuración de red del servidor.
- Documentar la configuración de almacenamiento.
- Documentar usuarios y grupos relevantes.
- Generar diagramas de arquitectura con Mermaid.
- Actualizar la base de conocimiento del proyecto y los índices documentales.
- Entregar la documentación (infraestructura, servicios Docker, redes, almacenamiento y diagramas) consistente con el resto del repositorio y fiel al estado real del servidor.

---

# Restricciones

- No modificar el estado del servidor.
- Ejecutar únicamente comandos de lectura.
- No instalar software.
- No reiniciar servicios.
- No realizar commit, push ni pull request.
- No inventar información.
- Toda afirmación deberá estar respaldada por evidencias verificables.

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`