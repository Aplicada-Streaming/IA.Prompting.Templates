# Rule — Indexación y Recuperación de Contexto

## Objetivo

Establecer las reglas para la utilización, mantenimiento y actualización de la base de conocimiento del proyecto, permitiendo que los agentes recuperen únicamente el contexto necesario, reduzcan el consumo de tokens y mantengan sincronizada la documentación con la memoria operativa.

---

# Memoria operativa

La base de conocimiento constituye la memoria operativa del proyecto.

Antes de ejecutar cualquier tarea que pueda beneficiarse del contexto previamente documentado, el agente deberá consultar dicha memoria.

La ubicación de la base de conocimiento deberá obtenerse desde los parámetros del framework y no codificarse de forma fija.

---

# Recuperación de contexto

Antes de comenzar una tarea:

- identificar el contexto necesario;
- recuperar únicamente la información relevante;
- evitar cargar documentación innecesaria;
- minimizar el consumo de tokens.

No cargar la totalidad de la documentación cuando solamente sea necesario consultar una parte de ella.

---

# Utilización de índices

Cuando existan índices o documentos de navegación:

- utilizarlos como punto de entrada a la documentación;
- determinar qué documentos son relevantes;
- recuperar únicamente los necesarios.

Evitar recorrer el repositorio completo cuando exista información indexada.

---

# Actualización de la memoria

Si durante la ejecución se generan:

- nuevos documentos;
- modificaciones relevantes;
- reorganizaciones;
- nuevas relaciones entre documentos;

el agente deberá mantener sincronizada la base de conocimiento.

---

# Consistencia

Si la información obtenida durante la ejecución contradice la información indexada:

- priorizar siempre la evidencia verificable;
- actualizar la indexación;
- eliminar referencias obsoletas;
- mantener la coherencia de toda la base de conocimiento.

Nunca conservar información conocida como incorrecta.

---

# Detección de cambios

Al finalizar una tarea, verificar si existen cambios que afecten:

- la estructura documental;
- los índices;
- las referencias cruzadas;
- el mapa general de documentación.

Actualizar únicamente aquello que resulte necesario.

---

# Duplicación

Evitar almacenar la misma información en múltiples índices.

Cuando un dato ya exista:

- reutilizarlo;
- referenciarlo;
- actualizarlo si corresponde.

No duplicar conocimiento.

---

# Navegación

La indexación deberá facilitar:

- localizar rápidamente la documentación;
- comprender la organización del repositorio;
- descubrir documentación relacionada;
- minimizar búsquedas repetitivas.

La memoria deberá comportarse como un punto de entrada al conocimiento, no como una copia completa de la documentación.

---

# Recuperación incremental

Cuando el contexto requerido sea amplio:

1. consultar primero el índice principal;
2. identificar los índices secundarios relevantes;
3. recuperar únicamente los documentos necesarios;
4. ampliar el contexto únicamente si resulta insuficiente.

Priorizar siempre una recuperación incremental.

---

# Reindexación

Actualizar la indexación únicamente cuando:

- existan cambios reales;
- se creen nuevos documentos;
- cambie la estructura del repositorio;
- cambien las relaciones entre documentos;
- se detecten inconsistencias.

Evitar reconstruir completamente la indexación cuando una actualización parcial sea suficiente.

---

# Principios

Durante toda la ejecución priorizar los siguientes principios:

1. Recuperar antes que volver a inferir.
2. Reutilizar antes que duplicar.
3. Actualizar antes que reconstruir.
4. Minimizar el consumo de tokens.
5. Mantener la memoria sincronizada con la documentación.
6. Priorizar siempre información verificable.
7. La memoria debe facilitar el trabajo del agente, no reemplazar la documentación.