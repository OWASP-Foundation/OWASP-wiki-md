Una referencia directa a objetos ("direct object reference") ocurre
cuando un programador expone una referencia hacia un objeto interno de
la aplicación, tales como un fichero, directorio, registro de base de
datos, o una clave tal como una URL o un parámetro de formulario Web. Un
atacante podría manipular este tipo de referencias en la aplicación para
acceder a otros objetos sin autorización, a menos que se aplique un
control de accesos como medida de prevención.

Por ejemplo, en las aplicaciones de banca en línea, es común utilizar el
número de cuenta como clave primaria. Por consiguiente, se podría tener
la tentación de usar esta clave directamente como parámetro en la
interfaz Web. Aún en el caso de que el equipo de desarrollo hubiera
utilizado consultas SQL *preparadas* ("parameterized SQL queries") para
evitar una inyección SQL, podría ser posible que un atacante modificara
este parámetro para ver o cambiar ***todas*** las demás cuentas, si no
se verifica también que el usuario es el titular de la cuenta bancaria o
está autorizado para acceder a la misma.

Este tipo de ataque fue el utilizado sobre el sitio Web *GST Start Up
Assistance*, de la *Australian Taxation Office*, en el cual un atacante
con credenciales válidas modificó el parámetro "ABN" (un identificador
fiscal) presente en la URL. Dicho atacante consiguió obtener los
detalles almacenados en el sistema de 17.000 compañías, y a continuación
envió un correo electrónico a cada una de ellas. Fue un escándalo para
la Dirección de las compañías afectadas. Aún cuando este tipo de
vulnerabilidad es muy común, generalmente no se verifica en las
aplicaciones actuales.

## Entornos Afectados

Todos los entornos de desarrollo de aplicaciones de Web son vulnerables
presentando referencias a objetos internos de la aplicación.

## Vulnerabilidad

Muchas aplicaciones presentan a los usuarios referencias a objetos
internos. Un atacante podría manipular los parámetros de entrada a la
aplicación cambiando estas referencias, saltándose de esta manera un
control de accesos incorrectamente desarrollado. Con frecuencia, estas
referencias apuntan a sistemas de ficheros y bases de datos, si bien
cualquier otro elemento de la aplicación podría ser vulnerable por un
problema de esta categoría.

Por ejemplo, en el caso de que el código utilizara la entrada del
usuario para construir nombres de fichero o rutas de acceso a los
mismos, podría ser posible que un atacante saliera del directorio donde
está la aplicación, y accediera a otros recursos.

`<select name="language"><option value="fr">Francais</option></select>`
`... `
`require_once ($_REQUEST['language']."lang.php");`

Un código como este puede ser atacado suministrando como entrada una
cadena como "../../../../etc/passwd%00" que utiliza la inyección de un
byte nulo ("[null byte
injection](http://www.owasp.org/index.php/Data_Validation)", véase la
[guía OWASP](http://www.owasp.org/index.php/OWASP_Guide_Project) para
ampliar información), y acceder así a cualquier fichero del sistema
atacado.

De igual forma, es habitual presentar referencias a claves de base de
datos. Un atacante puede explotar la vulnerabilidad sencillamente
adivinando o buscando otros valores válidos para la clave. A menudo son
secuenciales. En el ejemplo que se presenta a continuación, un atacante
puede cambiar el parámetro "cartID" para obtener la información asociada
a cualquier "carrito de la compra" de la aplicación.

`int cartID = Integer.parseInt( request.getParameter( "cartID" ) );`
`String query = "SELECT * FROM table WHERE cartID=" + cartID;`

## Verificando la seguridad

El objetivo es comprobar que la aplicación no presente ninguna
referencia directa a un objeto interno de la misma.

Enfoques automáticos: las herramientas de análisis automático de
vulnerabilidades podrían tener dificultades para identificar parámetros
manipulables, o si dicha manipulación ha tenido éxito. Las herramientas
de análisis estático no pueden saber qué parámetros deben ser sometidos
a un control de accesos antes de ser utilizados.

Enfoques manuales: mediante una revisión de código se puede rastrear el
uso de cada parámetro crítico y saber si podría ser manipulado.
Asimismo, mediante una prueba de intrusión se podría saber si dicha
manipulación es posible. Sin embargo, ambas técnicas de análisis son
costosas en tiempo y es posible que se dejen bastantes posibilidades sin
explorar.

## Protección

La mejor protección es evitar presentar al usuario cualquier referencia
directa a un objeto, mediante el uso de un índice, un mapa de
referencias indirectas, o cualquier otro método que sea fácil de
verificar. Si es necesario utilizar una referencia directa, se deberá
comprobar que el usuario está autorizado a usarla antes de hacerlo.

Es importante establecer una manera estándar para diseñar referencias a
objetos de la aplicación:

  - **Evitar presentar al usuario referencias a objetos privados de la
    aplicación siempre que sea posible, por ejemplo claves primarias o
    nombres de fichero.**
  - **Validar cualquier referencia a un objeto privado extensivamente
    aceptando "sólo los conocidos".**
  - **Verificar la autorización a todos los objetos referenciados.**

La mejor solución es el uso de un índice o un mapa de referencias que
eviten la manipulación de parámetros.

<http://www.example.com/application?file=1>

En caso de que sea necesario presentar referencias a elementos de base
de datos, hay que asegurarse de que las sentencias SQL y otros
mecanismos de acceso a base de datos sólo permiten que se obtengan los
registros autorizados:

`int cartID = Integer.parseInt( request.getParameter( "cartID" ) );`
`User user = (User)request.getSession().getAttribute( "user" );`
`String query = "SELECT * FROM table WHERE cartID=" + cartID + " `**`AND``
 ``userID="``   ``+``   ``user.getID()`**`;`

## Ejemplos

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0329>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4369>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-0229>

## Referencias

  - CWE: CWE-22 (Path Traversal), CWE-472 (Web Parameter Tampering)
  - WASC Threat Classification:
    \[<http://www.webappsec.org/projects/threat/classes/abuse_of_functionality.shtml>
    [http://www.webappsec.org/projects/threat/classes/abuse_of_functionality.shtml\]http://www.webappsec.org/projects/threat/classes/insufficient_authorization.shtml](http://www.webappsec.org/projects/threat/classes/abuse_of_functionality.shtml%5Dhttp://www.webappsec.org/projects/threat/classes/insufficient_authorization.shtml)
  - OWASP Testing Guide,
    <http://www.owasp.org/index.php/Testing_for_business_logic>
  - OWASP Testing Guide,
    <http://www.owasp.org/index.php/Testing_for_Directory_Traversal>
  - OWASP,
    <http://www.owasp.org/index.php/Category:Access_Control_Vulnerability>
  - GST Assist attack details,
    <http://www.abc.net.au/7.30/stories/s146760.htm>