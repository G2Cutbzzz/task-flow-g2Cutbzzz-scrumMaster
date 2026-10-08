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

