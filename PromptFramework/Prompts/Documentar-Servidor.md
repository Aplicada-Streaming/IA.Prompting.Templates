# Contexto

El proyecto administra un servidor Linux que requiere documentación técnica actualizada.

La documentación debe representar el estado real del servidor para facilitar su administración, mantenimiento, auditabilidad y eventual reconstrucción.

---

# Objetivo

Generar documentación técnica completa del servidor, representando fielmente su infraestructura, servicios, configuraciones y relaciones.

---

# Solicitudes

- Construir un inventario completo del servidor.
- Documentar sistema operativo y versión.
- Documentar hardware y recursos disponibles.
- Identificar aplicaciones instaladas.
- Documentar servicios configurados y en ejecución.
- Documentar infraestructura Docker (si aplica).
- Documentar configuración de red.
- Documentar almacenamiento y sistemas de archivos.
- Documentar usuarios y grupos.
- Documentar configuración de SSH.
- Documentar reglas de firewall.
- Documentar tareas programadas.
- Documentar mecanismos de backup.
- Documentar monitoreo.
- Generar diagramas de arquitectura.
- Actualizar la base de conocimiento.
- Actualizar los índices.

---

# Restricciones

- No modificar el estado del servidor.
- Ejecutar únicamente comandos de lectura.
- No instalar software.
- No reiniciar servicios.
- No inventar información.
- Toda afirmación deberá estar respaldada por evidencia verificable.

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Documentation.md`

## Parameters

Utilizar la configuración definida en:

- `/IA.Prompting.Templates/PromptFramework/Parameters`

---

# Resultado esperado

Al finalizar deberán existir:

- inventario del servidor;
- documentación de infraestructura;
- documentación de servicios;
- documentación de red;
- documentación de seguridad;
- documentación de monitoreo;
- diagramas de arquitectura;
- base de conocimiento actualizada;
- índices actualizados.