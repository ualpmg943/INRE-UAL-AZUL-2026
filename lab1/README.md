# Lab 1 - Definición de casos de uso y requisitos de información

## Supuesto 1: Horarios

En una universidad, el personal del PDI, el personal del PAS y los estudiantes pueden consultar horarios. Por su parte, el personal del PAS puede modificar horarios y dar de alta estudiantes. El personal de PDI puede proponer cambios en los horarios y dar de alta estudiantes. La funcionalidad de dar de alta estudiantes del PAS realiza una verificación de los datos del estudiante. Sin embargo, la funcionalidad de dar de alta estudiantes del PDI, además de verificar los datos también permite de forma excepcional realizar la búsqueda en las listas de clase de sus asignaturas.

<p align="center">
  <img src="supuesto1.jpg" alt="img_supuesto1" width="750">
</p>

### Requisitos del diagrama de casos de uso

| **Nombre:** | <span>Proponer cambios en los horarios</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-101</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Permite al PDI proponer un cambio en un horario existente para su posterior revisión y aprobación.</span> |
| **Actores:** | <span>PDI</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema como PDI.</span> |
| **Flujo Normal:** | <span>1.- El PDI selecciona la opción para proponer un cambio de horario. <br>2.- El sistema muestra el horario actual. <br>3.- El PDI introduce los cambios deseados y una justificación. <br>4.- El sistema registra la propuesta y la envía para su aprobación.</span> |
| **Flujo Alternativo:** | <span>3.A- El PDI decide cancelar la operación y el sistema vuelve al menú principal.</span> |
| **Poscondiciones:**| <span>La propuesta de cambio de horario queda registrada en el sistema pendiente de aprobación.</span> |
| **Artefactos relacionados:**| <span></span> |

### ---

| **Nombre:** | <span>Dar alta estudiante</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-102</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Caso de uso general para dar de alta a un estudiante en el sistema. Incluye la verificación de los datos del estudiante.</span> |
| **Actores:** | <span>PDI, PAS</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El actor inicia el proceso de alta. <br>2.- El sistema solicita los datos del estudiante. <br>3.- El actor introduce los datos. <br>4.- Se ejecuta el caso de uso "Verificar datos del estudiante" (CU-105). <br>5.- El sistema confirma el alta del estudiante.</span> |
| **Flujo Alternativo:** | <span>4.A- Si la verificación de datos falla, el sistema informa al actor y permite corregir los datos.</span> |
| **Poscondiciones:**| <span>El estudiante queda registrado en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-103, CU-104, CU-105</span> |

### ---

| **Nombre:** | <span>Dar alta estudiante(PDI)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-103</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Dar alta estudiante" para el PDI. Opcionalmente, **extiende** la funcionalidad para buscar en la lista de clase.</span> |
| **Actores:** | <span>PDI</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como PDI.</span> |
| **Flujo Normal:** | <span>1.- El PDI inicia el proceso de alta. <br>2.- El sistema solicita los datos del estudiante. <br>3.- El PDI introduce los datos. <br>4.- Se ejecuta el caso de uso "Verificar datos del estudiante" (CU-105). <br>5.- El sistema confirma el alta.</span> |
| **Flujo Alternativo:** | <span>3.A- De forma excepcional, el PDI puede ejecutar el caso de uso "Realizar busqueda en la lista de clase" (CU-106) para autocompletar datos.</span> |
| **Poscondiciones:**| <span>El estudiante queda registrado en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-102, CU-105, CU-106</span> |

### ---

| **Nombre:** | <span>Dar alta estudiante(PAS)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-104</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Dar alta estudiante" para el PAS.</span> |
| **Actores:** | <span>PAS</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como PAS.</span> |
| **Flujo Normal:** | <span>1.- El PAS inicia el proceso de alta. <br>2.- El sistema solicita los datos del estudiante. <br>3.- El PAS introduce los datos. <br>4.- Se ejecuta el caso de uso "Verificar datos del estudiante" (CU-105). <br>5.- El sistema confirma el alta.</span> |
| **Flujo Alternativo:** | <span>4.A- Si la verificación de datos falla, el sistema informa al actor y permite corregir los datos.</span> |
| **Poscondiciones:**| <span>El estudiante queda registrado en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-102, CU-105</span> |

### ---

| **Nombre:** | <span>Verificar datos del estudiante</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-105</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Funcionalidad que se **incluye** en "Dar alta estudiante" para verificar que los datos del estudiante son correctos y válidos.</span> |
| **Actores:** | <span>(Sistema)</span> |
| **Precondiciones:**| <span>Se está ejecutando un caso de uso que lo incluye (CU-103 o CU-104).</span> |
| **Flujo Normal:** | <span>1.- El sistema recibe los datos del estudiante. <br>2.- El sistema comprueba el formato y la validez de los datos contra la base de datos de la universidad. <br>3.- El sistema devuelve un resultado de validación exitoso.</span> |
| **Flujo Alternativo:** | <span>2.A- Si los datos no son válidos, el sistema devuelve un resultado de error.</span> |
| **Poscondiciones:**| <span>Los datos del estudiante han sido validados.</span> |
| **Artefactos relacionados:**| <span>CU-102</span> |

### ---

| **Nombre:** | <span>Realizar busqueda en la lista de clase</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-106</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Funcionalidad que **extiende** opcionalmente a "Dar alta estudiante(PDI)" para buscar a un estudiante en las listas de clase de las asignaturas del PDI.</span> |
| **Actores:** | <span>PDI</span> |
| **Precondiciones:**| <span>Se está ejecutando el caso de uso "Dar alta estudiante(PDI)" (CU-103).</span> |
| **Flujo Normal:** | <span>1.- El PDI activa la búsqueda en la lista de clase. <br>2.- El sistema solicita el nombre del estudiante y la asignatura. <br>3.- El PDI introduce los datos. <br>4.- El sistema busca al estudiante y, si lo encuentra, autocompleta los datos en el formulario de alta.</span> |
| **Flujo Alternativo:** | <span>4.A- Si el estudiante no se encuentra en la lista de clase, el sistema lo notifica.</span> |
| **Poscondiciones:**| <span>Los datos del estudiante se han recuperado de la lista de clase.</span> |
| **Artefactos relacionados:**| <span>CU-103</span> |

### ---

| **Nombre:** | <span>Modificar horarios</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-107</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Permite al personal del PAS modificar directamente los horarios existentes.</span> |
| **Actores:** | <span>PAS</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como PAS.</span> |
| **Flujo Normal:** | <span>1.- El PAS selecciona el horario que desea modificar. <br>2.- El sistema muestra la información del horario en un formulario editable. <br>3.- El PAS realiza las modificaciones. <br>4.- El PAS guarda los cambios y el sistema actualiza el horario.</span> |
| **Flujo Alternativo:** | <span>3.A- El PAS cancela la modificación y los cambios no se guardan.</span> |
| **Poscondiciones:**| <span>El horario ha sido actualizado en el sistema.</span> |
| **Artefactos relacionados:**| <span></span> |

### ---

| **Nombre:** | <span>Consultar horario</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-108</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Caso de uso general que permite a los usuarios consultar horarios. Es especializado por los diferentes roles.</span> |
| **Actores:** | <span>PDI, PAS, Estudiante</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado.</span> |
| **Flujo Normal:** | <span>1.- El actor accede a la función de consulta de horarios. <br>2.- El sistema muestra las opciones de búsqueda (por curso, profesor, asignatura, etc.). <br>3.- El actor introduce sus criterios de búsqueda y el sistema muestra los resultados.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la búsqueda no produce resultados, el sistema muestra un mensaje informativo.</span> |
| **Poscondiciones:**| <span>El actor ha visualizado la información del horario solicitado.</span> |
| **Artefactos relacionados:**| <span>CU-109, CU-110, CU-111</span> |

### ---

| **Nombre:** | <span>Consultar horario(PDI)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-109</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar horario" para el actor PDI.</span> |
| **Actores:** | <span>PDI</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como PDI.</span> |
| **Flujo Normal:** | <span>1.- El PDI accede a la consulta de horarios. <br>2.- El sistema muestra por defecto los horarios de sus asignaturas. <br>3.- El PDI puede realizar búsquedas específicas. <br>4.- El sistema muestra los horarios solicitados.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la búsqueda no produce resultados, el sistema lo indica.</span> |
| **Poscondiciones:**| <span>El actor ha visualizado la información del horario.</span> |
| **Artefactos relacionados:**| <span>CU-108</span> |

### ---

| **Nombre:** | <span>Consultar horario(PAS)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-110</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar horario" para el actor PAS.</span> |
| **Actores:** | <span>PAS</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como PAS.</span> |
| **Flujo Normal:** | <span>1.- El PAS accede a la consulta de horarios. <br>2.- El sistema proporciona opciones de búsqueda avanzadas (por titulación, grupo, aula, etc.). <br>3.- El PAS introduce los criterios y el sistema muestra los resultados.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la búsqueda no produce resultados, el sistema lo indica.</span> |
| **Poscondiciones:**| <span>El actor ha visualizado la información del horario.</span> |
| **Artefactos relacionados:**| <span>CU-108</span> |

### ---

| **Nombre:** | <span>Consultar horario(Estudiante)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-111</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>23/09/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar horario" para el actor Estudiante.</span> |
| **Actores:** | <span>Estudiante</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado como Estudiante.</span> |
| **Flujo Normal:** | <span>1.- El estudiante accede a la consulta de horarios. <br>2.- El sistema muestra el horario personal del estudiante según sus asignaturas matriculadas. <br>3.- El estudiante puede realizar búsquedas de otros horarios.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la búsqueda no produce resultados, el sistema lo indica.</span> |
| **Poscondiciones:**| <span>El actor ha visualizado la información del horario.</span> |
| **Artefactos relacionados:**| <span>CU-108</span> |
<br>

<p align="center">
  <img src="supuesto_1_DB.jpg" alt="img_supuesto2_DB" width="750">
</p>

## Supuesto 2: Sistema de compras

En un sistema de compra, existen cuatro tipos de usuarios: comprador, vendedor, proveedor y administrador. Los compradores pueden agregar productos, consultar precios, finalizar la compra y consultar ofertas. Agregar productos implica marcar esos productos como bloqueados. Los vendedores también pueden consultar ofertas y consultar precios. Los proveedores pueden consultar precios, avisar de nuevos productos y consultar ofertas. Avisar de nuevos productos, de forma excepcional, realiza la incorporación de una oferta. Los proveedores también tienen una funcionalidad para avisar del fin de una oferta. Cuando se avisa del fin de una oferta, se ejecuta la funcionalidad de eliminar la oferta. Ambas funcionalidades de avisar del proveedor tienen en común que se encarga de enviar una notificación. Los administradores pueden consultar precios, consultar ofertas y eliminar productos. La funcionalidad de consultar precios incluye una funcionalidad de buscar productos que es similar a la funcionalidad de consultar productos de los compradores. Sin embargo, la funcionalidad de consultar productos añade una funcionalidad para verificar la disponibilidad. Para realizar una venta, un comprador y un vendedor participan de forma conjunta. En dicha operación, se lleva a cabo el acuerdo de un precio; excepcionalmente, durante la realización de la venta, se consultará el histórico de ventas.

<p align="center">
  <img src="supuesto2.jpg" alt="img_supuesto1" width="750">
</p>

### **Requisitos del diagrama de casos de uso**

