
# C2 — Diagrama de Contenedores

**Proyecto:** Sistema de Gestión de Programas Sociales de Huamanga  
**Modelo:** C4 — Nivel 2: Contenedores  
**Propósito:** Mostrar las principales unidades tecnológicas y sus comunicaciones.

## Diagrama de contenedores

```mermaid
flowchart TB
    USER(["Usuario<br/>Dirigente / Personal municipal"])

    subgraph CLIENTE["01 · CAPA DE PRESENTACIÓN"]
        direction TB
        WEB["Aplicación web<br/>Vistas Razor / .cshtml"]
        PWA["Capacidades PWA<br/>Trabajo sin conexión"]
        LOCAL[("Almacenamiento local<br/>Operaciones pendientes")]
    end

    subgraph APLICACION["02 · APLICACIÓN — ASP.NET CORE MVC 9"]
        direction TB
        CTRL["Controladores MVC<br/>Gestión de solicitudes"]
        SERV["Servicios de aplicación<br/>Reglas de negocio"]
        REPO["Repository / Unit of Work<br/>Acceso organizado a datos"]
    end

    subgraph DATOS["03 · PERSISTENCIA"]
        direction TB
        EF["Entity Framework Core"]
        DB[("SQL Server<br/>Base de datos")]
    end

    subgraph EXTERNOS["04 · SERVICIOS Y FUENTES EXTERNAS"]
        direction TB
        SMS["Servicio de mensajería<br/>SMS / WhatsApp"]
        XLS[("Archivos históricos<br/>Excel / registros en papel")]
    end

    USER -->|"Usa el sistema"| WEB
    WEB -->|"Solicitudes HTTP"| CTRL
    CTRL -->|"Invoca operaciones"| SERV
    SERV -->|"Consulta y modifica datos"| REPO
    REPO --> EF
    EF -->|"Lee y guarda información"| DB

    USER -.->|"Cuando no hay conexión"| PWA
    PWA <--> LOCAL
    LOCAL -.->|"Sincronización al recuperar conexión"| CTRL

    SERV -->|"Solicita notificaciones"| SMS
    XLS -.->|"Información para importar"| SERV

    %% Estilos
    classDef user fill:#EAF2F8,stroke:#2874A6,color:#154360,stroke-width:1.5px
    classDef frontend fill:#D6EAF8,stroke:#2874A6,color:#154360,stroke-width:1.5px
    classDef business fill:#D5F5E3,stroke:#239B56,color:#145A32,stroke-width:1.5px
    classDef persistence fill:#FCF3CF,stroke:#B7950B,color:#7D6608,stroke-width:1.5px
    classDef external fill:#F4ECF7,stroke:#884EA0,color:#512E5F,stroke-width:1.5px

    class USER user
    class WEB,PWA,LOCAL frontend
    class CTRL,SERV,REPO business
    class EF,DB persistence
    class SMS,XLS external

    style CLIENTE fill:#F8FBFD,stroke:#2874A6,stroke-width:1.5px
    style APLICACION fill:#F7FCF8,stroke:#239B56,stroke-width:1.5px
    style DATOS fill:#FFFCF2,stroke:#B7950B,stroke-width:1.5px
    style EXTERNOS fill:#FBF7FC,stroke:#884EA0,stroke-width:1.5px

    linkStyle default stroke:#566573,stroke-width:1.4px,color:#273746
```

## Descripción

La solución se plantea como un monolito modular desarrollado con ASP.NET Core MVC 9 y C#. La interfaz utiliza vistas Razor, los servicios concentran las reglas del negocio y el acceso a datos se organiza mediante Repository y Unit of Work. Entity Framework Core permite la comunicación con SQL Server.

Las capacidades PWA y el almacenamiento local representan el soporte previsto para trabajar sin conexión y sincronizar operaciones pendientes. Su funcionamiento depende de la implementación concreta del proyecto.
