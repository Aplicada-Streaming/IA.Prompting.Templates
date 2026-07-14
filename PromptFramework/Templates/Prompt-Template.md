<!--
  Plantilla de prompt — núcleo de 5 secciones.
  Copiá desde "# Contexto" hasta el final, reemplazá el contenido de cada sección
  y borrá estos comentarios guía. Detalle de cada sección: ../Guides/How-To.md
-->

# Contexto

<!-- ¿Qué necesita saber el agente del estado actual para no asumir nada?
     Describí el sujeto (proyecto/servidor/repo) y su estado en presente. Sin verbos de acción. -->

...

---

# Objetivo

<!-- ¿Qué debería ser verdad cuando el agente termine?
     Una o dos frases, arrancando con un verbo en infinitivo (Documentar, Analizar, Generar). Específico y acotado. -->

...

---

# Solicitudes

<!-- ¿Qué acciones atómicas y verificables cumplen el objetivo?
     Una tarea por viñeta. Los ENTREGABLES van acá, con su ruta exacta cuando deban guardarse. -->

- ...
- ...
- Generar el informe en `<ruta/del/entregable.md>`.

---

# Restricciones

<!-- ¿Qué NO debe hacer el agente? Es el límite de seguridad.
     Definí siempre: si puede modificar archivos, si puede commitear/pushear, y qué queda fuera de alcance. -->

- No inventar información; toda afirmación debe estar respaldada por evidencia verificable.
- ...

---

# Framework

## Profile

<!-- ¿De qué tipo es la tarea? → elegí el Profile que la represente.
     Si ningún Profile encaja, referenciá un RuleSet (RuleSet-Lean para tareas simples).
     Catálogo: ../Profiles/README.md · ../RuleSets/Readme.md -->

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/[Profile].md`

<!--
  Nota opcional: agregá abajo, solo si hace falta, aclaraciones puntuales de ESTA corrida
  que el agente no pueda deducir del resto (permisos, prioridades, un dato disponible ahora).
  Lo reutilizable va en el Profile, no acá.
-->
