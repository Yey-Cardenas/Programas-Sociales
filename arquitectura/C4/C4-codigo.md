
# C4 — Diagrama de Código

**Proyecto:** Sistema de Gestión de Programas Sociales de Huamanga  
**Modelo:** C4 — Nivel 4: Código  
**Propósito:** Representar las clases conceptuales y sus relaciones.

## Diagrama UML de clases

```mermaid
classDiagram
    direction TB

    namespace Dominio {
        class Beneficiario {
            +int Id
            +string DNI
            +string Nombres
            +string Apellidos
            +bool Activo
            +DateTime FechaRegistro
        }

        class Comite {
            +int Id
            +string Nombre
            +string Ubicacion
        }

        class ProgramaSocial {
            +int Id
            +string Nombre
            +string Descripcion
        }

        class Auditoria {
            +int Id
            +string Accion
            +DateTime Fecha
            +string Usuario
        }
    }

    namespace Aplicacion {
        class BeneficiarioController {
            +Index()
            +Create()
            +Edit()
            +Details()
        }

        class BeneficiarioService {
            +Registrar()
            +Actualizar()
            +Inactivar()
        }

        class ValidadorDuplicadosService {
            +ValidarDNI()
            +BuscarDuplicados()
        }

        class RevalidacionService {
            +RevalidarBeneficiario()
        }

        class NotificacionService {
            +EnviarNotificacion()
        }

        class ReporteService {
            +GenerarReporte()
            +ExportarExcel()
            +ExportarPDF()
        }
    }

    namespace Infraestructura {
        class BeneficiarioRepository {
            +ObtenerPorId()
            +ObtenerPorDNI()
            +Agregar()
            +Actualizar()
        }

        class UnitOfWork {
            +GuardarCambios()
        }

        class ApplicationDbContext {
            +DbSet Beneficiarios
            +DbSet Comites
            +DbSet ProgramasSociales
            +DbSet Auditorias
        }
    }

    BeneficiarioController --> BeneficiarioService : utiliza
    BeneficiarioService --> ValidadorDuplicadosService : valida DNI
    BeneficiarioService --> BeneficiarioRepository : consulta datos
    BeneficiarioService --> UnitOfWork : confirma cambios

    RevalidacionService --> BeneficiarioRepository : consulta padrón
    ReporteService --> BeneficiarioRepository : obtiene información
    NotificacionService ..> Beneficiario : destinatario

    BeneficiarioRepository --> ApplicationDbContext : accede a datos
    UnitOfWork --> ApplicationDbContext : guarda cambios

    Comite "1" --> "0..*" Beneficiario : agrupa
    ProgramaSocial "1" --> "0..*" Beneficiario : registra
    Beneficiario "1" --> "0..*" Auditoria : historial

    classDef domain fill:#D6EAF8,stroke:#2874A6,color:#154360
    classDef application fill:#D5F5E3,stroke:#239B56,color:#145A32
    classDef infrastructure fill:#FCF3CF,stroke:#B7950B,color:#7D6608
```

## Descripción

El modelo divide las clases en tres grupos conceptuales:

- **Dominio:** contiene las entidades principales del negocio, como beneficiarios, comités, programas sociales y auditoría.
- **Aplicación:** representa los controladores y servicios que coordinan las operaciones del sistema.
- **Infraestructura:** representa el acceso a datos mediante repositorios, Unit of Work y Entity Framework Core.

Las relaciones muestran cómo los controladores utilizan servicios, los servicios acceden a los repositorios y los elementos de persistencia interactúan con el contexto de base de datos.

## Consideración importante

Los nombres, atributos, métodos y relaciones de este diagrama son ilustrativos. Antes de presentar el nivel C4 como una representación exacta del código, deben verificarse los archivos `.cs` del repositorio y ajustarse las clases a la implementación real.
