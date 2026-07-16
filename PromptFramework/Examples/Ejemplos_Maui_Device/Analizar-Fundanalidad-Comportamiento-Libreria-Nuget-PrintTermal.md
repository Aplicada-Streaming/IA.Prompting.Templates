# Tool-Prompt — Analizar capacidades de librería 

> **Invocación**:
> - `Lee y ejecuta /IA.Prompting.Templates/PromptFramework/Examples/Analizar-Fundanalidad-Libreria-Nuget-PrintTermal.md`

---

# Contexto

Lee `/Librerias/PrintThermal_Motor_Maui.Documentacion/ia-db/README.md`  en cuanto a las capacidades de los comandos escPost y las posibilidades que ofrecen las impresoras en post de valuar manejo de fallos

Lee `/Ejemplos_Maui/Ejemplos_Maui_Devices.Documentos/ia-db/README.md` en lo relacionado con los proyectos `Ejemplo_Maui_Hibrida`
y `Ejemplo_MotorDSL_Dialog`.

Estos dos poryectos usan las librerias nuget `MotorDsl.*` 

En el proyecto `Ejemplo_Maui_Hibrida` es un PoC (Proof of Concept) sobre una aplicación que mediante ciertos parametros, con el parametro `action=print` genero una impresión, ocurren ciertos comportamientos:

# Objetivo

Se hace necesario relevar y documentar en mardkown sobre el flujo de usuario antes diferentes casos de pruebas que prevea y aquellos que no preveea. Y de esos que no preveea saber que se propone para abordar las situaciones no previstas que se planteen.


# Solicitudes


1.a Analizar el proyecto `Ejemplo_Maui_Hibrida` e incluir en el documento las secciones referidas a: 
1.a explicar la estructura de dialogos overlay, servicios, pages, viewmodels. Ilustrado con ejemplos diagramas de clases, diagramas de secuencias. Como se extiende con ejemplos muy esquematizados, snippet de código. descripciones y explicaciones.

1.b En base a lo anterior, analizar la experiencia y flujo de usuario de la impresión de tickets. Incluir lo necesario para el desarrollador (diagrama de clases, diagrama de secuencia, historias), pero tambien para entender desde el puntoo de vista del usuario y del QA. Evaluar en este caso de uso las posibles eventualidades tanto en lo funcional de lo que provee la libreria `MotorDsl.*` como tambien en lo que se prevee en la aplicación PoC del proyecto `Ejemplo_Maui_Hibrida`
1.b.1. Multiples impresoras detectadas diferentes. 
1.b.2. Multiples impresoras iguales, misma marca y modelo
1.b.3. Fallo durante la impresión. Si se detecta falta de papel o algun bloqueo que se desconozca, ¿Se puede saber el fallo? se muestra el fallo, se puede reproducir, ¿como se puede reproducir?
1.b.4. Para el caso particular de querer imprimir un ticket para este tipo de aplicación hibrida en que se disparan los dispositivo a traves de queryparam especializados conviene que la impresora se configure la primera vez, y luego mantenga eso como configuración o bien darle la posibilidad de reconfigurar la impresora con otro comando adicional. Que conviene plantear en este sentido. 
Ahora si la impresora falla, lista la impresoras conectadas y da opciones para reconfigurar la impresora. Ejmplo de wireframe de fallo y propuesta de la app de elegir otra impresora

```
No se pudo conectar
No fue posible conectar a 58HB6.
[Reintentar]
[Elegir otra]
[Cerrar]
```

Al hacer click en el botón [Elegir otra] deriva en otra pantalla que dice

```
Elegí una impresora 

Se detectaron varias
impresoras disponibles.
[MTP-II]
[58HB6]
[Cerrar]
```
Se puede pensar que estos dialogos de manejo de situaciones durante el proceso de impresión, pero es importante saber si puedo mostrar fallos relativos a que la impresora no esté activa (puede que este registrada) o conectada, pero si configurada , si se quedo sin papel y hay que reiniar la impresión o ocurrio otro fallo y se desea volver a intenar imprimir.

Se debe evaluar posibles flujos de usuarios, dar los difentes situaciones, propuestas. acompañar con gaficos wireframes de los dialogos con el usuario e incluir en la seccion que corresponda 

Como experiencia de usuario indicar error, un detalle breve y una ligera explicación. 

---

# Framework

## Profile

Aplicar:

- `/IA.Prompting.Templates/PromptFramework/Profiles/Code-Review.md`




