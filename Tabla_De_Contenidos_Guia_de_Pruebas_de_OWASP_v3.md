__NOTOC__

**20 de Mayo, 2008** Este es el borrador de la tabla de contenido de la
nueva guía de pruebas Puede bajar la versión estable
[aqui](http://www.owasp.org/index.php/Image:OWASP_Testing_Guide_v2_pdf.zip)
o leerla en línea
[aqui](http://www.owasp.org/index.php/OWASP_Testing_Guide_v2_Table_of_Contents)

`Guía de Pruebas de OWASP v3 (borrador 20 de mayo, 2008) (OTG por sus siglas en inglés)`

`El índice principal es el OTG v2. (nuevo): nuevos artículos, (mejora): necesita mejorar`

`==`[`(mejorar)Prólogo`](Testing_Guide_Foreword "wikilink")`==`

## [(mejorar)1. Portada](Testing_Guide_Frontispiece "wikilink")

**[(mejorar)1.1 Sobre el proyecto de pruebas de
OWASP](Testing_Guide_Frontispiece "wikilink")**

**[1.2 Sobre el proyecto abierto en seguridad de
aplicaciones](About_The_Open_Web_Application_Security_Project "wikilink")**

## [2. Presentación](Testing_Guide_Introduction "wikilink")

**2.1 El proyecto de pruebas de OWASP**

**2.2 Principios de las pruebas**

**2.3 Explicación de las técnicas de pruebas**

(nuevo) 2.4 Derivación de requerimientos para pruebas de seguridad,
requerimientos de pruebas funcionales y no funcionales, y casos de
pruebas a través de casos de uso y mal uso

(nuevo) 2.4.1 Pruebas de seguridad integradas en los flujos de trabajo
de desarrolladores y probadores

(nuevo) 2.4.2 Pruebas de seguridad de los desarrolladores: Pruebas
unitarias, pruebas a nivel de componente, etc

(nuevo) 2.4.3 Pruebas de seguridad de los probadores funcionales:
pruebas integrales de sistema, pruebas de aceptación, y ambientes de
producción

(nuevo) 2.5 Análisis de datos y reporte de las pruebas de seguridad:
identificación de causas raíz y reporte de pruebas de datos basado en el
negocio y rol

## [3. El marco de pruebas de OWASP](The_OWASP_Testing_Framework "wikilink")

**3.1. Descripción**

**3.2. Fase 1: Anstes que empiece el desarrollo**

**3.3. Fase 2: Durante la definición y diseño**

**3.4. Fase 3: Durante el desarrollo**

**3.5. Fase 4: Durante la publicación**

**3.6. Fase 5: Mantenimiento y operaciones**

'''3.7. Un típico flujo de trabajo en el ciclo de desarrollo '''

## [4. (mejorar) Pruebas de intrusion en aplicaciones Web](Web_Application_Penetration_Testing "wikilink")

[**4.1 Presentación y
Objetivos**](Testing:_Introduction_and_objectives "wikilink")

[**(mejorar) 4.2 Recopilación de
información**](Testing:_Information_Gathering "wikilink")

[4.2.1 (mejorar) Pruebas de identificación de aplicaciones
Web](Testing_for_Web_Application_Fingerprint_\(OWASP-IG-004\) "wikilink")

[4.2.2 Descubrimiento de
aplicaciones](Testing_for_Application_Discovery "wikilink")

[(new:Christian Heinrich)4.2.3 "Spiders", Robots y
"Crawlers"](Testing:_Spiders,_Robots,_and_Crawlers_\(OWASP-IG-001\) "wikilink")

[(new:Christian Heinrich)4.2.4 Descubrimiento y reconocimiento con
buscadores"](Testing:_Search_engine_discovery/reconnaissance_\(OWASP-IG-002\) "wikilink")

[(mejorar)4.2.5 Análisis de códigos de
error](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")

[4.2.6 Pruebas de configuración en la
infraestructura](Testing_for_infrastructure_configuration_management_\(OWASP-CM-003\) "wikilink")

[4.2.6.1 Pruebas de
SSL/TLS](Testing_for_SSL-TLS_\(OWASP-CM-001\) "wikilink")

[4.2.6.2 Pruebas en el "listener" de bases de
datos](Testing_for_DB_Listener_\(OWASP-CM-002\) "wikilink")

[4.2.7 Pruebas de configuración en la
aplicación](Testing_for_application_configuration_management_\(OWASP-CM-004\) "wikilink")

[4.2.7.1 Pruebas sobre el manejo de extensiones de
archivos](Testing_for_file_extensions_handling_\(OWASP-CM-005\) "wikilink")

[4.2.7.2 Archivos viejo, de respaldo o sin
referencia](Testing_for_Old,_Backup_and_Unreferenced_Files_\(OWASP-CM-006\) "wikilink")

[**(mejorar)4.3 Pruebas de reglas de
negocio**](Testing_for_business_logic_\(OWASP-BL-001\) "wikilink")

[**(mejorar)4.4 Pruebas de
autenticación**](Testing_for_authentication "wikilink")

[(nuevo)4.4.1 Transporte de credenciales en un canal
cifrado](Testing_for_credentials_transport_\(OWASP-AT-001\) "wikilink")

[4.4.2 Probar cuentas de usuario previsibles (de
diccionario)](Testing_for_Default_or_Guessable_User_Account_\(OWASP-AT-003\) "wikilink")

[4.4.3 Pruebas de fuerza
bruta](Testing_for_Brute_Force_\(OWASP-AT-004\) "wikilink")

[4.4.4 Pruebas para sobrepasar el esquema de
autentificación](Testing_for_Bypassing_Authentication_Schema_\(OWASP-AT-005\) "wikilink")

[4.4.5 Pruebas de acceso a directorios protegidos/inclusión de
archivos](Testing_for_Directory_Traversal "wikilink")

[4.4.6 Pruebas en "olvide mi contraseña" y "restauración de contraseña"
vulnerables](Testing_for_Vulnerable_Remember_Password_and_Pwd_Reset_\(OWASP-AT-006\) "wikilink")

[4.4.7 Pruebas de terminación de sesión y manejo de memoria de acceso
rápido del
navegador](Testing_for_Logout_and_Browser_Cache_Management_\(OWASP-AT-007\) "wikilink")

[**(nuevo) 4.x Pruebas de
autorización**](Testing_for_Authorization "wikilink")

[(nuevo) 4.x.x Pruebas de acceso a directorios
protegidos](Testing_for_Path_Traversal_\(OWASP-AZ-001\) "wikilink")

[(nuevo)4.x.x Pruebas para sobrepasar el esquema de
autorización](Testing_for_Bypassing_Authorization_Schema "wikilink")

[(nuevo)4.x.x Pruebas de elevación de
privilegios](Testing_fot_Privilege_escalation "wikilink")

[**4.5 Pruebas de manejo de
sesión**](Testing_for_Session_Management "wikilink")

[4.5.1 Pruebas del esquema de manejo de
sesión](Testing_for_Session_Management_Schema_\(OWASP-SM-001\) "wikilink")

[(nuevo)4.5.2 Pruebas de fortaleza de testígos (anterior 4.5.2 Pruebas
del esquema de manejo de
sesión)](Testing_for_Cookie_and_Session_Token_Manipulation "wikilink")

[4.5.3 Probando variables de sesion
expuestas](Testing_for_Exposed_Session_Variables_\(OWASP-SM-004\) "wikilink")

[4.5.4 Probando CSRF](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")

[4.5.5 Probando vulnerabilidades de
HTTP](Testing_for_HTTP_Splitting/Smuggling_\(OWASP-DV-016\) "wikilink")

[**4.6 Pruebas de validación de
datos**](Testing_for_Data_Validation "wikilink")

[(nuevo)4.6.1 Pruebas de "Reflected Cross Site
Scripting"](Testing_for_Reflected_Cross_site_scripting_\(OWASP-DV-001\) "wikilink")

[(nuevo)4.6.2 Pruebas de "Cross Site Scripting"
almacenado](Testing_for_Stored_Cross_site_scripting_\(OWASP-DV-002\) "wikilink")

[4.6.3 Probando "Cross Site Scripting" basado en el
DOM](Testing_for_DOM-based_Cross_site_scripting_\(OWASP-DV-003\) "wikilink")

[(nuevo)4.6.4 Probando "Cross Site
Flashing"](Testing_for_Cross_site_flashing_\(OWASP-DV-004\) "wikilink")

[4.6.1.1 Probando metodos HTTP y
XST](Testing_for_HTTP_Methods_and_XST_\(OWASP-CM-008\) "wikilink")

[4.6.2 Probando inyección de
SQL](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")

[4.6.2.1 Pruebas para Oracle](Testing_for_Oracle "wikilink")

[4.6.2.2 Pruebas para MySql](Testing_for_MySQL "wikilink")

[4.6.2.3 Pruebas para Sql Server](Testing_for_SQL_Server "wikilink")

[4.6.3 Pruebas de inyección de
LDAP](Testing_for_LDAP_Injection_\(OWASP-DV-006\) "wikilink")

[4.6.4 Pruebas de inyección de
ORM](Testing_for_ORM_Injection_\(OWASP-DV-007\) "wikilink")

[4.6.5 Pruebas de inyección de
XML](Testing_for_XML_Injection_\(OWASP-DV-008\) "wikilink")

[4.6.6 Pruebas de inyección en
SSI](Testing_for_SSI_Injection_\(OWASP-DV-009\) "wikilink")

[4.6.7 Pruebas de inyección de
XPath](Testing_for_XPath_Injection_\(OWASP-DV-010\) "wikilink")

[4.6.8 Inyección en
IMAP/SMTP](Testing_for_IMAP/SMTP_Injection_\(OWASP-DV-011\) "wikilink")

[4.6.9 Pruebas de inyección de
código](Testing_for_Code_Injection_\(OWASP-DV-012\) "wikilink")

[4.6.10 Pruebas de inyección de
comandos](Testing_for_Command_Injection_\(OWASP-DV-013\) "wikilink")

[4.6.11 Pruebas de desbordamiento de
memoria](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")

[4.6.11.1 Pruebas de desbordamiento de
Heap](Testing_for_Heap_Overflow "wikilink")

[4.6.11.2 Pruebas de desbordamiento de
pila](Testing_for_Stack_Overflow "wikilink")

[4.6.11.3 Pruebas de formato de
cadenas](Testing_for_Format_String "wikilink")

[4.6.12 Probando incubación de
vulnerabilidades](Testing_for_Incubated_Vulnerability_\(OWASP-DV-015\) "wikilink")

[**4.7 Pruebas de negación de servicio
(NdS)**](Testing_for_Denial_of_Service "wikilink")

[4.7.1 Pruebas de NdS bloqueando cuentas de
cliente](Testing_for_DoS_Locking_Customer_Accounts_\(OWASP-DS-002\) "wikilink")

[4.7.2 Pruebas de NdS en desbordamientos de
meoria](Testing_for_DoS_Buffer_Overflows_\(OWASP-DS-003\) "wikilink")

[4.7.3 Pruebas de NdS en asignación de objectos específicos al
usuario](Testing_for_DoS_User_Specified_Object_Allocation_\(OWASP-DS-004\) "wikilink")

[4.7.4 Pruebas de entradas de usuario como contadores en
ciclos](Testing_for_User_Input_as_a_Loop_Counter_\(OWASP-DS-005\) "wikilink")

[4.7.5 Pruebas sobre escritura en disco de datos proveídos por el
usuario](Testing_for_Writing_User_Provided_Data_to_Disk_\(OWASP-DS-006\) "wikilink")

[4.7.6 Pruebas de NdS por fallas al liberar
recursos](Testing_for_DoS_Failure_to_Release_Resources_\(OWASP-DS-007\) "wikilink")

[4.7.7 Pruebas de demasiada información en la
sesión](Testing_for_Storing_too_Much_Data_in_Session_\(OWASP-DS-008\) "wikilink")

[**4.8 Pruebas en servicios Web**](Testing_for_Web_Services "wikilink")

[4.8.1 Pruebas estructurales de
XML](Testing_for_XML_Structural_\(OWASP-WS-003\) "wikilink")

[4.8.2 Pruebas a nivel de contenido en
XML](Testing_for_XML_Content-Level_\(OWASP-WS-004\) "wikilink")

[4.8.3 Pruebas de parametros Get de HTTP y
REST](Testing_for_WS_HTTP_GET_parameters/REST_attacks_\(OWASP-WS-005\) "wikilink")

[4.8.4 Pruebas de datos adjuntos en
SOAP](Testing_for_Naughty_SOAP_Attachments_\(OWASP-WS-006\) "wikilink")

[4.8.5 Pruebas de repeticion en
WebServices](Testing_for_WS_Replay_\(OWASP-WS-007\) "wikilink")

[(nuevo)4.10 Pruebas del lado del
cliente](Client-Side_Testing "wikilink")

[(nuevo) 4.10.1 Probando
AJAX](Testing_for_AJAX_\(OWASP-AJ-002\) "wikilink")

[(nuevo)4.10.2 Probando Flash](Flash_Testing "wikilink")

[(nuevo)4.10.3 Probando RIA](RIA_Testing "wikilink")

## [(mejorar)5. Escribiendo Reportes: valor del riesgo real](Writing_Reports:_value_the_real_risk "wikilink")

[5.1 Como valuar el riesgo real](How_to_value_the_real_risk "wikilink")

[5.2 Como escribir el reporte de
pruebas](How_to_write_the_report_of_the_testing "wikilink")

`OTGv3 Distribución del equipo`

Vea también
<http://www.owasp.org/index.php/OWASP_Testing_Guide_v3_Startup>.


La nueva guia de pruebas de OWASP v3:
Este
[documento](http://www.owasp.org/index.php/Image:Planning_OTGv3.doc)
analiza el checklist de la guía de pruebas de OWASP y una plan para
crear na nueva v3.

  - 1\) Pruebas metodológicas (Nueva categoría) \<-- (Mat) Necesita
    explicación
  - 2\) Faltan las pruebas de autorizacion. (Nueva categoría)
  - 3\) Recopilación de información no es una vulnerabilidad
  - 4\) Pruebas de reglas de negocio
  - 5\) Pruebas de infraestructura ? (Nueva categoría) \*esto se debe de
    concentrar solamente en el puerto 80 y 443 y otras pruebas
    relacionados con la Web
  - 6\) La sección de web services necesita mejoras
  - 7\) La sección de pruebas de AJAX necestia mejoras
  - 8\) Actualizacion a la seccion de metodologías de pruebas
    (requerimientos, planes, niveles y ambientes)
  - 9\) Nueva Categoría: Pruebas del lado del cliente
  - 10\) Nueva Categoría: Pruebas de clientes pesados
  - 11\) Nueva Categoría: Aplicaciones de Flash/Silverlight
  - 12\) Nueva Categoría: Probando aplicaciones financieras
  - 13\) Nueva Categoría: Fuzzing (tenemos vectores, pero debe explicar
    todo el concepto)

Nuevas categorias propuestas para la OTG v3:

  - OTG plantillas de formas
      - OTG Petición de citas (nuevo)
      - OTG Forma de autorizacion para pruebas en terceros (nuevo)
      - OTG Reporte de ejemplo (nuevo)
  - Modo Pasivo
  - Recopilación de información
  - Pruebas de reglas de negocio
  - Pruebas de intrusión en aplicaciones Web
      - Pruebas de infraestructura
      - Pruebas de autentificación
      - Pruebas de autorización (nuevo)
      - Pruebas de manejo de sesión
      - Pruebas de validación de datos
      - Pruebas de negación de servicios
      - Pruebas de servicios Web
      - Pruebas del lado del cliente
          - Pruebas de AJAX
          - Pruebas de Flash (nuevo)
          - Pruebas en RIA (nuevo)

[Category:OWASP Testing
Project](Category:OWASP_Testing_Project "wikilink")