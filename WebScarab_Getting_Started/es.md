*WebScarab*' tiene una gran cantidad de funcionalidad y como tal puede
ser bastante intimidante para los usuarios nuevos. Pero para el caso mas
simple, que es interceptar y modificar peticiones y respuestas entre un
navegador y un servidor HTTP/S no hay mucho que necesite ser aprendido.

Inicialmente, asumire que tiene acceso complete e irrestricto a Internet
(Esto es, que no esta tras un proxy). Para efectos de simplicidad,
tambien asumiré que esta usando Internet Explorer. Si necesita usar un
proxy para salir de su red corporativa, vea [encadenar otro proxy a
WebScarab](Chaining_WebScarab_onto_another_proxy "wikilink")

![Image:WebScarab_startup.png](WebScarab_startup.png
"Image:WebScarab_startup.png")

Asi es como luce WebScarab al iniciar. Hay algunas pocas areas
importantes que pueden necesitar explicación.

Primero, la barra de herramientas provee acceso a varios plugins asi
como a la ventana de resumen (vista principal) y la ventana de mensajes
(registro de eventos).

La ventana de resumen esta dividida en 2 partes. Arriba esta la tabla
estilo árbol, la cual muestra la distribución de los sitios que ha
visitado y algunos atributos de varios URL. Abajo está la tabla que
muestra todas las conversaciones que han sido vistas en WebScarab,
normalmente organizadas al descendentemente por su identificador, de
manera que las conversaciones mas recientes aparecen arriba en la tabla.
El orden puede ser cambiado dando clic en el encabezado de la columna
deseada.

Al iniciar a usar WebScarab como un proxy, necesita configurar su
navegador para usar ebScarab como un proxy. Esto es configurado en IE
usando el menú de herramientas. Seleccione Herramientas -\> Opciones de
Internet -\> Configuracion LAN para abrir la ventana de configuración de
proxy.

![Image:IE Proxy.PNG](IE_Proxy.PNG "Image:IE Proxy.PNG")

El puerto predeterminado de WebScarab es 8008 en locahost para su proxy.
Necesita configurar IE para enviar las peticiones a WebScarab, mas que
las obtenga por si mismo, como se muestra en la imagen de arriba.
Asegurece de que todas las cajas de verificación estan limpias (no
marcadas), excepto la de "Usar un servidor Proxy". Una ves que haya
configurado IE para usar un proxy, seleccione Aceptar en todas las
ventanas de dialogo para regresar a su navegador. Navere a un sitio que
no sea SSL y cambie a WebScarab.

Debe de ver algo similar a la siguiente imagen. Si no lo ve o si obtiene
un error al navegar, debe regresar y revisar su configuración de Proxy
en Internet Explorer como se describe arriba. So la configuración de
proxy está correcta, es posible que hay otro programa que ya este usando
el puerto 8008 y evita que WebScarab lo use. Si es asi, debe detener el
otro programa. Tambien le mostraré como debe decirle a WebScarab que use
un puerto diferente un poco despues.

**NOTA:** Si esta usando WebScarab para probar un sitio que está
corriendo en la misma computadora que el navegador (por ejemplo
localhost o 127.0.0.1) y está usando IE7 va a tener que agregar un punto
despues del nombre del servidor para forzar a IE a usar el proxy que ha
configurado. Este NO ES una falla de WebScarab, sino una desafortunada
desicion de diseño (me imagino) hecha por los desarrolladores de IE.
Basicamente, ignorará cualquier configuración de proxy si cree que el
sevidor que esta tratando de alcanzar está en la computadora local. Una
manera de engañar el navegador es agregar el punto como en
<http://localhost./WebGoat/attack>. Esto forzará a IR a usar el proxy
configurado.

![Image:WebScarab after browsing.png](WebScarab_after_browsing.png
"Image:WebScarab after browsing.png")

Aqui puede ver el árbol de URLs, el cua representa la distribución del
sitio asi como las conversaciones individuales que se han pasado a
travez de WebScarab. Para ver los detalles de la conversación en
particular, puede dar doble clic en un renglón de la tabla y una ventana
mostrará la peticion y los detalles de la respuesta. Puede ver la
peticion y la respuesta en una variedad de formas. La vista mostrada
aqui es la vista "interpretada" donde los encabezados estan distribuidos
en una tabla y el contenido de la petición y la respuesta es presentada
de acuerdo a el encabezado de Content-Type. Tambien puede escoger el
formato "crudo" donde la petición y la respuesta se muestran tal cual se
verían en la red.

