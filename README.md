# Proyecto de Título: Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI

## 1. Descripción general

Este repositorio contiene los artefactos técnicos, documentales y de evidencia asociados al proyecto **“Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI”**.

La propuesta se orienta a resolver dos necesidades principales del cliente:

* fortalecer la gestión de Mesa de Ayuda, actualmente muy dependiente del correo electrónico y con limitadas capacidades de reportería, trazabilidad, estandarización y control;
* incorporar gestión y control de activos TI, con foco en su trazabilidad, estado operativo, asignación y relación con tickets de soporte.

La solución se basa en **GLPI**, desplegado sobre una **máquina virtual institucional**, utilizando una arquitectura web monolítica en capas sobre **Apache**, **PHP** y **MariaDB**. El proyecto considera además inventario automatizado mediante **GLPI Inventory / GLPI Agent** como línea de apoyo para etapas futuras de maduración del control de activos.

---

## 2. Objetivo del repositorio

Este repositorio tiene por objetivo centralizar:

* la configuración técnica del entorno;
* los artefactos de despliegue y servidor web;
* los respaldos y estructuras de base de datos;
* la documentación técnica y funcional del proyecto;
* los casos de prueba y evidencias visuales del MVP;
* los manuales de instalación, operación y uso;
* los entregables formales asociados al informe final;
* el respaldo de la gestión del proyecto mediante GitHub, backlog, evidencias y control de cambios.

---

## 3. Contexto y problema que aborda la propuesta

La Junta Nacional de Jardines Infantiles (JUNJI) corresponde a un organismo público del Estado de Chile, con presencia nacional y alta complejidad operativa. En este contexto, se identificó una problemática asociada al sistema actual de Mesa de Ayuda, el cual operaba principalmente a partir de buzones de correo convertidos en tickets, con limitadas capacidades de análisis, reportería, trazabilidad y apoyo a la toma de decisiones. A ello se sumó la necesidad de fortalecer el control de activos TI institucionales, tales como computadores, notebooks, monitores y periféricos, con el propósito de mejorar su trazabilidad y reducir riesgos asociados a pérdida, robo, obsolescencia o descontrol de inventario.

En respuesta a esta necesidad, el proyecto propuso una solución basada en GLPI para centralizar tickets y activos en una única plataforma, estructurar la información desde su origen, mejorar visibilidad operativa y habilitar reportería y control institucional.

---

## 4. Alcance del MVP

El MVP considerado en este proyecto incluye:

* instalación y configuración base de GLPI en una máquina virtual institucional;
* parametrización de perfiles, entidades, ubicaciones y catálogos base;
* formularios estructurados para ingreso de tickets;
* gestión del ciclo de vida del ticket;
* asignación y trazabilidad de tickets;
* dashboards e indicadores operativos base;
* reportería y exportación básica;
* registro y consulta de activos TI;
* asociación entre tickets y activos;
* control de inventario y estados operativos;
* validación funcional mediante pruebas y sesión de aceptación con usuarios.

Quedan fuera del alcance inicial:

* desarrollo de software a medida sobre el core de GLPI;
* reportería ejecutiva avanzada;
* integración profunda con LDAP, Active Directory u otros sistemas institucionales;
* automatización completa del inventario en todo el parque tecnológico;
* despliegue productivo en contenedores o nube como parte del MVP inicial;
* integraciones complejas con otros sistemas del cliente.

---

## 5. Tecnologías utilizadas

* **GLPI** 10.0.15
* **Apache HTTP Server**
* **PHP** 8.3
* **MariaDB**
* **GLPI Inventory / GLPI Agent**
* **Git**
* **GitHub**

Estas tecnologías fueron seleccionadas por su compatibilidad con la instalación oficial, su bajo costo de adopción, su madurez técnica y su adecuación al contexto institucional del cliente. La arquitectura propuesta se justificó por su simplicidad operativa, facilidad de administración y coherencia con una implementación sobre infraestructura existente.

---

## 6. Estructura del repositorio

