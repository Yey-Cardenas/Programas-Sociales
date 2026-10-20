
# Plan de medición de atributos de calidad

## 1. Introducción

El presente documento establece el procedimiento propuesto para evaluar los atributos de calidad del Sistema de Gestión de Programas Sociales de Huamanga.

Los atributos de calidad permiten describir las condiciones que deberá cumplir el sistema respecto a su disponibilidad, rendimiento, usabilidad, seguridad, compatibilidad, auditabilidad, capacidad de crecimiento, mantenibilidad y recuperación de información.

Para que estos atributos puedan verificarse, cada uno debe relacionarse con un método de evaluación, un criterio de aceptación y una evidencia que permita revisar el resultado.

**Estado actual:** este documento define un plan de evaluación. Como el repositorio corresponde a una propuesta académica de arquitectura y documentación, los resultados de las pruebas de la aplicación quedan pendientes de una implementación funcional.

## 2. Objetivos

### 2.1. Objetivo general

Definir un procedimiento de medición que permita evaluar los atributos de calidad establecidos para el sistema y comprobar, mediante evidencias verificables, si se cumplen los criterios de aceptación definidos.

### 2.2. Objetivos específicos

- Establecer métricas o métodos de verificación para cada atributo de calidad.
- Identificar los criterios de aceptación existentes y los que necesitan definición.
- Registrar las condiciones bajo las cuales se ejecutará cada evaluación.
- Documentar los resultados sin confundir objetivos de diseño con resultados medidos.
- Relacionar las evaluaciones con los requisitos no funcionales y las decisiones arquitectónicas.

## 3. Criterios generales de medición

La evaluación de calidad seguirá estos criterios:

1. **Definir:** identificar el atributo, el requisito relacionado y su criterio de aceptación.
2. **Preparar:** especificar el entorno, los datos de prueba, las herramientas y las condiciones de ejecución.
3. **Ejecutar:** realizar la prueba o revisión correspondiente.
4. **Registrar:** guardar el resultado obtenido y la evidencia.
5. **Comparar:** contrastar el resultado con el criterio de aceptación.
6. **Concluir:** indicar si el criterio se cumple, no se cumple o todavía no puede evaluarse.

Los resultados se clasificarán mediante los siguientes estados:

| Estado | Significado |
|---|---|
| Pendiente | La evaluación todavía no se ha ejecutado o falta información necesaria. |
| Cumple | Existe evidencia suficiente y el resultado satisface el criterio establecido. |
| No cumple | La evaluación se realizó y el resultado no satisface el criterio. |
| No aplica | El criterio no corresponde al alcance evaluado; deberá justificarse. |

Un atributo no se considerará aprobado únicamente porque esté descrito en la documentación o porque exista una decisión arquitectónica relacionada con él.

## 4. Matriz de medición de atributos de calidad

### 4.1. AC-01: Disponibilidad

**Objetivo:** evaluar la capacidad del sistema para permanecer operativo durante el periodo establecido.

**Métrica propuesta:** porcentaje de disponibilidad durante el periodo de observación.

Fórmula:

Disponibilidad (%) = (Tiempo disponible / Tiempo de servicio comprometido) × 100

**Criterio de aceptación documentado:** disponibilidad mensual igual o superior al 99 %, de acuerdo con la propuesta actual de atributos de calidad.

**Procedimiento:**

1. Definir el periodo de servicio y los horarios en los que el sistema debe estar disponible.
2. Establecer cómo se identificarán las interrupciones.
3. Registrar el tiempo disponible y el tiempo de indisponibilidad.
4. Calcular el porcentaje de disponibilidad al finalizar el periodo.
5. Comparar el resultado con el objetivo del 99 %.

**Evidencia:** registros de monitoreo, incidencias y cálculo de disponibilidad.

**Estado inicial:** Pendiente. La medición requiere una aplicación desplegada y un periodo de observación.

### 4.2. AC-02: Rendimiento

**Objetivo:** evaluar el tiempo de respuesta de las operaciones relevantes del sistema.

