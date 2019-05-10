**Bienvenido al proyecto WebScarab (Proxima Generación)**

WebScarab-NG (por sus siglas en inglés) es la reescritura completa de la
antigua aplicacion WebScarab, con un enfoque especial en hacer la
aplicacion mas amigable. Para este propósito WebScarab-NG hace uso de la
[plataforma para clientes ricos de
Spring](http://spring-rich-c.sourceforge.net/) para proveer las
características de la interfaz de usuario. Al usar la plataforma para
clientes ricos de Spring, WebScarab-NG obtiene automaticamente algunas
cosas como botónes predeterminados, atajos, soporte para
internacionalización, etc.

Otra característica nueva es que la información de la sesion es escrita
ahora en la base de datos, mas que en cientos de miles de archivos
individuales. Esto hace la utilización del disco duro y cosas como el
archivado de las sesiones mucho mas fácil.

Finalmente, WebScarab-NG tentra todas las funcionalidades importantes
que la versión de WebScarab tiene, aunque estará recorganizada bastante
diferente, para hacer la aplicación mas amigable.

## Nueva interfáz de usuario

Como se menciona arriba, la interfaz de usuario ha cambiado mucho desde
la anterior WebScarab. Ademas de que la nueva imagen (JGoodies) usted
verá que el visor de conversaciones ha cambiado mucho. La anterior vista
"cruda" aun está ahi, pero la versión interpretada ha cambiado
dramáticamente - para bien, espero que usted concuerde conmigo.

La vista interpretada ahora muestra los detalles de la peticion y la
respuesta en forma de árbol, mas que en cajas de texto individuales.
Esto hace que la interfaz luzca mucho mas limpia, y lo mas importante es
que es mas compacta. También hace mucho mas fácil incluir
características como la separación automatica de los parámetros de la
URL y de multiples cookies en sus nodos propios, y donde es mucho mas
fácil ver los parámetros individuales. Tambien mostramos las peticiones
y las respuestas una junto a la otra, mas que una sobre la otra, dado
que mucha gente parece que le gusta mas la vista horizontal que
vertical. La separación de la peticion y la respuesta puede ser ajustada
arrastrandola, tal como puede ser la separación de los encabezados y el
contenido del mensaje.

![Image:WebScarab-NG-default.png](WebScarab-NG-default.png
"Image:WebScarab-NG-default.png")

## Estado actual

En esta estapa, la característica principal del WebScarab-NG es el proxy
de intercepción que permite al operador observar y modificar peticiones
de un navegador a otro cliente que pasen por el proxy. Una
característica nueva es la barra de control del proxy, la cual es
implementada como una barra de herramientas "siempre encima" que flota
sobre su navegador o otro cliente y permite abilitar or deshabilitar la
intersepción fácilmente. Tambien permite anotar o describir las
peticiones conforme pasan por el proxy. Si escribe altun texto en el
campo de anotación, ese texto será ligado a la proxima conversación que
pase por el proxy, y puede ser visto despues como parte de el histórico
de las conversaciones. Esto puede ser muy útil para rastrear lo que esta
haciendo en un procedimiento de multiples pasos.

Por ejemplo: seleccionar un elemento del menú, escribir un valor, enviar
el valor, etc. Frecuentemente los sitios se contruyen de manera que
pueden resultar en docenas de conversaciones resultantes de una acción
sencilla. Hacer anotaciones en una conversación que inicia el resto de
las demás hace muy fácil identificarlas en estapas posteriores.

![Image:WebScarab-NG-proxy-control-bar.png](WebScarab-NG-proxy-control-bar.png
"Image:WebScarab-NG-proxy-control-bar.png")

## Retroalimentación sobre errores

Una de las mejores características que provee la plataforma de clientes
ricos Spring es la abilidad para verificar que las entradas hagan
sentido y proveer retroalimentación "conforme telcea" a el usuario.

Por ejemplo, vea la ventana de "Intercepción de Request":

![Image:WebScarab-NG-intercept-request-error.png](WebScarab-NG-intercept-request-error.png
"Image:WebScarab-NG-intercept-request-error.png")

Podemos ver que el usuario trata de cambiar el método de "POST" a
"PROST". WebScarab-NG no tiene idea de como ejecutar un método "PROST"
asi que procee un mensaje de error para informar al usuario.
Adicionalmente el boton de OK es deshabilitado automaticamente, hasta
que el error es corregido.

## Como obtener WebScarab-NG

WebScarab.NG es distribuido via Java WebStart y puede ser obtenido de
[aqui](http://dawes.za.net/rogan/webscarab-ng/webstart/WebScarab-ng.jnlp).

Un beneficio importante de usar Java WebStart es que los usuarios
recibirán automaticamente nuevas versiones de WebScarab-NG conforme
estas estén disponibles, dado que WebStart verifica si hay nuevas
versiones disponibles cada véz que corre. Por supuesto, si se intenta
correr sin acceso a internet, aun asi correrá.

`Nota: Hay un problema con la firma de la aplicación y Java WebStart si esta usando Java 1.6.`
`Estamos investigando la solución. Por lo pronto, puede usar WebScarab-NG con una versión `
`anterior de JAva (Sin echar a perder su sistema).`
` `
` "set PATH="c:\Program Files\Java\jdk1.5.0_06\bin" o lo que sea`
` "javaws `<http://dawes.za.net/rogan/webscarab-ng/webstart/WebScarab-ng.jnlp>

Dependiendo de la demanda una ves que WebScarab NG madure tambien se
ofrecerá una version fuera de línea.

Para información sobre los cambios que hemos hecho, por favor vea [el
repositorio
GIT](http://dawes.za.net/gitweb.cgi?p=rogan/webscarab-ng/webscarab-ng.git;a=summary)

Si quiere obtener una copia de el código fuente, puede bajar un
"snapshot" de el visor de repositorio gitweb. Alternativamente, si
quiere verificar el repositorio usando git, puede usar el siguiente
comando:

` $ git clone `<http://dawes.za.net/rogan/webscarab-ng/webscarab-ng.git/>

Puede obtener cualquier cambio subsecuente usando:

` $ git fetch origin`

## Información técnica

Información técnica para aquellos interesados en involucrarse puede ser
encontrada [aqui](OWASP_WebScarab_NG_Project_Technical_Info "wikilink").

Esta página lista las [diferencia entre WebScarab Clásico y WebScarab
NG](OWASP_WebScarab_Differences_%28Classic_vs_NG%29 "wikilink"),
incluyendo una lista de acciones a realizar en WebScarab NG.

## Retroalimentación

Si tiene algun comentario o sugerencia para WebScarab-NG, por favor
siéntase libre de enviarlas a la [lista de sitribución de OWASP
WebScarab](http://lists.owasp.org/mailman/listinfo/owasp-webscarab).

Si retroalimentación es muy apreciada y será considerada cuidadosamente
para versiones posteriores de WebScarab-NG-

## Controbuyentes del proyecto

El proyecto de WebScarab-NG es administrado por Rogan Dawes de Aspect
Security. El puede ser contactado en rogan AT dawes.za.net

[Categoría:Archivo OWASP](Category:OWASP_Download "wikilink")
[Categoría:Proyecto OWASP WebScarab
NG](Category:OWASP_WebScarab_NG_Project "wikilink")