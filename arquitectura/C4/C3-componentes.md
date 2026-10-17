
# C4 — Nivel 3: Diagrama de Componentes

## Sistema de Gestión de Programas Sociales de Huamanga

Este diagrama representa los principales componentes de la arquitectura propuesta, sus responsabilidades y sus relaciones. El sistema se organiza mediante ASP.NET Core MVC, módulos funcionales, servicios transversales y persistencia de datos.

```mermaid
flowchart TB

    %% USUARIOS
    U["Usuarios del sistema<br/>Dirigente de comité y personal municipal"]

    %% PRESENTACION
    subgraph PRESENTACION["1. CAPA DE PRESENTACIÓN"]
        direction LR
        V["Vistas Razor<br/>HTML / Bootstrap"]
        C["Controladores MVC<br/>ASP.NET Core 10"]
        V --> C
    end

    %% MODULOS FUNCIONALES
    subgraph MODULOS["2. MÓDULOS FUNCIONALES"]
        direction TB

        subgraph FILA1["Gestión y control de beneficiarios"]
            direction LR
            M1["01 · Registro y padrón<br/>Beneficiarios e inscripciones"]
            M2["02 · Detección de duplicados<br/>Validación de registros"]
            M3["03 · Revalidación periódica<br/>Control semestral"]
        end

        subgraph FILA2["Operaciones y servicios al usuario"]
            direction LR
            M4["04 · Notificaciones<br/>Avisos y estado de envíos"]
            M5["05 · Cobertura y reportes<br/>Consultas y exportaciones"]
            M6["06 · Staging e importación<br/>Validación de archivos"]
        end

        M7["07 · Autenticación y autorización<br/>Usuarios, roles y permisos"]
    end

    %% SERVICIOS TRANSVERSALES
    subgraph SERVICIOS["3. SERVICIOS TRANSVERSALES"]
        direction LR
        AUD["Auditoría<br/>Trazabilidad de operaciones"]
        OFF["Sincronización offline<br/>Validación y sincronización"]
        DAT["Acceso a datos<br/>Entity Framework Core 10"]
    end

    %% SISTEMAS EXTERNOS
    subgraph EXTERNOS["4. PERSISTENCIA E INTEGRACIONES"]
        direction LR
        DB[("Azure SQL Database")]
        GW["Pasarela SMS / WhatsApp"]
        EX["Archivos históricos<br/>Excel y padrones en papel"]
    end

    %% FLUJO PRINCIPAL
    U --> V
    C --> M1
    C --> M2
    C --> M3
    C --> M4
    C --> M5
    C --> M6
    C --> M7

    %% RELACIONES FUNCIONALES
    M1 --> M2
    M1 --> M3
    M1 --> M5
    M6 --> M1
    M6 --> M2
    M3 --> M4

    %% SERVICIOS COMPARTIDOS
    M1 --> DAT
    M2 --> DAT
    M3 --> DAT
    M4 --> DAT
    M5 --> DAT
    M6 --> DAT
    M7 --> DAT

    M1 -.-> AUD
    M2 -.-> AUD
    M3 -.-> AUD
    M6 -.-> AUD

    OFF <--> M1
    OFF <--> M6

    %% INTEGRACIONES EXTERNAS
    DAT --> DB
    M4 --> GW
    EX --> M6

    %% ESTILOS
    classDef usuario fill:#F3F4F6,stroke:#6B7280,color:#111827,stroke-width:1.5px
    classDef presentacion fill:#DBEAFE,stroke:#3B82F6,color:#1E3A8A,stroke-width:1.5px
    classDef modulo fill:#D1FAE5,stroke:#10B981,color:#064E3B,stroke-width:1.5px
    classDef transversal fill:#FEF3C7,stroke:#D97706,color:#78350F,stroke-width:1.5px
    classDef externo fill:#EDE9FE,stroke:#8B5CF6,color:#4C1D95,stroke-width:1.5px

    class U usuario
    class V,C presentacion
    class M1,M2,M3,M4,M5,M6,M7 modulo
    class AUD,OFF,DAT transversal
    class DB,GW,EX externo

    %% ESTILO DE CONEXIONES
    linkStyle default stroke:#64748B,stroke-width:1.3px
```

## Responsabilidad de los módulos

| N.º | Módulo | Responsabilidad |
|---|---|---|
| 01 | Registro y padrón | Gestionar beneficiarios e inscripciones. |
| 02 | Detección de duplicados | Identificar posibles duplicados según las reglas del programa y comité. |
| 03 | Revalidación periódica | Controlar el proceso de revalidación semestral. |
| 04 | Notificaciones | Coordinar avisos y registrar el estado de los envíos. |
| 05 | Cobertura y reportes | Consultar cobertura y generar reportes autorizados. |
| 06 | Staging e importación | Recibir y validar archivos antes de incorporar los datos. |
| 07 | Autenticación y autorización | Gestionar el acceso mediante usuarios, roles y permisos. |

**Nota arquitectónica:** el diagrama representa el diseño propuesto. Las integraciones, la sincronización offline y los servicios deberán implementarse y validarse durante el desarrollo.