| **Nombre:** | Consultar productos |
| :--- | :--- |
| **Codigo:** | CU-201 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Permite a los compradores ver los productos disponibles en el sistema. Incluye la verificación de la disponibilidad del producto. |
| **Actores:** | Comprador |
| **Precondiciones:**| El actor debe haber iniciado sesión en el sistema. |
| **Flujo Normal:** | 1.- El comprador selecciona la opción de consultar productos. <br>2.- El sistema muestra una lista de los productos. <br>3.- El comprador selecciona un producto para ver los detalles. <br>4.- El sistema muestra la información del producto y ejecuta "Verificar disponibilidad" (CU-215). |
| **Flujo Alternativo:** | 2.A- Si no hay productos, el sistema muestra un mensaje indicándolo. |
| **Poscondiciones:**| El comprador ha visto la información y disponibilidad de un producto. |
| **Artefactos relacionados:**| CU-203, CU-219 |

### \---

| **Nombre:** | Consultar precios |
| :--- | :--- |
| **Codigo:** | CU-202 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Caso de uso general para consultar los precios de los productos. Es utilizado por compradores, vendedores, proveedores y administradores. |
| **Actores:** | Comprador, Vendedor, Proveedor, Administrador |
| **Precondiciones:**| El actor debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El actor elige la opción de consultar precios. <br>2.- El sistema le permite buscar productos. <br>3.- El actor busca un producto. <br>4.- El sistema muestra el precio del producto. |
| **Flujo Alternativo:** | 3.A- Si el producto no se encuentra, el sistema muestra un mensaje. |
| **Poscondiciones:**| El actor ha consultado el precio de un producto. |
| **Artefactos relacionados:**| CU-203, CU-204, CU-205, CU-206 |

### \---

| **Nombre:** | Consultar precios (comprador) |
| :--- | :--- |
| **Codigo:** | CU-203 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar precios" para el actor Comprador. |
| **Actores:** | Comprador |
| **Precondiciones:**| El comprador debe estar autenticado. |
| **Flujo Normal:** | 1.- El comprador busca un producto. <br>2.- El sistema muestra el precio del producto. |
| **Flujo Alternativo:** | 1.A- Si el producto no existe, se notifica al comprador. |
| **Poscondiciones:**| El comprador conoce el precio de un producto. |
| **Artefactos relacionados:**| CU-201, CU-202 |

### \---

| **Nombre:** | Consultar precios (vendedor) |
| :--- | :--- |
| **Codigo:** | CU-204 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar precios" para el actor Vendedor. |
| **Actores:** | Vendedor |
| **Precondiciones:**| El vendedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El vendedor busca un producto. <br>2.- El sistema muestra el precio del producto. |
| **Flujo Alternativo:** | 1.A- Si el producto no existe, se notifica al vendedor. |
| **Poscondiciones:**| El vendedor conoce el precio de un producto. |
| **Artefactos relacionados:**| CU-202 |

### \---

| **Nombre:** | Consultar precios (proveedor) |
| :--- | :--- |
| **Codigo:** | CU-205 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar precios" para el actor Proveedor. |
| **Actores:** | Proveedor |
| **Precondiciones:**| El proveedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El proveedor busca un producto. <br>2.- El sistema muestra el precio del producto. |
| **Flujo Alternativo:** | 1.A- Si el producto no existe, se notifica al proveedor. |
| **Poscondiciones:**| El proveedor conoce el precio de un producto. |
| **Artefactos relacionados:**| CU-202 |

### \---

| **Nombre:** | Consultar precios (administrador) |
| :--- | :--- |
| **Codigo:** | CU-206 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar precios" para el actor Administrador, que **incluye** la funcionalidad de "Buscar productos". |
| **Actores:** | Administrador |
| **Precondiciones:**| El administrador debe estar autenticado. |
| **Flujo Normal:** | 1.- El administrador ejecuta "Buscar productos" (CU-216). <br>2.- El sistema muestra el precio del producto encontrado. |
| **Flujo Alternativo:** | 1.A- Si no se encuentra el producto, el sistema lo notifica. |
| **Poscondiciones:**| El administrador conoce el precio de un producto. |
| **Artefactos relacionados:**| CU-202, CU-220 |

### \---

| **Nombre:** | Consultar oferta |
| :--- | :--- |
| **Codigo:** | CU-207 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Caso de uso general para que los usuarios puedan consultar las ofertas disponibles. |
| **Actores:** | Comprador, Vendedor, Proveedor, Administrador |
| **Precondiciones:**| El actor debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El actor accede a la sección de ofertas. <br>2.- El sistema muestra las ofertas disponibles. <br>3.- El actor selecciona una oferta para ver sus detalles. |
| **Flujo Alternativo:** | 2.A- Si no hay ofertas, el sistema muestra un mensaje. |
| **Poscondiciones:**| El actor ha visto las ofertas disponibles. |
| **Artefactos relacionados:**| CU-208, CU-209, CU-210, CU-211 |

### \---

| **Nombre:** | Consultar oferta (comprador) |
| :--- | :--- |
| **Codigo:** | CU-208 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar oferta" para el actor Comprador. |
| **Actores:** | Comprador |
| **Precondiciones:**| El comprador debe estar autenticado. |
| **Flujo Normal:** | 1.- El comprador accede a las ofertas. <br>2.- El sistema le muestra las ofertas. |
| **Flujo Alternativo:** | 2.A- Si no hay ofertas, se le notifica. |
| **Poscondiciones:**| El comprador conoce las ofertas. |
| **Artefactos relacionados:**| CU-207 |

### \---

| **Nombre:** | Consultar oferta (vendedor) |
| :--- | :--- |
| **Codigo:** | CU-209 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar oferta" para el actor Vendedor. |
| **Actores:** | Vendedor |
| **Precondiciones:**| El vendedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El vendedor accede a las ofertas. <br>2.- El sistema le muestra las ofertas. |
| **Flujo Alternativo:** | 2.A- Si no hay ofertas, se le notifica. |
| **Poscondiciones:**| El vendedor conoce las ofertas. |
| **Artefactos relacionados:**| CU-207 |

### \---

| **Nombre:** | Consultar oferta (proveedor) |
| :--- | :--- |
| **Codigo:** | CU-210 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar oferta" para el actor Proveedor. |
| **Actores:** | Proveedor |
| **Precondiciones:**| El proveedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El proveedor accede a las ofertas. <br>2.- El sistema le muestra las ofertas. |
| **Flujo Alternativo:** | 2.A- Si no hay ofertas, se le notifica. |
| **Poscondiciones:**| El proveedor conoce las ofertas. |
| **Artefactos relacionados:**| CU-207 |

### \---

| **Nombre:** | Consultar oferta (administrador) |
| :--- | :--- |
| **Codigo:** | CU-211 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Versión del caso de uso "Consultar oferta" para el actor Administrador. |
| **Actores:** | Administrador |
| **Precondiciones:**| El administrador debe estar autenticado. |
| **Flujo Normal:** | 1.- El administrador accede a las ofertas. <br>2.- El sistema le muestra las ofertas. |
| **Flujo Alternativo:** | 2.A- Si no hay ofertas, se le notifica. |
| **Poscondiciones:**| El administrador conoce las ofertas. |
| **Artefactos relacionados:**| CU-207 |

### \---

| **Nombre:** | Avisar de nuevos productos |
| :--- | :--- |
| **Codigo:** | CU-212 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Permite al proveedor notificar la llegada de nuevos productos. Opcionalmente, **extiende** la funcionalidad a "Incorporar oferta". **Incluye** el envío de una notificación. |
| **Actores:** | Proveedor |
| **Precondiciones:**| El proveedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El proveedor avisa de un nuevo producto. <br>2.- El sistema registra el nuevo producto. <br>3.- El sistema ejecuta "Enviar notificación" (CU-217). |
| **Flujo Alternativo:** | 2.A- De forma excepcional, el proveedor puede ejecutar "Incorporar oferta" (CU-218). |
| **Poscondiciones:**| Se ha notificado y registrado un nuevo producto. |
| **Artefactos relacionados:**| CU-221, CU-222 |

### \---

| **Nombre:** | Avisar de fin de oferta |
| :--- | :--- |
| **Codigo:** | CU-213 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Permite al proveedor notificar el fin de una oferta. **Incluye** las funcionalidades "Eliminar oferta" y "Enviar notificación". |
| **Actores:** | Proveedor |
| **Precondiciones:**| El proveedor debe estar autenticado. |
| **Flujo Normal:** | 1.- El proveedor avisa del fin de una oferta. <br>2.- El sistema ejecuta "Eliminar oferta" (CU-219). <br>3.- El sistema ejecuta "Enviar notificación" (CU-217). |
| **Flujo Alternativo:** | 2.A- Si la oferta no existe, el sistema lo notifica. |
| **Poscondiciones:**| La oferta ha sido eliminada y se ha enviado una notificación. |
| **Artefactos relacionados:**| CU-221, CU-223 |

### \---

| **Nombre:** | Eliminar producto |
| :--- | :--- |
| **Codigo:** | CU-214 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Permite al administrador eliminar un producto del sistema. |
| **Actores:** | Administrador |
| **Precondiciones:**| El administrador debe estar autenticado. |
| **Flujo Normal:** | 1.- El administrador selecciona un producto. <br>2.- El administrador confirma la eliminación. <br>3.- El sistema elimina el producto. |
| **Flujo Alternativo:** | 2.A- El administrador cancela la operación. |
| **Poscondiciones:**| El producto ya no está disponible en el sistema. |
| **Artefactos relacionados:**| |

### \---

| **Nombre:** | Realizar venta |
| :--- | :--- |
| **Codigo:** | CU-215 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 23/09/2025 |
| **Descripción:** | Gestiona el proceso de venta entre un comprador y un vendedor. **Incluye** "Acordar un precio" y, excepcionalmente, **extiende** a "Consultar el histórico de ventas". |
| **Actores:** | Comprador, Vendedor |
| **Precondiciones:**| Comprador y vendedor deben estar autenticados. |
| **Flujo Normal:** | 1.- Comprador y vendedor inician la venta. <br>2.- Se ejecuta "Acordar un precio" (CU-221). <br>3.- Se confirma la transacción. |
| **Flujo Alternativo:** | 2.A- Durante la negociación, se puede ejecutar "Consultar el histórico de ventas" (CU-222). |
| **Poscondiciones:**| La venta se ha completado. |
| **Artefactos relacionados:**| CU-224, CU-225 |

### \---

| **Nombre:** | Agregar productos |
| :--- | :--- |
| **Codigo:** | CU-216 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Permite a un comprador añadir productos a su cesta de la compra. **Incluye** la funcionalidad de "Marcar productos como bloqueados". |
| **Actores:** | Comprador |
| **Precondiciones:**| El comprador debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El comprador selecciona un producto y la cantidad que desea añadir. <br>2.- El comprador pulsa el botón para agregar a la cesta. <br>3.- El sistema ejecuta "Marcar productos como bloqueados" (CU-225) para asegurar la disponibilidad. <br>4.- El sistema confirma que el producto ha sido añadido a la cesta. |
| **Flujo Alternativo:** | 3.A- Si el producto no tiene stock suficiente, el sistema informa al comprador y no permite añadirlo. |
| **Poscondiciones:**| El producto seleccionado está en la cesta de la compra y su stock ha sido reservado temporalmente. |
| **Artefactos relacionados:**| CU-218 |

### \---

| **Nombre:** | Finalizar compra |
| :--- | :--- |
| **Codigo:** | CU-217 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Permite al comprador completar el proceso de adquisición de los productos que tiene en su cesta. |
| **Actores:** | Comprador |
| **Precondiciones:**| El comprador debe estar autenticado y tener al menos un producto en la cesta. |
| **Flujo Normal:** | 1.- El comprador accede a su cesta y selecciona la opción para finalizar la compra. <br>2.- El sistema muestra un resumen del pedido y solicita la confirmación. <br>3.- El comprador confirma y el sistema procesa el pago. <br>4.- El sistema confirma la compra y actualiza el estado del pedido a "completado". |
| **Flujo Alternativo:** | 3.A- Si el proceso de pago falla, el sistema informa al comprador y le permite intentarlo de nuevo. |
| **Poscondiciones:**| Los productos de la cesta han sido comprados y el stock se descuenta de forma definitiva. |
| **Artefactos relacionados:**| |

