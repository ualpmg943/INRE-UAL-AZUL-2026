| **INF-001** | **Usuario** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R (Visual Paradigm) |
| **Referencias** | <ul><li>Gestión de Usuarios</li><li>Autenticación en el sistema</li></ul> |
| **Descripción** | Representa a los usuarios registrados en el sistema. |
| **Datos específicos** | <ul><li>id_usuario INT (PK)</li><li>nombre VARCHAR(255)</li><li>AuthIdAuth INT (FK a Auth)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Es la entidad central para relacionar roles, noticias, eventos y logs. |

---

| **INF-002** | **Auth** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Login / Logout</li><li>Gestión de sesiones</li></ul> |
| **Descripción** | Almacena las credenciales y tokens de sesión de los usuarios. |
| **Datos específicos** | <ul><li>idAuth INT (PK)</li><li>token INT</li><li>tokenRen INT</li><li>tiempo_expiracion INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Separado de la tabla Usuario por seguridad de datos sensibles. |

---

| **INF-003** | **Rol** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Gestión de permisos</li></ul> |
| **Descripción** | Define los tipos de roles disponibles (Administrador, Ciudadano, Gestor). |
| **Datos específicos** | <ul><li>id_rol INT (PK)</li><li>nombre VARCHAR(255)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Permite escalar el sistema de permisos basado en perfiles. |

---

| **INF-004** | **UsuarioRol** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Asignación de roles</li></ul> |
| **Descripción** | Tabla intermedia para la relación N:M entre Usuarios y Roles. |
| **Datos específicos** | <ul><li>Usuarioid_usuario INT (FK)</li><li>RolidRol INT (FK)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Permite que un usuario posea múltiples funciones dentro del portal. |

---

| **INF-005** | **LogOperacion** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Auditoría del sistema</li></ul> |
| **Descripción** | Registra las acciones CRUD realizadas por los usuarios. |
| **Datos específicos** | <ul><li>id_log INT (PK)</li><li>entidad_modificada VARCHAR(255)</li><li>id_entidad_modificada INT</li><li>tipo_operacion VARCHAR(255)</li><li>fecha_hora TIMESTAMP</li><li>detalle_cambio VARCHAR(255)</li><li>Usuarioid_usuario INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Fundamental para la trazabilidad y seguridad legal del sistema. |

---

| **INF-006** | **Evento** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Publicación de eventos culturales</li><li>Consultar Agenda</li></ul> |
| **Descripción** | Almacena la información principal de los eventos de la ciudad. |
| **Datos específicos** | <ul><li>id_evento INT (PK)</li><li>titulo VARCHAR(255)</li><li>sinopsis VARCHAR(255)</li><li>fecha_hora_inicio TIME</li><li>fecha_hora_fin TIME</li><li>es_pago BIT</li><li>url_pasarela_pago VARCHAR(255)</li><li>url_organizador VARCHAR(255)</li><li>estado VARCHAR(255)</li><li>Usuarioid_usuario INT (FK)</li><li>Categoriaid_categoria INT (FK)</li><li>RecursoTuristicoid_recurso INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Posee enlaces a portal, fotos y categorías para su clasificación. |

---

| **INF-007** | **Portal** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Configuración del Frontend</li></ul> |
| **Descripción** | Define los diferentes portales web vinculados a la base de datos. |
| **Datos específicos** | <ul><li>id_portal INT (PK)</li><li>nombre VARCHAR(255)</li><li>url VARCHAR(255)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Permite gestionar múltiples sitios desde un único back-end. |

---

| **INF-008** | **EventoPortal** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Distribución de contenidos por portal</li></ul> |
| **Descripción** | Tabla intermedia que vincula eventos con portales específicos. |
| **Datos específicos** | <ul><li>Portalid_portal INT (FK)</li><li>Eventoid_evento INT (FK)</li><li>orden INT</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Permite decidir qué eventos aparecen en qué URL y en qué orden. |

---

