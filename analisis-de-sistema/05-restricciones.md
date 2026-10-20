# Restricciones del sistema

## 1. Introducción

Este documento describe las restricciones técnicas y operativas consideradas para el desarrollo del Sistema de Gestión de Programas Sociales de Huamanga.

Las restricciones delimitan las tecnologías seleccionadas y las condiciones que deben tenerse en cuenta al diseñar e implementar la solución.

## 2. Restricciones técnicas

| Código | Restricción | Descripción |
|---|---|---|
| RC-01 | Estilo arquitectónico | La solución se organizará como un monolito modular, evitando dividir inicialmente el sistema en microservicios independientes. |
| RC-02 | Plataforma y framework web | El backend utilizará C# sobre .NET 9 y ASP.NET Core MVC 9. |
| RC-03 | Tecnologías de presentación | La interfaz web utilizará Razor (`.cshtml`), HTML5, CSS3 y Bootstrap. |
| RC-04 | Acceso a datos | Se utilizará Entity Framework Core 9 para gestionar el acceso a la base de datos. |
| RC-05 | Motor de base de datos | La persistencia se realizará en Microsoft SQL Server. No se establece como requisito el uso de Azure SQL Database. |
| RC-06 | Conectividad limitada | El diseño deberá considerar las limitaciones de conexión que pueden presentarse durante el trabajo de campo. |
| RC-07 | Seguridad de la información | El sistema deberá proteger los datos personales mediante controles de acceso, comunicaciones seguras y medidas apropiadas de protección de la información. |
| RC-08 | Compatibilidad de acceso | La interfaz deberá evaluarse en los navegadores y dispositivos definidos para el proyecto. |
| RC-09 | Integraciones externas | Las integraciones de mensajería dependerán de la selección y disponibilidad de un proveedor compatible. |

## 3. Restricciones de conectividad y funcionamiento sin conexión

Debido a que algunas actividades pueden realizarse en zonas con conectividad limitada, se contempla evaluar capacidades PWA y almacenamiento local para determinadas operaciones.

Antes de implementar esta capacidad, se deberá definir:

- Qué operaciones estarán disponibles sin conexión.
- Qué información podrá almacenarse temporalmente en el dispositivo.
- Cómo se protegerán los datos personales almacenados localmente.
- Cómo se sincronizarán los registros cuando se recupere la conectividad.
- Cómo se detectarán y resolverán los conflictos entre datos locales y datos del servidor.
- Cómo se informará al usuario sobre los registros pendientes, sincronizados o fallidos.

El funcionamiento sin conexión no se considera una capacidad implementada hasta que se desarrolle y se valide mediante pruebas.

## 4. Restricciones de base de datos

Microsoft SQL Server es el motor de base de datos seleccionado para el proyecto.

El acceso a los datos se realizará mediante Entity Framework Core 9 y su proveedor compatible con SQL Server.

La ubicación del servidor de base de datos, la configuración de conexiones, las copias de seguridad y el entorno de alojamiento deberán definirse durante la planificación técnica.

No se presupone el uso de Azure SQL Database ni de un servicio específico de alojamiento en la nube.

## 5. Restricciones de integración

Se contempla la posibilidad de enviar notificaciones a los beneficiarios mediante SMS o WhatsApp. Para ello, será necesario seleccionar un proveedor, evaluar sus condiciones y definir los mecanismos de integración.

Los archivos históricos disponibles, como hojas de cálculo, deberán validarse antes de incorporar sus registros al sistema.

RENIEC y SISFOH no se consideran dependencias confirmadas de la primera versión.

## 6. Restricciones de seguridad

La solución deberá contemplar:

1. Autenticación de los usuarios autorizados.
2. Autorización basada en los roles y permisos definidos.
3. Uso de comunicaciones seguras entre el cliente y el servidor.
4. Protección de credenciales y cadenas de conexión.
5. Control de acceso a los datos personales.
6. Registro de operaciones relevantes para auditoría.
7. Protección de la información almacenada localmente si se habilita el funcionamiento sin conexión.

Las medidas concretas deberán implementarse y comprobarse durante el desarrollo.

## 7. Relación con la arquitectura

Estas restricciones deben reflejarse en los documentos y diagramas del proyecto:

- `arquitectura/enfoque-arquitectonico.md`
- `arquitectura/estilo-arquitectonico.md`
- `arquitectura/C4/C1-contexto.md`
- `arquitectura/C4/C2-contenedores.md`
- `arquitectura/C4/C3-componentes.md`
- `arquitectura/C4/C4-codigo.md`

Las tecnologías y versiones indicadas deben mantenerse uniformes en todos estos archivos.

## 8. Consideraciones finales

Las restricciones establecen las condiciones de partida para diseñar el sistema. Los aspectos pendientes, como la integración de mensajería, el despliegue y la sincronización sin conexión, deberán definirse y validarse antes de considerarse implementados.
