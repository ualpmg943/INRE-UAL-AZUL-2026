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

### **Casos de Uso Adicionales Identificados (CU-331 a CU-340)**

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