| **INF-009** | **Categoria** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Taxonomía del sistema</li></ul> |
| **Descripción** | Clasificación transversal recursiva (categorías y subcategorías). |
| **Datos específicos** | <ul><li>id_categoria INT (PK)</li><li>nombre VARCHAR(255)</li><li>texto VARCHAR(255)</li><li>orden VARCHAR(255)</li><li>Categoriaid_categoria INT (FK recursiva)</li><li>Usuarioid_usuario INT (FK Creador)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Clasifica eventos, incidencias, anuncios y archivos. |

---

| **INF-010** | **IncidenciaCiudadana** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Reporte de daños</li><li>Seguimiento de reparaciones</li></ul> |
| **Descripción** | Reportes de ciudadanos sobre mobiliario o servicios públicos. |
| **Datos específicos** | <ul><li>id_incidencia INT (PK)</li><li>descripcion VARCHAR(255)</li><li>ubicacion_texto VARCHAR(255)</li><li>latitud DOUBLE</li><li>longitud DOUBLE</li><li>nombre_contacto VARCHAR(255)</li><li>email_contacto VARCHAR(255)</li><li>estado VARCHAR(255)</li><li>fecha_creacion TIME</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Incluye datos de contacto y GPS para localización exacta del reporte. |

---

| **INF-011** | **RecursoTuristico** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Mapa turístico</li></ul> |
| **Descripción** | Información de monumentos, parques y puntos de interés. |
| **Datos específicos** | <ul><li>id_recurso INT (PK)</li><li>nombre VARCHAR(255)</li><li>descripcion VARCHAR(255)</li><li>direccion VARCHAR(255)</li><li>latitud DOUBLE</li><li>longitud DOUBLE</li><li>horario VARCHAR(255)</li><li>url_tour_virtual VARCHAR(255)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Vinculado a categorías turísticas para filtrado en la app/web. |

---

| **INF-012** | **Asociacion** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Registro de Asociaciones</li></ul> |
| **Descripción** | Entidades vecinales o culturales que solicitan espacios municipales. |
| **Datos específicos** | <ul><li>id_asociacion INT (PK)</li><li>nombre VARCHAR(255)</li><li>descripcion VARCHAR(255)</li><li>aforo INT</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Fundamental para controlar quién realiza la reserva de locales públicos. |

---

| **INF-013** | **EspacioReservable** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Inventario de centros municipales</li></ul> |
| **Descripción** | Salas, centros o recintos disponibles para reserva. |
| **Datos específicos** | <ul><li>id_espacio INT (PK)</li><li>nombre VARCHAR(255)</li><li>descripcion VARCHAR(255)</li><li>aforo INT</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Define la capacidad máxima para contrastar con el aforo de la asociación. |

---

| **INF-014** | **Reserva** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Gestión de alquileres</li></ul> |
| **Descripción** | Gestiona el calendario de uso de los espacios reservables. |
| **Datos específicos** | <ul><li>id_reserva INT (PK)</li><li>fecha_hora_inicio TIME</li><li>fecha_hora_fin TIME</li><li>estado VARCHAR(255)</li><li>motivo_rechazo VARCHAR(255)</li><li>fecha_solicitud VARCHAR(255)</li><li>Asociacionid_asociacion INT (FK)</li><li>EspacioReservableid_reserva INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Controla el flujo de aprobación y disponibilidad horaria. |

---

| **INF-015** | **Foto** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Repositorio Multimedia</li></ul> |
| **Descripción** | Entidad central para el almacenamiento de rutas de imágenes. |
| **Datos específicos** | <ul><li>id_foto INT (PK)</li><li>nombre VARCHAR(255)</li><li>ruta VARCHAR(255)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Vinculado a eventos, noticias e incidencias mediante tablas intermedias. |

---

| **INF-016** | **Noticia** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Publicación de boletines</li></ul> |
| **Descripción** | Artículos de actualidad municipal. |
| **Datos específicos** | <ul><li>id_noticia INT (PK)</li><li>texto VARCHAR(255)</li><li>Usuarioid_usuario INT (FK Autor)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Posee galería de fotos asociada (NoticiaFoto). |

---

