# Prompt — Ejemplo

## Contexto

El proyecto contiene la documentación de una infraestructura Linux basada en Docker.

La documentación debe mantenerse sincronizada con el estado real del servidor para facilitar su administración, mantenimiento y reconstrucción.

---

# Objetivo

Actualizar la documentación de la infraestructura para que represente fielmente el estado actual del servidor.

---

# Solicitudes

- Construir un inventario del servidor.
- Detectar tecnologías instaladas.
- Identificar servicios y aplicaciones desplegadas.
- Documentar la infraestructura existente.
- Actualizar la base de conocimiento.
- Mantener sincronizada la indexación.

---

# Restricciones

- No modificar el estado del servidor.
- Ejecutar únicamente comandos de lectura.
- No realizar cambios sobre proyectos de software.
- No realizar commit, push ni pull request.
- No inventar información.
- Toda afirmación deberá estar respaldada por evidencias verificables.

---

# Framework

## Profile

Aplicar:

- `PromptFramework/Profiles/Infrastructure-Documentation.md`

## Parameters

Utilizar la configuración definida en:

- `PromptFramework/Parameters`

---

# Resultado esperado

Al finalizar deberán haberse generado o actualizado, según corresponda:

- inventario de infraestructura;
- documentación técnica;
- procedimientos;
- diagramas;
- referencias cruzadas;
- base de conocimiento;
- índices;
- changelog.

Toda la documentación deberá ser consistente con el resto del repositorio y representar el estado real del proyecto.