### Gestionar permisos

| **Nombre:** | <span>Gestionar permisos</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-101</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite al Administrador gestionar los permisos de los diferentes usuarios o roles dentro del sistema.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El Administrador debe estar autenticado en el sistema con privilegios de superusuario.</span> |
| **Flujo Normal:** | <span>1.- El Administrador accede al panel de gestión de usuarios. <br>2.- El Administrador busca y selecciona el usuario o rol a modificar. <br>3.- El Administrador marca o desmarca las casillas de permisos correspondientes. <br>4.- El Administrador guarda los cambios realizados.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>Los permisos del usuario o rol quedan actualizados en la base de datos.</span> |
| **Artefactos relacionados:**| <span>CU-102</span> |

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
| **Artefactos relacionados:**| <span>CU-101</span> |

---

### Crear portal

| **Nombre:** | <span>Crear portal</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-116</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite al Administrador generar una nueva instancia o subsitio dentro de la plataforma web.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El Administrador debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El Administrador selecciona la opción de crear nuevo portal. <br>2.- El Administrador define el nombre, la URL y selecciona una plantilla base. <br>3.- El Administrador finaliza el asistente de creación.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>Un nuevo portal queda creado y accesible para su configuración.</span> |
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
| **Artefactos relacionados:**| <span>CU-104, CU-105</span> |

---

### Crear formulario

| **Nombre:** | <span>Crear formulario</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-104</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Herramienta para diseñar formularios de recogida de datos.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El administrativo inicia el constructor de formularios. <br>2.- El administrativo arrastra y suelta los campos necesarios (texto, fecha, selección). <br>3.- El administrativo configura el correo de recepción de datos. <br>4.- El administrativo guarda y obtiene el código para insertar el formulario.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El formulario queda guardado y listo para usarse en una página.</span> |
| **Artefactos relacionados:**| <span>CU-103</span> |

---

### Publicar noticia

| **Nombre:** | <span>Publicar noticia</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-105</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite redactar y lanzar una noticia en el portal.</span> |
| **Actores:** | <span>Administrativo del portal general, Administrador</span> |
| **Precondiciones:**| <span>El actor debe tener el texto de la noticia redactado.</span> |
| **Flujo Normal:** | <span>1.- El actor accede al editor de noticias. <br>2.- El actor escribe el titular, entradilla y cuerpo. <br>3.- El actor extiende el proceso para subir multimedia si es necesario. <br>4.- El actor pulsa el botón de publicar.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La noticia es pública en el listado de actualidad.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-110, CU-106</span> |

---

### Publicar anuncio

| **Nombre:** | <span>Publicar anuncio</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-106</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite crear un comunicado oficial o anuncio destacado.</span> |
| **Actores:** | <span>Administrativo del portal general, Administrativo del portal de turismo</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona crear nuevo anuncio. <br>2.- El actor introduce la información relevante. <br>3.- El actor puede adjuntar archivos mediante la extensión subir multimedia. <br>4.- El actor confirma la publicación.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El anuncio aparece en la sección de avisos del portal.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-110, CU-105, CU-107</span> |

---

### Publicar evento en la agenda

| **Nombre:** | <span>Publicar evento en la agenda</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-107</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite añadir una cita al calendario de eventos del portal.</span> |
| **Actores:** | <span>Agenda, Administrativos</span> |
| **Precondiciones:**| <span>El evento debe tener fecha y hora confirmadas.</span> |
| **Flujo Normal:** | <span>1.- El actor accede a la gestión de la agenda. <br>2.- El actor crea una nueva entrada con fecha, hora y lugar. <br>3.- El actor guarda el evento en el sistema.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El evento es visible en el calendario para los visitantes.</span> |
| **Artefactos relacionados:**| <span>CU-110</span> |

---

### Realizar un cambio en el contenido general

| **Nombre:** | <span>Realizar un cambio en el contenido general</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-108</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Edición de contenidos existentes en el portal general.</span> |
| **Actores:** | <span>Administrativo del portal general</span> |
| **Precondiciones:**| <span>El contenido a editar debe existir.</span> |
| **Flujo Normal:** | <span>1.- El administrativo localiza el contenido que desea cambiar. <br>2.- El administrativo edita el texto o las opciones. <br>3.- El sistema registra los detalles del cambio automáticamente. <br>4.- El administrativo guarda la actualización.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido queda actualizado.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-113</span> |