### \---

| **Nombre:** | Marcar productos como bloqueados |
| :--- | :--- |
| **Codigo:** | CU-218 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Agregar productos" que reserva temporalmente el stock de un producto cuando se añade a la cesta. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando el caso de uso "Agregar productos". |
| **Flujo Normal:** | 1.- El sistema recibe la solicitud de añadir un producto a la cesta. <br>2.- El sistema reduce el stock disponible de ese producto en la cantidad solicitada y lo marca como "bloqueado" o "reservado". |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El stock del producto ha sido reservado para evitar que otro usuario lo compre. |
| **Artefactos relacionados:**| CU-216 |

### \---

| **Nombre:** | Verificar disponibilidad |
| :--- | :--- |
| **Codigo:** | CU-219 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** a "Consultar productos" para comprobar si hay stock disponible. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando el caso de uso "Consultar productos". |
| **Flujo Normal:** | 1.- El sistema comprueba el stock actual del producto consultado. <br>2.- El sistema muestra el estado de disponibilidad (Ej: "En stock", "Pocas unidades", "Agotado"). |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El comprador conoce la disponibilidad del producto. |
| **Artefactos relacionados:**| CU-201 |

### \---

| **Nombre:** | Buscar productos |
| :--- | :--- |
| **Codigo:** | CU-220 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Consultar precios (administrador)" para encontrar productos en el sistema. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Consultar precios (administrador)". |
| **Flujo Normal:** | 1.- El sistema presenta al administrador una interfaz de búsqueda con filtros avanzados. <br>2.- El administrador introduce los criterios de búsqueda. <br>3.- El sistema devuelve una lista de productos que coinciden. |
| **Flujo Alternativo:** | 3.A- Si no se encuentran productos, se muestra un mensaje. |
| **Poscondiciones:**| Se ha obtenido un listado de productos según los criterios del administrador. |
| **Artefactos relacionados:**| CU-206 |

### \---

| **Nombre:** | Enviar notificacion |
| :--- | :--- |
| **Codigo:** | CU-221 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Avisar de nuevos productos" y "Avisar de fin de oferta" para comunicar eventos. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando un caso de uso que lo incluye. |
| **Flujo Normal:** | 1.- El sistema identifica a los usuarios que deben ser notificados. <br>2.- El sistema genera y envía una notificación (por email, push, etc.) sobre el nuevo producto o el fin de la oferta. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| Los usuarios correspondientes han sido notificados. |
| **Artefactos relacionados:**| CU-212, CU-213 |

### \---

| **Nombre:** | Incorporar oferta |
| :--- | :--- |
| **Codigo:** | CU-222 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** de forma excepcional a "Avisar de nuevos productos" para crear una oferta de lanzamiento. |
| **Actores:** | Proveedor |
| **Precondiciones:**| Se está ejecutando el caso de uso "Avisar de nuevos productos". |
| **Flujo Normal:** | 1.- Al avisar de un nuevo producto, el proveedor activa la opción de crear una oferta. <br>2.- El sistema solicita los detalles de la oferta (descuento, duración, etc.). <br>3.- El proveedor los introduce y el sistema crea y activa la oferta para el nuevo producto. |
| **Flujo Alternativo:** | 3.A- El proveedor decide no crear una oferta y cancela la operación. |
| **Poscondiciones:**| Se ha creado una nueva oferta asociada al nuevo producto. |
| **Artefactos relacionados:**| CU-212 |

### \---

| **Nombre:** | Eliminar oferta |
| :--- | :--- |
| **Codigo:** | CU-223 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Avisar de fin de oferta" que desactiva o elimina una oferta del sistema. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Avisar de fin de oferta". |
| **Flujo Normal:** | 1.- El sistema recibe el identificador de la oferta que ha finalizado. <br>2.- El sistema cambia el estado de la oferta a "inactiva" o la elimina de la base de datos. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| La oferta ya no está visible ni aplicable para los compradores. |
| **Artefactos relacionados:**| CU-213 |

### \---

| **Nombre:** | Acordar un precio |
| :--- | :--- |
| **Codigo:** | CU-224 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Realizar venta" donde el comprador y el vendedor negocian y fijan un precio final. |
| **Actores:** | Comprador, Vendedor |
| **Precondiciones:**| Se está ejecutando el caso de uso "Realizar venta". |
| **Flujo Normal:** | 1.- El vendedor propone un precio inicial. <br>2.- El comprador puede aceptarlo o proponer una contraoferta. <br>3.- El proceso se repite hasta que ambas partes aceptan un precio. <br>4.- El precio acordado se fija para la transacción. |
| **Flujo Alternativo:** | 3.A- Si no se llega a un acuerdo, la venta puede ser cancelada. |
| **Poscondiciones:**| Se ha establecido un precio final para la venta. |
| **Artefactos relacionados:**| CU-215 |

### \---

| **Nombre:** | Consultar el historico de ventas |
| :--- | :--- |
| **Codigo:** | CU-225 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 17/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** de forma excepcional a "Realizar venta" para consultar ventas anteriores del mismo producto o cliente. |
| **Actores:** | Vendedor |
| **Precondiciones:**| Se está ejecutando el caso de uso "Realizar venta". |
| **Flujo Normal:** | 1.- Durante la negociación del precio, el vendedor decide consultar el histórico. <br>2.- El sistema muestra un listado de ventas previas, incluyendo fechas y precios. <br>3.- El vendedor utiliza esta información para ajustar su estrategia de negociación. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El vendedor ha obtenido información sobre ventas pasadas para facilitar la negociación actual. |
| **Artefactos relacionados:**| CU-215 |

</br>

<p align="center">
  <img src="supuesto_2_DB.png" alt="img_supuesto2_DB" width="750">
</p>

### ---

| **INF-202** | **Usuario** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Autenticación de todos los actores</li></ul> |
| **Descripción** | El sistema deberá almacenar la información base de autenticación y los datos comunes para todos los actores. |
| **Datos específicos** | <ul><li>idUsuario INT</li><li>nombreUsuario VARCHAR(45)</li><li>correoElectronico VARCHAR(45)</li><li>contraseña VARCHAR(45)</li></ul> |
| **Importancia** | Muy importante |
| **Estado** | Aceptado |
| **Comentarios** | Es la tabla "padre" de la que heredan los roles de Administrador, Proveedor, Vendedor y Comprador. |

### ---

| **INF-203** | **Administrador** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Consultar precios (administrador)</li><li>Consultar oferta (administrador)</li><li>Eliminar producto</li></ul> |
| **Descripción** | El sistema deberá almacenar la referencia al rol de Administrador. |
| **Datos específicos** | <ul><li>idAdministrador INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Tabla de especialización. El 'idAdministrador' es una Clave Foránea (FK) que referencia a 'Usuario.idUsuario'. |

### ---

| **INF-204** | **Proveedor** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Consultar precios (proveedor)</li\><li>Avisar de nuevos productos</li><li>Avisar de fin de oferta</li></ul> |
| **Descripción** | El sistema deberá almacenar la referencia al rol de Proveedor. |
| **Datos específicos** | <ul><li>idProveedor INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Tabla de especialización. El 'idProveedor' es una FK que referencia a 'Usuario.idUsuario'. Es el responsable de los productos y las ofertas. |

### ---

| **INF-205** | **Vendedor** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Consultar precios (vendedor)</li><li>Realizar venta</li></ul> |
| **Descripción** | El sistema deberá almacenar la referencia al rol de Vendedor. |
| **Datos específicos** | <ul><li>idVendedor INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Tabla de especialización. El 'idVendedor' es una FK que referencia a 'Usuario.idUsuario'. Participa en la 'Venta'. |

### ---

| **INF-206** | **Comprador** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Agregar productos</li><li>Finalizar compra</li><li>Realizar venta</li></ul> |
| **Descripción** | El sistema deberá almacenar la referencia al rol de Comprador. |
| **Datos específicos** | <ul><li>idComprador INT</li></ul> |
| **Importancia** | Muy importante |
| **Estado** | Aceptado |
| **Comentarios** | Tabla de especialización. El 'idComprador' es una FK que referencia a 'Usuario.idUsuario'. Participa en la 'Venta'. |

### ---

| **INF-201** | **Producto** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Agregar productos</li><li>Consultar productos</li><li>Consultar precios</li><li>Eliminar producto</li></ul> |
| **Descripción** | El sistema deberá almacenar la información correspondiente a los productos que se gestionan en la tienda. |
| **Datos específicos** | <ul><li>idProducto INT</li><li>idProveedor INT</li><li>precio INT</li><li>stock INT</li></ul> |
| **Importancia** | Muy importante |
| **Estado** | Aceptado |
| **Comentarios** | Es la entidad principal sobre la que operan la mayoría de los casos de uso (comprar, consultar, gestionar). |

### ---

| **INF-207** | **Oferta** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Consultar oferta</li><li>Avisar de fin de oferta</li><li>Incorporar oferta</li></ul> |
| **Descripción** | El sistema deberá almacenar la información de las ofertas o promociones creadas por los proveedores. |
| **Datos específicos** | <ul><li>idOferta INT</li><li>idProveedor INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Se relaciona con los productos a los que aplica a través de la tabla 'OfertaProducto'. |

### ---

| **INF-208** | **OfertaProducto** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Consultar oferta</li><li>Incorporar oferta</li></ul> |
| **Descripción** | El sistema deberá almacenar la relación entre las ofertas y los productos. |
| **Datos específicos** | <ul><li>idOferta INT</li><li>idProducto INT</li></ul> |
| **Importancia** | Alta |
| **Estado** | Aceptado |
| **Comentarios** | Tabla asociativa (N:N) que permite que una oferta aplique a muchos productos y un producto esté en muchas ofertas. |

### ---

| **INF-209** | **Venta** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Realizar venta</li><li>Finalizar compra</li><li>Consultar el historico de ventas</li></ul> |
| **Descripción** | El sistema deberá almacenar la cabecera de una transacción de venta, identificando al comprador y al vendedor. |
| **Datos específicos** | <ul><li>idVenta INT</li><li>idComprador INT</li><li>idVendedor INT</li></ul> |
| **Importancia** | Muy importante |
| **Estado** | Aceptado |
| **Comentarios** | Representa el registro de la transacción. Se complementa con 'DetallesVenta'. |

### ---

| **INF-210** | **DetallesVenta** |
| :--- | :--- |
| **Versión** | 1.0 (Octubre-2025) |
| **Autores** | INRE Equipo Azul |
| **Fuentes** | Descripción del Supuesto 2 |
| **Referencias** | <ul><li>Realizar venta</li><li>Consultar el historico de ventas</li></ul> |
| **Descripción** | El sistema deberá almacenar el detalle de los productos (y sus cantidades) vendidos en una transacción. |
| **Datos específicos** | <ul><li>idVenta INT</li><li>idProducto INT</li><li>cantidadVendida INT</li><li>precioTotal INT</li></ul> |
| **Importancia** | Muy importante |
| **Estado** | Aceptado |
| **Comentarios** | Tabla asociativa (N:N) entre 'Venta' y 'Producto'. Esencial para el histórico de ventas. |

## Supuesto 3: Compañia Hotelera

