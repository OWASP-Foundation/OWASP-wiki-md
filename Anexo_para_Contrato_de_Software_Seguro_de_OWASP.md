**ANEXO DE CONTRATO PARA DESAROLLO DE SOFTWARE SEGURO**

` ADVERTENCIA: ESTE DOCUMENTO DEBE SER CONSIDERADO COMO UNA GUÍA SOLAMENTE.`
` OWASP RECOMIENDA VEHEMENTEMENTE QUE CONSULTE UN ABOGADO CALIFICADO`
` PARA AYUDARLE A NEGOCIAR UN CONTRATO DE SOFTWARE`
` `

## Introducción

Este anexo de contrato pretende ayudar a los proveedores de software y
sus clientes a negociar y capturar importantes términos y condiciones
contractuales relacionadas a la seguridad en el Software a ser
desarrollado o entregado. La razon para este proyecto es que la mayoría
de los contratos no mencionan estos temas, y las partes frecuentamente
tienen puntos de vista dramaticamente diferentes a lo que en ralidad fue
acordado. Creemos que articular claramente estos términos es la mejor
manera de asegurarse que ambas partes pueden hacer desiciones informadas
sobre como proceder.

`"La seguridad del software comercial mejorará cuando el mercado demande mejor seguridad.`
`Al menos, cada petición para propuestas de software debería pedir a los vendedores `
`detallar como van ellos a probar sus productos para encotrar vulnerabilidades de`
`seguridad. Este paso empezará convenciendo a los vendedores de software empaquetado`
`y proveedores externos que las compañias valoran la seguridad."`

\-- John Pescatore, Director de investiagacion con Gartner

`Pedimos a los clientes y proveedores que usen este documento como un marco para discutir`
`espectativas y negociar responsabilidades. Este anexo se creó para ser añadido a un`
`contrato de desarrollo de software. Estos términos son negociables, significa que ellos`
`pueden y deben ser discutidos por el cliente y el proveedor.`

## SOBRE EL PROYECTO

Este documento fue creado por la fundación OWASP (Open Web Application
Security Project por sus siglas en Inglés), una organización sin animo
de lucro con el objetivo de crear herramientas y documentación, gratuita
y abierta para asegurar software. Para facilitar su uso en contratación
privada, este documento es de dominio publico. Puede encontrar detalles
adicionales sobre este proyecto en
<http://www.owasp.org/index.php/OWASP_Legal_Project>. Son Bienvenidos
comentarios de ambos, productores y consumidores de software, asi como
de la comunidad legal.

