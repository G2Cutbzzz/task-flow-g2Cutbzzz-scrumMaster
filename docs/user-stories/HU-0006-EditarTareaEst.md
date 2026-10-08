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


