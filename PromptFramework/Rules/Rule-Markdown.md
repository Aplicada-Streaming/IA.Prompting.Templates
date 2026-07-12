# Rule — Markdown

## Objetivo

Establecer las reglas para la generación de documentación técnica en formato Markdown, garantizando uniformidad, claridad, mantenibilidad y facilidad de navegación.

---

## Organización del documento

Todo documento generado deberá:

- utilizar encabezados jerárquicos (`#`, `##`, `###`, `####`, ...);
- mantener una estructura lógica, desde los conceptos generales hacia los detalles específicos;
- dividir el contenido en secciones autocontenidas;
- evitar bloques extensos de texto cuando puedan dividirse naturalmente;
- incluir una tabla de contenidos cuando el tamaño del documento lo justifique.

No generar títulos vacíos.

No omitir niveles jerárquicos.

---

## Contenido

Cuando corresponda, incluir secciones como:

- Objetivo
- Alcance
- Introducción
- Definiciones
- Conceptos previos
- Arquitectura
- Componentes
- Configuración
- Funcionamiento
- Procedimientos
- Ejemplos
- Buenas prácticas
- Advertencias
- Observaciones
- Referencias
- Documentación relacionada

No agregar secciones que no aporten valor al documento.

---

## Estilo de redacción

La documentación deberá ser:

- técnica;
- clara;
- didáctica;
- objetiva;
- consistente.

Siempre que sea posible explicar:

- qué es;
- para qué sirve;
- cómo funciona;
- cuándo utilizarlo;
- por qué existe (cuando pueda inferirse de manera verificable).

Evitar:

- textos telegráficos;
- listas sin explicación;
- comandos sin contexto;
- definiciones ambiguas.

---

## Markdown

Utilizar cuando aporten claridad:

- listas
- listas numeradas
- tablas
- bloques de código
- citas
- notas
- advertencias
- enlaces internos
- referencias cruzadas

Evitar formatos innecesarios.

Priorizar siempre la legibilidad.

---

## Bloques de código

Todo bloque de código deberá:

- indicar el lenguaje cuando corresponda;
- ser lo más pequeño posible sin perder claridad;
- incluir contexto cuando resulte necesario.

No incluir código irrelevante.

---

## Diagramas

Cuando faciliten la comprensión, generar diagramas utilizando Mermaid.

Priorizar Mermaid frente a diagramas ASCII.

Cuando corresponda, generar diagramas de:

- arquitectura;
- flujo de procesos;
- secuencia;
- relaciones entre componentes;
- dependencias;
- topología de red;
- árbol de directorios.

No generar diagramas redundantes.

---

## Tablas

Utilizar tablas para resumir o comparar información.

Ejemplos:

- configuraciones;
- parámetros;
- versiones;
- servicios;
- puertos;
- dependencias;
- permisos;
- recursos.

Evitar tablas con texto excesivamente largo.

---

## Ejemplos

Siempre que sea posible utilizar ejemplos reales obtenidos durante la ejecución.

Cuando no sea posible:

- indicar claramente que se trata de un ejemplo ilustrativo;
- no presentar ejemplos ficticios como si fueran reales.

---

## Referencias cruzadas

Cuando exista documentación relacionada:

- evitar duplicar contenido;
- enlazar mediante rutas relativas;
- mantener la navegación entre documentos.

La documentación deberá favorecer el descubrimiento del resto del repositorio.

---

## Reutilización

Cada documento deberá poder comprenderse de forma independiente.

No asumir que el lector conoce otros documentos.

Cuando sea necesario, resumir brevemente el contexto antes de desarrollar un tema.

---

## Consistencia

Todos los documentos deberán mantener:

- la misma estructura general;
- el mismo estilo de escritura;
- la misma terminología;
- un nivel técnico coherente;
- un formato uniforme.

La documentación completa deberá percibirse como una única obra.

---

## Validación

Antes de finalizar la generación de un documento verificar que:

- la estructura sea coherente;
- no existan secciones vacías;
- no existan títulos duplicados;
- no existan contradicciones internas;
- los enlaces relativos sean válidos;
- los diagramas Mermaid sean sintácticamente correctos;
- los bloques de código sean legibles;
- el documento pueda comprenderse sin información externa innecesaria.

---

## Principios

Toda documentación generada deberá priorizar los siguientes principios:

1. Claridad sobre cantidad.
2. Comprensión sobre enumeración.
3. Explicación sobre descripción.
4. Consistencia sobre creatividad.
5. Reutilización sobre duplicación.
6. Evidencia sobre suposición.
7. Simplicidad sobre complejidad.
8. Mantenibilidad sobre volumen de contenido.