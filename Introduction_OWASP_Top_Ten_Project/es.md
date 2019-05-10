## Presentación

El **proyecto abierto de seguridad en aplicaciones Web** (OWASP por sus
siglas en inglés) ayuda a las organizaciones a entender y mejorar la
seguridad de sus aplicaciones y servicios web.

Esta lista fue creada para guíar a corporaciones y agencias de gobierno
sobre las vulnerabilidades más serias. La seguridad en aplicaciones Web
se ha convertido en un tema candente conforme la compañias compiten para
hacer su contenido y servicios accesibles a traves de la Web. Al mismo
tiempo, los hackers han volcado su atencion a vulnerabilidades comúnes
creadas por los desarrolladores de aplicaciones.

Cuando una organización publica una aplicación Web, invitan al mundo a
enviar peticiones HTTP. Los ataques incrustados en esas peticiones
suelen sobrepasar los cortafuegos, fistos, endurecimientos de plataforma
y sistemas de detección de intrusos sin ser notados ya que estan dentro
de peticiones HTTP legales. Esto afecta incluso a los sitios "seguros",
que usan SSL y solo aceptan las peticiones que llegan a travez de un
tunel cifrado sin escrutinio. **Esto significa que el código de su
aplicacion es parte de su seguridad perimetral**, conforme el número,
tamaño y complejidad de las aplicaciones web se incrementa, asi se
incrementa su exposisión perimetral.

Los problemas de seguridad comentados aqui no son nuevos. De hecho,
algunos han sido bien conocidos por décadas pero por una variedad de
razones, los proyectos de los mayores productores de software siguen
cayendo en estos errores y poniendo en peligro, no solo la seguridad de
sus clientes, sino la seguridad de la internet entera. El proyecto no es
una "bala de plata" para resolver todos estos problemas. Las revisiones
y tecnología de protección cada día están mejorando pero, en el mejor de
los casos, solo pueden manejar un conjuto limitado de problemas.

Para resolver los problemas descritos en este documento, las
organizaciones necesitan cambiar su cultura de desarrollo, formar
productores de software expertos, actualizar sus procesos de desarrollo
de software y usar tecnología cuando sea apropiado.

## Características Generales

**El proyecto de las 10 mayores vulnerabilidades de OWASP es una lista
de vulnerabilidades que requiren inmediata solución.** El código
existente debe ser revisado contra estas vulnerabilidades inmediatamente
ya que dichas fallas estan siendo atacadas activamente por los
atacantes. Los proyectos de desarrollo deben considerar estas
vulnerabilidades en sus documentos de requerimientos y diseño, en las
construcción y en las pruebas de sus aplicaciones para asegurarse que no
han sido introducidas o que han sido eliminadas de forma correcta. Los
supervisores deben incluir presupuesto y tiempo para las actividades de
seguridad en sus aplicaciones para la formación de productores de
software, el desarrollo de una politica de desarrollo seguro, mecanismos
de diseño y desarrollo seguro, pruebas de intrusion y revision de
seguridad en el código fuente.

Exhortamos a las organizaciones a unirse a la creciente lista de
compañias que han **adoptado la lista de las 10 mayores** como el
**estándar** mínimo y se han comprometido a producir aplicaciones Web
que no contienen estas vulnerabilidades.

Hemos escogido presentar la lista en un formato similar al altamente
exitoso **Top 20 del SANS/FBI** de manera que se facilite su uso y
entendimiento. La lista de SANS esta enfocada a las fallas en productos
de red e infraestructura.

Ya que cada sitio Web es único, la lista del OWASP Top 10 esta
organizada alrededor de tipos y categorias de vulnerabilidades que
ocurren frecuentemente en las aplicaciones Web. Estas categorias están
siendo estandarizadas en el proyecto de seguridad en aplicaciones Web de
**OASIS (OASIS Web Application Security (WAS) XML Project)**.

El listado representa el conocimiento combinado de los expertos de
OWASP, cuya experiencia incluye muchos años de trabajo en seguridad en
aplicaciones para gobierno, servicios financieros, farmacéuticos y de
manufactura. Tambien como productores de herramientas y tecnología.

En general, este documento esta diseñado para presentar las
vulnerabilidades mas serias en aplicaciones web. Hay muchos libros y
guías que describen estas vulnerabilidades en mas detalle y proveen
lineamientos sobre como eliminarlas. Tales lineamientos estan en la
lista de guía de OWASP disponible en [1](http://www.owasp.org).

El **Top 10 de OWASP** es un documento en constante progreso. Incluye
instrucciones,ayudas e información adicional útil para corregir estos
tipos de fallas de seguridad. Actualizamos la lista y las instrucciones
conforme nuevas amenazas críticas o nuevos métodos más convenientes y
actuales sean identificados.

Le damos la bienvenida y esperamos su retroalimentación en el camino.
Este es un documento de consenso en la comunidad - Su experiencias al
combatir atacantes y eliminar vulnerabilidades pueden ayudar a otros que
vienen despues de usted. Por favor envie sugerencias via correo a
topten@owasp.org con el asunto "OWASP Top Ten Comments.”

__NOEDITSECTION__

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")