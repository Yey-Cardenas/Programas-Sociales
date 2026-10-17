
# C1 - Diagrama de Contexto

## 1. Descripción

El diagrama de contexto muestra el Sistema de Gestión de Programas Sociales de Huamanga y su relación con los usuarios y los servicios externos.

Los dirigentes de los comités registran y actualizan la información de los beneficiarios. El personal de la Subgerencia supervisa los registros, revisa alertas y consulta reportes. Los beneficiarios pueden recibir notificaciones relacionadas con los programas sociales.

## 2. Diagrama

```mermaid
flowchart LR
    Dirigente["Dirigente de Comité"]
    Personal["Personal de la Subgerencia"]
    Beneficiario["Beneficiario"]
    Sistema["Sistema de Gestión de Programas Sociales<br/>ASP.NET Core MVC 9"]
    Archivos["Archivos históricos<br/>Excel y registros en papel"]
    Mensajeria["Servicio externo<br/>SMS / WhatsApp"]

    Dirigente -->|"Registra y actualiza beneficiarios"| Sistema
    Personal -->|"Supervisa y consulta reportes"| Sistema
    Sistema -->|"Envía notificaciones"| Mensajeria
    Mensajeria -->|"Entrega mensajes"| Beneficiario
    Archivos -->|"Información para revisión e importación"| Sistema
```

## 3. Elementos del diagrama

- **Dirigente de Comité:** registra, actualiza e inactiva beneficiarios y puede trabajar sin conexión cuando la funcionalidad está disponible.
- **Personal de la Subgerencia:** supervisa la información, revisa posibles duplicados y consulta reportes de cobertura.
- **Beneficiario:** persona inscrita en un programa social que puede recibir notificaciones.
- **Sistema:** aplicación encargada de gestionar la información y las operaciones de los programas sociales.
- **Archivos históricos:** hojas de cálculo y registros en papel que sirven como fuentes para revisar o importar información.
- **Servicio SMS / WhatsApp:** servicio externo previsto para enviar notificaciones.

## 4. Alcance

El sistema contempla la gestión de beneficiarios de programas como Vaso de Leche y Comedores Populares. Las integraciones con RENIEC y SISFOH no forman parte de la primera versión documentada.
