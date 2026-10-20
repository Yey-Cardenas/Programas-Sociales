
# Modelo C4 del Sistema de Gestión de Programas Sociales

**Proyecto:** Sistema de Gestión de Programas Sociales – Huamanga  
**Estado:** Propuesta de arquitectura; no implica que el sistema esté implementado o desplegado.

## 1. Stack tecnológico

- **Backend:** C# con ASP.NET Core 9 MVC.
- **Frontend:** Vistas Razor (`.cshtml`), HTML5, CSS3 y Bootstrap.
- **PWA:** Capacidades de funcionamiento limitado sin conexión y sincronización posterior, sujetas a implementación y pruebas.
- **ORM:** Entity Framework Core 9.
- **Base de datos:** Microsoft SQL Server.
- **Estilo arquitectónico:** Monolito modular.

## 2. Diagramas de arquitectura

1. [Nivel 1 — Contexto del sistema](C4-Nivel-1-Contexto.md)
2. [Nivel 2 — Contenedores](C4-Nivel-2-Contenedores.md)
3. [Nivel 3 — Componentes](C4-Nivel-3-Componentes.md)
4. [Nivel 4 — Código (vista complementaria)](C4-Nivel-4-Codigo.md)
5. [Vista de despliegue físico propuesta](C4-Despliegue-Fisico.md)

## 3. Descripción de los niveles

- **Nivel 1 — Contexto:** identifica los usuarios, el sistema principal y las dependencias externas.
- **Nivel 2 — Contenedores:** muestra la aplicación web, las capacidades PWA, la base de datos y sus comunicaciones.
- **Nivel 3 — Componentes:** describe las responsabilidades internas de la aplicación y sus relaciones.
- **Nivel 4 — Código:** presenta clases y secuencias ilustrativas para el registro de inscripciones.
- **Despliegue físico:** propone una distribución de los elementos en un entorno de ejecución todavía por definir.

## 4. Criterios de interpretación

- El dirigente administra únicamente los registros de su comité asignado.
- El personal municipal autorizado supervisa los registros y atiende las alertas que requieren revisión.
- Los beneficiarios son destinatarios de notificaciones; no se consideran usuarios que inician sesión en el alcance actual.
- La aplicación web utiliza MVC y Razor dentro de un monolito modular. La PWA forma parte de la misma solución y no constituye un frontend independiente.
- Los padrones históricos se someten a validación antes de incorporarse a los registros centrales.
- RENIEC y SISFOH se consideran posibles integraciones futuras, no dependencias confirmadas de la primera versión.
- Las operaciones realizadas sin conexión no se consideran confirmadas hasta que el servidor procese correctamente la sincronización.

## 5. Estado de la propuesta

Los diagramas representan decisiones de diseño. Las clases, integraciones, funcionalidades offline y recursos de infraestructura descritos deben verificarse durante la implementación.

La plataforma concreta de alojamiento y la configuración de red se definirán antes del despliegue. Microsoft SQL Server es el motor de base de datos elegido; no se presupone que esté alojado en Azure.

Los diagramas se mantienen en Markdown con Mermaid para facilitar su lectura, edición y visualización en GitHub.
