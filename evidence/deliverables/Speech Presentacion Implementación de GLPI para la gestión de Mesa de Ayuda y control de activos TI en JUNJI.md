# Speech defensa oral — 18 diapositivas

**Duración estimada:** 32 a 35 minutos

---

## Diapositiva 1. Portada

**Tiempo estimado:** 1 minuto 30 segundos

“Buenos días. Mi nombre es Jonathan Garcés, y junto a Andrés Vargas presentamos el proyecto titulado **Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI**.

Este proyecto se desarrolló para la Junta Nacional de Jardines Infantiles, JUNJI, una organización pública de alcance nacional, y tuvo como objetivo proponer una solución tecnológica que respondiera a dos necesidades críticas: mejorar la gestión de soporte TI y fortalecer el control de activos institucionales.

La solución se basó principalmente en GLPI, apoyado por tecnologías como PHP, Apache, MariaDB, Git y GitHub. Durante esta presentación mostraremos el problema identificado, la solución propuesta, la arquitectura, la validación funcional, los resultados alcanzados y las oportunidades de mejora futura.”

---

## Diapositiva 2. Agenda de la presentación

**Tiempo estimado:** 1 minuto

“Para ordenar la exposición, dividimos la presentación en nueve bloques. Primero veremos el contexto organizacional y el problema. Luego revisaremos objetivos y alcance. Después abordaremos la metodología de trabajo, la arquitectura y el diseño técnico. A continuación, mostraremos la implementación y la demo funcional. Luego presentaremos la calidad del proyecto, los riesgos y aprendizajes, y finalmente cerraremos con conclusiones, impacto y mejoras futuras.

La idea es que la presentación vaya desde el problema del cliente hasta la demostración concreta de cómo la propuesta responde a esa necesidad.”

---

## Diapositiva 3. Organización y contexto

**Tiempo estimado:** 2 minutos

“JUNJI es un organismo público chileno dependiente del Ministerio de Educación, creado en 1970, con presencia nacional y una estructura organizacional amplia y compleja. Su operación involucra miles de establecimientos educacionales y una gran cantidad de funcionarias y funcionarios distribuidos entre oficinas centrales, direcciones regionales y unidades educativas.

Esto significa que cualquier sistema de apoyo debe responder a un entorno con alto volumen de requerimientos, necesidad de trazabilidad, control administrativo y resguardo de recursos públicos.

Desde la perspectiva del proyecto, esto era importante porque no estábamos proponiendo una solución para una organización pequeña o aislada, sino para una institución con procesos distribuidos, exigencias normativas y fuerte necesidad de estandarización.” 

---

## Diapositiva 4. Usuarios y proceso actual

**Tiempo estimado:** 2 minutos

“En este contexto, identificamos distintos perfiles de usuario. Por una parte, los usuarios internos que generan tickets, como funcionarios administrativos, personal de jardines infantiles y equipos de apoyo. Por otra, el equipo de soporte TI que recibe y gestiona esos requerimientos. Finalmente, jefaturas y encargados de gestión, que necesitan reportería y visibilidad para tomar decisiones.

El proceso actual funcionaba principalmente a través del correo electrónico. El usuario detectaba una necesidad, enviaba un correo, el sistema lo convertía en ticket, y luego el seguimiento seguía dependiendo en gran medida de ese mismo flujo.

El problema no era solo que existiera una mesa de ayuda, sino que esta operaba más como un repositorio de correos que como una plataforma real de gestión. Eso limitaba la clasificación, la reportería, la trazabilidad y el análisis posterior.”

---

## Diapositiva 5. Problema identificado e impacto

**Tiempo estimado:** 2 minutos 30 segundos

“Las brechas detectadas fueron cuatro principalmente.

Primero, una reportería muy limitada. No existía suficiente visibilidad sobre tickets por área, abiertos versus cerrados, tiempos de respuesta o carga de trabajo por unidad o región.

Segundo, una capacidad de extracción de datos insuficiente. La información no estaba normalizada y requería revisiones manuales en correos y planillas.

Tercero, una dependencia excesiva del correo electrónico, lo que aumentaba el riesgo de pérdida de información, respuestas fuera del sistema y baja auditabilidad.

Y cuarto, una baja estandarización del ticket. Los usuarios enviaban solicitudes con distinto nivel de detalle, dificultando clasificación, priorización y análisis.

