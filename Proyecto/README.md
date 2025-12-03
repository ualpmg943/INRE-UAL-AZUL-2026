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
## BPMN 1:

<p align="center">
  <img src="BPMN_1_proyecto.drawio.svg" alt="img_bpmn_1" width="750">
</p>

## BPMN 2:

<p align="center">
  <img src="bpmn2_inre_proyecto.drawio.svg" alt="img_bpmn_2" width="750">
</p>
