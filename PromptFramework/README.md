# Prompt Framework

Framework reutilizable para ingeniería de prompts.

Proporciona una metodología consistente para construir prompts complejos mediante la composición de componentes independientes, reutilizables y mantenibles.

---

## Documentación

| Documento | Descripción |
|-----------|-------------|
| [Guía conceptual](Guides/Readme.md) | Arquitectura, filosofía y componentes del framework |
| [Guía de usuario](Guides/User-Guide.md) | Cómo utilizar el framework para construir prompts |
| [Guía de desarrollo](Guides/Develop-Guide.md) | Cómo extender y mantener el framework |
| [Guía de optimización de tokens](Guides/Token-Optimization.md) | Cómo minimizar el consumo de contexto (técnica ia-db) |

---

## Estructura

```
IA.Prompting.Templates/
├── PromptFramework/
│   ├── Rules/          # Reglas atómicas de comportamiento
│   ├── RuleSets/       # Conjuntos de reglas por dominio
│   ├── Profiles/       # Perfiles de comportamiento del agente
│   ├── Templates/      # Plantillas para construir prompts
│   ├── Prompts/        # Prompts predefinidos reutilizables
│   ├── Examples/       # Ejemplos concretos de uso
│   └── Guides/         # Documentación del framework
└── Tool-Prompts/       # Prompts-herramienta de invocación directa (ia-db)
```

Las referencias entre componentes usan rutas absolutas desde la raíz del workspace, con base `/IA.Prompting.Templates`.

---

## Jerarquía de composición

```
Prompt → Profile → RuleSet → Rules
```

| Capa | Responde a |
|------|------------|
| Prompt | ¿Qué necesita el usuario? |
| Profile | ¿Cómo se comporta el agente? |
| RuleSet | ¿Qué reglas aplican? |
| Rules | ¿Cuál es el comportamiento esperado? |
