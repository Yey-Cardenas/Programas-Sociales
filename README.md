
# Sistema de Gestión de Programas Sociales - Huamanga

![.NET](https://img.shields.io/badge/.NET-9.0-512BD4?style=flat-square&logo=dotnet)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-MVC-blue?style=flat-square)
![Base de datos](https://img.shields.io/badge/Base_de_datos-SQL_Server-red?style=flat-square)
![Arquitectura](https://img.shields.io/badge/Arquitectura-Monolito_Modular-success?style=flat-square)

Sistema web propuesto para gestionar los padrones de beneficiarios del Programa del Vaso de Leche y los Comedores Populares de la Municipalidad Provincial de Huamanga.

El sistema busca mejorar la administración de inscripciones, detectar posibles duplicidades, depurar padrones históricos y generar reportes de cobertura por zonas.

## Curso

Arquitectura de Software (IS-488) – Semestre 2026-II

## Integrantes

- Cárdenas García, Yery May
- Chipana Nuñez, Ever Neils

## Objetivos del sistema

- Gestionar los padrones de beneficiarios de los programas sociales.
- Detectar posibles inscripciones duplicadas y facilitar su revisión.
- Importar y depurar información procedente de archivos históricos.
- Generar reportes de beneficiarios activos y cobertura geográfica.
- Facilitar el trabajo de los dirigentes de comité y del personal municipal autorizado.
- Evaluar capacidades PWA para escenarios de conectividad limitada.

## Arquitectura y patrones

La solución se plantea como un **monolito modular** basado en el patrón **Modelo-Vista-Controlador (MVC)**. Esta organización permitirá agrupar las funcionalidades del sistema en módulos con responsabilidades diferenciadas y facilitar su mantenimiento.

Se propone utilizar la **inyección de dependencias** de ASP.NET Core para reducir el acoplamiento entre los componentes. Asimismo, se tomarán como referencia los principios **SOLID** para organizar las responsabilidades, definir abstracciones cuando sean necesarias y facilitar la evolución de las funcionalidades. Su aplicación se documentará como parte del diseño y deberá verificarse cuando exista una implementación del sistema.

El uso de los patrones Repository y Unit of Work se evaluará según las necesidades reales de acceso a datos, evitando incorporar complejidad que no aporte un beneficio claro.

Como parte de la propuesta de rendimiento, se evaluará el uso de `IMemoryCache` para almacenar temporalmente datos de referencia consultados con frecuencia que no sean sensibles. La estrategia deberá contemplar la expiración y la invalidación de las entradas cuando cambien los datos relacionados. Su efecto se comprobará mediante pruebas, sin asumir mejoras de rendimiento antes de medirlas.

El caché en memoria del servidor será independiente del almacenamiento local que pueda utilizar la aplicación web progresiva (PWA) en el navegador. Ambas capacidades están sujetas a implementación y validación.


## Stack tecnológico

- **Backend:** C# con ASP.NET Core 9 MVC.
- **Frontend:** Vistas Razor (`.cshtml`), HTML5, CSS3 y Bootstrap.
- **Base de datos:** Microsoft SQL Server.
- **ORM:** Entity Framework Core 9.
- **PWA:** capacidades offline-first sujetas a implementación y pruebas.
- **Acceso a datos:** proveedor de Entity Framework Core para SQL Server (`Microsoft.EntityFrameworkCore.SqlServer`).

Las versiones del SDK de .NET, el framework de destino y los paquetes NuGet deberán comprobarse para asegurar su compatibilidad. El stack descrito representa la decisión tecnológica del proyecto; no implica que la aplicación ya esté implementada.

## Despliegue propuesto

Se propone alojar la aplicación en un servidor compatible con ASP.NET Core 9 y utilizar Microsoft SQL Server como base de datos. La ubicación definitiva de ambos componentes —por ejemplo, un entorno local, un servidor institucional o un servicio de alojamiento compatible— deberá definirse antes del despliegue.

La configuración de producción deberá proteger las credenciales, limitar los permisos de la cuenta de aplicación, utilizar conexiones cifradas cuando corresponda y establecer procedimientos de respaldo y recuperación. Las cadenas de conexión y los secretos no deben almacenarse en el repositorio.

El despliegue y las pruebas de conexión, migraciones, permisos y recuperación quedan pendientes hasta contar con una implementación ejecutable y un entorno de prueba.

## Roles y autorización

- **Dirigente de comité:** administra la información correspondiente a su comité asignado.
- **Personal municipal autorizado:** realiza tareas de supervisión, reportes y revisión de alertas dentro de sus permisos.
- **Administrador designado:** gestiona las cuentas, los roles y las asignaciones autorizadas.
- **Beneficiario:** en el alcance actual, no requiere iniciar sesión en el sistema; puede ser destinatario de notificaciones cuando estas se implementen.

La autorización deberá validarse en el servidor. Las operaciones realizadas sin conexión no se considerarán confirmadas hasta que el servidor las valide y complete la sincronización.

## Documentación del repositorio

### Análisis del sistema

- [Actores](analisis-de-sistema/01-actores.md)
- [Historias de usuario](analisis-de-sistema/02-historias-de-usuario.md)
- [Requisitos funcionales](analisis-de-sistema/03-requisitos-funcionales.md)
- [Atributos de calidad](analisis-de-sistema/04-atributos-de-calidad.md)
- [Restricciones](analisis-de-sistema/05-restricciones.md)
- [Drivers arquitectónicos](analisis-de-sistema/06-drivers-arquitectonicos.md)
- [Requisitos no funcionales](analisis-de-sistema/07-requisitos-no-funcionales.md)
- [Plan de medición de atributos de calidad](analisis-de-sistema/08-medicion-de-calidad.md)

### Arquitectura

## Modelo C4

- [Nivel 1: Contexto](arquitectura/C4/C1-contexto.md)
- [Nivel 2: Contenedores](arquitectura/C4/C2-contenedores.md)
- [Nivel 3: Componentes](arquitectura/C4/C3-componentes.md)
- [Nivel 4: Código](arquitectura/C4/C4-codigo.md)
- [Documentación del modelo C4](arquitectura/C4/README.md)
- [Enfoque arquitectónico](arquitectura/enfoque-arquitectonico.md)
- [Estilo arquitectónico](arquitectura/estilo-arquitectonico.md)
- [Principios SOLID](arquitectura/principios-solid.md)

## Estado del proyecto

El repositorio contiene documentación de análisis y diseño arquitectónico. Las funcionalidades, integraciones, capacidades offline y decisiones de despliegue descritas como propuestas deberán implementarse y validarse mediante pruebas antes de considerarse operativas.
