
> **Uso**: copiá este prompt, reemplazá los datos y rutas por los de tu entorno y ejecutá.

---

# Contexto

La documentación generada deberá permitir comprender como responde el servidor ante los ciclos de apagado con respecto a los contenedores y encontrar una mecanismo para administrar los sistemas de energía ininterrumpida del host.

---

# Objetivo

- Conocer como docker responde ante ciclos de apagado/encendido del server
- Analizar y encontrar mecanismos de respuesta ante fallos de suministro de energía. 

---

# Solicitudes

- ¿Qué sucede al iniciar un comando power off en el host con los contenedores?. Reciben los contenedores un power off?, y Cuando inicia el server host , autoinician los contenedores?. Genera un informe en `Repos-Hosts/Host.Infra/Temas-Estudio/Contenedores-Ciclos-Apagado-Host.md`

- ¿Que propuesta relativo a impelementar un servicio de energía ininterrumpida?. Actualmente el servidor host tiene un UPS conectado con una autonomia de 20 minutos al puerto USB. Es tentativo desarrollar una aplicación net core web con un panel web que corra medianteun contenedor docker con el USB configurado del dispositivo UPS actual. En este sistema se podría manejar una tarea que este controlando la salud de la bateria, y los eventos de de corte de energía, y ahi planificar un apagado programado ante eventos de corte de energía, y o alertas por fallos del UPS. La aplicación podría ser un servicio web o un servicio bacground con un panel de control simple y una base de datos sqlite para mantener la configuracion. Esta conectado el UPS ahora, podes revisarlo y relevar datos. Pedi los permisos de root que necesites. Documenta tu propuesta en `/Repos-Hosts/Host.Infra/Backlog/Analisis-Servicio-Sistema-Manejo-SAI.md`. La justificación en principo sería el poder agregar caracteristicas en el futuro, como acceso a apis desde aplicación movil. 

---

# Framework

## Rule Set

- `/IA.Prompting.Templates/PromptFramework/RuleSets/RuleSet-Default.md`




