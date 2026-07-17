# Rule — Narrative-Voice

## Objetivo

Que la prosa de todo entregable escrito se lea como redactada por un profesional del dominio: técnica, formal y precisa, con ritmo y criterio propios de un autor humano. No cambia qué se dice ni la estructura del documento; regula **cómo se redacta la prosa** para eliminar los patrones que delatan un texto generado en serie.

Aplica solo a las **zonas de prosa** (resúmenes, análisis, impacto, racional, recomendaciones, narración de flujos). No altera las **zonas estructuradas** que otras reglas fijan —frontmatter, IDs con prefijo, tablas, matrices, anclas predecibles, diagramas como código (`Rule-Dual-Audience.md`, `Rule-Markdown.md`)—, que se mantienen rígidas a propósito.

---

# Voz

- Escribir desde el criterio de un analista que entiende el sistema, no desde un molde: cada sección responde a lo que ese caso concreto requiere, no a una plantilla rellenada.
- Formal y técnica, sin acartonamiento: se admite afirmar con seguridad cuando hay evidencia, y señalar incertidumbre cuando la hay, sin hedging defensivo.
- Vocabulario del dominio del sistema auditado o documentado; términos precisos por sobre genéricos.

---

# Ritmo y estructura de la prosa

- **Variar la longitud de frase**: alternar frases cortas y largas. Un texto donde todas las oraciones tienen el mismo largo y forma se percibe como automático.
- **Prosa donde corresponde prosa**: causa → efecto → impacto se narra en un párrafo conectado, no se fragmenta en viñetas sueltas. Reservar las listas para enumeraciones reales (pasos, ítems, opciones), no para esquivar la redacción.
- **Sin paralelismo forzado**: no todas las viñetas de una lista tienen que empezar igual ni tener la misma extensión; la simetría perfecta delata generación.
- **Abrir con contenido, no con el título**: la primera frase de una sección aporta un hecho o contexto; no reformula el encabezado ni anuncia lo que la sección "va a" tratar.

---

# Patrones a evitar (tells de texto generado)

- **Muletillas de relleno**: «Es importante destacar/señalar/mencionar que», «Cabe destacar», «En resumen», «En conclusión», «Como se puede observar», «Vale la pena mencionar».
- **Conectores decorativos encadenados**: «Además», «Asimismo», «Por otro lado», «Por consiguiente» usados como pegamento entre frases que no lo necesitan.
- **Cierres genéricos**: párrafos finales que resumen lo ya dicho sin agregar información o recomendación concreta.
- **Sobre-explicación de lo obvio** y **restatear el título** de la sección en su primera oración.
- **Doble audiencia mal entendida**: no convertir en prosa lo que debe ir en tabla o campo estructurado, ni al revés.

---

# Coherencia

- La voz es uniforme en todo el documento y entre documentos del mismo conjunto: se percibe una sola autoría (`Rule-Markdown.md`).
- Esta regla ajusta la redacción; no habilita omitir secciones, IDs, evidencias ni campos que otras reglas exijan. Ante conflicto, prevalece la regla estructural y esta se aplica solo dentro de la prosa resultante.

---

# Validación

Antes de finalizar, releer las zonas de prosa y verificar: no hay muletillas de la lista anterior; la longitud de frase varía; no hay listas que deberían ser párrafos; ninguna sección abre reformulando su título; los cierres aportan algo. Si un párrafo se puede borrar sin perder información, sobra.
