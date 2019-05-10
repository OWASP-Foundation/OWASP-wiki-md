Con frecuencia las aplicaciones fallan en el cifrado de tráfico de redes
cuando es necesario proteger comunicaciones importantes. El cifrado
(normalmente SSL) debería ser usado para todas las conexiones
autenticadas, especialmente páginas accesibles desde Internet, aunque
también para conexiones de bases de datos.

En caso contrario, la aplicación puede dejar expuestos los testigos de
autenticación y de sesión.

Además, el cifrado debe ser usado siempre que se transmitan datos
delicados, tales como información de tarjetas de crédito o información
de salud.

El estándar de PCI exige que toda la información de tarjetas de crédito
transmitida a través de Internet esté cifrada.

## Entornos Afectados

Todos los entornos de aplicaciones Web son vulnerables a comunicaciones
inseguras.

## Vulnerabilidad

Un fallo cifrando comunicaciones delicados significa que un atacante que
pueda husmear en el tráfico de una red será capaz de acceder a la
conversación, incluso a cualquier credencial o información sensible
transmitida. Se debe considerar que hay diferentes redes que serán más o
menos susceptibles al husmeo. Sin embargo, es importante comprender que
algunas veces un servidor puede ser comprometido en casi cualquier
segmento de red, y los atacantes rápidamente instalarán un "husmeador"
para capturar las credenciales de otros sistemas. Usar SSL para las
comunicaciones con usuarios finales es crítico, ya que estos
probablemente usarán redes inseguras para acceder a las aplicaciones.

Debido a que HTTP incluye credenciales de autenticación o testigos de
sesión en cada petición, todo el tráfico autenticado necesita ir sobre
SSL, no solamente la petición de conexión. El cifrado de comunicaciones
con servidores de bases de datos también es importante. Aunque es
probable que estas redes sean más seguras, la información y credenciales
que ellas portan son más delicadas y más extensas. Por lo que el uso de
SSL en el segmento de bases de datos es muy importante. El cifrado de
datos delicados, tales como datos de tarjetas de crédito y números de
seguridad social se ha convertido en una regulación de privacidad y
financiera para muchas organizaciones. El no usar SSL en conexiones que
manipulen este tipo de datos crea riesgos de cumplimiento de la
regulación.

## Verificando la seguridad

El objetivo es verificar que la aplicación cifra correctamente todas las
comunicaciones delicadas y autenticadas.

Enfoques automatizados: Herramientas para analizar vulnerabilidades
pueden verificar que SSL es usado en la interfaz y detectar muchas
fallas relacionadas con SSL. Sin embargo, estas herramientas no tienen
acceso a conexiones a bases de datos y no pueden verificar si son
seguras. Las herramientas de análisis estático podrían ayudar con
análisis de algunas llamadas a sistemas de bases de datos, pero
probablemente no serían capaces de entender la lógica particular
requerida para todos los tipos de sistemas.

Enfoques manuales: Las pruebas manuales pueden verificar el uso de SSL y
detectar muchas fallas relacionadas con SSL en el segmento de interfaz,
pero los enfoques automatizados son probablemente más eficientes. La
revisión de código es muy eficiente para la verificación de un uso
correcto de SSL en las conexiones de bases de datos.

## Protección

La protección más importante es usar SSL en cualquier conexión
autenticada o siempre que se transmitan datos delicados. Hay una serie
de detalles relacionados con la configuración correcta de SSL para
aplicaciones Web, por lo que es importante la comprensión y análisis de
su entorno. Por ejemplo, IE 7.0 tiene una barra verde para los
certificados SSL de "alta confianza", pero este no es un control idóneo
para probar el uso seguro de la criptografía solamente.

  - Use SSL para todas las conexiones que sean autenticadas, o
    transmitan datos delicados o de valor, tales como credenciales,
    detalles de tarjetas de crédito, información de salud u otros datos
    privados.
  - Asegúrese que las comunicaciones entre los elementos de
    infraestructura, tales como las que hay entre servidores Web y
    servidores de bases de datos, estén debidamente protegidas con el
    uso de una capa de transporte segura o un nivel de protocolo de
    cifrado para credenciales y datos de valor.
  - Según el requerimiento 4 de PCI Data Security Standard, se deben
    proteger los datos en tránsito de los titulares de tarjetas de
    crédito. En general, los accesos online de clientes, socios,
    personal y administrativos a los sistemas deben ser cifrados usando
    SSL o similares. Para más información, por favor, mire "PCI DSS
    Guidelines" e implemente los controles necesarios.

## Ejemplos

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6430>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-4704>
  - <http://www.schneier.com/blog/archives/2005/10/scandinavian_at_1.html>

## Referencias

  - CWE: CWE-311 (Failure to encrypt data), CWE-326 (Weak Encryption),
    CWE-321 (Use of hard-coded cryptographic key), CWE-325 (Missing
    Required Cryptographic Step), others.
  - WASC Threat Classification: No explicit mapping
  - OWASP *Testing Guide*, Testing for SSL / TLS,
    <https://www.owasp.org/index.php/Testing_for_SSL-TLS>
  - OWASP Guide, <http://www.owasp.org/index.php/Guide_to_Cryptography>
  - Foundstone - SSL Digger,
    <http://www.foundstone.com/index.htm?subnav=services/navigation.htm&subcontent=/services/overview_s3i_des.htm>
  - NIST, SP 800-52 Guidelines for the selection and use of transport
    layer security (TLS) Implementations,
    <http://csrc.nist.gov/publications/nistpubs/800-52/SP800-52.pdf>
  - NIST SP 800-95 Guide to secure Web services,
    <http://csrc.nist.gov/publications/drafts.html#sp800-95>