# Proyecto de Título: Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI

## 1. Descripción general

Este repositorio contiene los artefactos técnicos, documentales y de evidencia asociados al proyecto **“Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI”**.

La propuesta se orienta a resolver dos necesidades principales del cliente:

* fortalecer la gestión de Mesa de Ayuda, actualmente muy dependiente del correo electrónico y con limitadas capacidades de reportería, trazabilidad y control;
* incorporar gestión y control de activos TI, con foco en ubicación, estado, responsable, antigüedad y relación con tickets de soporte.

La solución se basa en **GLPI**, desplegado sobre una **máquina virtual institucional**, utilizando una arquitectura web monolítica en capas sobre **Apache**, **PHP** y **MariaDB**. El proyecto contempla además inventario automatizado mediante **GLPI Inventory / GLPI Agent** como línea de apoyo al control de activos. 

---

## 2. Objetivo del repositorio

Este repositorio tiene por objetivo centralizar:

* la configuración técnica del entorno;
* los artefactos de despliegue y servidor web;
* los respaldos y estructuras de base de datos;
* la documentación técnica del proyecto;
* los casos de prueba y evidencias funcionales;
* los manuales de instalación y de usuario;
* los entregables formales asociados al informe final.

---

## 3. Alcance del MVP

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
* control de estados de activos;
* validación funcional mediante pruebas y sesión de aceptación.

Quedan fuera del alcance inicial:

* desarrollo de software a medida sobre el core de GLPI;
* reportería ejecutiva avanzada;
* integración profunda con LDAP, Active Directory u otros sistemas institucionales;
* automatización completa del inventario en todo el parque tecnológico;
* despliegue productivo en contenedores o nube como parte del MVP inicial. 

---

## 4. Tecnologías utilizadas

* **GLPI** 11.0.6
* **Apache HTTP Server**
* **PHP** 8.3
* **MariaDB**
* **GLPI Inventory / GLPI Agent**
* **Git**
* **GitHub**

Estas tecnologías fueron seleccionadas por su compatibilidad con la instalación oficial, su bajo costo de adopción, su madurez técnica y su adecuación al contexto institucional del cliente. 

---

## 5. Estructura del repositorio

```text
proyecto-de-titulo-ipss-2026-eva2/
├── .github/
│   └── workflows/
│       └── changelog.yml
├── Container/
│   ├── .env
│   └── docker-compose.yml
├── config/
│   └── glpi/
│       ├── config.zip
│       └── files.zip
├── docs/
│   ├── install/
│   │   ├── Instalacion de Agente GLPI .docx
│   │   └── Instalacion de GLPI.docx
│   ├── testing/
│   │   └── evidencias TC-01 a TC-18
│   └── user-guides/
│       ├── Asignar Perfil en GLPI.docx
│       ├── Creacion de Ticket.docx
│       ├── Creacion de Usuarios en GLPI.docx
│       ├── Crear un Perfil en GLPI.docx
│       └── Eliminar Usuarios en GLPI.docx
├── evidence/
│   ├── deliverables/
│   │   └── Implementación de GLPI para la gestión...
│   └── screenshots/
│       └── Print de instalacion.docx
├── infra/
│   ├── database/
│   │   └── glpi_backup.sql
│   └── webserver/
│       └── etc/
│           ├── apache2/
│           │   └── sites-available/
│           │       └── glpi.conf
│           └── php/
│               └── 8.3/
│                   └── apache2/
│                       └── php.ini
├── LICENSE
└── README.md
```

### Descripción de carpetas principales

**`.github/workflows/`**
Contiene automatizaciones de apoyo al repositorio, como flujos de changelog.

**`Container/`**
Incluye artefactos asociados a una posible evolución futura basada en contenedores. No corresponde al mecanismo principal de despliegue del MVP, cuyo entorno oficial se definió sobre máquina virtual institucional.

**`config/glpi/`**
Contiene respaldos o artefactos de configuración del sistema GLPI.

**`docs/install/`**
Manual técnico de instalación de GLPI y del agente GLPI.

**`docs/testing/`**
Evidencias visuales de los casos de prueba funcionales, de integración, operacionales y de aceptación.

**`docs/user-guides/`**
Guías de usuario para tareas administrativas y operativas dentro de GLPI.

**`evidence/deliverables/`**
Entregables formales del proyecto, incluido el informe.

**`infra/database/`**
Respaldo de base de datos utilizado como referencia técnica del entorno.

**`infra/webserver/`**
Archivos de configuración de Apache y parámetros de PHP asociados al despliegue web.

---

## 6. Requisitos del entorno

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
* GLPI
* GLPI Agent / GLPI Inventory cuando corresponda

