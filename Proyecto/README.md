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

$ Descripción generica del apartado de requisitos$

## 4.1 Requisitos

$ Foto del diagrama de requisitos aqui (diagrama de bases de datos)$

## 4.2 Casos de Uso

### 4.2.1 Lista de diagramas de casos de uso del modelo

Fotos de los diagramas de casos de uso

#### 4.2.2 Lista general de casos de uso

Tabla solo de los nombres y codigo de cada caso de uso

| Código | Nombre |
| :--- | :--- |
| <span>CU-301</span> | <span>Ver las Ferias y Fiestas del Toro Enmaromado</span> |

#### 4.2.3 Detalles de los casos de uso

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
| Artefactos relacionados: | <span>CU-303, CU-304, CU-305, CU-306, CU-307</span> |

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
| Artefactos relacionados: | <span>CU-302, CU-304</span> |

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
| Artefactos relacionados: | <span>CU-303</span> |

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
| Artefactos relacionados: | <span>CU-302, CU-306</span> |

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
| Artefactos relacionados: | <span>CU-305</span> |

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
| Artefactos relacionados: | <span>CU-302</span> |

---

### Ver tablon virtual

| Nombre: | <span>Ver tablon virtual</span> |
| :--- | :--- |
| Codigo: | <span>CU-308</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Visualización digital de edictos y avisos oficiales con validez legal.</span> |
| Actores: | <span>Visitante</span> |
| Precondiciones: | <span>Haber accedido a la sede electrónica.</span> |
| Flujo Normal: | <span>1.- El ciudadano abre el tablón virtual de edictos. <br>2.- El sistema permite navegar por los PDF de edictos firmados digitalmente por el ayuntamiento.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario consulta los documentos oficiales de interés público.</span> |
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
| Flujo Normal: | <span>1.- El ciudadano entra en su área de gestión personal. <br>2.- El sistema lista las incidencias, solicitudes o contratos asociados a su perfil.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Gestión centralizada de trámites efectuada.</span> |
| Artefactos relacionados: | <span>CU-316, CU-317, CU-318, CU-319</span> |

---

### Iniciar proceso de envio de incidencia

| Nombre: | <span>Iniciar proceso de envio de incidencia</span> |
| :--- | :--- |
| Codigo: | <span>CU-316</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Arranque del flujo guiado para notificar desperfectos públicos.</span> |
| Actores: | <span>Visitante (Iniciado por CU-315)</span> |
| Precondiciones: | <span>El ciudadano desea reportar un desperfecto urbano.</span> |
| Flujo Normal: | <span>1.- El usuario pulsa en enviar nueva queja o incidencia. <br>2.- El sistema abre el asistente para capturar los datos del problema.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Registro inicial de incidencia abierto.</span> |
| Artefactos relacionados: | <span>CU-315, CU-320</span> |

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
| Flujo Normal: | <span>1.- El sistema muestra un catálogo de categorías. <br>2.- El ciudadano elige la que mejor define el desperfecto.</span> |
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
| Flujo Normal: | <span>1.- El visitante marca sobre el plano de la ciudad el lugar exacto. <br>2.- El sistema registra las coordenadas GPS para los operarios.</span> |
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
| Flujo Normal: | <span>1.- El ciudadano escribe los detalles del incidente en el campo de texto. <br>2.- El ciudadano añade fotos opcionales del estado real de la incidencia.</span> |
| Flujo Alternativo: | <span></span> |
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
| Flujo Normal: | <span>1.- El usuario selecciona archivos de imagen de su galería. <br>2.- El sistema sube los archivos y los vincula a la incidencia.</span> |
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
| Flujo Normal: | <span>1.- El visitante rellena su nombre, email y teléfono en el formulario. <br>2.- El sistema valida que los campos sean correctos antes de proceder.</span> |
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
| Flujo Normal: | <span>1.- El usuario confirma el envío definitivo del reporte. <br>2.- El sistema guarda los datos y entrega un número de registro al ciudadano.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Trámite de incidencia enviado satisfactoriamente.</span> |
| Artefactos relacionados: | <span>CU-324</span> |

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
| Flujo Normal: | <span>1.- El ciudadano abre el historial de sus solicitudes administrativas. <br>2.- El sistema muestra el estado de trámite de cada petición.</span> |
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
| Flujo Normal: | <span>1.- El usuario solicita ver la lista de sus contratos registrados. <br>2.- El sistema permite descargar o visualizar los documentos en formato digital.</span> |
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
| Flujo Normal: | <span>1.- El ciudadano accede a la lista de sus facturas de trámites. <br>2.- El sistema muestra los datos de facturación e importes liquidados.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Información de facturación municipal consultada.</span> |
| Artefactos relacionados: | <span>CU-315</span> |

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
| Flujo Normal: | <span>1.- El ciudadano elige pagar una tasa o impuesto online. <br>2.- El sistema redirige a la pasarela bancaria oficial para la introducción de tarjeta.</span> |
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
| Flujo Normal: | <span>1.- El usuario introduce su referencia catastral o DNI. <br>2.- El sistema localiza los impuestos adeudados y permite iniciar el ingreso.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Tributo municipal pagado telemáticamente.</span> |
| Artefactos relacionados: | <span>CU-326</span> |

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
| Flujo Normal: | <span>1.- El ciudadano clica sobre el banner de Sede Electrónica. <br>2.- El sistema carga el portal oficial de gestiones burocráticas certificadas.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Navegación efectuada a la sede del ayuntamiento.</span> |
| Artefactos relacionados: | <span>N/A</span> |

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
| Flujo Normal: | <span>1.- El ciudadano abre el calendario municipal. <br>2.- El sistema lista los eventos próximos por fecha y categoría.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario conoce la programación cultural local.</span> |
| Artefactos relacionados: | <span>CU-332, CU-333, CU-334</span> |

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
| Flujo Normal: | <span>1.- El usuario pulsa en el titular del evento. <br>2.- El sistema abre la ficha técnica (horarios, lugar, descripción).</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Información detallada del evento obtenida.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

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
| Flujo Normal: | <span>1.- El turista elige visitar virtualmente un monumento. <br>2.- El sistema carga el visor panorámico interactivo.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Interacción digital con el patrimonio local terminada.</span> |
| Artefactos relacionados: | <span>CU-313</span> |

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
| Flujo Normal: | <span>1.- El usuario selecciona un día en el calendario interactivo. <br>2.- El sistema actualiza la lista solo con eventos para ese día.</span> |
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
| Flujo Normal: | <span>1.- El usuario elige una temática (deportes, cultura) del menú lateral. <br>2.- El sistema actualiza la lista con eventos que coincidan.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Agenda filtrada temáticamente.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Buscar nombre del evento (Filtro)

