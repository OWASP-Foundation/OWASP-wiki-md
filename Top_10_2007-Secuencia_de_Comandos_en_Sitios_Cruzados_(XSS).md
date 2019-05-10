La secuencia de comandos en sitios cruzados, más conocida como XSS, es
en realidad un subconjunto de inyección HTML. XSS es la más
prevaleciente y perniciosa problemática de seguridad en aplicaciones
Web. Las fallas de XSS ocurren cuando una aplicación toma información
originada por un usuario y la envía a un navegador Web sin primero
validarla o codificando el contenido.

XSS permite a los atacantes ejecutar secuencias de comandos en el
navegador Web de la víctima, quienes pueden secuestrar sesiones de
usuario, modificar sitios Web, insertar contenido hostil, realizar
ataques de phising, y tomar control del navegador Web del usuario
utilizando secuencias de comando maliciosas. Generalmente JavaScript es
utilizado, pero cualquier lenguaje de secuencia de comandos soportado
por el navegador de la victima es un potencial objetivo para este
ataque.

## Entornos Afectados

Todas las plataformas de aplicación Web son vulnerables a este tipo de
ataque.

## Vulnerabilidad

Existen tres tipos conocidos de secuencias de comandos en sitios
cruzados: ''reflejado, almacenado e inyección DOM. ''XSS *reflejado* es
el más fácil para explotar – una página reflejara información
suministrada por el usuario directamente de vuelta al usuario:

`echo $_REQUEST['userinput'];`

XSS *almacenado* toma información hostil, la almacena en un fichero, una
base de datos, u otro sistema de almacenamiento, y luego en una etapa
posterior, muestra dicha información sin filtrado alguno. Esto es
extremadamente peligroso en sistemas de administración de contenidos
(CMS), blogs, o foros, donde un gran número de usuarios accederá a la
información introducida por otros usuarios.

Con ataques basados en *inyección DOM*, el código JavaScript del sitio
Web y sus variables son manipuladas, en lugar de los elementos HTML.

Alternativamente, los ataques pueden ser una mezcla o un híbrido de los
tres tipos mencionados anteriormente. El peligro con la secuencia de
comandos en sitios cruzados no es el tipo de ataque, sino la posibilidad
del mismo. Un comportamiento fuera del estándar o inesperado del
navegador Web puede introducir sutiles vectores de ataque.

Los ataques son implementados generalmente en JavaScript, que es un
poderoso lenguaje de secuencia de comandos. Utilizar JavaScript permite
a los atacantes manipular cualquier aspecto de la pagina mostrada,
incluyendo agregar nuevos elementos (tales como una pantalla de conexión
falsa que envía nuestras credenciales a un sitio hostil), manipular
cualquier aspecto del árbol interno DOM, y borrar o cambiar la manera en
la cual una pagina es visualizada. JavaScript permite la utilización de
XmlHttpRequest, el cual es utilizado en sitios con tecnologías AJAX,
incluso si el sitio de la victima no utiliza AJAX actualmente.

Algunas veces es posible evadir la política que indica al navegador Web
enviar la información a su origen utilizando XmlHttpRequest – y por lo
tanto reenviar la información de la victima a sitios hostiles, y crear
complejos gusanos y zombis maliciosos que se mantendrán activos mientras
el navegador Web se encuentre abierto. Los ataques AJAX no tienen por
qué ser visibles o requerir la interacción del usuario para realizar
peligrosos ataques CSRF (falsificación de petición en sitios cruzados).
Para mayor información sobre este tipo de ataques por favor diríjase al
apartado A-5.

## Verificando la seguridad

El objetivo es verificar que todos los parámetros en la aplicación sean
validados y/o codificados antes de ser incluidos en paginas HTML.

**Verificación automatizada:** herramientas automáticas de testeo de
penetración son capaces de detectar XSS *reflejado* a través de
inyección de parámetros, pero generalmente fallan a la hora de
encontrar XSS persistente, particularmente si la salida del vector XSS
inyectado es restringida a través de pruebas de autorización (tales como
si un usuario introduce información hostil que puede ser visualizada
solamente por los administradores de la aplicación). Herramientas
automáticas de escaneo de código fuente pueden encontrar APIs débiles o
peligrosas pero normalmente no pueden determinar si la validación o
codificación se ha realizado, lo cual puede resultar en falsos
positivos. Ninguna herramienta es capaz de encontrar XSS basado en DOM,
lo cual significa que las aplicaciones basadas en Ajax frecuentemente se
encontrarán en riesgo si sólo se ha realizado una verificación
automatizada.

**Verificación manual:** si se ha utilizado un mecanismo centralizado de
validación y codificación, la manera más eficiente de controlar la
seguridad es revisando el código. Si en cambio, se ha utilizado una
implementación distribuida, entonces la verificación tomará
considerablemente mucho más tiempo. El testeo toma mucho tiempo ya que
la superficie de ataque en la mayoría de las aplicaciones es muy amplia.

## Protección

La mejor protección para XSS es una combinación de validación de listas
blancas (“whitelists”) de toda la información entrante y una apropiada
codificación de la información saliente. La validación permite la
detección de ataques, y la codificación previene cualquier inyección de
secuencia de comandos de ejecutarse exitosamente en el navegador.

