# Modelado de amenazas

## Introducción

El término **Modelado de Amenazas** se ha vuelto bastante popular en los
últimos años. Microsoft ha publicado un libro sobre su proceso e incluye
al Modelado de Amenazas como una actividad clave en su [Ciclo de Vida de
Desarrollo Seguro
(S-SDLC)](http://www.microsoft.com/security/sdl/adopt/threatmodeling.aspx).

Un modelo de amenazas es en esencia una representación estructurada de
toda la información que afecta a la seguridad de una aplicación. En sí,
es una vista de la aplicación y su entorno a través de los "anteojos" de
la seguridad.

El modelado de amenazas es un proceso para capturar, organizar y
analizar toda esta información. Permite tomar decisiones informadas
sobre los riesgos de seguridad en las aplicaciones. Además de producir
un modelo, los esfuerzos para un modelado de amenazas típico también
producen una lista priorizada de mejoras de seguridad en los requisitos,
diseño e implementación de las aplicaciones.

## Objetivos del Modelado de Amenazas

El modelado de amenazas es un procedimiento para optimizar la seguridad
de la red/aplicaciones/Internet mediante la identificación de objetivos
y vulnerabilidades, y luego definir las contramedidas para prevenir o
mitigar los efectos de las amenazas al sistema.

Una **amenaza** es un evento potencial indeseable o real que puede ser
malicioso (como un ataque DoS) o accidental (fallo en un dispositivo de
almacenamiento). El modelado de amenazas es una actividad planificada
para la identificación y evaluación de las amenazas y vulnerabilidades
en las aplicaciones.

## Modelado de Amenazas a lo largo del Ciclo de Vida

El modelado de amenazas se aplica mejor de forma continua a lo largo de
un proyecto de desarrollo de software. El proceso es esencialmente el
mismo pero en diferentes niveles de abstracción, aunque la información
se vuelve más y más granular durante todo el ciclo de vida. Lo ideal es
que un modelo de amenazas de alto nivel debe estar definido en la fase
de planificación, y luego refinado a lo largo del ciclo de vida. A
medida que se agregan más detalles al sistema, se crean y se exponen a
nuevos vectores de ataque. El proceso de modelado de riesgos en curso
debe examinar, diagnosticar y tratar estas amenazas.

El refinar el sistema para las nuevas amenazas a las que se estará
expuesto es una parte natural del proceso. Por ejemplo, al seleccionar
una tecnología en particular, como Java por ejemplo, hay que asumir la
responsabilidad de identificar las nuevas amenazas que se crean por esa
elección. Incluso las opciones de implementación, tales como el uso de
expresiones regulares para una validación, introducen nuevas amenazas
potenciales a tratar.

## Modelado de Amenazas - Pasos genéricos

Para que exista una amenaza para una aplicación, tiene que haber una
combinación donde la probabilidad y el impacto en conjunto sean
suficientemente importantes como para hacer algo al respecto. A
continuación se presenta un borrador de una metodología genérica para el
modelado de amenazas:

  - Alcance de la evaluación
  - Modelado del sistema
  - Identificación de amenazas
  - Identificación de vulnerabilidades
  - Examinación del historial de amenazas
  - Evaluación del impacto en el negocio
  - Desarrollo de un plan de respuestas ante amenazas a la seguridad

Para comprender si una aplicación es lo suficientemente segura o no, hay
que buscar combinaciones de estos ingredientes que conducen hacia las
amenazas reales. El verdadero truco para el modelado de amenazas es no
perder el tiempo en las amenazas que son demasiado inverosímiles o
demasiado intrascendentes. Se debe tener cuidado con los procesos de
modelado de amenazas que son ineficientes debido a la reducción del
espacio de búsqueda; de las posibles amenazas para eliminar que son muy
poco probables; o de las que tienen un impacto mínimo.

No existe una manera "correcta" para evaluar el espacio de búsqueda de
posibles amenazas. Pero hay maneras "equivocadas". El intento por
evaluar todas las posibles combinaciones de agentes de amenazas,
ataques, vulnerabilidades e impacto, es una pérdida de tiempo y
esfuerzo. Existen muchas herramientas automatizadas que toman este
enfoque: la recopilación de una gran cantidad de datos y la producción
de miles de posibles amenazas. Generalmente es más productivo centrarse
en la búsqueda de amenazas con alta probabilidad y alto impacto.

El proceso básico de modelado de amenazas consiste en los siguientes
pasos genéricos. El proceso de explorar el espacio de búsqueda es
iterativo y constantemente perfeccionado sobre la base de lo que han
hecho hasta el momento. Así, por ejemplo, comenzar con todas las
vulnerabilidades posibles suele ser inútil, ya que la mayoría de ellas
no son atacables por los agentes de amenaza, protegidas por una
contramedida o no conducen a una consecuencia directa. Por lo tanto, en
general es mejor comenzar con los factores que hacen la diferencia.

  - **Alcance de la evaluación:** el primer paso siempre es entender lo
    que está en juego. La identificación de los activos tangibles, como
    bases de datos o archivos confidenciales o sensible, usualmente es
    fácil. La comprensión de las capacidades proporcionadas por la
    aplicación y la valoración de estas es más difícil. Cosas menos
    concretas, tales como la reputación y el renombre comercial son los
    más difíciles de medir, pero a menudo son los más críticos.
  - **Identificar agentes de amenaza y posibles ataques:** una parte
    fundamental del modelado de amenazas es una caracterización de los
    diferentes grupos de personas que podrían ser capaces de atacar a la
    aplicación. Estos grupos deben incluir elementos internos y
    externos, y la realización de ambos, errores involuntarios y ataques
    maliciosos.
  - **Entender contramedidas existentes:** el modelo debe incluir las
    contramedidas existentes.
  - **Identificar las vulnerabilidades explotables:** una vez que se
    tiene una comprensión de la seguridad en la aplicación, luego se
    podrán analizar las nuevas vulnerabilidades. La búsqueda es para las
    vulnerabilidades que se relacionan a los posibles ataques y las
    consecuencias negativas que se han identificado.
  - **Identificar riesgos prioritarios:** la priorización es todo en el
    modelado de amenazas ya que siempre hay muchos riesgos que
    simplemente no merecen ninguna atención. Para cada amenaza, se debe
    estimar una probabilidad y factor de impacto para determinar el
    riesgo general o el nivel de gravedad.
  - **Identificar las contramedidas para reducir la amenaza:** el último
    paso consiste en identificar las contramedidas para reducir el
    riesgo a niveles aceptables.

## Beneficios

Si se hace bien, el modelado de amenazas proporciona una "línea de
visión" clara a través de un proyecto que justifica los esfuerzos de
seguridad. El modelado de amenazas permite que las decisiones de
seguridad se hagan de manera racional, con toda la información sobre la
mesa. La alternativa consiste en tomar decisiones de seguridad
instintivas sin apoyo. El proceso de modelado de amenazas, naturalmente,
produce un argumento de seguridad que se puede utilizar para explicar y
defender la seguridad de una aplicación. Un argumento de aseguramiento
comienza con algunas exposiciones de alto nivel, y las justifica ya sea
con subexposiciones o evidencias.

## Referencias

  - [Microsoft's Application Consulting & Engineering Team's Threat
    Modeling Blog](http://blogs.msdn.com/b/threatmodeling/)
  - [RockyH.net Threat Modeling
    v2](http://www.rockyh.net/Posts/Post.aspx?postId=c85d6411-3eb8-4f26-9213-cbd735d01979)
  - [Microsoft's Security Development
    Process](http://www.microsoft.com/security/sdl/adopt/threatmodeling.aspx)

## Artículos relacionados

  - [Application Threat
    Modeling](https://www.owasp.org/index.php/Application_Threat_Modeling)
  - [OCRG1.1:Application Threat
    Modeling](https://www.owasp.org/index.php/OCRG1.1:Application_Threat_Modeling)
  - [Perform security analysis of system requirements and design (threat
    modeling)](https://www.owasp.org/index.php/Perform_security_analysis_of_system_requirements_and_design_\(threat_modeling\))
  - [OWASP Threat
    modeling](https://www.owasp.org/index.php/Threat_modeling)
  - [OWASP Threat Risk
    Modeling](https://www.owasp.org/index.php/Threat_Risk_Modeling)

# Aplicación del modelado de amenazas

## Introducción

El modelado de amenazas es un enfoque para el análisis de seguridad de
una aplicación. Se trata de un enfoque estructurado que permite
identificar, cuantificar y abordar los riesgos de seguridad asociados
con una aplicación. El modelado de amenazas no es un enfoque para la
revisión de código, pero sí para complementar dicha revisión. La
inclusión de modelos de amenazas en el SDLC puede ayudar a garantizar
que las aplicaciones se están desarrollando con seguridad incorporada
desde el principio.

Esto combinado con la documentación producida como parte del proceso de
modelado de amenazas, puede darle al revisor un mayor entendimiento del
sistema; le permite ver dónde están los puntos de entrada y las amenazas
asociadas con cada uno de estos punto. El concepto de modelado de
amenazas no es nuevo, pero se ha producido un cambio de mentalidad en
los últimos años. El modelado de amenazas moderno mira el sistema desde
la perspectiva de un potencial atacante, a diferencia del punto de vista
del defensor. Microsoft ha sido un fuerte defensor del proceso a lo
largo de los últimos años. Ellos han hecho del modelado de amenazas un
componente central en su SDLC, por lo que afirman que es una de las
razones para el aumento de la seguridad de sus productos en los últimos
años.

Cuando se realiza análisis de código fuente fuera del SDLC sobre ciertas
aplicaciones existentes, los resultados del modelado de amenazas ayuda
en la reducción de la complejidad del análisis del código, promoviendo
una primera aproximación en profundidad vs la amplitud del primer
enfoque. En lugar de revisar todo el código fuente con el mismo enfoque,
se puede dar prioridad a la revisión del código de seguridad de los
componentes, cuyo modelado de amenazas ha clasificado con amenazas de
riesgo alto.

## Pasos del modelado de amenazas

El proceso de modelado de amenazas se puede descomponer en 3 pasos de
alto nivel:

  - **Paso 1 - Descomponer la aplicación:** el primer paso en el proceso
    de modelado de amenazas se ocupa de profundizar el conocimiento de
    la aplicación y determinar cómo interactúa con entidades externas.
    Esto implica la creación de casos de uso para entender cómo se
    utiliza la aplicación, la identificación de puntos de entrada para
    ver dónde un potencial atacante podría interactuar con la aplicación
    y la identificación de activos. Por ejemplo: ítems/áreas que el
    atacante estaría interesado y la identificación de los niveles de
    confianza que representan los derechos de acceso que la aplicación
    le otorgará a las entidades externas. Esta información se registra
    en el documento "Modelo de amenazas" y también se utiliza para
    realizar los diagramas de flujo de datos (DFDs) para la aplicación.
    Los DFDs muestran los diferentes caminos a través del sistema,
    destacando las fronteras de privilegios.

<!-- end list -->

  - **Paso 2 - Determinar y jerarquizar amenazas:** la identificación de
    amenazas críticas se realiza con una metodología de categorización
    de amenazas. Se puede utilizar una categorización de amenazas como
    [STRIDE](http://msdn.microsoft.com/en-us/library/ee823878%28v=cs.20%29.aspx)
    (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of
    Service, Elevation of Privilege por sus siglas en inglés), o el
    marco de seguridad de aplicaciones (*Application Security Framework*
    ASF por sus siglas en ingglés) que define las categorías de amenazas
    tales como auditoría y *logging*, autenticación, autorización,
    gestión de configuración, protección de datos almacenados y en
    tránsito, validación de datos y gestión de excepciones.

El objetivo de la categorización de amenazas es ayudar a identificar
tanto las del atacante (STRIDE) como así también desde el punto de vista
del defensor (ASF). Los DFDs producidos en el paso 1 ayudan a
identificar los posibles objetivos de amenaza desde la perspectiva del
atacante, como fuentes de datos, procesos, flujos de datos y la
interacción con los usuarios. Estas amenazas se pueden identificar más
adelante como las raíces de [árboles de
amenazas](http://en.wikipedia.org/wiki/Attack_tree); hay un árbol por
cada objetivo de amenaza. Desde el punto de vista defensivo, la
categorización ASF ayuda a identificar las amenazas como las debilidades
en los controles de seguridad para este tipo de amenazas. Listas con
amenazas comunes con ejemplos pueden ayudar en la identificación de este
tipo de amenazas. Los casos de uso y abuso pueden ilustrar la forma en
que se pueden omitir las medidas de protección existentes, o cuando
existe una falta de esa protección. La determinación del riesgo de
seguridad para cada amenaza se puede determinar mediante un modelo de
riesgos basado en valores como
[DREAD](https://www.owasp.org/index.php/Threat_Risk_Modeling#DREAD)
(Damage, Reproducibility, Exploitability, Affected users,
Discoverability por sus siglas en inglés) o un modelo de riesgos
cualitativo menos subjetivo basado en factores de riesgo generales (por
ejemplo, probabilidad e impacto).

  - **Paso 3 - Determinar contramedidas y mitigaciones:** la falta de
    protección contra una amenaza podría indicar una vulnerabilidad cuya
    exposición al riesgo podría mitigarse con la aplicación de una
    contramedida. Tales medidas pueden identificarse utilizando listas
    de mapeo amenazas-contramedidas. Una vez que una clasificación de
    riesgos se corresponde con las amenazas, es posible clasificar las
    amenazas de mayor a menor riesgo, y dar prioridad a los esfuerzos de
    mitigación, cómo responder a tales amenazas aplicando las medidas
    identificadas. La estrategia de mitigación de riesgos puede implicar
    la evaluación de esas amenazas desde el impacto en el negocio que
    plantean, hasta la reducción del riesgo. Otras opciones podrían
    incluir asumir el riesgo, asumiendo que el impacto en el negocio es
    aceptable debido a controles compensatorios, informando de la
    amenaza al usuario, mitigando el riesgo que representa a través de
    la aplicación de un control o, la opción menos preferible, que es no
    hacer nada.

Cada uno de los pasos anteriores se tienen que documentar, para saber
cómo se llevan a cabo. El documento resultante es el modelo de amenazas
para la aplicación. En esta guía se utilizará un ejemplo para ayudar a
explicar los conceptos detrás del modelado de amenazas. El mismo ejemplo
se utilizará a lo largo de cada uno de los 3 pasos como una ayuda para
el aprendizaje. El ejemplo que se utilizará es un sitio web de la
biblioteca de una universidad. Cada uno de los pasos en el proceso de
modelado de amenazas se describen en detalle a continuación.

# Descomponer la Aplicación

El objetivo de este paso es obtener una comprensión de la aplicación y
cómo interactúa con entidades externas. Este objetivo se logra mediante
la recopilación y documentación de información. El proceso de
recopilación de información se lleva a cabo utilizando una estructura
definida claramente, lo que asegura que se recoge la información
correcta. Esta estructura también define la forma en que la información
debe ser documentada para producir el modelo de amenazas.

## Información del modelado de amenazas

El primer elemento del modelo de amenazas es la información relacionada
con el modelo de amenaza. Esto debe incluir lo siguiente:

1.  Nombre de la aplicación
2.  Versión de la aplicación
3.  Descripción: una descripción de alto nivel de la aplicación
4.  Propietario del documento: el propietario del documento del modelado
    de amenazas
5.  Participantes: los participantes involucrados en el proceso de
    modelado de amenazas para esta aplicación
6.  Revisor: el revisor/es del modelado de amenazas

|                           |
| ------------------------- |
| **Modelado de amenazas**  |
| Versión de la aplicación  |
| Descripción               |
| Propietario del documento |
| Participantes             |
| Revisor                   |

align="center" style="background:DarkSlateBlue; color:white"

### Dependencias externas

Las dependencias externas son elementos externos al código de la
aplicación que puede suponer una amenaza para la aplicación. Estos
elementos todavía suelen estar dentro del control de la organización,
pero posiblemente no bajo el control del equipo de desarrollo. La primer
área a observar a la hora de investigar las dependencias externas, es
cómo se va a implementar la aplicación en entorno de producción, y
cuáles son los requisitos en torno a ésta. Esto implica observar cómo
está o no destinada la aplicación a ser ejecutada. Por ejemplo, si se
espera que la aplicación se ejecute en un servidor que se ha
"fortalecido" *(hardening)* con el estándar de la organización y se
espera que se coloque detrás de un firewall, esta información debe ser
documentada en la sección de dependencias externas. Las dependencias
externas deben ser documentadas de la siguiente manera:

  - ID: un identificador único asignado a la dependencia externa.
  - Descripción: una descripción textual de la dependencia externa.

### Puntos de entrada

Los puntos de entrada definen las interfaces a través de la cual los
atacantes potenciales pueden interactuar con la aplicación o alimentarla
con datos. Para que un atacante potencial ataque una aplicación, deben
existir puntos de entrada. Los puntos de entrada de una aplicación se
pueden superponer, por ejemplo cada página web en una aplicación web
pueden contener varios puntos de entrada. Los puntos de entrada deben
ser documentados de la siguiente manera:

  - ID: un identificador único asignado al punto de entrada. Esto será
    utilizado para cruzar de referencia el punto de entrada a las
    amenazas o vulnerabilidades que se identifiquen. En el caso de los
    puntos de entrada de la capa, se debe utilizar una notación de
    mayor-menor.
  - Nombre: nombre descriptivo que identifica el punto de entrada y su
    propósito.
  - Descripción: una descripción textual que detalla la interacción o
    proceso que se produce en el punto de entrada.
  - Niveles de confianza: nivel de acceso requerido en el punto de
    entrada documentado. Serán referencias cruzadas con los niveles de
    confianza definidos más adelante.

### Activos

El sistema debe tener algo que al atacante le interese; estos
elementos/áreas de interés se definen como activos. Los activos son
esencialmente los objetivos de una amenaza, es decir, son la razón por
las cuales existirán las amenazas. Los activos pueden ser tanto físicos
como lógicos (abstractos). Por ejemplo, un activo de una aplicación
podría ser una lista de clientes y su información personal, este es un
activo físico. Un activo abstracto podría ser la reputación de una
organización. Dichos activos están documentados en el modelo de amenazas
de la siguiente manera:

  - ID: un identificador único es asignado para identificar cada activo.
    Esto será utilizado para cruzar referencias del activo con las
    amenazas o vulnerabilidades que se identifiquen.
  - Nombre: nombre descriptivo que identifique claramente el activo.
  - Descripción: una descripción textual de lo que es el activo y qué
    necesita ser protegido.
  - Niveles de confianza: el nivel de acceso requerido para acceder al
    punto de entrada se documenta aquí. Estas serán referencias cruzadas
    con los niveles de confianza definidos en el siguiente paso.

### Niveles de confianza

Los niveles de confianza representan los derechos de acceso que la
aplicación va a conceder a entidades externas. Los niveles de confianza
tienen una referencia cruzada con los puntos de entrada y activos. Esto
nos permite definir los derechos de acceso o privilegios requeridos en
cada punto de entrada, y los necesarios para interactuar con cada
activo. Los niveles de confianza están documentados en el modelo de
amenaza de la siguiente manera:

  - ID: número único asignado a cada nivel de la confianza. Esto se
    utiliza para cruzar referencia del nivel de confianza con los puntos
    de entrada y activos.
  - Nombre: nombre descriptivo que permita identificar a las entidades
    externas a las que se le ha concedido este nivel de confianza.
  - Descripción: descripción textual del nivel de confianza que detalla
    la entidad externa que se ha concedido el nivel de confianza.

## Diagrama de flujo de datos (DFD)

Toda la información recopilada permite modelar con precisión la
aplicación a través del uso de diagramas de flujo de datos (DFDs). El
DFD permitirá obtener una mejor comprensión de la aplicación,
proporcionando una representación visual de cómo la aplicación procesa
los datos. El enfoque del DFD está en cómo los datos se mueven a través
de la aplicación y lo que ocurre con los datos a medida que se mueven.
Los DFD son estructuras jerárquicas, por lo que se pueden usar para
descomponer la aplicación en subsistemas y subsistemas de nivel
inferior. El nivel alto del DFD permitirá aclarar el alcance de la
aplicación que se está modelando. Las iteraciones de bajo nivel
permitirán centrarse en los procesos involucrados en el tratamiento de
datos específicos. Hay un número de símbolos que se utilizan en DFD para
el modelado de amenazas.

## Referencias

  - [OWASP Application Threat
    Modeling](https://www.owasp.org/index.php/Application_Threat_Modeling)

# Contribución

Esta página es una traducción de [OWASP Threat
modeling](https://www.owasp.org/index.php/Threat_modeling) y [OWASP
Application Threat
Modeling](https://www.owasp.org/index.php/Application_Threat_Modeling)
desarrollada por Mauro Gioino y [Cristian
Borghello](https://www.owasp.org/index.php/User:Cristian_Borghello). Si
deseas contribuir no dudes en ponerte en contacto.

[Category:Threat_Modeling](Category:Threat_Modeling "wikilink")