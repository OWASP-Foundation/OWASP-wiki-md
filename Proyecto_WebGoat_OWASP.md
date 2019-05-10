<webgoat/>

![WebGoat-Phishing-XSS-Lesson.JPG](WebGoat-Phishing-XSS-Lesson.JPG
"WebGoat-Phishing-XSS-Lesson.JPG")![WebGoat-Bypass-Access-Control-Lesson.JPG](WebGoat-Bypass-Access-Control-Lesson.JPG
"WebGoat-Bypass-Access-Control-Lesson.JPG")

**WebGoat** es una aplicación web J2EE deliberadamente insegura,
mantenida por [OWASP](http://www.owasp.org) y diseñada para enseñar
lecciones de seguridad en aplicaciones Web. En cada lección, los
usuarios deben demostrar su entendimiento de los problemas de seguridad
al explotar la vulnerabilidad real en al aplicación WebGoat. Por
ejemplo, en una de las lecciones el usuario debe usar [SQL
injection](SQL_injection "wikilink") para robar números de tarjeta de
crédito ficticios. La aplicacion es un ambiente realista de enseñanza,
que provee a los usuarios con pistas y código para explicar mejor la
lección.

Porque el nombre "WebGoat"(Chivo Web en español)? Los desarrolladores no
deben sentirse mal sobre no conocer de seguridad. Encluso los mejores
programadores cometen errores de seguridad. Lo que necesitan es un
"chivo expiatorio", correcto? ¡*Solo culpa a el 'chivo*\!

**Para iniciar, lea la [Guia de uso e instalación de
WebGoat](WebGoat_User_and_Install_Guide_Table_of_Contents "wikilink")**

## Metas

La seguridad en aplicaciones web es difícil de aprender y practicar. No
mucha gente tiene applicaciones Web completas como tiendas electrónicas
de libros o bancos en línea que pueden ser usados para buscar
vulnerabilidades. Además, los profesionales de seguridad frecuentemente
necesitan probar herramientas contra una plataforma conocida por ser
vulnerable para asegurarse que se desempeñan segun se anuncian. Todo
esto necesita debe ocurrir en un ambiente seguro y legal. Incluso si sus
intenciones son buenas, creemos que no debe intentar buscar
vulnerabilidades sin permiso.

La meta principal del proyecto WebGoat es simple: *Crear un ambiente
interactivo de enseñanza para seguridad en aplicaciones web*. En el
futuro, el equipo del proyecto espera extender WebGoat para convertirse
en una plataforma para "benchmarking" de seguridad y un "Honeypot" para
sitios web badado en Java.

Dele un vistazo a el [plan de
trabajo](OWASP_WebGoat_Project_Roadmap "wikilink") del proyecto y
encuentre algunas tareas que le pueden ayudar de inmediato.

## Introducción

![WebGoat-Session-Hijack-Lesson.JPG](WebGoat-Session-Hijack-Lesson.JPG
"WebGoat-Session-Hijack-Lesson.JPG") WebGoat esta escrito en Java y por
lo tanto se instala en cualquier plataforma con una máquina virtual de
Java. Hay programas de instalación para Linux, OS X Tiger y Windows. Una
vez instalado, el usuario puede revisar las lecciones y rastrear su
progreso con el tablero electrónico. Actualmente hay mas de 30
lecciones, incluyendo las que lidian con los siguientes problemas:

<table>
<tbody>
<tr class="odd">
<td><p>valign="top"</p></td>
<td><ul>
<li><a href="Cross_Site_Scripting" title="wikilink">Secuencia de Comandos en Sitios Cruzados (Cross Site Scripting)</a></li>
<li>Control de acceso</li>
<li><a href="Race_conditions" title="wikilink">Seguridad de Hilos</a></li>
<li><a href="Unvalidated_Input" title="wikilink">Manipulación de campos ocultos</a></li>
<li>Manipulación de parámetros</li>
<li><a href="Session_Management#Weak_Session_Cryptographic_Algorithms" title="wikilink">Testigos de sesión inseguros</a></li>
<li><a href="SQL_injection" title="wikilink">Inyección SQL</a></li>
</ul></td>
<td><p>valign="top"</p></td>
<td><ul>
<li>Inyección de SQL con números</li>
<li>Inyección de SQL con cadenas de caracteres</li>
<li><a href="Web_Services1Servicios_Web" title="wikilink">Web Services1Servicios Web</a></li>
<li><a href="Improper_Error_Handling" title="wikilink">Autentificación fallida</a></li>
<li>Los peligros de los comentarios HTML</li>
<li>... y muchos mas!</li>
</ul></td>
</tr>
</tbody>
</table>

Para más detalles, vea por favor la [Guía de uso e instalación de
WebGoat](WebGoat_User_and_Install_Guide_Table_of_Contents "wikilink").

## Soluciones en Video

El grupo de hackeo ético YGN ha creado una serie de videos que uestran
las soluciones posibles a las lecciones de WebGoat. Estos videos de
entrenamiento están disponibles en
<http://yehg.net/lab/pr0js/training/webgoat.php>

## Versiones

Puede sincronizarse con la version actual del código fuente de WebGoat
en [Google code](http://code.google.com/p/webgoat/)(En inglés).

Las distribuciones de Webgoat estan disponibles en los [Google code
downloads](http://code.google.com/p/webgoat/downloads/list)(En inglés).

Puede bajar versiones anteriores de WebGoat desde el [Centro de Código
fuente de OWASP en
Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=61824).
Hay versiones con y sin Java, y la instalación solo require descomprimir
el archivo y correr el script de inicio. Para su conveniencia, un
archivo WAR listo para usar esta disponible tambien para soltarlo
diretamente en su servidor de aplicación J2EE.

### WebGoat 5.2 estandar:

La instalación standard es procedimiento de bajar, descompriimr y dar
clic. Viene con el "Java Runtime Environment" y un servidor Tomcat 5.5
ya configurado.

`   * De click doble en webgoat.bat - una ventan de comandos de Tomcat se inicia`
`   * Navegue a `<http://localhost/WebGoat/attack>
`   `

### Desarrollador WebGoat 5.2 (En [SourceForge](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=61824)):

**Notece:** Esta versión pretende proveer un ambiente para trabajar en
los laboratorios WebGoat. Si le gustaría desarrollar lecciones,
sincronizese con la version base en Google code.

La versión para desarrolador incluye la versión estándar ademas de un
ambiente de eclipse preconfigurado. La versión de desarrollador tambien
es es procedimiento de bajar, descompriimr y dar click. Trabaja
exactamente de la misma manera que la versión estándar por si quiere
explorar las lecciones. Sin embargo, si quiere realizar laboratorios o
usar WebGoat en un salón de clase, use el eclipse.bat para iniciar el
ambiente preconfigurado de WebGoat. Las instrucciones detalladas están
incluidas en el archivo _HOW TO create the WebGoat workspace.txt_(En
inglés)

`   * Extraiga el archivo Eclipse-Workspace.zip en el directorio de trabajo`
`   * De doble click en el archivo eclipse.bat`
`   * En el Explorador de paquetes de Eclipse (arriba a la derecha), de click derecho en el proyecto de Webgoat y refresque`
`   * En el Explorador de paquetes de Eclipse (arriba a la derecha), de click derecho en el proyecto de Servidores y refresque`
`   * En la vista de servidores (abajo), de click derecho en el servidor LocalHost y luego en Inicio`
`   * Navegue a `<http://localhost/WebGoat/attack>
`   * Cualquier cambio hecho a el código se compilarán y publicaran automaticamente cuando se guarden los cambios`
`   `

Por favor mande sus comentarios relacionados a esta version a Bruce
Mayhew en **webgoat AT owasp.org**

## Desarrollo futuro

WebGoat 5.2 - Is now available via svn at google code

WebGoat 5.3 - Estimated release date: TBD

Si le gustaría convertirse en un miembro de el codigo fuente del
proyecto WebGoat publicado en [Google
Code](http://code.google.com/p/webgoat/) contacte a Bruce Mayhew en
**webgoat AT owasp.org**.

**Nuevas características en 5.2**

  - Presentación e instrucciones de WebGoat
  - Lección multinivel de conexión
  - Lección de fijado de sesiones
  - Lección de acceso inseguro
  - Videos de solución a lecciones
  - Capacidad para reportar problemas
  - Muchas mejoras y arreglos menores

## Contribuyentes al Proyecto

El proyecto de Webgoat es administrado por Bruce Mayhew. El puede ser
contactado en **webgoat AT owasp.org**. Las versiones de WebGoat son
mantenidas en
[SourceForge](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=61824)
y [Google](http://code.google.com/p/webgoat/downloads/list). El marco de
trabajo de WebGoat lo hace estremandamente sencillo para agregar
lecciones. Estamos pidiendo activamente a los desarrolladores que
agregen lecciones conforme emergen nuevas tecnologias. Si esta
interesado en ser volunratio para el proyecto, o tiene un comentario,
pregunta o sugerencia, por favor únase a la [lista de
distribución](http://lists.owasp.org/mailman/listinfo/owasp-webgoat) de
WebGoat.

Gracias a [Ounce Labs](http://www.ouncelabs.com) por darme el tiempo
para trabajar y dirigir rl proyecto WebGoat durante my trabajo diario\!.

## Patrocinadores del proyecto

El proyecto es patrocinado por
[<https://www.owasp.org/images/3/30/100px-Aspect_Security_Logo.jpg>](http://www.aspectsecurity.com)

__NOTOC__

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP Download](Category:OWASP_Download "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink")