<!-- Ejemplo de un prompt completo ya redactado con el núcleo de 5 secciones. -->

# Contexto

El proyecto contiene la documentación de una infraestructura Linux basada en Docker. La documentación quedó desactualizada respecto del estado real del servidor y debe volver a representarlo fielmente para facilitar su administración, mantenimiento y reconstrucción.

---

# Objetivo

Actualizar la documentación de la infraestructura para que represente fielmente el estado actual del servidor.

---

# Solicitudes

- Construir un inventario del servidor.
- Detectar tecnologías instaladas, servicios y aplicaciones desplegadas.
- Documentar la infraestructura existente y sus relaciones.
- Actualizar la base de conocimiento y mantener sincronizada la indexación.
- Generar o actualizar, según corresponda: inventario, documentación técnica, procedimientos, diagramas, referencias cruzadas, índices y changelog.

---

# Restricciones

- No modificar el estado del servidor; ejecutar únicamente comandos de lectura.
- No realizar cambios sobre proyectos de software.
- No realizar commit, push ni pull request.
- No inventar información; toda afirmación debe estar respaldada por evidencia verificable.

---

# Framework

## Profile

Aplicar:

- `/IA/IA.Prompts/PromptFramework/Profiles/Infrastructure-Documentation.md`
