# Historias de usuario

## 1. Objetivo

Este documento describe las historias de usuario del Sistema de Gestión de Programas Sociales de Huamanga. Cada historia representa una necesidad de los usuarios y establece criterios de aceptación que permitirán orientar el desarrollo y comprobar el comportamiento esperado del sistema.

Las historias se encuentran vinculadas con los requisitos funcionales y los atributos de calidad. Su descripción corresponde a la propuesta del sistema; no implica que las funcionalidades ya estén implementadas.

## 2. Actores identificados

- **Responsable de comité:** registra y consulta información de los beneficiarios según sus permisos.
- **Personal municipal autorizado:** revisa registros, atiende alertas y realiza operaciones administrativas.
- **Administrador del sistema:** gestiona los accesos y las configuraciones que le correspondan.
- **Beneficiario:** recibe notificaciones cuando corresponda y cuando los canales de comunicación estén disponibles.

## 3. Historias de usuario

### HU-01. Registro y actualización de beneficiarios

**Como** responsable de comité,

**quiero** registrar y actualizar la información de los beneficiarios,

**para** mantener los datos necesarios para la gestión de los programas sociales.

**Criterios de aceptación:**

- El sistema permite ingresar los datos obligatorios definidos para el registro.
- El sistema valida los campos requeridos y sus formatos.
- El sistema informa cuando faltan datos o existe algún error.
- El usuario puede consultar los datos existentes antes de actualizarlos.
- Solo los usuarios autorizados pueden registrar o modificar información.
- Las modificaciones sujetas a auditoría quedan registradas.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-01, RF-03 y RF-13.

### HU-02. Detección de beneficiarios duplicados

**Como** responsable de comité,

**quiero** que el sistema compruebe si el documento de identidad ya está registrado,

**para** evitar duplicaciones en el padrón de beneficiarios.

**Criterios de aceptación:**

- El sistema comprueba el documento de identidad antes de confirmar el registro.
- Si encuentra una coincidencia, muestra una alerta al usuario.
- El sistema evita crear automáticamente un registro duplicado.
- La coincidencia puede remitirse al personal autorizado para su revisión.
- El sistema no elimina ni modifica automáticamente un registro existente por el solo hecho de encontrar una coincidencia.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-02 y RF-05.

### HU-03. Desactivación de beneficiarios

**Como** personal municipal autorizado,

**quiero** desactivar un registro cuando corresponda,

**para** mantener actualizado el padrón sin perder la información histórica necesaria.

**Criterios de aceptación:**

- El sistema solicita confirmación antes de desactivar el registro.
- La operación solo puede realizarla un usuario autorizado.
- El registro desactivado deja de aparecer como activo en las consultas operativas correspondientes.
- La información histórica se conserva según las reglas de gestión de datos.
- La operación queda registrada cuando corresponda.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-04 y RF-13.

### HU-04. Revisión de duplicados y consulta de auditoría

**Como** personal municipal autorizado,

**quiero** revisar las alertas de posibles duplicados y consultar el historial de operaciones relevantes,

**para** resolver inconsistencias y conocer los cambios realizados en los registros.

**Criterios de aceptación:**

- El sistema muestra las alertas pendientes de revisión.
- La información presentada permite analizar las coincidencias sin exponer datos innecesarios.
- El usuario autorizado puede registrar el resultado de la revisión.
- El sistema permite consultar los registros de auditoría según los permisos asignados.
- Los eventos auditables incluyen información suficiente para identificar la operación y su responsable.
- Las decisiones relacionadas con duplicados entre comités siguen un procedimiento previamente definido.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-05, RF-13 y RF-12.

### HU-05. Revalidación periódica de beneficiarios

**Como** personal municipal autorizado,

**quiero** identificar y registrar las revalidaciones de los beneficiarios,

**para** mantener actualizada su información y verificar que corresponda a los criterios del programa social.

**Criterios de aceptación:**

