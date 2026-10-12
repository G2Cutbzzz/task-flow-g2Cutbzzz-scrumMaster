# SPEC-001 — Gestión básica de tareas (Sprint 1)

**Estado:** Aprobado como especificación de alcance y trazabilidad del Sprint 1. Las decisiones D1–D5 siguen pendientes y deberán resolverse antes de implementar los aspectos afectados.

## 1. Propósito

Especificar el comportamiento observable y los contratos técnicos necesarios para implementar exclusivamente las historias HU-0001, HU-0002, HU-0003 y HU-0005 del Sprint 1 de TaskFlow Lite, manteniendo la trazabilidad entre historias, criterios de aceptación, reglas de negocio y tareas técnicas.

## 2. Alcance

Incluye:

- Crear tareas con validaciones del título y la descripción.
- Consultar el listado de tareas y el detalle de una tarea.
- Actualizar el estado de una tarea existente.
- Conservar tareas y cambios entre cargas de la aplicación mediante `localStorage`.
- Manejar el almacenamiento vacío y el error de lectura descrito por HU-0005.
- Verificar el comportamiento con base en los criterios de aceptación y reglas de negocio de las historias seleccionadas.

No se incorporan historias ni funcionalidades de otros sprints.

## 3. Documentos de referencia

- `SPEC-000-foundation.md`
- `HU-0001-CrearTarea.md`
- `HU-0002-ConsultarTarea.md`
- `HU-0003-ActualizarTarea.md`
- `HU-0005-ConservarTarea.md`

**Nota de trazabilidad:** los nombres de archivo usan identificadores de cuatro dígitos (`HU-0001`), mientras que los encabezados internos de las historias usan tres (`HU-001`). Se recomienda uniformar la identificación documental sin cambiar el contenido funcional aprobado.

## 4. Restricciones técnicas

- HTML5, CSS3 y JavaScript ES Modules.
- Sin backend, API propia ni base de datos.
- Persistencia local mediante `localStorage`.
- Ejecución local en VSCode mediante un servidor HTTP estático; no depender de abrir el HTML como `file://`.
- Control de versiones con Git.
- El código fuente deberá permanecer organizado dentro de `src/`, de acuerdo con SPEC-000.
- **Pendiente de decisión D1:** SPEC-000 prohíbe frameworks/librerías de frontend, pero el contexto del Sprint solicita TailwindCSS por CDN. No se elige una opción hasta que se apruebe una resolución explícita.

## 5. Contratos funcionales propuestos

### F-001 — Datos de una tarea

Cada tarea deberá contener los datos necesarios para satisfacer las historias aprobadas:

- `id`: identificador único (RN-006 de HU-0001).
- `title`: título de la tarea.
- `description`: descripción opcional.
- `status`: uno de los tres estados válidos aprobados.
- `createdAt`: fecha de creación (RN-007 de HU-0001).
- `updatedAt`: fecha y hora de la última modificación de estado (RN-003 de HU-0003).

La representación exacta del identificador y de las fechas es una decisión técnica que deberá documentarse antes de implementar. Como opción técnica para revisión, se propone un identificador generado en el navegador y fechas almacenadas en formato ISO 8601.

### F-002 — Crear una tarea

- El título es obligatorio y debe tener entre 3 y 80 caracteres, inclusive.
- La descripción es opcional y no debe superar 300 caracteres.
- Si los datos no cumplen las reglas, la tarea no deberá crearse y la interfaz informará la validación correspondiente.
- Toda tarea nueva iniciará en el estado inicial aprobado, actualmente descrito como `Pendiente` en las historias.
- Cada tarea tendrá un identificador único y fecha de creación.
- La creación deberá persistirse de acuerdo con RN-001 de HU-0005.

### F-003 — Consultar el listado

- Se mostrarán todas las tareas registradas.
- Cada elemento mostrará, como mínimo, identificador, título, estado y fecha de registro, conforme a CA-001 de HU-0002.
- El orden predeterminado será cronológico descendente por fecha de creación (RN-001 de HU-0002).
- Si no existen tareas, se mostrará un mensaje que explique que aún no hay tareas registradas.
- Consultar no modificará los datos ni el estado de las tareas.

### F-004 — Consultar el detalle

- Al seleccionar una tarea, se mostrará su detalle.
- La descripción se mostrará cuando exista; si fue omitida durante la creación, el detalle deberá seguir siendo consultable.

### F-005 — Actualizar el estado