El impacto operacional de esto era claro: baja visibilidad de la gestión, mayor carga administrativa, dificultad para identificar cuellos de botella y decisiones basadas más en percepción que en datos.” 

---

## Diapositiva 6. Objetivo general y objetivos específicos

**Tiempo estimado:** 2 minutos

“El objetivo general del proyecto fue implementar GLPI como plataforma institucional para la gestión de Mesa de Ayuda y control de activos TI en JUNJI, reduciendo la dependencia del correo electrónico, fortaleciendo la trazabilidad del soporte y mejorando el control del inventario tecnológico.

De este objetivo general se desprendieron cinco objetivos específicos.

Primero, configurar una plataforma GLPI operativa.
Segundo, diseñar formularios estructurados para mejorar calidad y clasificación del dato.
Tercero, habilitar la gestión centralizada de activos TI.
Cuarto, incorporar dashboards y reportes operativos para jefaturas.
Y quinto, validar funcionalmente la solución mediante pruebas de aceptación.

Estos objetivos fueron importantes porque conectaron directamente la propuesta técnica con los subproblemas concretos detectados en JUNJI.”

---

## Diapositiva 7. Alcance, MVP y funcionalidades clave

**Tiempo estimado:** 2 minutos

“En cuanto al alcance, el proyecto se definió como un MVP, es decir, una primera entrega funcional enfocada en resolver lo más crítico sin sobredimensionar la implementación.

Dentro del alcance se consideró la instalación base de GLPI en una máquina virtual, la parametrización de perfiles, entidades, ubicaciones, formularios, categorías, estados, gestión de tickets, activos TI, dashboards operativos y reportería base.

Fuera del alcance quedaron funcionalidades que, si bien son deseables, aumentaban complejidad: reportería ejecutiva avanzada, integración profunda con otros sistemas institucionales, automatización total del inventario y reglas avanzadas de escalamiento.

Esto permitió mantener una propuesta realista, con foco en valor temprano y adopción inicial.”

---

## Diapositiva 8. Metodología y gestión del proyecto

**Tiempo estimado:** 2 minutos

“Metodológicamente, se trabajó con un enfoque ágil basado en Scrum, ajustado a la naturaleza del proyecto. Se utilizó una dinámica semanal, con planificación, seguimiento, revisión y retrospectiva adaptadas a un proyecto de implementación más que de desarrollo puro.

El backlog se construyó priorizando valor para el cliente, criticidad operativa y viabilidad del MVP. La planificación formal del informe se representó entre S2 y S10, mientras que GitHub se utilizó como herramienta de gestión y trazabilidad del trabajo.

Este enfoque fue útil porque permitió ordenar levantamiento, configuración, validación y cierre documental de manera incremental, sin perder el control del alcance.” 

---

## Diapositiva 9. Arquitectura de la solución

**Tiempo estimado:** 2 minutos 30 segundos

“En arquitectura, la decisión central fue utilizar un **modelo web monolítico en capas**, desplegado sobre una **máquina virtual institucional**, con GLPI como plataforma central.

En términos prácticos, esto significa una aplicación web única que integra interfaz, lógica de negocio y persistencia de datos, soportada por PHP, Apache y MariaDB.

Elegimos esta arquitectura por cuatro razones:
primero, porque reduce complejidad técnica y acelera la puesta en marcha;
segundo, porque centraliza helpdesk e inventario en una sola plataforma;
tercero, porque simplifica la administración para el equipo TI de JUNJI;
y cuarto, porque facilita mantenimiento, respaldo y control operacional.

También evaluamos alternativas como microservicios o desarrollo a medida, pero se descartaron porque habrían aumentado costo, complejidad y tiempo sin aportar valor proporcional al problema real.”

---

## Diapositiva 10. C4 simplificado y componentes

**Tiempo estimado:** 2 minutos

“Si lo miramos en términos de componentes, el sistema se organiza en un servidor web con GLPI, una base de datos MariaDB, almacenamiento local y, como componente complementario, GLPI Inventory o GLPI Agent para automatización futura del inventario.

En el nivel de contexto, los actores principales son solicitantes, agentes de soporte, jefaturas y administrador. El sistema interactúa además con correo institucional, activos TI y la infraestructura de virtualización.