| Nombre: | <span>Buscar nombre del evento</span> |
| :--- | :--- |
| Codigo: | <span>CU-337</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Búsqueda directa por título dentro de la agenda.</span> |
| Actores: | <span>Visitante (Vía CU-331)</span> |
| Precondiciones: | <span>Agenda cargada.</span> |
| Flujo Normal: | <span>1.- El usuario escribe el nombre de la actividad en el filtro. <br>2.- El sistema busca coincidencias en tiempo real sobre el listado.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Actividad localizada dentro de la agenda.</span> |
| Artefactos relacionados: | <span>CU-331</span> |

---

### Añadir evento al calendario (Personal)

| Nombre: | <span>Añadir evento al calendario</span> |
| :--- | :--- |
| Codigo: | <span>CU-338</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Exportar cita a Google Calendar o Outlook.</span> |
| Actores: | <span>Visitante (Vía CU-332)</span> |
| Precondiciones: | <span>Ficha de evento abierta.</span> |
| Flujo Normal: | <span>1.- El ciudadano pulsa en añadir a mi calendario personal. <br>2.- El sistema genera un archivo .ics para la descarga.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>Actividad guardada en el dispositivo personal.</span> |
| Artefactos relacionados: | <span>CU-332</span> |

---

### Compartir evento en redes sociales (Post)

| Nombre: | <span>Compartir evento en redes sociales</span> |
| :--- | :--- |
| Codigo: | <span>CU-339</span> |
| Autor: | <span>INRE Equipo Azul</span> |
| Fecha: | <span>08/12/2025</span> |
| Descripción: | <span>Difusión de una actividad concreta en perfiles sociales personales.</span> |
| Actores: | <span>Visitante (Vía CU-332)</span> |
| Precondiciones: | <span>Ficha de evento abierta.</span> |
| Flujo Normal: | <span>1.- El ciudadano elige compartir en WhatsApp o Twitter. <br>2.- El sistema genera el enlace directo con un mensaje predefinido.</span> |
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
| Flujo Normal: | <span>1.- El usuario clica en el nombre del organizador. <br>2.- El navegador abre la web del organizador en ventana nueva.</span> |
| Flujo Alternativo: | <span></span> |
| Poscondiciones: | <span>El usuario se informa en la fuente directa del evento.</span> |
| Artefactos relacionados: | <span>CU-332</span> |

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
| **Artefactos relacionados:**| <span>CU-202, CU-203, CU-204</span> |

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
| **Artefactos relacionados:**| <span>CU-207</span> |

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