- Solo se aceptarán los tres estados válidos una vez que se resuelva D2.
- Los cambios entre estados válidos deberán respetar RN-002 de HU-0003, que permite transicionar libremente entre ellos.
- Un valor fuera del catálogo aprobado deberá rechazarse sin modificar el estado anterior.
- Cada cambio de estado válido actualizará la fecha y hora de modificación.
- Los cambios confirmados deberán persistirse y estar disponibles en consultas posteriores.

**Pendiente de decisión D2:** el contexto del Sprint enumera `Pendiente`, `En Curso` y `terminada`; HU-0003 enumera `Pendiente`, `En progreso` y `Completada`. No se normalizarán nombres ni valores almacenados hasta aprobar un único catálogo.

### F-006 — Persistencia con `localStorage`

- Al iniciar, la aplicación leerá las tareas guardadas y las pondrá disponibles para consulta.
- Si todavía no hay datos almacenados, se inicializará un estado vacío sin provocar errores.
- Las operaciones de creación y cambio de estado se guardarán inmediatamente, según RN-001 de HU-0005.
- Los datos guardados deberán recuperarse después de recargar, cerrar y volver a abrir la aplicación desde el mismo origen y perfil del navegador, siempre que el almacenamiento no haya sido borrado o perdido externamente.
- No se promete sincronización entre navegadores, perfiles, dispositivos o usuarios.

### F-007 — Error al leer el almacenamiento

- Si ocurre un error de lectura, la aplicación notificará la incidencia.
- No deberá sobrescribir datos preexistentes cuando no pueda leerlos correctamente, según RN-002 de HU-0005.
- HU-0005 no define un criterio de aceptación específico para este caso; se requiere decidir si se amplía la historia con un criterio verificable o si se conservará como regla trazada en esta especificación.
- El comportamiento ante un error de escritura de `localStorage` no está especificado en las historias y no se ampliará unilateralmente en este borrador.

## 6. Decisiones que deben resolverse antes de implementar

- **D1 — TailwindCSS:** confirmar si se permite como excepción y se actualiza SPEC-000, o si se mantiene la prohibición de frameworks y se usa CSS3 convencional.
- **D2 — Catálogo de estados:** aprobar los nombres exactos y consistentes de los tres estados.
- **D3 — Descripción:** confirmar que es opcional, tal como establecen CA-005 y RN-003 de HU-0001, pese a la redacción de la historia.
- **D4 — Errores de almacenamiento:** confirmar cómo se verifica RN-002 de HU-0005 y si se añadirá un criterio de aceptación. El comportamiento ante un fallo de escritura queda igualmente sin definir.
- **D5 — Convención técnica de ID y fechas:** aprobar la representación del identificador y el formato de persistencia de las fechas para garantizar consistencia entre creación, ordenamiento y actualización.

## 7. Matriz de trazabilidad HU → CA → SPEC

| Historia | Criterio de aceptación | Elemento de SPEC-001 | Cobertura / observación |
|---|---|---|---|
| HU-0001 | CA-001 — Crear correctamente | F-001, F-002 | Tarea creada con título válido e inicia en el estado inicial aprobado. |
| HU-0001 | CA-002 — Título obligatorio | F-002 | Rechaza el título ausente e informa la validación. |
| HU-0001 | CA-003 — Longitud mínima del título | F-002 | Rechaza títulos con menos de 3 caracteres. |
| HU-0001 | CA-004 — Longitud máxima del título | F-002 | Rechaza títulos con más de 80 caracteres. |
| HU-0001 | CA-005 — Descripción opcional | F-002, D3 | Debe permitirse crear sin descripción; confirmar discrepancia de redacción. |
| HU-0001 | CA-006 — Descripción demasiado extensa | F-002 | Rechaza descripciones de más de 300 caracteres. |
| HU-0002 | CA-001 — Consulta con tareas existentes | F-001, F-003 | Lista identificador, título, estado y fecha de registro. |
| HU-0002 | CA-002 — Consulta sin registros previos | F-003 | Muestra mensaje informativo en lugar de una lista vacía sin contexto. |
| HU-0002 | CA-003 — Visualización de detalle | F-004 | Muestra el detalle y la descripción si existe. |
| HU-0003 | CA-001 — Cambio de estado válido | F-005, F-006 | Cambia el estado y actualiza la fecha de modificación; los nombres dependen de D2. |
| HU-0003 | CA-002 — Transición a completada | F-005, F-006 | Refleja y conserva el último estado en consultas posteriores. |
| HU-0003 | CA-003 — Selección de estado inválido | F-005 | Rechaza valores ajenos al catálogo y conserva el estado previo. |
| HU-0005 | CA-001 — Recuperación de datos al iniciar | F-006 | Recupera las tareas guardadas entre cargas de la aplicación. |
| HU-0005 | CA-002 — Persistencia tras modificaciones | F-006 | Conserva el último estado después de recargar o volver a abrir. |
| HU-0005 | CA-003 — Almacenamiento vacío | F-006 | Inicializa sin errores cuando todavía no existen datos guardados. |
| HU-0005 | RN-002 — Error de lectura | F-007 | La regla existe, pero no tiene CA específico; pendiente D4. |
| HU-0003 | RN-002 — Transición libre entre estados válidos | F-005 | La regla cubre transiciones entre estados válidos, pero los CA solo ejemplifican dos pasos consecutivos. Debe verificarse la regla completa sin cambiarla. |
| HU-0001 | RN-006 y RN-007 — ID único y fecha de creación | F-001, F-002 | Deben generarse y poder consultarse; la representación técnica queda sujeta a D5. |
| HU-0003 | RN-003 — Fecha de modificación | F-005 | Debe actualizarse cuando se modifica el estado. |
| HU-0005 | RN-001 — Persistencia inmediata de creación y actualización | F-002, F-006 | Incluye la persistencia tras crear, además de actualizar el estado. |