![Image:WebScarab conversation.png](WebScarab_conversation.png
"Image:WebScarab conversation.png")

Puede ir caminando de una conversación (petición/respuesta) a la
siguiente en la ventana de conversación usando los botones de "Previous"
y "Next", asi como yendo directamente a una conversación en particular
usando el campo desplegable.

Ahora que esta familiarizado con el funcionamiento interno de WebScarab,
y se ha asegurado que el navegador esta configurado correctamente, el
siguiente paso es interceptar algunas peticiones y modificarla antes de
que sean enviadas al servidor.

Usted puede abilitar la intercepción del proxy por medio del plugin de
proxy, el cual esta accesible por medio del boton de "proxy" en la barra
de herramientas, entonses eliga la pestaña de "Manual Edit". Una ves que
de clic en la casilla "Intecept Request", puede elegir los métodos de
petición que desea interceptar (comumente serán GET y POST) puede
incluso seleccionar múltiples metodos usando "Control + clic".
Seleccione "GET" por el momento.

![Image:Webscarab configure
intercept.png](Webscarab_configure_intercept.png
"Image:Webscarab configure intercept.png")

Ahora regrese a su navegador, y de clic en una liga. Debe ver algo como
la siguiente ventana (puede ser que solo parpadee en la barra de tareas
inicialmente,solo seleccionela. Ventanas futuras apareceran
aproiadamente)

![Image:WebScarab intercept request.png](WebScarab_intercept_request.png
"Image:WebScarab intercept request.png")

Ahora puede editar cualquier parte que elija de la peticion. Note que
los encabezados ya estan decodificados y cualquiera cosa que escriba va
a ser codificado automaticamente. Si no quiere que esto pase, debe de
usar el modo "crudo" (Raw). En algunos casos, usando el modo crudo puede
ser la manera mas fácil, especialmente si tiene algo que desee pegar.

Una ves que este contento con los cambios, de click en el botón de
**"Accept changes"** para permitir que la petición modificada sea
enviada al servidor. Si decide que le gustaría revertir los cambios que
ha hecho, puede dar click en el botón de **"Cancel changes"** para que
la petición original sea enviada al servidor. Puede tambien dar clic en
el botón de **"Abort request"** si no quiere enviar la peticion a el
servidor. Esto va a enviar un error en el navegador. Finalmente, si hay
multiples ventanas de intersepción abiertas (por ejemplo el navegador
esta usando varios hilos simultaneamente) puede liberar todas las
peticiones usando el botón de **"Cancel ALL intercepts"**.

WebScarab continuarpa interceptando todas las peticiones que encajan con
el método que especificó hasta que limpie la casilla "Intercept
requests", ya sea en la ventana de **intercept conversation** o en la
pestaña de **"Manual Edit"** en el plugin de **Proxy** . Pero puede ser
que se pregunte porque WebScarab no intercepta las peticiones de
imagenes, hojas de estilo, Javascript, etc. Si regresa a la pestaña de
**"Manual Edit"** verá el campo etiquetado como "Exclude paths
matching:". Este campo contiene una expresión regular la cual concuerda
con el URL de la petición. Si concuerda la petición no es interceptada
nunca.

Puede configurara WebScarab tambien para interceptar respuestas, en caso
de que quiera cambia el comportamiente de algunas partes de la página,
por eejmplo, puede deshabilitar la validación de Javascript, cambiar la
lista de posibles elementos en un campo **SELECT**, etc.

## Tips y trucos

Si esta usando IE y le gustaría que Webscarab actualize automáticamente
su configuración de proxy, necesitará completar las siguientes pasos.
**Nota:** esto solo trabaja con la version de instalador de Webscarab\!

  - Cambie la interfaz completa (Tools -\> Use Full-featured Interface),
    luego vaya a la pestaña de Proxy-\>Listeners.
  - Seleccione el único puerto de escucha mostrado y de clic en "Stop".
  - Mas o menos a 2/3 abajo en la ventana hay varios campos, que
    corresponden a las columnas en la tabla de el "listener".
  - Cada caja debe ser llenada con un valor de el el proxy detenido mas
    recientemente.
  - A este punto, puede seleccionar la casilla "Primary" y entonses dar
    clic en "Start".

Si configuración de proxy para IE automaticamente es actualizada para
apuntar a WebScarab y se reconfigurará cuando salga de WebScarab. Esta
configuración será almacenada y usada en corridas posteriores de
Webscarab.

[Categoría:Como Hacer](Category:How_To "wikilink") [Categoría:Proyecto
OWASP WebScarab](Category:OWASP_WebScarab_Project "wikilink")