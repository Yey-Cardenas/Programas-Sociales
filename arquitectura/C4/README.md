# Modelo C4 — Sistema de Gestión de Programas Sociales

## 1. Objetivo

El modelo C4 permite representar la arquitectura del Sistema de Gestión de Programas Sociales de Huamanga mediante diferentes niveles de detalle. Su finalidad es facilitar la comprensión del sistema, sus usuarios, sus contenedores, sus componentes y la organización conceptual del código.

## 2. Tecnologías de referencia

Los diagramas toman como referencia el stack definido en el README principal:

- C# y ASP.NET Core 9.
- MVC con vistas Razor (`.cshtml`).
- HTML5, CSS3 y Bootstrap.
- Entity Framework Core 9.
- Microsoft SQL Server.
- Arquitectura de monolito modular.

## 3. Diagramas incluidos

| Archivo | Nivel | Propósito |
|---|---|---|
| `C1-contexto.md` | C1 — Contexto | Muestra los usuarios, el sistema y sus relaciones externas. |
| `C2-contenedores.md` | C2 — Contenedores | Presenta las principales unidades ejecutables y los almacenes de datos. |
| `C3-componentes.md` | C3 — Componentes | Describe los componentes internos de la aplicación y sus relaciones. |
| `C4-codigo.md` | C4 — Código | Presenta una vista conceptual de clases y responsabilidades. |

## 4. Criterios de uniformidad

- Todos los diagramas deben representar el mismo sistema.
- Se debe mantener ASP.NET Core MVC como tecnología de aplicación web.
- La base de datos prevista debe identificarse como Microsoft SQL Server.
- Entity Framework Core 9 debe aparecer como tecnología de acceso a datos.
- La arquitectura debe representarse como monolito modular.
- Los actores y las integraciones externas deben conservar nombres coherentes entre niveles.
- Los elementos todavía no implementados deben entenderse como parte de la propuesta arquitectónica.

## 5. Alcance

Los diagramas representan el diseño arquitectónico documentado. Los nombres de clases, métodos y componentes del nivel C4 de código son conceptuales mientras no se contrasten con los archivos reales de implementación.
