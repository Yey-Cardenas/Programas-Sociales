
# Modelo C4 del Sistema de Gestión de Programas Sociales

## 1. Descripción

El modelo C4 permite representar la arquitectura del Sistema de Gestión de Programas Sociales de Huamanga mediante cuatro niveles de detalle: contexto, contenedores, componentes y código.

El sistema tiene como finalidad apoyar la gestión de beneficiarios de los programas sociales, como Vaso de Leche y Comedores Populares, facilitando el registro, la validación de información, el seguimiento y la generación de reportes.

## 2. Objetivo

Documentar la estructura arquitectónica del sistema, identificando a los usuarios, los principales contenedores, los componentes internos y las relaciones entre las clases propuestas.

## 3. Diagramas del modelo C4

### Nivel 1: Contexto del sistema

Archivo: [C1-contexto.md](C1-contexto.md)

Presenta el sistema en su entorno, los actores que interactúan con él y los servicios externos relacionados.

### Nivel 2: Contenedores

Archivo: [C2-contenedores.md](C2-contenedores.md)

Describe las principales partes técnicas del sistema, como la aplicación web, el almacenamiento local, la lógica de negocio y la base de datos.

### Nivel 3: Componentes

Archivo: [C3-componentes.md](C3-componentes.md)

Detalla los componentes funcionales internos y sus relaciones dentro de la aplicación.

### Nivel 4: Código

Archivo: [C4-codigo.md](C4-codigo.md)

Presenta un modelo conceptual de las clases, servicios y elementos de acceso a datos que pueden formar parte de la solución.

## 4. Tecnologías y decisiones arquitectónicas

De acuerdo con la documentación de arquitectura del proyecto, se consideran las siguientes tecnologías y decisiones:

- ASP.NET Core MVC 9 para la aplicación web.
- C# como lenguaje de programación.
- Razor y archivos `.cshtml` para las vistas.
- Entity Framework Core para el acceso a datos.
- SQL Server como sistema de gestión de base de datos.
- Arquitectura de monolito modular con separación lógica por responsabilidades.
- Patrón Repository y Unit of Work para organizar el acceso a datos.
- Funcionalidad PWA para apoyar el trabajo sin conexión y la sincronización posterior.
- Integración prevista con servicios externos de mensajería SMS o WhatsApp.

## 5. Consideraciones

Los diagramas documentan la arquitectura propuesta para el sistema. Los nombres de clases, servicios y componentes del nivel de código deben verificarse con la implementación real antes de considerarlos definitivos.

Los diagramas Mermaid se pueden visualizar en GitHub y en editores compatibles con esta sintaxis.
