## **PROYECTO INRE EQUIPO AZUL**
## 1. Introducción:
El presente documento especifica la solución técnica y funcional para la transformación digital del ecosistema turístico de Benavente, un proyecto estratégico impulsado por el Plan de Sostenibilidad Turística en Destino y los fondos Next Generation EU. El propósito fundamental no es solo la renovación estética de los portales web, sino la implantación de una arquitectura de información centralizada que dinamice la promoción del destino y agilice la gestión interna de sus recursos culturales.

El núcleo de la intervención reside en el desarrollo del nuevo Portal de Turismo y Cultura, concebido como una plataforma de servicios interactivos para el visitante y no como un mero escaparate estático. Esta herramienta permitirá la geolocalización de recursos, la planificación de visitas y la gestión integral de la agenda cultural, integrando capacidades transaccionales para la venta de entradas mediante pasarelas externas. De forma paralela, se digitalizan procesos críticos para el tejido social del municipio, como la gestión de solicitudes y reservas de espacios por parte de las asociaciones locales, automatizando flujos que actualmente requieren intervención manual.

Para sostener este ecosistema, la solución abarca también la actualización tecnológica del Portal Web Oficial y la normalización de la Identidad Corporativa. Aunque el foco prioritario es la proyección turística, el portal institucional actuará como garante de la unicidad del dato, asegurando que la información de eventos y noticias se sincronice bidireccionalmente entre departamentos, evitando duplicidades y garantizando el cumplimiento de los esquemas de seguridad y accesibilidad vigentes.

## 2.	Información del Dominio del problema:

### 2.1 Organigrama
### 2.2 Glosario de terminos

El desarrollo de software para la gestión de un destino turístico requiere una alineación precisa entre los procesos administrativos del Ayuntamiento y la lógica técnica de la plataforma. Para garantizar que la solución responda a la realidad operativa del área de Turismo, se ha modelado el dominio del problema atendiendo a dos dimensiones críticas: la estructura de roles y la semántica del negocio.

En primer lugar, la definición del Modelo Organizativo es indispensable para trasladar la jerarquía administrativa al sistema de permisos del software. A través de la representación visual de los actores, se delimitan las fronteras de responsabilidad entre los distintos perfiles intervinientes: desde los administrativos encargados de la redacción y carga de eventos, pasando por los responsables de validación que autorizan la publicación, hasta las entidades externas (asociaciones) que interactúan con el sistema para gestionar recursos. Este mapeo es vital para configurar los flujos de trabajo (workflows) de aprobación y publicación de contenidos.

Complementariamente, se establece un Diccionario de Conceptos (Glosario) que unifica el lenguaje entre el equipo técnico y los gestores municipales. Dada la naturaleza específica del sector, es necesario desambiguar términos operativos como "evento recurrente", "recurso visitable", "bloqueo de agenda" o "itinerario". Esta base terminológica asegura que las reglas de negocio implementadas —por ejemplo, cómo se comporta una reserva o cuándo caduca una noticia— coincidan exactamente con las expectativas de gestión del servicio de Turismo.

A continuación, se detallan estos artefactos de análisis para sentar las bases del diseño funcional.

## 3. Necesidades del negocio
### 3.1 Objetivos del negocio
### 3.2 Modelos de Proceso de Negocio
#### 3.2.1 Procesos
##### Diagrama BPMN 1:

###### Parte 1: Proceso de creación y contratación de eventos
<p align="center">
  <img src="BPMN_1_proyecto.drawio.svg" alt="img_bpmn_1" width="750">
</p>

###### Parte 2: Proceso de eliminación de eventos finalizados
<p align="center">
  <img src="BPMN_1_2_inre.drawio.svg" alt="img_bpmn_2" width="750">
</p>

###### Diagrma BPMN 2: Gestion de reservas para asociaciones.
<p align="center">
  <img src="bpmn2_inre_proyecto.drawio.svg" alt="img_bpmn_2" width="750">
</p>

#### 3.2.2 Tareas
##### Tareas de la parte 1 del diagrama 1: Proceso de creación y contratación de eventos:
| *Código de tarea* | *Nombre* | *Descripción* |
| :--- | :--- | :--- |
| *T-01* | **El administrativo da de alta el evento en la agenda** | El administrativo del departamento de turismo inicia el proceso de creación de un nuevo registro en la agenda. |
| *T-02* | **Introduce la información del evento** | Se completan los detalles necesarios como fecha, hora, sinopsis y cartel promocional. |
| *T-03* | **Pone un enlace externo a la pasarela de pago** | Al ser un evento de pago, se configura la redirección hacia la plataforma de venta. |
| *T-04* | **Cuando un turista entra, la pasarela le solicita sus datos personales y bancarios** | El sistema externo solicita al usuario la información necesaria para la transacción. |
| *T-05* | **Recibe la solicitud de datos** | El usuario visualiza el formulario donde se le requieren sus datos para la compra. |
| *T-06* | **Es devuelto al portal web** | En caso de no querer aceptar el pago, el usuario es redirigido de vuelta a la página de turismo. |
| *T-07* | **Relena y manda los datos soicitados** | En caso de estar dispuesto a realizar el pago, el usuario introduce su información personal y bancaria y confirma la compra. |
| *T-08* | **Recibe los datos del comprador** | La pasarela de pago recepciona la información introducida por el usuario. |
| *T-09* | **Procesa el pago** | El sistema bancario valida la operación y confirma si es aceptada o rechazada. |
| *T-10* | **Envia la información de la entrada y el recibo al comprador** | Tras el pago exitoso, la pasarela emite y manda los documentos al usuario. |
| *T-11* | **Recibe la entrada y el recibo de la compra** | El usuario obtiene en su correo o pantalla los tickets y el justificante de pago. |

##### Tareas de la parte 2 del diagrama 2: Proceso de eliminación de eventos finalizados
| *Código de tarea* | *Nombre* | *Descripción* |
| :--- | :--- | :--- |
| *T-01* | **Elimina el evento de la agenda** | Una vez que este proceso se activa al haber finalizado el evento, y transcurren 5 días desde su finalización, el sistema elimina dicho evento de la agenda turística. |

##### Tareas del diagrma 2: Gestion de reservas para asociaciones.
| *Código de tarea* | *Nombre* | *Descripción* |
| :--- | :--- | :--- |
| *T-01* | **Adjunta los datos necesarios para hacer la reserva** | El personal correspondiente de una asociación local, desde el formulario de la página de turismo del ayuntamiento, adjunta un correo electrónico y la fecha de reserva de un lugar determinado. |
| *T-02* | **Completa el formulario de reserva y se envía al sistema** | El formulario es completado y enviado al sistema de gestión de reservas. |
| *T-03* | **Recibe la solicitud de la reserva** | El sistema de gestión de reservas recibe la petición. |
| *T-04* | **Rechazar la solicitud de reserva y enviar sugerencias disponibles** | En caso de conflicto de disponibilidad, el sistema deniega la petición y propone alternativas disponibles. |
| *T-05* | **Recibir rechazo y sugerencias disponibles** | La asociación es notificada de la no aceptación de su reserva y visualiza las opciones sugeridas. En caso de que quiera aceptar alguna de las sugerencias volvería a pasar por la tarea ´T-01´, si ninguna sugerencia le viene bien entonces terminaría el proceso. |
| *T-06* | **Bloquear franja horaria seleccionada** | Si no hay ningún problema de disponibilidad, el sistema marca el espacio seleccionado por la asociación como ocupado en la agenda oficial. |
| *T-07* | **Mandar datos de la reserva** | El sistema genera y envía la confirmación con los detalles finales de la reserva aceptada. |
| *T-08* | **Recibir datos de la reserva** | La asociación recibe la información definitiva de su reserva confirmada. |

## 4. Requisitos del sistema a desarrollar

El proyecto tiene como objetivo principal la modernización de la presencia digital del Ayuntamiento de Benavente mediante la actualización de su imagen corporativa, la creación de un Portal de Turismo y Cultura unificado, y la renovación del Portal Web Oficial.

El sistema debe basarse en un Gestor de Contenidos (CMS), preferiblemente Wordpress, que permita una gestión descentralizada y ágil por parte del personal municipal, sin requerir conocimientos técnicos avanzados. El alcance no es solo estético (diseño responsive y moderno), sino técnico, exigiendo cumplimiento de estándares de seguridad (ENS nivel medio), accesibilidad (UNE-EN 301549:2022) y optimización SEO.

## 4.1 Requisitos

### 4.1.1 Requisitos funcionales