OWASP reconoce gratamente la contribución especial de [Aspect
Security](http://www.aspectsecurity.com) por su rol en la investigación
y preparación de este documento.

## OBJECIONES

Las siguientes páginas cubren algunas objeciones que escuchamos
frecuentemente sobre usar este lenguaje en contratos de desarrollo de
software:

### PERO NO TODOS LOS TÉRMINOS SON CORRECTOS PARA NOSOTROS…

Este documento debe ser considerado un punto de inicio para su contrato.
Puede que no le gusten todas las actividades, o puede querer proponer
mas. Puede querer asignar responsabilidades de manera diferente. Este
documento no pretende capturar exactamente las necesidades de todos los
clientes y proveedores de software. Pretende proveer un marco para
discutir temas clave, importantes para asegurarse que el software se
cree de forma segura. Despues de que tengan una discusión sobre
seguridad y alcancen un acuerdo. Puede ajustar el convenio para que
concuerde con el contrato.

### PERO, ¿QUIEN DEBE PAGAR POR ESTAS ACTIVIDADES?…

Este contrato no es sobre poner mas peso al desarollo de software. La
pregunta no es sobre si hay costos asociados con seguridad (por supuesto
que hay). La pregunta correcta es qué actividades deberían hacerse por
ambas partes para minimizar costos, y cuando deberían ocurrir.

Este anexo no menciona (intensionalmente) sobre el detalle de quién
debería pagar por la actividades descritas. Mientras muchas de estas
actividades deben estar pasando ya, y son esperadas por muchos clientes,
ellas no estan practicadas regularmente en la industria del software. La
cuestion de quién paga (y cuándo) debe ser parte de la negociación.

Calcular el costo de la seguridad es muy difícil. Auque hay costos
asociados con realizar actividades de seguridad, hay también costos
importantes asociados con ignorar estas actividades. Estamos convencidos
el mejor costo-beneficio para desarrollar software es reducir la
probabilidad de que fallas de seguridad sean introducidas y minimzar el
tiempo entre introducir una falla y arreglarla.

Una distición importante a hacer cuando calculamos costos es entre
construir mecanismos de seguridad y las actividades para asegurarse que
esos mecanismos sean correctos y efectivos. Intentar agregar mecanismoa
al final de el ciclo de desarrollo puede causar serios problemas de
diseño e incrementará el costo dramáticamente. Este convenio promueve
decisiones sobre mecanismos para minimizar estos costos. Similarmente,
esperar hasta justo antes de la puesta en producción para hacer
actividades de aseguramiento, tales como revisión de código y pruebas de
intrusión, tambien incrementaría los costos dramaticamente. Creemos que
el mejor costo-beneficio para ganar certeza es poner un nivel constante
de esfuerzo en el aseguramiento a través del ciclo de desarrollo.

### PERO EL NIVEL DE RIGOR ESTA INCORRECTO….

Este convenio asume que el software que esta siendo desarrollado es
razonablemente importante para una empresa grande o agencia de gobierno.
Hemos seleccionado un "nivel de rigor" para el convenio que es
alcanzable por la mayoria de las organizaciones proveedoras de software,
e identificaría y manejaría los riesgos más comunes.

Sin embargo, para el software que va a ser usado en aplicaciones
críticas, como aplicaciones médicas, financieras o relacionadas con el
ejército. Puede querer incrementar el nivel de rigor. Puede querer
agregar revisiones, documentación y actividades adicionales de prueba.
Puede querer mejorar el proceso de encontrar, diagnosticar y remediar
vulnerabilidades. Para aplicaciones menos sensibles, puede desear
reducir o remover actividades.

### PERO NOSOTROS NO PODEMOS ACEPTAR TANTO RIESGO…

Este convenio pretende facilitar la discusión sobre quién tomaría el
riesgo por las vulnerabilidades de seguridad en el software. Por un lado
del espectro, el cliente podría tomar todo el riesgo y el proveedor
podría entregar código con muchas vulnerabilidades. Por el otro
extremo, el proveedor podría tomar todo el riesgo y asumir la
responsabilidad de entregar código perfecto. Ambos extremos son
irrealizables.

Actualmente, en este convenio, el proveedor toma el riesgo por problemas
que sean descubiertos en los requerimientos o deben ser cubiertos por
esfuerzos razonables en pruebas. Pero la remediación de "nuevos"
problemas de seguridad tendría que ser pagado por el cliente. Creemos
que este es un equilibrio funcional, ya que limita el riesgo adquirido
por el proveedor y promueve obtener requerimientos de seguridad por
anticipado. Pero hay muchas otras posibles soluciones a este problema.
Por favor, dejenos saber si tiene sugerencias alternas, podriamos
incluirlas en versiones futuras de este documento.

Note que la discusión aqui solo cubre el riesgo asociado con arreglar
las vulnerabilidades de seguridad en el código, y no incluye los costos
asociados con recuperarse de incidentes de seguridad relacionados con
explotar cualquiera de esas vulnerabilidades. Estamos interesados en las
mejores prácticas en esta area.

### PERO COMO PODEMOS ASEGURAR CÓDIGO DE TERCEROS…

Casi todos los proyectos de sofware tienen una cantidad importante de
código de terceros como librerias, frameworks y productos. Desde la
perspectiva de seguridad, este código es tan importante como el código
desarrollado a la medida para su proyecto. Creemos que la
responsabilidad de garantizar la seguridad de este código es llevada
mejor por el proveedor, aunque ellos podrían no tener toda la capacidad
para garantizar la seguridad por ellos mismos. Sin embargo, la seguridad
puede ser parte de el la desición de "construir o comprar", y esta
parece ser la mejor manera de promoverla.

El proveedor, por supuesto, tiene la opción de pasar la responsabilidad
al proveedor del software de terceros. El desarrollador puede también
analizar el código de terceros por él mismo o contratar expertos en
seguridad para analizarlo por él.

### PERO PORQUE DEBO PASAR POR TODO ESTE PROBLEMA…

En última instancia, creemos que no hay alternativa para hacer de la
seguridad una parte de el proceso de contratación de software.
Actualmente, creemos que hay serios malentendidos sobre la seguridad del
código que esta siendo desarrollado bajo muchos contratos de desarrollo
de software. Esto puede solamente llevar a una cara litigación y a
desiciones hechas por individuos con poca experiencia y entendimiento
sobre software. Lea el [Caso de estudio hipotético sobre contratación de
software
seguro](Secure_software_contracting_hypothetical_case_study "wikilink")
para una discusión completa de este problema.

Hay muchos beneficios al trabajar con este convenio. El principal es que
pondrá claras las expectativas entre las partes involucradas. En algunos
casos ayudará a evitar demandas cuando problemas de seguridad difíciles
aparecen en el software. Tambien, estas son las mismas actividades
requeridas por muchas razónes legales y de conformidad con
estándares/leyes.

### PERO ES MUY DIFÍCIL PRODUCIR TODA ESTA DOCUMENTACIÓN…

OWASP no promueve la documentación por la simpre documentación. Este
convenio está enfocado en promover la calidad, no la cantidad. Creemos
que puede ser posible (en algunos proyectos) cumplir con este contrato
con una pequeña evaluación de riesgo, algunas páginas de requerimientos,
un pequeño documento de diseño de seguridad, un plan de pruebas, y
algunos resultados de pruebas.

El objetivo de esta documentación es simplemente asegurar, en cada etapa
del desarrollo de software, que se ha puesto la atención apropiada en la
seguridad. Un beneficio adicional es que esta documentación puede ser
recolectada en conjunto para formar un "paquete de certificación" que
básicamente esboce el argumento de porque deberiamos confiar que el
software hará lo que dice.

## ANEXO DE CONTRATO

### 1\. INTRODUCCIÓN

Esta anexo esta hecho para _____________________
("convenio") entre el Cliente y el proveedor. Tanto el Cliente como el
proveedor acuerdan maximisar la seguridad del software de acuerdo a los
siguientes términos.

### 2\. FILOSOFÍA

Esta anexo pretende aclarar los derechos y obligaciones relacionados a
seguridad de todas las partes en una relacion de desarrollo de software.
Al mayor nivel, las partes acuerdan que:

  - (a) Las desiciones de seguridad estarán basadas en el riesgo : Las
    desciciones sobre la seguridad seran tomadas en conunto por el
    cliente y el proveedor basandose en un firme entendimiento de el
    riesgo involucrado.

<!-- end list -->

  - (b) Las actividades de seguridad estarán balanceadas : El esfurzo de
    seguridad será distribuido equitativamente a través de todo el ciclo
    de desarollo de software.

<!-- end list -->

  - (c) Las actividades de seguridad estarán integradas : Todas las
    actividades y documentación discutidas aqui pueden y deben ser
    integradas dentro del ciclo de desarrollo de software del proveedor
    y no mantenerse separadas de el resto del proyecto. Nada en este
    anexo implica algún processo de desarrollo de software en
    particular.

<!-- end list -->

  - (d) Se esperan vulnerabilidades : Todo software contiene defectos, y
    algunos de estos crearan problemas de seguridad. Ambos, cliente y
    proveedor se esforzará para identificar las vulnerabilidades tan
    pronto como sea posible en el ciclo de desarrollo.

<!-- end list -->

  - (e) La información sobre seguridad será comunicada por completo :
    Toda la información relevante para la seguridad se compartirá entre
    el cliente y el proveedor inmediatamente y completamente.

<!-- end list -->

  - (f) Se requerirá solo documentacion de seguridad necesaria : La
    documentación de seguridad no necesita ser demasiado amplia para
    describir claramente el diseño de seguridad, análisis de riesgo y
    problemas.

### 3\. ACTIVIDADES EN EL CICLO DE DESARROLLO

  - (a) Entendimiento del Riesgo 
    El proveedor y el cliente acuerdan trabajar juntos para entender y
    documentar los riesgos que enfrenta la aplicacion. Este esfuerzo
    debe identificar los riesgos clave para los activos y funciones
    importantes que provee la aplicación. Cada uno de los temas listados
    en la sección de requerimientos debe ser considerado.

<!-- end list -->

  - (b) Requerimientos 
    Basado en los riesgos, el proveedor y cliente acuerda trabajar
    juntos para crear requerimientos de seguridad detallados como parte
    de la especificacion del software a ser desarrollado. Cada uno de
    los temas listados en la sección de requerimientos de este anexo
    deben ser discutidos y evaluados por ambos, cliente y proveedor.
    Estos requerimientos pueden ser satisfechos por software creado a la
    medida, software de terceros, o la plataforma.

<!-- end list -->

  - (c) Diseño 
    El desarollador acuerda proveer documentación que explique
    claramente el diseño para adquirir cada uno de los requerimientos de
    seguridad. En muchos de los casos, esta documentacion describirá los
    mecanismos de seguridad, donde se incluirán dentro de la
    arquitectura, todos los patrones de diseño relevantes para asegurar
    su uso adecuado. El diseño debe especificar claramente si tales
    mecanismos vienen de software a la medida, software de terceros o de
    la plataforma.

<!-- end list -->

  - (d) Implementación 
    El proveedor acuerda entregar y seguir un conjunto de lineamientos
    de codificación segura. Estos lineamientos indicarán como se le de
    debe dar formato, estructurar y comentar el código fuente. Todo
    código relacionado a seguridad debe ser comentado profundamente.
    Guías sobre como evitar vulnerabilidades se seguridad comunes debe
    ser incluida. Tambien, todo el código debe ser revisado por al menos
    otro desarollador basándose en los requerimientos de seguridad y los
    lineamientos de codificación antes de ser conciderado listo para
    pruebas unitarias.

<!-- end list -->

  - (e) Pruebas y análisis de seguridad 
    El proveedor acuerda entregar y seguir un plan de pruebas de
    seguridad que defina cómo se realizarán las pruebas o bien
    establecer como cada uno de los requerimientos de seguridad va a ser
    complido. El nivel de rigor de esta actividad debe ser considerado y
    detallado en un plan. El proveedor ejecutará el plan de prueba y
    proveera los resultados a el cliente.

<!-- end list -->

  - (f) Publicación segura 
    El proveedor acuerda entregar lineamientos de configuración segura
    que describan completamente todas las opciones de configuración
    relacionadas con seguridad y sus implicaciones para la seguridad del
    software en su conjunto. Los lineamientos deben incluir una
    descripción completa de las dependencias en la plataforma y como
    deben ser configuradas de manera segura, incluidas las del sistema
    operativo, servidor Web y servidor de aplicacion. La configuración
    predeterminada del software debe ser segura.

### 4\. ÁREAS CON REQUERIMIENTOS DE SEGURIDAD

Los siguientes temas/áreas deben ser considerados durante las
actividades de entendimiento de riesgo y definición de requerimientos.
Este esfuerzo debe producir un conjunto de requerimientos ajustados,
especificos y probables. Ambos, proveedor y cliente deben ser
involucrados en este proceso y deben ponerse de acuerdo sobre el
conjunto final de requerimientos.

  - (a) Validación de entradas y condificación : Los requerimientos
    deben especificar las reglas para canonicalización, validación y
    codificación de cada dato de entrada a la aplicación, ya sea de
    usuarios, sistemas de archivos, bases de datos o sistemas externos.
    La regla predeterminada debe ser que todas las entradas sean
    validadas a menos que cumplan con una especificacion detallada de
    que esta permitido. Además, los requerimientos deben especificar las
    acciones a tomar cuando se reciven entradas no válidas.
    Especificamente, la aplicación no debe ser susceptible a
    inyecciones, desbordamientos, manipulación y otros ataques con
    entradas de usuario corruptas.

<!-- end list -->

  - (b) Autentificación y manejo de sessiones : Los requerimientos deben
    especificar como se protegeran las credenciales para autentificación
    y los identificadores de sesión a través del ciclo de desarrollo de
    software. Los requerimientos para todas las funciones relacionadas
    deben ser agregadas incluyendo recuperar contraseñas, cambio de
    contraseñas, recordar contraseñas, desconexión y conexión multiple.

<!-- end list -->

  - (c) Control de Acceso : Los requerimientos deben incluir una
    descripcion detallada de todos los roles (grupos, privilegios,
    autorizaciones) usadas en la aplicación. Los requerimientos deben
    indicar todos los activos y funciones que provee la aplicacion. Los
    requerimientos deben especificar detallada y exactamente los
    derechos de acceso para cualquier activo y función de cada rol. Se
    sugiere utilizar un formato de matriz de control de acceso para
    documentar estas reglas.

<!-- end list -->

  - (d) Manejo de Errores : Los requerimientos deben detallar como se
    van a manejar los errores que ocurran dentro del procesamiento.
    Algunas aplicaciones deberían hacer lo mejor posible en caso de un
    error, mientras que otras deberían terminar su procesamiento
    inmediatamente.

<!-- end list -->

  - (e) Historial : Los requerimientos deben especificar que eventos son
    relevantes para la seguridad y necesitan ser registrados, como
    ataques detectados, intentos de conexión fallidos e intentos de
    exeder la autorización. Los requerimientos deben especificar tambien
    que information registrar con cada evento, incluyendo hora y fecha,
    descripción del evento, detalles de aplicación, y otra información
    útil en esfuerzos forences.

<!-- end list -->

  - (f) Conexiones a sistemas externos : Los requerimientos deben
    especifica como la autentificación y cifrado será manejado para
    todos los systemas externos, tales como bases de datos, directorios
    y servicios Web. Todas las credenciales requeridas para la
    comunicación con sistemas externos deben almacenarce cifradas y
    fuera de el código dentro de archivos de configuración.

<!-- end list -->

  - (g) Cifrado : Los requerimientos deben especificar que datos deben
    ser cifrados, como serán cifrados y como todos los certificados y
    otras credenciales deben ser manejadas. Las aplicaciones deben usar
    algoritmos estándar implementados en una librerias de cifrado que
    hayan sido usadas y probadas ampliamente.

<!-- end list -->

  - (h) Disponibilidad : Los requerimientos deben especificar como
    protegerse de ataques de negación de servicio. Todos los posibles
    ataques en la aplicacion deben ser considerados, incluyendo bloqueos
    de auntentificación, agotamiento de conexiones y otros ataques de
    agotamiento de recursos.

<!-- end list -->

  - (i) Configuración segura : Los requerimientos deben especificar que
    los valores predeterminados para todas las configuraciones
    relacionadas a seguridad deben ser seguras. Para propósitos de
    auditoría, el software deberia ser capás de producir un reporte
    sencillo de leer que muestre los detalles de todas las
    configuraciones relacionadas con seguridad.

<!-- end list -->

  - (j) Vulnerabilidades especificas : Los requerimientos deben incluir
    un conjunto de vulnerabilidades especificas que no deben estar
    presentes en el software. A menos que sea especificado de otra
    manera, el software no debe incluir ninguna de las fallas descritas
    en el la "Lista de OWASP sobre las 10 vulnerabilidades mas críticas
    en aplicaciones Web".

### 5\. PERSONAL Y ORGANIZACIÓN

  - (a) Arquitecto en seguridad : El desarollador asignará la
    responsabilidad por la seguridad a un solo recurso técnico
    experimentado, para ser conocido como el arquitecto de seguridad del
    proyecto. El arquitecto de seguridad certificará la seguridad de
    cada entregable.

<!-- end list -->

  - (b) Entrenamiento en Seguridad : el proveedor será responsable de
    verificar que todos los miembros del equipo de desarrollo han sido
    entrenados en tecnicas de programación segura.

<!-- end list -->

  - (c) Desarrolladores dignos de confianza : El proveedor acuerda
    realizar las investigaciones de antecendentes apropiadas a todos los
    miembros del equipo de desarrollo.

### 6\. AMBIENTE DE DESARROLLO

  - (a) Codificación segura : El proveedor debe mencionar que
    herramientas se usarán en el ambiente de desarrollo de software para
    promover la codificación segura.

<!-- end list -->

  - (b) Adminstración de configuración : El proveedor debe usar un
    sistema de control de versiones que autentifique y registre el
    miembro del equipo asociado con todos los cambios en el código base,
    todos los archivos de configuración y compilación.

<!-- end list -->

  - (c) Distribución : El proveedor debe usar un proceso de compilación
    que construya confiablemente un archivo de distribución completo
    desde el código fuente. Este proceso debe incluir un método para
    verificar la integridad de el software entregado al cliente.

### 7\. LIBRERIAS, MARCOS DE DESARROLLO Y PRODUCTOS

  - (a) Apertura : El proveedor debe mencionar todas los aplicaciones de
    terceros usadas en el software, incluyendo todas las librerias,
    marcos de desarrollo, componentes y otros productos, ya sean
    comerciales, gratuitos, de código abierto o código cerrado.

<!-- end list -->

  - (b) Evaluación : El proveedor debe hacer esfuerzos rasonables para
    asegurar que el sofware de terceros cumple con todos los términos de
    este contrato y es tan seguro como el código a la medida
    desarrollado bajo este contrato.

### 8\. REVISIONES DE SEGURIDAD

  - (a) Derecho de revisión : El cliente tiene el derecho mandar revisar
    el software para buscar fallas de seguridad, esto a sus expesas y en
    cualquier momento dentro de los 60 dias despues de la entrega. El
    desarrollador acepta proveer apoyo rasonable al equipo de revisión
    proveyendo el codigo fuente y acceso a los ambientes de pruebas.

<!-- end list -->

  - (b) Covertura de la revisión : Las revisiones de seguridad deben
    cubrir todos los aspectos de el software entregado, incluyendo
    código a la medida, componentes, productos y configuración de
    sistema.

<!-- end list -->

  - (c) Alcance de la revisión : Al menos, la revisión debe cubrir todos
    los requerimientos de seguridad y debería buscar otras
    vulnerabilidades comunes. La revisión puede incluir una combinación
    de busqueda automatizada de vulnerabilidades, pruebas de intrusión,
    análisis estático de código fuente y revisión de código por
    expertos.

<!-- end list -->

  - (d) Problemas encontrados : Los problemas de seguridad descubiertos
    serán reportados a el cliente y proveedor por igual. A todos los
    problemas se les dará seguimiento y serán reparados como se
    especifique en la sección de seguimiento de problemas de seguridad
    de este anexo.

### 9\. ADMINISTRACIÓN DE PROBLEMAS DE SEGURIDAD

  - (a) Identificación : El proveedor dara seguimiento a todos los
    problemas de seguridad descubiertos en todo el ciclo de desarrollo,
    ya sea un problema en los requerimientos, diseño, implementación,
    pruebas, publicación u operación. El riesgo asociado con cada
    problema de seguridad será evaluado, documentado y reportado a el
    cliente tan pronto como sea posible.

<!-- end list -->

  - (b) Protección : El proveedor protegerá apropiadamente la
    información relacionada a problemas de seguridad y la documentación
    relacionada a ellos, esto, para ayudar a disminuir la probabilidad
    de las vulnerabilidades en el software operacioneal del cliente sean
    expuestas.

<!-- end list -->

  - (c) Reparación : Los problemas de seguridad que sean indentificados
    antes de la entrega deben ser reparados por el proveedor. Los
    problemas de seguridad descubiertos despues de la entrega deben ser
    manejados en la misma manera que otros problemas funcionales según
    lo especificado en este contrato.

### 10\. CERTEZA

  - (a) Certeza : El proveedor proveera un "paquete de certificación"
    consistente en la documentación de seguridad creada a traves del
    proceso de desarrollo. El paquete deberá establecer que los
    requerimientos de seguridad, diseño, implementación y resultados de
    pruebas fueron completados apropiadamente y todos los problemas de
    seguridad fueron resueltos apropiadamente.

<!-- end list -->

  - (b) Auto-Certificación : El aquitecto de seguridad certificará que
    el software cumple con los requerimientos de seguridad, que todas
    las actividades de seguridad se realizaron, y que todos los
    problemas de seguridad identificados han sido documentados y
    resueltos. Cualquier excepción a el estado de la certificacion debe
    estar totalmente documentada al momento de la entrega.

<!-- end list -->

  - (c) No código malicioso : El proveedor garantize que el sofware no
    debe contener ningun código que no se alinee a algun requerimiento
    del software y debilite la seguridad de la aplicación, incluyendo
    viruses, gusanos, bombas de tiempo, puertas traseras, caballos de
    troya, huevos de pascua y cualquier otra forma de código malicioso.

### 11\. CONCENTIMIENTO Y MANTENIMIENTO DE LA SEGURIDAD

  - (a) Consentimiento : El software no debe ser considerado como
    aceptado hasta que el paquete de certificación este completo y todos
    los problemas de seguridad han sido resueltos.

<!-- end list -->

  - (b) Investigación de problemas de seguridad : Despues del
    concentimiento, si se sospecha (razonablemente) o descubren
    problemas de seguridad, el proveedor deberá asisitir al cliente en
    realizar una investigación para determinar la naturaleza del
    problema. El problema debe ser considerado "nuevo" si no es cubierto
    por los requerientos de seguridad y esta fuera de el alcance
    (razonable) de las pruebas de seguridad.

<!-- end list -->

  - (c) Problemas de seguridad nuevos : El proveedor y el cliente
    consientes en medir el alcance y esfuerzo requerido para resolver
    problemas de seguridad nuevos, y negociad de buena fe para alcanzar
    un acuerdo y realizar el trabajor requerido para solucionarlos.

<!-- end list -->

  - (d) Otros problemas de seguridad : El proveedor debe usar todos los
    esfuersos comercialmente rasonables consistentes con practicas de
    desarrollo comunes en la industria, tomando en cuenta la severidad
    de el riesgo, para resolver todos los problemas de seguridad
    considerados nuevos tan pronto como sea posible.

__NOTOC__

[Category:OWASP Legal Project](Category:OWASP_Legal_Project "wikilink")
[Category:OWASP Secure Software Contract
Annex](Category:OWASP_Secure_Software_Contract_Annex "wikilink")