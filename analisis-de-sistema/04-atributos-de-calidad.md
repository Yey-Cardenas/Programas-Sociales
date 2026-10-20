# Atributos de calidad

## Escenario general

Un dirigente de comité registra a varios beneficiarios en una zona con baja cobertura de internet. Al recuperar la conexión, su aplicativo sincroniza los datos y el sistema debe validar los DNI contra todo el padrón municipal, mientras el personal de la Sub Gerencia consulta el mapa de cobertura. Los datos son personales y sensibles, y el sistema opera durante todo el año.


## Escenarios de calidad

| ID | Atributo de calidad | Escenario y criterio verificable | Origen |
|---|---|---|---|
| AC01 | Disponibilidad y continuidad | Se propone una disponibilidad mensual mínima del 99%. El registro sin conexión se considera un requisito independiente y deberá probarse verificando la conservación de los datos y su sincronización posterior. | RNF-01 |
| AC02 | Rendimiento | La validación de duplicados por DNI deberá responder en menos de 0.5 segundos en las condiciones de carga definidas para las pruebas. Se registrará el tiempo de respuesta y el número de usuarios concurrentes. | RNF-02 |
| AC03 | Usabilidad | El formulario de registro tendrá como máximo cinco campos obligatorios, siempre que se mantenga la información necesaria para validar el registro. | RNF-03 |
| AC04 | Seguridad y privacidad | Los datos personales estarán protegidos mediante comunicación cifrada, autorización por roles y controles de acceso. Las copias de seguridad también deberán contar con protección de acceso. | RNF-04 |
| AC05 | Compatibilidad | Se definirá y probará una matriz de navegadores y dispositivos móviles compatibles. Android 8+ se mantendrá como objetivo de compatibilidad que deberá validarse con las tecnologías PWA seleccionadas. | RNF-05 |
| AC06 | Auditabilidad | Las modificaciones relevantes deberán registrar usuario, fecha, acción y resultado. Cuando corresponda, también se registrarán el motivo y los valores modificados. | RNF-06 |
| AC07 | Capacidad | El sistema deberá gestionar al menos 15,000 beneficiarios sin superar los umbrales de rendimiento definidos en las pruebas de carga. | RNF-07 |
| AC08 | Mantenibilidad | La incorporación de un nuevo programa social deberá poder realizarse sin rediseñar la totalidad del sistema, respetando la separación modular. | RNF-08 |
| AC09 | Respaldo y recuperación | Se propone generar copias de seguridad diarias. Se deberá definir el periodo de conservación y comprobar mediante una prueba que los datos puedan restaurarse. | RNF-09 |



## Escenarios con formato estímulo – respuesta – medida

### AC02 – Rendimiento

| Elemento | Descripción |
|---|---|
| Estímulo | Un usuario registra un DNI para comprobar si ya existe en el padrón. |
| Respuesta | El sistema consulta los registros y muestra el resultado de la validación. |
| Medida | La respuesta deberá ser inferior a 0.5 segundos bajo una carga de prueba documentada con 15,000 beneficiarios. También se registrarán los tiempos de respuesta y las condiciones de ejecución. |

### AC01 – Disponibilidad y continuidad

| Elemento | Descripción |
|---|---|
| Estímulo | Un usuario intenta registrar información sin conexión a internet. |
| Respuesta esperada | Si la funcionalidad offline está implementada, la aplicación conserva temporalmente el registro y permite intentar la sincronización cuando se recupere la conexión. |
| Medida | Las pruebas comprobarán que no se pierdan registros, que los errores de sincronización puedan identificarse y que no se creen duplicados por reintentos. La disponibilidad mensual se medirá por separado. |

### AC09 – Respaldo y recuperación

| Elemento | Descripción |
|---|---|
| Estímulo | Se requiere recuperar información después de una pérdida de datos o una incidencia. |
| Respuesta esperada | Se restaura una copia de seguridad válida en un entorno controlado. |
| Medida | Se documentan la fecha del respaldo, el resultado de la restauración y el tiempo empleado. El periodo de conservación y los objetivos de recuperación se definirán para el proyecto. |