| Código | Nombre |
| :--- | :--- |
| <span>RF-01</span> | <span>Gestión de Usuarios y Roles: El CMS debe permitir crear usuarios y asignar permisos diferenciados (ej. administradores vs. departamentos específicos) para que cada área gestione solo su contenido. <br>CU: CU-101, CU-102</span> |
| RF-02 | Gestión de Contenidos: Creación, edición y eliminación de contenidos de forma dinámica e intuitiva. Debe incluir versionado automático para revertir cambios. <br>CU: CU-119, CU-118, CU-105. |
| RF-03 | Programación de Publicaciones: El sistema debe permitir programar la fecha de publicación y la fecha de caducidad (despublicación automática) de los contenidos. <br>CU: CU-110, CU-111 |
| RF-04 | Gestión Multimedia: Capacidad para subir imágenes y vídeos o enlazarlos desde sitios externos, así como gestionar archivos para compartir mediante enlace. <br>CU: CU-114 |
| RF-05 | Creación de Formularios: El CMS debe permitir a los técnicos crear formularios personalizados (contacto, quejas) con sistemas antispam. <br>CU: CU-104 |
| RF-06 | Gestión de Banners: Posibilidad de colocar y gestionar banners en la página principal para redirigir a otros servicios. <br>CU: CU-103 |
| RF-07 | Agenda y Eventos: Visualización de eventos mediante calendario, con sincronización para evitar duplicidades entre portales. <br>CU: CU-220, CU-332, CU-338 |
| RF-08 | Buscador Interno: Motor de búsqueda capaz de indexar toda la información para facilitar la localización de contenidos. <br>CU: CU-333, CU-337 |
| RF-09 | Integración con Redes Sociales: Botones visibles para compartir contenidos y acceso a los perfiles oficiales (Twitter, Facebook, Instagram, etc.). <br>CU:  CU-330, CU-339 |
| RF-10 | Formularios de Incidencias: El usuario debe poder enviar incidencias (ej. vía formulario). <br>CU: CU-316, CU-323 y CU-325. |
| RF-11 | Enlaces a Servicios Externos: Redirección clara a servicios fuera del alcance como la Sede Electrónica, Venta de Entradas o Perfil del Contratante. <br>CU: CU-328, CU-319, CU-326 |
| RF-12 | Catálogo de Recursos: Mostrar información sobre recursos naturales, patrimonio, historia, rutas, etc. <br>CU: CU-203, CU-204, CU-211. |
| RF-13 | Venta de Entradas (Exclusión/Redirección): La web NO gestionará la venta directa, sino que debe redirigir a la plataforma de venta de entradas existente desde la sección de teatro. <br>CU: CU-212 |

### 4.1.2 Requisitos no funcionales

| Código | Nombre |
| :--- | :--- |
| RNF-01 | Diseño Responsive: Adaptabilidad total a dispositivos móviles (smartphones, tablets) y diferentes resoluciones mediante maquetación flexible (HTML5/CSS3). |
| RNF-02 | Identidad Corporativa: El diseño debe basarse estrictamente en el nuevo Manual de Identidad Corporativa y Guía de Estilo. |
| RNF-03 | Accesibilidad: Cumplimiento de las pautas WCAG según la norma UNE-EN 301549:2022 y validación mediante el modelo IRA. |
| RNF-04 | Experiencia de Usuario (UX): Análisis mediante mapas de calor (heatmaps) y reestructuración basada en analíticas tras los primeros meses de uso. |
| RNF-05 | Caché y Estáticos: Generación de versiones estáticas de las páginas y sistema avanzado de caché para maximizar velocidad. |
| RNF-06 | Disponibilidad (SLA): Servicio accesible 24x7x365. Penalizaciones si la resolución de incidencias críticas supera las 6 horas. |
| RNF-07 | Hosting: Alojamiento en tecnología 'Cloud' asumido por el licitador durante el primer año. |
| RNF-08 | Esquema Nacional de Seguridad (ENS): Cumplimiento de medidas para un sistema de nivel medio. |
| RNF-09 | Copias de Seguridad: Backup diario sin pérdida de datos y con tiempo de recuperación menor de 4 horas. |
| RNF-10 | Protección: Sistemas anti-DDoS, control de IPs, y Hardening periódico de sistemas. |
| RNF-11 | Protección de Datos: Cumplimiento del Reglamento (UE) 2016/679 y LOPD 3/2018 (política de cookies, privacidad, avisos legales). |
| RNF-12 | Posicionamiento SEO: Generación de URLs amigables, gestión de metadatos y mantenimiento del posicionamiento adquirido. |
| RNF-13 | Analítica Web: Integración con Google Analytics (o similar) para medir accesos, tiempos de navegación y páginas vistas. |

## 4.2 Casos de Uso

### 4.2.1 Lista de diagramas de casos de uso del modelo

<p align="center">
  <img src="Portal_principal.jpg" alt="Imagen del DCU del portal general" width="750">
</p>

<p align="center">
  <img src="Portal_turismo.jpg" alt="Imagen del DCU del portal de turismo" width="750">
</p>

<p align="center">
  <img src="CMS.jpg" alt="Imagen del DCU del CMS" width="750">
</p>

#### 4.2.2 Lista general de casos de uso

| Código | Nombre |
| :--- | :--- |
| <span>CU-101</span> | <span>Gestionar permisos</span> |
| <span>CU-102</span> | <span>Gestionar rol de usuario</span> |
| <span>CU-103</span> | <span>Colocar banner en la pagina principal</span> |
| <span>CU-104</span> | <span>Crear formulario</span> |
| <span>CU-105</span> | <span>Publicar noticia</span> |
| <span>CU-106</span> | <span>Publicar anuncio</span> |
| <span>CU-107</span> | <span>Publicar evento en la agenda</span> |
| <span>CU-108</span> | <span>Realizar un cambio en el contenido general</span> |
| <span>CU-109</span> | <span>Eliminar contenido</span> |
| <span>CU-110</span> | <span>Programar publicacion</span> |
| <span>CU-111</span> | <span>Indicar fecha de vencimiento</span> |
| <span>CU-112</span> | <span>Indicar fecha de publicacion</span> |
| <span>CU-113</span> | <span>Realizar un cambio en el contenido turismo</span> |
| <span>CU-114</span> | <span>Subir multimedia</span> |
| <span>CU-115</span> | <span>Registrar detalles</span> |
| <span>CU-116</span> | <span>Crear portal</span> |
| <span>CU-117</span> | <span>Eliminar contenido (general)</span> |
| <span>CU-118</span> | <span>Eliminar contenido (turismo)</span> |
| <span>CU-119</span> | <span>Realizar un cambio en el contenido</span> |
| <span>CU-201</span> | <span>Ver informacion sobre la ciudad</span> |
| <span>CU-202</span> | <span>Ver informacion sobre la historia de la ciudad</span> |
| <span>CU-203</span> | <span>Ver recursos naturales</span> |
| <span>CU-204</span> | <span>Ver patrimonio monumental artistico</span> |
| <span>CU-205</span> | <span>Ver esculturas urbanas</span> |
| <span>CU-206</span> | <span>Ver informacion sobre la ruta de la plata</span> |
| <span>CU-207</span> | <span>Ver informacion sobre la situacion de la ciudad</span> |
| <span>CU-208</span> | <span>Buscar informacion turismo</span> |
| <span>CU-209</span> | <span>Acceder a las redes sociales turismo</span> |
| <span>CU-210</span> | <span>Ver informacion util turismo</span> |
| <span>CU-211</span> | <span>Ver rutas por Benavente</span> |
| <span>CU-212</span> | <span>Comprar entrada de un evento del teatro</span> |
| <span>CU-213</span> | <span>Registrarse como cliente</span> |
| <span>CU-214</span> | <span>Iniciar sesion como cliente</span> |
| <span>CU-215</span> | <span>Ver eventos del teatro</span> |
| <span>CU-216</span> | <span>Añadir evento al calendario turismo</span> |
| <span>CU-217</span> | <span>Ver mas informacion de un evento del teatro</span> |
| <span>CU-218</span> | <span>Abrir mapa en google maps</span> |
| <span>CU-219</span> | <span>Ver localizacion del teatro en google maps</span> |
| <span>CU-220</span> | <span>Acceder a la agenda de eventos turismo</span> |
| <span>CU-221</span> | <span>Seleccionar dia del evento turismo</span> |
| <span>CU-222</span> | <span>Ver evento turismo</span> |
| <span>CU-223</span> | <span>Buscar nombre del evento turismo</span> |
| <span>CU-224</span> | <span>Seleccionar categoria de evento turismo</span> |
| <span>CU-225</span> | <span>Ver tour virtual turismo</span> |
| <span>CU-226</span> | <span>Acceder al portal del organizador del evento turismo</span> |
| <span>CU-227</span> | <span>Compartir evento en redes sociales turismo</span> |
| <span>CU-301</span> | <span>Ver las Ferias y Fiestas del Toro Enmaromado</span> |
| <span>CU-302</span> | <span>Consultar actualidad</span> |
| <span>CU-303</span> | <span>Ver todas las noticias</span> |
| <span>CU-304</span> | <span>Ver noticia</span> |
| <span>CU-305</span> | <span>Ver todos los anuncios</span> |
| <span>CU-306</span> | <span>Ver anuncio</span> |
| <span>CU-307</span> | <span>Ver informacion util</span> |
| <span>CU-308</span> | <span>Ver tablon virtual</span> |
| <span>CU-309</span> | <span>Acceder a Factura Electronica</span> |
| <span>CU-310</span> | <span>Ver webs municipales</span> |
| <span>CU-311</span> | <span>Acceder a atencion ciudadana</span> |
| <span>CU-312</span> | <span>Ver areas municipales</span> |
| <span>CU-313</span> | <span>Acceder al portal de turismo</span> |
| <span>CU-314</span> | <span>Acceder al canal plenario</span> |
| <span>CU-315</span> | <span>Gestionar tramites</span> |
| <span>CU-316</span> | <span>Iniciar proceso de envio de incidencia</span> |
| <span>CU-317</span> | <span>Ver solicitudes</span> |
| <span>CU-318</span> | <span>Ver contratos</span> |
| <span>CU-319</span> | <span>Ver factura electronica</span> |
| <span>CU-320</span> | <span>Seleccionar la categoria de incidencia</span> |
| <span>CU-321</span> | <span>Seleccionar lugar de la incidencia</span> |
| <span>CU-322</span> | <span>Describir la incidencia</span> |
| <span>CU-323</span> | <span>Adjuntar imagenes</span> |
| <span>CU-324</span> | <span>Introducir datos personales</span> |
| <span>CU-325</span> | <span>Enviar incidencia</span> |
| <span>CU-326</span> | <span>Acceder a la pasarela de pago</span> |
| <span>CU-327</span> | <span>Acceder a los pagos de tributos online</span> |
| <span>CU-328</span> | <span>Acceder a la Sede Electronica</span> |
| <span>CU-329</span> | <span>Acceder al portal de transparencia</span> |
| <span>CU-330</span> | <span>Visitar las redes sociales</span> |
| <span>CU-331</span> | <span>Acceder a la agenda de eventos</span> |
| <span>CU-332</span> | <span>Ver evento</span> |
| <span>CU-333</span> | <span>Buscar información</span> |
| <span>CU-334</span> | <span>Ver tour virtual</span> |
| <span>CU-335</span> | <span>Seleccionar día del evento</span> |
| <span>CU-336</span> | <span>Seleccionar categoría de evento</span> |
| <span>CU-337</span> | <span>Buscar nombre del evento</span> |
| <span>CU-338</span> | <span>Añadir evento al calendario</span> |
| <span>CU-339</span> | <span>Compartir evento en redes sociales</span> |
| <span>CU-340</span> | <span>Acceder al portal del organizador del evento</span> |