En una compañía hotelera, el administrador y el comercial pueden consultar reservas. El comercial realiza ofertas y gestiona nuevas reservas. El administrador gestiona nuevas peticiones y también realiza ofertas. La realización de ofertas por parte del comercial conlleva un recálculo de precios. Además, dicha realización de ofertas conlleva opcionalmente el bloqueo temporal de una reserva. Los clientes, los administradores y los comerciales pueden consultar disponibilidades y visualizar ofertas. La consulta de disponibilidades y la consulta de reservas tienen la funcionalidad común de buscar elementos. Por su parte, la consulta de disponibilidades conlleva una funcionalidad que muestra un calendario.

<p align="center">
  <img src="supuesto3.jpg" alt="img_supuesto1" width="1000">
</p>


### Requisitos del diagrama de casos de uso

### Consultar Disponibilidad

| **Nombre:** | <span>Consultar disponibilidad</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-301</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite consultar la disponibilidad de habitaciones. Este caso de uso **incluye** las funcionalidades "Buscar elemento" y "Mostrar calendario".</span> |
| **Actores:** | <span>Cliente, Comercial, Administrador</span> |
| **Precondiciones:**| <span>Ninguna para el cliente, pero el comercial y el administrador deben estar autenticados.</span> |
| **Flujo Normal:** | <span>1.- El actor introduce las fechas para las que desea consultar la disponibilidad. <br>2.- Se ejecuta la funcionalidad incluida "Buscar elemento". <br>3.- Se ejecuta la funcionalidad incluida "Mostrar calendario" para visualizar los resultados.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay disponibilidad para las fechas seleccionadas, el sistema informa al actor y puede sugerir fechas alternativas.</span> |
| **Poscondiciones:**| <span>El actor conoce la disponibilidad para las fechas seleccionadas.</span> |
| **Artefactos relacionados:**| <span>CU-302, CU-303, CU-304, CU-319, CU-320</span> |

### ---

| **Nombre:** | <span>Consultar disponibilidad(Cliente)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-302</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar disponibilidad" para el actor Cliente.</span> |
| **Actores:** | <span>Cliente</span> |
| **Precondiciones:**| <span>Ninguna.</span> |
| **Flujo Normal:** | <span>1.- El cliente introduce las fechas deseadas. <br>2.- Se ejecuta la funcionalidad incluida "Buscar elemento". <br>3.- Se ejecuta la funcionalidad incluida "Mostrar calendario" con los resultados.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay disponibilidad, el sistema informa y sugiere alternativas.</span> |
| **Poscondiciones:**| <span>El cliente visualiza la disponibilidad para las fechas seleccionadas.</span> |
| **Artefactos relacionados:**| <span>CU-301</span> |

### ---

| **Nombre:** | <span>Consultar disponibilidad(Comercial)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-303</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar disponibilidad" para el actor Comercial.</span> |
| **Actores:** | <span>Comercial</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El comercial introduce las fechas deseadas. <br>2.- Se ejecuta la funcionalidad incluida "Buscar elemento". <br>3.- Se ejecuta la funcionalidad incluida "Mostrar calendario" con los resultados.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay disponibilidad, el sistema informa y sugiere alternativas.</span> |
| **Poscondiciones:**| <span>El comercial visualiza la disponibilidad para las fechas seleccionadas.</span> |
| **Artefactos relacionados:**| <span>CU-301</span> |

### ---

| **Nombre:** | <span>Consultar disponibilidad(Administrador)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-304</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar disponibilidad" para el actor Administrador.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El administrador introduce las fechas deseadas. <br>2.- Se ejecuta la funcionalidad incluida "Buscar elemento". <br>3.- Se ejecuta la funcionalidad incluida "Mostrar calendario" con los resultados.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay disponibilidad, el sistema informa y sugiere alternativas.</span> |
| **Poscondiciones:**| <span>El administrador visualiza la disponibilidad para las fechas seleccionadas.</span> |
| **Artefactos relacionados:**| <span>CU-301</span> |

### ---

### Consultar Reserva

| **Nombre:** | <span>Consultar reserva</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-305</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite consultar los detalles de una reserva existente. Este caso de uso **incluye** la funcionalidad "Buscar elemento".</span> |
| **Actores:** | <span>Comercial, Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El actor invoca la funcionalidad incluida "Buscar elemento" para encontrar la reserva por un criterio. <br>2.- El sistema muestra un listado de resultados. <br>3.- El actor selecciona la reserva deseada y el sistema muestra todos sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si la búsqueda no arroja resultados, el sistema lo notifica.</span> |
| **Poscondiciones:**| <span>El actor ha podido consultar la información de la reserva.</span> |
| **Artefactos relacionados:**| <span>CU-306, CU-307, CU-319</span> |

### ---

| **Nombre:** | <span>Consultar reserva(Comercial)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-306</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar reserva" para el actor Comercial.</span> |
| **Actores:** | <span>Comercial</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El comercial invoca la funcionalidad incluida "Buscar elemento". <br>2.- El sistema muestra los resultados. <br>3.- El comercial selecciona la reserva para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si la búsqueda no arroja resultados, el sistema lo notifica.</span> |
| **Poscondiciones:**| <span>El comercial ha consultado la información de la reserva.</span> |
| **Artefactos relacionados:**| <span>CU-305</span> |

### ---

| **Nombre:** | <span>Consultar reserva(Administrador)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-307</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Consultar reserva" para el actor Administrador.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El administrador invoca la funcionalidad incluida "Buscar elemento". <br>2.- El sistema muestra los resultados. <br>3.- El administrador selecciona la reserva para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si la búsqueda no arroja resultados, el sistema lo notifica.</span> |
| **Poscondiciones:**| <span>El administrador ha consultado la información de la reserva.</span> |
| **Artefactos relacionados:**| <span>CU-305</span> |

### ---

### Realizar Oferta

| **Nombre:** | <span>Realizar oferta</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-308</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite crear y enviar una oferta a un cliente.</span> |
| **Actores:** | <span>Comercial, Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona la opción para realizar una oferta. <br>2.- El sistema solicita los detalles de la oferta. <br>3.- El actor confirma y el sistema genera y envía la oferta.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la oferta no puede ser procesada, el sistema muestra un error.</span> |
| **Poscondiciones:**| <span>La oferta es creada y registrada en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-309, CU-310</span> |

### ---

| **Nombre:** | <span>Realizar oferta(Comercial)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-309</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Realizar oferta" para el actor Comercial. **Extiende** a "Recalcular precios" y opcionalmente a "Bloquear temporalmente una reserva".</span> |
| **Actores:** | <span>Comercial</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El comercial selecciona la opción para realizar una oferta. <br>2.- El sistema pide los detalles. <br>3.- Se ejecuta la extensión para recalcular precios. <br>4.- El comercial confirma la oferta. <br>5.- El sistema genera y envía la oferta.</span> |
| **Flujo Alternativo:** | <span>3.A- El comercial puede activar la extensión para bloquear temporalmente una reserva.</span> |
| **Poscondiciones:**| <span>La oferta es creada y registrada en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-308, CU-317, CU-318</span> |

### ---

| **Nombre:** | <span>Realizar oferta(Administrador)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-310</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Realizar oferta" para el actor Administrador.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El administrador selecciona la opción para realizar una oferta. <br>2.- El sistema pide los detalles. <br>3.- El administrador confirma la oferta. <br>4.- El sistema genera y envía la oferta.</span> |
| **Flujo Alternativo:** | <span>4.A- Si la oferta no puede ser procesada, el sistema muestra un error.</span> |
| **Poscondiciones:**| <span>La oferta es creada y registrada en el sistema.</span> |
| **Artefactos relacionados:**| <span>CU-308</span> |

### ---

### Visualizar Oferta

| **Nombre:** | <span>Visualizar oferta</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-311</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite visualizar las ofertas disponibles.</span> |
| **Actores:** | <span>Cliente, Comercial, Administrador</span> |
| **Precondiciones:**| <span>Ninguna para el cliente, pero el comercial y el administrador deben estar autenticados.</span> |
| **Flujo Normal:** | <span>1.- El actor accede a la sección de ofertas. <br>2.- El sistema muestra un listado con las ofertas vigentes. <br>3.- El actor puede seleccionar una oferta para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay ofertas vigentes, el sistema muestra un mensaje indicándolo.</span> |
| **Poscondiciones:**| <span>El actor ha podido consultar las ofertas y sus detalles.</span> |
| **Artefactos relacionados:**| <span>CU-312, CU-313, CU-314</span> |

### ---

| **Nombre:** | <span>Visualizar oferta(Cliente)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-312</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Visualizar oferta" para el actor Cliente.</span> |
| **Actores:** | <span>Cliente</span> |
| **Precondiciones:**| <span>Ninguna.</span> |
| **Flujo Normal:** | <span>1.- El cliente accede a la sección de ofertas. <br>2.- El sistema muestra un listado con las ofertas vigentes. <br>3.- El cliente selecciona una oferta para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay ofertas vigentes, el sistema muestra un mensaje.</span> |
| **Poscondiciones:**| <span>El cliente ha podido consultar las ofertas.</span> |
| **Artefactos relacionados:**| <span>CU-311</span> |

### ---

| **Nombre:** | <span>Visualizar oferta(Comercial)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-313</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Visualizar oferta" para el actor Comercial.</span> |
| **Actores:** | <span>Comercial</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El comercial accede a la sección de ofertas. <br>2.- El sistema muestra un listado con las ofertas vigentes. <br>3.- El comercial selecciona una oferta para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay ofertas vigentes, el sistema muestra un mensaje.</span> |
| **Poscondiciones:**| <span>El comercial ha podido consultar las ofertas.</span> |
| **Artefactos relacionados:**| <span>CU-311</span> |

### ---

| **Nombre:** | <span>Visualizar oferta(Administrador)</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-314</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Versión del caso de uso "Visualizar oferta" para el actor Administrador.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El actor debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El administrador accede a la sección de ofertas. <br>2.- El sistema muestra un listado con las ofertas vigentes. <br>3.- El administrador selecciona una oferta para ver sus detalles.</span> |
| **Flujo Alternativo:** | <span>2.A- Si no hay ofertas vigentes, el sistema muestra un mensaje.</span> |
| **Poscondiciones:**| <span>El administrador ha podido consultar las ofertas.</span> |
| **Artefactos relacionados:**| <span>CU-311</span> |

### ---

### Otros Casos de Uso

| **Nombre:** | <span>Gestionar nueva reserva</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-315</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite a un comercial gestionar una nueva reserva de hotel.</span> |
| **Actores:** | <span>Comercial</span> |
| **Precondiciones:**| <span>El comercial debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El comercial selecciona la opción para gestionar una nueva reserva. <br>2.- El sistema muestra un formulario para introducir los datos. <br>3.- El comercial completa el formulario y confirma. <br>4.- El sistema valida los datos, crea la reserva y muestra confirmación.</span> |
| **Flujo Alternativo:** | <span>4.A- Si los datos son inválidos, el sistema muestra un error.</span> |
| **Poscondiciones:**| <span>La nueva reserva queda registrada en el sistema.</span> |
| **Artefactos relacionados:**| <span></span> |

### ---

| **Nombre:** | <span>Gestionar nueva petición</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-316</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Permite al administrador gestionar las peticiones de los clientes.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:**| <span>El administrador debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El administrador accede a la lista de peticiones. <br>2.- Selecciona una petición y el sistema muestra sus detalles. <br>3.- El administrador realiza las acciones y marca la petición como resuelta.</span> |
| **Flujo Alternativo:** | <span>3.A- Si la petición no puede ser resuelta, puede cambiar su estado a "en progreso".</span> |
| **Poscondiciones:**| <span>La petición del cliente queda resuelta y registrada.</span> |
| **Artefactos relacionados:**| <span></span> |

### ---

