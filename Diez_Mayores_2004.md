# NOTA: ESTA NO ES LA VERSIÓN MAS RECIENTE

Por favor visite el [Top 10 2007](Top_10_2007 "wikilink") para acceder a
la ultima edición.

**Bienvenido al proyecto de las 10 mayores vulnerabilidades de OWASP**

La lista de las 10 mayores vulnerabilidades de OWASP es un poderoso
documento para dar a conocer la seguridad en aplicaciones Web. Esta
lista representa un amplio concenso sobre lo que son las fallas de
seguridad más críticas en la seguridad de aplicaciones Web. Los miembros
del proyecto incluyen una variedad de expertos de todo el mundo que han
compartido su experiencia para producir esta lista. Actualmente hay
Versiones en Inglés, Francés, Japones, Koreano, Turco y Español.
Exortamos a todas las compañoas a adoptar este documento dentro de sus
organizaciones y comenzar el proceso de asegurar que sus aplicaciones no
contienen estas fallas. Adoptar la lista de las 10 mayores de OWASP es
quizas, el mas efectivo primer paso hacia cambiar la cultura de
desarrollo de software dentro de su organicación a una que produzca
código seguro.

## Versiones

**Navéguela en linea**

  - [browse](Commentary_OWASP_Top_Ten_Project "wikilink")

**Bájela**

  - [English (Word)](Media:OWASP_Top_Ten_2004.doc "wikilink")
  - [English
    (PDF)](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=70827)

Puede [bajar versiones
internacionales](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=70827)
de SourceForge mientras la movemos al sitio principal. Hay versiones en
todos los lenguajes siguientes:

  - Chino
  - Inglés
  - Francés
  - Italiano
  - Japonés
  - Español
  - Koreano

## Introducción al la lista

La siguiente lista reune las 10 mayores de OWASP. Sin embargo, le
recomendamos vehementenmente leer todo el reporte, dado que cada área
cubre muchisimo terreno.

  - [Comentarios](Commentary_OWASP_Top_Ten_Project "wikilink")
    [Presentación](Introduction_OWASP_Top_Ten_Project "wikilink")
    [Antecedentes](Background_OWASP_Top_Ten_Project "wikilink")
    [Actualizaciones](Updates_OWASP_Top_Ten_Project "wikilink")

<!-- end list -->

  - [A1 2004 Entradas sin
    validar](A1_2004_Entradas_sin_validar "wikilink")
    La informacion de las peticiones web no es validada antes de ser
    usada en una aplicación web. Los atacastes pueden usar estas fallas
    para atacar desde componentes de la base de datos hasta la
    aplicación web.

<!-- end list -->

  - [A2 2004 Control de acceso
    disfunsional](A2_2004_Control_de_acceso_disfunsional "wikilink")
    Las restricciones de lo que los usuarios autentificados estan
    permitidos a hacer no se hacen cumplir adecuadamente. Los atacantes
    pueden explorar esas fallas para acceder a las cuentas de otros
    usuarios, ver archivos con información importante o funcionalidad no
    autorizada.

<!-- end list -->

  - [A3 2004 Atentificación y manejo de sesión
    disfuncional](A3_2004_Atentificación_y_manejo_de_sesión_disfuncional "wikilink")
    Las crededenciales y testigos de sesión no estan protegidos
    adecuadamente. Los atacantes pueden ver contraseñas, llaves, cookies
    de sesión u otros testigos pueden vencer las restricciones de
    autentificación y asumir la identidad de otros usuarios.

<!-- end list -->

  - [A4 2004 Fallas de Cross Site Scripting
    (XSS)](A4_2004_Fallas_de_Cross_Site_Scripting_\(XSS\) "wikilink")
    La aplicacion Web puede ser usada como mecanismo para transportas un
    ataque a el navegador de el usuario final. Un ataque existoso puede
    mostrar el testigo de sesión del usuario final, atacar la
    computadora local o reemplazar contenido para engañar al usuario.

<!-- end list -->

  - [A5 2004 Desbordamiento de
    memoria](A5_2004_Desbordamiento_de_memoria "wikilink")

Los componentes de aplicación Web hechos en algunos lenguajes que no
validan apropiadamente las entradas de usuario pueden hacer fallar y, en
algunos casos, hacer tomar el control de un proceso. Estos componentes
pueden incluir CGIs, librerias, unidades de disco y componentes del
servidor de la aplicación Web.

  - [A6 2004 Fallas de
    Inyección](A6_2004_Fallas_de_Inyección "wikilink")
    LAs aplicaciones Web pasan parametros cuando acceden a sistemas
    externos o el sistema operativo local. Si un atacante puede
    incrustar un comando malicioso en estos parámetros, el sistema
    externo puede ejecutar esos comandos en nombre de la aplicación Web.

<!-- end list -->

  - [A7 2004 Manejo inapropiado de
    errores](A7_2004_Manejo_inapropiado_de_errores "wikilink")
    Son condiciones de error que ocurren durante la operacion normal que
    no son manejados apropiadamente. Si un atacantes puede provocar que
    ocurran errores que no pueda manejar la aplicación Web, ellos pueden
    obtener información detallada del sistema, niege el servicio, cause
    que fallen los mecanismos de seguridad o haga fallar el servidor.

