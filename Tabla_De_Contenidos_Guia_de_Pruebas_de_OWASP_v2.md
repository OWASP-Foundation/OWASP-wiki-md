__NOTOC__

## [Prólogo](Testing_Guide_Foreword "wikilink")

## [1. Portada](Testing_Guide_Frontispiece "wikilink")

**[1.1 Sobre el proyecto de pruebas de
OWASP](Testing_Guide_Frontispiece "wikilink")**

1.1.1 Derechos de Autor

1.1.2 Editores

1.1.3 Autores y revisores

1.1.4 Historial de revisión

1.1.5 Marcas Registradas

**[1.2 Sobre el proyecto abierto en seguridad de
aplicaciones](About_The_Open_Web_Application_Security_Project "wikilink")**

1.2.1 Introducción

1.2.2 Estructura

1.2.3 Licensias

1.2.4 Participación y Membrecías

1.2.5 Proyectos

1.2.6 Política de privacidad de OWASP

## [2. Presentación](Testing_Guide_Introduction "wikilink")

**2.1 El proyecto de pruebas de OWASP**

**2.2 Principios de las pruebas**

**2.3 Explicación de las técnicas de pruebas**

## [3. El marco de pruebas de OWASP](The_OWASP_Testing_Framework "wikilink")

**3.1. Descripción**

**3.2. Fase 1: Anstes que empiece el desarrollo**

**3.3. Fase 2: Durante la definición y diseño**

**3.4. Fase 3: Durante el desarrollo**

**3.5. Fase 4: Durante la publicación**

**3.6. Fase 5: Mantenimiento y operaciones**

'''3.7. Un típico flujo de trabajo en el ciclo de desarrollo '''

## [4. Pruebas de intrusion en aplicaciones Web](Web_Application_Penetration_Testing "wikilink")

[**4.1 Presentación y
objetivos**](Testing:_Introduction_and_objectives "wikilink")

[**4.2 Obteniendo
información**](Testing:_Information_Gathering "wikilink")

[4.2.1 Pruebas de identificación de aplicaciones
Web](Testing_for_Web_Application_Fingerprint "wikilink")

[4.2.2 Descubrimiento de
aplicaciones](Testing_for_Application_Discovery "wikilink")

[4.2.3 "Spidering" y
"Googling"](Testing:_Spidering_and_googling "wikilink")

[4.2.4 Análisis de códigos de
error](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")

[4.2.5 Pruebas de configuración en la
infraestructura](Testing_for_infrastructure_configuration_management_\(OWASP-CM-003\) "wikilink")

[4.2.5.1 Pruebas de
SSL/TLS](Testing_for_SSL-TLS_\(OWASP-CM-001\) "wikilink")

[4.2.5.2 Pruebas en el "listener" de bases de
datos](Testing_for_DB_Listener_\(OWASP-CM-002\) "wikilink")

[4.2.6 Pruebas de configuración en la
aplicación](Testing_for_application_configuration_management_\(OWASP-CM-004\) "wikilink")

[4.2.6.1 Pruebas sobre el manejo de extensiones de
archivos](Testing_for_file_extensions_handling_\(OWASP-CM-005\) "wikilink")

[4.2.6.2 Archivos viejo, de respaldo o sin
referencia](Testing_for_Old,_Backup_and_Unreferenced_Files_\(OWASP-CM-006\) "wikilink")

[**4.3 Pruebas de reglas de
negocio**](Testing_for_business_logic_\(OWASP-BL-001\) "wikilink")

[**4.4 Pruebas de
autenticación**](Testing_for_authentication "wikilink")

[4.4.1 Probar cuentas de usuario previsibles (de
diccionario)](Testing_for_Default_or_Guessable_User_Account_\(OWASP-AT-003\) "wikilink")

[4.4.2 Pruebas de fuerza
bruta](Testing_for_Brute_Force_\(OWASP-AT-004\) "wikilink")

[4.4.3 Pruebas para sobrepasar el esquema de
autentificación](Testing_for_Bypassing_Authentication_Schema_\(OWASP-AT-005\) "wikilink")

[4.4.4 Pruebas de acceso a directorios protegidos/inclusión de
archivos](Testing_for_Directory_Traversal "wikilink")

[4.4.5 Pruebas en "olvide mi contraseña" y "restauración de contraseña"
vulnerables](Testing_for_Vulnerable_Remember_Password_and_Pwd_Reset_\(OWASP-AT-006\) "wikilink")

[4.4.6 Pruebas de terminación de sesión y manejo de memoria de acceso
rápido del
navegador](Testing_for_Logout_and_Browser_Cache_Management_\(OWASP-AT-007\) "wikilink")

[**4.5 Pruebas de manejo de
sesión**](Testing_for_Session_Management "wikilink")

[4.5.1 Pruebas del esquema de manejo de
sesión](Testing_for_Session_Management_Schema_\(OWASP-SM-001\) "wikilink")

[4.5.2 Probando manipulación de testigos de sessión y
cookies](Testing_for_Cookie_and_Session_Token_Manipulation "wikilink")

[4.5.3 Probando variables de sesion
expuestas](Testing_for_Exposed_Session_Variables_\(OWASP-SM-004\) "wikilink")

[4.5.4 Probando CSRF](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")

[4.5.5 Probando vulnerabilidades de
HTTP](Testing_for_HTTP_Splitting/Smuggling_\(OWASP-DV-016\) "wikilink")

[**4.6 Pruebas de validación de
datos**](Testing_for_Data_Validation "wikilink")

[4.6.1 Probando "Cross Site
Scripting"](Testing_for_Cross_site_scripting "wikilink")

[4.6.1.1 Probando metodos HTTP y XST (por sus siglas en
inglés)](Testing_for_HTTP_Methods_and_XST_\(OWASP-CM-008\) "wikilink")

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

[**4.9 Pruebas en AJAX**](Testing_for_AJAX:_introduction "wikilink")

[4.9.1 Vulnerabilidades de
AJAX](Testing_for_AJAX_Vulnerabilities_\(OWASP-AJ-001\) "wikilink")

[4.9.2 Como probar AJAX](Testing_for_AJAX_\(OWASP-AJ-002\) "wikilink")

## [5. Escribiendo Reportes: valor del riesgo real](Writing_Reports:_value_the_real_risk "wikilink")

[5.1 Como valuar el riesgo real](How_to_value_the_real_risk "wikilink")

[5.2 Como escribir el reporte de
pruebas](How_to_write_the_report_of_the_testing "wikilink")

## [Apéndice A: Herramientas de pruebas](Appendix_A:_Testing_Tools "wikilink")

  - Herramientas de pruebas de "caja negra"
  - Analizadores de código fuente
  - Otras herramientas

## [Apéndice B: Lecturas recomendadas](OWASP_Testing_Guide_Appendix_B:_Suggested_Reading "wikilink")

  - Documentos Técnicos
  - Libros
  - Sitiós útiles

## [Apéndice C: Vectores de fuzzing](OWASP_Testing_Guide_Appendix_C:_Fuzz_Vectors "wikilink")

  - Categorias de fuzzing
      - Fuzzing recursivo
      - Fuzzing "Replasivo"
  - Cross Site Scripting (XSS)
  - Errores de desbordamiento de memoria y formato de cadenas
      - Desbordamientos de memoria
      - Errores de formato de cadenas
      - Desbordamiento en enteros
  - Inyección de SQL
      - Inyección pasivas de SQL
      - Inyección activas de SQL
  - Inyección de LDAP
  - Inyección de XPATH

[Category:OWASP Testing
Project](Category:OWASP_Testing_Project "wikilink")