#### 4.2.3 Detalles de los casos de uso

### DCU - CMS

### Gestionar permisos

| **Nombre:** | <span>Gestionar permisos</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-101</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite definir qué acciones pueden realizar los diferentes roles dentro del sistema.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El Administrador debe estar autenticado en el sistema con privilegios de superusuario.</span> |
| **Flujo Normal:** | <span>1.- El Administrador accede al panel de gestión de permisos. <br>2.- El Administrador busca y selecciona el rol a modificar. <br>3.- El Administrador marca o desmarca las casillas de permisos correspondientes. <br>4.- El Administrador guarda los cambios realizados.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>Los permisos del usuario o rol quedan actualizados en la base de datos.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Gestionar rol de usuario

| **Nombre:** | <span>Gestionar rol de usuario</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-102</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite al Administrador asignar o modificar el rol funcional de un usuario (ej. cambiar de editor a administrador).</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El Administrador debe estar logueado y el usuario destino debe existir.</span> |
| **Flujo Normal:** | <span>1.- El Administrador entra en la configuración de cuentas de usuario. <br>2.- El Administrador selecciona una cuenta de la lista. <br>3.- El Administrador asigna un nuevo rol desplegando la lista de roles disponibles. <br>4.- El Administrador confirma la operación.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El usuario tiene asignado su nuevo rol y las capacidades asociadas al mismo.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Colocar banner en la pagina principal

| **Nombre:** | <span>Colocar banner en la pagina principal</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-103</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite situar una imagen destacada o aviso en la home del portal general.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El actor debe tener la imagen del banner preparada.</span> |
| **Flujo Normal:** | <span>1.- El administrativo accede al gestor de contenidos de la página principal. <br>2.- El administrativo selecciona la zona de banners. <br>3.- El administrativo sube la imagen y asigna un enlace de destino. <br>4.- El administrativo publica los cambios.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El banner aparece visible para todos los visitantes de la página principal.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Crear formulario

| **Nombre:** | <span>Crear formulario</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-104</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Herramienta para generar formularios de contacto o encuestas dinámicas.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El administrativo inicia el constructor de formularios. <br>2.- El administrativo arrastra y suelta los campos necesarios (texto, fecha, selección). <br>3.- El administrativo configura el correo de recepción de datos. <br>4.- El administrativo guarda y obtiene el código para insertar el formulario.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El formulario queda guardado y listo para usarse en una página.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Publicar noticia

| **Nombre:** | <span>Publicar noticia</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-105</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite redactar y lanzar una noticia en el portal.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El usuario está en el dashboard de noticias.</span> |
| **Flujo Normal:** | <span>1.- El actor accede al editor de noticias. <br>2.- El actor escribe el titular, entradilla y cuerpo. <br>3.- El actor extiende el proceso para subir multimedia si es necesario. <br>4.- El actor pulsa el botón de publicar. <br>5.- El sistema valida los campos obligatorios. <br>6.- La noticia se hace visible inmediatamente.</span> |
| **Flujo Alternativo:** | <span>3a. Subir multimedia: <br>1.- El actor selecciona "Adjuntar imagen/video". <br>2.- El sistema abre el explorador de archivos. <br>3.- El actor selecciona el archivo y el sistema lo carga al servidor. <br>4.- El archivo se asocia a la noticia. <br>5.- Retorna al paso 4 del flujo normal. <br>4a. Programar publicación: <br>1.- En lugar de "Publicar", el actor selecciona "Programar". <br>2.- El sistema solicita la fecha de publicación. <br>3.- El actor introduce la fecha futura. <br>4.- El sistema guarda la noticia en estado "Pendiente".</span> |
| **Poscondiciones:**| <span>La noticia es pública en el listado de actualidad.</span> |
| **Artefactos relacionados:**| <span>CU-110, CU-114</span> |

---

### Publicar anuncio

| **Nombre:** | <span>Publicar anuncio</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-106</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Publicación de anuncios breves o destacados. Similar a noticias pero con formato distinto.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>Acceso al módulo de anuncios.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona crear nuevo anuncio. <br>2.- El actor introduce la información relevante. <br>3.- El actor pulsa "Publicar" <br>4.- El sistema actualiza el portal.</span> |
| **Flujo Alternativo:** | <span>3a. Subir multimedia: <br>1.- El actor decide añadir un banner gráfico. <br>2.- Sube la imagen al servidor. <br>3.- Asocia la imagen al anuncio. <br>4.- Retorna al flujo normal. <br>4a. Programar publicación: <br>1.- El actor elige diferir la publicación. <br>2.- Define fecha de inicio y opcionalmente fin. <br>3.- El anuncio queda en espera.</span> |
| **Poscondiciones:**| <span>El anuncio es visible o queda programado.</span> |
| **Artefactos relacionados:**| <span>CU-110, CU-114</span> |

---

### Publicar evento en la agenda

| **Nombre:** | <span>Publicar evento en la agenda</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-107</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Creación de eventos en el calendario.</span> |
| **Actores:** | <span>Agenda</span> |
| **Precondiciones:**| <span>El evento debe tener fecha y hora confirmadas.</span> |
| **Flujo Normal:** | <span>1.- El actor accede a la gestión de la agenda. <br>2.- El actor crea una nueva entrada con fecha, hora y lugar. <br>3.- El actor guarda el evento en el sistema.</span> |
| **Flujo Alternativo:** | <span>3a. Programar publicación: <br>1.- En lugar de "Publicar", el actor selecciona "Programar". <br>2.- El sistema solicita la fecha de publicación. <br>3.- El actor introduce la fecha futura. <br>4.- El sistema guarda la noticia en estado "Pendiente".</span> |
| **Poscondiciones:**| <span>El evento es visible en el calendario para los visitantes.</span> |
| **Artefactos relacionados:**| <span>CU-110</span> |

---

### Realizar un cambio en el contenido (General)

| **Nombre:** | <span>Realizar un cambio en el contenido (General)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-108</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Edición de contenidos existentes en el portal general.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El contenido a editar debe existir.</span> |
| **Flujo Normal:** | <span>1.- El administrativo localiza el contenido que desea cambiar. <br>2.- El administrativo edita el texto o las opciones. <br>3.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>4.- El sistema almacena el registro en el log de auditoría. <br> 5.- El sistema confirma que el contenido ha sido actualizado y registrado.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido queda actualizado.</span> |
| **Artefactos relacionados:**| <span>CU-119</span> |

---

### Eliminar contenido

| **Nombre:** | <span>Eliminar contenido</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-109</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Acción de borrar un elemento del sistema. Incluida en los flujos de cambio de contenido.</span> |
| **Actores:** | <span>Administrativo del portal de turismo o Administrativo del portal general</span> |
| **Precondiciones:**| <span>El actor tiene permisos de borrado.</span> |
| **Flujo Normal:** | <span>1.- El Administrativo selecciona el contenido a eliminar. <br>2.- El actor confirma la acción en el mensaje de advertencia. <br>3.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>4.- El sistema almacena el registro en el log de auditoría. <br> 5.- El sistema confirma que el contenido ha sido actualizado y registrado. <br>6.- El sistema marca el contenido como eliminado (borrado lógico) o lo elimina físicamente.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido deja de existir en el portal.</span> |
| **Artefactos relacionados:**| <span>CU-115</span> |

---

### Programar publicacion

| **Nombre:** | <span>Programar publicacion</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-110</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite diferir la publicación de un contenido a una fecha futura.</span> |
| **Actores:** | <span>Sistema (invocado por los administradores)</span> |
| **Precondiciones:**| <span>El contenido está listo pero no se desea publicar ya.</span> |
| **Flujo Normal:** | <span>1.- En lugar de "Publicar", el actor selecciona "Programar". <br>2.- El sistema solicita la fecha de publicación. <br>3.- El actor introduce la fecha futura. <br>4.- El sistema guarda la noticia en estado "Pendiente".</span> |
| **Flujo Alternativo:** | <span>2a. Indicar fecha de vencimiento: <br>1.- El usuario indica que el contenido es temporal. <br>2.- El sistema solicita fecha de fin. <br>3.- El usuario selecciona una fecha posterior a la de publicación. <br>4.- El sistema programa la despublicación automática. <br>5.- Retorna al flujo normal.</span> |
| **Poscondiciones:**| <span>El contenido se publicará automáticamente cuando llegue la fecha.</span> |
| **Artefactos relacionados:**| <span>CU-105, CU-106, CU-107, CU-111, CU-112</span> |

---

### Indicar fecha de vencimiento

| **Nombre:** | <span>Indicar fecha de vencimiento</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-111</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Establece cuándo un contenido debe dejar de ser visible.</span> |
| **Actores:** | <span>Sistema (invocado por los administrativos)</span> |
| **Precondiciones:**| <span>Se está programando una publicación y ya se ha definido una fecha de inicio.</span> |
| **Flujo Normal:** | <span>1.- El usuario indica que el contenido es temporal. <br>2.- El sistema solicita fecha de fin. <br>3.- El usuario selecciona una fecha posterior a la de publicación. </span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido se despublicará en la fecha indicada.</span> |
| **Artefactos relacionados:**| <span>CU-110</span> |

---

### Indicar fecha de publicacion

| **Nombre:** | <span>Indicar fecha de publicacion</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-112</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Acción de seleccionar el día de inicio de visibilidad. Incluido en programar publicación.</span> |
| **Actores:** | <span>Sistema (invocado por los administrativos)</span> |
| **Precondiciones:**| <span>Se esta ejecutando el flujo de "Programar publicacion"</span> |
| **Flujo Normal:** | <span>1.- El sistema solicita la fecha de publicación. <br>2.- El actor introduce la fecha futura.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La fecha de inicio queda registrada.</span> |
| **Artefactos relacionados:**| <span>CU-110</span> |

---

### Realizar un cambio en el contenido (turismo)

| **Nombre:** | <span>Realizar un cambio en el contenido turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-113</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Gestión de contenidos específica para el portal de turismo.</span> |
| **Actores:** | <span>Administrativo del portal de turismo</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el área de turismo.</span> |
| **Flujo Normal:** | <span>1.- El administrativo selecciona un recurso turístico. <br>2.- El administrativo modifica la descripción o fotos. <br>3.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>4.- El sistema almacena el registro en el log de auditoría. <br> 5.- El sistema confirma que el contenido ha sido actualizado y registrado.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La información turística queda actualizada.</span> |
| **Artefactos relacionados:**| <span>CU-119</span> |

---

### Subir multimedia

| **Nombre:** | <span>Subir multimedia</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-114</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Proceso de carga de archivos al servidor.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El usuario debe estar en un formulario de creación/edición de contenido.</span> |
| **Flujo Normal:** | <span>1.- El actor decide añadir un banner gráfico. <br>2.- Sube la imagen al servidor. <br>3.- Asocia la imagen al anuncio.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El archivo se encuentra en el servidor y en el contenido al que ha sido adjunto.</span> |
| **Artefactos relacionados:**| <span>CU-105, CU-106</span> |

---

### Registrar detalles

| **Nombre:** | <span>Registrar detalles</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-115</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Funcionalidad de sistema para capturar y almacenar la traza de quién hizo qué cambio y cuándo (Log de auditoría).</span> |
| **Actores:** | <span>Sistema (invocado automáticamente por los administrativos)</span> |
| **Precondiciones:**| <span>Se debe haber realizado una acción de modificación.</span> |
| **Flujo Normal:** | <span>1.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>2.- El sistema almacena el registro en el log de auditoría. <br> 3.- El sistema confirma que el contenido ha sido actualizado y registrado.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La acción queda trazada para seguridad.</span> |

| **Artefactos relacionados:**| <span>CU-119, CU-109</span> |

---

### Crear portal

| **Nombre:** | <span>Crear portal</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-116</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite al Administrador dar de alta un nuevo portal dentro del sistema.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El Administrador debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El Administrador selecciona la opción de crear nuevo portal. <br>2.- El Administrador define el nombre, la URL y selecciona una plantilla base. <br>3.- El sistema valida que la URL no exista. <br>4.- El sistema crea la estructura de base de datos y archivos. <br>5.- El sistema confirma la creación del portal.</span> |
| **Flujo Alternativo:** | <span>4a. La URL ya existe: <br>1.- El sistema muestra un error indicando duplicidad. <br>2.- El sistema solicita una nueva URL. <br>3.- Vuelve al paso 3 del flujo normal.</span> |
| **Poscondiciones:**| <span>El nuevo portal está activo y listo para ser configurado.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Eliminar contenido (general)

| **Nombre:** | <span>Eliminar contenido (general)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-117</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite borrar contenido del portal general. Es una especialización de la acción genérica de eliminar.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El contenido debe existir y no estar bloqueado.</span> |
| **Flujo Normal:** | <span>1.- El Administrativo selecciona el contenido a eliminar. <br>2.- El actor confirma la acción en el mensaje de advertencia. <br>3.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>4.- El sistema almacena el registro en el log de auditoría. <br> 5.- El sistema confirma que el contenido ha sido actualizado y registrado. <br>6.- El sistema marca el contenido como eliminado (borrado lógico) o lo elimina físicamente.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido deja de existir en el portal.</span> |
| **Artefactos relacionados:**| <span>CU-109</span> |

---

### Eliminar contenido (turismo)

