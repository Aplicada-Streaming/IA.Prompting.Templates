# Auditoría técnica de un servidor Linux

## Contexto

Se requiere realizar una auditoría técnica completa sobre un servidor Linux con el objetivo de conocer su estado actual, detectar configuraciones relevantes, identificar posibles inconsistencias y actualizar la documentación existente.

El servidor deberá analizarse sin modificar su estado.

La documentación generada deberá permitir comprender la infraestructura actual y servir como evidencia técnica de la auditoría realizada.

---

# Objetivo

Realizar una auditoría integral del servidor, generando un informe técnico respaldado por evidencias verificables y manteniendo sincronizada la documentación y la base de conocimiento del proyecto.

---

# Solicitudes

- Construir un inventario completo del servidor.
- Identificar el sistema operativo y su configuración.
- Auditar hardware y recursos disponibles.
- Detectar aplicaciones instaladas.
- Detectar servicios configurados.
- Detectar servicios en ejecución.
- Auditar contenedores Docker.
- Auditar redes.
- Auditar almacenamiento.
- Auditar usuarios y grupos.
- Auditar permisos relevantes.
- Auditar configuración de SSH.
- Auditar firewall.
- Auditar tareas programadas.
- Auditar mecanismos de backup.
- Auditar monitoreo.
- Auditar automatizaciones.
- Detectar inconsistencias entre la documentación existente y el estado actual del servidor.
- Actualizar la documentación afectada.
- Actualizar la base de conocimiento.
- Actualizar la indexación.
- Actualizar el changelog documental.

---

# Restricciones

- No modificar el servidor.
- Ejecutar únicamente comandos de lectura.
- No instalar software.
- No actualizar paquetes.
- No reiniciar servicios.
- No eliminar archivos.
- No modificar configuraciones.
- No realizar commit, push ni pull request.
- No inventar información.
- Toda conclusión deberá estar respaldada por evidencias verificables.

---

# Framework

## Profile

Aplicar:

- `PromptFramework/Profiles/Infrastructure-Audit.md`

## Parameters

Utilizar la configuración definida en:

- `PromptFramework/Parameters`

---

# Resultado esperado

Al finalizar la auditoría deberán haberse generado o actualizado, según corresponda:

- inventario del servidor;
- documentación técnica;
- documentación de arquitectura;
- documentación de servicios;
- documentación de redes;
- documentación de almacenamiento;
- documentación de seguridad;
- documentación de monitoreo;
- documentación de automatización;
- observaciones de auditoría;
- inconsistencias detectadas;
- base de conocimiento;
- índices;
- changelog.

Toda la documentación deberá representar el estado real del servidor y mantener consistencia con el resto del repositorio.