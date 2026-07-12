# Rule — Markdown

## Objetivo

Reglas de formato y estructura para toda la documentación Markdown generada.

---

# Estructura

- Encabezados jerárquicos sin saltar niveles ni títulos vacíos; de lo general a lo específico.
- Secciones autocontenidas; tabla de contenidos cuando el tamaño lo justifique.
- Secciones típicas cuando aporten valor: Objetivo, Alcance, Arquitectura, Configuración, Procedimientos, Ejemplos, Observaciones, Referencias. No agregar secciones vacías o decorativas.

---

# Redacción

Estilo técnico, claro, didáctico y consistente. Evitar: texto telegráfico, listas sin explicación, comandos sin contexto, definiciones ambiguas.

Todos los documentos del repositorio mantienen la misma estructura, terminología y estilo: la documentación se percibe como una única obra.

---

# Elementos

| Elemento | Uso |
|----------|-----|
| Tablas | Resumir o comparar (configuraciones, parámetros, servicios, puertos); sin celdas de texto largo |
| Bloques de código | Con lenguaje indicado, mínimos y con contexto; sin código irrelevante |
| Diagramas | Mermaid (preferido sobre ASCII) para arquitectura, flujos, secuencias, dependencias; sin diagramas redundantes |
| Ejemplos | Reales, obtenidos en la ejecución; los ilustrativos se marcan como tales |
| Enlaces | Rutas relativas entre documentos relacionados; referenciar en lugar de duplicar |

---

# Validación

Antes de finalizar un documento: estructura coherente, sin secciones vacías ni títulos duplicados, enlaces válidos, Mermaid sintácticamente correcto, comprensible sin información externa innecesaria.
