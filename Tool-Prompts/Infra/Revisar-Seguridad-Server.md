# Tool-Prompt — Revisar Seguridad de Servidor

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Infra/Revisar-Seguridad-Server.md en {sistema}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{sistema}` | Servidor, host o proyecto sobre el que se hace la revisión de seguridad | Solicitarlo al usuario antes de comenzar |

---

# Contexto

`{sistema}` requiere una revisión de seguridad para identificar vulnerabilidades, configuraciones inadecuadas y oportunidades de mejora en su postura de seguridad. La revisión es de solo lectura.

---

# Objetivo

Identificar vulnerabilidades, configuraciones incorrectas y recomendaciones de mejora, respaldadas por evidencia verificable y diferenciando hallazgos verificados de riesgos potenciales.

---

# Solicitudes

- Revisar configuración de SSH y acceso remoto, reglas de firewall y políticas de red.
- Revisar usuarios, grupos, permisos y servicios expuestos.
- Revisar configuraciones de autenticación y gestión de secretos y credenciales.
- Identificar software con versiones obsoletas y configuraciones inseguras (incluidos contenedores Docker, si aplica).
- Documentar cada vulnerabilidad con su severidad y su evidencia de respaldo.
- Generar recomendaciones de mejora priorizadas y actualizar la documentación de seguridad.
- Diferenciar los hallazgos en: vulnerabilidades verificadas, configuraciones inadecuadas, riesgos potenciales y recomendaciones.

---

# Restricciones

- No modificar configuraciones durante la revisión ni instalar software.
- No ejecutar comandos destructivos.
- No inventar vulnerabilidades; toda observación debe estar respaldada por evidencia.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Audit.md`
