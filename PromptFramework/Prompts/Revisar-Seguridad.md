# Contexto

El proyecto requiere una revisión de seguridad para identificar posibles vulnerabilidades, configuraciones inadecuadas y oportunidades de mejora en la postura de seguridad del sistema.

---

# Objetivo

Realizar una revisión de seguridad del sistema, identificando vulnerabilidades, configuraciones incorrectas y recomendaciones de mejora, respaldadas por evidencia verificable.

---

# Solicitudes

- Revisar configuración de SSH y acceso remoto.
- Revisar reglas de firewall y políticas de red.
- Revisar usuarios, grupos y permisos.
- Revisar servicios expuestos.
- Revisar configuraciones de autenticación.
- Revisar gestión de secretos y credenciales.
- Identificar software con versiones obsoletas.
- Revisar configuraciones de contenedores Docker (si aplica).
- Identificar configuraciones inseguras.
- Documentar vulnerabilidades encontradas.
- Generar recomendaciones de mejora.
- Actualizar la documentación de seguridad.
- Registrar evidencias de cada hallazgo.

---

# Restricciones

- No modificar configuraciones durante la revisión.
- No instalar software.
- No ejecutar comandos destructivos.
- No inventar vulnerabilidades.
- Toda observación deberá estar respaldada por evidencia.
- Diferenciar claramente hallazgos verificados de riesgos potenciales.

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/Infrastructure-Audit.md`

## Parameters

Utilizar la configuración definida en:

- `/IA.Prompting.Templates/PromptFramework/Parameters`

---

# Resultado esperado

Al finalizar deberán existir:

- inventario de hallazgos de seguridad;
- descripción de vulnerabilidades identificadas;
- evaluación de severidad de cada hallazgo;
- evidencias que respalden cada observación;
- recomendaciones de mejora priorizadas;
- documentación de seguridad actualizada.

Todos los hallazgos deberán diferenciarse claramente entre:

- vulnerabilidades verificadas;
- configuraciones inadecuadas;
- riesgos potenciales;
- recomendaciones de mejora.