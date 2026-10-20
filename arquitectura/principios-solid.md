
# Aplicación de los principios SOLID

## 1. Introducción

Los principios SOLID son cinco principios de diseño de software que ayudan a organizar el código, reducir el acoplamiento y facilitar el mantenimiento y la evolución del sistema.

En el proyecto **Sistema de Gestión de Programas Sociales de Huamanga**, estos principios se tomarán como referencia para orientar el diseño de los módulos y componentes cuando se desarrolle la aplicación.

La solución se plantea como un monolito modular basado en ASP.NET Core MVC. Por ello, la aplicación de SOLID buscará que los controladores, servicios, componentes de acceso a datos y mecanismos de notificación tengan responsabilidades claras.

**Importante:** los ejemplos de este documento son propuestas de diseño en C#. No representan funcionalidades implementadas ni verificadas en el repositorio actual.

## 2. Objetivo

Establecer criterios de diseño para que los futuros componentes del sistema:

- Tengan responsabilidades bien definidas.
- Puedan extenderse sin modificar innecesariamente componentes existentes.
- Mantengan contratos coherentes entre abstracciones e implementaciones.
- Expongan interfaces específicas según las necesidades de cada componente.
- Dependan de abstracciones en lugar de acoplarse directamente a implementaciones concretas.

## 3. Principios SOLID aplicados al proyecto

### 3.1. SRP: principio de responsabilidad única

**Definición:** una clase debe tener una responsabilidad principal y una razón clara para cambiar.

**Aplicación propuesta:** los controladores MVC se encargarán de recibir las solicitudes y coordinar la respuesta HTTP. Las reglas de negocio relacionadas con los beneficiarios se ubicarán en servicios específicos, mientras que el acceso a datos se separará en componentes apropiados.

Por ejemplo, `BeneficiariosController` no debería concentrar la validación de reglas de negocio, las consultas SQL y la generación de reportes.

Ejemplo conceptual:

```csharp
public interface IBeneficiarioService
{
    Task<bool> ExisteDocumentoAsync(
        string numeroDocumento,
        CancellationToken cancellationToken);
}
```

El controlador podría utilizar el servicio mediante inyección de dependencias:

```csharp
public class BeneficiariosController : Controller
{
    private readonly IBeneficiarioService _beneficiarioService;

    public BeneficiariosController(
        IBeneficiarioService beneficiarioService)
    {
        _beneficiarioService = beneficiarioService;
    }
}
```

El ejemplo muestra la separación de responsabilidades. La implementación completa deberá incorporar las acciones, validaciones y respuestas que correspondan a los requisitos del sistema.

**Beneficio esperado:** facilitar las pruebas, reducir la complejidad de los controladores y hacer más sencillo el mantenimiento.

### 3.2. OCP: principio abierto/cerrado

**Definición:** los componentes deben permitir la incorporación de nuevas funcionalidades sin requerir modificaciones innecesarias en el código que ya funciona.

**Aplicación propuesta:** los mecanismos de notificación podrán diseñarse mediante una abstracción común. De esta manera, en el futuro se podrán incorporar diferentes canales sin colocar toda la lógica en una única clase.

Ejemplo conceptual:

```csharp
public interface INotificador
{
    Task EnviarAsync(
        string destinatario,
        string mensaje,
        CancellationToken cancellationToken);
}
```

Se podrían desarrollar implementaciones como:

- `NotificadorCorreo`: para notificaciones por correo electrónico.
- `NotificadorSms`: para mensajes de texto.
- `NotificadorWhatsApp`: para notificaciones mediante WhatsApp, si se dispone de un proveedor adecuado.

Cada implementación deberá cumplir el contrato definido por `INotificador`.

**Beneficio esperado:** facilitar la incorporación de nuevos canales de notificación sin modificar innecesariamente los módulos que los utilizan.

La incorporación de nuevos canales dependerá de los requisitos, los servicios externos disponibles y las condiciones de seguridad correspondientes.

### 3.3. LSP: principio de sustitución de Liskov

**Definición:** una implementación debe poder sustituir a otra que cumpla el mismo contrato sin provocar comportamientos inesperados para el componente que la utiliza.

**Aplicación propuesta:** si el sistema utiliza `INotificador`, cualquier implementación de esta interfaz deberá respetar el significado de sus parámetros, la operación asíncrona y las reglas acordadas para comunicar errores.

Por ejemplo, el componente que solicita una notificación no debería necesitar conocer detalles internos de `NotificadorCorreo` o `NotificadorSms` para invocar la operación común.

Las implementaciones deberán documentar y respetar el tratamiento de errores, cancelaciones y resultados de envío. No deberán informar un envío exitoso cuando el proveedor haya indicado un fallo.

**Beneficio esperado:** poder cambiar o incorporar implementaciones compatibles sin alterar el comportamiento esperado de los componentes consumidores.

### 3.4. ISP: principio de segregación de interfaces

**Definición:** es preferible disponer de interfaces pequeñas y específicas antes que obligar a los componentes a depender de operaciones que no necesitan.

