# Atributos de calidad

## 1. Objetivo

Este documento identifica los atributos de calidad relevantes para el Sistema de Gestión de Programas Sociales de Huamanga. Estos atributos permiten orientar las decisiones arquitectónicas y establecer criterios para evaluar el comportamiento esperado del sistema.

Los valores indicados son objetivos propuestos. Su cumplimiento deberá comprobarse mediante pruebas durante el desarrollo y la validación de la solución.

## 2. Atributos de calidad identificados

### AC-01. Disponibilidad

**Descripción:** El sistema deberá estar disponible para los usuarios autorizados durante las operaciones habituales de gestión de los programas sociales.

**Escenario de calidad:** Cuando el personal municipal necesite registrar o consultar información, el sistema deberá encontrarse operativo de acuerdo con las condiciones del entorno de despliegue.

**Métrica propuesta:** Disponibilidad mensual mínima del 99 %, considerando los periodos de mantenimiento previamente definidos.

**Decisión arquitectónica relacionada:** Definir un entorno de despliegue compatible con ASP.NET Core 9 y procedimientos de recuperación ante incidentes.

**Prioridad:** Alta.

**Validación:** Medir los periodos de disponibilidad e interrupción una vez definido el entorno de despliegue.

### AC-02. Rendimiento

**Descripción:** Las operaciones principales del sistema deberán responder en un tiempo adecuado para facilitar el trabajo del personal municipal.

**Escenario de calidad:** Cuando un usuario registre un beneficiario, el sistema deberá comprobar si existe un posible registro duplicado y presentar el resultado oportunamente.

**Métrica propuesta:** Tiempo de respuesta inferior a 0,5 segundos para la validación de duplicados, bajo condiciones de prueba definidas.

**Decisión arquitectónica relacionada:** Optimizar las consultas realizadas mediante Entity Framework Core 9 y Microsoft SQL Server. Evaluar índices y restricciones de integridad según las reglas del negocio.

**Prioridad:** Alta.

**Validación:** Ejecutar pruebas de rendimiento con datos representativos, incluyendo un padrón de referencia de hasta 15 000 beneficiarios. Documentar el entorno, la concurrencia y los tiempos obtenidos.

### AC-03. Facilidad de uso

**Descripción:** La interfaz deberá permitir que el personal municipal realice las operaciones habituales de manera comprensible y ordenada.

**Escenario de calidad:** Cuando un usuario registre o actualice información, deberá identificar fácilmente los campos obligatorios, los errores y las acciones disponibles.

**Métrica propuesta:** Procurar que el formulario de registro tenga como máximo cinco campos obligatorios, siempre que las reglas del negocio lo permitan.

**Decisión arquitectónica relacionada:** Utilizar ASP.NET Core MVC 9, Razor, HTML5, CSS3 y Bootstrap para organizar formularios y vistas consistentes.

**Prioridad:** Media-alta.

**Validación:** Revisar los formularios y realizar pruebas de uso con usuarios representativos.

### AC-04. Seguridad y privacidad

**Descripción:** El sistema deberá proteger la información personal de los beneficiarios y restringir el acceso a las funciones según las responsabilidades de cada usuario.

**Escenario de calidad:** Cuando una persona intente acceder a una función restringida, el sistema deberá comprobar su autenticación y los permisos correspondientes antes de permitir la operación.

**Criterios propuestos:**

- Autenticación para las funciones que requieran acceso restringido.
- Autorización basada en roles y permisos.
- Protección de las comunicaciones mediante HTTPS en los entornos desplegados.
- Almacenamiento seguro de credenciales.
- Protección de la información personal y limitación de accesos.
- Ausencia de contraseñas, claves y otros secretos en el repositorio.

**Decisión arquitectónica relacionada:** Definir los mecanismos de autenticación, autorización, validación y protección de datos de acuerdo con los requisitos del sistema.

**Prioridad:** Alta.

**Validación:** Revisar los permisos y realizar pruebas de acceso autorizado y no autorizado.

### AC-05. Compatibilidad y funcionamiento en distintos dispositivos

**Descripción:** El sistema deberá ofrecer una experiencia de uso adecuada en los navegadores y dispositivos definidos para el proyecto.

**Escenario de calidad:** Cuando el personal municipal acceda desde un equipo de escritorio o un dispositivo móvil compatible, deberá poder utilizar las funciones disponibles sin problemas de visualización que impidan su operación.

**Métrica propuesta:** Establecer una matriz de compatibilidad que incluya los navegadores y dispositivos que se decida soportar. Considerar Android 8 o superior como objetivo inicial sujeto a validación.

**Decisión arquitectónica relacionada:** Diseñar una interfaz adaptable y evaluar las capacidades PWA previstas para el sistema.

**Prioridad:** Media-alta.

**Validación:** Ejecutar pruebas de navegación, visualización y formularios en los dispositivos y navegadores seleccionados.

### AC-06. Trazabilidad y auditoría

**Descripción:** El sistema deberá permitir revisar las operaciones relevantes efectuadas sobre la información de los beneficiarios.

**Escenario de calidad:** Cuando un usuario autorizado realice una modificación que deba auditarse, el sistema deberá conservar información suficiente para identificar la operación y su responsable.

**Criterio propuesto:** Registrar, según corresponda, el usuario, la fecha y hora, el tipo de operación y una referencia al registro afectado.

**Decisión arquitectónica relacionada:** Definir un mecanismo de auditoría integrado con los módulos funcionales y con acceso restringido.

**Prioridad:** Alta.

**Validación:** Ejecutar operaciones de prueba y comprobar la integridad y accesibilidad de los registros de auditoría.

