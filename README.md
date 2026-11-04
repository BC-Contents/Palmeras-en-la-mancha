# Proyecto Full-Stack en equipo: Palmeras en la Mancha Records

¡Ha llegado el momento de construir en equipo una solución Full-Stack profesional y moderna!

En este proyecto grupal vais a diseñar e implementar conjuntamente tanto el **backend** (API REST en FastAPI) como la **interfaz web cliente** (HTML, CSS/Tailwind, JS Vanilla y Axios) para gestionar el catálogo, las ediciones y las filiales de la tienda de discos **Palmeras en la Mancha Records**.

La aplicación contará con funcionalidad completa en ambos lados (Frontend y Backend) para realizar operaciones CRUD sobre un modelo de datos relacional que implementa tanto relaciones **1:N (One-to-Many)** como **N:M (Many-to-Many)**, utilizando nomenclatura en inglés para las entidades y tablas del modelo.

Vuestro proyecto explicará la arquitectura backend diseñada, cómo se gestiona la integridad referencial en la base de datos, la estructura de las peticiones HTTP y cómo se devuelven las respuestas en formato JSON mediante una arquitectura cliente-servidor real.

> **Importante:** el proyecto es **obligatorio en equipo**. El desarrollo backend debe implementar explícitamente las entidades en inglés:
> - `record_labels` (1:N con `albums`)
> - `albums`
> - `formats` (N:M con `albums` mediante la tabla intermedia `album_formats` con `price` y `stock`)
> - `branches`

---

## Estructura del trabajo

Trabajaréis en equipo dividiendo el desarrollo en dos partes:

### Parte 1. Servidor Backend & Modelo Relacional (FastAPI)

Diseñaréis el Diagrama Entidad-Relación (DER) en inglés, crearéis la API con FastAPI, la validación de esquemas con Pydantic, la persistencia en base de datos relacional (SQLite o PostgreSQL mediante SQLAlchemy/SQLModel) definiendo las relaciones 1:N y N:M (con tabla intermedia `album_formats`), los endpoints de filtrado avanzado y las operaciones CRUD.

### Parte 2. Cliente Web Frontend & Documentación (Axios + Tailwind)

Construiréis el portal de documentación de la API, conectaréis el cliente mediante JavaScript y Axios, diseñaréis la interfaz interactiva (con Tailwind CSS u otras librerías) para probar las operaciones CRUD, el módulo de búsqueda y filtros combinados en tiempo real, y adaptaréis la web a dispositivos móviles (Responsive).

---

## Metodologías Ágiles en Equipo

Organizaréis el trabajo del equipo mediante metodologías ágiles:

- **Historias de Usuario:** redacción de las Historias de Usuario principales del sistema (tanto para el backend como para el frontend), definiendo claramente sus **Criterios de Aceptación** y descomponiéndolas en tareas técnicas asignadas a cada integrante.
- **Gestión del Proyecto:** creación y seguimiento activo de un **tablero Kanban** (GitHub Projects, Trello o Jira) con backlog de tareas (*Por hacer, En proceso, En revisión y Hecho*).
- **Gitflow Grupal:** uso obligatorio de ramas por funcionalidad (`feature/`) y resolución de conflictos mediante **Pull Requests** revisadas entre compañeros/as.

---

## Parte 1. Servidor Backend & Modelo Relacional (FastAPI)

**Objetivo:** diseñar la arquitectura de la base de datos relacional con estructuras 1:N y N:M en inglés y construir el servidor backend con FastAPI para gestionar las entidades vinculadas, sus operaciones CRUD y los filtros de búsqueda.

### Requisitos funcionales

