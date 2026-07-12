# Parameters

## Objetivo

Este documento define los parámetros de configuración utilizados por el Prompt Framework.

Los parámetros permiten desacoplar las reglas, plantillas y prompts de una estructura específica de repositorios o rutas físicas, haciendo que el framework pueda reutilizarse en distintos proyectos sin modificar las reglas.

---

# Principios

Todos los componentes del framework deberán utilizar parámetros en lugar de rutas, nombres o valores codificados.

Las reglas, plantillas y prompts deberán obtener la configuración desde los documentos ubicados en la carpeta `Parameters`.

---

# Tipos de parámetros

Los parámetros del framework se organizan en las siguientes categorías:

| Categoría | Descripción |
|-----------|-------------|
| Repositories | Define los repositorios utilizados por el proyecto. |
| Paths | Define las rutas relevantes dentro de los repositorios. |
| Variables | Define variables generales utilizadas por el framework. |

---

# Resolución de parámetros

Antes de ejecutar una tarea, el agente deberá:

1. cargar los parámetros necesarios;
2. resolver las referencias utilizadas por las reglas y plantillas;
3. utilizar siempre los valores resueltos durante la ejecución.

---

# Prioridad

Cuando un parámetro exista en más de un lugar, deberá respetarse el siguiente orden de prioridad:

1. Parámetro definido explícitamente en el prompt.
2. Parámetro definido por el proyecto.
3. Parámetro definido en este framework.
4. Valor por defecto (si existiera).

---

# Buenas prácticas

Siempre que sea posible:

- utilizar parámetros en lugar de rutas literales;
- evitar valores codificados;
- centralizar la configuración;
- reutilizar parámetros existentes;
- eliminar parámetros obsoletos.

---

# Parámetros obligatorios

El framework espera que, como mínimo, puedan resolverse los siguientes grupos de información:

- repositorios;
- rutas principales;
- ubicación de la documentación;
- ubicación de la base de conocimiento;
- ubicación de los prompts.

Cada proyecto podrá incorporar parámetros adicionales según sus necesidades.

---

# Extensibilidad

Los proyectos podrán definir nuevos parámetros sin modificar las reglas del framework.

Las nuevas variables deberán documentarse dentro de la carpeta `Parameters`.

---

# Convención de uso

Las reglas y plantillas deberán hacer referencia a los parámetros mediante su nombre lógico y nunca mediante valores concretos.

Ejemplo conceptual:

- Repositorio de documentación
- Ruta de la base de conocimiento
- Carpeta de documentación generada

En lugar de utilizar rutas específicas como:

- `/Infra.Documentacion`
- `/Bot.Documentacion`
- `/MiProyecto.Documentacion`

---

# Principios

Durante toda la ejecución deberán respetarse los siguientes principios:

1. Configuración centralizada.
2. Reutilización.
3. Independencia del proyecto.
4. Mantenibilidad.
5. Portabilidad.
6. Consistencia.