Estos parámetros corresponden al entorno de referencia utilizado para la instalación descrita en la documentación técnica del proyecto. 

---

## 7. Instalación y ejecución

La instalación completa de la plataforma se documenta en detalle en:

* `docs/install/Instalacion de GLPI.docx`
* `docs/install/Instalacion de Agente GLPI .docx`

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
  `infra/webserver/etc/apache2/sites-available/glpi.conf`

* Configuración de PHP:
  `infra/webserver/etc/php/8.3/apache2/php.ini`

* Respaldo de base de datos:
  `infra/database/glpi_backup.sql`

---

## 8. Acceso a la plataforma

En el entorno de referencia documentado, el acceso inicial se realiza desde navegador hacia la URL del servidor configurado para GLPI.

El asistente web de instalación permite:

* seleccionar idioma;
* validar requisitos;
* configurar conexión a MariaDB;
* inicializar las tablas del sistema;
* habilitar los usuarios por defecto del entorno GLPI.

---

## 9. Funcionalidades cubiertas

Las funcionalidades principales consideradas en la solución son:

* creación de tickets mediante formularios estructurados;
* validación de campos obligatorios;
* gestión de estados del ticket;
* asignación de tickets a técnicos o grupos;
* seguimiento y bitácora de acciones;
* dashboards operativos;
* exportación de reportes;
* registro de activos TI;
* asociación ticket-activo;
* consulta de inventario;
* control de estados de activos;
* gestión de perfiles y permisos. 

---

## 10. Testing y validación

El proyecto contempla una estrategia de validación basada principalmente en:

* pruebas funcionales;
* pruebas de integración;
* pruebas operacionales;
* pruebas de seguridad básica;
* pruebas de aceptación con usuario final.

Los casos de prueba se encuentran documentados en el informe y respaldados con evidencias visuales en la carpeta:

* `docs/testing/`

Actualmente se incluyen evidencias asociadas a los casos **TC-01 a TC-18**, cubriendo flujos críticos del MVP, tales como creación de tickets, validación de formularios, reportería, perfiles de acceso, inventario y asociación entre tickets y activos. 

---

## 11. Manuales disponibles

### Manual técnico

* Instalación de GLPI
* Instalación del agente GLPI

Ubicación:

* `docs/install/`

### Manuales de usuario

* Creación de usuarios
* Asignación de perfiles
* Creación de tickets
* Eliminación de usuarios

Ubicación:

* `docs/user-guides/`

---

## 12. Documentación del proyecto

La documentación formal del proyecto se encuentra respaldada principalmente en:

* informe final del proyecto;
* anexos técnicos;
* estructura documental del repositorio;
* evidencia de pruebas;
* manuales de instalación y uso.

Entregable principal:

* `evidence/deliverables/Implementación de GLPI para la gestión de Mesa de Ayuda y control de activos TI en JUNJI.docx`

---

## 13. Estado actual del proyecto

El proyecto se encuentra desarrollado como una **propuesta técnica de implementación con MVP funcional validado en ambiente de prueba**. Su foco está en demostrar viabilidad, cobertura funcional crítica y alineación con las necesidades del cliente, más que en una puesta en producción institucional completa.

En este contexto, las capacidades críticas del MVP fueron verificadas mediante pruebas documentadas, y las líneas de evolución futura incluyen:

* reportería ejecutiva avanzada;
* mayor automatización de reglas de negocio;
* ampliación del inventario automatizado;
* integración con servicios de identidad;
* posible despliegue futuro en contenedores o nube. 

---

## 14. Repositorio y control de versiones

El proyecto utiliza:

* **Git** para control de versiones
* **GitHub** como plataforma de gestión y respaldo del repositorio

Repositorio:
`https://github.com/g3nsvrv/proyecto-de-titulo-ipss-2026/`

---

## 15. Licencia

Este repositorio incluye archivo `LICENSE`.
La plataforma base utilizada en el proyecto corresponde a GLPI, la cual mantiene su propia licencia y condiciones de distribución según documentación oficial del proyecto.

---

## 16. Autores

* **Andrés Vargas**
* **Jonathan Garcés**

Proyecto desarrollado para:
**Ingeniería en Informática – Instituto Profesional San Sebastián**
Asignatura: **Taller de Integración Profesional – TIP-INF-401**

---

## 17. Observaciones finales

Este repositorio debe entenderse como un soporte técnico y documental del proyecto. La instalación productiva definitiva, los ajustes institucionales específicos, las integraciones avanzadas y la evolución posterior del sistema dependen de decisiones operativas del cliente y de etapas futuras de implementación.