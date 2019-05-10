**Bienvenido al proyecto WebScarab**

Webscarab es un marco de trabajo para analizar aplicaciónes web que se
comunica usando los protocolos HTTP y HTTPS. Esta escrito en Java, por
lo que es portable a muchas plataformas. WebScarac tiene muchos modos de
operación, implementados por varios plugins. Su uso mas común es operar
WebScarab como un proxy de intercepción, que permite al operador revisar
y modificar las peticiones creadas por el navegador antes de que sean
enviados al servidor, y para revisar y modificar respuestas enviadas por
el servidor antes de que sean recividas por el navegador. Webscarab es
capaz de interceptar comunicacion en HTTP y HTTPS. El operador puede
tambien revisar las conversaciones (peticiones y respuestas) que hayan
pasado por WebScarab.

Usted puede tambien estar interesado en probar la [nueva generación de
WebScarab](OWASP_WebScarab_NG_Project "wikilink").

## Imagenes

Aqui está la ventana principal de WebScarab. Vea la guía de [inicio en
WebScarab](WebScarab_Getting_Started "wikilink") para mas imagenes de
WebScarab en acción.

![Image:WebScarab after browsing.png](WebScarab_after_browsing.png
"Image:WebScarab after browsing.png")

## Introducción

No hay ningun gran boton rojo en WebScarab, es una herramienta diseñada
principalmente para ser usada por personas que pueden escribir codigo
por ellos mismos, or al menos tienen un muy buen conocimiento el
protocolo HTTP. Si eso suena como a usted, Bienvenido\! baje WebScarab,
unase a la lista de distribución en la [pagina de suscripción de
OWASP](http://lists.owasp.org/mailman/listinfo/owasp-webscarab) y a
disfrutar\!. Puede leer este [pequeño
tutorial](WebScarab_Tutorial "wikilink") que explica la funcionalidad
básica.

WebScarab está diseñado para ser una herramienta que cualquiera que
necesite exponer la funcionalidad de una aplicación basada en HTTP(S),
ya sea para permitir al desarrollador depurar problemas difíciles o
permitir a un especialista en seguridad identificar vulnerabilidades
mientras la aplicacion está siendo diseñada o implementada.

## Archivos

Puede bajar WebScarab desde el [centro de código fuente de OWASP en
Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=61823).
Luego instalelo como sigue:

  - Linux: `java -jar ./webscarab-selfcontained-[numbers].jar`
  - Windows: de doble clic al archivo Jar de instalación

Puede encontrar un paquete de Mac OS X de la ultima version en la
[página de Corsaire](http://research.corsaire.com/tools/).

Puede probar también [la version de Java Web
Start](http://dawes.za.net/rogan/webscarab/WebScarab.jnlp), la cual ha
sido firmada por Rogan Dawes.

## Características

Un marco de trabajo sin ninguna función que no valga la pena, por
supuesto, WebScarab provee un numero de plugins, cuyo objetivo
principal, por el momento, es agregar funcionalidad de seguridad. Estos
plugins incluyen:

  - Fragmentos - extraer los scripts y comentarios de las páginas HTML
    en el momento en que son vistar por el proxy y otros plugins.

<!-- end list -->

  - Proxy - Observa el trafico entre el navegador y el servidor Web. El
    proxy de WebScarab es capaz de observar tanto HTTP como trafico
    HTTPS cifrado al negociar una conexión SSL entre WebScarab y el
    navegador en ves de simplemente conectar el navegador a el sevidor y
    permitir que un flujo de datos cifrado pase por él. Varios plugins
    del proxy has sido tambien desarrollados para permitir al operador
    controlar las peticiones y respuestas que pasan por el proxy.

<!-- end list -->

  - Intercepción Manual - permite al usuario modificar peticiones y
    respuestas HTTP y HTTPS "al vuelo", antes de que ellas alcancen el
    servidor o el navegador.

<!-- end list -->

  - Beanshell - permite la ejecucion de operaciones arbitrarias
    complejas en las peticiones y respuestas. Cualquier cosas que pueda
    ser expresada en Java puede ser ejecutada.

<!-- end list -->

  - Revelar campos ocultos - algunas veces es mas fácil modificar un
    campo oculto en la página misma, mas que interceptar la peticion
    despues que ha sido enviada. Este plugin cambia todos los campos
    ocultos encontrados en las páginas HTML a campos de texto,
    haciéndolos visibles y editables.

<!-- end list -->

  - Simulador de ancho de banda - permite al usuario emular una red mas
    lenta, de manera que observe como se desempeña su sitio con es
    accedido, por ejemplo, desde un modem.

<!-- end list -->

  - Araña (Spider) - identifica nuevas URLs en el sitio objetivo y
    obtiene e contenido cuando se le indica.

<!-- end list -->

  - Peticiones manuales - permite editar y reenviar peticiones
    anteriores o la creación de peticiones nuevas completas.

<!-- end list -->

  - Análisis de identificadores de sesión - recolecta y analiza un
    número de cookies (y eventualmente parametros en el URL tambien)
    para determinar visualmente el grado de aleatoriedad y
    predecibilidad.

<!-- end list -->

  - Scripted - los operadores pueden usar BeanShell para escribir un
    script para create peticiones y obtenerlas del servidor. El script
    puede entonses realizar algunos análisis en las peticiones, con todo
    el poder del modelo de objetos de peticiones y respuestas de
    WebScarab para simplificar las cosas.

<!-- end list -->

  - Ofuscador de parámetros - realiza la sustitución automatizada de
    valores en los parametros que es probable que muestre una validación
    incompleta de parámetros. que lleve a vulnerabilidades como
    Secuencia de comandos en sitios cruzados(XSS) o inyección de SQL.

<!-- end list -->

  - Búsqueda - permite al usuario crear expresiones arbitrarias de
    BeanShell para identificar conversaciones que deben ser mostradas en
    la lista.

<!-- end list -->

  - Comparación - calcula la distacia de edición en el cuerpo de la
    respuesta de la conversación observada y una conversación
    predeterminada. La distacia de edicion es "el número de ediciones
    requeridad para transformar un documento en otro". Por razones de
    desempeño, las ediciones son calculadas usando testigos de palabras,
    mas que byte por byte.

<!-- end list -->

  - SOAP - hay un plucing que interpreta WSDL, y presenta las varias
    funciones y los parámetros requeridas, permitiendo que sean editadas
    antes de que sean enviadas a el servidor.

<!-- end list -->

  - Extensiones - automatiza las revisiones de archivos que fueron
    dejados por error en el directorio raiz del servidor (e.g. .bak, \~,
    etc). Las revisiones son realizadas en archivos y directorios (por
    ejemplo para /app/login.jsp se revisará /app/login.jsp.bak,
    /app/login.jsp\~, /app.zip, /app.tar.gz, etc). Las extensiones para
    archivos y directorios pueden ser editados por el usuario.

<!-- end list -->

  - XSS/CRLF - este plugin de análisis pasivo busca datos controlados
    por el usuario en los encabezados y cuerpo de las respuestas HTTP
    para identificar posibles inyecciones CRLF (partición de respuesta
    HTTP) y vulnerabilidades de secuencia de comandos en sitios cruzados
    (XSS).

## Desarrollo futuro

Features will probably include:

Las características probablemente incluirán:

  - Un plugin de SOAP mejorado, mejorando el soporte para esquemas
    complejos y diferentes codificaciones

<!-- end list -->

  - Combinar los plugins de búsqueda y comparación, de manera que
    podamos comparar solo respuestas específicas.

## Estensibilidad

Dado que es un marco de trabajo, WebScarab es extendible. Cada
característica arriba es implementada como un plugin y puede ser
removido o remplazado. Las nuevas características pueden ser fácilmente
implementados también. El cielo es el límite\! Si tiene una buena idea
para un plugin, por favor déjenos saber sobre ello en la lista.

## Contribuyentes del proyecto

el proyecto WebScarab es administrado por Rogan Dawes. Él puede ser
contactado en rogan AT dawes.za.net

[WebScarab Proyecto](Category:OWASP_Project "wikilink") [Herramienta
OWASP](Category:OWASP_Tool "wikilink") [Archivos
OWASP](Category:OWASP_Download "wikilink")