**Aplicación propuesta:** si los módulos de beneficiarios requieren diferentes operaciones, se evaluará separar las interfaces de consulta y gestión.

Ejemplo conceptual:

```csharp
public interface IConsultaBeneficiarios
{
    Task<bool> ExisteDocumentoAsync(
        string numeroDocumento,
        CancellationToken cancellationToken);
}

public interface IGestionBeneficiarios
{
    Task RegistrarAsync(
        Beneficiario beneficiario,
        CancellationToken cancellationToken);
}
```

`Beneficiario` representa una entidad del dominio que deberá definirse durante la implementación. El ejemplo no presupone que dicha clase ya exista en el repositorio.

Un componente que solamente necesite consultar la existencia de un documento podría depender de `IConsultaBeneficiarios`, sin requerir las operaciones de registro.

Las interfaces definitivas se establecerán después de revisar los casos de uso y las operaciones reales de cada módulo.

**Beneficio esperado:** reducir dependencias innecesarias y facilitar la evolución de las interfaces.

### 3.5. DIP: principio de inversión de dependencias

**Definición:** los componentes de alto nivel y los de bajo nivel deben depender de abstracciones, no directamente unos de otros mediante implementaciones concretas.

**Aplicación propuesta:** los servicios de negocio utilizarán interfaces para acceder a las operaciones que necesiten. ASP.NET Core permitirá registrar y proporcionar las implementaciones mediante inyección de dependencias.

Por ejemplo, un servicio de beneficiarios podría depender de `IConsultaBeneficiarios` en lugar de crear directamente una instancia de una clase concreta de acceso a datos.

Los registros de dependencias se definirán durante la implementación, por ejemplo, en el punto de configuración de servicios de ASP.NET Core.

**Beneficio esperado:** reducir el acoplamiento, facilitar las pruebas unitarias y permitir cambiar implementaciones con menos impacto en los componentes consumidores.

La elección de las abstracciones deberá responder a necesidades reales del sistema. No será necesario crear interfaces para todas las clases de manera automática.

## 4. Relación con la arquitectura propuesta

La aplicación de SOLID se organizará de acuerdo con las responsabilidades previstas en la arquitectura MVC y el enfoque de monolito modular.

| Componente | Responsabilidad propuesta |
|---|---|
| Controladores MVC | Recibir solicitudes y coordinar respuestas HTTP. |
| Servicios de aplicación | Coordinar casos de uso y operaciones del sistema. |
| Componentes de acceso a datos | Consultar y persistir información. |
| Interfaces | Definir contratos entre componentes cuando sea necesario. |
| Implementaciones de infraestructura | Resolver operaciones técnicas, como el acceso a datos o el envío de notificaciones. |
| Inyección de dependencias | Proporcionar las implementaciones requeridas por los componentes. |

La organización definitiva deberá mantenerse coherente con los módulos y componentes descritos en los diagramas C4 del proyecto.

## 5. Criterios para verificar su aplicación

Cuando se implemente el sistema, la revisión de SOLID tendrá en cuenta los siguientes criterios:

- [ ] Los controladores no concentran reglas de negocio ni acceso directo a la base de datos.
- [ ] Cada clase tiene una responsabilidad principal identificable.
- [ ] Las nuevas funcionalidades pueden incorporarse sin modificar innecesariamente componentes no relacionados.
- [ ] Las implementaciones respetan los contratos de las interfaces.
- [ ] Las interfaces contienen operaciones relacionadas con una finalidad concreta.
- [ ] Los servicios dependen de abstracciones cuando ello aporta una separación útil.
- [ ] Las dependencias pueden sustituirse o aislarse para facilitar las pruebas.
- [ ] Los cambios en un módulo no provocan modificaciones innecesarias en otros módulos.

La revisión deberá acompañarse de pruebas automatizadas cuando existan componentes implementados. La presencia de interfaces o clases con determinados nombres no será suficiente para demostrar que SOLID se ha aplicado correctamente.

## 6. Relación con la mantenibilidad y la calidad

La aplicación de SOLID contribuirá al diseño orientado a la mantenibilidad, la modularidad y la facilidad de evolución del sistema.

Su cumplimiento se revisará en relación con el atributo de calidad **AC-08: Mantenibilidad y evolución**, definido en la documentación de atributos de calidad.

Estos principios no garantizan por sí solos la calidad del sistema. Su aporte deberá evaluarse mediante revisión del diseño, análisis del código disponible y pruebas cuando corresponda.

Mientras no exista una implementación funcional, los principios descritos se consideran criterios de diseño propuestos y no resultados de una evaluación técnica.

## 7. Conclusión

Se propone utilizar SOLID como guía para organizar las responsabilidades, establecer contratos entre componentes y reducir el acoplamiento en el Sistema de Gestión de Programas Sociales de Huamanga.

Su aplicación deberá verificarse durante el desarrollo, considerando los requisitos, los diagramas arquitectónicos y las necesidades reales de cada módulo. De esta manera, se buscará facilitar el mantenimiento y la incorporación de cambios sin añadir complejidad innecesaria.
