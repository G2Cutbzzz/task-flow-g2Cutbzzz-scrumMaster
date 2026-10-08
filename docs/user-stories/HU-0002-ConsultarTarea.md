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
Depende de HU-001 (Crear una tarea).

## Fuera del Alcance
* Paginación avanzada de resultados.
* Búsqueda por texto predictivo.
* Exportación a formatos externos (Excel).