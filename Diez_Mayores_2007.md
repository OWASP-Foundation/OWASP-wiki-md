## Presentación

Bienvenidos a la lista de las 10 mayores vulnerabilidades de OWASP
2007\! Esta edición, totalmente reescrita lista las vulnerabilidades más
serias en aplicaciones web, discute como protegerse de ellas y provee
ligas a mas información. **La lista de las 10 mayores vulnerabilidades
de OWASP ha sido traducida al Español. [De clic
aquí](https://www.owasp.org/images/a/ae/OWASP_Top_10_2007_Spanish.pdf)
para la traducción al español\!**

La lista de las 10 mayores de OWASP para la versión empresarial de Java
esta disponible para bajarla
[aqui](https://www.owasp.org/images/8/89/OWASP_Top_10_2007_for_JEE.pdf)

## Objetivo

**El objetivo principal de la lista de las 10 de OWASP es formar
desarrolladores, diseñadores, arquitectos y organizaciones** sobre las
consecuencias de las vulnerabilidades más comunes en aplicaciones web.
Las lista provee métodos básicos para protegerse contra estas
vulnerabilidades - un gran inicio para su programa de codificación
segura.

**La seguridad no es un evento de una sola vez**. No es suficiente
asegurar su código solo una vez. Para 2008, esta lista cambiará y sin
cambiar una línea de el código de su aplicación, puede ser vulnerable.
Por favor revise el consejo en [Top 10 2007-¿A dondé sigo
Ahora?](Top_10_2007-Where_to_Go_From_Here "wikilink") para mas
información.

**Una iniciativa de codificación segura debe lidiar con todas las etapas
de desarrollo del programa**. Las aplicaciones Web seguras ***solo*** es
posible cuando un SDLC seguro es usado. Los programas seguros desde el
inicio por su diseño y desarrollo. Hay al menos 300 problemas que
afectan la seguridad en general de una aplicación Web. Estos mas de 300
problemas están detallados en la [Guía de
OWASP](http://www.owasp.org/index.php/OWASP_Guide_Project), la cua es
una lectura escencial para cualquiera que desarolle aplicaciones Web en
la actualidad.

**Este documento es el principalmente un documento educativo, no un
standard**. Por favor no adopte este documento como una política o
estándar sin [hablar con nosotros](mailto:owasp@owasp.org) primero\! Si
necesita una política o estandar de codificación segura, OWASP tiene
proyectos de políticas y estándares de seguridad que están en progreso.
Por favor considere unirse o asistir financieramente estos esfuerzos.

## Retroalimentación

|                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Agradecemos a [MITRE](http://www.mitre.org/) por hacer *La distribución de tipos de vulnerabilidades en el [CVE](http://cve.mitre.org/)* disponibles libremente para su uso. El proyecto de la lista de las 10 mayores esta dirijida y patrocinada por [<https://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com). |

Líder de proyecto: Andrew van der Stock (Director ejecutivo, Fundación
OWASP) Co-autores: Jeff Williams (Presidencia, Fundación OWASP), Dave
Wichers (Presidencia de conferencia, Fundación OWASP)

Queremos agradecer a los revisores:

  - Raoul Endres por ayudar a echar a andar la lista de nuevo y por sus
    valiosos comentarios.
  - \[[mailto:coley](mailto:coley)...at...mitre.org Steve
    Christey\](MITRE) por una importante revisión y la adición de los
    datos del MITRE CWE
  - [Jeremiah Grossman](http://jeremiahgrossman.blogspot.com/)
    ([WhiteHat Security](http://www.whitehatsec.com/)) por revisar y
    contribuir con información sobre el éxico (o falla) de la medidas de
    detección automatizadas.
  - [Neil Smithline](http://www.smithline.net/) ([BEA
    Systems](http://www.bea.com/)) por sus comentarios y producir la
    versión Wiki-
  - Sylvan von Stuppe por una revisión ejemplar.
  - Colin Wong, Nigel Evans y Andre Gironda por comentarios enviados por
    correo.

## Conclusión

|                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [A1 - Secuencia de comandos en sitios cruzados (XSS)](Top_10_2007-Secuencia_de_Comandos_en_Sitios_Cruzados_\(XSS\) "wikilink")                               | Las fallas de XSS acurren cuando una aplicación toma la información proveida por el usuario y la envia a un navegador sin validarla primero o codificar el contenido. El XSS permite a los atacantes ejecurar scripts en el navegador de la víctima la cual puede secuestrar la sesión del usuario, modificación de sitios web, la posible introducción de gusanos, etc.                                       |
| [A2 - Inyección de código](Top_10_2007-Fallas_de_Inyección "wikilink")                                                                                       | La fallas de inyección, particularmente la inyección de SQL, son comunes en las aplicaciones Web. La inyección ocurre cuando los datos proveidos por el usuario son enviados a un interprete como parte de un comando o petición. Los datos hostiles del atacante engañan al interprete a ejecutar comandos no intencionados o cambiar los datos.                                                              |
| [A3 - Ejecución maliciosa de archivos](Top_10_2007-Ejecución_de_Ficheros_Malintencionados "wikilink")                                                        | El código vulnerable a inclusión remota de archivos permite a los atacantes incluir código y datos hostiles, resultando en ataques devastadores, como secuestro total del servidor. Los ataques de ejecución maliciosa de archivos afectan a PHP, XML y cualquier marco de trabajo que soporte el manejo de nombres de archivos o permita la interacción con los usuarios mediante el intercambio de archivos. |
| [A4 - Referencia directa e insegura a objetos](Top_10_2007-Referencia_Insegura_y_Directa_a_Objetos "wikilink")                                               | Una referencia directa e insegura a objetos ocurre cuando un desarrollador expone una referencia a una implementación interna de un objeto como unn archivo, un directorio, un registro de BD o una llave, en forma de parámetro de URL o de una forma. Los atacantes pueden manipular esas referencias para acceder a otros objetos sin tener autorización                                                    |
| [A5 - Falsificación de petición en sitios crusados (CSRF)](Top_10_2007-Vulnerabilidades_de_Falsificación_de_Petición_en_Sitios_Cruzados_\(CSRF\) "wikilink") | A CSRF attack forces a logged-on victim's browser to send a pre-authenticated request to a vulnerable web application, which then forces the victim's browser to perform a hostile action to the benefit of the attacker. CSRF can be as powerful as the web application that it attacks.                                                                                                                      |
| [A6 - Revelación de Información y Gestión Incorrecta de Errores](Top_10_2007-Revelación_de_Información_y_Gestión_Incorrecta_de_Errores "wikilink")           | Las aplicaciones pueden (sin intención) revelar información sobre su configuración, funcionalidad interna o violar la privacidad a travez de una variedad de problemas de la aplicación. Los atacantes usan estas debilidades para robar información delicada o conducir ataques mas serios.                                                                                                                   |
| [A7 - Autentificación y gestión de sesiones disfuncional](Top_10_2007-Autenticación_y_Gestión_de_Sesiones_Disfuncional "wikilink")                           | Las credenciales de las cuenta y testigos de sesión son frecuentemente protegidos inadecuadamente. Los atacantes roban contraseñas, llaves o testigos de autneticación para asumir la identidad de otros usuarios.                                                                                                                                                                                             |
| [A8 - Almacenamiento cirptográfico inseguro](Top_10_2007-Almacenamiento_Criptográfico_Inseguro "wikilink")                                                   | Las aplicaciones Web raramente usan funciones criptográdicas apropiadamente para proteger información y credenciales. Los atacantes usan la información mal protegida para hacer robos de identidad y otros crimenes, como fraude con tarjetas de crédito.                                                                                                                                                     |
| [A9 - Comunicación Insegura](Top_10_2007-Comunicaciones_inseguras "wikilink")                                                                                | Las aplicaciones frecuentement falla al cifrar el tráfico de red cuando es necesario proteger comunicaciones delicadas.                                                                                                                                                                                                                                                                                        |
| [A10 - Falla de restricción de acceso a URL](Top_10_2007-Falla_de_restricción_de_acceso_a_URL "wikilink")                                                    | Frecuentemente, una aplicacion solo protege funcionalidad delicada evitando mostrar la ligas o URLs a usuarios no autorizados. Los atacantes pueden usar esta debilidad para acceder y realizar operaciones no autorizadas al acceder a esas URLs directamente.                                                                                                                                                |

'''

<center>

Tabla 1: La 10 mayores vulnerabilidades de OWASP 2007

</center>

'''

Hay muchas páginas en este documento que no están dedicadas a
vulnerabilidades en específico y por lo tanto no están listadas en la
tabla. Aqui hay una lista de ellas.

|                                                                                 |                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Top 10 2007](Top_10_2007 "wikilink")                                           | Ademas de proveer una presentación, y un marcador de la sección de "conclusiones" (esto puede hacerse arrastrando [este enlace](https://www.owasp.org/index.php/Top_10_2007#Summary) a sus favoritos) nos da acceso rápido a el documento completo. |
| [Top 10 2007-Metodología](Top_10_2007-Metodología "wikilink")                   | Una descripción de la metodología usada para selecionar las vulnerabilidades para este documento.                                                                                                                                                   |
| [Top 10 2007-¿A dondé sigo Ahora?](Top_10_2007-¿A_dondé_sigo_Ahora? "wikilink") | Algunas sugerencias sobre como proceder una ves que ha leído este documento.                                                                                                                                                                        |
| [Top 10 2007-Referencias](Top_10_2007-Referencias "wikilink")                   | Recomendaciones para lectura posterior.                                                                                                                                                                                                             |

'''

<center>

Tabla 1a: Paginas en el documento de la *lista de las 10 mayores 2007*
que no son la lista de vulnerabilidades mencionadas arriba.

</center>

'''

## Una nota sobre las diferentes versiones

Mientras que la única versión oficial de la *lista de las 10 mayores
vulnerabilidades de OWASP 2007* es la version en PDF y en inglés, OWASP
ah puesto a su disposición este Wiki que inicialmente contenia el mismo
contenido que el PDF. Pero OWASP espera que cambien con su ayuda. OWASP
promueve el envolvimiento de la comunidad y quiere su ayuda para hacer
la versión Wiki mejor que nunca. Para ayudar a esto han creado un
pequeño [tutorial](Editing:Top_10_2007 "wikilink") para iniciarlo en
este proceso.

## Versiones para bajar

Puede bajar la lista 2007 (versión final) aqui:

  - [(PDF, 930
    kb)](http://www.owasp.org/images/e/e8/OWASP_Top_10_2007.pdf)

<!-- end list -->

  - [(Español
    PDF, 488kb)](https://www.owasp.org/images/a/ae/OWASP_Top_10_2007_Spanish.pdf)

<!-- end list -->

  - [(Francés PDF, 455
    kb)](https://www.owasp.org/images/c/ce/OWASP_Top_10_2007_-_French.pdf)

<!-- end list -->

  - [(Koreano PDF, 768
    kb)](http://www.metasecurity.org/owasp/OWASP_Top_10_2007_Korean.pdf)

<!-- end list -->

  - [(Turco PDF, 718
    kb)](http://csirt.ulakbim.gov.tr/dokumanlar/Ceviri_OWASP_ilk10_2007.pdf)

<!-- end list -->

  - [(Portuguese Brasileño PDF, 329
    kb)](http://www.owasp.org/images/4/42/OWASP_TOP_10_2007_PT-BR.pdf)

<!-- end list -->

  - [OWASP Top 10 para la versión empresarial de Java (PDF, 630
    kb)](https://www.owasp.org/images/8/89/OWASP_Top_10_2007_for_JEE.pdf)

<!-- end list -->

  - Le gustaría tener esta versión en otro idioma? podriamos usar su
    ayuda para traducirla. Contacte a Andrew van der Stock (vanderaj
    ...(@)... owasp.org) para ayudarnos a traducir la lista de las 10
    mayores a otro idioma.