| **Nombre:** | <span>Eliminar contenido (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-118</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Eliminación de contenidos dentro del ámbito turístico.</span> |
| **Actores:** | <span>Administrativo del portal de turismo</span> |
| **Precondiciones:**| <span>El actor tiene permisos de borrado.</span> |
| **Flujo Normal:** | <span>1.- El Administrativo selecciona el contenido a eliminar. <br>2.- El actor confirma la acción en el mensaje de advertencia. <br>3.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>4.- El sistema almacena el registro en el log de auditoría. <br> 5.- El sistema confirma que el contenido ha sido actualizado y registrado. <br>6.- El sistema marca el contenido como eliminado (borrado lógico) o lo elimina físicamente.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido deja de existir en el portal.</span> |
| **Artefactos relacionados:**| <span>CU-109</span> |

---

### Realizar un cambio en el contenido

| **Nombre:** | <span>Realizar un cambio en el contenido</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-119</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Caso de uso general que encapsula la lógica común de edición de contenidos.</span> |
| **Actores:** | <span>Administrativo del portal de turismo o Administrativo del portal general</span> |
| **Precondiciones:**| <span>Usuario autenticado con permisos de edición.</span> |
| **Flujo Normal:** | <span>1.- El administrativo modifica la descripción o fotos. <br>2.- El sistema captura automáticamente la fecha, hora y ID del usuario. <br>3.- El sistema almacena el registro en el log de auditoría. <br> 4.- El sistema confirma que el contenido ha sido actualizado y registrado.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>Contenido modificado.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-111</span> |

---

### DCU - Portal de turismo del ayuntamiento

### Ver informacion sobre la ciudad

| **Nombre:** | <span>Ver informacion sobre la ciudad</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-201</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Permite al turista acceder a datos generales y presentación de la ciudad.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>El portal de turismo es accesible.</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona el menú de información de la ciudad. <br>2.- El turista visualiza la página de bienvenida y datos generales.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista obtiene la información general.</span> |
| **Artefactos relacionados:**| <span>CU-202, CU-203, CU-204, CU-206</span> |

---

### Ver informacion sobre la historia de la ciudad

| **Nombre:** | <span>Ver informacion sobre la historia de la ciudad</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-202</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Muestra el recorrido histórico y fechas clave de la localidad.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista elige la sección de historia. <br>2.- El turista lee los textos históricos presentados.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista conoce la historia local.</span> |
| **Artefactos relacionados:**| <span>CU-201</span> |

---

### Ver recursos naturales

| **Nombre:** | <span>Ver recursos naturales</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-203</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Información sobre parques, ríos y entornos naturales visitables.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista navega a la categoría de naturaleza. <br>2.- El turista revisa la lista de parajes naturales.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista visualiza la oferta natural.</span> |
| **Artefactos relacionados:**| <span>CU-201</span> |

---

### Ver patrimonio monumental artistico

| **Nombre:** | <span>Ver patrimonio monumental artistico</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-204</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Catálogo de monumentos y edificios de interés artístico.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista accede a la sección de patrimonio. <br>2.- El turista explora las fichas de los monumentos.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista conoce los monumentos disponibles.</span> |
| **Artefactos relacionados:**| <span>CU-201, CU-205</span> |

---

### Ver esculturas urbanas

| **Nombre:** | <span>Ver esculturas urbanas</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-205</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Detalle sobre el arte urbano y estatuas en la vía pública.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona el apartado de esculturas. <br>2.- El turista ve la ubicación y descripción de las obras.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista visualiza la información de esculturas.</span> |
| **Artefactos relacionados:**| <span>CU-204</span> |

---

### Ver informacion sobre la ruta de la plata

| **Nombre:** | <span>Ver informacion sobre la ruta de la plata</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-206</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Información específica para peregrinos o interesados en esta ruta.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista entra en la sección de la Ruta de la Plata. <br>2.- El turista consulta mapas y etapas que pasan por la ciudad.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista obtiene información de la ruta.</span> |
| **Artefactos relacionados:**| <span>CU-207, CU-201</span> |

---

### Ver informacion sobre la situacion de la ciudad

| **Nombre:** | <span>Ver informacion sobre la situacion de la ciudad</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-207</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Datos sobre ubicación geográfica, accesos y clima.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista busca cómo llegar o dónde está la ciudad. <br>2.- El turista visualiza los mapas de situación.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista se ubica geográficamente.</span> |
| **Artefactos relacionados:**| <span>CU-206</span> |

---

### Buscar informacion (turismo)

| **Nombre:** | <span>Buscar informacion (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-208</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Uso del buscador interno para localizar contenidos en el portal de turismo.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista introduce palabras clave en la barra de búsqueda. <br>2.- El turista examina los resultados que devuelve el sistema.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista encuentra el contenido deseado.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Acceder a las redes sociales (turismo)

| **Nombre:** | <span>Acceder a las redes sociales (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-209</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Enlace a los perfiles sociales promocionales de turismo.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista hace clic en los iconos de redes sociales. <br>2.- El sistema abre la red social externa.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista visita el perfil social.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Ver informacion util (turismo)

| **Nombre:** | <span>Ver informacion util (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-210</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Datos prácticos para el visitante (oficina de turismo, horarios museos).</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista accede al apartado de info útil. <br>2.- El turista consulta los horarios y teléfonos.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista obtiene datos prácticos.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Ver rutas por benavente

| **Nombre:** | <span>Ver rutas por benavente</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-211</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Propuestas de itinerarios dentro de la localidad.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista explora las rutas sugeridas. <br>2.- El turista selecciona una para ver el detalle del recorrido.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista planifica su recorrido.</span> |
| **Artefactos relacionados:**| <span>N/A</span> |

---

### Comprar entrada de un evento del teatro

| **Nombre:** | <span>Comprar entrada de un evento del teatro</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-212</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Proceso de adquisición de tickets.</span> |
| **Actores:** | <span>Turista, Cliente</span> |
| **Precondiciones:**| <span>El evento debe tener entradas a la venta.</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona las butacas y confirma la compra. <br>2.- El turista realiza el pago. <br>3.- El sistema envía las entradas.</span> |
| **Flujo Alternativo:** | <span>1.- El turista introduce sus datos personales y contraseña. <br>2.- El sistema crea la cuenta de usuario. <br><br>1.- El turista introduce email y contraseña. <br>2.- El sistema valida el acceso.</span> |
| **Poscondiciones:**| <span>El turista obtiene sus entradas.</span> |
| **Artefactos relacionados:**| <span>CU-213, CU-214, CU-215</span> |

---

### Registrarse como cliente

| **Nombre:** | <span>Registrarse como cliente</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-213</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Creación de cuenta para compras en el teatro.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>No tener cuenta previa.</span> |
| **Flujo Normal:** | <span>1.- El turista introduce sus datos personales y contraseña. <br>2.- El sistema crea la cuenta de usuario.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista es ahora un cliente registrado.</span> |
| **Artefactos relacionados:**| <span>CU-212</span> |

---

### Iniciar sesion como cliente

| **Nombre:** | <span>Iniciar sesion como cliente</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-214</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Identificación de usuario recurrente.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>Tener cuenta activa.</span> |
| **Flujo Normal:** | <span>1.- El turista introduce email y contraseña. <br>2.- El sistema valida el acceso.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista está logueado.</span> |
| **Artefactos relacionados:**| <span>CU-212</span> |

---

### Ver eventos del teatro

| **Nombre:** | <span>Ver eventos del teatro</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-215</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Cartelera de espectáculos disponibles.</span> |
| **Actores:** | <span>Turista, Cliente</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista entra en la sección de teatro. <br>2.- El turista visualiza la lista de obras.</span> |
| **Flujo Alternativo:** | <span>1.- El turista clica en un cartel de obra. <br>2.- El turista lee la ficha técnica y artística. <br><br>1.- El turista selecciona las butacas y confirma la compra. <br>2.- El turista realiza el pago. <br>3.- El sistema envía las entradas. <br><br>1.- El turista consulta la ubicación del teatro. <br>2.- El turista ve el pin en el mapa.</span> |
| **Poscondiciones:**| <span>El turista conoce la programación.</span> |
| **Artefactos relacionados:**| <span>CU-212, CU-217, CU-219</span> |

---

### Añadir evento al calendario (turismo)

| **Nombre:** | <span>Añadir evento al calendario (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-216</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Exportar cita a la agenda personal.</span> |
| **Actores:** | <span>N/A (Caso de uso extendido)</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona guardar en calendario. <br>2.- El sistema descarga el archivo .ics.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El evento queda agendado en el dispositivo del usuario.</span> |
| **Artefactos relacionados:**| <span>CU-222</span> |

---

### Ver mas informacion de un evento del teatro

| **Nombre:** | <span>Ver mas informacion de un evento del teatro</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-217</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Ficha detallada de una obra (sinopsis, reparto).</span> |
| **Actores:** | <span>Turista, Cliente</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista clica en un cartel de obra. <br>2.- El turista lee la ficha técnica y artística.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista tiene detalles para decidir la compra.</span> |
| **Artefactos relacionados:**| <span>CU-215</span> |

---

### Ver localizacion del teatro en google maps

| **Nombre:** | <span>Ver localizacion del teatro en google maps</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-219</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Mostrar dónde está el teatro específicamente.</span> |
| **Actores:** | <span>Turista, Cliente</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista consulta la ubicación del teatro. <br>2.- El turista ve el pin en el mapa.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista sabe dónde está el teatro.</span> |
| **Artefactos relacionados:**| <span>CU-215</span> |

---

### Acceder a la agenda de eventos (turismo)

| **Nombre:** | <span>Acceder a la agenda de eventos (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-220</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Calendario general de actividades turísticas.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista abre la agenda. <br>2.- El turista ve los eventos del mes. <br>3.- El turista elige un día específico. <br>4.- El sistema muestra solo eventos de ese día. <br>5.- El turista selecciona una actividad. <br>6.- El turista revisa toda la información asociada.</span> |
| **Flujo Alternativo:** | <span>1.- El turista escribe el nombre del evento. <br>2.- El sistema devuelve coincidencias. <br><br>1.- El turista marca una categoría. <br>2.- El sistema actualiza la lista. <br><br>1.- El turista inicia el tour virtual. <br>2.- El turista navega interactivamente por las imágenes.</span> |
| **Poscondiciones:**| <span>El turista consulta la oferta de ocio y detalla un evento.</span> |
| **Artefactos relacionados:**| <span>CU-224, CU-225, CU-221, CU-223</span> |

---

### Seleccionar dia del evento (turismo)

| **Nombre:** | <span>Seleccionar dia del evento (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-221</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Filtrado de agenda por fecha.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista elige un día específico. <br>2.- El sistema muestra solo eventos de ese día. <br>3.- El turista selecciona una actividad. <br>4.- El turista revisa toda la información asociada.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista filtra los resultados y ve el detalle.</span> |
| **Artefactos relacionados:**| <span>CU-220, CU-222</span> |

---

### Ver evento (turismo)

| **Nombre:** | <span>Ver evento (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-222</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Detalle de una actividad turística concreta.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona una actividad. <br>2.- El turista revisa toda la información asociada.</span> |
| **Flujo Alternativo:** | <span>1.- El turista selecciona guardar en calendario. <br>2.- El sistema descarga el archivo .ics. <br><br>1.- El turista clica en la web del organizador. <br>2.- El navegador abre el sitio externo. <br><br>1.- El turista pulsa el botón de compartir. <br>2.- El turista elige la red social. <br>3.- El sistema prepara la publicación.</span> |
| **Poscondiciones:**| <span>El turista se informa del evento.</span> |
| **Artefactos relacionados:**| <span>CU-216, CU-227, CU-226, CU-221</span> |

---

### Buscar nombre del evento (turismo)

| **Nombre:** | <span>Buscar nombre del evento (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-223</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Búsqueda textual en la agenda.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista escribe el nombre del evento. <br>2.- El sistema devuelve coincidencias.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista encuentra el evento específico.</span> |
| **Artefactos relacionados:**| <span>CU-220</span> |

---

### Seleccionar categoria de evento (turismo)

| **Nombre:** | <span>Seleccionar categoria de evento (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-224</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Filtrado por tipo (concierto, exposición, etc.).</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista marca una categoría. <br>2.- El sistema actualiza la lista.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista ve eventos temáticos.</span> |
| **Artefactos relacionados:**| <span>CU-220</span> |

---

### Ver tour virtual (turismo)

| **Nombre:** | <span>Ver tour virtual (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-225</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Visita 360 grados online.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>El evento dispone de tour virtual.</span> |
| **Flujo Normal:** | <span>1.- El turista inicia el tour virtual. <br>2.- El turista navega interactivamente por las imágenes.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista realiza la visita virtual.</span> |
| **Artefactos relacionados:**| <span>CU-220</span> |

---

### Acceder al portal del organizador del evento (turismo)

| **Nombre:** | <span>Acceder al portal del organizador del evento (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-226</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Redirección a la web oficial del promotor.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista clica en la web del organizador. <br>2.- El navegador abre el sitio externo.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista sale del portal hacia la web externa.</span> |
| **Artefactos relacionados:**| <span>CU-222</span> |

---

### Compartir evento en redes sociales (turismo)

| **Nombre:** | <span>Compartir evento en redes sociales (turismo)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-227</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Publicar el evento en perfiles personales.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista pulsa el botón de compartir. <br>2.- El turista elige la red social. <br>3.- El sistema prepara la publicación.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El evento se comparte socialmente.</span> |
| **Artefactos relacionados:**| <span>CU-222</span> |

---

### DCU - Portal general del ayuntamiento

### Ver las Ferias y Fiestas del Toro Enmaromado

| Nombre: | <span>Ver las Ferias y Fiestas del Toro Enmaromado</span> |
| :--- | :--- |
| Codigo: | <span>CU-301</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Permite al visitante acceder a la información específica sobre las festividades locales.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>El portal debe estar operativo y la sección de festejos publicada.</span> |
| Flujo Normal: | <span>1.- El visitante pulsa en la sección de ferias y fiestas del menú. <br>2.- El sistema carga la agenda festiva, el programa de mano y la galería multimedia histórica.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario visualiza los contenidos culturales de las fiestas locales.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Consultar actualidad

| Nombre: | <span>Consultar actualidad</span> |
| :--- | :--- |
| Codigo: | <span>CU-302</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Actúa como el centro de noticias y boletines informativos del ayuntamiento.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>El servidor de contenidos debe tener noticias recientes publicadas.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona el apartado de actualidad en la página de inicio. <br>2.- El sistema muestra un resumen visual de las últimas noticias, bandos e informaciones de interés.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El ciudadano accede al resumen informativo del día.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver todas las noticias

| Nombre: | <span>Ver todas las noticias</span> |
| :--- | :--- |
| Codigo: | <span>CU-303</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Permite navegar por el archivo histórico de prensa municipal.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Haber entrado previamente en el hub de actualidad.</span> |
| Flujo Normal: | <span>1.- El visitante clica sobre el enlace de ver archivo de noticias. <br>2.- El sistema lista de forma cronológica los titulares y entradillas de toda la hemeroteca.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El visitante visualiza el listado completo de prensa municipal.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver noticia

| Nombre: | <span>Ver noticia</span> |
| :--- | :--- |
| Codigo: | <span>CU-304</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Lectura detallada del contenido de un artículo de prensa local.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>La noticia debe haber sido recuperada por el sistema.</span> |
| Flujo Normal: | <span>1.- El visitante pulsa en un titular específico de la lista. <br>2.- El sistema abre el artículo mostrando texto, autor, fecha y fotos asociadas.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario lee el artículo informativo completo.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver todos los anuncios

| Nombre: | <span>Ver todos los anuncios</span> |
| :--- | :--- |
| Codigo: | <span>CU-305</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Consulta de los avisos y comunicados oficiales vigentes para la ciudadanía.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Acceso general al portal.</span> |
| Flujo Normal: | <span>1.- El usuario selecciona la opción de ver anuncios oficiales. <br>2.- El sistema muestra un listado de comunicados breves ordenados por relevancia.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El ciudadano consulta los avisos municipales.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver anuncio

| Nombre: | <span>Ver anuncio</span> |
| :--- | :--- |
| Codigo: | <span>CU-306</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Visualización individualizada de un aviso municipal.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Estar en el listado global de anuncios.</span> |
| Flujo Normal: | <span>1.- El visitante elige un anuncio específico. <br>2.- El sistema presenta el texto íntegro del aviso en pantalla.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Consulta terminada del contenido del anuncio.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver informacion util

| Nombre: | <span>Ver informacion util</span> |
| :--- | :--- |
| Codigo: | <span>CU-307</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Acceso rápido a teléfonos de emergencia, farmacias y transportes.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Servicio de información habilitado en el portal.</span> |
| Flujo Normal: | <span>1.- El visitante accede al apartado de teléfonos y servicios de interés. <br>2.- El sistema organiza visualmente los datos de contacto y horarios de servicio público.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El ciudadano obtiene la información de primera necesidad municipal.</span> |
| Artefactos relacionados: | <span></span> |

---

### Ver tablon virtual

| Nombre: | <span>Ver tablon virtual</span> |
| :--- | :--- |
| Codigo: | <span>CU-308</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Visualización digital de edictos y avisos oficiales con validez legal.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span></span> |
| Flujo Normal: | <span>1.- El ciudadano abre el tablón virtual. <br>2.- El sistema permite navegar por los PDF de edictos firmados digitalmente por el ayuntamiento.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span></span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Acceder a Factura Electronica

| Nombre: | <span>Acceder a Factura Electronica</span> |
| :--- | :--- |
| Codigo: | <span>CU-309</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Redirección a los sistemas de facturación digital para proveedores y usuarios.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Tener contratado el servicio con el municipio.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona el enlace de facturación. <br>2.- El sistema deriva al portal especializado FACE o equivalente bancario local.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario se encuentra en la plataforma de gestión de recibos digitales.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Ver webs municipales

| Nombre: | <span>Ver webs municipales</span> |
| :--- | :--- |
| Codigo: | <span>CU-310</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Guía de portales vinculados al ayuntamiento (bibliotecas, deportes, etc.).</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Navegar en el portal municipal.</span> |
| Flujo Normal: | <span>1.- El usuario consulta el listado de portales amigos y webs oficiales de la ciudad. <br>2.- Al pulsar un enlace, el sistema abre la web correspondiente en una pestaña nueva.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Navegación iniciada a una página externa vinculada.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Acceder a atencion ciudadana

| Nombre: | <span>Acceder a atencion ciudadana</span> |
| :--- | :--- |
| Codigo: | <span>CU-311</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Permite localizar canales de soporte, quejas y contacto directo.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Identificación básica.</span> |
| Flujo Normal: | <span>1.- El visitante hace clic sobre atención al ciudadano. <br>2.- El sistema presenta formularios de contacto, teléfonos y un chat de ayuda opcional.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario establece contacto informativo con la institución.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Ver areas municipales

| Nombre: | <span>Ver areas municipales</span> |
| :--- | :--- |
| Codigo: | <span>CU-312</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Consulta del organigrama institucional y las distintas concejalías.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Datos organizativos publicados.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona el organigrama político del ayuntamiento. <br>2.- El sistema muestra un listado con los responsables de cada área y sus funciones principales.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario conoce la estructura departamental municipal.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Acceder al portal de turismo

| Nombre: | <span>Acceder al portal de turismo</span> |
| :--- | :--- |
| Codigo: | <span>CU-313</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Puente de navegación hacia la oficina de turismo digital local.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Estar navegando en el portal principal.</span> |
| Flujo Normal: | <span>1.- El visitante pulsa en el acceso directo de turismo del menú lateral o footer. <br>2.- El sistema carga la interfaz dedicada a guías de viaje y monumentos.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Navegación terminada en el portal turístico.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Acceder al canal plenario

| Nombre: | <span>Acceder al canal plenario</span> |
| :--- | :--- |
| Codigo: | <span>CU-314</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Visualización de vídeos grabados o en directo de las sesiones del pleno.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Haber sesiones cargadas en el servidor de vídeo.</span> |
| Flujo Normal: | <span>1.- El visitante entra en la videoteca de plenos municipales. <br>2.- El sistema carga el reproductor y ofrece una lista de sesiones por fecha.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario visualiza la política local mediante contenidos audiovisuales.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Gestionar tramites

| Nombre: | <span>Gestionar tramites</span> |
| :--- | :--- |
| Codigo: | <span>CU-315</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Punto de entrada general para trámites administrativos del ciudadano.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Uso de identificación digital según el trámite.</span> |
| Flujo Normal: | <span>1.- El ciudadano gestiona sus tramites. <br>2.- .</span> |
| Flujo Alternativo: | <span>1a. Ver solicitudes: <br>1.- El visitante accede a sus solicitudes pendientes o finalizadas. <br> 1b. Ver contratos: <br>1.- El visitante accede a sus contratos. <br>1c. Ver factura electronica: <br>1.- El visitante accede sus facturas electronicas. <br>1d. Acceder a los pagos de tributos online: <br>1.- El visitante accede a sus pagos de tributos online. <br>2.- El sistema redirige a la pasarela bancaria oficial para la introducción de tarjeta. <br>1e. Acceder a la sede electronica: <br>1.- El visitante accede a la sede electronica.</span> |
| Poscondiciones: | <span>Gestión centralizada de trámites efectuada.</span> |
| Artefactos relacionados: | <span>CU-327, CU-328, CU-319, CU-318, CU-317</span> |

---

### Iniciar proceso de envio de incidencia

| Nombre: | <span>Iniciar proceso de envio de incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-316</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Arranque del flujo guiado para notificar desperfectos públicos.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>El ciudadano desea reportar un desperfecto urbano.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona la opcion de "Nueva incidencia". <br>2.- El visitante selecciona la categoria a la que pertenece la incidencia. <br>3.- El visitante selecciona el lugar donde ocurre la incidencia. <br>4.- El visitante describe la incidencia a reportar. <br>5.- El visitante introduce sus datos personales. <br>6.- El visitante manda la incidencia. <br>7.- El sistema guarda los datos y entrega un número de registro al ciudadano.</span> |
| Flujo Alternativo: | <span>4a. Adjuntar imagenes: <br>1.- El usuario decide si adjuntar imagenes o no. <br>2.- El flujo de ejecucion retorna al flujo principal.</span> |
| Poscondiciones: | <span>Registro inicial de incidencia abierto.</span> |
| Artefactos relacionados: | <span>CU-320</span> |

---

### Ver solicitudes

| Nombre: | <span>Ver solicitudes</span> |
| :--- | :--- |
| Codigo: | <span>CU-317</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Permite comprobar el estado y las respuestas a escritos realizados.</span> |
| Actores: | <span>Visitante (Vía CU-315)</span> |
| Precondiciones: | <span>Sesión administrativa iniciada.</span> |
| Flujo Normal: | <span>1.- El visitante accede a sus solicitudes pendientes o finalizadas.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Consulta de expedientes administrativos terminada.</span> |
| Artefactos relacionados: | <span>CU-315</span> |

---

### Ver contratos

| Nombre: | <span>Ver contratos</span> |
| :--- | :--- |
| Codigo: | <span>CU-318</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Acceso a documentos contractuales públicos asociados al perfil.</span> |
| Actores: | <span>Visitante (Vía CU-315)</span> |
| Precondiciones: | <span>Ser poseedor de un contrato firmado con el ayuntamiento.</span> |
| Flujo Normal: | <span>1.- El visitante accede a sus contratos.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El ciudadano accede a sus contratos municipales.</span> |
| Artefactos relacionados: | <span>CU-315</span> |

---

### Ver factura electronica (tramites)

| Nombre: | <span>Ver factura electronica</span> |
| :--- | :--- |
| Codigo: | <span>CU-319</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Consulta de justificantes de pago internos de gestiones.</span> |
| Actores: | <span>Visitante (Vía CU-315)</span> |
| Precondiciones: | <span>Existencia de facturas emitidas al ciudadano.</span> |
| Flujo Normal: | <span>1.- El visitante accede sus facturas electronicas.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Información de facturación municipal consultada.</span> |
| Artefactos relacionados: | <span>CU-315</span> |

---

### Seleccionar la categoria de incidencia

| Nombre: | <span>Seleccionar la categoria de incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-320</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Clasificación del desperfecto (limpieza, vías, alumbrado).</span> |
| Actores: | <span>Visitante (Iniciado por CU-316)</span> |
| Precondiciones: | <span>Estar dentro del proceso de reporte.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona la categoria a la que pertenece la incidencia.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Categoría vinculada al reporte.</span> |
| Artefactos relacionados: | <span>CU-316, CU-321</span> |

---

### Seleccionar lugar de la incidencia

| Nombre: | <span>Seleccionar lugar de la incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-321</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Indicar mediante mapa o dirección física la localización del problema.</span> |
| Actores: | <span>Visitante (Iniciado por CU-320)</span> |
| Precondiciones: | <span>Tener categoría seleccionada.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona el lugar donde ocurre la incidencia.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Ubicación geográfica asignada a la queja.</span> |
| Artefactos relacionados: | <span>CU-320, CU-322</span> |

---

### Describir la incidencia

| Nombre: | <span>Describir la incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-322</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Explicación textual y gráfica del problema reportado.</span> |
| Actores: | <span>Visitante (Iniciado por CU-321)</span> |
| Precondiciones: | <span>Haber situado la incidencia.</span> |
| Flujo Normal: | <span>1.- El visitante describe la incidencia a reportar.</span> |
| Flujo Alternativo: | <span>1a. Adjuntar imagenes: <br>1.- El usuario decide si adjuntar imagenes o no. <br>2.- El flujo de ejecucion retorna al flujo principal.</span> |
| Poscondiciones: | <span>El reporte cuenta con una descripción detallada.</span> |
| Artefactos relacionados: | <span>CU-321, CU-323, CU-324</span> |

---

### Adjuntar imagenes

| Nombre: | <span>Adjuntar imagenes</span> |
| :--- | :--- |
| Codigo: | <span>CU-323</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Funcionalidad para subir fotografías desde el dispositivo personal.</span> |
| Actores: | <span>Visitante (Vía CU-322)</span> |
| Precondiciones: | <span>Permisos de cámara o acceso a archivos concedidos.</span> |
| Flujo Normal: | <span>1.- El usuario decide si adjuntar imagenes o no.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Imágenes incorporadas al trámite administrativo.</span> |
| Artefactos relacionados: | <span>CU-322</span> |

---

### Introducir datos personales

| Nombre: | <span>Introducir datos personales</span> |
| :--- | :--- |
| Codigo: | <span>CU-324</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Recopilación de información de contacto para informar al ciudadano.</span> |
| Actores: | <span>Visitante (Iniciado por CU-322)</span> |
| Precondiciones: | <span>Descripción de queja finalizada.</span> |
| Flujo Normal: | <span>1.- El visitante introduce sus datos personales. <br>2.- El visitante manda la incidencia. <br>3.- El sistema guarda los datos y entrega un número de registro al ciudadano.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El ciudadano ha aportado su identificación para el seguimiento.</span> |
| Artefactos relacionados: | <span>CU-322, CU-325</span> |

---

### Enviar incidencia

| Nombre: | <span>Enviar incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-325</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Acción que transmite la información del ciudadano al servidor municipal.</span> |
| Actores: | <span>Visitante (Iniciado por CU-324)</span> |
| Precondiciones: | <span>Haber cumplimentado todos los pasos guiados.</span> |
| Flujo Normal: | <span>1.- El visitante manda la incidencia. <br>2.- El sistema guarda los datos y entrega un número de registro al ciudadano.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Trámite de incidencia enviado satisfactoriamente.</span> |
| Artefactos relacionados: | <span>CU-324</span> |

---

### Acceder a la pasarela de pago

| Nombre: | <span>Acceder a la pasarela de pago</span> |
| :--- | :--- |
| Codigo: | <span>CU-326</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Entrada segura al módulo de transacciones económicas bancarias.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Acceso al servidor bancario disponible.</span> |
| Flujo Normal: | <span>1.- El sistema redirige a la pasarela bancaria oficial para la introducción de tarjeta.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario entra en el entorno seguro de pagos.</span> |
| Artefactos relacionados: | <span>CU-327</span> |

---

### Acceder a los pagos de tributos online

| Nombre: | <span>Acceder a los pagos de tributos online</span> |
| :--- | :--- |
| Codigo: | <span>CU-327</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Liquidación específica de impuestos locales (IBI, circulación).</span> |
| Actores: | <span>Visitante (Vía CU-326)</span> |
| Precondiciones: | <span>Tener tributos pendientes de pago asociados al perfil.</span> |
| Flujo Normal: | <span>1.- El visitante accede a sus pagos de tributos online. </span> |
| Flujo Alternativo: | <span>1a. Acceder a la pasarela de pago: <br>1.- El sistema redirige a la pasarela bancaria oficial para la introducción de tarjeta.</span> |
| Poscondiciones: | <span>Tributo municipal pagado telemáticamente.</span> |
| Artefactos relacionados: | <span>CU-315, CU-326</span> |

---

### Acceder a la Sede Electronica

| Nombre: | <span>Acceder a la Sede Electronica</span> |
| :--- | :--- |
| Codigo: | <span>CU-328</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Navegación al entorno de trámites oficiales certificados.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Disponer de medios de identificación digital opcionalmente.</span> |
| Flujo Normal: | <span>1.- El visitante accede a la sede electronica.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Navegación efectuada a la sede del ayuntamiento.</span> |
| Artefactos relacionados: | <span>CU-315</span> |

---

### Acceder al portal de transparencia

| Nombre: | <span>Acceder al portal de transparencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-329</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Consulta de datos públicos abiertos municipales.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Información de transparencia disponible para el público.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona transparencia institucional. <br>2.- El sistema carga los datos de sueldos públicos, presupuestos y contratos abiertos.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Ciudadano informado mediante datos abiertos.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Visitar las redes sociales

| Nombre: | <span>Visitar las redes sociales</span> |
| :--- | :--- |
| Codigo: | <span>CU-330</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Conectar con los perfiles institucionales externos del municipio.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Enlaces sociales cargados en el sistema.</span> |
| Flujo Normal: | <span>1.- El usuario selecciona el icono de red social institucional del menú lateral. <br>2.- El sistema abre el perfil de Instagram o Facebook oficial en una pestaña externa.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Usuario navegando por los canales sociales del ayuntamiento.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Acceder a la agenda de eventos

| Nombre: | <span>Acceder a la agenda de eventos</span> |
| :--- | :--- |
| Codigo: | <span>CU-331</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Visualización del calendario institucional de actividades.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Agenda publicada.</span> |
| Flujo Normal: | <span>1.- El ciudadano abre la agenda de eventos. <br>2.- El sistema lista los eventos próximos por fecha y categoría. <br>3.- El visitante selecciona un dia de la agenda para ver los eventos. <br>4.- El visitante clica sobre un evento para observar sus detalles.</span> |
| Flujo Alternativo: | <span>2a. Ver tour virtual: <br>1.- El visitante clica en el banner de ver tour virtual. <br>2.- Se le muestra al visitante un tour virtual por los puntos de interes de Benavente. <br>1b. Seleccionar la categoria del evento> <br>1.- El visitante filtra los eventos seleccionando una categoria. <br>1c. Buscar nombre del evento: <br>1.- El visitante filtra los eventos buscando por el nombre de uno en especifico. <br>4a. Añadir evento al calendario: <br>1.- El visitante decide añadir el evento seleccionado a su calendario. <br>2.- El sistema interactua con la API de google calendar y le añade un recordatorio al visitane. <br>4b. Compartir evento en redes sociales: <br>1.- El visitante decide compartir el evento en sus redes sociales. <br>2.- La pagina interactua con la API de las redes sociales seleccionadas por el visitante y publica un post sobre el evento. <br>4c. Acceder al portal del organizador del evento: <br>1.- El visitante clica en el enlace externo para ver el organizador del evento. <br>2.- El visitante es redirigido al portal web del organizador.</span> |
| Poscondiciones: | <span>El usuario conoce la programación cultural local.</span> |
| Artefactos relacionados: | <span>CU-334, CU-335, CU-336, CU-337</span> |

---

### Ver evento

| Nombre: | <span>Ver evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-332</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Ficha de detalle de una actividad específica de la agenda.</span> |
| Actores: | <span>Visitante (Vía CU-331)</span> |
| Precondiciones: | <span>Evento seleccionado de la lista.</span> |
| Flujo Normal: | <span>1.- El visitante clica sobre un evento para observar sus detalles.</span> |
| Flujo Alternativo: | <span>1a. Añadir evento al calendario: <br>1.- El visitante decide añadir el evento seleccionado a su calendario. <br>2.- El sistema interactua con la API de google calendar y le añade un recordatorio al visitane. <br>1b. Compartir evento en redes sociales: <br>1.- El visitante decide compartir el evento en sus redes sociales. <br>2.- La pagina interactua con la API de las redes sociales seleccionadas por el visitante y publica un post sobre el evento. <br>1c. Acceder al portal del organizador del evento: <br>1.- El visitante clica en el enlace externo para ver el organizador del evento. <br>2.- El visitante es redirigido al portal web del organizador.</span> |
| Poscondiciones: | <span>Información detallada del evento obtenida.</span> |
| Artefactos relacionados: | <span>CU-340, CU-339, CU-338</span> |

---

### Buscar información

| Nombre: | <span>Buscar información</span> |
| :--- | :--- |
| Codigo: | <span>CU-333</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Motor de búsqueda general en todo el portal.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Conexión al servidor.</span> |
| Flujo Normal: | <span>1.- El usuario introduce texto en la barra de búsqueda principal. <br>2.- El sistema devuelve enlaces a noticias, trámites o avisos que coincidan.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Contenidos localizados rápidamente.</span> |
| Artefactos relacionados: | <span>N/A</span> |

---

### Ver tour virtual

| Nombre: | <span>Ver tour virtual</span> |
| :--- | :--- |
| Codigo: | <span>CU-334</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Experiencia inmersiva en monumentos o museos digitales.</span> |
| Actores: | <span>Visitante (Vía CU-313)</span> |
| Precondiciones: | <span>Navegador compatible con 360 grados.</span> |
| Flujo Normal: | <span>1.- El visitante clica en el banner de ver tour virtual. <br>2.- Se le muestra al visitante un tour virtual por los puntos de interes de Benavente.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Interacción digital con el patrimonio local terminada.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Seleccionar día del evento

| Nombre: | <span>Seleccionar día del evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-335</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Filtrado de la agenda municipal por fechas concretas.</span> |
| Actores: | <span>Visitante (Vía CU-331)</span> |
| Precondiciones: | <span>Agenda cargada.</span> |
| Flujo Normal: | <span>1.- El visitante selecciona un dia de la agenda para ver los eventos. <br>2.- El visitante clica sobre un evento para observar sus detalles.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Agenda filtrada cronológicamente.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Seleccionar categoría de evento

| Nombre: | <span>Seleccionar categoría de evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-336</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Filtrado de la agenda municipal por temáticas.</span> |
| Actores: | <span>Visitante (Vía CU-331)</span> |
| Precondiciones: | <span>Agenda cargada.</span> |
| Flujo Normal: | <span>1.- El visitante filtra los eventos seleccionando una categoria.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Agenda filtrada temáticamente.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Buscar nombre del evento

| Nombre: | <span>Buscar nombre del evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-337</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Búsqueda directa por título dentro de la agenda.</span> |
| Actores: | <span>Visitante (Vía CU-331)</span> |
| Precondiciones: | <span>Agenda cargada.</span> |
| Flujo Normal: | <span>1.- El visitante filtra los eventos buscando por el nombre de uno en especifico.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Actividad localizada dentro de la agenda.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Añadir evento al calendario

| Nombre: | <span>Añadir evento al calendario</span> |
| :--- | :--- |
| Codigo: | <span>CU-338</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Exportar cita a Google Calendar o Outlook.</span> |
| Actores: | <span>Visitante (Vía CU-332)</span> |
| Precondiciones: | <span>Ficha de evento abierta.</span> |
| Flujo Normal: | <span>1.- El visitante decide añadir el evento seleccionado a su calendario. <br>2.- El sistema interactua con la API de google calendar y le añade un recordatorio al visitane.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Actividad guardada en el dispositivo personal.</span> |
| Artefactos relacionados: | <span>CU-332</span> |

---

### Compartir evento en redes sociales

| Nombre: | <span>Compartir evento en redes sociales</span> |
| :--- | :--- |
| Codigo: | <span>CU-339</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Difusión de una actividad concreta en perfiles sociales personales.</span> |
| Actores: | <span>Visitante (Vía CU-332)</span> |
| Precondiciones: | <span>Ficha de evento abierta.</span> |
| Flujo Normal: | <span>1.- 1.- El visitante decide compartir el evento en sus redes sociales. <br>2.- La pagina interactua con la API de las redes sociales seleccionadas por el visitante y publica un post sobre el evento.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Enlace difundido públicamente.</span> |
| Artefactos relacionados: | <span>CU-332</span> |

---

### Acceder al portal del organizador del evento

| Nombre: | <span>Acceder al portal del organizador del evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-340</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Navegación al sitio externo del promotor o club deportivo.</span> |
| Actores: | <span>Visitante (Vía CU-332)</span> |
| Precondiciones: | <span>Enlace externo vinculado en la ficha.</span> |
| Flujo Normal: | <span>1.- El visitante clica en el enlace externo para ver el organizador del evento. <br>2.- El visitante es redirigido al portal web del organizador.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario se informa en la fuente directa del evento.</span> |
| Artefactos relacionados: | <span>CU-332</span> |

---

### 4.3 Diagramas de clases asociados a los requisitos de información

Foto base de datos


| **INF-001** | **Usuario** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Auditoría del sistema</li></ul> |
| **Descripción** | Registra las acciones CRUD realizadas por los usuarios. |
| **Datos específicos** | <ul><li>id_log INT (PK)</li><li>entidad_modificada VARCHAR(255)</li><li>tipo_operacion VARCHAR(255)</li><li>fecha_hora TIMESTAMP</li><li>Usuarioid_usuario INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Fundamental para la trazabilidad y seguridad legal del sistema. |


| **INF-006** | **Evento** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Publicación de eventos culturales</li><li>Consultar Agenda</li></ul> |
| **Descripción** | Almacena la información principal de los eventos de la ciudad. |
| **Datos específicos** | <ul><li>id_evento INT (PK)</li><li>titulo VARCHAR(255)</li><li>sinopsis VARCHAR(255)</li><li>fecha_hora_inicio TIME</li><li>es_pago BIT</li><li>Usuarioid_usuario INT (FK)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Posee enlaces a portal, fotos y categorías para su clasificación. |

---

| **INF-007** | **Portal** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Taxonomía del sistema</li></ul> |
| **Descripción** | Clasificación transversal recursiva (categorías y subcategorías). |
| **Datos específicos** | <ul><li>id_categoria INT (PK)</li><li>nombre VARCHAR(255)</li><li>Categoriaid_categoria INT (FK recursiva)</li><li>Usuarioid_usuario INT (FK Creador)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Clasifica eventos, incidencias, anuncios y archivos. |


| **INF-010** | **IncidenciaCiudadana** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Reporte de daños</li><li>Seguimiento de reparaciones</li></ul> |
| **Descripción** | Reportes de ciudadanos sobre mobiliario o servicios públicos. |
| **Datos específicos** | <ul><li>id_incidencia INT (PK)</li><li>latitud/longitud DOUBLE</li><li>estado VARCHAR(255)</li><li>fecha_creacion TIME</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Incluye datos de contacto y GPS para localización exacta del reporte. |

---

| **INF-011** | **RecursoTuristico** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Mapa turístico</li></ul> |
| **Descripción** | Información de monumentos, parques y puntos de interés. |
| **Datos específicos** | <ul><li>id_recurso INT (PK)</li><li>direccion VARCHAR(255)</li><li>horario VARCHAR(255)</li><li>url_tour_virtual VARCHAR(255)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Vinculado a categorías turísticas para filtrado en la app/web. |

---

| **INF-012** | **Asociacion** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Registro de Asociaciones</li></ul> |
| **Descripción** | Entidades vecinales o culturales que solicitan espacios municipales. |
| **Datos específicos** | <ul><li>id_asociacion INT (PK)</li><li>nombre VARCHAR(255)</li><li>aforo INT</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Fundamental para controlar quién realiza la reserva de locales públicos. |

---

| **INF-013** | **EspacioReservable** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Inventario de centros municipales</li></ul> |
| **Descripción** | Salas, centros o recintos disponibles para reserva. |
| **Datos específicos** | <ul><li>id_reserva INT (PK - Espacio)</li><li>aforo INT</li><li>nombre VARCHAR(255)</li></ul> |
| **Importancia** | Media |
| **Estado** | Aceptado |
| **Comentarios** | Define la capacidad máxima para contrastar con el aforo de la asociación. |

---

| **INF-014** | **Reserva** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Gestión de alquileres</li></ul> |
| **Descripción** | Gestiona el calendario de uso de los espacios reservables. |
| **Datos específicos** | <ul><li>id_reserva INT (PK)</li><li>fecha_hora_inicio/fin TIME</li><li>estado VARCHAR(255)</li><li>Asociacionid_asociacion INT (FK)</li><li>EspacioReservableid_reserva INT (FK)</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Controla el flujo de aprobación y disponibilidad horaria. |

---

| **INF-015** | **Foto** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
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
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Tablón de anuncios</li></ul> |
| **Descripción** | Comunicaciones breves de ciudadanos o la administración. |
| **Datos específicos** | <ul><li>id_anuncio INT (PK)</li><li>texto VARCHAR(255)</li><li>Usuarioid_usuario INT (FK)</li><li>Categoriaid_categoria INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Clasificado por categorías. |

---

| **INF-018** | **RRSS** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Social Media Feed</li></ul> |
| **Descripción** | Almacena enlaces a redes sociales vinculados a eventos o noticias. |
| **Datos específicos** | <ul><li>id_RRSS INT (PK)</li><li>URL VARCHAR(255)</li><li>Noticiaid_noticia INT (FK)</li><li>Eventoid_evento INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Permite rastrear la repercusión social del contenido. |

---

| **INF-019** | **Formulario** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Generador de Forms</li></ul> |
| **Descripción** | Define la cabecera de formularios de captura de datos dinámicos. |
| **Datos específicos** | <ul><li>id_formulario INT (PK)</li><li>PostURL VARCHAR(255)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Estructura para crear trámites online sin cambiar el código. |

---

| **INF-020** | **Campos** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Diagrama E-R |
| **Referencias** | <ul><li>Definición de inputs</li></ul> |
| **Descripción** | Define los campos individuales, su tipo y posición en un formulario. |
| **Datos específicos** | <ul><li>id_campos INT (PK)</li><li>tipo, orden, PosX, PosY INT</li><li>Formularioid_formulario INT (FK)</li></ul> |
| **Importancia** | Baja |
| **Estado** | Aceptado |
| **Comentarios** | Permite el diseño visual de formularios desde la base de datos. |

---

## 5. Apéndices

Preguntas y respuestas de la entrevista.