### Funcionalidades Incluidas / Extendidas

| **Nombre:** | <span>Recalcular precios</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-317</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Funcionalidad que **extiende** a "Realizar oferta(Comercial)".</span> |
| **Actores:** | <span>(Sistema)</span> |
| **Precondiciones:**| <span>Se está ejecutando "Realizar oferta(Comercial)".</span> |
| **Flujo Normal:** | <span>1.- El sistema recalcula los precios de la oferta en base a los parámetros introducidos.</span> |
| **Flujo Alternativo:** | <span>1.A- Si un parámetro es inválido, el sistema notifica el error.</span> |
| **Poscondiciones:**| <span>Los precios de la oferta son actualizados.</span> |
| **Artefactos relacionados:**| <span>CU-309</span> |

### ---

| **Nombre:** | <span>Bloquear temporalmente una reserva</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-318</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Funcionalidad que **extiende** opcionalmente a "Realizar oferta(Comercial)".</span> |
| **Actores:** | <span>(Sistema)</span> |
| **Precondiciones:**| <span>Se está ejecutando "Realizar oferta(Comercial)" y el comercial activó la opción.</span> |
| **Flujo Normal:** | <span>1.- El sistema bloquea la disponibilidad de la habitación por un tiempo determinado.</span> |
| **Flujo Alternativo:** | <span>1.A- Si la reserva no puede ser bloqueada, el sistema notifica al comercial.</span> |
| **Poscondiciones:**| <span>La habitación queda temporalmente no disponible.</span> |
| **Artefactos relacionados:**| <span>CU-309</span> |

### ---

| **Nombre:** | <span>Buscar elemento</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-319</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Funcionalidad que se **incluye** en "Consultar disponibilidad" y "Consultar reserva".</span> |
| **Actores:** | <span>(Sistema)</span> |
| **Precondiciones:**| <span>Se está ejecutando un caso de uso que lo incluye.</span> |
| **Flujo Normal:** | <span>1.- El sistema recibe los criterios de búsqueda. <br>2.- El sistema filtra y devuelve los resultados.</span> |
| **Flujo Alternativo:** | <span>2.A- Si la búsqueda no arroja resultados, devuelve un conjunto vacío.</span> |
| **Poscondiciones:**| <span>Se obtienen los elementos que coinciden con la búsqueda.</span> |
| **Artefactos relacionados:**| <span>CU-301, CU-305</span> |

### ---

| **Nombre:** | <span>Mostrar calendario</span> |
| :--- | :--- |
| **Codigo:** | <span>CU-320</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/2025</span> |
| **Descripción:** | <span>Funcionalidad que se **incluye** en "Consultar disponibilidad".</span> |
| **Actores:** | <span>(Sistema)</span> |
| **Precondiciones:**| <span>Se está ejecutando el caso de uso "Consultar disponibilidad".</span> |
| **Flujo Normal:** | <span>1.- El sistema presenta un calendario visual. <br>2.- Marca los días con y sin disponibilidad.</span> |
| **Flujo Alternativo:** | <span>2.A- Si ocurre un error al cargar los datos, el sistema muestra un mensaje de error.</span> |
| **Poscondiciones:**| <span>El actor puede ver claramente la disponibilidad en el calendario.</span> |
| **Artefactos relacionados:**| <span>CU-301</span> |

</br>

<p align="center">
  <img src="supuesto_3_DB.jpg" alt="img_supuesto2_DB" width="750">
</p>

## Supuesto 4: Fotografía Online

En una aplicación de fotografía online, los clientes pueden visualizar las fotos, donde de forma excepcional se puede realizar una denuncia sobre la foto. Al denunciar una foto, se ha de introducir una explicación sobre la denuncia. Los clientes también pueden llevar a cabo consultas sobre las fotos, operación que es un caso particular de visualizar las fotos. Los controladores de fotos pueden indicar que una foto debe ser revisada. Esta funcionalidad es un caso general de la funcionalidad de denunciar foto. Además, los controladores también pueden editar la información de las fotos. En esta aplicación también participan usuarios de tipo vendedor. Los vendedores pueden escribir a los clientes para hacerles ofertas sobre los productos de la aplicación. De forma excepcional, al hacer una oferta pueden reducir el precio de un producto. Los vendedores también pueden buscar detalles en las fotos, operación que es un caso particular de visualizar fotos. Pero esa búsqueda conlleva la verificación de los datos introducidos. Por otro lado, los gestores de la aplicación pueden ver ofertas, bloquear ofertas, emitir facturas y editar facturas. La emisión de facturas requiere la participación de un software de facturación. El administrador de la tienda puede ver ofertas, emitir facturas, editar facturas, bloquear ofertas, crear usuarios y editar usuarios. Esta funcionalidad de ver ofertas también la pueden realizar los clientes. Editar usuarios tiene características en común con editar facturas. Crear usuarios conlleva el envío de un email en el que es necesario el uso de un gestor de correo.

<p align="center">
  <img src="supuesto4.jpg" alt="img_supuesto1" width="1000">
</p>

#### Aqui los requisitos del diagrama
#### Aqui los requisitos del diagrama

| **Nombre:** | <span>Visualizar fotos</span> |
| :--- | :--- |
| **Código:** | <span> CU_401</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite a Clientes y Vendedores ver las fotos disponibles en la aplicación.</span> |
| **Actores:** | <span>Cliente, Vendedor</span> |
| **Precondiciones:** | <span>El usuario debe estar autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El usuario accede a la sección de fotos.<br>2.- El sistema carga y muestra la galería de fotos.<br>3.- El usuario puede desplazarse o seleccionar una foto.</span> |
| **Flujo Alternativo:** | <span>.Si el usuario selecciona una foto eliminada/no existente, el sistema muestra un mensaje de error.</span> |
| **Poscondiciones:** | <span>El usuario ha visualizado el contenido de las fotos.</span> |
| **Artefactos relacionados:** | <span>CU_402, CU_409</span> |

---

| **Nombre:** | <span>**Consultar fotos**</span> |
| :--- | :--- |
| **Código:** | <span>CU_402</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite a los Clientes aplicar filtros o criterios de búsqueda avanzados sobre el listado de fotos. Es un caso particular de Visualizar fotos.</span> |
| **Actores:** | <span>Cliente</span> |
| **Precondiciones:** | <span>El sistema está ejecutando Visualizar fotos(CU_400).</span> |
| **Flujo Normal:** | <span>1.- El Cliente selecciona una opción de consulta (ej. aplicar filtro por fecha o tags).<br>2.- El sistema aplica la consulta.<br>3.- El sistema muestra el resultado filtrado.</span> |
| **Flujo Alternativo:** | <span>El sistema no encuentra fotos que coincidan con los criterios y notifica al Cliente.</span> |
| **Poscondiciones:** | <span>El listado de fotos mostrado al Cliente ha sido filtrado según su criterio.</span> |
| **Artefactos relacionados:** | <span>CU_401</span> |

---

| **Nombre:** | <span>**Denunciar foto**</span> |
| :--- | :--- |
| **Código:** | <span>CU_403</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite a un Cliente reportar una foto. Esta acción requiere obligatoriamente introducir una explicación.</span> |
| **Actores:** | <span>Cliente</span> |
| **Precondiciones:** | <span>El Cliente está visualizando una foto.</span> |
| **Flujo Normal:** | <span>1.- El Cliente selecciona "Denunciar foto".<br>2.- El sistema iniciala explicación de la denuncia.<br>3.- El Cliente envía la denuncia.<br>4.- El sistema registra la denuncia para su revisión por el Controlador.</span> |
| **Flujo Alternativo:** | <span> El Cliente cancela el proceso antes de enviar el formulario; la denuncia no se registra.</span> |
| **Poscondiciones:** | <span>Una nueva denuncia ha sido registrada en el sistema.</span> |
| **Artefactos relacionados:** | <span>CU_404, CU_405 </span> |

---

| **Nombre:** | <span>**Explicación Denuncia**</span> |
| :--- | :--- |
| **Código:** | <span>CU_404</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Proceso de introducción de una explicación textual detallando el motivo de la denuncia.</span> |
| **Actores:** | <span>Cliente</span> |
| **Precondiciones:** | <span>Se ha denunciado una foto.</span> |
| **Flujo Normal:** | <span>1.- El sistema presenta el campo de texto para la explicación.<br>2.- El Cliente introduce la explicación.<br>3.- El sistema valida que el texto no esté vacío.</span> |
| **Flujo Alternativo:** | <span> El texto de la explicación excede el límite de caracteres; el sistema pide acortar el texto.</span> |
| **Poscondiciones:** | <span>Se ha capturado una explicación válida para la denuncia en curso.</span> |
| **Artefactos relacionados:** | <span>CU_403</span> |

---

| **Nombre:** | <span>**Indicar revisión**</span> |
| :--- | :--- |
| **Código:** | <span>CU_405</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Controlador marcar que una foto debe ser sometida a un proceso de revisión. **Denunciar foto** es un caso particular de este CU.</span> |
| **Actores:** | <span>Controlador</span> |
| **Precondiciones:** | <span>El Controlador ha iniciado sesión y tiene acceso a las herramientas de gestión de fotos.</span> |
| **Flujo Normal:** | <span>1.- El Controlador selecciona una foto pendiente.<br>2.- El Controlador selecciona la opción "Indicar revisión".<br>3.- El sistema marca la foto con el estado "Pendiente de Revisión".</span> |
| **Flujo Alternativo:** | <span> El Controlador intenta marcar una foto que ya tiene el estado "Revisión en curso"; el sistema muestra una advertencia.</span> |
| **Poscondiciones:** | <span>El estado de la foto ha sido marcado como "Revisión Pendiente".</span> |
| **Artefactos relacionados:** | <span>CU_403</span> |

---

| **Nombre:** | <span>**Editar información**</span> |
| :--- | :--- |
| **Código:** | <span>CU_406</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Controlador modificar los metadatos o la información asociada a una foto.</span> |
| **Actores:** | <span>Controlador</span> |
| **Precondiciones:** | <span>El Controlador ha seleccionado la foto a editar.</span> |
| **Flujo Normal:** | <span>1.- El Controlador accede al formulario de edición de metadatos de la foto.<br>2.- El Controlador modifica uno o más campos (ej. tags, descripción).<br>3.- El sistema guarda los cambios y actualiza la información de la foto.</span> |
| **Flujo Alternativo:** | <span>El Controlador introduce un valor en un formato incorrecto (ej. texto en un campo numérico); el sistema rechaza el guardado y resalta el error.</span> |
| **Poscondiciones:** | <span>La información de la foto ha sido actualizada en la base de datos.</span> |
| **Artefactos relacionados:** | <span></span> |

---

| **Nombre:** | <span>**Realizar oferta**</span> |
| :--- | :--- |
| **Código:** | <span>CU_407</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite a los Vendedores escribir a los Clientes para proponerles una oferta sobre los productos de la aplicación.</span> |
| **Actores:** | <span>Vendedor</span> |
| **Precondiciones:** | <span>El Vendedor tiene un producto asociado y un Cliente objetivo.</span> |
| **Flujo Normal:** | <span>1.- El Vendedor inicia la creación de una oferta.<br>2.- El Vendedor introduce el producto, el precio y el Cliente.<br>3.- El sistema valida la información y registra la oferta.</span> |
| **Flujo Alternativo:** | <span> El sistema detecta que el producto en oferta no tiene stock; el Vendedor debe modificar la oferta o cancelar.</span> |
| **Poscondiciones:** | <span>La oferta ha sido registrada y notificada al Cliente.</span> |
| **Artefactos relacionados:** | <span>CU_408 </span> |

---