Y si bajamos a un nivel más específico, el módulo más crítico es gestión de tickets, porque concentra formularios, validación, clasificación, asignación, bitácora, notificaciones y reportería. En otras palabras, ahí es donde se transforma una solicitud dispersa en un flujo controlado y trazable.”

---

## Diapositiva 11. Modelo de datos y decisiones técnicas

**Tiempo estimado:** 2 minutos

“En diseño de datos, se modelaron como entidades principales: usuarios, grupos, ubicaciones, categorías, tickets, tareas de ticket, validaciones, activos TI y la relación ticket-activo.

Desde el punto de vista físico, GLPI separa distintos tipos de activos en tablas propias, pero el proyecto se concentró en el subconjunto relevante para el MVP: tickets, usuarios, categorías, tareas, estados, activos y asociaciones.

Además, justificamos normalización hasta tercera forma normal en el subconjunto analizado, para reducir duplicidad y fortalecer consistencia.

En cuanto a decisiones técnicas, las más relevantes fueron: usar GLPI en vez de software comercial o desarrollo propio; desplegar sobre máquina virtual en vez de contenedores como base del MVP; estructurar tickets con formularios obligatorios; e integrar tickets y activos en una misma plataforma.”

---

## Diapositiva 12. Implementación: vista general

**Tiempo estimado:** 1 minuto 30 segundos

“En implementación, la propuesta se apoyó en una estructura organizada por configuración, infraestructura, documentación, evidencias y pruebas. El foco no estuvo en desarrollar código desde cero, sino en configurar correctamente una plataforma existente para responder a necesidades específicas.

En esta etapa se definieron perfiles, entidades, catálogos, formularios, estados, reportería base, activos y reglas de operación. Además, se documentó la instalación completa en el Anexo A, lo que deja una ruta de implementación concreta y replicable.”

---

## Diapositiva 13. Demo funcional: login, dashboard y flujo crítico

**Tiempo estimado:** 3 minutos

“En la demo funcional, los flujos críticos que se deben mostrar son los siguientes.

Primero, el ingreso al sistema con usuario autenticado y la diferenciación por perfil.

Segundo, la creación de un ticket mediante formulario estructurado, mostrando que el sistema exige campos obligatorios y mejora la calidad del dato desde el origen.

Tercero, la gestión de ese ticket por parte del agente: revisión, cambio de estado, asignación, comentario y cierre.

Cuarto, la asociación del ticket con un activo TI, para demostrar trazabilidad entre soporte e inventario.

Y quinto, la vista de dashboards y reportería base desde una jefatura.

La idea en la defensa es que esta demo no sea solo una navegación superficial, sino la evidencia concreta de que el flujo completo del usuario funciona sin errores bloqueantes.”

---

## Diapositiva 14. Validaciones y resultados funcionales

**Tiempo estimado:** 2 minutos

“Para validar la solución se definieron 18 casos de prueba entre funcionales, de integración, operacionales, de seguridad y de aceptación. Todos quedaron en estado completado en ambiente controlado.

Entre los casos validados estuvieron: creación de ticket, validación de campos obligatorios, cambio de estado, asignación, asociación ticket-activo, registro de activos, consulta de inventario, dashboards, exportación de reportes, restricciones por perfil y pruebas de aceptación con usuario final.

En términos globales, los resultados mostraron que el núcleo funcional del MVP operó sin errores críticos, quedando solo observaciones menores asociadas a redacción, nomenclatura o presentación.” 

---

## Diapositiva 15. Calidad del proyecto

**Tiempo estimado:** 2 minutos

“En calidad del proyecto, el foco se puso en tres dimensiones.

Primero, la calidad funcional, respaldada por la estrategia de pruebas, la cobertura de escenarios críticos y la sesión de aceptación.

Segundo, la calidad técnica, reflejada en la coherencia entre arquitectura, estructura documental, control de versiones y buenas prácticas sobre los artefactos propios del proyecto.

Y tercero, la trazabilidad del trabajo, apoyada en Git y GitHub para versionamiento, evolución del backlog, documentación y respaldo de evidencias.

Aquí es importante transparentar un punto: al tratarse de una implementación sobre GLPI y no de desarrollo completo de software a medida, la validación se centró más en cobertura funcional que en pruebas unitarias tradicionales sobre lógica propia.” 

---

