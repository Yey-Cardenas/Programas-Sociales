# Requisitos funcionales

## 1. Objetivo

Este documento describe los requisitos funcionales del Sistema de Gestión de Programas Sociales de Huamanga. Estos requisitos especifican las operaciones que deberá ofrecer el sistema para registrar, consultar y mantener la información de los beneficiarios, facilitar el trabajo del personal municipal y apoyar la gestión de los programas sociales.

Los requisitos se plantean como parte de la propuesta académica. Su inclusión en este documento no significa que las funcionalidades ya se encuentren implementadas.

## 2. Actores del sistema

| Actor | Responsabilidad |
|---|---|
| Responsable de comité | Registrar y consultar información de los beneficiarios de acuerdo con sus permisos. |
| Personal municipal autorizado | Revisar registros, atender alertas de duplicidad y realizar las operaciones administrativas permitidas. |
| Administrador del sistema | Gestionar los accesos y las configuraciones que le correspondan. |
| Beneficiario | Recibir notificaciones cuando el sistema y los canales de comunicación definidos lo permitan. |

Los beneficiarios no se consideran usuarios que necesariamente deban iniciar sesión en el sistema. Su participación se limita a las operaciones que les correspondan, como la recepción de notificaciones.

## 3. Requisitos funcionales

### RF-01. Registro de beneficiarios

**Descripción:** El sistema deberá permitir que los usuarios autorizados registren nuevos beneficiarios de los programas sociales.

**Actor principal:** Responsable de comité.

**Criterios de aceptación:**
- Permitir ingresar los datos requeridos para registrar al beneficiario.
- Validar los campos obligatorios y los formatos correspondientes.
- Comprobar la información antes de guardar el registro.
- Informar al usuario si el registro se realizó correctamente o si existen errores.

**Prioridad:** Alta.

**Trazabilidad:** HU-01.

### RF-02. Detección de posibles beneficiarios duplicados

**Descripción:** El sistema deberá verificar si el documento de identidad de un beneficiario ya se encuentra registrado en el padrón.

**Actor principal:** Responsable de comité.

**Criterios de aceptación:**
- Comprobar el documento de identidad antes de confirmar el registro.
- Advertir cuando se encuentre una coincidencia.
- Evitar la creación automática de un registro duplicado.
- Permitir que el usuario autorizado siga el procedimiento de revisión establecido.

**Prioridad:** Alta.

**Trazabilidad:** HU-02, DA-02 y AC-02.

**Consideración:** La coincidencia deberá tratarse como una alerta que requiere revisión cuando no sea posible determinar automáticamente si se trata de la misma persona o de un error en los datos.

### RF-03. Actualización de información de beneficiarios

**Descripción:** El sistema deberá permitir que los usuarios autorizados actualicen los datos de los beneficiarios según sus permisos.

**Actor principal:** Responsable de comité o personal municipal autorizado.

**Criterios de aceptación:**
- Permitir consultar la información existente.
- Validar los datos antes de guardar las modificaciones.
- Informar si la actualización fue exitosa.
- Registrar las modificaciones que deban quedar sujetas a auditoría.

**Prioridad:** Alta.

**Trazabilidad:** HU-01, AC-04 y AC-06.

### RF-04. Desactivación de beneficiarios

**Descripción:** El sistema deberá permitir desactivar un registro cuando corresponda, conservando la información histórica necesaria.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Solicitar confirmación antes de desactivar un registro.
- Registrar la operación de acuerdo con las reglas de auditoría.
- Evitar que un registro desactivado se considere automáticamente activo en las consultas operativas.
- Permitir consultar el historial según los permisos del usuario.

**Prioridad:** Alta.

**Trazabilidad:** HU-03 y AC-06.

**Consideración:** La desactivación no implica eliminar físicamente el registro. Las condiciones para reactivar un beneficiario deberán definirse como parte de las reglas del negocio.

### RF-05. Gestión de alertas de duplicidad

**Descripción:** El sistema deberá permitir que el personal municipal autorizado revise las alertas relacionadas con posibles beneficiarios duplicados.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Mostrar información suficiente para revisar la coincidencia sin exponer datos innecesarios.
- Permitir registrar el resultado de la revisión.
- Conservar evidencia de la decisión cuando corresponda.
- Restringir la resolución de las alertas a los usuarios autorizados.

**Prioridad:** Alta.

**Trazabilidad:** HU-04, DA-02 y AC-06.

**Consideración:** Se deberá definir quién resuelve las alertas cuando los registros pertenezcan a distintos comités y qué procedimiento se seguirá en caso de desacuerdo.

