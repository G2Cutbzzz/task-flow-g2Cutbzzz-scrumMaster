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

