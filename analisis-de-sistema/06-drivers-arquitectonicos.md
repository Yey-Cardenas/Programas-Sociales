# Drivers arquitectónicos

## 1. Objetivo

Los drivers arquitectónicos representan las necesidades, restricciones y atributos de calidad que influyen en las decisiones de arquitectura del Sistema de Gestión de Programas Sociales de Huamanga.

Estos drivers permiten justificar la elección de un monolito modular, la organización de los módulos funcionales, el uso de Microsoft SQL Server y las consideraciones necesarias para trabajar con conectividad limitada.

Las decisiones descritas en este documento corresponden a la propuesta arquitectónica del sistema. Su implementación y cumplimiento deberán verificarse durante las etapas de desarrollo y pruebas.

## 2. Identificación de los drivers arquitectónicos

### DA-01. Funcionamiento con conectividad limitada

**Descripción:** El sistema debe considerar las dificultades de conectividad que pueden presentarse durante el registro y la consulta de información de los beneficiarios.

**Importancia:** Alta.

**Decisión arquitectónica:** Considerar capacidades de aplicación web progresiva (PWA) y almacenamiento local temporal para permitir determinadas operaciones cuando no exista conexión. La sincronización deberá contemplar la validación de datos, los reintentos y la resolución de conflictos.

**Justificación:** La propuesta busca facilitar el trabajo del personal municipal en lugares donde la conexión a Internet puede ser inestable.

**Trazabilidad:** HU-11, AC-05 y RC-06.

**Validación pendiente:** Definir qué operaciones funcionarán sin conexión, cómo se protegerán los datos almacenados localmente y cómo se resolverán los conflictos durante la sincronización.

### DA-02. Validación eficiente de beneficiarios duplicados

**Descripción:** El sistema debe detectar posibles registros duplicados utilizando el documento de identidad del beneficiario, evitando la duplicación de información entre comités.

**Importancia:** Alta.

**Decisión arquitectónica:** Centralizar la validación de duplicados en la lógica de negocio y utilizar consultas eficientes sobre Microsoft SQL Server mediante Entity Framework Core 9. Se evaluará el uso de índices y restricciones de integridad de acuerdo con las reglas del negocio.

**Justificación:** La detección oportuna de duplicados contribuye a mantener un padrón de beneficiarios consistente y facilita la revisión por parte del personal autorizado.

**Trazabilidad:** HU-02, HU-04, AC-02 y AC-07.

**Criterio propuesto:** La validación deberá responder en menos de 0,5 segundos bajo una carga de prueba definida, considerando un padrón de referencia de hasta 15 000 beneficiarios.

**Validación pendiente:** Definir el entorno de pruebas, la concurrencia esperada y las condiciones de medición para comprobar el tiempo de respuesta.

### DA-03. Seguridad, privacidad y trazabilidad

**Descripción:** La información de los beneficiarios debe protegerse frente a accesos no autorizados y las operaciones relevantes deben poder revisarse posteriormente.

**Importancia:** Alta.

**Decisión arquitectónica:** Incorporar autenticación, autorización basada en roles, validación de permisos y registro de auditoría para las operaciones que lo requieran. Las comunicaciones deberán protegerse mediante HTTPS en los entornos desplegados.

**Justificación:** La información administrada por el sistema requiere controles de acceso y mecanismos que permitan identificar las acciones realizadas por los usuarios autorizados.

**Trazabilidad:** HU-04, HU-10, AC-04, AC-06 y RC-07.

**Validación pendiente:** Definir los permisos de cada rol, los eventos que se registrarán en auditoría, los plazos de conservación y las medidas de protección de los datos.

### DA-04. Facilidad para incorporar nuevos programas sociales

**Descripción:** La solución debe permitir incorporar o modificar programas sociales sin generar cambios innecesarios en toda la aplicación.

**Importancia:** Media-alta.

**Decisión arquitectónica:** Organizar el sistema como un monolito modular, separando responsabilidades funcionales y procurando mantener bajo acoplamiento entre los módulos.

**Justificación:** Esta organización permite mantener una solución sencilla de desplegar y administrar, sin impedir que las funcionalidades evolucionen de forma ordenada.

**Trazabilidad:** AC-08 y las historias de usuario relacionadas con la gestión de beneficiarios y programas sociales.

**Validación pendiente:** Definir las responsabilidades y dependencias de cada módulo, evitando duplicar reglas de negocio.

### DA-05. Control de costos y complejidad técnica

**Descripción:** La solución debe responder a las necesidades del proyecto sin incorporar complejidad tecnológica que no esté justificada por los requisitos.

**Importancia:** Alta.

**Decisión arquitectónica:** Utilizar una arquitectura de monolito modular con ASP.NET Core MVC 9, Entity Framework Core 9 y Microsoft SQL Server. No se propone inicialmente una arquitectura de microservicios.

**Justificación:** El monolito modular permite organizar las funcionalidades en una aplicación integrada, simplificando el despliegue y la administración mientras el tamaño y las necesidades del sistema lo permitan.

**Trazabilidad:** RC-01, RC-02, RC-04, RC-05 y AC-08.

**Validación pendiente:** Revisar la decisión si el volumen, la carga de trabajo o las necesidades de despliegue cambian significativamente.

### DA-06. Envío de notificaciones a beneficiarios