| **Nombre:** | <span>**Reducir precio**</span> |
| :--- | :--- |
| **Código:** | <span>CU_408</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Funcionalidad excepcional que permite al Vendedor aplicar un descuento al precio estándar al realizar una oferta.</span> |
| **Actores:** | <span>Vendedor</span> |
| **Precondiciones:** | <span>El Vendedor está en el proceso de realizando una oferta.</span> |
| **Flujo Normal:** | <span>1.- El Vendedor accede al punto de extensión 'reducir precio'.<br>2.- El Vendedor introduce un precio más bajo que el estándar.<br>3.- El sistema valida el precio (ej. debe ser positivo).</span> |
| **Flujo Alternativo:** | <span> El precio introducido está por debajo del mínimo permitido (ej. costo); el sistema rechaza el precio.</span> |
| **Poscondiciones:** | <span>El precio de la oferta se ha establecido con una reducción.</span> |
| **Artefactos relacionados:** | <span>CU_407</span> |

---

| **Nombre:** | <span>**Buscar detalles**</span> |
| :--- | :--- |
| **Código:** | <span>CU_409</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite a los Vendedores realizar una búsqueda avanzada de detalles dentro de una foto. Conlleva la verificación de los datos introducidos. Es un caso particular de Visualizar fotos.</span> |
| **Actores:** | <span>Vendedor</span> |
| **Precondiciones:** | <span>El Vendedor ha seleccionado una foto y el sistema inicia la verificación de datos.</span> |
| **Flujo Normal:** | <span>1.- El Vendedor inicia la búsqueda detallada.<br>2.- El sistema inicia la verificación de datos.<br>3.- El sistema ejecuta la búsqueda y muestra los detalles encontrados.</span> |
| **Flujo Alternativo:** | <span> No se encuentran los detalles buscados en la foto; el sistema notifica la ausencia de resultados.</span> |
| **Poscondiciones:** | <span>Los detalles de la foto han sido presentados al Vendedor.</span> |
| **Artefactos relacionados:** | <span>CU_401, CU_410 </span> |

---

| **Nombre:** | <span>**Verificar datos**</span> |
| :--- | :--- |
| **Código:** | <span>CU_4010</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Proceso de comprobación de la validez y consistencia de los datos introducidos durante la búsqueda de detalles.</span> |
| **Actores:** | <span>Vendedor</span> |
| **Precondiciones:** | <span>Se han buscado detalles previamente</span> |
| **Flujo Normal:** | <span>1.- El sistema recibe los parámetros de búsqueda.<br>2.- El sistema ejecuta las rutinas de validación.<br>3.- El sistema confirma que los datos son válidos.</span> |
| **Flujo Alternativo:** | <span> Uno o más parámetros de búsqueda son inválidos; el sistema detiene la búsqueda y devuelve un error</span> |
| **Poscondiciones:** | <span>Se ha confirmado la validez de los datos de búsqueda.</span> |
| **Artefactos relacionados:** | <span>CU_409</span> |

---

| **Nombre:** | <span>**Ver ofertas (Gestor)**</span> |
| :--- | :--- |
| **Código:** | <span>CU_411</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Gestor visualizar todas las ofertas activas, bloqueadas y finalizadas del sistema.</span> |
| **Actores:** | <span>Gestor</span> |
| **Precondiciones:** | <span>El Gestor ha iniciado sesión con el rol apropiado.</span> |
| **Flujo Normal:** | <span>1.- El Gestor selecciona la opción "Ver ofertas".<br>2.- El sistema carga y muestra el listado completo de ofertas.<br>3.- El Gestor puede ordenar o filtrar el listado.</span> |
| **Flujo Alternativo:** | <span> El Gestor no tiene los permisos para ver todas las ofertas; el sistema solo muestra un subconjunto o niega el acceso.</span> |
| **Poscondiciones:** | <span>El Gestor ha visualizado la información de las ofertas del sistema.</span> |
| **Artefactos relacionados:** | <span>CU_415 </span> |

---

| **Nombre:** | <span>**Bloquear ofertas**</span> |
| :--- | :--- |
| **Código:** | <span>CU_412</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Gestor o Administrador inhabilitar o cancelar una oferta para que deje de ser visible o aceptable por el Cliente.</span> |
| **Actores:** | <span>Gestor, Administrador</span> |
| **Precondiciones:** | <span>El actor ha identificado una oferta activa.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona la oferta y elige "Bloquear".<br>2.- El sistema solicita confirmación.<br>3.- El sistema cambia el estado de la oferta a "Bloqueada".</span> |
| **Flujo Alternativo:** | <span> La oferta ya ha sido aceptada o expiró; el sistema niega la acción y sugiere anular la venta (si aplica).</span> |
| **Poscondiciones:** | <span>La oferta seleccionada pasa al estado "Bloqueada".</span> |
| **Artefactos relacionados:** | <span></span> |

---

| **Nombre:** | <span>**Emitir facturas**</span> |
| :--- | :--- |
| **Código:** | <span>CU_413</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Genera un documento de factura para una venta completada. Esta operación requiere la intervención de un sistema externo de facturación.</span> |
| **Actores:** | <span>Gestor, Administrador, Software de facturación (actor externo)</span> |
| **Precondiciones:** | <span>Existe una venta completada pendiente de facturar.</span> |
| **Flujo Normal:** | <span>1.- El actor selecciona la venta y elige "Emitir factura".<br>2.- El sistema envía los datos de la venta al Software de facturación.<br>3.- El sistema recibe la factura generada y la asocia a la venta.</span> |
| **Flujo Alternativo:** | <span> El software externo no responde o devuelve un error; el sistema notifica y permite reintentar.</span> |
| **Poscondiciones:** | <span>Se ha generado una factura y se ha asociado a la venta.</span> |
| **Artefactos relacionados:** | <span></span> |

---

| **Nombre:** | <span>**Editar facturas**</span> |
| :--- | :--- |
| **Código:** | <span>CU_414</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Gestor o Administrador modificar los datos de una factura ya emitida (ej. corrección de datos fiscales).</span> |
| **Actores:** | <span>Gestor, Administrador</span> |
| **Precondiciones:** | <span>El actor ha seleccionado una factura.</span> |
| **Flujo Normal:** | <span>1.- El actor accede al formulario de edición de la factura.<br>2.- El actor realiza las modificaciones (ej. dirección, nombre).<br>3.- El sistema valida y guarda la factura editada.</span> |
| **Flujo Alternativo:** | <span> La factura tiene un estado que impide la edición directa; el sistema requiere generar una nota de crédito/débito.</span> |
| **Poscondiciones:** | <span>Los datos de la factura han sido actualizados.</span> |
| **Artefactos relacionados:** | <span>CU_418 </span> |

---

| **Nombre:** | <span>**Ver ofertas**</span> |
| :--- | :--- |
| **Código:** | <span>CU_415</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Cliente y al Administrador visualizar las ofertas (las recibidas o todas, respectivamente).</span> |
| **Actores:** | <span>Cliente, Administrador</span> |
| **Precondiciones:** | <span>El usuario está autenticado en el sistema.</span> |
| **Flujo Normal:** | <span>1.- El usuario accede a la sección de ofertas.<br>2.- El sistema muestra el listado de ofertas pertinentes (propias para el Cliente).<br>3.- El usuario puede seleccionar una oferta.</span> |
| **Flujo Alternativo:** | <span> El sistema muestra un mensaje indicando que no hay ofertas disponibles para el usuario en ese momento.</span> |
| **Poscondiciones:** | <span>El usuario ha revisado las ofertas disponibles.</span> |
| **Artefactos relacionados:** | <span>CU_411 </span> |

---

| **Nombre:** | <span>**Crear usuarios**</span> |
| :--- | :--- |
| **Código:** | <span>CU_416</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Administrador dar de alta un nuevo usuario en el sistema. Conlleva la notificación por correo electrónico.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:** | <span>El Administrador ha iniciado sesión.</span> |
| **Flujo Normal:** | <span>1.- El Administrador introduce los datos del nuevo usuario.<br>2.- El sistema valida los datos y registra el usuario.<br>3.- El sistema inicia el envío de Email</span> |
| **Flujo Alternativo:** | <span> Ya existe un usuario con el mismo email o DNI; el sistema rechaza la creación y notifica al Administrador.</span> |
| **Poscondiciones:** | <span>Se ha creado un nuevo registro de usuario y se ha enviado un email de bienvenida.</span> |
| **Artefactos relacionados:** | <span>CU_417 , CU_418 </span> |

---

| **Nombre:** | <span>**Enviar e-mail**</span> |
| :--- | :--- |
| **Código:** | <span>CU_417</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Proceso de envío de un correo electrónico (ej. bienvenida, confirmación de cuenta), utilizando un gestor de correo externo.</span> |
| **Actores:** | <span>Gestor de correo (actor externo)</span> |
| **Precondiciones:** | <span>Se ha creado un usuario.</span> |
| **Flujo Normal:** | <span>1.- El sistema prepara el contenido del email.<br>2.- El sistema interactúa con el Gestor de correo externo.<br>3.- El sistema recibe la confirmación de envío.</span> |
| **Flujo Alternativo:** | <span> La dirección de correo es incorrecta o el envío rebota; el sistema registra un estado de "email fallido" para el usuario.</span> |
| **Poscondiciones:** | <span>Se ha intentado o completado el envío del correo electrónico al nuevo usuario.</span> |
| **Artefactos relacionados:** | <span>CU_416 </span> |

---

| **Nombre:** | <span>**Editar usuarios**</span> |
| :--- | :--- |
| **Código:** | <span>CU_418</span> |
| **Autor:** | <span>INRE Equipo Azul</span> |
| **Fecha:** | <span>15/10/25</span> |
| **Descripción:** | <span>Permite al Administrador modificar los datos de cualquier usuario (rol, información de contacto, etc.). Comparte características con Editar facturas.</span> |
| **Actores:** | <span>Administrador</span> |
| **Precondiciones:** | <span>El Administrador ha seleccionado un usuario existente.</span> |
| **Flujo Normal:** | <span>1.- El Administrador accede al formulario de edición del usuario.<br>2.- El Administrador modifica los datos necesarios.<br>3.- El sistema valida y guarda los cambios en el perfil del usuario.</span> |
| **Flujo Alternativo:** | <span>El Administrador intenta rebajar su propio rol a uno inferior; el sistema rechaza la operación por seguridad.</span> |
| **Poscondiciones:** | <span>Los datos del usuario han sido actualizados.</span> |
| **Artefactos relacionados:** | <span>CU_414 </span> |

</br>

## Supuesto 5: Gestión de Incidencias

En un sistema de gestión de incidencias, los técnicos y los operadores pueden dar de alta incidencias, para lo cual, de forma excepcional se enviará un correo (en esta operación participa un sistema de gestión de correo). Los técnicos también atienden llamadas telefónicas y realizan informes sobre las incidencias. Por su parte, los operadores atienden llamadas telefónicas, marcan incidencias como duplicadas y ordenan incidencias. La forma de atender llamadas de los técnicos y los operadores no es exactamente igual, pero tiene similitudes. De forma específica, cuando los técnicos atienden llamadas, comprueban datos de la incidencia en el sistema. Cuando los operadores atienden llamadas, introducen nuevos datos de la incidencia. Los administradores del sistema gestionan categorías de incidencias, consultan incidencias y ordenan incidencias. La ordenación por parte de los administradores conlleva la adición de un comentario. Los técnicos y los operadores también pueden consultar incidencias. La consulta de incidencias por parte técnicos, operadores y administradores puede conllevar, de forma excepcional, la edición de los datos de la incidencia. Los usuarios invitados también pueden consultar incidencias, pero sin la posible edición de los datos. Además, los invitados informan sobre posibles incidencias, se pueden registrar para ver notificaciones y pueden acceder a un listado del histórico de notificaciones. El informe de posibles incidencias conlleva el dar de alta la localización en un mapa, la incorporación de una explicación completa en formato textual y la subida de una foto.

