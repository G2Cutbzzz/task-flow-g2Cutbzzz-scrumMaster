# HU-001-Crear una tarea
## Historia de usuario
Como integrante del equipo, quiero registrar una nueva tarea cin titulo y descripcion, para documentar el trabajo que necesito realizar.

## Criterios de Aceptacion
### CA-001 - Crear correctamente
Given que el usuario proporciona el titulo válido
When solicita crear la tarea
Then la tarea debe agregarse
And debe de iniciar con un estado Pendiente

### CA-002 - Titulo obligatorio
Given que el usuario desea crear una tarea
And no proporciona el titulo
When intenta registrar la tarea
Then la tarea no debe ser creada
And debe recibir información indicando que el titulo es obligatorio

### CA-003 - Longitud minima del titulo
Given que el usuario desea crear una tarea
And proporciona un titulo con menos de 3 caracteres
When intenta registrar la tarea
Then la tarea no debe ser creada
And debe informarse que el titulo no cumple con la longitud minima 

### CA-004 - Longitud maxima del titulo
Given que el usuario desea crear una tarea
And proporciona un titulo mayor a 80 caracteres
When intenta registrar la tarea
Then la tarea no debe ser creada
And debe informarse que el titulo no cumple con la longitud maxima

### CA-005 - Descripcion opcional
Given que el usuario proporciona un titulo valido
And no proporciona descripcion
When registra la tarea 
Then la tarea debe de crearse correctamente

### CA-006 - Descripcion demasiado extensa
Given que el usuario proporciona una descripcion mayor a 300 caracteres
When intenta crear la tarea
Then la tarea no debe ser registrada
And debe informarse la restriccion correspondiente


## Reglas del Negocio
RN-001: Toda tarea debe de tener título.
RN-002: El titulo debe de contener entre 3 y 80 caracteres.
RN-003: La descripción es opcional.
RN-004: La descripción tendrá máximo 300 caracteres.
RN-005: Toda tarea nueva inicia como pendiente.
RN-006: Cada tarea debe de poder identificarse de una manera unica.
RN-007: Debe conocerse cuando fue creada la tarea.

## Dependencias
Esta hostoria no depende funcionalmente de otra HU.

## Fuera del Alcance
* Asignar tareas a personas.
* Fechas limite.
* Prioridades
* Categorias.
* Archivos adjuntos.
* SubTareas.
* Notificaciones

# HU-002-Consultar tareas registradas
## Historia de usuario
Como integrante del equipo, quiero ver la lista completa de tareas registradas con sus datos principales, para dar seguimiento al trabajo pendiente del proyecto.

## Criterios de Aceptacion
### CA-001 - Consulta con tareas existentes
Given que existen tareas registradas en el sistema
When el usuario accede a la vista de tareas
Then debe mostrarse el listado de todas las tareas
And cada elemento debe exhibir su identificador, título, estado y fecha de registro

### CA-002 - Consulta sin registros previos
Given que no existe ninguna tarea registrada en el sistema
When el usuario accede a la vista de tareas
Then no debe presentarse ninguna lista vacía sin contexto
And debe mostrarse un mensaje informativo indicando que aún no hay tareas registradas

### CA-003 - Visualización de detalle de una tarea
Given que el usuario observa el listado de tareas
When selecciona una tarea específica
Then debe desplegarse el detalle completo incluyendo su descripción si fue registrada

## Reglas del Negocio
RN-001: La lista debe mostrarse ordenada cronológicamente de forma descendente por fecha de creación de manera predeterminada.
RN-002: Cada elemento del listado debe mostrar como mínimo identificador único, título y estado actual.
RN-003: La consulta no debe alterar el estado ni los datos de ninguna tarea.

## Dependencias
Depende de HU-001.

## Fuera del Alcance
* Paginación avanzada de resultados.
* Búsqueda por texto predictivo.
* Exportación a formatos externos (Formatos de excel).


# HU-003-Actualizar estado de una tarea
## Historia de usuario
Como integrante del equipo, quiero cambiar el estado de una tarea existente, para reflejar el avance real del trabajo en el flujo del proyecto.

## Criterios de Aceptacion
### CA-001 - Cambio de estado válido
Given que existe una tarea registrada
And se encuentra en estado "Pendiente"
When el usuario selecciona cambiar su estado a "En progreso"
Then el estado de la tarea debe actualizarse correctamente
And debe registrarse la fecha y hora de la última modificación

### CA-002 - Transición a completada
Given que una tarea se encuentra en estado "En progreso"
When el usuario actualiza el estado a "Completada"
Then la tarea debe reflejar el estado final "Completada"
And debe quedar visible el cambio en las consultas posteriores

### CA-003 - Selección de estado inválido
Given que el usuario desea actualizar el estado de una tarea
When intenta ingresar un valor distinto a "Pendiente", "En progreso" o "Completada"
Then el sistema debe rechazar la modificación
And debe mantenerse el estado previo sin alteraciones

## Reglas del Negocio
RN-001: Los únicos estados válidos son: "Pendiente", "En progreso" y "Completada".
RN-002: Una tarea puede transicionar libremente entre los estados válidos según la necesidad del equipo.
RN-003: Cada cambio de estado debe actualizar la fecha de modificación de la tarea.

## Dependencias
Depende de HU-001 y HU-002.

## Fuera del Alcance
* Flujos de aprobación o validaciones de cambio de estado por roles.
* Bloqueo automático de tareas completadas.
* Historial detallado de auditoría por cambio de estado.


# HU-004-Identificar tareas por estado: pendientes, en progreso y completadas
## Historia de usuario
Como integrante del equipo, quiero filtrar y diferenciar visualmente las tareas según su estado, para conocer de inmediato la distribución del trabajo.