**Descripción:** El sistema contempla informar a los beneficiarios sobre determinados eventos, como la aprobación o revalidación de su registro.

**Importancia:** Media-alta.

**Decisión arquitectónica:** Separar la lógica de notificaciones de los módulos funcionales mediante un servicio dedicado. El proveedor y el canal de envío, como SMS o WhatsApp, deberán definirse según la viabilidad técnica, el costo y los requisitos institucionales.

**Justificación:** Esta separación facilita el mantenimiento de las notificaciones y evita que las reglas de negocio dependan directamente de un proveedor externo.

**Trazabilidad:** HU-06, AC-08 y RC-09.

**Validación pendiente:** Confirmar el proveedor, los costos, la disponibilidad, el consentimiento requerido y el tratamiento de los datos personales. La integración todavía no debe considerarse implementada.

### DA-07. Consolidación de información histórica

**Descripción:** La información histórica de los programas sociales puede encontrarse en hojas de cálculo u otros registros previos y necesita revisarse antes de incorporarse al sistema.

**Importancia:** Alta.

**Decisión arquitectónica:** Considerar un proceso de importación controlada que permita validar formatos, identificar datos incompletos, detectar posibles duplicados y revisar los errores antes de confirmar la incorporación de los registros.

**Justificación:** La validación previa reduce el riesgo de trasladar inconsistencias al padrón centralizado de beneficiarios.

**Trazabilidad:** HU-09, AC-06 y AC-08.

**Validación pendiente:** Definir los formatos de origen, las reglas de validación, el procedimiento de corrección y los mecanismos de respaldo antes de realizar una importación.

### DA-08. Consulta geográfica de cobertura

**Descripción:** El sistema contempla visualizar la distribución geográfica de los beneficiarios o la cobertura de los programas sociales.

**Importancia:** Media.

**Decisión arquitectónica:** Mantener la funcionalidad de consulta geográfica separada de las reglas centrales de gestión de beneficiarios. La solución cartográfica y los mecanismos de consulta deberán ser compatibles con la arquitectura y los datos disponibles.

**Justificación:** La separación facilita modificar la representación geográfica sin afectar las funciones principales del sistema.

**Trazabilidad:** HU-07, AC-08 y RC-05.

**Validación pendiente:** Definir la fuente de los datos geográficos, la herramienta de visualización, el nivel de precisión permitido y los controles de privacidad aplicables. La solución deberá mantener la compatibilidad con Microsoft SQL Server.

## 3. Relación entre los drivers y las decisiones arquitectónicas

| Driver | Decisión arquitectónica principal | Elementos relacionados |
|---|---|---|
| DA-01 | Considerar funcionamiento limitado sin conexión y sincronización controlada. | PWA, almacenamiento local y sincronización. |
| DA-02 | Centralizar la validación de duplicados y optimizar las consultas. | ASP.NET Core MVC 9, EF Core 9 y SQL Server. |
| DA-03 | Aplicar control de acceso, protección de comunicaciones y auditoría. | Autenticación, autorización y registro de operaciones. |
| DA-04 | Separar las responsabilidades funcionales en módulos. | Monolito modular. |
| DA-05 | Evitar complejidad distribuida no justificada. | ASP.NET Core MVC 9 y monolito modular. |
| DA-06 | Desacoplar las notificaciones del resto de la lógica de negocio. | Servicio de notificaciones e integración externa por definir. |
| DA-07 | Validar la información histórica antes de incorporarla. | Proceso de importación controlada. |
| DA-08 | Separar la consulta geográfica de las funciones centrales. | Solución cartográfica compatible con la arquitectura. |

## 4. Priorización de los drivers

Los drivers DA-01, DA-02, DA-03, DA-05 y DA-07 tienen prioridad alta porque se relacionan directamente con la continuidad operativa, la integridad de los datos, la protección de la información y la viabilidad de la solución.

Los drivers DA-04, DA-06 y DA-08 tienen prioridad media-alta o media, según el alcance que finalmente se establezca para la evolución funcional, las notificaciones y las consultas geográficas.

Esta priorización es una propuesta inicial y podrá ajustarse durante la validación de requisitos con los responsables del proyecto.

## 5. Consideraciones para la validación

Antes de considerar satisfechos estos drivers, será necesario:

- Verificar la coherencia de los diagramas de arquitectura con los requisitos del sistema.
- Definir las reglas para detectar y resolver registros duplicados.
- Establecer las condiciones de prueba para medir el rendimiento.
- Especificar las operaciones disponibles sin conexión y el tratamiento de conflictos.
- Definir los roles, permisos y eventos de auditoría.
- Confirmar las integraciones externas y sus proveedores.
- Validar los procedimientos de importación y recuperación de información.
- Definir la solución cartográfica y sus requisitos de privacidad.

Los drivers describen necesidades y decisiones propuestas; no constituyen evidencia de que las funcionalidades hayan sido desarrolladas o probadas.

## 6. Referencias relacionadas

- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Estilo arquitectónico](../arquitectura/estilo-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
- [Historias de usuario](./02-historias-de-usuario.md)
- [Atributos de calidad](./04-atributos-de-calidad.md)
- [Restricciones](./05-restricciones.md)
- [Requisitos no funcionales](./07-requisitos-no-funcionales.md)
