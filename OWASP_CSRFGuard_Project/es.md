## Descripción general

Justo cuando los desarrolladores están empezando a correr en círculos
alrededor de [Cross Site Scripting](Cross_Site_Scripting "wikilink"), el
['gigante
dormido'](http://www.darkreading.com/document.asp?doc_id=107651&WT.svl=news1_2)
despierta por una catástrofe web mas. [Cross-Site Request
Forgery](Cross-Site_Request_Forgery "wikilink") (CSRF) es un ataque
donde la victima es engañada para cargar información desde o enviar
información hacia una aplicación web en la que esta actualmente
autenticada. El problema es que la aplicación web no tiene medios para
verificar la integridad de la petición. El proyecto OWASP CSRFGuard
trata de resolver este problema a través del uso de un token de petición
único.

[Click aquí](http://www.owasp.org/index.php/How_CSRFGuard_Works) para
mas información acerca del diseño e implementación de CSRFGuard.

## Licencia

CSRFGuard es ofrecido bajo
[LGPL](http://www.gnu.org/copyleft/lesser.html). Para mayor información
sobre las licencias de OWASP, favor de consultar la pagina de licencias
de OWASP: [OWASP Licenses](OWASP_Licenses "wikilink") (en ingles).

## Descargas

### Versión 1

[Click aquí](http://www.owasp.org/index.php/Image:CSRF_Guard.zip) para
descargar la ultima versión de la serie OWASP CSRFGuard 1.x.

### Versión 2

[Click
aquí](http://www.owasp.org/index.php/Image:OWASP-CSRFGuard-2.0.jar)
para descargar la ultima versión binaria de OWASP CSRFGuard 2.0.

[Click
aquí](http://www.owasp.org/index.php/Image:OWASP_CSRFGuard-2.0-src.zip)
para descargar la ultima versión de OWASP CSRFGuard 2.0 fuente, binarios
y archivos muestra de configuración **(Recomendado)**.

[Click
aquí](http://www.owasp.org/images/c/c9/CSRF_DangerDetectionDefenses.ppt)
para descargar la presentación del autor en la conferencia OWASP 2007 en
San José acerca de los peligros de CSRF y una breve descripción de CSRF
Guard y CSRF Tester.

## Instrucciones de instalación

[Click aquí](http://www.owasp.org/index.php/CSRFGuard_1.x_Installation)
para ver las instrucciones de instalación de la serie OWASP CSRFGuard
1.0.

[Click aquí](http://www.owasp.org/index.php/CSRFGuard_2.0_Installation)
para ver las instrucciones de instalación de la serie OWASP CSRFGuard
2.0.

## Plan de trabajo

[Click aquí](https://www.owasp.org/index.php/CSRF_Guard_2.2_Roadmap)
para ver el plan de trabajo (roadmap) para la ultima versión de
desarrollo de CSRFGuard. Siéntase libre de agregar sus propios
requerimientos de cambios o enviarme parches/retos.

## CSRF Testing Tool

Vea la herramienta [OWASP CSRF
Tester](http://www.owasp.org/index.php/Category:OWASP_CSRFTester_Project)
la cual le permite probar vulnerabilidades de CSRF. Esta herramienta
también esta escrita en Java.

## Comentarios y participación

Esperamos que encuentre útil a CSRFGuard. Por favor contribuya con el
proyecto enviando sus comentarios, preguntas y sugerencias a OWASP.
Gracias\!

## Proyectos Similares

Hay un pequeño numero de otros proyectos que implementan el concepto de
token de petición único similar al de CSRFGuard. Son los siguientes:

:\*<http://www.owasp.org/index.php/PHP_CSRF_Guard>

:\*<http://www.thespanner.co.uk/2007/10/19/jsck/>

:\*<http://www.owasp.org/index.php/.Net_CSRF_Guard>

## Donaciones

OWASP es puramente una comunidad open source impulsada por el esfuerzo.
Como tal, todos los proyectos y esfuerzos de investigación son
contribuidos y mantenidos con un “tiempo libre” individual. Si encuentra
útil este o algún otro proyecto, por favor apoye a OWASP con una
[donación](https://www.owasp.org/index.php/Contributions).

## Patrocinadores del proyecto

El proyecto OWASP CSRFGuard es dirigido por Eric Sheridan (eric dot
sheridan at owasp dot org) y patrocinado por
[<https://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com).

[Category:OWASP_Validation_Project](Category:OWASP_Validation_Project "wikilink")
[CSRFGuard Project/es](Category:OWASP_Project "wikilink")
[Category:Java](Category:Java "wikilink")