# Actores del sistema

## 1. Objetivo

Este documento identifica a los actores que interactúan con el Sistema de Gestión de Programas Sociales de Huamanga y describe sus responsabilidades dentro de la solución propuesta.

Los actores coinciden con los representados en el [diagrama de contexto C1](../arquitectura/C4/C1-contexto.md): **Dirigente de Comité**, **Personal de la Subgerencia** y **Beneficiario**.

La identificación de los actores permite definir las funciones que tendrá cada tipo de usuario, establecer los permisos necesarios y relacionar sus necesidades con las historias de usuario y los requisitos funcionales.

## 2. Actores del sistema

### 2.1. Dirigente de Comité

**Descripción:** Persona encargada de registrar y actualizar la información de los beneficiarios de su comité, de acuerdo con las funciones que tenga asignadas.

**Responsabilidades:**
- Registrar nuevos beneficiarios.
- Actualizar los datos que tenga autorización para modificar.
- Consultar la información de su comité según sus permisos.
- Revisar las alertas de posibles duplicados que se generen durante el registro.
- Identificar los registros pendientes de sincronización, si esta capacidad está disponible.

**Necesidades principales:** Contar con una interfaz sencilla que facilite el registro y la consulta de información, incluso en escenarios de conectividad limitada si se implementan las capacidades correspondientes.

**Historias de usuario relacionadas:** HU-01, HU-02 y HU-11.

### 2.2. Personal de la Subgerencia

**Descripción:** Personal autorizado de la Subgerencia responsable de supervisar, consultar y administrar la información de los beneficiarios y de los programas sociales.

**Responsabilidades:**
- Supervisar y consultar los registros de beneficiarios.
- Atender las alertas de posibles duplicados y registrar el resultado de la revisión.
- Gestionar las revalidaciones periódicas.
- Desactivar registros cuando exista una justificación y autorización.
- Consultar la cobertura geográfica y generar reportes.
- Revisar e importar información histórica después de validarla.
- Consultar los registros de auditoría cuando tenga los permisos correspondientes.
- Gestionar cuentas, roles y permisos, únicamente el personal designado para la administración del sistema.

**Necesidades principales:** Acceder a información confiable y actualizada para supervisar los registros y gestionar los programas sociales.

**Historias de usuario relacionadas:** HU-03, HU-04, HU-05, HU-07, HU-08, HU-09 y HU-10.

**Consideración:** La administración de cuentas y permisos se asigna como un rol específico dentro del Personal de la Subgerencia. Este rol no implica automáticamente autorización para consultar o modificar toda la información personal.

### 2.3. Beneficiario

**Descripción:** Persona inscrita o considerada para participar en un programa social cuya información es gestionada por el sistema.

**Interacción con el sistema:** El beneficiario no inicia sesión en el sistema. Recibe notificaciones relacionadas con eventos definidos, como la aprobación o revalidación de su registro, a través del servicio externo de mensajería cuando este se encuentre habilitado.

**Necesidades principales:**
- Recibir información pertinente sobre los procesos que le correspondan.
- Contar con un tratamiento adecuado de sus datos personales.
- Evitar recibir comunicaciones destinadas a otra persona.

**Historia de usuario relacionada:** HU-06.

## 3. Sistemas y recursos externos relacionados

Además de los actores, el diagrama de contexto contempla los siguientes recursos externos. No se consideran actores, sino fuentes o servicios con los que el sistema se relaciona.

### 3.1. Servicio externo de mensajería

**Descripción:** Servicio de SMS o WhatsApp que podría utilizarse para enviar notificaciones a los beneficiarios.

**Estado:** Integración pendiente de definición. No se ha establecido un proveedor concreto.

**Requisito relacionado:** RF-07.

### 3.2. Archivos históricos

**Descripción:** Hojas de cálculo y registros en papel utilizados previamente para administrar la información de los beneficiarios.

**Estado:** Los formatos admitidos y las reglas de validación deberán definirse antes de implementar la importación.

**Requisito relacionado:** RF-10.

### 3.3. Servicios institucionales externos

RENIEC y SISFOH no forman parte de la primera versión documentada. Cualquier integración futura deberá evaluarse según su disponibilidad, los permisos necesarios y la protección de los datos personales.

## 4. Matriz de actores y responsabilidades

| Actor | Registrar beneficiarios | Revisar duplicados | Revalidar registros | Generar reportes | Administrar accesos |
|---|---|---|---|---|---|
| Dirigente de Comité | Sí, en su comité | Revisar alertas propias | No | Según permisos | No |
| Personal de la Subgerencia | Según permisos | Sí | Sí | Sí | Solo el personal designado |
| Beneficiario | No | No | No | No | No |

La matriz representa una propuesta inicial de responsabilidades. Los permisos definitivos deberán acordarse con los responsables del proyecto y aplicarse mediante los mecanismos de autorización del sistema.

## 5. Relación entre actores e historias de usuario

| Actor | Historias de usuario relacionadas |
|---|---|
| Dirigente de Comité | HU-01, HU-02, HU-11 |
| Personal de la Subgerencia | HU-03,