### RF-06. Revalidación periódica de beneficiarios

**Descripción:** El sistema deberá permitir gestionar la revalidación periódica de la información de los beneficiarios.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Permitir identificar los registros que requieren revalidación.
- Registrar el resultado y la fecha de la revisión.
- Permitir consultar el estado de la revalidación.
- Informar al usuario cuando se requiera una revisión.

**Prioridad:** Alta.

**Trazabilidad:** HU-05.

**Consideración:** La propuesta contempla una revalidación cada seis meses. El periodo definitivo y las condiciones aplicables deberán confirmarse con los responsables del proyecto.

### RF-07. Notificaciones a beneficiarios

**Descripción:** El sistema deberá contemplar el envío de notificaciones a los beneficiarios sobre eventos definidos, como la aprobación o revalidación de su registro.

**Actor principal:** Personal municipal autorizado y servicio de notificaciones.

**Criterios de aceptación:**
- Identificar los eventos que generan una notificación.
- Preparar el mensaje correspondiente.
- Utilizar un canal y un proveedor previamente definidos.
- Registrar el resultado del intento de envío cuando la integración lo permita.
- Informar de los errores de envío para facilitar su revisión.

**Prioridad:** Media-alta.

**Trazabilidad:** HU-06 y DA-06.

**Consideración:** La integración con SMS o WhatsApp está pendiente de definición. El envío de mensajes no deberá considerarse disponible hasta que se seleccione y valide el proveedor correspondiente.

### RF-08. Consulta geográfica de cobertura

**Descripción:** El sistema deberá contemplar la visualización geográfica de la cobertura de los programas sociales utilizando la información disponible y autorizada.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Permitir consultar la cobertura por los criterios que se definan.
- Mostrar la información geográfica disponible.
- Restringir la exposición de datos personales según los permisos establecidos.
- Informar cuando no existan datos suficientes para generar la visualización.

**Prioridad:** Media.

**Trazabilidad:** HU-07 y DA-08.

**Consideración:** La herramienta cartográfica y la fuente de datos geográficos deberán definirse posteriormente, manteniendo la compatibilidad con Microsoft SQL Server.

### RF-09. Generación de reportes

**Descripción:** El sistema deberá permitir generar reportes sobre la información de los beneficiarios y la gestión de los programas sociales.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Permitir consultar información mediante filtros que se definan.
- Presentar los resultados de forma ordenada.
- Respetar los permisos de acceso a la información.
- Permitir la exportación a Excel y PDF cuando se hayan definido y validado los mecanismos correspondientes.

**Prioridad:** Alta.

**Trazabilidad:** HU-08.

**Consideración:** Los reportes deberán incluir únicamente la información necesaria para la finalidad de cada consulta.

### RF-10. Importación de información histórica

**Descripción:** El sistema deberá contemplar la importación controlada de información histórica procedente de archivos utilizados previamente para gestionar los programas sociales.

**Actor principal:** Personal municipal autorizado.

**Criterios de aceptación:**
- Permitir seleccionar un archivo en un formato admitido.
- Validar la estructura y los datos antes de incorporarlos.
- Identificar registros incompletos, inválidos o posiblemente duplicados.
- Presentar un resumen de los resultados y errores de la importación.
- Permitir revisar los errores antes de confirmar la incorporación de los registros.

**Prioridad:** Alta.

**Trazabilidad:** HU-09 y DA-07.

**Consideración:** Los formatos admitidos, el procedimiento de corrección y las reglas para confirmar una importación deberán definirse antes de desarrollar esta funcionalidad.

### RF-11. Autenticación de usuarios

**Descripción:** El sistema deberá permitir que los usuarios autorizados se identifiquen para acceder a las funciones restringidas.

**Actor principal:** Usuarios del sistema.

**Criterios de aceptación:**
- Permitir iniciar sesión mediante el mecanismo de autenticación definido.
- Rechazar credenciales inválidas.
- Restringir las funciones protegidas a usuarios autenticados.
- Permitir cerrar sesión.
- Proteger las credenciales y la información de autenticación.

**Prioridad:** Alta.

**Trazabilidad:** HU-10, AC-04 y DA-03.

**Consideración:** El mecanismo concreto de autenticación deberá definirse durante el diseño detallado.

### RF-12. Autorización por roles

**Descripción:** El sistema deberá limitar las operaciones disponibles según el rol y los permisos asignados a cada usuario.

**Actor principal:** Administrador del sistema.