<!-- end list -->

  - [A8 2004 Almacenamiento
    Inseguro](A8_2004_Almacenamiento_Inseguro "wikilink")
    Las aplicaciones Web frecuentemente usan funciones critográficas
    para proteger la información y cuentas de usuario. Estas funciones y
    el código para integrarlas han probado ser difíciles de codificar,
    resultando frecuentemente en una protección inadecuada.

<!-- end list -->

  - [A9 2004 Negación de servicio de
    aplicación](A9_2004_Negación_de_servicio_de_aplicación "wikilink")
    Los atacantes pueden consumir recursos de la aplicación web a el
    punto de que otros usuarios legítimos no puedan acceder o usar la
    aplicación. Los atacantes pueden tambien bloquear las cuentas de los
    usuarios o incluso causar que la aplicación entera falle.

<!-- end list -->

  - [A10 2004 Manejo inseguro de
    configuración](A10_2004_Manejo_inseguro_de_configuración "wikilink")
    Tener un estándar para la configuración de servidor es crítico para
    asegurar la aplicación Web. Los servidores tienen muchas opciones de
    configuración las cuales afectan la seguridad y no son seguras por
    sí mismas.

<!-- end list -->

  - [Conclusión](Conclusion_OWASP_Top_Ten_Project "wikilink")

## Reconocimientos

A OWASP le gustaría agradecer a los investigadores de Aspect Security
por su liderazgo y contribuciones a el proyecto de las 10 mayores.

el proyecto de las 10 mayores vulnerabilidades de OWASP es dirigido por
Jeff Williams de Aspect security. El puede ser contactado en
jeff.williams 'at' owasp.org.

Traductores Internacionales

  - Ludovic Petit (Fancés)
  - Satoru Takahashi (Japonés)
  - Jeremy Bae (Koreano)
  - Juan Carlos Calderon, Pedro DelReal, Rogelio Morell and Javier
    Muzquiz (Español)
  - Weilin Zhong, Zhendong Yu, Wei Le (Chino)

## Usuarios y Adoptantes

La Comision federal de comercio de E.U (U.S. Federal Trade Commission)
recomienda vehementemente que todas la compañias usen la lista y se
aseguren de que sus socios hagan lo mismo. Además, la agencía de
sistemas de información para la defensa de E.U. (U.S. Defense
Information Systems Agency) ha listado este documento como una de las
prácticas claves que deberían ser parte de el proceso de Certificación
y acreditación para la seguridad de tecnologías de información (DOD
Information Technology Security Certification and Accreditation (C\&A)
Process (DITSCAP))

En el mercado comercial, el [Estándard de la industria de tarjetas de
pago (PCI por sus siglas en
inglés)](http://usa.visa.com/download/business/accepting_visa/ops_risk_management/cisp_PCI_Data_Security_Standard.pdf)
ha adoptado esta lista, y pide (entre otras cosas) que los comerciantes
hagan una revision de seguridad en código para todo su código a la
medida. Ademas, un amprio rango de compañias y agencias en todo el globo
estan tambien usando la lista de las 10 mayores de OWASP, incluyendo:

  - A.G. Edwards
  - Bank of Newport
  - Best Software
  - British Telecom
  - Bureau of Alcohol, Tobacco, and Firearms (ATF)
  - Cboss Internet
  - Cognizant
  - Contra Costa County, CA
  - Corillian Corporation
  - Foundstone Strategic Security
  - IBM Global Services
  - National Australia Bank
  - Norfolk Southern
  - Online Business Systems
  - Predictive Systems
  - Price Waterhouse Coopers
  - Recreational Equipment, Inc. (REI)
  - SSP Solutions
  - Samsung SDS (Korea)
  - Sempra Energy
  - Sprint
  - Sun Microsystems
  - Swiss Federal Institute of Technology
  - Texas Dept of Human Services
  - Zapatec
  - ZipForm
  - ...and many others

Muchas escuelas han adoptado también la lista de las 10 mayores de OWASP
como parte de sus planes de carrera, incluyendo la "Michigan State
University (MSU)", y la "University of California at San Diego (UCSD)".

Muchos proyectos de código abierto han adoptado la lista como parte de
sus auditorias de seguridad, incluyendo:

  - [El Proyecto de código abierto "Plone CMS"](http://plone.org)
    (Administrado por la Fundación Plone)

## Retroalimentación

Por favor dejenos saber como esta usando su organización esta lista.
Incluya su nombre, nombre de la organización, y una brebe descripción de
como usa la lista. Gracias por su apoyo a OWASP\!

Esperamos que se útil la informacion en la lista de las 10 mayores de
OWASP. Por favor, contribuya a el proyecto enviando sus comentarios,
preguntas, y sugerencias a topten@owasp.org. Gracias\!

Para unirse a la lista de distribucion de las 10 mayores o ver los
archivos, por favor visite la [página de
suscripción.](http://lists.owasp.org/mailman/listinfo/owasp-topten)

## Patrocinadores del proyecto

El proyecto de las 10 mayores vulnerabilidades de OWASP es patrocinado
por
[<https://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com)

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP Document](Category:OWASP_Document "wikilink")
[Category:OWASP Download](Category:OWASP_Download "wikilink")