### Buscar informacion turismo

| **Nombre:** | <span>Buscar informacion turismo</span> |
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

### Acceder a las redes sociales turismo

| **Nombre:** | <span>Acceder a las redes sociales turismo</span> |
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

### Ver informacion util turismo

| **Nombre:** | <span>Ver informacion util turismo</span> |
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

### Ver rutas por Benavente

| **Nombre:** | <span>Ver rutas por Benavente</span> |
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
| **Flujo Alternativo:** | <span>1A.- Si no está registrado, se le solicita registro o inicio de sesión.</span> |
| **Poscondiciones:**| <span>El turista obtiene sus entradas.</span> |
| **Artefactos relacionados:**| <span>CU-213, CU-214, CU-215, CU-216, CU-217</span> |

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
| **Artefactos relacionados:**| <span>CU-212, CU-214</span> |

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
| **Artefactos relacionados:**| <span>CU-212, CU-213</span> |

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
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista conoce la programación.</span> |
| **Artefactos relacionados:**| <span>CU-212, CU-217</span> |

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
| **Artefactos relacionados:**| <span>CU-212</span> |

---

### Abrir mapa en google maps

| **Nombre:** | <span>Abrir mapa en google maps</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-218</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Lanzar la aplicación externa de mapas.</span> |
| **Actores:** | <span>Turista, Cliente</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista pulsa en cómo llegar. <br>2.- El sistema abre Google Maps con la ruta.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista navega con el GPS.</span> |
| **Artefactos relacionados:**| <span>CU-212, CU-220</span> |

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
| **Artefactos relacionados:**| <span>CU-212, CU-218</span> |

---

### Acceder a la agenda de eventos turismo

| **Nombre:** | <span>Acceder a la agenda de eventos turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-220</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Calendario general de actividades turísticas.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista abre la agenda. <br>2.- El turista ve los eventos del mes.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista consulta la oferta de ocio.</span> |
| **Artefactos relacionados:**| <span>CU-224, CU-225</span> |

---

### Seleccionar dia del evento turismo

| **Nombre:** | <span>Seleccionar dia del evento turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-221</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Filtrado de agenda por fecha.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista elige un día específico. <br>2.- El sistema muestra solo eventos de ese día.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista filtra los resultados.</span> |
| **Artefactos relacionados:**| <span>CU-224, CU-223</span> |

---

### Ver evento turismo

| **Nombre:** | <span>Ver evento turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-222</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Detalle de una actividad turística concreta.</span> |
| **Actores:** | <span>Turista</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona una actividad. <br>2.- El turista revisa toda la información asociada.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El turista se informa del evento.</span> |
| **Artefactos relacionados:**| <span>CU-216, CU-227, CU-228</span> |

---

### Buscar nombre del evento turismo

| **Nombre:** | <span>Buscar nombre del evento turismo</span> |
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
| **Artefactos relacionados:**| <span>CU-224, CU-221</span> |

---

### Seleccionar categoria de evento turismo

| **Nombre:** | <span>Seleccionar categoria de evento turismo</span> |
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
| **Artefactos relacionados:**| <span>CU-220, CU-223, CU-221</span> |

---

### Ver tour virtual turismo

| **Nombre:** | <span>Ver tour virtual turismo</span> |
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

### Acceder al portal del organizador del evento turismo

| **Nombre:** | <span>Acceder al portal del organizador del evento turismo</span> |
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

### Compartir evento en redes sociales turismo

| **Nombre:** | <span>Compartir evento en redes sociales turismo</span> |
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

### Añadir evento al calendario turismo

| **Nombre:** | <span>Añadir evento al calendario turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-216</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>07/12/2025</span> |
| **Descripción:** | <span>Exportar cita a la agenda personal.</span> |
| **Actores:** | <span>N/A (Caso de uso incluido)</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El turista selecciona guardar en calendario. <br>2.- El sistema descarga el archivo .ics.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El evento queda agendado en el dispositivo del usuario.</span> |

| **Artefactos relacionados:**| <span>CU-222</span> |

---

### DCU - CMS

---

### 4.3 Diagramas de clases asociados a los requisitos de información

Foto base de datos y sus tablas

## 5. Apéndices

Preguntas y respuestas de la entrevista.
