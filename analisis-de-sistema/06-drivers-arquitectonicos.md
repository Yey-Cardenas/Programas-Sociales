# 06. Drivers arquitectónicos

## 1. Drivers identificados

| ID | Driver arquitectónico | Origen | Influencia en la arquitectura |
|---|---|---|---|
| DA01 | El sistema debe permitir registrar información en zonas con conectividad limitada y sincronizarla cuando se recupere la conexión. | AC01; restricción operativa | Condiciona el diseño de la PWA, el almacenamiento local temporal y el proceso de sincronización. |
| DA02 | La validación de duplicados por DNI debe responder en menos de 0.5 segundos bajo una carga definida. | AC02; RF-02 | Influye en los índices de la base de datos, las consultas y las validaciones del servidor. |
| DA03 | El sistema debe proteger los datos personales y registrar las operaciones relevantes. | AC04; AC06; AC09 | Influye en la autenticación, la autorización por roles, la auditoría, las copias de seguridad y la protección de las comunicaciones. |
| DA04 | Deben incorporarse nuevos programas sociales sin rediseñar todo el sistema. | AC08 | Favorece módulos cohesionados, responsabilidades delimitadas y bajo acoplamiento. |
| DA05 | La solución debe mantener una complejidad operativa y un costo adecuados al proyecto. | Restricciones tecnológicas y operativas; AC07 | Justifica evaluar un monolito modular antes de considerar servicios distribuidos. La infraestructura concreta se definirá posteriormente. |
| DA06 | El sistema debe permitir integrar servicios externos de mensajería. | RF-07; restricción de mensajería | Favorece un módulo de notificaciones que aísle los errores del proveedor externo y permita registrar los resultados de envío. |
| DA07 | Los padrones históricos deben validarse antes de incorporarse a los registros centrales. | RF-11 | Requiere un proceso de importación, validación, detección de errores y confirmación de los datos. |
| DA08 | La información debe permitir consultar y visualizar la cobertura por zonas geográficas. | RF-08; RF-09 | Requiere modelar las zonas y sus relaciones con los registros. La solución geográfica debe ser compatible con Microsoft SQL Server, sin introducir PostgreSQL como motor de base de datos. |

## 2. Evaluación de otros elementos

| Elemento | ¿Es un driver arquitectónico? | Justificación |
|---|---|---|
| AC03 — Usabilidad | No necesariamente | Influye principalmente en el diseño y la interacción de la interfaz, aunque puede condicionar decisiones técnicas concretas. |
| AC06 — Auditabilidad | Sí | Requiere registrar quién realizó una operación, cuándo ocurrió y qué cambio se efectuó. |
| RF-10 — Exportación a Excel/PDF | No necesariamente | Puede resolverse como una funcionalidad del módulo de reportes, salvo que existan requisitos especiales de volumen o seguridad. |
| Control de versiones con Git y GitHub | No | Es una restricción del proceso de desarrollo y no una decisión estructural del sistema. |

## 3. Criterios de validación

- Los drivers deben mantener trazabilidad con los requisitos y las restricciones existentes.
- Las decisiones tecnológicas deben ser coherentes con C#, ASP.NET Core 9 MVC, Entity Framework Core 9 y Microsoft SQL Server.
- La PWA, la sincronización, la mensajería y las integraciones externas se consideran propuestas hasta que se implementen y prueben.
- No se debe afirmar que el sistema está desplegado o que cumple métricas de rendimiento sin evidencia de pruebas.
- La infraestructura de despliegue se definirá en una etapa posterior.