**Métrica propuesta:** tiempo transcurrido entre el envío de una solicitud y la recepción de su respuesta, expresado en milisegundos.

**Criterio de aceptación documentado:** la validación de registros duplicados deberá realizarse en menos de 500 milisegundos, según el requisito de rendimiento definido en la propuesta.

**Procedimiento:**

1. Identificar la operación exacta que valida posibles duplicados.
2. Definir el entorno de prueba, la configuración del servidor y de la base de datos.
3. Preparar un conjunto de datos representativo.
4. Registrar el tiempo de respuesta en múltiples ejecuciones.
5. Documentar la cantidad de solicitudes, la concurrencia y las condiciones de la prueba.
6. Comparar los resultados con el límite establecido.

Como información adicional, se recomienda registrar la mediana y el percentil 95 (p95) de los tiempos de respuesta. El uso del p95 como criterio formal de aceptación deberá acordarse antes de ejecutar la prueba; no debe confundirse con el requisito original de menos de 500 milisegundos.

**Evidencia:** resultados de la herramienta de pruebas, configuración del entorno y resumen de tiempos.

**Estado inicial:** Pendiente. No existen resultados de rendimiento medidos en esta propuesta documental.

### 4.3. AC-03: Usabilidad

**Objetivo:** evaluar si los usuarios pueden realizar las tareas principales de manera comprensible y con errores controlados.

**Métricas propuestas:**

- Porcentaje de tareas completadas correctamente.
- Número de errores durante la ejecución de las tareas.
- Tiempo necesario para completar cada tarea.
- Cantidad de campos obligatorios por formulario.

Fórmula para completar tareas:

Tasa de éxito (%) = (Tareas completadas correctamente / Total de tareas ejecutadas) × 100

**Criterio de aceptación:** deberá definirse un umbral de éxito y un conjunto de tareas antes de realizar la evaluación. La cantidad de campos obligatorios deberá contrastarse con los formularios y requisitos funcionales aprobados.

**Procedimiento:**

1. Seleccionar tareas representativas, como registrar un beneficiario o consultar su información.
2. Definir instrucciones iguales para todos los participantes.
3. Registrar si cada tarea se completa correctamente.
4. Documentar errores, dificultades y tiempos.
5. Revisar los formularios para identificar campos obligatorios innecesarios.
6. Comparar los resultados con los umbrales que se hayan aprobado previamente.

**Evidencia:** protocolo de evaluación, resultados anonimizados, registro de errores y revisión de formularios.

**Estado inicial:** Pendiente. Los umbrales de aceptación deben establecerse antes de la prueba.

### 4.4. AC-04: Seguridad y privacidad

**Objetivo:** verificar que el sistema aplique los controles de acceso y las medidas de protección de información previstas.

**Métricas y verificaciones propuestas:**

- Casos de prueba de autorización aprobados.
- Intentos de acceso no autorizado bloqueados correctamente.
- Verificación de protección de operaciones sensibles.
- Revisión del manejo de datos personales y credenciales.
- Revisión de registros para detectar exposición de información sensible.

Fórmula para los casos de autorización:

Tasa de aprobación (%) = (Casos de autorización aprobados / Total de casos ejecutados) × 100

**Criterio de aceptación:** todos los casos de seguridad definidos como obligatorios deberán cumplir su resultado esperado. La cobertura concreta de pruebas y los controles exigibles deberán establecerse antes de la evaluación.

**Procedimiento:**

1. Identificar los roles y permisos definidos en los requisitos.
2. Elaborar casos de prueba para usuarios autorizados y no autorizados.
3. Verificar las restricciones en las operaciones protegidas.
4. Revisar el manejo de credenciales y datos personales.
5. Registrar las vulnerabilidades encontradas y las acciones correctivas.

**Evidencia:** matriz de permisos, casos de prueba, informes de revisión y registro de incidencias.

**Estado inicial:** Pendiente. No se afirma que los controles hayan sido implementados o auditados.

