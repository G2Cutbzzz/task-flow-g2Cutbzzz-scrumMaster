# SPEC-000 — Foundation

## Propósito

Definir la base técnica y las convenciones iniciales de **TaskFlow Lite**, estableciendo una estructura mínima, consistente y mantenible para comenzar el desarrollo incremental del producto sin implementar todavía funcionalidades relacionadas con las historias de usuario.

## Alcance

Esta especificación establece:

* La estructura inicial de archivos y carpetas del proyecto.
* Las tecnologías y restricciones técnicas que deberán respetarse.
* Las convenciones básicas de organización del código.
* Las convenciones iniciales para el uso de Git.
* La Definition of Done técnica para esta etapa de fundación.
* Los elementos que quedan explícitamente fuera de alcance.

Esta etapa **no implementa funcionalidades de gestión de tareas**.

## Estructura inicial del proyecto

La estructura propuesta para la fundación es:

```text
TaskFlow-Lite/
├── src/
│   ├── css/
│   │   └── styles.css
│   ├── js/
│   │   └── main.js
│   └── index.html
├── .gitignore
└── README.md
```

### Responsabilidad de los elementos

* `src/index.html`: documento HTML principal de la aplicación.
* `src/css/`: hojas de estilo CSS del proyecto.
* `src/js/`: módulos JavaScript de la aplicación.
* `.gitignore`: archivos y directorios que no deberán versionarse.
* `README.md`: información básica para identificar, ejecutar y mantener el proyecto.

La estructura podrá crecer conforme se incorporen funcionalidades, manteniendo la separación entre HTML, CSS y JavaScript.

## Restricciones técnicas

1. El proyecto utilizará exclusivamente **HTML5, CSS3 y JavaScript con ES Modules**.
2. No se utilizarán frameworks o librerías de frontend.
3. No existirá backend ni API propia para esta etapa.
4. La persistencia de información se contemplará posteriormente mediante **localStorage**.
5. El proyecto deberá poder ejecutarse localmente utilizando **VSCode** y un entorno de servidor estático local.
6. El código fuente deberá mantenerse dentro de `src/`.
7. JavaScript deberá organizarse mediante módulos para favorecer separación de responsabilidades y mantenimiento.
8. No se implementarán todavía historias funcionales ni reglas de negocio de las tareas.
9. No se establecerán dependencias técnicas que no sean necesarias para cumplir esta fundación.

## Convenciones de Git

Se utilizará Git como sistema de control de versiones.

### Ramas

La rama principal del proyecto será:

* `main`: versión estable del proyecto.

Las modificaciones de trabajo deberán realizarse en ramas independientes siguiendo una convención descriptiva, por ejemplo:

* `feature/<nombre>`
* `fix/<nombre>`
* `docs/<nombre>`

### Commits

Los commits deberán:

* Representar un cambio concreto y coherente.
* Utilizar mensajes claros y breves.
* Describir principalmente qué cambio se realizó.
* Evitar mezclar cambios no relacionados en un mismo commit.

La especificación inicial deberá quedar registrada mediante un commit independiente de documentación.

## Definition of Done técnica inicial

La fundación se considerará terminada cuando:

* La estructura inicial del proyecto exista y sea coherente con esta especificación.
* HTML5, CSS3 y JavaScript ES Modules estén establecidos como tecnologías base.
* No existan frameworks ni backend en esta etapa.
* Los archivos fuente estén organizados dentro de `src/`.
* Git esté inicializado y `.gitignore` esté configurado.
* El proyecto pueda abrirse y ejecutarse localmente desde VSCode mediante un servidor estático local.
* El proyecto tenga un `README.md` con las instrucciones mínimas de ejecución.
* La especificación `SPEC-000-foundation.md` esté registrada en el repositorio.
* No se hayan agregado historias funcionales ni funcionalidades de gestión de tareas.

## Fuera de alcance

Queda fuera de esta especificación:

* Registro, edición o eliminación de tareas.
* Visualización funcional de tareas.
* Actualización de estados de tareas.
* Filtros, búsqueda o clasificación de tareas.
* Implementación de `localStorage`.
* Usuarios, autenticación o roles.
* Backend, API o base de datos.
* Integraciones con servicios externos.
* Frameworks o librerías de frontend.
* Historias de usuario y criterios de aceptación.
* Diseño funcional definitivo de las pantallas.
* Pruebas funcionales de las capacidades del producto.
