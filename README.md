# CitaFacil

Sistema digital académico para la gestión de citas médicas. Este README resume la propuesta, la arquitectura y el seguimiento de CitaFacil. Actualmente es el único archivo en la raíz del repositorio; los documentos completos y los diagramas elaborados todavía no están incorporados como archivos aquí.

> Proyecto académico de Ingeniería de Software I. El sistema se trabaja como una propuesta ficticia debido a que la asignatura Diseño de Interfaz de Usuario no se encontraba disponible.

## 1. Nombre y objetivo

**CitaFacil** busca facilitar la gestión de citas médicas mediante una plataforma que permita a los pacientes consultar disponibilidad, reservar horarios y administrar sus citas. También permite que el personal autorizado gestione usuarios, roles, médicos, servicios y horarios.

## 2. Problema que resuelve

La gestión manual de citas puede provocar pérdida de información, duplicación de horarios, dificultad para consultar la disponibilidad y poca visibilidad sobre las citas futuras. CitaFacil centraliza la información y aplica reglas para evitar reservas en horarios ocupados.

## 3. Funcionalidades principales

- Registro e inicio de sesión de usuarios.
- Consulta de disponibilidad por servicio, médico, fecha y horario.
- Reserva de citas médicas.
- Consulta de citas futuras y anteriores.
- Cancelación y reprogramación de citas.
- Gestión de usuarios y roles.
- Administración de médicos, servicios y horarios.
- Validación para evitar conflictos de horario.
- Confirmación y seguimiento del estado de la cita.

## 4. Enfoque metodológico y gestión

Se adopta un enfoque ágil combinado **Scrum + Kanban (Scrumban)**. Scrum orienta la organización iterativa del trabajo y las prioridades; Kanban permite visualizar el flujo y el estado de las tareas en GitHub Projects.

El tablero utiliza las columnas:

- **Backlog:** ideas y tareas pendientes de priorización.
- **Por hacer:** tareas priorizadas y listas para iniciar.
- **En progreso:** tareas que se están trabajando activamente.
- **En revisión:** entregables pendientes de validación.
- **Finalizado:** entregables revisados y aceptados.

Los roles definidos para el inicio son:

- **Analista:** identifica necesidades y redacta requisitos.
- **Responsable del tablero:** organiza tarjetas, prioridades y estados.
- **Responsable de modelado:** mantiene los diagramas UML.
- **Responsable de documentación:** consolida requisitos, decisiones y evidencias.
- **Apoyo técnico:** revisa la solución y apoya la definición de frontend, backend y datos.

## 5. Arquitectura seleccionada

Se propone una arquitectura web por capas:

1. **Frontend:** interfaz con la que interactúan pacientes y administradores.
2. **Backend:** API y lógica de negocio.
3. **Base de datos:** persistencia de usuarios, roles, médicos, servicios, horarios y citas.

### Organización del frontend

El frontend será responsable de:

- Mostrar las pantallas de registro e inicio de sesión.
- Permitir consultar la disponibilidad.
- Presentar formularios para reservar, cancelar y reprogramar.
- Mostrar las citas del paciente.
- Mostrar el panel administrativo según el rol.
- Validar datos básicos antes de enviarlos.
- Consumir la API del backend mediante solicitudes HTTPS y respuestas JSON.

### Organización del backend

El backend será responsable de:

- Autenticar usuarios y controlar sesiones.
- Autorizar operaciones según el rol.
- Validar requisitos y reglas de negocio.
- Consultar horarios disponibles.
- Evitar reservas duplicadas o en horarios ocupados.
- Registrar, cancelar y reprogramar citas.
- Gestionar usuarios, médicos, servicios y horarios.
- Conectarse con la base de datos.
- Registrar errores y eventos importantes.

### Comunicación entre frontend y backend

El frontend enviará solicitudes HTTPS a endpoints de la API. El backend validará la identidad, los permisos y las reglas de negocio; luego consultará o actualizará la base de datos y devolverá una respuesta JSON. El frontend mostrará el resultado al usuario.

Flujo principal de reserva:

1. El paciente inicia sesión.
2. El frontend solicita la disponibilidad al backend.
3. El backend consulta horarios y devuelve los espacios disponibles.
4. El paciente selecciona un horario.
5. El backend verifica nuevamente que el horario continúe libre.
6. El backend registra la cita y devuelve la confirmación.
7. El frontend muestra el resultado al paciente.

## 6. Requisitos y evidencias técnicas

Durante el proyecto se elaboraron los siguientes artefactos:

- Problema y necesidad principal del sistema.
- Técnica breve de levantamiento de información y cinco hallazgos.
- Cinco historias de usuario.
- Requisitos funcionales y no funcionales con prioridades y criterios de aceptación.
- Tabla de trazabilidad entre hallazgos, historias, requisitos e Issues.
- Diagramas de casos de uso, clases, secuencia, colaboración y actividades.
- Propuesta de arquitectura y organización frontend/backend.
- Gestión del avance mediante GitHub Projects.

