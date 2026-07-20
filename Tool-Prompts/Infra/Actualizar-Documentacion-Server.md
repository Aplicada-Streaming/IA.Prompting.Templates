# Tool-Prompt — Actualizar Documentación de Servidor

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Infra/Actualizar-Documentacion-Server.md en {destino}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{destino}` | Ubicación de la documentación del servidor a actualizar | Solicitarlo al usuario antes de comenzar |
| `{servidor}` | Servidor o host Linux al que corresponde la documentación | Deducirlo de la documentación existente en `{destino}`; si no puede deducirse, solicitarlo al usuario |

---

# Contexto

La documentación del servidor `{servidor}` existente en `{destino}` fue generada en un momento anterior y puede haber quedado desactualizada respecto del estado real del host: servicios, contenedores, versiones, red, usuarios y tareas programadas cambian con la operación.

---

# Objetivo

Sincronizar la documentación existente con el estado real del servidor: corregir lo que cambió, completar lo que falta, retirar lo que ya no existe y preservar lo que sigue siendo válido.

---

# Solicitudes

- Leer la documentación existente en `{destino}` e identificar su alcance, fecha y prompt generador.
- Relevar el estado actual del servidor con comandos de solo lectura, sobre los mismos dominios que documenta el material existente: sistema operativo y hardware, aplicaciones y servicios, Docker, red, almacenamiento y sistemas de archivos, usuarios, grupos, SSH y firewall, tareas programadas, backups y monitoreo.
- Comparar estado relevado contra documentación y clasificar cada diferencia en: sin cambios, desactualizado, faltante u obsoleto.
- Actualizar únicamente los documentos afectados, conservando su estructura y estilo.
- Documentar los componentes nuevos que no estaban cubiertos.
- Marcar como retirado —no borrar sin reemplazo— lo que ya no existe en el servidor.
- Regenerar los diagramas de arquitectura cuyas relaciones hayan cambiado.
- Actualizar la base de conocimiento, los índices y las referencias cruzadas en `{destino}`.
- Registrar en el changelog documental qué cambió, con fecha y evidencia.
- Informar al usuario un resumen de diferencias detectadas y documentos actualizados.

---

# Restricciones

- No modificar el estado del servidor; ejecutar únicamente comandos de lectura.
- No instalar software ni reiniciar servicios.
- No regenerar desde cero la documentación existente: aplicar mínima intervención sobre lo que cambió.
- No eliminar documentación útil sin reemplazarla.
- No inventar información; toda afirmación debe estar respaldada por evidencia verificable del relevamiento.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
