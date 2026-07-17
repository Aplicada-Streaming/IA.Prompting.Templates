# Tool-Prompt — Documentar Docker

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Documentar-Docker.md en {proyecto}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{proyecto}` | Proyecto, host o ruta cuya infraestructura Docker se documenta | Solicitarlo al usuario antes de comenzar |
| `{destino}` | Dónde escribir la documentación | El repositorio del proyecto |

---

# Contexto

La infraestructura de contenedores Docker de `{proyecto}` requiere documentación técnica que permita comprender su arquitectura, administrarla y reconstruirla cuando sea necesario.

---

# Objetivo

Generar documentación técnica completa de la infraestructura Docker, representando fielmente los contenedores, redes, volúmenes, configuraciones y relaciones existentes.

---

# Solicitudes

- Construir un inventario de la infraestructura Docker: imágenes, versiones y contenedores (en ejecución y detenidos).
- Documentar redes Docker, volúmenes, puntos de montaje y puertos expuestos.
- Analizar los archivos Docker Compose e identificar dependencias entre contenedores.
- Generar diagramas de arquitectura de contenedores.
- Documentar procedimientos de despliegue y mantenimiento.
- Actualizar la base de conocimiento y los índices en `{destino}`.

---

# Restricciones

- No modificar configuraciones de Docker ni reiniciar contenedores.
- No inventar información; toda afirmación debe estar respaldada por evidencia verificable.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Docker-Documentation.md`
