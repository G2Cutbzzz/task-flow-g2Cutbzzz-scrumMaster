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