## Diapositiva 16. Riesgos y mitigaciones

**Tiempo estimado:** 2 minutos

“Durante el proyecto se identificaron riesgos principales asociados a infraestructura, calidad de datos, crecimiento no controlado del alcance, adopción de usuarios y reportería más compleja de lo previsto.

El riesgo más crítico fue el crecimiento no controlado del alcance, porque GLPI ofrece muchas capacidades y era fácil intentar incorporar demasiado en la primera entrega.

Para mitigarlo, se trabajó con un MVP claramente delimitado, backlog priorizado y exclusiones justificadas.

Otros riesgos se abordaron mediante arquitectura simple sobre VM, formularios estructurados, dashboards base, pruebas de aceptación y enfoque en usabilidad. Esto permitió que el proyecto no solo propusiera una solución tecnológica, sino también una estrategia razonable para hacerla viable.” 

---

## Diapositiva 17. Aprendizajes y deuda técnica

**Tiempo estimado:** 3 minutos

“En cuanto a aprendizajes, uno de los más importantes fue entender que una solución tecnológica no se evalúa solo por lo que hace, sino también por su viabilidad operativa, su alineamiento con el contexto y su sostenibilidad.

Otro aprendizaje clave fue diferenciar entre implementar una plataforma existente y desarrollar desde cero. En este proyecto, el valor no estuvo en programar un sistema nuevo, sino en configurar correctamente una solución madura y justificar por qué era la opción más adecuada.

Respecto de la deuda técnica, identificamos cinco líneas de mejora futura:
primero, reportería ejecutiva avanzada;
segundo, mayor automatización de reglas de asignación y escalamiento;
tercero, inventario automatizado más profundo mediante agentes;
cuarto, integración con LDAP o Active Directory;
y quinto, maduración del gobierno del dato.

La deuda técnica no compromete la viabilidad del MVP, pero sí marca con claridad la ruta de evolución futura del sistema.” 

---

## Diapositiva 18. Conclusiones e impacto

**Tiempo estimado:** 3 minutos

“Para cerrar, este proyecto permitió formular una propuesta sólida para responder a una necesidad real de JUNJI.

En términos de resultados, se logró cubrir el núcleo funcional esperado del MVP: mesa de ayuda estructurada, trazabilidad del soporte, reportería base, control de activos y validación funcional.

En términos de impacto, la solución permitiría reemplazar una lógica muy dependiente del correo por una plataforma centralizada, trazable y más útil para la toma de decisiones. Además, aportaría mayor control sobre activos TI, reduciendo riesgos de descontrol de inventario, pérdida o falta de visibilidad.

Finalmente, creemos que el principal valor del proyecto está en que no solo propone una herramienta, sino una base tecnológica más ordenada, sostenible y escalable para la gestión de soporte TI en JUNJI.

Muchas gracias. Quedamos atentos a sus preguntas y, a continuación, pasamos a la demo funcional.”

---

# Cierre tipo elevator pitch para apertura o cierre

Puedes usar esto al inicio o al final, como remate:

“En simple, este proyecto busca transformar una mesa de ayuda basada principalmente en correos dispersos en una plataforma institucional capaz de ordenar tickets, relacionarlos con activos TI, entregar trazabilidad y dar visibilidad real a la gestión. Nuestra propuesta no busca solo reemplazar una herramienta, sino instalar una base tecnológica más robusta para controlar mejor el soporte y los recursos informáticos de JUNJI.”

---

# Recomendación de tiempo por bloque

Para llegar a **30 a 35 minutos**, puedes manejarlo así:

* Diapositivas 1 a 5: **9 minutos**
* Diapositivas 6 a 8: **6 minutos**
* Diapositivas 9 a 11: **6,5 minutos**
* Diapositivas 12 a 14: **6,5 minutos**
* Diapositivas 15 a 18: **7 minutos**

Total aproximado: **35 minutos**

---

# Cómo presentar la demo sin que falle

Cuando pases a demo, sigue este orden:

1. Login con perfil solicitante
2. Crear ticket
3. Validación por campos obligatorios
4. Vista del ticket creado
5. Cambiar a perfil agente
6. Asignar ticket y cambiar estado
7. Asociar activo TI
8. Mostrar dashboard
9. Mostrar inventario o ficha de activo
10. Cerrar con reportería base