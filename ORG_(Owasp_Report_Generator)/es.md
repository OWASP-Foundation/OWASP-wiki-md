El ORG (Generador de reportes OWASP) es una herramienta para consultores
de seguridad que soporta la documentación y reporteo de vulnerabilidades
de seguridad descubiertas durante auditorias de seguridad.

El líder del proyecto es [Dinis Cruz](User:Dinis.cruz "wikilink") con
fuertes contribuciones de [Mike de Libero](User:medelibero "wikilink").
Mike es actualmente patrocinado bajo el OWASP Autumn of Code 2006 para
trabajar en ORG.

## Descargas

La ultima versión del inhalador de ORG puede ser encontrado en
(actualizado el 1/15/2007) [Instalador del generador de
reportes](http://sourceforge.net/project/downloading.php?group_id=64424&use_mirror=osdn&filename=ORG_v0.88.msi)

El código fuente de la ultima versión estable puede ser descargado de
aquí (actualizado el 11/1/2006): [Fuente del generador de
reportes](http://prdownloads.sourceforge.net/owasp/ReportGenerator.zip)

El proyecto esta en desarrollo activo y la ultima versión puede
obtenerse de [Google
SVN](http://owasp-code-central.googlecode.com/svn/trunk/labs/ReportGenerator)

**Instrucciones para usar el archivo zip**

1\) Descomprimir los archivos

2\) Ejecutar regAuthenticPlugin.bat para registrar AuthenticPlugin

3\) Abrir la solución en VS.Net 2k5. Puede usar cualquier versión de VS
pero la versión principal usada para el desarrollo es la versión
express.

4\) Es mas que probable que necesite modificar el área de referencias
para usar los archivos locales para
\[IxInterop|AxInterop\].XMLSPYPLUGIN.

5\) Luego trate de compilar y debería estar listo. Si no es así,
contacte a Mike y trabajaremos con usted para arreglarlo y así podamos
ajustar este proceso.

## Desarrollo de ORG

La actual versión bajo desarrollo es v0.86 y puede ver el registro de
cambios aquí: [ORG (Owasp Report Generator) - Change
Log](ORG_\(Owasp_Report_Generator\)_-_Change_Log "wikilink") (en ingles)

Las actividades pendientes están aquí: [ORG (Owasp Report Generator) -
To Do](ORG_\(Owasp_Report_Generator\)_-_To_Do "wikilink") (en ingles)

## Configurando una auditoria

**Paso 1)** Cree un perfil para usarlo en su computadora. Puede hacer
esto en la primer pantalla que se encontrara al ejecutar ORG.

![Image:Profile_ss.jpg](Profile_ss.jpg "Image:Profile_ss.jpg")

Una vez que la información haya sido introducida haga clic en “Start Pen
Test Reporter” y esta listo para empezar a agregar nuevos proyectos.

**Paso 2)** El siguiente paso es crear un proyecto. Con la ventana de
“Current and Archived Projects” abierta asegúrese que la pestaña de
metadatos del proyecto este seleccionada. De ahí, en la esquina de abajo
a la izquierda vera una área para escribir un nuevo proyecto y luego
haga clic en “Add”. Entonces vera una ventana como la siguiente.

![Image:Project_setup_ss.jpg](Project_setup_ss.jpg
"Image:Project_setup_ss.jpg")

Ahora puede escribir la información pertinente acerca de su proyecto.
Después de eso, usted esta listo para identificar sus objetivos y
empezar el ataque (es decir. la parte divertida\!).

**Paso 3)** A continuación haga clic en la pestaña de objetivos, esto le
permitirá definir los objetivos de su auditoria. A continuación hay una
pantalla de un ejemplo de un objetivo durante una auditoria.

![Image:Org_target_ss.jpg](Org_target_ss.jpg
"Image:Org_target_ss.jpg")

El área de arriba le da la logística de las cosas del objetivo, como
nombre, IP(s), el tipo de objetivo y nombres DNS comunes. El área de
abajo le permite poner archivos relacionados al objetivo.

También puede importar objetivos de un escaneo de NMap si usa la opción
de archivo xml de salida. Para importar objetivos haga clic en el botón
“Import Targets” y seleccione el escaneo salvado.

**Paso 4)** Después de definir los objetivos a atacar, usted puede
especificar las tareas individuales que desea realizar en los objetivos.
Una pantalla como la siguiente debería ser mostrada

![Image:Org_target_tasks_ss.jpg](Org_target_tasks_ss.jpg
"Image:Org_target_tasks_ss.jpg")

Usando esta pantalla usted puede administrar las tareas que necesitan
ser realizadas para una auditoria, cosas como recolección de
información, auditoria de código fuente y otras tareas que normalmente
se realizan durante una auditoria de seguridad. Puede especificar el
estado de cada tarea con el menú desplegable en la columna de estado.