Prevenir XSS en una aplicación entera requiere una solución de
arquitectura consistente en:

  - **Validación de entrada.** Utilizar un mecanismo estándar de
    validación de entrada para validar toda la información entrante
    contra longitud, tipo, sintaxis, y reglas de negocio antes de
    permitir que la información sea visualizada o almacenada. Utilizar
    una estrategia de validación de “aceptar solo lo bueno”. Rechazar la
    información inválida en lugar de rehabilitar posible información
    hostil. No olvidar que los mensajes de errores pueden también
    contener información inválida.
  - **Codificación fuerte de salida.** Asegurar que toda la información
    suministrada por el usuario sea apropiadamente codificada (sea HTML
    o XML dependiendo en el mecanismo de salida) antes de devolver la
    página, mediante la codificación de todos los caracteres a
    excepción de un pequeño subgrupo. Este es el enfoque Anti-XSS de la
    librería Microsoft, y próximamente utilizado en la librería OWASP
    PHP Anti-XSS. También, configurar la codificación de caracteres para
    cada página de salida, lo cual reducirá la exposición a algunas
    variantes.
  - **Especificación de la codificación de salida.** (tales como ISO
    8859-1 o UTF 8). No permitir que el atacante elija esto en nombre de
    los usuarios.
  - '''No utilizar la validación de lista negra “blacklist” *'para
    detectar XSS en la entrada o para validar la salida. Buscar y
    reemplazar solo algunos caracteres (*“\<” “\>” y otros caracteres
    similares o frases tales como “script”*) es una técnica débil y ha
    sido atacada satisfactoriamente con anterioridad. Incluso una
    etiqueta “*\<b\>''” sin verificar es inseguro en algunos contextos.
    XSS tiene un sorprendente número de variantes que hacen sencillo
    evitar la validación de listas negras.

<!-- end list -->

  - '''Cuidado con los errores canónicos. '''Los valores de entrada
    deben ser decodificados y canonizados a la representación interna de
    la aplicación antes de ser validados. Asegurarse que la aplicación
    no decodifique la misma entrada dos veces. Tales errores pueden ser
    usados para evadir los esquemas de listas blancas “whitelists”
    introduciendo entradas peligrosas luego de haber sido controladas.

Recomendaciones específicas de lenguaje:

  - '''Java: Utilizar mecanismos de salida Struts '''tales como
    *\<bean:write..\>*, o utilizar el atributo JSTL por defecto
    *escapeXML=”true”* en *\<c:out...\>*. NO utilizar *\<%=....%\>*
    desanidados (esto es, fuera de un mecanismo de salida codificado
    apropiadamente).
  - '''NET: Utilizar la librería Microsoft de Anti-XSS '''versión 1.5 la
    cual se encuentra disponible gratuitamente en MSDN. No asignar a los
    campos de un formulario información directamente desde un objeto
    Request: *username.Text = Request.QueryString(“username”)*; sin
    utilizar esta librería. Comprender qué controles .NET
    automáticamente codifican la información de salida.
  - **PHP: Asegurar que la salida es pasada a través de
    *htmlentities()*** **o *htmlspecialchars()*** o utilizar la librería
    OWASP PHP Anti-XSS que será lanzada próximamente. '''Deshabilitar
    *register_globals* '''si aun se encuentra habilitado.

## Ejemplos

  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4206>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4206%20)
  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-3966>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-3966%20)
  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5204>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5204%20)

## Páginas Relacionadas

  - [Proyecto Stinger](:Category:OWASP_Stinger_Project "wikilink")
  - [Probar XSS](Testing_for_Cross_site_scripting "wikilink")
  - [Filtros para PHP de OWASP](OWASP_PHP_Filters "wikilink")
  - [Proyecto de codificación de
    OWASP](:Category:OWASP_Encoding_Project "wikilink")

## Referencias

  - CWE: CWE-79, Cross-Site scripting (XSS)
  - WASC Threat Classification:
    <http://www.webappsec.org/projects/threat/classes/cross-site_scripting.shtml>
  - OWASP – Cross site scripting,
    [<http://www.owasp.org/index.php/Cross_Site_Scripting>](http://www.owasp.org/index.php/Cross_Site_Scripting%20)
  - OWASP – Testing for XSS,
    <http://www.owasp.org/index.php/Testing_for_Cross_site_scripting>
  - OWASP Stinger Project (A Java EE validation filter) –
    <http://www.owasp.org/index.php/Category:OWASP_Stinger_Project>
  - OWASP PHP Filter Project -
    <http://www.owasp.org/index.php/OWASP_PHP_Filters>
  - OWASP Encoding Project -
    <http://www.owasp.org/index.php/Category:OWASP_Encoding_Project>
  - RSnake, XSS Cheat Sheet,
    [<http://ha.ckers.org/xss.html>](http://ha.ckers.org/xss.html%20)
  - Klein, A., DOM Based Cross Site Scripting,
    [<http://www.webappsec.org/projects/articles/071105.shtml>](http://www.webappsec.org/projects/articles/071105.shtml%20)
  - .NET Anti-XSS Library -
    <http://www.microsoft.com/downloads/details.aspx?FamilyID=efb9c819-53ff-4f82-bfaf-e11625130c25&DisplayLang=en>