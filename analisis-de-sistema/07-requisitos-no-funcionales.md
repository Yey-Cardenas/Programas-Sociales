# Requisitos no funcionales

## 1. Objetivo

Este documento describe los requisitos no funcionales del Sistema de Gestión de Programas Sociales de Huamanga. Estos requisitos establecen criterios de calidad relacionados con el rendimiento, la seguridad, la disponibilidad, la compatibilidad, la capacidad de crecimiento y el mantenimiento del sistema.

Los valores cuantitativos indicados representan objetivos propuestos para orientar el diseño y las pruebas. Su cumplimiento deberá comprobarse durante el desarrollo y la validación del sistema.

## 2. Requisitos no funcionales

### RNF-01. Disponibilidad

**Descripción:** El sistema deberá procurar mantenerse disponible para los usuarios autorizados durante las operaciones habituales de gestión de los programas sociales.

**Criterio de aceptación:** Se establece como objetivo una disponibilidad mensual mínima del 99 %, considerando las condiciones del entorno de despliegue y los periodos de mantenimiento previamente definidos.

**Justificación:** La disponibilidad permite que el personal autorizado consulte y gestione la información cuando lo necesite.

**Prioridad:** Alta.

**Trazabilidad:** AC-01 y DA-01.

**Verificación:** Registrar los periodos de interrupción y calcular la disponibilidad durante un periodo de medición definido. El funcionamiento sin conexión, si se implementa, deberá evaluarse por separado.

### RNF-02. Rendimiento

**Descripción:** El sistema deberá responder oportunamente a las operaciones de consulta y validación de beneficiarios.

**Criterio de aceptación:** La validación de posibles duplicados deberá tener como objetivo un tiempo de respuesta inferior a 0,5 segundos, bajo condiciones de prueba previamente establecidas y con un padrón de referencia de hasta 15 000 beneficiarios.

**Justificación:** Una validación eficiente reduce las demoras durante el registro y permite detectar posibles inconsistencias a tiempo.

**Prioridad:** Alta.

**Trazabilidad:** AC-02, AC-07, DA-02 y HU-02.

**Verificación:** Realizar pruebas de rendimiento con datos representativos y documentar el entorno, el volumen de datos, la concurrencia y los tiempos obtenidos.

### RNF-03. Facilidad de uso

**Descripción:** Las pantallas de registro y consulta deberán ser comprensibles para el personal municipal que utilice el sistema.

**Criterio de aceptación:** El formulario de registro deberá procurar que los datos obligatorios se limiten a un máximo de cinco campos, siempre que las reglas del negocio y las necesidades de validación lo permitan. Los campos adicionales deberán justificarse.

**Justificación:** Una interfaz sencilla facilita el registro de información y disminuye los errores durante el trabajo cotidiano.

**Prioridad:** Media-alta.

**Trazabilidad:** AC-03.

**Verificación:** Revisar los formularios y realizar pruebas de uso con usuarios representativos.

### RNF-04. Seguridad y protección de datos

**Descripción:** El sistema deberá proteger la información de los beneficiarios y permitir el acceso únicamente a los usuarios autorizados según sus responsabilidades.

**Criterios de aceptación:**

- Exigir autenticación para acceder a las funciones restringidas.
- Aplicar autorización por roles y comprobar los permisos en las operaciones protegidas.
- Proteger las comunicaciones mediante HTTPS en los entornos desplegados.
- No almacenar contraseñas en texto plano.
- No incluir contraseñas, claves, cadenas de conexión sensibles ni otros secretos en el repositorio.
- Validar las entradas y controlar los errores para reducir riesgos de acceso o modificación indebida.
- Limitar el acceso a los datos personales según las funciones autorizadas.

**Justificación:** El sistema administrará información personal que requiere medidas adecuadas de confidencialidad e integridad.

**Prioridad:** Alta.

**Trazabilidad:** AC-04, DA-03, HU-10 y RC-07.

**Verificación:** Revisar la configuración de seguridad y realizar pruebas de autenticación, autorización, validación de entradas y protección de información sensible.

### RNF-05. Compatibilidad

**Descripción:** El sistema deberá poder utilizarse desde navegadores web compatibles con la aplicación y desde dispositivos habituales del personal municipal.

**Criterio de aceptación:** Se definirá una matriz de compatibilidad que incluya los navegadores de escritorio y móviles que se decidan soportar. La compatibilidad con Android 8 o superior será un objetivo inicial sujeto a pruebas.

**Justificación:** Los usuarios pueden acceder al sistema desde equipos con diferentes características y versiones de software.

**Prioridad:** Media-alta.

**Trazabilidad:** AC-05 y RC-08.

**Verificación:** Ejecutar pruebas de navegación, formularios y visualización en los navegadores y dispositivos incluidos en la matriz.

### RNF-06. Trazabilidad y auditoría

**Descripción:** El sistema deberá permitir revisar las operaciones relevantes realizadas por los usuarios autorizados.

**Criterio de aceptación:** Los eventos definidos como auditables deberán registrar, según corresponda, el usuario responsable, la fecha y hora, el tipo de operación y una referencia al registro afectado. No deberán almacenarse contraseñas ni datos sensibles innecesarios en los registros de auditoría.

**Justificación:** La trazabilidad facilita la revisión de modificaciones y el análisis de posibles inconsistencias en la información.

**Prioridad:** Alta.

**Trazabilidad:** AC-06, DA-03 y HU-04.