## 8. Tareas técnicas propuestas

| ID | Tarea | Historias relacionadas | Dependencias |
|---|---|---|---|
| TT-01 | Resolver D1–D5 y registrar las decisiones aprobadas en la especificación. | Todas | Ninguna; bloquea la implementación de los puntos afectados. |
| TT-02 | Definir el contrato de datos de una tarea: identificador, título, descripción, estado y fechas. | HU-0001, HU-0002, HU-0003, HU-0005 | TT-01 para las decisiones abiertas. |
| TT-03 | Preparar la lectura e inicialización del almacenamiento local, incluyendo almacenamiento vacío y el tratamiento acordado del error de lectura. | HU-0005 | TT-01, TT-02. |
| TT-04 | Implementar la validación y creación de tareas: título obligatorio, límites de longitud, descripción opcional, estado inicial, identificador y fecha de creación. | HU-0001 | TT-02, TT-03 para guardar inmediatamente. |
| TT-05 | Implementar la consulta del listado, el orden cronológico descendente y el mensaje de lista vacía. | HU-0002 | TT-02, TT-03. |
| TT-06 | Implementar la consulta del detalle y mostrar la descripción cuando exista. | HU-0002 | TT-05. |
| TT-07 | Implementar el cambio de estado, rechazo de estados no válidos, actualización de fecha y persistencia. | HU-0003, HU-0005 | TT-01, TT-02, TT-03, TT-05. |
| TT-08 | Integrar el flujo completo de crear → consultar → actualizar → recargar y recuperar datos. | HU-0001, HU-0002, HU-0003, HU-0005 | TT-04–TT-07. |
| TT-09 | Verificar cada CA y las reglas de negocio trazadas; registrar resultados sin afirmar pruebas no ejecutadas. | Todas | TT-08. |
| TT-10 | Actualizar las instrucciones de ejecución y registrar cambios coherentes en Git. | Todas | Según los cambios aprobados. |

## 9. Definition of Done propuesta para Sprint 1

- Cada criterio de aceptación de las cuatro historias tiene trazabilidad a uno o más elementos de SPEC-001.
- Las tareas incluidas en el Sprint 1 cumplen los criterios y reglas de negocio aprobados.
- Crear y cambiar el estado persiste inmediatamente y los datos se recuperan tras recargar o volver a abrir la aplicación.
- La lista se ordena por fecha de creación descendente; el detalle y el estado reflejan los datos guardados.
- Los escenarios de datos vacíos, validación y estados inválidos están verificados.
- El tratamiento de error de lectura se verifica de acuerdo con la decisión D4.
- La aplicación se ejecuta localmente desde VSCode mediante un servidor HTTP estático y respeta las restricciones técnicas aprobadas.
- La trazabilidad y las instrucciones de ejecución están actualizadas en el repositorio.

## 10. Fuera de alcance

Se excluye de esta especificación cualquier funcionalidad no incluida en HU-0001, HU-0002, HU-0003 y HU-0005. En particular, no se incorporan asignaciones, fechas límite, prioridades, categorías, subtareas, archivos adjuntos, notificaciones, paginación avanzada, búsqueda predictiva, exportación, autenticación, roles, sincronización en la nube, backend ni base de datos.

---

**Aprobación:** aprobado como línea base de especificación del Sprint 1. Las historias validadas no se modifican; las decisiones abiertas D1–D5 deben resolverse antes de implementar los puntos afectados. El alcance queda limitado a HU-0001, HU-0002, HU-0003 y HU-0005; no autoriza funcionalidades del Sprint 2.
