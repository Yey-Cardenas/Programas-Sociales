
# C3 — Diagrama de Componentes

**Proyecto:** Sistema de Gestión de Programas Sociales de Huamanga  
**Modelo:** C4 — Nivel 3: Componentes  
**Propósito:** Detallar las responsabilidades internas de la aplicación.

## Diagrama de componentes

```mermaid
flowchart TB
    USER(["Dirigente de Comité / Personal de la Subgerencia"])

    subgraph PRESENTACION["01 · CAPA DE PRESENTACIÓN"]
        direction LR
        VISTAS["Vistas Razor<br/>Formularios y consultas"]
        CBEN["Controlador de<br/>beneficiarios"]
        CREP["Controlador de<br/>reportes"]
        CUSR["Controlador de<br/>usuarios y acceso"]
    end

    subgraph NEGOCIO["02 · CAPA DE LÓGICA DE NEGOCIO"]
        direction TB

        subgraph GESTION["Gestión de beneficiarios"]
            direction LR
            SBEN["Servicio de<br/>beneficiarios"]
            SDUP["Validación de<br/>duplicados"]
            SPAD["Gestión del<br/>padrón"]
            SREV["Revalidación<br/>periódica"]
        end

        subgraph PROCESOS["Procesos complementarios"]
            direction LR
            SSTA["Importación y<br/>staging"]
            SNOT["Servicio de<br/>notificaciones"]
            SREP["Servicio de<br/>reportes"]
            SUSR["Gestión de<br/>usuarios y roles"]
        end
    end

    subgraph PERSISTENCIA["03 · CAPA DE ACCESO A DATOS"]
        direction LR
        REPOS["Repositorios"]
        UOW["Unit of Work"]
        CTX["Entity Framework Core<br/>DbContext"]
    end

    DB[("SQL Server")]
    XLS[("Archivos históricos<br/>Excel")]
    MSG["Pasarela externa<br/>SMS / WhatsApp"]

    USER --> VISTAS
    VISTAS --> CBEN
    VISTAS --> CREP
    VISTAS --> CUSR

    CBEN --> SBEN
    CREP --> SREP
    CUSR --> SUSR

    SBEN --> SDUP
    SBEN --> SPAD
    SPAD --> SREV
    SSTA --> SBEN
    SREP --> SPAD
    SNOT --> SBEN

    SBEN --> REPOS
    SDUP --> REPOS
    SPAD --> REPOS
    SREV --> REPOS
    SSTA --> REPOS
    SREP --> REPOS
    SUSR --> REPOS

    REPOS --> UOW
    UOW --> CTX
    CTX --> DB

    XLS -.-> SSTA
    SNOT -.-> MSG

    %% Estilos
    classDef actor fill:#EAF2F8,stroke:#2874A6,color:#154360,stroke-width:1.5px
    classDef presentation fill:#D6EAF8,stroke:#2874A6,color:#154360,stroke-width:1.5px
    classDef business fill:#D5F5E3,stroke:#239B56,color:#145A32,stroke-width:1.5px
    classDef data fill:#FCF3CF,stroke:#B7950B,color:#7D6608,stroke-width:1.5px
    classDef external fill:#F4ECF7,stroke:#884EA0,color:#512E5F,stroke-width:1.5px

    class USER actor
    class VISTAS,CBEN,CREP,CUSR presentation
    class SBEN,SDUP,SPAD,SREV,SSTA,SNOT,SREP,SUSR business
    class REPOS,UOW,CTX,DB data
    class XLS,MSG external

    style PRESENTACION fill:#F5FAFE,stroke:#2874A6,stroke-width:1.5px
    style NEGOCIO fill:#F4FBF6,stroke:#239B56,stroke-width:1.5px
    style PERSISTENCIA fill:#FFFCF2,stroke:#B7950B,stroke-width:1.5px

    linkStyle default stroke:#566573,stroke-width:1.3px,color:#273746
```

## Descripción

La capa de presentación recibe las solicitudes de los usuarios. La capa de negocio agrupa las operaciones de beneficiarios, validación de duplicados, padrón, revalidación, importación, notificaciones, reportes y administración de usuarios. La capa de acceso a datos organiza la persistencia mediante repositorios, Unit of Work y Entity Framework Core.

La separación facilita el mantenimiento y permite identificar las responsabilidades de cada parte del sistema.

**Nota:** los componentes son una organización conceptual basada en los requisitos y la arquitectura documentada. Se deben contrastar con el código fuente para confirmar sus nombres y relaciones reales.