```text
proyecto-de-titulo-ipss-2026-evax/
├── CHANGELOG.md
├── Container
│   └── docker-compose.yml
├── LICENSE
├── README.md
├── config
│   └── glpi
│       ├── config.zip
│       └── files.zip
├── docs
│   ├── install
│   │   ├── Instalacion de Agente GLPI .docx
│   │   └── Instalacion de GLPI.docx
│   ├── operation
│   │   └── Manual de Operaciones GLPI.docx
│   └── user-guides
│       ├── Asignar Perfil en GLPI.docx
│       ├── Creacion de Ticket.docx
│       ├── Creacion de Usuarios en GLPI.docx
│       ├── Crear un Perfil en GLPI.docx
│       └── Eliminar Usuarios en GLPI.docx
├── evidence
│   ├── deliverables
│   │   └── Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI.pdf
│   ├── screenshots
│   │   ├── capturas-de-instalacion.docx
│   │   └── repositorio
│   │       ├── backlog.png
│   │       ├── commits.png
│   │       ├── pantalla-principal.png
│   │       ├── releases.png
│   │       └── vista-expandida-del-backlog.png
│   └── testing
│       ├── tc-01_crear-ticket-con-formulario-estructurado-completo
│       ├── tc-02_intentar-crear-ticket-sin-campos-obligatorios
│       ├── tc-03_cambiar-estado-de-ticket-desde-nuevo-a-en-proceso
│       ├── tc-04_asignar-ticket-a-tecnico-o-grupo-de-soporte
│       ├── tc-05_asociar-ticket-a-un-activo-ti-registrado
│       ├── tc-06_registrar-un-activo-ti-con-datos-basicos
│       ├── tc-07_consultar-inventario-filtrado-por-ubicacion
│       ├── tc-08_verificar-relacion-entre-ticket-usuario-ubicacion-y-activo
│       ├── tc-09_validar-que-dashboards-reflejen-datos-de-tickets-reales
│       ├── tc-10_exportar-reporte-filtrado-por-area-y-estado
│       ├── tc-11_validar-restricciones-por-perfil-de-usuario
│       ├── tc-12_verificar-acceso-al-sistema-desde-navegador-institucional
│       ├── tc-13_validar-persistencia-de-datos-luego-de-reinicio-del-servicio
│       ├── tc-14_usuario-final-registra-y-consulta-su-ticket
│       ├── tc-15_jefatura-consulta-indicadores-basicos-de-gestion
│       ├── tc-16_validar-notificacion-al-crear-o-actualizar-ticket
│       ├── tc-17_modificar-estado-de-activo-a-mantencion-o-extraviado
│       └── tc-18_validar-comprension-del-formulario-por-usuario-no-tecnico
└── infra
    ├── database
    │   └── glpi_backup.sql
    └── webserver
        └── etc
            ├── apache2
            │   └── sites-available
            │       └── glpi.conf
            └── php
                └── 8.3
                    └── apache2
                        └── php.ini
````

### Descripción de carpetas principales

**[Container/](<Container/>)**
Incluye artefactos asociados a una posible evolución futura basada en contenedores. No corresponde al mecanismo principal de despliegue del MVP, cuyo entorno oficial se definió sobre máquina virtual institucional.

**[config/glpi/](<config/glpi/>)**
Contiene respaldos o artefactos de configuración del sistema GLPI.

**[docs/install/](<docs/install/>)**
Contiene el manual técnico de instalación de GLPI y del agente GLPI.

**[docs/operation/](<docs/operation/>)**
Contiene el manual breve de operaciones del sistema, incluyendo verificación de estado del servicio Apache, reinicio del servicio y respaldo de base de datos.

**[docs/user-guides/](<docs/user-guides/>)**
Contiene guías de usuario para tareas administrativas y operativas dentro de GLPI.

**[evidence/deliverables/](<evidence/deliverables/>)**
Contiene los entregables formales del proyecto, incluido el informe final.

**[evidence/screenshots/repositorio/](<evidence/screenshots/repositorio/>)**
Contiene capturas del repositorio, backlog, actividad del proyecto y evidencia visual del uso de GitHub como soporte de gestión.

**[evidence/testing/](<evidence/testing/>)**
Contiene evidencias visuales organizadas por caso de prueba, cubriendo TC-01 a TC-18.

**[infra/database/](<infra/database/>)**
Contiene el respaldo de base de datos utilizado como referencia técnica del entorno.

**[infra/webserver/](<infra/webserver/>)**
Contiene los archivos de configuración de Apache y parámetros de PHP asociados al despliegue web.

---

## 7. Requisitos del entorno

### Requisitos de infraestructura

* Hipervisor: **Proxmox Virtual Environment**
* Sistema operativo: **Ubuntu 24.04 LTS**
* CPU: **4 vCPU**
* RAM: **16 GB**
* Disco: **500 GB**
* Arquitectura: **x64**
* Red: **2 interfaces**
* Nombre de máquina: **GLPI_QA**

### Requisitos de software

* Apache
* PHP 8.3
* MariaDB
* GLPI 10.0.15
* GLPI Agent / GLPI Inventory cuando corresponda

Estos parámetros corresponden al entorno de referencia utilizado para la instalación descrita en la documentación técnica del proyecto.

---

## 8. Instalación y ejecución

La instalación completa de la plataforma se documenta en detalle en:

* [Instalacion de GLPI](<docs/install/Instalacion de GLPI.docx>)
* [Instalacion de Agente GLPI](<docs/install/Instalacion de Agente GLPI .docx>)

De manera resumida, el flujo de instalación es el siguiente:

1. Actualizar el sistema operativo.
2. Instalar Apache.
3. Instalar PHP y extensiones requeridas.
4. Instalar MariaDB.
5. Descargar y descomprimir GLPI en `/var/www/html/`.
6. Configurar permisos sobre la carpeta de GLPI.
7. Crear y habilitar el Virtual Host de Apache.
8. Crear base de datos y usuario de aplicación.
9. Finalizar la instalación mediante el asistente web.
10. Validar el acceso al sistema desde navegador.

### Referencias técnicas en el repositorio

* Configuración de Apache:
  [glpi.conf](<infra/webserver/etc/apache2/sites-available/glpi.conf>)

* Configuración de PHP:
  [php.ini](<infra/webserver/etc/php/8.3/apache2/php.ini>)

* Respaldo de base de datos:
  [glpi_backup.sql](<infra/database/glpi_backup.sql>)

* Manual de operaciones:
  [Manual de Operaciones GLPI](<docs/operation/Manual de Operaciones GLPI.docx>)

---

## 9. Acceso a la plataforma

En el entorno de referencia documentado, el acceso inicial se realiza desde navegador hacia la URL del servidor configurado para GLPI.

El asistente web de instalación permite:

* seleccionar idioma;
* validar requisitos;
* configurar conexión a MariaDB;
* inicializar las tablas del sistema;
* habilitar los usuarios por defecto del entorno GLPI.

---

## 10. Funcionalidades cubiertas

Las funcionalidades principales consideradas en la solución son:

* creación de tickets mediante formularios estructurados;
* validación de campos obligatorios;
* gestión de estados del ticket;
* asignación de tickets a técnicos o grupos;
* seguimiento y bitácora de acciones;
* dashboards operativos;
* exportación de reportes;
* registro y consulta de activos TI;
* asociación entre tickets y activos;
* control de inventario y estados operativos;
* gestión de perfiles y permisos.

En términos globales, la solución alcanzó implementación funcional sobre la totalidad de los requerimientos definidos para el MVP, con predominio de funcionalidades completamente implementadas y con operación verificable en ambiente de prueba.

---

## 11. Testing y validación

El proyecto contempla una estrategia de validación basada principalmente en:

* pruebas funcionales;
* pruebas de integración;
* pruebas operacionales;
* pruebas de seguridad básica;
* pruebas de aceptación con usuario final;
* validación de operación directa sobre la plataforma vía navegador web.

Los casos de prueba se encuentran documentados en el informe y respaldados con evidencias visuales en la carpeta:

* [evidence/testing/](<evidence/testing/>)

Actualmente se incluyen evidencias asociadas a los casos **TC-01 a TC-18**, cubriendo flujos críticos del MVP, tales como creación de tickets, validación de formularios, reportería, perfiles de acceso, inventario y asociación entre tickets y activos.

---

## 12. Manuales disponibles

### Manuales técnicos

* [Instalación de GLPI](<docs/install/Instalacion de GLPI.docx>)
* [Instalación del agente GLPI](<docs/install/Instalacion de Agente GLPI .docx>)
* [Manual de operaciones GLPI](<docs/operation/Manual de Operaciones GLPI.docx>)

Ubicación:

* [docs/install/](<docs/install/>)
* [docs/operation/](<docs/operation/>)

### Manuales de usuario

* [Asignación de perfiles](<docs/user-guides/Asignar Perfil en GLPI.docx>)
* [Creación de tickets](<docs/user-guides/Creacion de Ticket.docx>)
* [Creación de usuarios](<docs/user-guides/Creacion de Usuarios en GLPI.docx>)
* [Crear un perfil en GLPI](<docs/user-guides/Crear un Perfil en GLPI.docx>)
* [Eliminación de usuarios](<docs/user-guides/Eliminar Usuarios en GLPI.docx>)

Ubicación:

* [docs/user-guides/](<docs/user-guides/>)

---

## 13. Gestión del proyecto y trazabilidad

El proyecto utilizó **Git** para control de versiones y **GitHub** como plataforma de respaldo, trazabilidad y gestión del trabajo técnico. Además del repositorio, se empleó **GitHub Projects** como soporte para seguimiento del backlog, visualización de actividades, control de iteraciones y registro de avance del proyecto. Esto permitió mantener coherencia entre backlog, planificación semanal, carta Gantt, issues asociados y evolución del trabajo.

Como evidencia complementaria, el repositorio incluye capturas de pantalla del tablero del proyecto, backlog, commits y vistas de seguimiento en:

* [evidence/screenshots/repositorio/](<evidence/screenshots/repositorio/>)

Estas evidencias respaldan la metodología de trabajo descrita en el informe y permiten observar la trazabilidad entre tareas, documentación, control de versiones y avance del MVP.

---

## 14. Documentación del proyecto

La documentación formal del proyecto se encuentra respaldada principalmente en:

* informe final del proyecto;
* anexos técnicos;
* estructura documental del repositorio;
* evidencia de pruebas;
* manuales de instalación, operación y uso;
* capturas del tablero y del repositorio en GitHub.

Entregable principal:

* [Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI](<evidence/deliverables/Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI.pdf>)

---

## 15. Estado actual del proyecto

El proyecto se encuentra desarrollado como una **propuesta técnica de implementación con MVP funcional validado en ambiente de prueba**. Su foco está en demostrar viabilidad, cobertura funcional crítica y alineación con las necesidades del cliente, más que en una puesta en producción institucional completa.

En este contexto, las capacidades críticas del MVP fueron verificadas mediante pruebas documentadas, y las líneas de evolución futura incluyen:

* reportería ejecutiva avanzada;
* mayor automatización de reglas de negocio;
* ampliación del inventario automatizado;
* integración con servicios de identidad;
* fortalecimiento del gobierno del dato;
* posible despliegue futuro en contenedores o nube.

---

## 16. Repositorio y control de versiones

El proyecto utiliza:

* **Git** para control de versiones
* **GitHub** como plataforma de gestión y respaldo del repositorio

Repositorio:
[https://github.com/g3nsvrv/proyecto-de-titulo-ipss-2026/](https://github.com/g3nsvrv/proyecto-de-titulo-ipss-2026/)

Se recomienda mantener en este espacio los commits asociados a documentación, configuración, evidencias y evolución de la propuesta, favoreciendo trazabilidad y mantenibilidad del proyecto.

---

## 17. Licencia

Este repositorio incluye archivo [LICENSE](<LICENSE>).
La plataforma base utilizada en el proyecto corresponde a GLPI, la cual mantiene su propia licencia y condiciones de distribución según la documentación oficial del proyecto.

---

## 18. Autores

* **Andrés Vargas**
* **Jonathan Garcés**

Proyecto desarrollado para:
**Ingeniería en Informática – Instituto Profesional San Sebastián**
Asignatura: **Taller de Integración Profesional – TIP-INF-401**

---

## 19. Observaciones finales

Este repositorio debe entenderse como un soporte técnico y documental del proyecto. La instalación productiva definitiva, los ajustes institucionales específicos, las integraciones avanzadas y la evolución posterior del sistema dependen de decisiones operativas del cliente y de etapas futuras de implementación.