| Código | Requisito | Descripción |
|--------|-----------|-------------|
| **RF1** | Backend con FastAPI | Desarrollo obligatorio del servidor utilizando el framework FastAPI en Python. |
| **RF2** | Modelo relacional dual (nomenclatura en inglés) | Diseñar e implementar las entidades `record_labels`, `albums`, `formats`, `album_formats` (tabla intermedia N:M con `price` y `stock`) y `branches`. |
| **RF3** | Persistencia con ORM | Gestión de la base de datos relacional (SQLite o PostgreSQL) mediante un ORM como SQLAlchemy o SQLModel, configurando adecuadamente las relaciones entre modelos. |
| **RF4** | Validación de datos (Pydantic) | Definición de esquemas Pydantic para validar los datos de entrada/salida y representar adecuadamente las relaciones 1:N y N:M. |
| **RF5** | Endpoints de filtrado avanzado (Query Parameters) | Implementar en `GET /albums` la capacidad de filtrar el catálogo combinando parámetros por título/artista (`title`, `artist`), discográfica (`label_id`), formato físico (`format_id`) y filial (`branch_id`). |
| **RF6** | Operaciones CRUD relacionales | Endpoints `POST`, `GET`, `PUT/PATCH` y `DELETE` para crear, consultar, modificar y eliminar registros gestionando adecuadamente la integridad referencial. |
| **RF7** | Respuestas HTTP & CORS | Configuración del middleware de CORS (`CORSMiddleware`) para permitir peticiones desde el cliente web y uso de códigos HTTP semánticos (200, 201, 400, 404, 422, 500). |
| **RF8** | Control de errores | Manejo explícito de excepciones mediante `HTTPException` para notificar errores de validación, claves foráneas inexistentes o fallos de base de datos. |

---

## Parte 2. Cliente Web Frontend & Documentación (Axios)

**Objetivo:** desarrollar la aplicación web cliente (HTML, CSS/Tailwind CSS, JavaScript Vanilla y Axios) que sirva como portal de documentación y demostración interactiva para consumir la API y gestionar el catálogo de Palmeras en la Mancha Records.

### Requisitos funcionales

| Código | Requisito | Descripción |
|--------|-----------|-------------|
| **R1** | Portal de documentación web | Página principal en HTML/CSS que explique el propósito de la API, muestre el modelo de datos relacional, los endpoints disponibles, sus parámetros de entrada/salida, ejemplos de peticiones JSON y el enlace a Swagger (`/docs`). |
| **R2** | Estilos y librerías CSS | Se permite e incentiva el uso de librerías CSS como Tailwind CSS, Bootstrap o Bulma para agilizar el diseño de la interfaz. |
| **R3** | Consumo asíncrono con Axios | Conectar la interfaz web con el servidor FastAPI utilizando la librería Axios para realizar todas las peticiones HTTP. |
| **R4** | Gestión interactiva de datos (CRUD completo en la web) | Formularios e interfaces que permitan crear nuevos álbumes (eligiendo la discográfica en un selector 1:N y los formatos con precio/stock en la relación N:M), listar elementos, modificar datos y eliminarlos. |
| **R5** | Módulo completo de búsqueda y filtros | Panel visual interactivo con barra de búsqueda y desplegables para filtrar el catálogo en tiempo real mediante Axios (por título/artista, discográfica, formato y filial). |
| **R6** | Layout Responsive (Mobile First) & feedback visual | Estructura adaptable a pantallas móviles con HTML semántico, notificaciones visuales de éxito/error y estados de "Cargando..." durante las peticiones asíncronas. |

### Benchmarks y Recursos de Referencia

Para el análisis de mercado, la maquetación visual y la experiencia de usuario (UX/UI) del catálogo y la tienda de vinilos, utilizad los siguientes sitios web como recursos y benchmarks de inspiración:

