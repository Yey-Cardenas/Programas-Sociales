# 05. Restricciones del sistema

## 1. Objetivo

Las restricciones del sistema establecen las condiciones tecnológicas, arquitectónicas y operativas que deben considerarse durante el diseño y desarrollo del Sistema de Gestión de Programas Sociales de Huamanga.

Estas restricciones permiten mantener la coherencia tecnológica del proyecto y orientar las decisiones de arquitectura.

## 2. Restricciones tecnológicas y arquitectónicas

| ID | Restricción | Descripción |
|---|---|---|
| RC01 | Monolito modular | El sistema seguirá una arquitectura de monolito modular, organizando sus funcionalidades en módulos con responsabilidades definidas. |
| RC02 | ASP.NET Core 9 MVC | El desarrollo del sistema web utilizará ASP.NET Core 9 con el patrón Modelo-Vista-Controlador (MVC). |
| RC03 | Tecnologías de interfaz web | La interfaz utilizará Razor, HTML5, CSS3 y Bootstrap para la presentación y el diseño adaptable. |
| RC04 | Entity Framework Core 9 | El acceso y la persistencia de datos se realizarán mediante Entity Framework Core 9 como ORM. |
| RC05 | Microsoft SQL Server | La base de datos relacional del sistema utilizará Microsoft SQL Server para almacenar y administrar la información. |
| RC06 | Conectividad limitada | El sistema deberá considerar las condiciones de conectividad limitada de las zonas donde se utilizará. La estrategia de operación sin conexión y sincronización deberá definirse y validarse durante el diseño técnico. |

## 3. Consideraciones para el cumplimiento

- **RC01:** Los módulos deberán mantener responsabilidades diferenciadas y evitar dependencias innecesarias entre ellos.
- **RC02:** La aplicación deberá desarrollarse utilizando ASP.NET Core 9 MVC, manteniendo una estructura organizada de controladores, modelos y vistas.
- **RC03:** Las interfaces deberán ser comprensibles y adaptables a los dispositivos previstos para el uso del sistema.
- **RC04:** El acceso a los datos deberá centralizarse mediante Entity Framework Core 9, evitando duplicar innecesariamente la lógica de persistencia.
- **RC05:** La información deberá almacenarse en Microsoft SQL Server, definiendo adecuadamente las relaciones, restricciones e integridad de los datos.
- **RC06:** La conectividad limitada deberá considerarse en los procesos de registro y consulta. Si se requiere operar sin conexión, será necesario definir el almacenamiento local, la sincronización, la resolución de conflictos y las medidas de protección de la información.

## 4. Observaciones

Las tecnologías indicadas constituyen la base tecnológica definida para el proyecto. La implementación concreta de las funcionalidades sin conexión, la sincronización de datos y los mecanismos de seguridad deberá validarse durante el desarrollo.

Los identificadores RC01 a RC06 se utilizarán de forma única en la documentación para evitar duplicidades y mantener la trazabilidad de las restricciones del sistema.