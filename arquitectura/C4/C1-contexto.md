
# C1 — Diagrama de Contexto del Sistema

**Proyecto:** Sistema de Gestión de Programas Sociales de Huamanga  
**Modelo:** C4 — Nivel 1: Contexto  
**Propósito:** Identificar los usuarios, el sistema y sus relaciones externas.

## Diagrama de contexto

```mermaid
flowchart TB
    %% Actores
    DIR(["👤 Dirigente de Comité<br/>Registra y actualiza beneficiarios"])
    SUB(["👤 Personal de la Subgerencia<br/>Supervisa y consulta información"])
    BEN(["👤 Beneficiario<br/>Recibe notificaciones"])

    %% Sistema principal
    SYS["<b>SISTEMA DE GESTIÓN DE PROGRAMAS SOCIALES</b><br/><br/>Aplicación web para gestionar beneficiarios,<br/>validaciones, revalidaciones y reportes"]

    %% Sistemas externos
    HIST[("Archivos históricos<br/>Excel y registros en papel")]
    MSG["Servicio externo de mensajería<br/>SMS / WhatsApp"]

    %% Relaciones
    DIR -->|"Registra y actualiza datos"| SYS
    SUB -->|"Supervisa, consulta y genera reportes"| SYS
    HIST -.->|"Fuente para revisión e importación"| SYS
    SYS -->|"Solicita envío de mensajes"| MSG
    MSG -->|"Entrega notificaciones"| BEN

    %% Estilos
    classDef actor fill:#EAF2F8,stroke:#2874A6,color:#154360,stroke-width:1.5px
    classDef system fill:#17365D,stroke:#0B1F3A,color:#FFFFFF,stroke-width:2.5px
    classDef external fill:#E8F6F3,stroke:#148F77,color:#145A4A,stroke-width:1.5px

    class DIR,SUB,BEN actor
    class SYS system
    class HIST,MSG external

    linkStyle default stroke:#566573,stroke-width:1.5px,color:#273746
```

## Descripción

El sistema centraliza la gestión de beneficiarios de programas sociales, como Vaso de Leche y Comedores Populares. Los dirigentes registran y actualizan información, mientras que el personal de la Subgerencia supervisa los datos y consulta reportes. Los archivos históricos sirven como fuente de información y el servicio externo de mensajería permite contemplar el envío de notificaciones.

**Nota:** las integraciones con RENIEC y SISFOH no se representan porque no forman parte de la primera versión documentada.