**Verificación:** Ejecutar operaciones de prueba y comprobar que los eventos definidos se registren correctamente y que el acceso a los registros esté restringido.

### RNF-07. Capacidad de crecimiento

**Descripción:** El sistema deberá organizarse para permitir el crecimiento del padrón de beneficiarios sin requerir una modificación completa de su arquitectura.

**Criterio de aceptación:** La arquitectura y las pruebas deberán considerar un padrón de referencia de hasta 15 000 beneficiarios, manteniendo los objetivos de rendimiento establecidos para las operaciones prioritarias.

**Justificación:** El volumen de información puede aumentar a medida que se incorporen beneficiarios o nuevos programas sociales.

**Prioridad:** Alta.

**Trazabilidad:** AC-07, DA-02 y DA-04.

**Verificación:** Ejecutar pruebas con un conjunto de datos representativo y revisar el comportamiento de las consultas y operaciones principales.

### RNF-08. Mantenibilidad

**Descripción:** El sistema deberá contar con una organización que facilite la comprensión, corrección y ampliación de sus funcionalidades.

**Criterio de aceptación:** El código deberá mantener responsabilidades diferenciadas, nombres comprensibles, validaciones consistentes y una estructura modular. Las modificaciones deberán evitar dependencias innecesarias entre los módulos.

**Justificación:** Una estructura ordenada facilita el mantenimiento y reduce el riesgo de introducir errores al incorporar cambios.

**Prioridad:** Alta.

**Trazabilidad:** AC-08, DA-04 y DA-05.

**Verificación:** Revisar la estructura del proyecto, la separación de responsabilidades y los resultados de las pruebas asociadas a los cambios realizados.

### RNF-09. Copias de seguridad y recuperación

**Descripción:** La información almacenada deberá contar con mecanismos de respaldo y procedimientos para su recuperación ante incidentes.

**Criterio de aceptación:** Se propone realizar copias de seguridad diarias de la base de datos y establecer procedimientos documentados de restauración. La frecuencia definitiva y el periodo de conservación deberán ajustarse a las necesidades institucionales.

**Justificación:** Los respaldos permiten reducir el riesgo de pérdida de información por fallos técnicos, errores operativos u otros incidentes.

**Prioridad:** Alta.

**Trazabilidad:** AC-09 y DA-03.

**Verificación:** Comprobar la ejecución de las copias de seguridad y realizar pruebas periódicas de restauración en un entorno controlado.

## 3. Relación con la arquitectura propuesta

Los requisitos no funcionales influyen en las decisiones de arquitectura del sistema de la siguiente manera:

| Requisito | Consideración arquitectónica |
|---|---|
| RNF-01. Disponibilidad | Definir el entorno de despliegue, el mantenimiento y los mecanismos de recuperación. |
| RNF-02. Rendimiento | Optimizar las consultas y validar el comportamiento de Entity Framework Core 9 y Microsoft SQL Server. |
| RNF-03. Facilidad de uso | Organizar formularios claros utilizando ASP.NET Core MVC 9, Razor, HTML, CSS y Bootstrap. |
| RNF-04. Seguridad | Aplicar autenticación, autorización, validación y protección de datos. |
| RNF-05. Compatibilidad | Validar la interfaz en los navegadores y dispositivos definidos. |
| RNF-06. Trazabilidad | Definir los eventos auditables y proteger los registros correspondientes. |
| RNF-07. Capacidad de crecimiento | Organizar los módulos y comprobar el rendimiento con datos representativos. |
| RNF-08. Mantenibilidad | Mantener responsabilidades separadas dentro del monolito modular. |
| RNF-09. Copias de seguridad | Definir los procedimientos de respaldo y restauración de Microsoft SQL Server. |

## 4. Consideraciones de validación

Los requisitos descritos deberán validarse mediante pruebas y revisiones documentadas. En particular:

- Los objetivos de rendimiento requieren condiciones de prueba reproducibles.
- La disponibilidad deberá medirse en el entorno de despliegue que se defina.
- La compatibilidad debe confirmarse mediante una matriz de navegadores y dispositivos.
- Las capacidades sin conexión deberán probarse si se incorporan a la solución.
- La seguridad requiere revisar permisos, protección de datos y configuración del entorno.
- Los respaldos deberán probarse mediante restauraciones, no solamente mediante la comprobación de que se generaron archivos.
- Los valores propuestos podrán ajustarse cuando se definan las condiciones reales de uso.

## 5. Tecnologías consideradas

La propuesta arquitectónica mantiene las siguientes tecnologías:

- **Lenguaje:** C#.
- **Plataforma:** .NET 9.
- **Framework web:** ASP.NET Core MVC 9.
- **Interfaz:** Razor, HTML5, CSS3 y Bootstrap.
- **Acceso a datos:** Entity Framework Core 9.
- **Base de datos:** Microsoft SQL Server.

La selección de estas tecnologías corresponde a la propuesta documentada. La disponibilidad, el rendimiento, la seguridad y la compatibilidad deberán verificarse durante el desarrollo y las pruebas.

## 6. Referencias relacionadas

- [README del proyecto](../README.md)
- [Atributos de calidad](./04-atributos-de-calidad.md)
- [Restricciones](./05-restricciones.md)
- [Drivers arquitectónicos](./06-drivers-arquitectonicos.md)
- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Estilo arquitectónico](../arquitectura/estilo-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
