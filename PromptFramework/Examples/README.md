# Examples

Prompts completos y funcionales que demuestran el framework en escenarios reales. Sirven para **copiar, reemplazar los placeholders y ejecutar**. Cada uno abre con una cabecera `> **Uso**` y sigue el núcleo de 5 secciones.

Los `Example-*` son ejemplos pulidos que reutilizan un **Profile** o un **RuleSet**.

Referencia: [Cómo escribir cada sección](../Guides/How-To.md) · [Templates](../Templates/README.md)

---

## Catálogo

| Ejemplo | Escenario | Framework |
|---------|-----------|-----------|
| [Example-Auditoria](Example-Auditoria.md) | Auditoría técnica de un servidor Linux (solo lectura) | Profile `Infrastructure-Audit` |
| [Example-Mantener-Guias](Example-Mantener-Guias.md) | Mantenimiento de las guías del framework: secciones para agentes automáticos + coherencia | RuleSet `Documentation` |

---

## Cómo usar un Example

1. Elegí el ejemplo cuyo escenario se parezca al tuyo.
2. Copiá su contenido y reemplazá los datos concretos (rutas, IP, nombres) por los de tu entorno.
3. Ajustá el Profile/RuleSet si tu tarea cambia de naturaleza.
4. Ejecutá.

Para construir uno desde cero en lugar de partir de un ejemplo, usá un [Template](../Templates/README.md).
