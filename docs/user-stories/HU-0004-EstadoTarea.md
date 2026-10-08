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