### 4.5. AC-05: Compatibilidad

**Objetivo:** comprobar que las funciones principales se utilicen correctamente en los dispositivos y navegadores incluidos en el alcance del sistema.

**Métrica propuesta:** porcentaje de casos de compatibilidad aprobados.

Fórmula:

Compatibilidad (%) = (Casos aprobados / Total de casos ejecutados) × 100

**Criterio de aceptación:** las funciones críticas deberán operar correctamente en todos los entornos declarados como obligatorios. La lista de navegadores, dispositivos y resoluciones deberá aprobarse antes de la evaluación.

**Procedimiento:**

1. Identificar los dispositivos y navegadores que utilizará la población objetivo.
2. Preparar una matriz de combinaciones que se evaluarán.
3. Ejecutar las tareas principales en cada entorno.
4. Registrar errores visuales, funcionales y de interacción.
5. Comparar los resultados con la matriz de compatibilidad aprobada.

Si se desarrolla la PWA propuesta, también deberán evaluarse por separado las funciones que dependan de la conexión y las que se hayan diseñado para funcionar sin conexión.

**Evidencia:** matriz de dispositivos y navegadores, capturas de resultados e incidencias.

**Estado inicial:** Pendiente. Los entornos de prueba deben definirse.

### 4.6. AC-06: Auditoría

**Objetivo:** verificar que las operaciones relevantes puedan rastrearse mediante registros suficientes para conocer qué ocurrió y cuándo ocurrió.

**Métricas propuestas:**

- Porcentaje de operaciones auditables con un registro válido.
- Integridad de los campos obligatorios del registro.
- Capacidad para localizar eventos relacionados con una operación de prueba.

Fórmula:

Cobertura de auditoría (%) = (Operaciones auditables registradas correctamente / Total de operaciones auditables ejecutadas) × 100

**Criterio de aceptación:** las operaciones identificadas como auditables deberán producir registros que cumplan los campos y reglas definidos en los requisitos. La lista definitiva de operaciones y campos obligatorios debe establecerse antes de probar.

**Procedimiento:**

1. Identificar las operaciones que necesitan trazabilidad.
2. Definir los campos de cada registro, como fecha, tipo de operación, resultado e identificador del usuario cuando corresponda.
3. Ejecutar operaciones de prueba.
4. Verificar la existencia y consistencia de los registros.
5. Comprobar que la información sensible no se exponga indebidamente.
6. Revisar las medidas de protección contra modificación o eliminación no autorizada.

**Evidencia:** registros de prueba anonimizados, matriz de eventos y resultados de revisión.

**Estado inicial:** Pendiente. La existencia de auditoría debe verificarse en la futura implementación.

### 4.7. AC-07: Capacidad de crecimiento

**Objetivo:** evaluar el comportamiento del sistema al aumentar la cantidad de beneficiarios y la actividad de los usuarios.

**Referencia de volumen documentada:** hasta 15 000 beneficiarios.

Esta cifra representa un volumen de datos de referencia; por sí sola no demuestra que el sistema pueda manejarlo de manera satisfactoria.

**Métricas propuestas:**

- Tiempo de respuesta de las operaciones relevantes.
- Tasa de errores durante la prueba.
- Uso de memoria y procesador.
- Comportamiento de las consultas a la base de datos.

**Criterio de aceptación:** el sistema deberá procesar el volumen de referencia de 15 000 beneficiarios y satisfacer los criterios de rendimiento aplicables. Los niveles de concurrencia y los límites de recursos deberán definirse antes de la prueba.

**Procedimiento:**

1. Preparar datos sintéticos o anonimizados hasta alcanzar el volumen de referencia.
2. Definir las operaciones que se evaluarán y la carga de usuarios prevista.
3. Ejecutar consultas y operaciones representativas.
4. Registrar tiempos de respuesta, errores y uso de recursos.
5. Comparar los resultados con los requisitos de rendimiento.
6. Documentar los cuellos de botella y las posibles mejoras.

