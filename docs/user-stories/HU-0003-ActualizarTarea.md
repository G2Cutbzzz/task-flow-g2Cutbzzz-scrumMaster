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
Depende de HU-001 (Crear una tarea) y HU-002 (Consultar tareas registradas).

## Fuera del Alcance
* Flujos de aprobación o validaciones de cambio de estado por roles.
* Bloqueo automático de tareas completadas.
* Historial detallado de auditoría por cambio de estado.