- El sistema permite consultar los beneficiarios que requieren revalidación.
- El usuario autorizado puede registrar la fecha y el resultado de la revisión.
- El sistema permite consultar el estado de la revalidación.
- Las revisiones realizadas quedan registradas según las reglas de auditoría.
- El sistema permite identificar los registros pendientes de revisión.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-06 y RF-13.

**Consideración:** Se propone un periodo de revalidación de seis meses. La periodicidad definitiva deberá confirmarse con los responsables del proyecto.

### HU-06. Notificaciones a beneficiarios

**Como** personal municipal autorizado,

**quiero** que los beneficiarios puedan recibir notificaciones sobre eventos importantes de su registro,

**para** mantenerlos informados sobre los procesos de aprobación o revalidación que les correspondan.

**Criterios de aceptación:**

- Se definen los eventos que generan una notificación.
- El sistema prepara el mensaje correspondiente al evento.
- El envío utiliza un canal y un proveedor previamente definidos.
- Cuando la integración lo permita, el sistema registra el resultado del intento de envío.
- Los errores de envío pueden identificarse para su revisión.
- Las notificaciones respetan las medidas de protección de datos personales aplicables.

**Prioridad:** Media-alta.

**Requisitos relacionados:** RF-07.

**Consideración:** La integración con SMS o WhatsApp está pendiente de definición y validación.

### HU-07. Consulta geográfica de cobertura

**Como** personal municipal autorizado,

**quiero** consultar la distribución geográfica de la cobertura de los programas sociales,

**para** comprender cómo se distribuyen los beneficiarios en las zonas atendidas.

**Criterios de aceptación:**

- El sistema permite consultar la cobertura según los criterios que se definan.
- La visualización utiliza los datos geográficos disponibles.
- Si faltan datos para generar una visualización, el sistema informa esta situación.
- La consulta respeta los permisos y las restricciones de privacidad.
- La representación geográfica permite interpretar los resultados de manera comprensible.

**Prioridad:** Media.

**Requisitos relacionados:** RF-08.

**Consideración:** La herramienta cartográfica y las fuentes de datos geográficos deberán seleccionarse durante el diseño detallado.

### HU-08. Generación y exportación de reportes

**Como** personal municipal autorizado,

**quiero** generar reportes sobre los beneficiarios y los programas sociales,

**para** revisar información consolidada y facilitar las actividades administrativas.

**Criterios de aceptación:**

- El sistema permite consultar información mediante filtros definidos.
- Los resultados se presentan de forma ordenada.
- Los reportes respetan los permisos de acceso a la información.
- El sistema contempla la exportación a Excel y PDF.
- El usuario recibe información cuando no existen resultados para los criterios seleccionados.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-09.

**Consideración:** Los formatos, los filtros y las plantillas definitivas deberán definirse antes de implementar los mecanismos de exportación.

### HU-09. Importación de información histórica

**Como** personal municipal autorizado,

**quiero** importar información histórica desde archivos previamente utilizados,

**para** consolidar los registros existentes y facilitar su gestión desde el nuevo sistema.

**Criterios de aceptación:**

- El sistema permite seleccionar archivos de formatos admitidos.
- Se valida la estructura del archivo antes de procesarlo.
- Se identifican datos incompletos, formatos inválidos y posibles duplicados.
- El sistema presenta un resumen de los registros válidos y de los errores detectados.
- Los registros no se incorporan definitivamente hasta completar las validaciones establecidas.
- El usuario autorizado puede revisar los errores antes de confirmar la importación.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-10.

**Consideración:** Los formatos de origen y las reglas de validación deberán definirse antes de implementar esta funcionalidad.

### HU-10. Acceso seguro y gestión de permisos

**Como** administrador del sistema,

**quiero** gestionar el acceso de los usuarios según sus roles y responsabilidades,

**para** proteger la información y asegurar que cada usuario realice únicamente las operaciones autorizadas.

**Criterios de aceptación:**