<p align="center">
  <img src="supuesto5.jpg" alt="img_supuesto1" width="750">
</p>

### Requisitos del diagrama de casos de uso

| **Nombre:** | Dar de Alta Incidencia |
| :--- | :--- |
| **Codigo:** | CU-501 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Caso de uso general para dar de alta una nueva incidencia en el sistema. Opcionalmente, se extiende para enviar un correo de notificación. |
| **Actores:** | Técnico, Operador |
| **Precondiciones:**| El actor debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El actor inicia el proceso para dar de alta una incidencia. <br>2.- El sistema solicita la información requerida. <br>3.- El actor introduce los datos de la incidencia. <br>4.- El sistema valida y registra la nueva incidencia. |
| **Flujo Alternativo:** | 3.A- De forma excepcional, el actor puede ejecutar el caso de uso "Enviar correo" (CU-502) para notificar la alta. |
| **Poscondiciones:**| La incidencia queda registrada en el sistema. |
| **Artefactos relacionados:**| CU-502, CU-503, CU-504 |

### ---

| **Nombre:** | Enviar correo |
| :--- | :--- |
| **Codigo:** | CU-502 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** opcionalmente a "Dar de Alta Incidencia" para enviar una notificación por correo. |
| **Actores:** | Gestor de correos |
| **Precondiciones:**| Se está ejecutando el caso de uso "Dar de Alta Incidencia". |
| **Flujo Normal:** | 1.- El sistema invoca al gestor de correos con los detalles de la incidencia. <br>2.- El gestor de correos envía la notificación a los interesados. |
| **Flujo Alternativo:** | 2.A- Si el envío del correo falla, el sistema registra el error pero continúa el flujo principal. |
| **Poscondiciones:**| Se ha enviado un correo electrónico notificando la nueva incidencia. |
| **Artefactos relacionados:**| CU-501 |

### ---

| **Nombre:** | Dar de Alta Incidencia (Técnicos) |
| :--- | :--- |
| **Codigo:** | CU-503 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Dar de Alta Incidencia" para el actor Técnico. |
| **Actores:** | Técnico |
| **Precondiciones:**| El actor debe estar autenticado como Técnico. |
| **Flujo Normal:** | 1.- El técnico inicia el alta de la incidencia. <br>2.- El sistema pide los datos. <br>3.- El técnico introduce los detalles. <br>4.- El sistema registra la incidencia. |
| **Flujo Alternativo:** | 3.A- Opcionalmente, se ejecuta "Enviar correo" (CU-502). |
| **Poscondiciones:**| La incidencia queda registrada en el sistema. |
| **Artefactos relacionados:**| CU-501, CU-502 |

### ---

| **Nombre:** | Dar de Alta Incidencia (Operadores) |
| :--- | :--- |
| **Codigo:** | CU-504 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Dar de Alta Incidencia" para el actor Operador. |
| **Actores:** | Operador |
| **Precondiciones:**| El actor debe estar autenticado como Operador. |
| **Flujo Normal:** | 1.- El operador inicia el alta de la incidencia. <br>2.- El sistema pide los datos. <br>3.- El operador introduce los detalles. <br>4.- El sistema registra la incidencia. |
| **Flujo Alternativo:** | 3.A- Opcionalmente, se ejecuta "Enviar correo" (CU-502). |
| **Poscondiciones:**| La incidencia queda registrada en el sistema. |
| **Artefactos relacionados:**| CU-501, CU-502 |

### ---

| **Nombre:** | Atender llamadas |
| :--- | :--- |
| **Codigo:** | CU-505 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Caso de uso general para la atención de llamadas relacionadas con incidencias. |
| **Actores:** | Técnico, Operador |
| **Precondiciones:**| El actor debe estar autenticado. |
| **Flujo Normal:** | 1.- El actor recibe una llamada sobre una incidencia. <br>2.- El actor busca la incidencia en el sistema. <br>3.- El actor gestiona la llamada según su rol. |
| **Flujo Alternativo:** | 2.A- Si la incidencia no se encuentra, el actor puede proceder a darla de alta. |
| **Poscondiciones:**| La llamada ha sido atendida y la incidencia correspondiente actualizada si es necesario. |
| **Artefactos relacionados:**| CU-506, CU-507 |

### ---

| **Nombre:** | Atender llamadas (Técnicos) |
| :--- | :--- |
| **Codigo:** | CU-506 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión de "Atender llamadas" para el Técnico, que **incluye** la comprobación de datos de la incidencia. |
| **Actores:** | Técnico |
| **Precondiciones:**| El actor debe estar autenticado como Técnico. |
| **Flujo Normal:** | 1.- El técnico atiende la llamada. <br>2.- El sistema solicita el identificador de la incidencia. <br>3.- El técnico lo introduce y se ejecuta "Comprobar datos de incidencia" (CU-508). <br>4.- El técnico resuelve la consulta. |
| **Flujo Alternativo:** | 3.A- Si los datos son incorrectos, el sistema lo notifica. |
| **Poscondiciones:**| La consulta de la llamada ha sido resuelta. |
| **Artefactos relacionados:**| CU-505, CU-508 |

### ---

| **Nombre:** | Atender llamadas (Operadores) |
| :--- | :--- |
| **Codigo:** | CU-507 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión de "Atender llamadas" para el Operador, que **extiende** la funcionalidad para introducir nuevos datos. |
| **Actores:** | Operador |
| **Precondiciones:**| El actor debe estar autenticado como Operador. |
| **Flujo Normal:** | 1.- El operador atiende la llamada y busca la incidencia. <br>2.- El operador actualiza la información verbalmente. |
| **Flujo Alternativo:** | 1.A- Si es necesario, se ejecuta la extensión "Introducir nuevos datos incidencia" (CU-509). |
| **Poscondiciones:**| La llamada ha sido gestionada. |
| **Artefactos relacionados:**| CU-505, CU-509 |

### ---

| **Nombre:** | Comprobar datos de incidencia |
| :--- | :--- |
| **Codigo:** | CU-508 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Atender llamadas (Técnicos)" para verificar los datos de una incidencia. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Atender llamadas (Técnicos)". |
| **Flujo Normal:** | 1.- El sistema recibe el identificador de la incidencia. <br>2.- El sistema busca y muestra los datos de la incidencia. |
| **Flujo Alternativo:** | 2.A- Si la incidencia no existe, el sistema devuelve un error. |
| **Poscondiciones:**| Los datos de la incidencia han sido verificados y mostrados. |
| **Artefactos relacionados:**| CU-506 |

### ---

| **Nombre:** | Introducir nuevos datos incidencia |
| :--- | :--- |
| **Codigo:** | CU-509 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** a "Atender llamadas (Operadores)" para añadir información a una incidencia. |
| **Actores:** | Operador |
| **Precondiciones:**| Se está ejecutando "Atender llamadas (Operadores)". |
| **Flujo Normal:** | 1.- El operador activa la opción para añadir nuevos datos. <br>2.- El sistema muestra los campos para añadir la nueva información. <br>3.- El operador introduce los datos y los guarda. |
| **Flujo Alternativo:** | 3.A- El operador cancela la operación y no se guardan cambios. |
| **Poscondiciones:**| La incidencia ha sido actualizada con nueva información. |
| **Artefactos relacionados:**| CU-507 |

### ---

| **Nombre:** | Consultar incidencias (comun editores) |
| :--- | :--- |
| **Codigo:** | CU-510 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a los usuarios con permisos de edición consultar incidencias, con la opción de editar sus datos. |
| **Actores:** | Técnico, Operador, Administrador |
| **Precondiciones:**| El actor debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El actor busca y selecciona una incidencia. <br>2.- El sistema muestra los detalles de la incidencia. |
| **Flujo Alternativo:** | 2.A- De forma excepcional, el actor puede ejecutar el caso de uso "Editar datos de la incidencia" (CU-511). |
| **Poscondiciones:**| El actor ha consultado la información de la incidencia. |
| **Artefactos relacionados:**| CU-511, CU-512, CU-513, CU-514, CU-530 |

### ---

| **Nombre:** | Editar datos de la incidencia |
| :--- | :--- |
| **Codigo:** | CU-511 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad que **extiende** opcionalmente a "Consultar incidencias (comun editores)" para modificar los datos de una incidencia. |
| **Actores:** | Técnico, Operador, Administrador |
| **Precondiciones:**| Se está ejecutando el caso de uso "Consultar incidencias (comun editores)". |
| **Flujo Normal:** | 1.- El actor elige la opción para editar. <br>2.- El sistema presenta un formulario con los datos editables. <br>3.- El actor modifica los datos y guarda los cambios. |
| **Flujo Alternativo:** | 3.A- El actor cancela la edición y los datos no se modifican. |
| **Poscondiciones:**| Los datos de la incidencia han sido actualizados. |
| **Artefactos relacionados:**| CU-510 |

### ---

| **Nombre:** | Consultar incidencias (Técnicos) |
| :--- | :--- |
| **Codigo:** | CU-512 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Consultar incidencias" para el actor Técnico. |
| **Actores:** | Técnico |
| **Precondiciones:**| El actor debe estar autenticado como Técnico. |
| **Flujo Normal:** | 1.- El técnico accede a la consulta de incidencias. <br>2.- El sistema muestra por defecto las incidencias asignadas al técnico. <br>3.- El técnico puede realizar búsquedas. |
| **Flujo Alternativo:** | 3.A- Opcionalmente, el técnico puede editar la incidencia (CU-511). |
| **Poscondiciones:**| El actor ha visualizado la información de la incidencia. |
| **Artefactos relacionados:**| CU-510 |

### ---

| **Nombre:** | Consultar incidencias (Operadores) |
| :--- | :--- |
| **Codigo:** | CU-513 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Consultar incidencias" para el actor Operador. |
| **Actores:** | Operador |
| **Precondiciones:**| El actor debe estar autenticado como Operador. |
| **Flujo Normal:** | 1.- El operador accede a la consulta de incidencias. <br>2.- El sistema muestra un panel con filtros de búsqueda. <br>3.- El operador busca y visualiza las incidencias. |
| **Flujo Alternativo:** | 3.A- Opcionalmente, el operador puede editar la incidencia (CU-511). |
| **Poscondiciones:**| El actor ha visualizado la información de la incidencia. |
| **Artefactos relacionados:**| CU-510 |

### ---

| **Nombre:** | Consultar incidencias (Administradores) |
| :--- | :--- |
| **Codigo:** | CU-514 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Consultar incidencias" para el actor Administrador. |
| **Actores:** | Administrador |
| **Precondiciones:**| El actor debe estar autenticado como Administrador. |
| **Flujo Normal:** | 1.- El administrador accede a la consulta de incidencias. <br>2.- El sistema proporciona opciones de búsqueda avanzadas. <br>3.- El administrador busca y visualiza las incidencias. |
| **Flujo Alternativo:** | 3.A- Opcionalmente, el administrador puede editar la incidencia (CU-511). |
| **Poscondiciones:**| El actor ha visualizado la información de la incidencia. |
| **Artefactos relacionados:**| CU-510 |

### ---