**Evidencia:** conjunto de datos de prueba, configuración del entorno e informe de carga.

**Estado inicial:** Pendiente. La capacidad de crecimiento no se considera demostrada por la sola definición de una arquitectura modular.

### 4.8. AC-08: Mantenibilidad y evolución

**Objetivo:** evaluar si la organización del código permite comprender, probar y modificar los componentes sin generar dependencias innecesarias.

**Métodos de evaluación propuestos:**

- Revisión de la separación de responsabilidades.
- Verificación de los principios SOLID.
- Revisión de dependencias entre módulos.
- Ejecución de pruebas automatizadas relacionadas con los cambios.
- Análisis estático del código cuando exista una implementación.
- Registro del impacto de un cambio representativo.

**Criterio de aceptación:** deberá definirse una lista de comprobación de arquitectura y código. Los criterios obligatorios deberán cumplirse y las excepciones deberán documentarse con su justificación.

La presencia de interfaces, servicios o carpetas separadas no será suficiente para concluir que el sistema es mantenible.

**Procedimiento:**

1. Seleccionar componentes representativos de los módulos implementados.
2. Revisar sus responsabilidades y dependencias.
3. Comprobar la aplicación de los principios SOLID.
4. Ejecutar las pruebas disponibles.
5. Analizar el impacto de un cambio representativo.
6. Registrar los problemas identificados y las acciones correctivas.

**Evidencia:** lista de comprobación SOLID, resultados de pruebas, informe de revisión y análisis de dependencias.

**Estado inicial:** Pendiente. La evaluación técnica requiere código fuente implementado.

### 4.9. AC-09: Respaldo y recuperación

**Objetivo:** comprobar que la información respaldada pueda recuperarse cuando ocurra una pérdida de datos o una incidencia que lo requiera.

**Métricas propuestas:**

- Porcentaje de respaldos completados correctamente.
- Porcentaje de restauraciones de prueba exitosas.
- Tiempo necesario para restaurar el servicio.
- Diferencia entre el estado recuperado y el estado esperado.

**Criterio de aceptación:** los respaldos deberán poder generarse y restaurarse de acuerdo con el procedimiento aprobado. La frecuencia definitiva, la retención, el tiempo máximo de recuperación (RTO) y la pérdida máxima de datos tolerable (RPO) deberán acordarse con la institución.

**Procedimiento:**

1. Definir la frecuencia y la ubicación de los respaldos.
2. Establecer controles de acceso y protección de las copias.
3. Realizar un respaldo de prueba.
4. Restaurarlo en un entorno controlado.
5. Verificar la integridad de los datos recuperados.
6. Registrar el tiempo de recuperación y las incidencias.

**Evidencia:** registro de respaldo, bitácora de restauración y comprobaciones de integridad.

**Estado inicial:** Pendiente. No se considera comprobada la recuperación hasta ejecutar una restauración de prueba.

## 5. Resumen de métricas y criterios

| Atributo | Métrica o método principal | Criterio o decisión necesaria |
|---|---|---|
| AC-01 Disponibilidad | Porcentaje de disponibilidad mensual | Objetivo documentado: al menos 99 %. |
| AC-02 Rendimiento | Tiempo de respuesta | Validación de duplicados: menos de 500 ms. |
| AC-03 Usabilidad | Éxito de tareas, errores y revisión de formularios | Definir tareas y umbrales. |
| AC-04 Seguridad y privacidad | Casos de autorización y revisión de controles | Definir controles obligatorios. |
| AC-05 Compatibilidad | Casos aprobados por entorno | Definir navegadores y dispositivos. |
| AC-06 Auditoría | Cobertura de operaciones auditables | Definir eventos y campos obligatorios. |
| AC-07 Crecimiento | Rendimiento y errores con 15 000 beneficiarios | Definir concurrencia y límites de recursos. |
| AC-08 Mantenibilidad | Revisión SOLID, dependencias y pruebas | Aprobar lista de comprobación. |
| AC-09 Respaldo y recuperación | Respaldos y restauraciones de prueba | Definir frecuencia, retención, RTO y RPO. |

