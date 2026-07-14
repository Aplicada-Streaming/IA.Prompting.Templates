# Examples

Prompts completos y funcionales que demuestran el framework en escenarios reales. Sirven para **copiar, reemplazar los placeholders y ejecutar**. Cada uno abre con una cabecera `> **Uso**` y sigue el núcleo de 5 secciones.

Los `Example-*` son ejemplos pulidos que reutilizan un **Profile**; el resto son prompts reales que fueron funcionando y muestran el uso directo de un **RuleSet** (`Lean` para análisis simple, `Default` para trabajo con entregables).

Referencia: [Cómo escribir cada sección](../Guides/How-To.md) · [Templates](../Templates/README.md)

---

## Catálogo

| Ejemplo | Escenario | Framework |
|---------|-----------|-----------|
| [Example-Auditoria](Example-Auditoria.md) | Auditoría técnica de un servidor Linux (solo lectura) | Profile `Infrastructure-Audit` |
| [Example-Documentar-Infra](Example-Documentar-Infra.md) | Documentación de infraestructura Linux con Docker | Profile `Infrastructure-Documentation` |
| [Example-Mantener-Guias](Example-Mantener-Guias.md) | Mantenimiento de las guías del framework: secciones para agentes automáticos + coherencia | RuleSet `Documentation` |
| [Reconfiguracion-IP-Host](Reconfiguracion-IP-Host.md) | Reconfigurar la IP propia de un contenedor siguiendo un modelo | Profile `Architecture-Review` |
| [Analisis-Comportamiento-Software](Analisis-Comportamiento-Software.md) | Diagnóstico de un bug de UI en una app MAUI | RuleSet `Lean` |
| [Analisis-MyAI-NoUpdate](Analisis-MyAI-NoUpdate.md) | Investigación de alternativas para correr IA local en un servidor | RuleSet `Lean` |
| [Crear-Relevamiento-CameraIP-NoUpdate](Crear-Relevamiento-CameraIP-NoUpdate.md) | Relevamiento/plan sobre cámaras IP | RuleSet `Lean` |
| [Consulta-Ciclo-Inicio-Server](Consulta-Ciclo-Inicio-Server.md) | Comportamiento de Docker ante ciclos de energía + propuesta UPS/SAI | RuleSet `Default` |
| [Configurar-IP-Static-NoUpdate](Configurar-IP-Static-NoUpdate.md) | Configurar una IP estática en el host | RuleSet `Default` |
| [Crear-Contenedor-MyAI-NoUpdate](Crear-Contenedor-MyAI-NoUpdate.md) | Diseñar el docker-compose de un servicio de IA local | RuleSet `Default` |
| [Crear-Contenedor-Print3d-NoUpdate](Crear-Contenedor-Print3d-NoUpdate.md) | Contenerizar Repetier-Server para impresión 3D | RuleSet `Default` |
| [Crear-Contenedor-Web-NoUpdate](Crear-Contenedor-Web-NoUpdate.md) | Servicio web contenerizado | RuleSet `Default` |

---

## Cómo usar un Example

1. Elegí el ejemplo cuyo escenario se parezca al tuyo.
2. Copiá su contenido y reemplazá los datos concretos (rutas, IP, nombres) por los de tu entorno.
3. Ajustá el Profile/RuleSet si tu tarea cambia de naturaleza.
4. Ejecutá.

Para construir uno desde cero en lugar de partir de un ejemplo, usá un [Template](../Templates/README.md).
