# Rule — Documentation

## Objetivo

Reglas para generar documentación técnica que represente fielmente el sistema y preserve el conocimiento necesario para operarlo, mantenerlo y evolucionarlo.

---

# Contenido

- Documentar el **estado real** del sistema; nunca configuraciones hipotéticas. Lo no verificable se marca como tal.
- Explicar, no solo describir: qué es, para qué sirve, cómo funciona, cuándo se usa, cómo se relaciona con el resto.
- Documentar relaciones (dependencias, servicios, redes, procesos) para dar visión integral.
- Adecuar la profundidad al tema: ni superficial ni innecesariamente extensa.
- Incorporar el contexto suficiente; no asumir que el lector conoce el proyecto ni la documentación previa.

---

# Procedimientos y arquitectura

- Un procedimiento explica: objetivo, prerrequisitos, pasos, resultado esperado, validaciones y errores posibles. No es una lista de comandos.
- La arquitectura documenta componentes, responsabilidades, relaciones, flujos y límites; no la enumeración de archivos.

---

# Organización

- Un dato vive en un solo documento; el resto lo referencia (única fuente de verdad).
- Documentos pequeños y especializados, con una única responsabilidad cada uno.
- Mantener la documentación sincronizada con el sistema: actualizar lo afectado y eliminar lo obsoleto.

---

# Verificación de calidad

Antes de finalizar: la documentación representa el sistema real, es consistente con el repositorio, no duplica ni contradice, y facilita la comprensión del tema.