## 6. Registro de resultados

Cada evaluación deberá registrar, como mínimo, los siguientes datos:

| Campo | Descripción |
|---|---|
| Identificador | Código del atributo evaluado. |
| Fecha | Fecha de ejecución de la evaluación. |
| Versión | Versión del sistema evaluado. |
| Entorno | Configuración de hardware, software y datos de prueba. |
| Procedimiento | Pasos y herramienta utilizados. |
| Criterio | Condición de aceptación definida antes de probar. |
| Resultado | Valor o hallazgo obtenido durante la ejecución. |
| Estado | Pendiente, Cumple, No cumple o No aplica. |
| Evidencia | Ruta al informe, registro o archivo que respalda el resultado. |
| Observaciones | Limitaciones, incidencias y acciones correctivas. |

La siguiente tabla se utilizará para registrar las evaluaciones cuando puedan ejecutarse:

| ID | Resultado medido | Estado | Evidencia |
|---|---|---|---|
| AC-01 | Pendiente de medición | Pendiente | Por generar |
| AC-02 | Pendiente de medición | Pendiente | Por generar |
| AC-03 | Pendiente de evaluación | Pendiente | Por generar |
| AC-04 | Pendiente de evaluación | Pendiente | Por generar |
| AC-05 | Pendiente de evaluación | Pendiente | Por generar |
| AC-06 | Pendiente de evaluación | Pendiente | Por generar |
| AC-07 | Pendiente de prueba de carga | Pendiente | Por generar |
| AC-08 | Pendiente de revisión técnica | Pendiente | Por generar |
| AC-09 | Pendiente de prueba de restauración | Pendiente | Por generar |

Los estados de esta tabla describen la situación inicial de la propuesta documental, no el resultado de una prueba de la aplicación.

## 7. Herramientas de evaluación

Las herramientas definitivas dependerán de la implementación y del entorno de despliegue. Como opciones para evaluar la solución propuesta, se podrán considerar:

- **Pruebas automatizadas de .NET:** para verificar reglas de negocio y comportamientos esperados.
- **Herramientas de pruebas de carga:** para medir tiempos de respuesta y comportamiento bajo concurrencia.
- **Análisis estático de código:** para identificar posibles problemas de calidad y mantenibilidad.
- **Registros y monitoreo del despliegue:** para observar disponibilidad e incidencias.
- **Herramientas de administración de SQL Server:** para revisar consultas, respaldos y restauraciones.
- **Pruebas manuales estructuradas:** para evaluar usabilidad, compatibilidad y flujos funcionales.

La selección de herramientas no implica que estas ya estén configuradas o ejecutadas en el proyecto.

## 8. Relación con la arquitectura y SOLID

La medición de calidad se relaciona con los requisitos no funcionales y los atributos definidos en el análisis del sistema.

El atributo AC-08 se evaluará, entre otros criterios, mediante la revisión de los principios SOLID documentados en `arquitectura/principios-solid.md`.

Las decisiones de arquitectura deberán justificar cómo contribuyen a los atributos de calidad. Sin embargo, una decisión arquitectónica no sustituye la medición: por ejemplo, utilizar un monolito modular no demuestra por sí mismo el cumplimiento de rendimiento o mantenibilidad.

Los resultados deberán utilizarse para identificar desviaciones y proponer mejoras en el diseño o en la implementación.

## 9. Conclusión

Este plan establece una base para evaluar los atributos de calidad del Sistema de Gestión de Programas Sociales de Huamanga de forma verificable y trazable.

Los objetivos existentes se conservan como criterios de diseño cuando están definidos en la documentación. Los criterios que todavía no cuentan con un umbral aprobado deberán precisarse antes de ejecutar las pruebas.

La calidad del sistema se determinará a partir de resultados medidos y evidencias registradas, no únicamente de las características propuestas en los documentos de arquitectura.