### AC-07. Capacidad de crecimiento

**Descripción:** El sistema deberá poder gestionar el crecimiento del padrón de beneficiarios sin requerir una modificación completa de su arquitectura.

**Escenario de calidad:** Cuando aumente la cantidad de beneficiarios registrados, las operaciones principales deberán continuar cumpliendo los objetivos de rendimiento establecidos para el proyecto.

**Métrica propuesta:** Considerar un padrón de referencia de hasta 15 000 beneficiarios para las pruebas iniciales.

**Decisión arquitectónica relacionada:** Organizar las funcionalidades mediante un monolito modular y optimizar el acceso a los datos almacenados en Microsoft SQL Server.

**Prioridad:** Alta.

**Validación:** Ejecutar pruebas con diferentes volúmenes de datos y revisar el comportamiento de las consultas principales.

### AC-08. Mantenibilidad y evolución

**Descripción:** La organización del sistema deberá facilitar la corrección de errores, el mantenimiento y la incorporación de nuevas funcionalidades.

**Escenario de calidad:** Cuando se requiera modificar un módulo o incorporar una funcionalidad relacionada con un programa social, los cambios deberán realizarse procurando no afectar innecesariamente a los demás módulos.

**Criterio propuesto:** Mantener responsabilidades diferenciadas, dependencias controladas y una estructura de código comprensible.

**Decisión arquitectónica relacionada:** Utilizar un monolito modular con ASP.NET Core MVC 9 y separar las responsabilidades de presentación, lógica de negocio y acceso a datos.

**Prioridad:** Alta.

**Validación:** Revisar la estructura del proyecto y comprobar que los cambios no afecten las funciones existentes mediante pruebas pertinentes.

### AC-09. Respaldo y recuperación de información

**Descripción:** El sistema deberá contar con mecanismos para respaldar la información y recuperarla ante incidentes.

**Escenario de calidad:** Cuando se produzca una pérdida de datos o un fallo que afecte a la base de datos, deberá existir un procedimiento documentado para recuperar la información desde una copia de seguridad válida.

**Métrica propuesta:** Establecer una frecuencia inicial de respaldo diario y definir los periodos de conservación y los objetivos de recuperación según las necesidades institucionales.

**Decisión arquitectónica relacionada:** Definir los procedimientos de copia de seguridad y restauración de Microsoft SQL Server en el entorno de despliegue seleccionado.

**Prioridad:** Alta.

**Validación:** Verificar la generación de respaldos y realizar pruebas periódicas de restauración en un entorno controlado.

## 3. Priorización de los atributos de calidad

| Código | Atributo de calidad | Prioridad |
|---|---|---|
| AC-01 | Disponibilidad | Alta |
| AC-02 | Rendimiento | Alta |
| AC-03 | Facilidad de uso | Media-alta |
| AC-04 | Seguridad y privacidad | Alta |
| AC-05 | Compatibilidad y funcionamiento en distintos dispositivos | Media-alta |
| AC-06 | Trazabilidad y auditoría | Alta |
| AC-07 | Capacidad de crecimiento | Alta |
| AC-08 | Mantenibilidad y evolución | Alta |
| AC-09 | Respaldo y recuperación de información | Alta |

## 4. Relación con las decisiones arquitectónicas

Los atributos de calidad influyen en la organización y las decisiones de diseño de la siguiente manera:

| Atributos | Decisión o consideración arquitectónica |
|---|---|
| AC-01 | Definir el entorno de despliegue y los procedimientos de recuperación. |
| AC-02 | Optimizar consultas y validar el rendimiento de Entity Framework Core 9 y Microsoft SQL Server. |
| AC-03 | Diseñar formularios claros y consistentes con Razor y Bootstrap. |
| AC-04 | Definir autenticación, autorización y protección de datos personales. |
| AC-05 | Validar la interfaz en navegadores y dispositivos seleccionados. |
| AC-06 | Definir eventos auditables y proteger los registros. |
| AC-07 | Organizar módulos y validar el comportamiento con volúmenes representativos. |
| AC-08 | Separar responsabilidades dentro del monolito modular. |
| AC-09 | Definir copias de seguridad y procedimientos de restauración. |

## 5. Consideraciones de validación

Los atributos de calidad deberán evaluarse durante el desarrollo y las pruebas. En particular:

- Los tiempos de respuesta deberán medirse en condiciones reproducibles.
- La disponibilidad dependerá del entorno de despliegue y de su operación.
- La compatibilidad deberá confirmarse con pruebas en los dispositivos seleccionados.
- Las capacidades PWA y el funcionamiento sin conexión deberán probarse si se implementan.
- La seguridad deberá evaluarse mediante revisiones de configuración y pruebas de acceso.
- La auditoría deberá comprobarse mediante operaciones de prueba.
- La recuperación deberá verificarse mediante restauraciones reales en un entorno controlado.

Los valores establecidos son objetivos de diseño y no representan resultados de pruebas ya realizadas.

## 6. Referencias relacionadas

- [Historias de usuario](./02-historias-de-usuario.md)
- [Requisitos funcionales](./03-requisitos-funcionales.md)
- [Restricciones](./05-restricciones.md)
- [Drivers arquitectónicos](./06-drivers-arquitectonicos.md)
- [Requisitos no funcionales](./07-requisitos-no-funcionales.md)
- [Enfoque arquitectónico](../arquitectura/enfoque-arquitectonico.md)
- [Estilo arquitectónico](../arquitectura/estilo-arquitectonico.md)
- [Modelo C4](../arquitectura/C4/README.md)