- Los usuarios deben autenticarse para acceder a las funciones restringidas.
- El sistema diferencia los roles y sus permisos.
- Las operaciones protegidas comprueban los permisos antes de ejecutarse.
- Los usuarios sin autorización no pueden realizar operaciones restringidas.
- Las credenciales se gestionan de manera segura.
- El usuario puede cerrar su sesión.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-11 y RF-12.

**Consideración:** La matriz definitiva de roles y permisos deberá acordarse con los responsables del proyecto.

### HU-11. Registro con conectividad limitada

**Como** responsable de comité,

**quiero** poder registrar temporalmente determinadas operaciones cuando no exista conexión a Internet,

**para** continuar mi trabajo y sincronizar los datos cuando la conexión esté disponible.

**Criterios de aceptación:**

- Se definen las operaciones que podrán realizarse sin conexión.
- Los datos pendientes de sincronización pueden identificarse.
- La información se valida antes de incorporarse al sistema central.
- El sistema informa si la sincronización se realizó o si ocurrió un error.
- Se contemplan reintentos y mecanismos para resolver conflictos.
- Los datos almacenados localmente se protegen frente a accesos no autorizados.
- El usuario puede identificar las operaciones que todavía no se han sincronizado.

**Prioridad:** Alta.

**Requisitos relacionados:** RF-14.

**Consideración:** El almacenamiento local, las capacidades PWA y la sincronización deberán diseñarse y probarse antes de considerar disponible esta funcionalidad.

## 4. Resumen de historias de usuario

| Código | Historia de usuario | Prioridad |
|---|---|---|
| HU-01 | Registro y actualización de beneficiarios | Alta |
| HU-02 | Detección de beneficiarios duplicados | Alta |
| HU-03 | Desactivación de beneficiarios | Alta |
| HU-04 | Revisión de duplicados y consulta de auditoría | Alta |
| HU-05 | Revalidación periódica de beneficiarios | Alta |
| HU-06 | Notificaciones a beneficiarios | Media-alta |
| HU-07 | Consulta geográfica de cobertura | Media |
| HU-08 | Generación y exportación de reportes | Alta |
| HU-09 | Importación de información histórica | Alta |
| HU-10 | Acceso seguro y gestión de permisos | Alta |
| HU-11 | Registro con conectividad limitada | Alta |

## 5. Matriz de trazabilidad

La siguiente matriz relaciona las historias de usuario con los requisitos funcionales que describen su comportamiento esperado.

| Historia | Requisitos funcionales |
|---|---|
| HU-01 | RF-01, RF-03, RF-13 |
| HU-02 | RF-02, RF-05 |
| HU-03 | RF-04, RF-13 |
| HU-04 | RF-05, RF-12, RF-13 |
| HU-05 | RF-06, RF-13 |
| HU-06 | RF-07 |
| HU-07 | RF-08 |
| HU-08 | RF-09 |
| HU-09 | RF-10 |
| HU-10 | RF-11, RF-12 |
| HU-11 | RF-14 |

## 6. Consideraciones generales

Las historias de usuario deberán validarse con los responsables del proyecto antes de comenzar su implementación.

En particular, es necesario:

- Definir los campos obligatorios del registro.
- Establecer el procedimiento para resolver duplicados entre comités.
- Confirmar la periodicidad de revalidación.
- Determinar los canales de notificación y sus proveedores.
- Definir los formatos de importación y exportación.
- Establecer la matriz de roles y permisos.
- Determinar qué operaciones funcionarán sin conexión y cómo se sincronizarán.

Los criterios de aceptación constituyen condiciones que deberán comprobarse mediante pruebas; no representan funcionalidades ya verificadas.

## 7. Referencias relacionadas

- [Actores del sistema](./01-actores.md)
- [Requisitos funcionales](./03-requisitos-funcionales.md)
- [Atributos de calidad](./04-atributos-de-calidad.md)
- [Drivers arquitectónicos](./06-drivers-arquitectonicos.md)
- [Requisitos no funcionales](./07-requisitos-no-funcionales.md)
- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
