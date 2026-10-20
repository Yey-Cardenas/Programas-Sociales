# Actores del sistema

## 1. Objetivo

Este documento identifica a los actores que interactúan con el Sistema de Gestión de Programas Sociales de Huamanga y describe sus responsabilidades dentro de la solución propuesta.

La identificación de los actores permite definir las funciones que tendrá cada tipo de usuario, establecer los permisos necesarios y relacionar sus necesidades con las historias de usuario y los requisitos funcionales.

## 2. Actores principales

### 2.1. Responsable de comité

**Descripción:** Persona encargada de realizar actividades de registro y consulta de información de los beneficiarios de acuerdo con las funciones que tenga asignadas.

**Responsabilidades:**
- Registrar nuevos beneficiarios.
- Consultar la información disponible según sus permisos.
- Actualizar los datos que tenga autorización para modificar.
- Revisar las alertas de posibles duplicados que se generen durante el registro.
- Identificar los registros que requieren revisión o sincronización, si estas capacidades están disponibles.

**Necesidades principales:** Contar con una interfaz sencilla que facilite el registro y la consulta de información, incluso en escenarios de conectividad limitada si se implementan las capacidades correspondientes.

**Historias de usuario relacionadas:** HU-01, HU-02 y HU-11.

### 2.2. Personal municipal autorizado

**Descripción:** Personal responsable de realizar tareas administrativas y de supervisión relacionadas con los beneficiarios y los programas sociales.

**Responsabilidades:**
- Consultar y revisar los registros de beneficiarios.
- Atender alertas de posibles duplicados.
- Registrar los resultados de las revisiones que le correspondan.
- Gestionar las revalidaciones periódicas.
- Desactivar registros cuando exista una justificación y autorización.
- Generar reportes para apoyar las actividades administrativas.
- Revisar información histórica y participar en su validación.
- Consultar los registros de auditoría cuando tenga los permisos correspondientes.

**Necesidades principales:** Acceder a información confiable y actualizada para facilitar la revisión de registros y la gestión de los programas sociales.

**Historias de usuario relacionadas:** HU-03, HU-04, HU-05, HU-08 y HU-09.

### 2.3. Administrador del sistema

**Descripción:** Usuario responsable de administrar los accesos y las configuraciones del sistema que le correspondan.

**Responsabilidades:**
- Gestionar las cuentas de usuario según las políticas definidas.
- Asignar o modificar roles y permisos autorizados.
- Revisar la configuración general de acceso.
- Apoyar la revisión de incidentes relacionados con los accesos.
- Supervisar las operaciones administrativas para las que tenga autorización.

**Necesidades principales:** Disponer de mecanismos para gestionar los accesos y mantener un control adecuado sobre las operaciones administrativas.

**Historias de usuario relacionadas:** HU-10.

**Consideración:** Los permisos definitivos del administrador deberán definirse para evitar que el acceso administrativo implique automáticamente autorización para consultar o modificar toda la información personal.

## 3. Actor relacionado con las notificaciones

### 3.1. Beneficiario

**Descripción:** Persona inscrita o considerada para participar en un programa social cuya información es gestionada por el sistema.

**Interacción con el sistema:** En la propuesta inicial, el beneficiario no necesita iniciar sesión. Puede recibir notificaciones relacionadas con eventos definidos, como la aprobación o revalidación de su registro, cuando exista un canal de comunicación habilitado.

**Necesidades principales:**
- Recibir información pertinente sobre los procesos que le correspondan.
- Contar con un tratamiento adecuado de sus datos personales.
- Evitar recibir comunicaciones destinadas a otra persona.

**Historia de usuario relacionada:** HU-06.

**Consideración:** El envío de notificaciones mediante SMS o WhatsApp requiere definir y validar el proveedor, los costos, el tratamiento de los datos y las condiciones de uso del canal.

## 4. Sistemas y recursos externos relacionados

Además de los actores humanos, la propuesta contempla recursos e integraciones externas que podrían intervenir en determinados procesos.

### 4.1. Servicio externo de notificaciones

**Descripción:** Servicio que podría utilizarse para enviar mensajes a los beneficiarios mediante un canal como SMS o WhatsApp.

**Responsabilidad prevista:** Procesar las solicitudes de envío y, cuando el proveedor lo permita, devolver información sobre el resultado de la operación.

**Estado:** Integración pendiente de definición. No se ha establecido un proveedor concreto.

**Requisito relacionado:** RF-07.

### 4.2. Archivos de información histórica

**Descripción:** Archivos utilizados previamente para administrar información de beneficiarios, por ejemplo, hojas de cálculo.

**Responsabilidad prevista:** Proporcionar información que pueda revisarse, validarse e importarse mediante un procedimiento controlado.

**Estado:** Los formatos admitidos y las reglas de validación deberán definirse antes de implementar la importación.

**Requisito relacionado:** RF-10.

### 4.3. Servicios institucionales externos

**Descripción:** En el futuro podría evaluarse la integración con servicios institucionales que permitan verificar información, siempre que exista autorización y viabilidad técnica.

**Estado:** No forman parte de las integraciones confirmadas para la propuesta inicial. No se considera establecida una conexión con RENIEC o SISFOH.

**Consideración:** Cualquier integración futura deberá evaluarse según su disponibilidad, los permisos necesarios, las condiciones institucionales y la protección de los datos personales.

## 5. Matriz de actores y responsabilidades

| Actor | Registrar beneficiarios | Revisar duplicados | Revalidar registros | Generar reportes | Administrar accesos |
|---|---|---|---|---|---|
| Responsable de comité | Sí, según permisos | Revisar alertas propias | Según autorización | Según permisos | No |
| Personal municipal autorizado | Según permisos | Sí, según autorización | Sí | Sí | No, salvo permiso específico |
| Administrador del sistema | Según permisos asignados | Según autorización | Según autorización | Según permisos | Sí |
| Beneficiario | No directamente en la propuesta inicial | No | No | No | No |

La matriz representa una propuesta inicial de responsabilidades. Los permisos definitivos deberán acordarse con los responsables del proyecto y aplicarse mediante los mecanismos de autorización del sistema.

## 6. Relación entre actores e historias de usuario

| Actor | Historias de usuario relacionadas |
|---|---|
| Responsable de comité | HU-01, HU-02, HU-11 |
| Personal municipal autorizado | HU-03, HU-04, HU-05, HU-08, HU-09 |
| Administrador del sistema | HU-10 |
| Beneficiario | HU-06 |

Algunas historias pueden involucrar más de un actor. La asignación anterior identifica la relación principal y no excluye la participación de otros usuarios autorizados.

## 7. Consideraciones de seguridad y privacidad

El acceso a la información deberá limitarse según las responsabilidades de cada actor.

Se deberán considerar las siguientes medidas:

- Exigir autenticación para las funciones restringidas.
- Aplicar permisos específicos para registrar, modificar, desactivar y consultar información.
- Restringir el acceso a los registros de auditoría.
- Evitar mostrar datos personales innecesarios en las alertas y reportes.
- Proteger las comunicaciones y las credenciales.
- Definir las condiciones de acceso a la información almacenada localmente si se implementa el funcionamiento sin conexión.

## 8. Referencias relacionadas

- [Historias de usuario](./02-historias-de-usuario.md)
- [Requisitos funcionales](./03-requisitos-funcionales.md)
- [Atributos de calidad](./04-atributos-de-calidad.md)
- [Restricciones](./05-restricciones.md)
- [Drivers arquitectónicos](./06-drivers-arquitectonicos.md)
- [Requisitos no funcionales](./07-requisitos-no-funcionales.md)
- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