Ahora tenemos toda la información inicial, pero ahora necesitamos una
forma de hacer saber a nuestros clientes lo que hemos encontrado, ahí es
donde la pestaña de hallazgos (“findings”) entra en juego.

## Registrando los hallazgos de la auditoria

Durante la auditoria usted puede registrar todos sus hallazgos usando la
pestaña de hallazgos (“findings”) en la forma de proyectos. Todos los
hallazgos deben estar asociados a un objetivo. Un ejemplo de una ventana
de hallazgos se muestra a continuación. Estos hallazgos serán agregados
después a los reportes que entregara a sus clientes.

![Image:Org_findings_ss.jpg](Org_findings_ss.jpg
"Image:Org_findings_ss.jpg")

Puede agregar pantallas en el área de detalles adicionales de la
pantalla de hallazgos. Para crear hallazgos use el área de “Add
Finding”. Esto le dará una pizarra en blanco e inicialmente usa el
modo simple.

Puede cambiar la plantilla para el editor usando el menú etiquetado como
“Editor Template To Use”. Hay otras dos opciones además del modo simple,
las cuales son: Autentico – Modo todos los campos y explorador de
Windows. El modo todos los campos le permite especificar información mas
detallada. Mientras que el modo explorador de Windows le permite agregar
otros artefactos relacionados a este hallazgo, como extractos de código,
código PoC, etc…

Después de que hayamos encontrado todos los agujeros en nuestros
objetivos necesitamos reportarlos a nuestros clientes.

## Reportando nuestros hallazgos

**Paso 1)** Haga clic en la pestaña “Report Contents” y llene la
información ahí. Esto será usado después para el resumen ejecutivo y
otros reportes que necesitan ejecutarse. Abajo esta una pantalla de
ejemplo de los contenidos del reporte llenados.

![Image:Org_report_contents_tab_ss.jpg](Org_report_contents_tab_ss.jpg
"Image:Org_report_contents_tab_ss.jpg")

Haga clic en ”Save Report Contents” y estamos listos para el siguiente
paso, generar un reporte.

**Paso 2)** La primer cosa que hay que hacer es hacer clic en la pestaña
“Report Pdf”. Seleccione el xslt que desea usar para el reporte y luego
seleccione “FOP” con el que se desea crear el reporte. Después haga clic
en “Create report files using”. Después de presionar el botón, un
pequeño lector PDF se mostrara en la forma. Entonces puede guardar el
reporte a dondequiera que desee. Una pantalla de ejemplo se muestra a
continuación.

![Image:Org_pdf_report_ss.jpg](Org_pdf_report_ss.jpg
"Image:Org_pdf_report_ss.jpg")

La otra forma para crear reportes es presionar el botón de reportes
hasta arriba. Vera una pantalla como la que esta abajo.

![Image:Org_reports_ss.jpg](Org_reports_ss.jpg
"Image:Org_reports_ss.jpg")

## Agregando nuevas entradas en los menús desplegables

Un usuario tiene la habilidad para modificar los valores en los menús
desplegables en los objetivos, hallazgos, detalles del proyecto y tareas
del objetivo modificando cualquiera de los archivos sps en
<Application_Path>/VulnReport_Files/sps/.

## Desarrolladores activos de ORG

  - [ORG (Owasp Report Generator) - Mike de
    Libero](ORG_\(Owasp_Report_Generator\)_-_Mike_de_Libero "wikilink")
  - [ORG (Owasp Report Generator) - Dinis
    Cruz](ORG_\(Owasp_Report_Generator\)_-_Dinis_Cruz "wikilink")

Otros relacionados [Descargas de proyectos .NET
OWASP](https://sourceforge.net/project/showfiles.php?group_id=64424&package_id=105632)
(en ingles)

## Construyendo el instalador

ORG es construido usando el instalador WiX
[1](http://wix.sourceforge.net/). La suposición es que el folder donde
están las bibliotecas WiX esta en su ruta de búsqueda.

  - Prepare un directorio como el de la pantalla de abajo
      - **Nota** los archivos siguientes pueden ser encontrados en el
        Google SVN: BuildInstaller.bat, FOP.zip.txt,
        regAuthenticPlugin.bat, ORG_v0.88.wxs,
        ORG_CONFIG_FILEs.zip.txt, AuthenticPlugin.zip.txt,
        AxInterop.PdfLib.dll, AxInterop.SHDocVw.dll,
        AxInterop.XMLSPYPLUGINLib.dll, ICSharpCode.TextEditor.dll,
        ICSharpCode.TextEditor.dll, Interop.SHDocVw.dll,
        Interop.XMLSPYPLUGINLib.dll, SharpZipLib.dll

![Image:Org_installer_files_ss.gif](Org_installer_files_ss.gif
"Image:Org_installer_files_ss.gif")

  - Ejecute el script BuildInstaller.bat

Cuando una nueva versión del instalador necesita ser construida el ID
para el elemento del producto necesita ser reemplazado junto con la
información de la versión.

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")