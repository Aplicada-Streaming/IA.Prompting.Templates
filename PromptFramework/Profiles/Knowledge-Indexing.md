# Profile — Knowledge Indexing

## Objetivo

Configurar el comportamiento del agente para construir y mantener bases de conocimiento (`ia-db`): índices semánticos que permiten a futuros agentes recuperar contexto sin releer código fuente ni documentación completa.

La ia-db es la memoria operativa del proyecto. Reduce el consumo de tokens y acelera el arranque de contexto en nuevas conversaciones.

---

# Framework

## Parámetros

Utilizar la configuración definida en:

- `/IA.Prompting.Templates/PromptFramework/Parameters`

## Rule Set

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/RuleSets/RuleSet-Documentation.md`

Prestar especial atención a `Rule-Indexing.md` y, para indexados multi-proyecto, a `Rule-Agents.md`.

---

# Génesis de la técnica

La técnica proviene de la ia-db de `Discord.Bot.Moderador.Core` (implementación de referencia: `/Discord.Bot.Moderador.Core.Documentos/ia-db`), de la que conserva: punto de entrada con instrucción para IA, tabla de navegación «Necesitas saber... → Lee este índice», resumen ejecutivo de 1 pantalla e índices temáticos numerados.

Este Profile la mejora en cinco aspectos:

1. **Entrada única** — un solo `README.md`; sin `INDEX.md` duplicado.
2. **Manifiesto de generación** — la ia-db registra cómo regenerarse (alcance, fuentes, prompt generador).
3. **Federación** — soporta indexar varios proyectos en una ia-db de workspace.
4. **Presupuestos de tamaño** — límite orientativo por índice.
5. **Actualización incremental** — versionado y fecha para sincronizar solo lo afectado.

---

# Enfoque

Comprender el proyecto como un sistema antes de indexarlo. Indexar significa **destilar**, no copiar: cada índice condensa lo esencial de un dominio y referencia las fuentes para el detalle. Construir desde la visión general (índice maestro) hacia los dominios particulares.

---

# Estructura canónica

## Modo proyecto (un solo proyecto)

Destino por defecto: `<proyecto>/ia-db`.

```
<proyecto>/ia-db/
├── README.md                  ← Punto de entrada único
└── indexes/
    ├── 00_MASTER-INDEX.md     ← Visión general, stack, decisiones clave
    ├── 01_<tema>.md           ← Índices temáticos numerados
    └── NN_<tema>.md
```

## Modo workspace (federado, varios proyectos)

Destino: la raíz indicada (por defecto la raíz del workspace, `/ia-db`).

```
/ia-db/
├── README.md                  ← Entrada única: tabla de proyectos + navegación
└── indexes/
    ├── 00_WORKSPACE-INDEX.md  ← Visión del workspace: proyectos, relaciones entre ellos
    ├── <proyecto-a>/
    │   ├── 00_MASTER-INDEX.md
    │   └── NN_<tema>.md
    └── <proyecto-b>/
        └── ...
```

Si un proyecto ya posee su propia ia-db, el índice federado la **referencia** en lugar de duplicarla.

## README.md (punto de entrada)

Contiene, en orden:

1. **Instrucción para IA** — blockquote: este archivo es el punto de entrada único y cómo usarlo.
2. **Tabla de navegación** — «Necesitas saber... → Lee este índice» (en modo workspace, agrupada por proyecto).
3. **Resumen ejecutivo de 1 pantalla** — datos clave (proyecto/s, tipo, stack, repo, versión), función principal, arquitectura en una línea.
4. **Estructura** — árbol comentado de primer nivel.
5. **Restricciones para IA** — qué no debe hacer un agente que consuma este índice.
6. **Manifiesto de generación** — ver abajo.

## Manifiesto de generación

Sección final del README.md que captura la génesis y permite regenerar o actualizar la base:

```markdown
## Manifiesto de generación

- Generado por : /IA.Prompting.Templates/Tool-Prompts/Iniciar-Indexado.md
- Alcance      : <proyectos indexados>
- Fuentes      : <raíces escaneadas: src/, docs/, scripts/, ...>
- Generado     : <fecha> · Versión: <n.n>
- Actualizar   : /IA.Prompting.Templates/Tool-Prompts/Actualizar-Indexado.md
```

## Índices temáticos

Cada índice: cubre un único dominio (arquitectura, dominio, infraestructura, pruebas, devops, glosario, decisiones...); abre con blockquote de propósito y fuente primaria; privilegia tablas, árboles y diagramas sobre prosa; referencia las fuentes para el detalle; respeta un presupuesto orientativo de 300–500 líneas; no duplica contenido de otro índice. Los temas se adaptan al proyecto; la numeración `NN_` mantiene orden estable.

---

# Fuentes y exclusiones

El inventario de fuentes considera únicamente contenido con valor de conocimiento: código fuente, documentación, configuración, scripts y manifiestos de build.

Excluir siempre del escaneo y del índice:

| Categoría | Carpetas / archivos |
|-----------|--------------------|
| Control de versiones | `.git`, `.svn`, `.hg` |
| IDE y herramientas | `.vs`, `.vscode`, `.idea` |
| Dependencias | `node_modules`, `packages`, `vendor`, `.venv`, `__pycache__` |
| Artefactos de build | `bin`, `obj`, `dist`, `build`, `target`, `out`, `publish` |
| Binarios y pesados | Ejecutables, librerías compiladas, comprimidos, imágenes, videos, bases de datos |
| La propia base | `ia-db` (no autoindexarse) |

Respetar además los patrones de `.gitignore` del proyecto cuando exista. Los proyectos pueden ampliar esta lista en `Parameters/Paths.md`.

---

# Ejecución

- Identificar dominios de conocimiento y construir el inventario de fuentes por proyecto, aplicando las exclusiones definidas arriba.
- En modo workspace, indexar los proyectos en paralelo mediante subagentes (uno por proyecto, según `Rule-Agents.md`) y consolidar la entrada federada al final.
- Toda entrada del índice debe ser trazable a una fuente; lo no verificable se marca, no se completa por inferencia.

## Actualización incremental

- Leer el manifiesto para conocer alcance y fecha vigentes.
- Detectar cambios desde esa fecha (historial git, fechas de modificación, changelog) y actualizar solo los índices afectados.
- Eliminar referencias obsoletas; actualizar fecha y versión del manifiesto.
- No reconstruir la base cuando alcanza una actualización parcial.

---

# Resultado esperado

Una ia-db que permita a un agente: cargar contexto de un tema leyendo la entrada más 1–2 índices; localizar la fuente de cualquier afirmación; conocer la vigencia del índice; y regenerar o actualizar la base a partir de su manifiesto — todo sin releer las fuentes completas.
