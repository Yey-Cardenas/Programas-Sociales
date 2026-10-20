# 05. Restricciones del sistema

## 1. Restricciones tecnológicas

| ID | Restricción |
|---|---|
| RC01 | El sistema se diseñará como un monolito modular. |
| RC02 | El backend utilizará C# con ASP.NET Core 9 y el patrón MVC. |
| RC03 | La interfaz utilizará vistas Razor (.cshtml), HTML5, CSS3 y Bootstrap. |
| RC04 | El acceso a datos utilizará Entity Framework Core 9. |
| RC05 | El motor de base de datos previsto será Microsoft SQL Server. |

Las tecnologías indicadas deben mantenerse uniformes en los documentos de análisis y arquitectura, salvo que exista una decisión formal de cambio.

## 2. Restricciones de arquitectura

- La aplicación se organizará en módulos con responsabilidades delimitadas.
- MVC organizará los controladores, las vistas y la interacción con los servicios.
- Repository y Unit of Work se evaluarán según las necesidades de persistencia y no se presentarán como implementados sin verificar el código.
- La inyección de dependencias se utilizará para administrar las dependencias de la aplicación.
- No se introducirá React, Node.js ni PostgreSQL como parte del stack definido sin una decisión formal de arquitectura.

## 3. Restricciones de datos

- RC06: La información se almacenará en Microsoft SQL Server.
- RC07: El acceso a datos se realizará mediante Entity Framework Core 9.
- Los registros de beneficiarios deberán protegerse frente al acceso no autorizado.
- Las operaciones relevantes deberán incluir validaciones y mecanismos de auditoría.
- El modelo de datos definitivo deberá validarse durante el diseño y la implementación.

## 4. Restricciones operativas

- RC08: El diseño deberá considerar zonas con conectividad limitada.
- La PWA y la sincronización posterior se consideran objetivos de diseño sujetos a implementación y pruebas.
- La importación desde Excel deberá validar los datos antes de incorporarlos a los registros centrales.
- La mensajería por SMS o WhatsApp dependerá de un proveedor externo, su disponibilidad y su configuración.
- Las decisiones de alojamiento, cantidad de servidores y configuración de red quedan pendientes de definición.

## 5. Restricciones de seguridad

- El acceso a las funcionalidades deberá controlarse según los roles autorizados.
- Los datos personales deberán manejarse con medidas de seguridad adecuadas.
- Las entradas recibidas deberán validarse antes de procesarse.
- Las credenciales y cadenas de conexión no deberán publicarse en el repositorio.
- La auditoría deberá registrar las operaciones relevantes, incluyendo usuario, fecha, acción y resultado cuando corresponda.
- Las copias de seguridad deberán protegerse frente al acceso no autorizado.

## 6. Alcance y estado

Este documento describe las restricciones previstas para el proyecto académico. No implica que todas las funcionalidades hayan sido implementadas.

El funcionamiento sin conexión, la sincronización, las integraciones de mensajería y cualquier integración externa deberán verificarse mediante pruebas antes de considerarse funcionalidades operativas.
