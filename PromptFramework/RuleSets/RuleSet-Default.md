# RuleSet — Default

## Objetivo

Conjunto base aplicado a la mayoría de las tareas. Los RuleSets especializados lo extienden agregando las reglas de su dominio; `RuleSet-Lean` es el único que carga menos.

Un RuleSet es solo una **lista de Rules**: el comportamiento y el énfasis los define el Profile que lo aplica.

---

## Reglas

- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-All.md`
- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-Workflow.md`
- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-Evidences.md`
- `/IA.Prompting.Templates/PromptFramework/Rules/Rule-Markdown.md`

---

## Extensión

| RuleSet | Agrega sobre Default |
|---------|----------------------|
| `RuleSet-Documentation.md` | `Rule-Documentation`, `Rule-Indexing`, `Rule-Agents` |
| `RuleSet-Development.md` | `Rule-Agents` |
| `RuleSet-Audit.md` | `Rule-Indexing`, `Rule-Agents` |

`RuleSet-Lean.md` carga solo `Rule-All` + `Rule-Workflow` (subconjunto de Default) para tareas simples.