- **Vetusta Morla (Tienda Oficial):** [https://www.vetustamorla.com/tienda/](https://www.vetustamorla.com/tienda/) — Referencia en presentación de lanzamientos discográficos, merchandising oficial y estética de bandas.
- **Revólver Records:** [https://www.revolverrecords.es/](https://www.revolverrecords.es/) — Tienda especializada en vinilos, coleccionismo, ediciones especiales y organización de catálogo por géneros musicales.
- **Marilians Records:** [https://www.marilians.com/](https://www.marilians.com/) — Tienda de discos independiente con un catálogo moderno, fichas de producto detalladas y filtrado ágil de novedades.
- **Awwwards - Empire:** [https://www.awwwards.com/sites/empire](https://www.awwwards.com/sites/empire) — Referente de diseño web de vanguardia, tipografía editorial audaz, animaciones e interactividad visual premiada.

---

## Extras Opcionales

- **Integración con Cloudinary:** integrar el SDK de Cloudinary en Python (`cloudinary`) mediante `UploadFile` de FastAPI para permitir la subida directa de portadas desde el frontend (`<input type="file">` mediante `FormData`), guardando la URL pública generada en la base de datos.
- **Suite de Tests con Pytest:** pruebas unitarias e integración para validar los endpoints de la API usando `pytest`. Cobertura de código testeando las operaciones CRUD, filtros combinados y la integridad referencial.

---

## Entregables del Equipo

1. **Presentación Grupal (15 min):** exposición oral del equipo demostrando la organización en Git/Kanban, las Historias de Usuario desarrolladas, la arquitectura del DER en inglés, el catálogo estilizado con el sistema de filtros y la demo en vivo del sistema cliente-servidor.
2. **Diseño y Planificación:** prototipo visual en Stitch/Figma, Diagrama Entidad-Relación (DER) de la base de datos y evidencias de gestión ágil grupal (tablero Kanban y reparto de tareas).
3. **Diagramas Técnicos:** diagrama de flujo de la aplicación y diagrama de arquitectura/rutas de la API REST.
4. **Repositorio GitHub Grupal:** código fuente completo (Frontend + Backend) en un repositorio público con historial de commits de todos los miembros (siguiendo Gitflow) y un archivo `README.md` detallado que incluya:
   - Descripción y tecnologías.
   - Guía de instalación local.
   - Configuración de variables de entorno.
   - Diagrama DER.
   - Comandos de ejecución.
   - Documentación de endpoints con query parameters.
5. **Subida a producción** de backend y frontend.

---

## Normas para el uso de la Inteligencia Artificial (IA)

Podéis utilizar herramientas de IA como apoyo para resolver dudas puntuales o consultar sintaxis durante el trabajo en equipo, pero el objetivo es que **todo el grupo comprenda y sepa defender el código desarrollado**.

### ✅ Usos permitidos

- Consultar sobre la sintaxis de FastAPI, modelos Pydantic, relaciones en SQLAlchemy/SQLModel o uso de Axios.
- Pedir ayuda para interpretar errores de consola, fallos en claves foráneas o excepciones en la terminal.
- Consultar cómo estructurar la definición de Historias de Usuario o Criterios de Aceptación.
- Pedir ejemplos concretos de manipulación del DOM, formularios HTML con selectores de relaciones o diseño responsive con CSS/Tailwind.
- Consultar buenas prácticas sobre la organización del repositorio y la resolución de conflictos en Git.

### ❌ Usos no permitidos

- Pedir a la IA que genere todo el backend en FastAPI, el esquema de la base de datos o la interfaz web completa del grupo.
- Copiar y pegar código de rutas, relaciones de base de datos o llamadas asíncronas sin que el equipo entienda su funcionamiento.
- Pedir que la IA resuelva la lógica completa del proyecto en lugar del trabajo colaborativo de las integrantes.
- Presentar como propio un código grupal que ningún miembro del equipo sea capaz de explicar o depurar durante la exposición.

> **Regla principal:** la IA puede actuar como un apoyo de aprendizaje para el equipo, pero **no puede realizar el proyecto por vosotras**. Todas las integrantes del grupo deben ser capaces de explicar la estructura del código, las Historias de Usuario implementadas, cómo se conectan las tablas mediante relaciones y cómo interactúa el cliente Axios con el servidor FastAPI. El objetivo es demostrar capacidad de trabajo en equipo y dominio técnico en el desarrollo Full-Stack.
