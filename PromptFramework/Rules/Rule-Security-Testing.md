# Rule — Security-Testing

## Objetivo

Fijar el comportamiento del agente al relevar la seguridad de un sistema (web, API o aplicación): pruebas autorizadas y no destructivas, metodología alineada a estándares de la industria y hallazgos clasificados por severidad con evidencia reproducible.

---

# Autorización y ética

- Actuar **solo bajo autorización explícita** del titular del sistema. El prompt debe declarar quién autoriza y sobre qué alcance; ante autorización ausente o ambigua, detenerse y solicitarla.
- Ceñirse al **alcance declarado**: dominios, hosts, aplicaciones y cuentas indicados. No pivotar hacia sistemas de terceros, subdominios fuera de alcance ni infraestructura no autorizada.
- Encuadre defensivo: el fin es identificar y remediar debilidades, nunca explotarlas más allá de lo necesario para demostrar el riesgo.

---

# Pruebas no destructivas

- Preferir siempre técnicas pasivas y de solo lectura; usar pruebas activas únicamente cuando sean necesarias para confirmar un hallazgo.
- No: alterar o borrar datos de producción, escalar de forma persistente, instalar backdoors, exfiltrar datos reales, degradar el servicio (DoS, fuerza bruta masiva) ni dejar artefactos sin registrar.
- Si una prueba de confirmación pudiera tener efecto colateral, **describirla como prueba potencial** en vez de ejecutarla, y proponer cómo validarla en un entorno controlado.
- Registrar toda acción activa (payload, endpoint, cuenta, marca temporal) para trazabilidad y reversión.

---

# Metodología (estándar de la industria)

Encarar el relevamiento por fases y mapear cada prueba a un estándar reconocido:

| Fase | Actividad |
|------|-----------|
| Reconocimiento | Superficie expuesta, tecnologías, endpoints, roles y flujos de autenticación |
| Mapeo | Funcionalidades, puntos de entrada, controles de acceso y confianza |
| Pruebas | Ejecución por categoría contra el catálogo del estándar |
| Análisis de riesgo | Severidad, probabilidad e impacto de cada hallazgo |
| Reporte | Consolidación priorizada con remediación |

- Referenciar el estándar aplicable: **OWASP Top 10**, **OWASP WSTG** (Web Security Testing Guide), **OWASP ASVS** o **OWASP API Security Top 10** según corresponda. El Profile fija el catálogo concreto a cubrir.
- Cubrir como mínimo: autenticación y gestión de sesión, control de acceso (vertical y horizontal / IDOR), validación de entradas (inyección, XSS), exposición de datos sensibles, configuración de seguridad y cabeceras, gestión de errores y logging, transporte (TLS) y dependencias con vulnerabilidades conocidas.

---

# Clasificación de hallazgos

- Asignar a cada hallazgo una **severidad** (`Crítica`, `Alta`, `Media`, `Baja`, `Informativa`) derivada de impacto y probabilidad; usar **CVSS** cuando aplique e indicar el vector.
- Cada hallazgo declara: título, categoría del estándar (p. ej. `WSTG-ATHN-01`, `A01:2021`), activos afectados, precondiciones, evidencia de reproducción, impacto y remediación concreta.
- Evidencia y trazabilidad se rigen por `Rule-Evidences.md`: no reportar como confirmado lo no verificado; los falsos positivos potenciales se marcan como «requiere verificación manual».
- Priorizar la remediación por riesgo; distinguir vulnerabilidad confirmada, configuración inadecuada, riesgo potencial y recomendación de mejora.

---

# Manejo de credenciales y datos sensibles

- Tratar credenciales, tokens y datos personales como secretos: no incluirlos en claro en el informe ni en logs; enmascararlos (`fer***`, `29*****`) y referenciar su origen sin exponerlo.
- No conservar ni difundir datos reales extraídos durante las pruebas; usar el mínimo necesario para demostrar el hallazgo.
- El informe entregable no debe filtrar secretos operativos ni facilitar la explotación por terceros más allá de lo imprescindible para remediar.
