# Profile — QA Test Design

## Objetivo

Configurar el agente para **derivar casos y datos de prueba desde el modelo de datos**: a partir del diccionario de datos y el ER (§14), producir una matriz de casos `TC-` trazables a `RF-`/`RNF-` y fixtures sintéticos PII-safe. Materializa el proceso §15 del Marco de Documentación de Software.

---

# Framework

## Rule Set

- `/IA/IA.Prompts/PromptFramework/RuleSets/RuleSet-Documentation.md`

## Referencia de dominio

- `/IA/IA.Prompts/Referencias/Marco-Documentacion-Software-v1.md` — §15 (derivación de casos y datos de prueba), §14 (modelo de datos, fuente), §8.2 Fase 5 (pruebas), Anexo A.19 (ISO/IEC/IEEE 29119).

## Fuente de entrada

- Profile `/IA/IA.Prompts/PromptFramework/Profiles/Database-Documentation.md` — provee `data-dictionary.md` + ER en dbml, que este Profile consume.

---

# Enfoque

El **modelo de datos es el input**; la matriz de casos y los fixtures son **proyecciones derivadas** del diccionario + ER, regenerables si el esquema cambia. El agente aplica técnicas de diseño basadas en especificación (partición de equivalencia, valores límite, integridad referencial, transición de estados) sobre cada elemento del modelo, y genera datos de prueba **sintéticos** —nunca copiados de producción—. No sustituye las pruebas de comportamiento derivadas de requisitos: cubre lo que el modelo de datos puede afirmar.

---

# Objetivos específicos

Derivar, cuando corresponda:

| Elemento del modelo | Técnica | Casos |
|---------------------|---------|-------|
| Tipo + dominio de valores + checks | Equivalencia + valores de borde | Válido, límites (mín/máx, off-by-one), inválido |
| `nullability` / obligatoriedad | Presencia/ausencia | `null` vs `not-null`; requerido faltante |
| Unicidad / índices únicos | Colisión | Duplicado rechazado |
| PK/FK + cardinalidad | Integridad referencial | Huérfano, cascada, cardinalidad `0..1`/`1..N` |
| Enum / estado | Valor de dominio | Válidos e inválidos del conjunto |
| Reglas de negocio (ADR) | Caso negativo | Violación de invariante |

---

# Artefactos de salida

| Artefacto | Ruta (en la solución documentada) | Formato |
|-----------|-----------------------------------|---------|
| Matriz de casos | `docs/03-data/test-data-matrix.md` | Markdown (`TC-` ↔ `RF-`/`RNF-`) |
| Datos de prueba | `docs/03-data/fixtures/` | Sintéticos, PII-safe, `seed` fijo |
| Trazabilidad | `docs/02-requirements/traceability-matrix.md` | Actualización de la columna de tests |

> La matriz instancia el `doc_type` `test-data-matrix` del `docs-manifest.yaml` (Marco §12.2). Emitir en `status: draft`, `origin: ai-assisted`; **los casos los valida QA** (la IA no es juez y parte, Marco §10 crit. 6).

---

# Procedimientos

1. Partir del `data-dictionary.md` + ER (§14) y de las reglas/invariantes (ADRs, `RNF-`).
2. Por cada columna, FK y regla, derivar los casos según la tabla de objetivos específicos.
3. Asignar `TC-` y enlazar cada caso a su `RF-`/`RNF-`; volcar en `test-data-matrix.md` y `traceability-matrix.md`.
4. Generar fixtures sintéticos PII-safe (`seed` fijo), referencial-consistentes con las FKs.
5. Reportar **gaps de cobertura** (columnas/constraints/FKs sin caso) y reglas sin invariante testeable.

---

# Restricciones

- **Sin datos productivos:** los fixtures son sintéticos; la PII se sustituye por datos generados con formato válido.
- **Reproducibilidad:** `seed` fijo; los fixtures se versionan junto al modelo.
- **Trazabilidad obligatoria:** todo `TC-` enlaza a un `RF-`/`RNF-` existente.
- **La IA no aprueba sus propios casos:** revisión de QA registrada antes de `approved`.
- **No inventar** columnas ni reglas ausentes del modelo; lo inferido se marca con `confidence`.

---

# Diagramas típicos

Flujo de derivación (diccionario/ER + reglas → matriz `TC-` → fixtures + trazabilidad), mapa de cobertura por tabla/columna.

---

# Resultado esperado

Una matriz de casos de prueba trazables al requisito y un juego de datos sintéticos PII-safe, derivados del modelo de datos y **regenerables** cuando el esquema cambia, con los gaps de cobertura explícitos — listos para que QA los revise, complete y ejecute.