| **Nombre:** | Realizar informe |
| :--- | :--- |
| **Codigo:** | CU-515 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a un técnico generar un informe detallado sobre una incidencia. |
| **Actores:** | Técnico |
| **Precondiciones:**| El actor debe estar autenticado como Técnico y la incidencia sobre la que se informa debe existir. |
| **Flujo Normal:** | 1.- El técnico selecciona una incidencia para realizar un informe. <br>2.- El sistema presenta una plantilla para el informe. <br>3.- El técnico rellena los campos con el análisis, las acciones realizadas y las conclusiones. <br>4.- El técnico guarda el informe, que queda asociado a la incidencia. |
| **Flujo Alternativo:** | 3.A- El técnico cancela la creación del informe. |
| **Poscondiciones:**| Se ha generado y almacenado un nuevo informe en el sistema. |
| **Artefactos relacionados:**| |

### ---

| **Nombre:** | Marcar incidencias como duplicada |
| :--- | :--- |
| **Codigo:** | CU-516 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a un operador marcar una incidencia como duplicada de otra ya existente. |
| **Actores:** | Operador |
| **Precondiciones:**| El actor debe estar autenticado como Operador. Deben existir al menos dos incidencias que puedan ser relacionadas. |
| **Flujo Normal:** | 1.- El operador selecciona la incidencia que quiere marcar como duplicada. <br>2.- El sistema solicita el identificador de la incidencia original. <br>3.- El operador lo introduce y el sistema vincula ambas incidencias. <br>4.- La incidencia duplicada cambia su estado a "cerrada" o "duplicada". |
| **Flujo Alternativo:** | 3.A- Si el identificador de la incidencia original no es válido, el sistema muestra un error. |
| **Poscondiciones:**| Una incidencia ha sido marcada como duplicada y vinculada a la original. |
| **Artefactos relacionados:**| |

### ---

| **Nombre:** | Ordenan incidencias |
| :--- | :--- |
| **Codigo:** | CU-517 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Caso de uso general que permite a operadores y administradores ordenar las incidencias según diferentes criterios. |
| **Actores:** | Operador, Administrador |
| **Precondiciones:**| El actor debe estar autenticado. |
| **Flujo Normal:** | 1.- El actor accede a la vista de listado de incidencias. <br>2.- El actor selecciona un criterio de ordenación (prioridad, fecha, estado, etc.). <br>3.- El sistema reorganiza el listado de incidencias según el criterio seleccionado. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El listado de incidencias se muestra en el orden deseado. |
| **Artefactos relacionados:**| CU-518, CU-519 |

### ---

| **Nombre:** | Ordenan incidencias (Operadores) |
| :--- | :--- |
| **Codigo:** | CU-518 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión del caso de uso "Ordenan incidencias" para el actor Operador. |
| **Actores:** | Operador |
| **Precondiciones:**| El actor debe estar autenticado como Operador. |
| **Flujo Normal:** | 1.- El operador accede al listado de incidencias. <br>2.- El operador aplica un filtro de ordenación. <br>3.- El sistema actualiza la vista. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| Las incidencias se muestran ordenadas. |
| **Artefactos relacionados:**| CU-517 |

### ---

| **Nombre:** | Ordenan incidencias (Administradores) |
| :--- | :--- |
| **Codigo:** | CU-519 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Versión de "Ordenan incidencias" para el Administrador, que **incluye** la funcionalidad de "Añadir comentario". |
| **Actores:** | Administrador |
| **Precondiciones:**| El actor debe estar autenticado como Administrador. |
| **Flujo Normal:** | 1.- El administrador ordena las incidencias. <br>2.- Se ejecuta el caso de uso "Añadir comentario" (CU-520) para justificar la ordenación. <br>3.- El sistema guarda el orden y el comentario. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| Las incidencias se han ordenado y se ha añadido un comentario explicativo. |
| **Artefactos relacionados:**| CU-517, CU-520 |

### ---

| **Nombre:** | Añadir comentario |
| :--- | :--- |
| **Codigo:** | CU-520 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad que se **incluye** en "Ordenan incidencias (Administradores)" para agregar un comentario. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Ordenan incidencias (Administradores)". |
| **Flujo Normal:** | 1.- El sistema solicita al administrador que introduzca un comentario. <br>2.- El administrador escribe y guarda el comentario. <br>3.- El comentario queda registrado. |
| **Flujo Alternativo:** | 2.A- El administrador decide no añadir un comentario y continúa. |
| **Poscondiciones:**| Se ha añadido un comentario a la acción de ordenación. |
| **Artefactos relacionados:**| CU-519 |

### ---

| **Nombre:** | Gestionar categorías incidencias |
| :--- | :--- |
| **Codigo:** | CU-521 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite al administrador crear, editar y eliminar las categorías de las incidencias. |
| **Actores:** | Administrador |
| **Precondiciones:**| El actor debe estar autenticado como Administrador. |
| **Flujo Normal:** | 1.- El administrador accede a la sección de gestión de categorías. <br>2.- El sistema muestra las categorías existentes. <br>3.- El administrador puede crear una nueva, modificar o eliminar una existente. <br>4.- El sistema aplica los cambios en la base de datos. |
| **Flujo Alternativo:** | 3.A- Si se intenta eliminar una categoría en uso, el sistema lo impide y muestra una notificación. |
| **Poscondiciones:**| El listado de categorías de incidencias ha sido actualizado. |
| **Artefactos relacionados:**| |

### ---

| **Nombre:** | Consultar incidencia (invitados) |
| :--- | :--- |
| **Codigo:** | CU-522 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a los usuarios invitados consultar incidencias públicas con información limitada y sin opción a edición. |
| **Actores:** | Invitado |
| **Precondiciones:**| Ninguna. |
| **Flujo Normal:** | 1.- El invitado accede al portal público de incidencias. <br>2.- El sistema muestra una lista de incidencias públicas. <br>3.- El invitado puede usar un buscador básico para filtrar los resultados. <br>4.- El invitado selecciona una incidencia para ver su estado y descripción general. |
| **Flujo Alternativo:** | 3.A- Si la búsqueda no arroja resultados, el sistema lo indica. |
| **Poscondiciones:**| El invitado ha consultado el estado de una incidencia pública. |
| **Artefactos relacionados:**| CU-530 |

### ---

| **Nombre:** | Informar incidencias |
| :--- | :--- |
| **Codigo:** | CU-523 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a un usuario invitado informar sobre una posible incidencia. **Incluye** dar de alta la localización, añadir una explicación y subir una foto. |
| **Actores:** | Invitado |
| **Precondiciones:**| Ninguna. |
| **Flujo Normal:** | 1.- El invitado selecciona la opción para informar de una incidencia. <br>2.- Se ejecuta "Dar de alta la localizacion de un mapa" (CU-524). <br>3.- Se ejecuta "Dar explicación completa en formato textual" (CU-525). <br>4.- Se ejecuta "Subir foto" (CU-526). <br>5.- El invitado envía el informe y el sistema crea un borrador de incidencia para su revisión. |
| **Flujo Alternativo:** | 5.A- El invitado cancela el proceso. |
| **Poscondiciones:**| Se ha enviado un informe de una posible incidencia para que sea validada por un operador. |
| **Artefactos relacionados:**| CU-524, CU-525, CU-526 |

### ---

| **Nombre:** | Dar de alta la localizacion de un mapa |
| :--- | :--- |
| **Codigo:** | CU-524 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Informar incidencias" para especificar la ubicación del suceso. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Informar incidencias". |
| **Flujo Normal:** | 1.- El sistema muestra un mapa interactivo. <br>2.- El invitado selecciona la ubicación exacta en el mapa. <br>3.- El sistema guarda las coordenadas. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| La localización de la incidencia ha sido registrada. |
| **Artefactos relacionados:**| CU-523 |

### ---

| **Nombre:** | Dar explicación completa en formato textual |
| :--- | :--- |
| **Codigo:** | CU-525 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Informar incidencias" para detallar lo ocurrido. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Informar incidencias". |
| **Flujo Normal:** | 1.- El sistema muestra un campo de texto. <br>2.- El invitado escribe la descripción de la incidencia. <br>3.- El sistema guarda el texto. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| La descripción de la incidencia ha sido registrada. |
| **Artefactos relacionados:**| CU-523 |

### ---

| **Nombre:** | Subir foto |
| :--- | :--- |
| **Codigo:** | CU-526 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Informar incidencias" para adjuntar una imagen como evidencia. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando "Informar incidencias". |
| **Flujo Normal:** | 1.- El sistema muestra un botón para seleccionar un archivo. <br>2.- El invitado selecciona una foto de su dispositivo. <br>3.- El sistema adjunta la foto al informe. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| Se ha adjuntado una foto al informe de la incidencia. |
| **Artefactos relacionados:**| CU-523 |

### ---

| **Nombre:** | Registrarse |
| :--- | :--- |
| **Codigo:** | CU-527 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a un invitado crear una cuenta de usuario en el sistema. **Incluye** la funcionalidad "Ver notificaciones". |
| **Actores:** | Invitado |
| **Precondiciones:**| Ninguna. |
| **Flujo Normal:** | 1.- El invitado accede al formulario de registro. <br>2.- El invitado introduce sus datos personales y credenciales. <br>3.- El sistema valida los datos y crea la cuenta. <br>4.- El nuevo usuario puede ahora "Ver notificaciones" (CU-528). |
| **Flujo Alternativo:** | 3.A- Si los datos no son válidos (ej. email ya existe), el sistema muestra un error. |
| **Poscondiciones:**| El invitado se ha convertido en un usuario registrado del sistema. |
| **Artefactos relacionados:**| CU-528 |

### ---

| **Nombre:** | Ver notificaciones |
| :--- | :--- |
| **Codigo:** | CU-528 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Funcionalidad **incluida** en "Registrarse", que permite a los usuarios ver las notificaciones de sus incidencias. |
| **Actores:** | (Sistema) |
| **Precondiciones:**| Se está ejecutando el caso de uso "Registrarse" o el usuario ya está registrado. |
| **Flujo Normal:** | 1.- El usuario accede a su panel personal. <br>2.- El sistema muestra una lista con las últimas notificaciones. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El usuario ha visualizado sus notificaciones. |
| **Artefactos relacionados:**| CU-527 |

### ---

| **Nombre:** | Acceder a listado historico de notificaciones |
| :--- | :--- |
| **Codigo:** | CU-529 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Permite a los usuarios registrados consultar el historial completo de sus notificaciones. |
| **Actores:** | Invitado (ya registrado) |
| **Precondiciones:**| El actor debe estar autenticado en el sistema. |
| **Flujo Normal:** | 1.- El usuario accede a la sección de historial de notificaciones. <br>2.- El sistema muestra un listado completo y paginado de todas las notificaciones recibidas. <br>3.- El usuario puede navegar y buscar en su historial. |
| **Flujo Alternativo:** | |
| **Poscondiciones:**| El usuario ha consultado su historial de notificaciones. |
| **Artefactos relacionados:**| |

### ---

| **Nombre:** | Consultar Incidencias |
| :--- | :--- |
| **Codigo:** | CU-530 |
| **Autor:** | INRE Equipo Azul |
| **Fecha:** | 16/10/2025 |
| **Descripción:** | Caso de uso general que permite a los diferentes actores del sistema buscar y visualizar las incidencias según sus permisos. |
| **Actores:** | Técnico, Operador, Administrador, Invitado |
| **Precondiciones:**| El actor debe estar autenticado (excepto el Invitado). |
| **Flujo Normal:** | 1.- El actor accede a la funcionalidad para consultar incidencias. <br>2.- El sistema muestra una interfaz de búsqueda. <br>3.- El actor introduce los criterios de búsqueda y el sistema muestra un listado de incidencias que coinciden. <br>4.- El actor selecciona una incidencia para ver sus detalles. |
| **Flujo Alternativo:** | 3.A- Si la búsqueda no produce resultados, el sistema muestra un mensaje informativo. |
| **Poscondiciones:**| El actor ha visualizado la información de las incidencias solicitadas. |
| **Artefactos relacionados:**| CU-510, CU-522 |
