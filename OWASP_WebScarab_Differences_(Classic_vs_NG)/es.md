**Esta página intenta documentar las diferencias entre WebScaraba
clásico y webScarab siguiente generación**

Esl objetivo es listar las características principales que tiene uno
sobre el otro, intentando mostrar la importación de características
deseables de el Clásico a Next Generation (NG por sus siglas en inglés).

## Funcionalidad del marco de trabajo

NG no tiene un concepto de Jar de cookie compartida, el cual es usado en
el clásico para permitir a los plugins como el "Spider" o las peticiones
manuales a usar las cookies mas recientes para un URL en particular.
Esto puede/debe ser reemplazado por un módulo de identidad, el cual
puede proveer los identificadores mas recientes para una identidad en
particular (Cookies, autentificación básica, etc).

NG también tiene ahora la funcionalidad de Transcoded, implementada como
una ventana no modal. La cual pretende implementar menús de clic derecho
para realizar varias operaciones de transcodificación "en el lugar" en
campos arbitrarios de texto.

## Plugins

NG tienes muchos menos plugins que la versión clásica. Los únicos
plugins actualmente implementados en NG son el Proxy, las peticiones
manuales y los plugins de servicios Web.

Algunas características de el plugin de proxy faltan de ser migradas:

  - Script de BeanShell para la modificación por programación de
    peticiones/respuestas.
  - plugins miceláneos de proxy - Revelar campos ocultos, evitar guardar
    las respuestas en memoria rápida.
  - La habilidad de modificar la configuración de proxy del Internet
    Explorer al iniciar y al salir

Algunas características de el plugin de peticiones manuales faltan por
migrar:

  - La habilidad para convertir las peticiones de GET a POST o POST
    multipart y viceversa.

Esto deja los siguientes plugins a ser implementados:

  - Spider
  - Estensiones
  - XSSCRLF
  - Análisis de Identificadores de sesión
  - Scripting
  - Fragmentos
  - Comparación
  - Búsqueda

Migracion de el plugin de Servicios Web a NG esta completa parcialmente.
Actualmente es suficiente acceder a el servicio Web de WebGoat, pero no
soporta tipos de datos complejos. Esta funcionalidad puede ser
fácilmente agregada si se desea.

## Suporte del protocolo HTTP

WebScarab Clásico tiene soporte para autentificacion para servidores
usando certificados de cliente (incluyendo aquellos almacenados en una
tarjeta inteligente), también usando NTLM. NG actualmente no soporta
certificados SSL de cliente. NTML debe ser soportado a través de la
librería HTTPClient de Apache, pero no ha sido probada.

## Sugerencias de Migración

Para las personas interesadas en contribuir en este proyecto al migrar
uno de los plugins de arriba, aquí hay algunas sugerencias:

  - Análisis de identificadores de sesión

El plugin actual de análisis de identificadores de sesión, aunque se ve
muy bien, en realidad es muy engañoso. Cualquiera que quiera implementar
esta característica para NG le recomendaría que viera el "stompy de
Michal Zalewski" para ver como se puede hacer mejor.

  - Búsqueda y comparación

Estos plugins son muy anticuados para usarlos. Hace mucho mas sentido
hacer estas características disponibles como parte de la interfaz
principal, mas que relegarlos. La Búsqueda debe proveer una interfaz
simple donde el operador pueda teclear algún texto y dar clic en "Ir",
mas que tener que escribir código.

  - Spider

Este plugin debe también identificar las Formas en las respuestas HTML e
identificar aquellas que ha sido enviadas para compararlas con los
parametros de la petición GET o con el cuerpo del POST, usando un
algoritmo de comparación inteligente. (Los parámetros vacíos en la forma
pueden ser comparados con cualquier cosa en el GET/POST)

## Ejecución

WebScarab NG solamente puede ser ejecutado por el momento vía WebStart,
lo cual puede ser un problema hasta cierto punto. Un paquete alternativo
ha sido creado, usando el plugin de Maven onejar, el cual empaqueta
todos los jars requeridos en un subdirectorio del "onejar" y provee un
cargador de clases especializado para permitir a Java acceder al
contenido de esos jars.

[Categoría:Proyecto OWASP
WebScarab](Category:OWASP_WebScarab_Project "wikilink")
[Categoría:Proyecto WebScarab
NG](Category:OWASP_WebScarab_NG_Project "wikilink")