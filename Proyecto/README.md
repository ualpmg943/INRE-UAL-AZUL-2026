## **Init Proyecto**
## Introducción:
El presente documento especifica la solución técnica y funcional para la transformación digital del ecosistema turístico de Benavente, un proyecto estratégico impulsado por el Plan de Sostenibilidad Turística en Destino y los fondos Next Generation EU. El propósito fundamental no es solo la renovación estética de los portales web, sino la implantación de una arquitectura de información centralizada que dinamice la promoción del destino y agilice la gestión interna de sus recursos culturales.

El núcleo de la intervención reside en el desarrollo del nuevo Portal de Turismo y Cultura, concebido como una plataforma de servicios interactivos para el visitante y no como un mero escaparate estático. Esta herramienta permitirá la geolocalización de recursos, la planificación de visitas y la gestión integral de la agenda cultural, integrando capacidades transaccionales para la venta de entradas mediante pasarelas externas. De forma paralela, se digitalizan procesos críticos para el tejido social del municipio, como la gestión de solicitudes y reservas de espacios por parte de las asociaciones locales, automatizando flujos que actualmente requieren intervención manual.

Para sostener este ecosistema, la solución abarca también la actualización tecnológica del Portal Web Oficial y la normalización de la Identidad Corporativa. Aunque el foco prioritario es la proyección turística, el portal institucional actuará como garante de la unicidad del dato, asegurando que la información de eventos y noticias se sincronice bidireccionalmente entre departamentos, evitando duplicidades y garantizando el cumplimiento de los esquemas de seguridad y accesibilidad vigentes.
## 2.	Información del Dominio del problema:
El desarrollo de software para la gestión de un destino turístico requiere una alineación precisa entre los procesos administrativos del Ayuntamiento y la lógica técnica de la plataforma. Para garantizar que la solución responda a la realidad operativa del área de Turismo, se ha modelado el dominio del problema atendiendo a dos dimensiones críticas: la estructura de roles y la semántica del negocio.

En primer lugar, la definición del Modelo Organizativo es indispensable para trasladar la jerarquía administrativa al sistema de permisos del software. A través de la representación visual de los actores, se delimitan las fronteras de responsabilidad entre los distintos perfiles intervinientes: desde los administrativos encargados de la redacción y carga de eventos, pasando por los responsables de validación que autorizan la publicación, hasta las entidades externas (asociaciones) que interactúan con el sistema para gestionar recursos. Este mapeo es vital para configurar los flujos de trabajo (workflows) de aprobación y publicación de contenidos.

Complementariamente, se establece un Diccionario de Conceptos (Glosario) que unifica el lenguaje entre el equipo técnico y los gestores municipales. Dada la naturaleza específica del sector, es necesario desambiguar términos operativos como "evento recurrente", "recurso visitable", "bloqueo de agenda" o "itinerario". Esta base terminológica asegura que las reglas de negocio implementadas —por ejemplo, cómo se comporta una reserva o cuándo caduca una noticia— coincidan exactamente con las expectativas de gestión del servicio de Turismo.

A continuación, se detallan estos artefactos de análisis para sentar las bases del diseño funcional.

## Diagrama BPMN 1:

### Parte 1: Proceso de creación y contratación de eventos
El administrativo da de alta un evento en la agenda turistica, con la informacion del evento (fecha, hora, sinopsis, lugar, descripcion, mapa, foto). Si el evento es de pago, el administrativo pone un enlace externo a una pasarela de pago para comprar los tickets. La pasarela pide los datos bancarios y personales. Si el usuario rechaza el pago se le devuelve al portal web, si acepta el pago, la pasarela manda al usuario los datos del ticket y el recibo, y tambien los envia a la base de datos de la pagina de turismo.

<p align="center">
  <img src="BPMN_1_proyecto.drawio.svg" alt="img_bpmn_1" width="750">
</p>

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

### Parte 2: Proceso de eliminación de eventos finalizados
Si el evento ha finalizado, hay otro proceso que elimina el evento de la agenda cuando pasen 5 dias de su finalizacion.

<p align="center">
  <img src="BPMN_1_2_inre.drawio.svg" alt="img_bpmn_2" width="750">
</p>

| *Código de tarea* | *Nombre* | *Descripción* |
| :--- | :--- | :--- |
| *T-01* | **Elimina el evento de la agenda** | Una vez que este proceso se activa al haber finalizado el evento, y transcurren 5 días desde su finalización, el sistema elimina dicho evento de la agenda turística. |

## Diagrma BPMN 2: Gestion de reservas para asociaciones.
Las asociaciones locales solicitan reservas mediante un formulario en el portal web de turismo adjuntando su correo electrónico con la fecha en la que quieren reservar un lugar. La reserva llega al sistema, se puede rechazar por problemas de disponibilidad y se le envian sugerencias a la asociación con otros lugares disponibles. Si la reserva se acepta, se bloquea la franja horaria reservada.

<p align="center">
  <img src="bpmn2_inre_proyecto.drawio.svg" alt="img_bpmn_2" width="750">
</p>

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
