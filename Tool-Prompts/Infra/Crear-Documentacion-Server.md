# Tool-Prompt — Crear Documentación de Servidor

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Infra/Crear-Documentacion-Server.md de {servidor} en {destino}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{servidor}` | Servidor o host Linux a documentar (acceso, nombre o proyecto que lo administra) | Solicitarlo al usuario antes de comenzar |
| `{destino}` | Dónde escribir la documentación | El repositorio del proyecto que administra el servidor |

---

# Contexto

El servidor Linux `{servidor}` requiere documentación técnica que represente su estado real, para facilitar su administración, mantenimiento, auditabilidad y eventual reconstrucción.

---

# Objetivo

Generar documentación técnica completa del servidor, representando fielmente su infraestructura, servicios, configuraciones y relaciones.

---

# Solicitudes

- Construir un inventario completo del servidor.
- Documentar sistema operativo, versión, hardware y recursos disponibles.
- Identificar aplicaciones instaladas y servicios configurados y en ejecución.
- Documentar infraestructura Docker (si aplica).
- Documentar red, almacenamiento y sistemas de archivos.
- Documentar usuarios, grupos, configuración de SSH y reglas de firewall.
- Documentar tareas programadas, mecanismos de backup y monitoreo.
- Generar diagramas de arquitectura.
- Actualizar la base de conocimiento y los índices en `{destino}`.

---

# Restricciones

- No modificar el estado del servidor; ejecutar únicamente comandos de lectura.
- No instalar software ni reiniciar servicios.
- No inventar información; toda afirmación debe estar respaldada por evidencia verificable.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
