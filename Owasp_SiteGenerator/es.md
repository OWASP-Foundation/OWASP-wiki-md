<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

**Versión actual: 0.80 (Beta publica)**

**Patrocinador: Foundstone y [SPI
Dynamics](http://64.233.183.104/search?q=cache:3KOC8rvncLQJ:www.spydynamics.com/news/pr/pr30707.html+SPIDynamics+OSG&hl=en&ct=clnk&cd=1&gl=uk&client=firefox-a)
y OWASP Spring of Code 2007**

[OWASP Site Generator's SpoC 007 Pagina de
progreso](SpoC_007_-_OWASP_Site_Generator "wikilink") (en ingles)

## Descripción

El generador de sitios OWASP (SiteGenerator) permite la creación de
sitios Web dinámicos basados en archivos XML y vulnerabilidades
predefinidas (algunas simples, algunas complejas) cubriendo los
lenguajes .Net y arquitecturas de desarrollo Web (por ejemplo,
navegación: Html, Javascript, Flash, Java, etc...).

## Usos

  - Evaluación de scanners de seguridad de aplicaciones Web
  - Evaluación de cortafuegos de aplicación Web
  - Entrenamiento de desarrollador
  - Honeypots Web
  - Torneos (o evaluaciones) de hacking en aplicaciones Web
  - Cualquier cosa que a su mente se le ocurra\!

## Descargas

  - Instalador:
    [Instalador](http://downloads.sourceforge.net/owasp/OSG_v0.80.msi?use_mirror=easynews)
    (Versión 0.80) – Actualizado el 03/05/2007
  - Código fuente:
    [Current_SiteGenerator_Source.zip](http://owasp.cvs.sourceforge.net/*checkout*/owasp/dotnet/SiteGenerator/SiteGenerator.zip)
    (Versión 0.80)

## Accesando a SVN para SiteGenerator

  - Una forma es explorar el SVN en línea en [Árbol fuente de
    SiteGenerator](http://owasp-code-central.googlecode.com/svn/trunk/labs/SiteGenerator/)
  - Otra forma es configurar su cliente SVN para descargar el código
    fuente localmente.

## Instalación y notas de configuración

  - Antes de instalar la parte del sitio Web por favor confirme lo
    siguiente.
      - Hay un conjunto de aplicaciones (“application pool”) que esta
        configurada para ejecutarse bajo la cuenta del Sistema
      - Un sitio Web que esta apuntando a donde quiere que la parte Web
        de SiteGenerator sea instalada
      - Configure el sitio Web para ejecutar Asp.Net 2.0
      - Asegúrese de que hay una aplicación para ese sitio Web y esta
        puesta en la piscina de aplicaciones creada en el primer paso
      - Agregue un “IIS wildcard Application Mapping” (accesible a
        través de Home Directory -\> Configuration) a
        C:\\WINDOWS\\Microsoft.NET\\Framework\\v2.0.50727\\aspnet_isapi.dll
        y desmarque 'Verify that file exists'
          - Nota: En Windows XP el botón OK tal vez aparezca como
            deshabilitado. Necesitara buscar el archivo y luego
            seleccionar la ubicación y también poner un punto delante
            del asterisco (es decir, .\*) para que se habilite el botón
            OK
      - Asegúrese que Default.htm es uno de los archivos incluidos en la
        lista de documentos por omisión (en la pestaña 'Documents')
      - Configure la dirección IP del sitio Web a 127.0.0.1, y haga clic
        en el botón “Advanced” para agregar un nuevo mapeo de cabecera
        de sitio
  - Ejecutar el instalador
  - Apunte el documento raíz del sito Web al directorio de instalación
    \\sitegenerator_contentpages y asegúrese que el usuario de IIS
    tenga los permisos correctos
  - Haga clic en la liga de SiteGenerator que fue colocada en su
    escritorio

Si todo va bien ahora puede explorar su sitio local y ver la pagina por
omisión de SiteGenerator. Si ve una pagina en blanco, intente
http://\<sitio\>/Default.htm (tal vez este obteniendo una versión en
cache de http://\<SITE NAME\>)

Note que las vulnerabilidades de inyección SQL esperan que usted tenga
la ultima versión de HacmeBank (v2.0) instalada en su maquina.

## Introducción a SiteGenerator

  - Esta herramienta ha sido patrocinada por Foundstone, PERO (y es un
    gran pero) esta siendo liberada bajo licencia Owasp .Net Project y
    una licencia Open Source. Así que felicidades a Foundstone por hacer
    esto y espero que obtengan buena exposición de ello.

<!-- end list -->

  - El objetivo principal de la herramienta es crear sitios Web
    dinámicos basada en archivos XML, los cuales se ‘enlazaran’ a una
    base de datos que contienen cientos de vulnerabilidades diferentes
    (algunas simples de detectar/explotar, algunas mas difíciles)
    cubriendo múltiples lenguajes y arquitecturas de desarrollo Web (por
    ejemplo navegación: Html, JavaScript, Flash, Java, etc...)

<!-- end list -->

  - Hay muchas formas en las que esta herramienta puede ser usada, aquí
    hay solo un par de ideas iniciales:
      - Como herramienta de entrenamiento, ya que permite la creación de
        múltiples sitios Web con múltiples variaciones de
        vulnerabilidades
      - Como un Honeypot de aplicación Web (ya que somos capaces de
        crear sitios Web dinámicos (falsos) y rastrear/monitorear en
        tiempo real todas las peticiones hechas)
      - Como un campo de prueba para nuevos tipos de vulnerabilidades
        descubiertas y sus exploits
      - Como punto de referencia para scanners de seguridad Web

<!-- end list -->

  - El punto de referencia y pruebas para scanners de seguridad Web es
    la aplicación mas obvia a corto termino para esta herramienta, pero
    creo que como vaya evolucionando se probará que las otras son igual
    (si no es que mas) valiosas.

<!-- end list -->

  - En el asunto del scanner de seguridad Web:
      - Mi principal esperanza es que las compañías de scanners de
        seguridad Web vean esta herramienta como una oportunidad y
        trabajen con el proyecto Owasp .Net (y otros grupos que quieran
        ser involucrados) en una forma productiva y constructiva.
      - Aunque en el corto plazo algunos scanners de seguridad Web
        podrían tener algunos malos resultados (bueno, al menos
        comparados con lo que publica su mercadotecnia :) en el plazo
        medio, mientras adaptan y mejoran sus técnicas de escaneo, todos
        serán beneficiados
      - Uno de los objetivos básicos de la herramienta (pensando acerca
        de punto de referencia para scanners de seguridad Web) es ser
        capaz de crear métricas reales y medibles. Por ejemplo:
          - Scanner X fue capaz de detectar 65% de las vulnerabilidades
            mientras que el Scanner Y fue capaz de detectar el 90%
          - Scanner X hizo 10000 peticiones para detectar ese 65% (en un
            periodo de 16h) mientas que el scanner Y hizo 4000
            Peticiones (en un periodo de 10h)
              - 20% de los resultados del scanner X fueron falsos
                positivos, mientas que el scanner Y tuvo 50% de falsos
                positivos
              - Scanner X fue capaz d tratar con la navegación Html y
                JavaScript, el Scanner Y fue capaz de tratar con Html,
                JavaScript y Flash, y ninguno fue capaz de manejar
                sistemas de navegación basados en Java
              - Scanner X no es capaz de ir mas allá de 40 niveles de
                profundidad, el Scanner Y es capaz de ir mínimo a 100
                niveles de profundidad
              - etc, etc, etc
      - Habrá dos tipos principales de pruebas que pueden llevarse a
        cabo en el corto plazo:
          - Proporcionar las ligas a todos los diferentes tipos de
            vulnerabilidades existentes en la base de datos, y ver
            cuantas puede identificar correctamente el scanner, y
          - Cuando múltiples tipos de arquitecturas Web y técnicas de
            navegación son usadas, cuantas vulnerabilidades puede
            detectar el scanner?
      - Para poder probar (y mejorar la herramienta) quiero tomar esta
        oportunidad para pedir a los scanners de seguridad de
        aplicaciones Web que se suscriban a esta lista para dar al
        proyecto Owasp .Net una licencia temporal para su producto para
        que la podamos usar durante el desarrollo y durante algún punto
        de referencia básico que tal vez hagamos (y NO, no firmare un
        NDA que no me permita publicar la información recolectada, de
        hecho no firmare ningún NDA con ninguna compañía de scanners de
        seguridad de aplicación Web)
      - Nótese que en este momento, yo (Dinis) no tengo planes de hacer
        un ejercicio completo de punto de referencia ya que no tengo el
        tiempo requerido, pero conozco al menos un grupo de consultores
        de seguridad experimentados que esta empezando tal proyecto (y
        los estaré apoyando). Si alguien mas esta interesado en hacer un
        proyecto similar de puntos de referencia por favor contácteme
        directamente

<!-- end list -->

  - En cuanto a la forma en la que la herramienta funciona, aquí hay una
    breve descripción técnica:

Hay dos componentes principales: Un servidor Web (el cual puede ser IIS
o un servidor Web personalizado) y una GUI (interfaz grafica de usuario)
(escrita en C\# 2.0). La GUI es responsable de manejar todos los enlaces
(de la petición virtual a las paginas reales en disco). Los dos
componentes principales se comunican a través de tcp en el puerto 4,000,
la GUI escucha por peticiones de un servidor Web y después regresa la
respuesta al servidor Web

La versión actual esta forzada a IIS, aunque en el código hay soporte
para usar un servidor Web personalizado para.Net. Esta versión de IIS
usa un HttpHander para capturar todas la peticiones y comunicarse con la
(llamada SiteGeneratorGUI)

Los sitios Web dinámicos están definidos por archivos XML como este (los
cuales son editados en la GUI usando WYSIWYG Altova Authentic Browser
Object (los archivos SPS fueron creados con la aplicación Altova's
StyleVision)):

<?xml versión="1.0" encoding="utf-8" ?>

`  `<SiteGenerator name="SiteGenerator Demo" xmlns:ipo="<nowiki>http://www.altova.com/IPO</nowiki>"
    ns="<nowiki>http://www.xmlspy.com/schemas/orgchart</nowiki>" xmlns:xsi="<nowiki>http://www.w3.org/2001/XMLSchema-instance</nowiki>">
`         `<site>
`             `<folder name="">
`                `<file mappedTo="aspx/Default.aspx" name="HelloWorld.aspx" />
`                `<folder name="htm" />
`                `<folder name="aspx">
`                    `<file mappedTo="aspx/pages.htm" name="pages.htm" />
`                    `<file mappedTo="aspx/xss.aspx" name="xss.aspx" />
`                    `<file mappedTo="aspx/SqlInjection_Easy.aspx" name="SqlInjection.aspx" />
`                    `<file mappedTo="aspx/SqlInjection_Hard.aspx" name="SqlInjection2.aspx" />
`                `</folder>
`                `<folder name="flash">
`                     `<file mappedTo="flash/cromas_xml.swf" name="cromas_xml.swf" />
`                     `<file mappedTo="flash/cromas_xml.htm" name="menu.htm" />
`                     `<file mappedTo="/flash/cromas_menu.xml" name="cromas_menu.xml" />
`                `</folder>
`             `</folder>
`        `</site>
`  `</SiteGenerator>

SiteGeneratorGUI.exe y IIS enlazaran el nombre virtual "HelloWorld.aspx"
al archivo en disco "aspx/Default.aspx" . Por ejemplo:

<http://localhost/HelloWorld.aspx> --\> F:\\Owasp
SiteGenerator\\SiteGenerator_ContentPages\\aspx\\Default.aspx

Así que para crear nuevos sitios Web todo lo que necesita hacer es crear
un nuevo archivo XML

Luego para crear un nuevo tipo de vulnerabilidades, todo lo que necesita
hacer es crear una pagina Aspx y enlazarla al archivo XML

## Como usar SiteGenerator

SiteGenerator contiene cuatro diferentes pantallas que pueden ser
usadas, son ampliamente explicadas mas adelante. En todas las pantallas
vera un panel inferior, este contiene toda la información que va del
sitio Web al cliente. Haciendo clic en "Clear Received Data" limpiara el
área de texto inferior y la información encontrada en la pestaña de
registro de transformación de archivo.

'''pestaña para Editar / Crear sitios Web dinámicos '''

![Image:sg_maintain_websites_ss.jpg](sg_maintain_websites_ss.jpg
"Image:sg_maintain_websites_ss.jpg")

Esta área permitirá a los usuarios crear un sitio Web básico que podría
ser usado. También puede eliminar un sitio Web y modificarlo usando el
widget parecido a Word.

Seleccione la ruta raíz para el sitio "/", puede elegir la pagina por
omisión, esta puede ser otra pagina que usted ha enlazado previamente o
una ruta especifica a un archivo.

*' Registro de transformaciones de archivo*'

![Image:sg_file_transformations_tab.jpg](sg_file_transformations_tab.jpg
"Image:sg_file_transformations_tab.jpg")

Esta pestaña le permite al usuario ver como están trabajando las
transformaciones. Por ejemplo, usted podría asegurarse que el nuevo
enlace para f00.aspx en realidad fue convertido a /test123/test.aspx.

**pestaña de navegador Web**

![Image:sg_webrowser_tab_ss.jpg](sg_webrowser_tab_ss.jpg
"Image:sg_webrowser_tab_ss.jpg")

Esta pestaña le permitirá al usuario explorar el sitio Web generado en
lugar de usar un navegador normal.

**pestaña de creador de sitios Web**

![Image:Sg_website_creator_tab_ss.jpg](Sg_website_creator_tab_ss.jpg
"Image:Sg_website_creator_tab_ss.jpg")

Esta pestaña permite al usuario crear inicialmente los archivos para un
sitio Web.

## Notas de desarrollo

[OSG_Dev_Notes](OSG_Dev_Notes "wikilink")

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")