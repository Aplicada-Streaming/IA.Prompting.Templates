# Tool-Prompt — Auditoría técnica de seguridad de sistema web

> **Invocación**:
> - `Lee y ejecuta /IA/IA.Prompts/Tool-Prompts/Seguridad/Auditoria-Seguridad.md en {URL} con Usuario:{Usuario} y Clave:{Clave} y deja el informe en {destino}`

---

# Parámetros de invocación

| Parámetro | Descripción | Si no se indica |
|-----------|-------------|-----------------|
| `{URL}` | Dominio del sistema web en alcance | Solicitarlo al usuario antes de comenzar |
| `{Usuario}` | Usuario de la cuenta autorizada para las pruebas | Solicitarlo al usuario antes de comenzar |
| `{Clave}` | Clave de la cuenta autorizada | Solicitarla al usuario antes de comenzar |
| `{destino}` | Ruta del archivo Markdown único donde dejar el informe | Proponer `<sistema>.Auditoria-Seguridad.md` y confirmar |

---

# Contexto

`{URL}` es un sistema web autenticado cuyo titular autoriza esta auditoría de seguridad sobre su propio entorno.

- Dominio en alcance: `{URL}`
- Credenciales de prueba (cuenta propia del titular): usuario `{Usuario}`, clave `{Clave}`.

Antes de comenzar, confirmar que se cuenta con autorización explícita del titular del sistema para auditar `{URL}` dentro del alcance indicado. Sin esa confirmación, no iniciar las pruebas.


---

# Objetivo

Auditar la seguridad del portal web autenticado mediante pruebas autorizadas y no destructivas, y generar un informe técnico conforme al estándar de la industria (OWASP), con hallazgos priorizados por riesgo y remediación accionable.

---

# Solicitudes

- Reconocer la superficie expuesta del dominio en alcance: tecnologías, endpoints, roles y flujos de autenticación.
- Mapear funcionalidades, puntos de entrada y controles de acceso usando la cuenta autorizada.
- Ejecutar las pruebas por categoría del catálogo OWASP (Top 10 / WSTG) definido en el Profile, priorizando técnicas pasivas y de solo lectura.
- Analizar el riesgo de cada hallazgo (severidad, CVSS, impacto y probabilidad) y consolidar la remediación priorizada.
- Generar el informe técnico de seguridad como **un único archivo Markdown** en `{destino}`, con tabla de contenidos al inicio y la estructura estándar (resumen ejecutivo, alcance, metodología, hallazgos, matriz de riesgo, plan de remediación, anexos); los anexos van al final del mismo documento.

---

# Restricciones

- Operar solo dentro del alcance autorizado (dominio y cuenta indicados); no pivotar a otros subdominios, sistemas de terceros ni infraestructura fuera de alcance.
- Pruebas no destructivas: no alterar ni borrar datos, no degradar el servicio (sin fuerza bruta masiva ni DoS), no dejar artefactos persistentes. Ante una prueba de confirmación con posible efecto colateral, describirla como prueba potencial en vez de ejecutarla.
- Enmascarar credenciales y datos personales en el informe; no filtrar secretos operativos ni datos reales.
- No inventar vulnerabilidades: todo hallazgo confirmado debe tener evidencia reproducible; lo no confirmado se marca como «requiere verificación manual».

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Web-Security-Audit.md`