**Estado de los archivos:** estos materiales se trabajaron en documentos académicos y Visual Paradigm Online, pero todavía no están adjuntos ni versionados en este repositorio. La raíz del repositorio contiene actualmente solo este README.md.

## 7. Registro breve de cambios

| # | Avance o ajuste | Resultado |
|---|---|---|
| 1 | Definición del alcance de CitaFacil | Se establecieron usuarios, citas, disponibilidad, roles y administración. |
| 2 | Levantamiento y organización de requisitos | Se documentaron hallazgos, historias de usuario, requisitos y criterios de aceptación. |
| 3 | Configuración de GitHub Projects | Se crearon tarjetas iniciales, prioridades, responsables y columnas Kanban. |
| 4 | Modelado UML | Se elaboraron y validaron los diagramas de casos de uso, clases, secuencia, colaboración y actividades. |
| 5 | Consolidación técnica | Se definieron la arquitectura frontend/backend, los riesgos, los Issues de seguimiento y esta versión inicial controlada. |

## 8. Issues seleccionados para seguimiento

Estos cuatro Issues siguen abiertos y representan tareas, riesgos y validaciones relevantes para la siguiente etapa:

1. [#14 Diseñar la API para la gestión de citas](https://github.com/unkserious/CitaFacil/issues/14) — **Por hacer**; tarea técnica para definir la comunicación entre frontend y backend.
2. [#15 Configurar copias de seguridad y recuperación de datos](https://github.com/unkserious/CitaFacil/issues/15) — **Backlog**; riesgo de pérdida de información.
3. [#18 Implementar el control de permisos por rol](https://github.com/unkserious/CitaFacil/issues/18) — **Por hacer**; control necesario para proteger las funciones administrativas.
4. [#20 Preparar pruebas funcionales de autenticación](https://github.com/unkserious/CitaFacil/issues/20) — **Por hacer**; verificación pendiente para registro e inicio de sesión.

Los Issues de historias de usuario #7–#11 se conservan como evidencia y están en **Finalizado** en el tablero porque sus historias y criterios de aceptación quedaron documentados.

## 9. Estado actual del tablero

El [Project CitaFacil](https://github.com/users/unkserious/projects/2/views/1) contiene 21 tarjetas distribuidas según el avance documentado:

- **Finalizado (10):** #2 modelo de datos inicial, #3 requisitos, #6 gestión de roles, #7–#11 historias de usuario, #13 casos de uso y criterios de aceptación, y #19 reglas de validación de reservas.
- **En revisión (1):** #4 diseño de registro e inicio de sesión; el flujo base está modelado y falta validar el detalle.
- **Por hacer (7):** #5 módulo de reserva, #12 estructura inicial del proyecto, #14 API, #16 interfaces de agenda y disponibilidad, #17 esquema de base de datos, #18 permisos por rol y #20 pruebas funcionales de autenticación.
- **Backlog (3):** #1 panel administrativo, #15 copias de seguridad y recuperación, y #21 pruebas de integración.
- **En progreso (0):** no hay implementación activa; el proyecto está en documentación y planificación técnica.

Los diez Issues asociados a elementos finalizados están cerrados. Las otras once tareas continúan abiertas en GitHub para su seguimiento.

## 10. Herramientas utilizadas

- Git y GitHub para control de versiones y repositorio.
- GitHub Issues para incidencias, riesgos, mejoras y tareas pendientes.
- GitHub Projects para planificación y seguimiento Kanban.
- Visual Paradigm Online para los diagramas UML.
- Markdown para documentación técnica.
- Microsoft Word para la entrega de evidencias académicas.

## 11. Nota técnica de versión

### Versión documental 0.1.0 — línea base inicial

Esta es una línea base de documentación y planificación, no una versión ejecutable del sistema.

**Contenido:** alcance funcional, propuesta de arquitectura, registro de cambios, Issues seleccionados y estado del tablero. Los documentos completos de requisitos y los diagramas UML se elaboraron fuera del repositorio y todavía falta incorporarlos aquí.

**Cambios controlados:** se registraron cinco avances; se actualizaron los estados de las 21 tarjetas; se cerraron en GitHub los Issues cuyos entregables documentales quedaron finalizados; se separaron los casos de uso Cancelar cita y Reprogramar cita; y se corrigieron las relaciones UML de inclusión y extensión junto con el límite del sistema.

**Pendientes:** incorporar al repositorio los archivos de requisitos, trazabilidad y modelos UML; iniciar la implementación de frontend y backend; diseñar la API; crear la base de datos; implementar permisos; y preparar pruebas, copias de seguridad e integración.

**Próximo paso técnico:** añadir al repositorio las evidencias documentales y modelos UML ya elaborados; luego configurar la estructura inicial del proyecto (#12) y diseñar la API de citas (#14).

## Estado del proyecto

CitaFacil se encuentra en etapa de análisis, modelado y planificación técnica. La documentación y la versión inicial controlada están preparadas; la implementación funcional queda como siguiente etapa.
