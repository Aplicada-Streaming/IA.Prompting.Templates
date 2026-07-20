# Prompt Framework

Framework reutilizable para ingeniería de prompts.

Proporciona una metodología consistente para construir prompts complejos mediante la composición de componentes independientes, reutilizables y mantenibles.

---

## Documentación

| Documento | Descripción |
|-----------|-------------|
| [Guía conceptual](Guides/Readme.md) | Arquitectura, filosofía y componentes del framework |
| [How-To](Guides/How-To.md) | Escribir prompts y extender el framework (esquemas copy-paste) |
| [Guía de usuario](Guides/User-Guide.md) | Cómo utilizar el framework para construir prompts |
| [Guía de desarrollo](Guides/Develop-Guide.md) | Cómo extender y mantener el framework |
| [Guía de optimización de tokens](Guides/Token-Optimization.md) | Cómo minimizar el consumo de contexto (técnica ia-db) |

---

## Estructura

```
IA.Prompts/
├── PromptFramework/
│   ├── Rules/          # Reglas atómicas de comportamiento (7)
│   ├── RuleSets/       # Conjuntos de reglas por dominio (Lean + Default + 3)
│   ├── Profiles/       # Perfiles de comportamiento del agente
│   ├── Templates/      # Plantillas para construir prompts
│   ├── Examples/       # Prompts funcionales completos de ejemplo
│   └── Guides/         # Documentación del framework
└── Tool-Prompts/       # Prompts-herramienta de invocación directa (una línea)
    ├── Indexado-Documentado/  # ia-db, arranque de contexto y documentación de fuentes
    ├── Software/             # Código fuente: QA y derivación de pruebas
    ├── BasesDatos/           # Estructura de bases de datos
    ├── Docker/               # Infraestructura de contenedores
    ├── Infra/                # Servidores y redes
    └── Seguridad/            # Auditoría de seguridad de sistemas web expuestos
```

Las referencias entre componentes usan rutas absolutas desde la raíz del workspace, con base `/IA/IA.Prompts`.

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
