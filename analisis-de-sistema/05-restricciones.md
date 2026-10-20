# 05. Restricciones del Sistema

## 1. Restricciones tecnológicas

El desarrollo del Sistema de Gestión de Programas Sociales de Huamanga se plantea con las siguientes tecnologías:

- **Lenguaje de programación:** C#.
- **Framework web:** ASP.NET Core 9 con el patrón MVC.
- **Interfaz de usuario:** vistas Razor (`.cshtml`), HTML5, CSS3 y Bootstrap.
- **Gestión de datos:** Entity Framework Core 9.
- **Base de datos:** Microsoft SQL Server.
- **Organización arquitectónica:** monolito modular.

Las tecnologías indicadas deben mantenerse uniformes en los documentos de análisis y arquitectura, salvo que exista una decisión formal de cambio.

## 2. Restricciones de arquitectura

- El sistema se organizará como un monolito modular, separando las responsabilidades funcionales en módulos.
- Se utilizará MVC para organizar los controladores, las vistas y el acceso a los datos.
- Se contempla el uso de Repository y Unit of Work para organizar las operaciones de persistencia, según las necesidades del proyecto.
- La inyección de dependencias permitirá gestionar los servicios y sus dependencias.
- La solución no se documentará como una arquitectura basada en React, Node.js o PostgreSQL, porque estas tecnologías no corresponden al stack definido en el README principal.

## 3. Restricciones de datos

- Microsoft SQL Server será el gestor de base de datos previsto.
- Entity Framework Core 9 será el ORM utilizado para el acceso a los datos.
- La información de los beneficiarios deberá protegerse frente al acceso no autorizado.
- Las operaciones importantes deberán contemplar mecanismos de validación y auditoría.
- El esquema definitivo de la base de datos deberá validarse durante el diseño e implementación.

## 4. Restricciones operativas

- El sistema deberá considerar las condiciones de conectividad limitada de algunas zonas de Huamanga.
- Se contempla una PWA con capacidades de funcionamiento sin conexión y sincronización posterior, cuya implementación deberá validarse.
- La importación de información desde Excel deberá contemplar validaciones antes de incorporar los registros al sistema.
- Las funcionalidades de mensajería por SMS o WhatsApp dependerán de la disponibilidad y configuración de servicios externos.

## 5. Restricciones de seguridad

- El acceso a las funcionalidades deberá controlarse de acuerdo con los roles definidos.
- Los datos personales de los beneficiarios deberán manejarse con medidas de seguridad apropiadas.
- Las entradas del usuario deberán validarse antes de procesarse.
- Las credenciales y cadenas de conexión no deberán publicarse en el repositorio.
- La auditoría deberá permitir registrar las operaciones relevantes, según las reglas que se definan para el sistema.

## 6. Consideraciones de alcance

Este documento describe las restricciones tecnológicas y operativas previstas para el proyecto académico. Las funcionalidades que todavía no se hayan desarrollado, como el trabajo sin conexión, la sincronización o la integración con servicios de mensajería, se consideran objetivos de diseño y no funcionalidades implementadas.