**Criterios de aceptación:**
- Diferenciar los permisos de los responsables de comité, el personal municipal y los administradores.
- Comprobar los permisos antes de ejecutar operaciones protegidas.
- Impedir que un usuario realice operaciones para las que no tiene autorización.
- Permitir revisar y mantener las asignaciones de roles de acuerdo con las responsabilidades administrativas.

**Prioridad:** Alta.

**Trazabilidad:** HU-10 y AC-04.

**Consideración:** La matriz definitiva de permisos deberá aprobarse antes de la implementación.

### RF-13. Registro de auditoría

**Descripción:** El sistema deberá registrar las operaciones relevantes que requieran trazabilidad.

**Actor principal:** Personal municipal autorizado y administrador del sistema, según sus permisos.

**Criterios de aceptación:**
- Registrar las operaciones definidas como auditables.
- Conservar la fecha, el usuario, el tipo de operación y la referencia al registro afectado cuando corresponda.
- Restringir la consulta de los registros de auditoría.
- Evitar almacenar credenciales o información sensible innecesaria en dichos registros.

**Prioridad:** Alta.

**Trazabilidad:** HU-04, AC-06 y DA-03.

### RF-14. Registro y sincronización con conectividad limitada

**Descripción:** El sistema deberá evaluar y contemplar la posibilidad de registrar temporalmente determinadas operaciones cuando no exista conexión, sincronizando posteriormente los datos con el sistema central.

**Actor principal:** Responsable de comité.

**Criterios de aceptación:**
- Definir qué operaciones estarán disponibles sin conexión.
- Identificar los datos pendientes de sincronización.
- Validar la información antes de incorporarla al sistema central.
- Informar el resultado de la sincronización y los posibles errores.
- Contemplar reintentos y procedimientos de resolución de conflictos.
- Proteger los datos almacenados localmente.

**Prioridad:** Alta.

**Trazabilidad:** HU-11, AC-05 y DA-01.

**Consideración:** La disponibilidad de operaciones sin conexión, el almacenamiento local y la sincronización requieren diseño, implementación y pruebas específicas.

## 4. Resumen de requisitos funcionales

| Código | Requisito | Prioridad |
|---|---|---|
| RF-01 | Registro de beneficiarios | Alta |
| RF-02 | Detección de posibles beneficiarios duplicados | Alta |
| RF-03 | Actualización de información de beneficiarios | Alta |
| RF-04 | Desactivación de beneficiarios | Alta |
| RF-05 | Gestión de alertas de duplicidad | Alta |
| RF-06 | Revalidación periódica de beneficiarios | Alta |
| RF-07 | Notificaciones a beneficiarios | Media-alta |
| RF-08 | Consulta geográfica de cobertura | Media |
| RF-09 | Generación de reportes | Alta |
| RF-10 | Importación de información histórica | Alta |
| RF-11 | Autenticación de usuarios | Alta |
| RF-12 | Autorización por roles | Alta |
| RF-13 | Registro de auditoría | Alta |
| RF-14 | Registro y sincronización con conectividad limitada | Alta |

## 5. Consideraciones generales

Los requisitos funcionales deberán detallarse con los responsables del proyecto antes de su implementación. En particular:

- Se deberán definir los datos obligatorios para el registro de beneficiarios.
- Se deberá establecer el procedimiento para resolver posibles duplicados entre comités.
- Se deberán precisar las reglas de revalidación y desactivación.
- Se deberán confirmar los canales de notificación y sus proveedores.
- Se deberán definir los formatos de importación y exportación.
- Se deberá establecer la matriz de roles y permisos.
- Se deberán definir las operaciones sin conexión y las reglas de sincronización.
- Se deberán identificar las operaciones que requieren auditoría.

## 6. Relación con la arquitectura

La propuesta utiliza un monolito modular desarrollado con C#, .NET 9 y ASP.NET Core MVC 9. Para la persistencia de datos se consideran Entity Framework Core 9 y Microsoft SQL Server.

La organización de los módulos deberá permitir mantener separadas las responsabilidades de gestión de beneficiarios, validación de registros, consultas, reportes, auditoría y servicios compartidos.

Las funcionalidades de notificación, consulta geográfica e interacción sin conexión deberán detallarse antes de definir sus integraciones técnicas.

## 7. Referencias relacionadas

- [Actores del sistema](./01-actores.md)
- [Historias de usuario](./02-historias-de-usuario.md)
- [Atributos de calidad](./04-atributos-de-calidad.md)
- [Restricciones](./05-restricciones.md)
- [Drivers arquitectónicos](./06-drivers-arquitectonicos.md)
- [Requisitos no funcionales](./07-requisitos-no-funcionales.md)
- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
