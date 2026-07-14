# Referencias

Documentación de referencia **externa al framework de prompts**. No define comportamiento del agente (eso vive en `/IA.Prompting.Templates/PromptFramework`): son marcos, normas y guías de dominio que los prompts consultan como **fuente de características** para poblar sus secciones (Contexto, Restricciones, Solicitudes) o para fijar criterios de salida.

Se mantienen acá, fuera de `PromptFramework`, precisamente porque su ciclo de vida y su autoría son independientes del framework.

---

## Cómo se usan

Un prompt (o Tool-Prompt) referencia estos documentos por ruta absoluta desde la raíz del workspace y extrae de ellos las características que necesita —estructura documental, metadatos, criterios de calidad, checklists— en vez de reinventarlas.

```
... siguiendo el marco de /IA.Prompting.Templates/Referencias/Marco-Documentacion-Software-v1.md
```

---

## Referencias disponibles

| Referencia | Qué aporta | Usar cuando |
|------------|------------|-------------|
| [Marco-Documentacion-Software-v1.md](Marco-Documentacion-Software-v1.md) | Marco de documentación de soluciones de software multi-proyecto: criterios de calidad documental, estructura de repositorio, metadatos/IDs máquina-legibles, perfiles por tipo de pieza, procesos greenfield/legacy y checklist operativo. | Un prompt debe generar, actualizar o auditar documentación de software y necesita estructura, metadatos y criterios de calidad consistentes. |
