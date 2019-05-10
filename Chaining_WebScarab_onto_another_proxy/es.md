Este documento pretende explicar como configurar WebScarab para
encadenarlo en un proxy de salida.

Asumo que está familiarizado con la funcionalidad básica de WebScarab, y
ha logrado usarlo como un proxy para ver o interceptar algunas
conversaciones. Si no, le sugiero que lea el documento de
["Iniciado"](WebScarab_Getting_Started "wikilink").

**[Stephen Venter](User:Stephen_Venter "wikilink")** 07:37, 16 March
2007 (EDT)

## Introducción

En caso de que esté navegando con un servidor proxy en su red local, el
cual es un caso común en redes comrporativas, necesitará configurar
WebScarab para encadenarlo en ese servidor proxy si es que va a trabajar
correctamente.

Algunas personas se refieren a esto como "Usar WebScarab detras de un
cortafuegos", dado que es el cortafuegos el que estará bloqueando el
trafico externo, que no sea tráfico que se origina por el servidor
proxy. Pero en realidad es un servidor proxy la clave para hacer que
WebScarab trabaje en estas circunstancias.

## Esquema para configurar este ejemplo

Para hacer esto es necesita obviamente conocer que la dirección IP del
servidor proxy (o su nombre de servidor que se resuelve en su LAN) junto
con el número de puerto que el servidor proxy escucha. Para cuestion de
simplicidad, vamos a asumir que tengo una red local con un rango de red
192.168.1.0 /24 (el cual significa que tiene una máscara de
255.255.255.0) y el servidor proxy esta en la dirección 192.168.1.10 y
escucha en el puerto 8080.

Si no está seguro cual es la direccion IP del servidor proxy y alguien
mas configura su servidor de manera que está navegando correctamente con
el proxy, puede ser capaz de verlo en su configuración de navegador
(donde ha sido manualmente configurado y no esta siendo seleccionado
automaticamente por el navegador - hay otras maneras de resolverlo en
ese caso, pero no las mencionaré aqui)

Dado que estoy usando Microsoft Internet Explorer en este ejemplo, puedo
ver mis propiedades de proxy aqui: Herramientas -\> Opciones de Internet
-\> Configuración LAN -\> Usar un servidor proxy en su LAN -\>
Dirección: 192.168.1.10 Port: 8080

Estoy corriendo WebScarab localmente en mi PC, usando las propiedades
estandar. Por lo tanto estará escuchando en la direccion estandar web
127.0.0.1 en el puerto 8008. Algunas personas les gusta usar el nombre
"localhost", yo prefiero usar la dirección IP "127.0.0.1" - pero ambos
son lo mismo, asi que no importará cual use.

## Paso Uno: Configurando WebScarab para apunta a el proxy de mi red interna

Nota: El número del puerto estandar es el valor "3128" incluido en la
configuración de WebScarab para encadenarlo con otro servidor proxy
(Herramientas -\> Proxies). No significa necesariamente que es el numero
de puerto correcto que debe usar en su red. En mi ejemplo, el proxy de
mi red local esta configurado para escuchar en el puerto "8080". Asi que
es el valr que tengo que usar en WebScarab en: Herramientas -\> Proxies
-\> \[la caja de "Puerto" para ambos el proxy HTTP y HTTPS\]

Una ves que he configurado esto correctamente, WebScarab puede hacer
conexiones fuera de nuestra red a travez de el proxy de la red local.

**ADVERTENCIA\!\!** asegurese que el proxy que especificó via
Herramientas -\> Proxies no apunte de regreso a el puerto de el proxy
WebScarab, de otra manera terminaremos creando un ciclo infinito, dado
que WebScarab intentará de usarse a si mismo como el proxy de salida y
simplemente se quedará sin sockets libres o memoria disponible.

**Nota:** Si esta usando WebScarab en Windows e Internet Explorer esta
accediendo correctamente a la red externa a travez de el proxy
designado, usted puede simplemente ser capaz de acceder a proxy de
salida de WebScarab a travez de Tools -\> Proxies, y dar clic en el
botón de "Get IE Settings". Esto solo funciona desde la version
"instalador" de WebScarab, no la version "auto-contenida" o Java
WebStart. Dado que esta funcionalidad confía en llamadas a una librería
nativa de windows para leer esta información.

## Paso dos: configurando mi navegador para enviar conexiones via WebScarab

Este paso es el usual para hacer que WebScarab funcione ya sea
encadenado a otro proxy interno o no.

El número "3128" no es el número correcto a usar con IE. Tambien, la
dirección IP del proxy en la red interna no es lo que quiero usar aqui
(a menos que me este conectando a el internet directemanete sin
webscarab en el medio).

Como se menciona arriba estoy corriendo WebScarab localmente en la misma
PC en la que estoy navegando. Asi que en IE necesito poner el valor
"127.0.0.1" en el campo "Dirección" y "8008" en el campo "Puerto" como
sigue: Herramientas -\> Opciones de Internet -\> Conexiones -\>
Configuración LAN -\> Usar un servidor Proxy en su LAN -\>
Dirección:127.0.0.1 Puerto:8008

También, le sugiero que deje el campo "Detectar automaticamente las
pripiedades" limpio. Y lo mismo aplica para el de "Evitar el sevidor
proxy para direcciones locales". Si pretende usar WebScarab solo cuando
hace conexiones a sitios fuera de su red local, no importa. Pero si
intenta conectarse a un sitio Web en su red Local, esa configuración
resultará en IE conectandose directamente a el servidor web local sin
pasar por WebScarab. Asi que por seguridad, le suegiero mantener este
campo limpio tambien.

Ahora tengo:

  - A mi navegador reenviando conexiones via WebScarab, el cual esta
    escuchando en 127.0.0.1:8008
  - y a WebScarab reenviado conexiones fuera de mi red local via el
    proxy de red en la dirección 192.168.1.10 y el puerto número 8080
    (tambien conocido como hacer que WebScarab se encadene a otro proxy
    192.168.1.10:8080).

[Categoría:Proyecto OWASP
WebScarab](Category:OWASP_WebScarab_Project "wikilink")