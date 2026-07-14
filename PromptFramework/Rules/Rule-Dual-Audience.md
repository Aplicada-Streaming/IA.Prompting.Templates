# Rule — Dual-Audience

## Objetivo

Toda documentación generada sirve a dos audiencias a la vez: personas que necesitan **comprender** y agentes de IA que necesitan **extraer datos y razonar**. Esta regla fija los recursos mínimos de cada cara y su coherencia.

---

# Cara humana — recursos narrativos y didácticos

- Abrir cada documento con un **resumen ejecutivo** breve: qué es, para qué sirve, a quién le sirve.
- Narrar los flujos importantes **de punta a punta con un caso concreto** («qué pasa desde que el usuario aprieta Reservar»), con datos de ejemplo realistas pero sintéticos; la narrativa complementa al diagrama, no lo repite.
- Definir cada término en su primer uso y registrarlo en el glosario; usar analogías cuando acerquen un concepto complejo.
- Progresar de lo general a lo específico; cerrar las secciones densas con **preguntas guía** que ayuden al lector a formar criterio.
- Contextualizar todo ejemplo o snippet: qué demuestra, precondiciones, resultado esperado.

---

# Cara agente — contrato máquina-legible

- **Frontmatter YAML** en todo documento: `doc_id`, `doc_type`, `title`, `status`, `origin`, `confidence` (si `origin != human`), `owner`, `last_review`, `audience`, `traces` — según el marco de referencia que aplique el Profile.
- **IDs estables con prefijo** (`RF-`, `RNF-`, `ADR-`, `TC-`, `RB-`, …): los enlaces y las trazas apuntan al ID, no a la ruta.
- **Encabezados y anclas predecibles**: los documentos del mismo tipo comparten las mismas secciones, lo que permite parseo y validación por estructura.
- **Diagramas y modelos como código** (Mermaid, dbml, OpenAPI): diffeables y regenerables; imágenes binarias solo cuando no existe alternativa.
- **Bloques para agentes** (`entradas` / `salidas` / `validaciones`) en los documentos que definan un proceso que un agente deba ejecutar o verificar.
- **Snippets con procedencia** (ruta + rango + versión de la fuente); nunca copias sin origen.

---

# Coherencia entre caras

- Las dos caras describen el mismo hecho; ante divergencia, corregir: nunca mantener versiones paralelas (única fuente de verdad, `Rule-Documentation.md`).
- El vocabulario narrativo y el máquina-legible comparten el mismo glosario; los sinónimos se registran como alias del término canónico.