## Criterios de Aceptacion
### CA-001 - Filtrado por estado específico
Given que existen tareas en distintos estados
When el usuario aplica un filtro seleccionando "En progreso"
Then el listado debe mostrar exclusivamente las tareas cuyo estado sea "En progreso"

### CA-002 - Filtro sin resultados coincidentes
Given que existen tareas registradas
And ninguna se encuentra en estado "Completada"
When el usuario filtra por el estado "Completada"
Then la lista debe quedar despejada
And debe mostrarse un mensaje indicando que no hay tareas en dicho estado

### CA-003 - Restablecer visualización completa
Given que el usuario tiene un filtro de estado activo
When solicita remover el filtro o ver todas las tareas
Then el sistema debe restaurar el listado completo sin restricciones de estado

## Reglas del Negocio
RN-001: El filtrado debe operar sobre los tres estados oficiales: "Pendiente", "En progreso" y "Completada".
RN-002: La vista filtrada debe conservar el orden cronológico original de las tareas resultantes.
RN-003: La interfaz debe indicar claramente cuál es el filtro actualmente aplicado.

## Dependencias
Depende de HU-002 y HU-003.

## Fuera del Alcance
* Filtros combinados múltiples por fecha y usuario.
* Vistas tipo tablero Kanban con arrastrar y soltar .
* Contadores analíticos o métricas de productividad.

# HU-005-Conservar las tareas registradas entre sesiones
## Historia de usuario
Como integrante del equipo, quiero que las tareas registradas y sus cambios se almacenen de forma permanente, para no perder información al cerrar el navegador o reiniciar la aplicación.

## Criterios de Aceptacion
### CA-001 - Recuperación de datos al iniciar sesión
Given que el usuario registró tareas en una sesión previa
When vuelve a ingresar a la aplicación
Then todas las tareas creadas deben estar disponibles con su información intacta

### CA-002 - Persistencia inmediata tras modificaciones
Given que el usuario actualiza el estado de una tarea
When la modificación es confirmada y se recarga o cierra la aplicación
Then al volver a consultar la tarea debe reflejar el último estado guardado

### CA-003 - Integridad ante almacenamiento vacío
Given que es el primer uso de la aplicación y no hay archivo o almacén previo
When se inicializa el sistema
Then debe crearse la estructura de almacenamiento vacía sin generar errores de lectura

## Reglas del Negocio
RN-001: Toda operación de creación, actualización o cambio de estado debe persistirse de forma inmediata.
RN-002: En caso de error de lectura del almacenamiento, el sistema debe notificar la incidencia sin sobreescribir datos preexistentes.

## Dependencias
Aplica transversalmente a HU-001, HU-002 y HU-003.

## Fuera del Alcance
* Sincronización en la nube multi-dispositivo en tiempo real.
* Manejo de bases de datos distribuidas o réplicas.
* Copias de seguridad automáticas externas.


# HU-006-Editar datos generales de una tarea
## Historia de usuario
Como integrante del equipo, quiero modificar el título o la descripción de una tarea existente, para corregir errores o detallar el trabajo sin tener que rehacer la tarea.

## Criterios de Aceptacion
### CA-001 - Edición exitosa de título y descripción
Given que existe una tarea registrada
When el usuario modifica su título por otro válido y actualiza la descripción
Then la información debe quedar guardada con los nuevos valores
And el identificador único y el estado actual deben permanecer intactos

### CA-002 - Intento de dejar título vacío
Given que el usuario está editando una tarea existente
When elimina el contenido del título e intenta guardar
Then los cambios no deben aplicarse
And debe mostrarse un mensaje indicando que el título es obligatorio

### CA-003 - Título fuera del rango de caracteres
Given que el usuario edita una tarea
When ingresa un título menor a 3 o mayor a 80 caracteres
Then el sistema debe bloquear el guardado
And debe informar las restricciones de longitud correspondientes

## Reglas del Negocio
RN-001: El identificador único de la tarea es inmutable y no puede ser alterado.
RN-002: Las validaciones de longitud para título 3 a 80 caracteres y descripción máximo 300 caracteres aplican idénticas a la creación.
RN-003: La fecha de última modificación debe actualizarse tras cada edición exitosa.

## Dependencias
Depende de HU-001 y HU-002.

## Fuera del Alcance
* Control de versiones o rollback de cambios anteriores.
* Edición colaborativa concurrente sobre la misma tarea.

# HU-007-Eliminar tarea
## Historia de usuario
Como integrante del equipo, quiero dar de baja una tarea que ya no es necesaria o que fue creada por error, para mantener limpio y relevante el tablero de trabajo.

## Criterios de Aceptacion
### CA-001 - Confirmación previa a la eliminación
Given que el usuario selecciona eliminar una tarea específica
When solicita la acción de borrado
Then el sistema debe solicitar confirmación explícita antes de proceder

### CA-002 - Eliminación confirmada
Given que el usuario solicitó eliminar una tarea
When confirma la acción en el diálogo de advertencia
Then la tarea debe removerse del almacenamiento
And no debe volver a mostrarse en los listados ni filtros

### CA-003 - Cancelación de la eliminación
Given que se presentó el mensaje de confirmación de borrado
When el usuario cancela la operación
Then la tarea no debe eliminarse y debe conservar todos sus datos

## Reglas del Negocio
RN-001: Toda acción de eliminación debe requerir confirmación del usuario para prevenir pérdidas accidentales.
RN-002: Una tarea eliminada no puede ser recuperada en el flujo regular de trabajo.
RN-003: El identificador de una tarea eliminada no debe ser reutilizado por nuevas tareas.

## Dependencias
Depende de HU-001 y HU-002.

## Fuera del Alcance
* Papelera de reciclaje o restauración de elementos eliminados.
* Registro de motivos o justificaciones de eliminación.

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





