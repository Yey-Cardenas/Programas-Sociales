# Modelo C4 — Sistema de Gestión de Programas Sociales de Huamanga

## 1. Objetivo

Este directorio contiene los diagramas del modelo C4 propuesto para el Sistema de Gestión de Programas Sociales de Huamanga.

El modelo permite representar el sistema desde diferentes niveles de detalle: su contexto, los contenedores tecnológicos, los componentes internos y una vista conceptual de código.

Los diagramas forman parte de la documentación académica de la arquitectura. Representan una propuesta que deberá validarse y actualizarse durante el desarrollo del sistema.

## 2. Tecnologías y estilo arquitectónico

La arquitectura documentada utiliza las siguientes tecnologías:

- **Lenguaje:** C#.
- **Plataforma:** .NET 9.
- **Framework web:** ASP.NET Core MVC 9.
- **Interfaz:** Razor (`.cshtml`), HTML5, CSS3 y Bootstrap.
- **Acceso a datos:** Entity Framework Core 9.
- **Base de datos:** Microsoft SQL Server.
- **Estilo arquitectónico:** monolito modular.
- **Modelo de interfaz:** MVC.

La solución se organiza en módulos funcionales dentro de una misma aplicación. No se plantea una arquitectura de microservicios independientes.

El uso de Repository y Unit of Work no se considera obligatorio; se evaluará durante la implementación si aporta valor al diseño.

## 3. Diagramas del modelo C4

| Nivel | Archivo | Propósito |
|---|---|---|
| C1 — Contexto | [C1-contexto.md](C1-contexto.md) | Muestra el sistema, sus usuarios y las entidades externas con las que podría interactuar. |
| C2 — Contenedores | [C2-contenedores.md](C2-contenedores.md) | Representa el cliente web, la aplicación, el acceso a datos y las integraciones previstas. |
| C3 — Componentes | [C3-componentes.md](C3-componentes.md) | Organiza los módulos funcionales, los servicios compartidos y el acceso a datos. |
| C4 — Vista de código | [C4-codigo.md](C4-codigo.md) | Presenta un modelo UML conceptual de clases y sus relaciones. |

## 4. Criterios de diseño

Los diagramas siguen los siguientes criterios:

1. **Uniformidad tecnológica:** todos los diagramas deben reflejar ASP.NET Core MVC 9, Entity Framework Core 9 y Microsoft SQL Server.
2. **Monolito modular:** los módulos funcionales pertenecen a una misma aplicación y se separan por responsabilidades.
3. **Separación de responsabilidades:** la presentación, la lógica de aplicación y el acceso a datos se representan de forma diferenciada.
4. **Trazabilidad:** los módulos deben corresponder con los requisitos funcionales, las historias de usuario y los atributos de calidad documentados.
5. **Claridad visual:** cada diagrama debe mostrar las relaciones principales sin sobrecargarlo con detalles innecesarios.
6. **Coherencia:** los componentes del nivel C3 deben corresponder con los contenedores descritos en C2.
7. **Carácter conceptual:** las clases, servicios e integraciones propuestos no se consideran implementados hasta que se verifiquen en el código fuente.

## 5. Consideraciones sobre los contenedores y las integraciones

### 5.1. Cliente web y capacidades PWA

La interfaz se plantea para utilizarse desde un navegador web. Las capacidades PWA y el almacenamiento local se consideran parte de la experiencia del cliente, no una aplicación frontend independiente.

El funcionamiento sin conexión y la sincronización posterior requieren diseño, implementación y pruebas específicas. Deben contemplarse la protección de los datos locales, los errores de sincronización y la resolución de conflictos.

### 5.2. Base de datos

Microsoft SQL Server es el motor de base de datos seleccionado. Entity Framework Core 9 se propone para el acceso a los datos.

No se presupone que SQL Server esté alojado en Azure ni se establece un proveedor de alojamiento específico.

### 5.3. Notificaciones

El envío de avisos por SMS o WhatsApp se considera una posible integración externa. El proveedor, sus condiciones y la forma de integración deberán definirse antes de su implementación.

### 5.4. Datos históricos e integraciones institucionales

Los archivos históricos, como hojas de cálculo y registros existentes, pueden utilizarse como fuentes para la importación y validación de datos.

RENIEC y SISFOH no se consideran dependencias confirmadas de la primera versión del sistema.

## 6. Relación con la documentación del proyecto

Los diagramas deben revisarse junto con los siguientes documentos:

- [Enfoque arquitectónico](../enfoque-arquitectonico.md).
- [Estilo arquitectónico](../estilo-arquitectonico.md).
- [Actores del sistema](../../analisis-de-sistema/01-actores.md).
- [Historias de usuario](../../analisis-de-sistema/02-historias-de-usuario.md).
- [Requisitos funcionales](../../analisis-de-sistema/03-requisitos-funcionales.md).
- [Atributos de calidad](../../analisis-de-sistema/04-atributos-de-calidad.md).
- [Restricciones](../../analisis-de-sistema/05-restricciones.md).
- [Drivers arquitectónicos](../../analisis-de-sistema/06-drivers-arquitectonicos.md).
- [Requisitos no funcionales](../../analisis-de-sistema/07-requisitos-no-funcionales.md).

## 7. Estado de la documentación

Los diagramas representan la arquitectura propuesta para fines de análisis y documentación académica. Deben actualizarse cuando se tomen decisiones técnicas definitivas o se implemente el sistema.

Antes de considerar completa la documentación, se debe verificar que los diagramas sean legibles, que sus relaciones correspondan con los requisitos y que todas las referencias a tecnologías coincidan con el `README.md` principal del repositorio.