| **INF-017** | **Anuncio** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Tablón de anuncios</li></ul> |
| **Descripción** | Comunicaciones breves de ciudadanos o la administración. |
| **Datos específicos** | <ul><li>id_anuncio INT (PK)</li><li>texto VARCHAR(255)</li><li>desc VARCHAR(255)</li><li>Usuarioid_usuario INT (FK)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Clasificado por categorías. |

---

| **INF-018** | **RRSS** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Social Media Feed</li></ul> |
| **Descripción** | Almacena enlaces a redes sociales vinculados a eventos o noticias. |
| **Datos específicos** | <ul><li>id_RRSS INT (PK)</li><li>URL VARCHAR(255)</li><li>texto VARCHAR(255)</li><li>Noticiaid_noticia INT (FK)</li><li>Eventoid_evento INT (FK)</li><li>Anuncioid_anuncio INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Permite rastrear la repercusión social del contenido. |

---

| **INF-019** | **Formulario** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Generador de Forms</li></ul> |
| **Descripción** | Define la cabecera de formularios de captura de datos dinámicos. |
| **Datos específicos** | <ul><li>id_formulario INT (PK)</li><li>nombre VARCHAR(255)</li><li>PostURL VARCHAR(255)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Estructura para crear trámites online sin cambiar el código. |

---

| **INF-020** | **Campos** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Definición de inputs</li></ul> |
| **Descripción** | Define los campos individuales, su tipo y posición en un formulario. |
| **Datos específicos** | <ul><li>id_campos INT (PK)</li><li>tipo VARCHAR(255)</li><li>orden INT</li><li>PosX INT</li><li>PosY INT</li><li>Formularioid_formulario INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Permite el diseño visual de formularios desde la base de datos. |

---

| **INF-021** | **Area** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Organización departamental</li></ul> |
| **Descripción** | Define las áreas o departamentos (con icono y color para UI). |
| **Datos específicos** | <ul><li>id_area INT (PK)</li><li>nombre VARCHAR(255)</li><li>icono VARCHAR(255)</li><li>ordenamiento VARCHAR(255)</li><li>color VARCHAR(255)</li><li>Usuarioid_usuario INT (FK)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Entidad nueva detectada en el diagrama. |

---

| **INF-022** | **Archivo** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Gestión documental</li></ul> |
| **Descripción** | Almacena archivos generales asociados a categorías. |
| **Datos específicos** | <ul><li>nombre VARCHAR(255)</li><li>ruta VARCHAR(255)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Entidad nueva detectada en el diagrama. |

---

| **INF-023** | **UsuarioNoticia** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Relación Usuario-Noticia</li></ul> |
| **Descripción** | Tabla intermedia para vincular usuarios con noticias. |
| **Datos específicos** | <ul><li>Usuarioid_usuario INT (FK)</li><li>Noticiaid_noticia INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Tabla intermedia detectada en el diagrama. |

---

| **INF-024** | **EventoFoto** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Galería de eventos</li></ul> |
| **Descripción** | Vincula múltiples fotos a un evento específico. |
| **Datos específicos** | <ul><li>orden INT</li><li>Eventoid_evento INT (FK)</li><li>Fotoid_foto INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Tabla intermedia detectada en el diagrama. |

---

| **INF-025** | **NoticiaFoto** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Galería de noticias</li></ul> |
| **Descripción** | Vincula múltiples fotos a una noticia específica. |
| **Datos específicos** | <ul><li>orden VARCHAR(255)</li><li>Noticiaid_noticia INT (FK)</li><li>Fotoid_foto INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Tabla intermedia detectada en el diagrama. |

---

| **INF-026** | **IncidenciaFoto** |
| :--- | :--- |
| **Versión** | 1.1 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Pruebas gráficas de incidencias</li></ul> |
| **Descripción** | Vincula fotos a un reporte de incidencia ciudadana. |
| **Datos específicos** | <ul><li>Fotoid_foto INT (FK)</li><li>IncidenciaCiudadanaid_incidencia INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Tabla intermedia detectada en el diagrama. |
