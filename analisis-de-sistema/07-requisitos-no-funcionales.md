
# 07. Requisitos no funcionales

## RNF-01. Disponibilidad y continuidad

El sistema deberá procurar una disponibilidad mensual mínima del 99%. El registro sin conexión y la sincronización posterior se evaluarán mediante pruebas específicas cuando se implementen.

## RNF-02. Rendimiento

La validación de duplicados por DNI deberá responder en menos de 0.5 segundos bajo las condiciones de carga definidas para las pruebas, considerando un padrón de al menos 15,000 beneficiarios.

## RNF-03. Usabilidad

El formulario de registro deberá tener como máximo cinco campos obligatorios, siempre que se conserve la información necesaria para validar el registro.

## RNF-04. Seguridad y privacidad

El sistema deberá restringir el acceso a los datos personales según los roles autorizados y proteger las comunicaciones mediante cifrado. Las credenciales no deberán publicarse en el repositorio.

## RNF-05. Compatibilidad

La aplicación deberá definir y validar una matriz de navegadores y dispositivos móviles compatibles. La compatibilidad con Android 8 o superior será un objetivo que deberá comprobarse con la solución tecnológica seleccionada.

## RNF-06. Auditabilidad

Las modificaciones relevantes deberán registrar el usuario responsable, la fecha, la acción realizada y el resultado. El motivo del cambio se registrará cuando corresponda.

## RNF-07. Capacidad

El sistema deberá gestionar al menos 15,000 beneficiarios sin superar los umbrales de rendimiento establecidos para las pruebas.

## RNF-08. Mantenibilidad

La arquitectura deberá permitir incorporar nuevos programas sociales sin rediseñar la totalidad del sistema, manteniendo la separación de responsabilidades entre módulos.

## RNF-09. Respaldo y recuperación

Se propone generar copias de seguridad diarias de la base de datos. Deberán definirse la conservación de las copias y los procedimientos de restauración, y comprobarse su funcionamiento mediante pruebas.
