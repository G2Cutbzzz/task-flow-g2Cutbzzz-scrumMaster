# HU-008-Resumen y métricas de seguimiento de tareas
## Historia de usuario
Como integrante del equipo, quiero consultar un resumen numérico del estado de las tareas, para evaluar rápidamente el avance general y la carga de trabajo pendiente del proyecto.

## Criterios de Aceptacion
### CA-001 - Visualización de métricas generales
Given que existen tareas registradas en el sistema
When el usuario accede a la sección de resumen o métricas
Then debe visualizarse el total acumulado de tareas registradas
And el desglose numérico de tareas por cada estado: pendientes, en progreso y completadas
And el porcentaje de avance general respecto al total

### CA-002 - Métricas sin tareas registradas
Given que no existen tareas registradas en el sistema
When el usuario consulta el resumen de seguimiento
Then los contadores numéricos deben mostrarse en cero
And el porcentaje de avance general debe reflejarse como 0%
And debe indicarse un mensaje informativo notificando la ausencia de datos

### CA-003 - Actualización en tiempo real de métricas
Given que el usuario visualiza el resumen de seguimiento
When se produce un cambio en el estado de una tarea o se registra una nueva
Then los contadores y porcentajes deben actualizarse de manera automática e inmediata reflejando el nuevo estado

## Reglas del Negocio
RN-001: El porcentaje de avance se calcula dividiendo la cantidad de tareas completadas entre el total de tareas registradas, multiplicado por 100.
RN-002: Si el total de tareas es igual a cero, el porcentaje de avance debe ser exactamente 0% para evitar errores de división entre cero.
RN-003: Los contadores deben ser de solo lectura y mostrar la suma.

## Dependencias
Depende de HU-001, HU-002 y HU-003.

## Fuera del Alcance
* Generación de gráficas avanzadas tipo Burndown o Diagramas de Gantt.
* Cálculo de tiempos promedio de resolución o ciclo de vida.
* Envío de reportes automatizados por correo electrónico.