---

### Eliminar contenido

| **Nombre:** | <span>Eliminar contenido</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-109</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Acción de borrar un elemento del sistema. Incluida en los flujos de cambio de contenido.</span> |
| **Actores:** | <span>N/A (Caso de uso incluido)</span> |
| **Precondiciones:**| <span>El actor tiene permisos de borrado.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona la opción de eliminar sobre un elemento. <br>2.- El actor confirma la acción en el mensaje de advertencia. <br>3.- El sistema elimina el registro.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido deja de existir en el portal.</span> |
| **Artefactos relacionados:**| <span>CU-108, CU-113</span> |

---

### Programar publicacion

| **Nombre:** | <span>Programar publicacion</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-110</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Permite diferir la publicación de un contenido a una fecha futura.</span> |
| **Actores:** | <span>N/A (Caso de uso de extensión)</span> |
| **Precondiciones:**| <span>El contenido está listo pero no se desea publicar ya.</span> |
| **Flujo Normal:** | <span>1.- El actor marca la opción de programar en lugar de publicar. <br>2.- Se ejecuta la inclusión de indicar fecha de publicación. <br>3.- El sistema guarda el contenido en estado pendiente.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
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
| **Actores:** | <span>N/A (Caso de uso de extensión)</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El actor accede a las opciones de caducidad. <br>2.- El actor selecciona el día en el calendario para la retirada del contenido.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El contenido se despublicará en la fecha indicada.</span> |
| **Artefactos relacionados:**| <span>CU-110, CU-113</span> |

---

### Indicar fecha de publicacion

| **Nombre:** | <span>Indicar fecha de publicacion</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-112</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Acción de seleccionar el día de inicio de visibilidad. Incluido en programar publicación.</span> |
| **Actores:** | <span>N/A (Caso de uso incluido)</span> |
| **Precondiciones:**| <span>N/A</span> |
| **Flujo Normal:** | <span>1.- El actor despliega el calendario. <br>2.- El actor clica en el día y hora deseados.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La fecha de inicio queda registrada.</span> |
| **Artefactos relacionados:**| <span>CU-110</span> |

---

### Realizar un cambio en el contenido turismo

| **Nombre:** | <span>Realizar un cambio en el contenido turismo</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-113</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Gestión de contenidos específica para el portal de turismo.</span> |
| **Actores:** | <span>Administrativo del portal de turismo</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el área de turismo.</span> |
| **Flujo Normal:** | <span>1.- El administrativo selecciona un recurso turístico. <br>2.- El administrativo modifica la descripción o fotos. <br>3.- El sistema registra los detalles de la auditoría. <br>4.- El administrativo guarda los cambios.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La información turística queda actualizada.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-111</span> |

---

### Subir multimedia

| **Nombre:** | <span>Subir multimedia</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-114</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Proceso de carga de archivos al servidor.</span> |
| **Actores:** | <span>N/A (Caso de uso de extensión)</span> |
| **Precondiciones:**| <span>El archivo debe cumplir los requisitos de tamaño y formato.</span> |
| **Flujo Normal:** | <span>1.- El actor pulsa el botón de añadir archivo. <br>2.- El actor explora su disco duro y elige el fichero. <br>3.- El sistema carga el fichero y confirma la subida.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>El archivo está disponible en la biblioteca de medios.</span> |
| **Artefactos relacionados:**| <span>CU-105, CU-106</span> |

---

### Registrar detalles

| **Nombre:** | <span>Registrar detalles</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-115</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>08/12/2025</span> |
| **Descripción:** | <span>Auditoría automática de acciones. Incluido en cambios de contenido.</span> |
| **Actores:** | <span>N/A (Caso de uso incluido)</span> |
| **Precondiciones:**| <span>Se ha realizado una acción de modificación.</span> |
| **Flujo Normal:** | <span>1.- El sistema captura el ID del usuario, la fecha y el tipo de cambio. <br>2.- El sistema escribe esta entrada en el log de operaciones.</span> |
| **Flujo Alternativo:** | <span>N/A</span> |
| **Poscondiciones:**| <span>La acción queda trazada para seguridad.</span> |
| **Artefactos relacionados:**| <span>CU-108, CU-113</span> |