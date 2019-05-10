## Vamos a demandar a esos idiotas -- Seguridad, Software, Contratos, y abogados

  - Por Jeff Williams (Aspect Security, Inc.)
  - Publicado Enero 13, 2004

## Introducción

¿Qué haría si usted encargo el desarrollo de su apliación web a un
taller de software externo, solo para encontrar años despues que el
código que podujeron esta lleno de problemas de seguridad? ¿Qué haría
si usted fuera el desarrollador que escribió ese código? ¿Le suena
familiar?. En muchas organizaciones, la reacción automática es demandar
a los desarrolladores sobre una parte del contrato o la teoría de
negligencia, pero eso es el mas grande error que puede hacer. Este
artículo menciona como ocurren estas disputas, como funcionan los
contratos, algunos de los argumentos de ambos lados, y sugiere un
terreno neutro que esperamos ayude a guiartle a través de esta delicada
situación.

`¿Qué hacer cuando se da cuenta que el software que escribió podría tener vulnerabilidades?`

## Solo otra aplicación Web enviada a un tercero

Imagínese el apuro de National Widgets. Hace dos años, la National
contrató a un talentoso Front End Associates para contruir un sitio web
para sus usuario. El contrato detallaba el trabajo a realizar, el
calendario, y muchos requerimientos funcionales - pero era completamente
mudo sobre seguridad. Front End contruyó el sitio y National lo publicó
desde hace 18 meses sin incidentes. El sitio ha estat trabajando bien y
National ha dado grandes referencias sobre Front End.

Recientement, algunos empleados de National mencionaron la posibilidad
de problemas de seguridad, asi que National fue a Front End y les
pregunto si la apliación era segura. El equipo de ventas de Front End
empezó a bailar y dijo que ellos estaban confiados que complieron su
obligación contractual y estarían felices de enciar una propuesta para
responder a estos "nuevos" requerimientos. National no estaba seguro
sobre el contrato original y fue con sus abogados para ver si el
contrato original tenia requerimientos de seguridad.

## Manden los abogados\!

Los abogados se emocioinaron mucho sobre el problema, y empezaron a
hacer argumentos sobre el cuidado estándard, derechos, obligaciones y
res ipsa loquitur. National obtuvo una respuesta clara sobre si el
contrato pedía o no seguridad. Asi que ellos solo regresaron a Front End
y les pidieron que arreglaran los problemas gratuitamente. Y ahi es
donde la situación inició a descomponerse.

Front End dijo que ellos no creian que hubiera ningún problema de
seguridad en el código. Antes de la entrega, ellos contrataron una
compañia de pruebas de seguridad para hacer una auditoría de seguridad
en su aplicación. La compañía que contrataron dijo especializarse en
pruebas de intrusión para probara y preparar un reporte.
Desafortunadamente, todo loq ue la compañía hizo fue correr algunos
herramientas de análisis como nmap y nessus. Ellos limpiaron la salida
de la herramienta y entregaron el reporte. National se rió cuando Front
End enseñó el reporte, y pidió producir los resultados de la revisión de
seguridad a nivel aplicacion para la aplicacion que desarrollaron.
Confrontado con eso, Front End rápidamente se retrocedió y de nuevo dijo
que no había problemas de seguridad en su código, y que incluso si
hubiera, a ellos no les pidieron contruir código seguro.

National respondio que los requerimientos para construir código seguro
eran obvios, y que cualquier vendedor que concientemente contruye código
inseguro es claramente negligente. Entonses, obviamente asombrados,
ellos empezaron a lanrar terminos como garantia implicada,
responsabilidad estricta y demanda colectiva. Ellos incluso llamaron a
el OWASP Top 10 el estandard defacto para seguridad en aplicaciones web
y mencionaron que incluso la Comisión Federal de Comercio de EU
(U.S.Federal Trade Commission) esta yendo tras compañías que no cumplan
el standard.

## Todo mundo contrata expertos

Calladamente, Front End empezto a preocupartse que su código si tuviera
problemas de seguridad. Asi que contrato sus propios expertos. Ellos
buscaron una firma especializada en seguridad en aplicaciones web para
revisar su código y hacer algunas pruebas de intrusión. Estos expertos
encontraton muchos mas problemas en los primeros días, y llamaron a
Front End para dejarles saber como iban. Un ejecutivo de Front End llamó
a los expertos después de algunos dias para dejarles saber que ellos no
requeriran un reporte escrito para sus resultados. En vés de eso
perefieren recibir los resultados oralmente durante teleconferencias.

Entre tanto, National decidio que la prioridad del negocio era probar
que de hecho había problemas serios de seguridad en su código. Asi que
contrataron sus propios expertos en seguridad en aplicaciones web y
areglaron una revisión de seguridad en la aplicación. Estos expertos
empesaron con los analizadores estándar para aplicaciones web, pero solo
encontraron unos pocos problemas. Los expertos queria hacer una revisión
de código, y pidieron a National enviar una copia de el código fuente
para la aplicación. Pero National nunca lo pidió, y no tenía una copia
del código fuente para su aplicación. Cuando pidieron a Front end una
copia, ellos la retrazaron y finalmente se reuzaron, mencionando
problemas de secreto industrial y derechos de autor. Afortunadamente
para National, the codigo fue escrito en Java y no fue ofuscado. Asi que
los expertos se metieron en el Acta de derechos de autor digital del
milenio (Digital Millennium Copyright Act \[DMCA\]) decompilaron el
código con Jad, y realizaron su revisión de código de todas maneras.
Ellos tambien hicieron algunas pruebas de intrusión junto a la revisión
de código para validar sus resultados.

Desafortunadamente (pero no sorpresivamente), la revision encontro
problemas serios de seguridad en seis de las 10 categorias del Top Ten.
Muchos de los problemas eran problemas de diseño y requeririan algunos
meses-hombre de esfuerzo para corregirlos. Asi que , National regresó a
Front End, le mostro los resultados y pidió de nuevo que los arreglaran
gratuitamente. Front End, ahora muy preocupado, respondió que ellos
llevarían el asunto con sus abogados y dejaron la junta. No
sorpresivamente, los abogados nunca respondieron a National.

## De mal en peor

Entonses, National se sintió obligado a demandar a Front End,
argumentando que Front End no había realizado el trabajo requerido en el
contrato y que ellos deberias arreglar los problemas y pagar los
honorarios legales de National. Front End respondio con una moción para
cesar el caso, basado en el hecho de que el código fue hecho hace mas de
dos años, que ellos habian sido pagados y que el código había sido
entonses completamente aceptado por National. Ellos tambien argumentaron
en la alternativa que ellos no podía ser responsables por no complir con
requerimientos que no existían al momento de contratar.

Ambos lados habían ahora invertido varias decenas de miles de dolares en
gastos legales, perdieron productividad, y dañaron su reputación. Ademas
de los costos reales del litigio, ambas partes gastaron importantes
cantidades de tiempo respondiendo interrogatorios, produciendo
documentos, preparandose para testimonios y el juicio. Muchos de los
desarrolladores originales de la aplicación de National habían dejado
Front End dado que el ambiente había cambiado dramáticamente, y ellos no
querían ser culpados por la catástrofe.

## ¿Una mejor manera?

Esta miserable historia es una buen ejemplo de como no manejar este
problema. Hay claramente muchac compañias que estan en esta situación, y
el sistema legal no es una buena manera de salir. Hay algo de razón y
error en ambas partes, asi que veamos una mejor manera de limpiar este
desastre, y entonses concluiremos con algunas ideas sobre evitar que
pasen estos problemas en el futuro.

Primero, todos en ambos lados necesitan entender que contruir codigo
seguro in aplicaciones web implica mas esfuerso que solo contruir una
que se vea bonita. Si usted es un cliente, debería dejar de sentirse
robado. Si usted y el constuctor hubieran discutido el problema con
antelación, casi seguro que el precio hubiera sido mayor. Debería
tambien tomar en cuenta que la vasta mayoria de desarrolladores no
tienen grandes conocimientos sobre seguridad, asi que no es razonable
esperar código sin vulnerabilidades sin pagar por ello. Y al final del
día, probablemente obtendra por lo que pagó. Si sospecha problemas de
seguridad en sus aplicaciones, no los ignore.

Pero, si usted es el desarrollador, no pretenda ser inocente. Si el
cliente hubiera preguntado si el código tendría vulnerabilidades, usted
seguramente diria no. Y no le habiera agregado mucho, sino es que nada,
a la oferta. Sabe que realmente debería haberse tomado el tiempo para
hacer los requerimientos de seguridad y hacer que se contruyan y prueben
correctamente. Muchas de estas vulnerabilidades han sido bien entendidas
por muchos años, y ellos no son dificiles de evitar. Si descubre o
incluso sospecha de vulnerabilidades en el código que su compañia
escribió, lo responsable es notificar a los clientes. De hecho, usted
puede tener obligacion legal de advertir a su cliente - justo como si
les hubiera vendido un auto con frenos defectuosos. Muchos compradores
respetaran el hecho de que usted haya tomado la iniciativa con esta
information y trabaje con usted para resolver los problemas.

`Nadie gana si termina en la corte.`
`haga su tarea y trabajelo.`

La única cosa justa para las partes en esta situación es encontrar una
manera de compartir el costo incvolucrado con arreglar los problemas. Si
usted se encuentra en esta situacion, la primera cosa a hacer es
reunirse con la otra parte a discutir sus preocupaciones y sugerir un
plan para resolver cualquier posible problema. El hecho es que hay
vulnerabilidades en el software en las que niguna de las partes pensó
cuando estubieron negociando hacer el trabajo. Ponganse de acuerdo en un
tercero independiente que realizar una prueba certera de cuanto tomará
arreglar la aplicación. Compartir los costos de esta revisión es
rasonable, dado que ambas partes se beneficiarán con los resultados. La
junta debería tambien incluir una revisión minuciosa de el lenguaje del
contrato para ver si hay algún término que asigne responsabilidad en
esta situación

Para asegurar que todo este completo, la revisión del tercero deberia
incluir analisis de código y algunas pruebas de intrusión. Es rasonable
que la revisión se enfoque en el Top Ten de OWASP, para mantener los
resultados ligados a un estántar mínimo para aplicaciones web. El
reporte deberia incluir descripciones detalladas de los resultados,
enfocarse en qué exáctamente esta mal con el código. Los revisores
neceistaran acceso al código para hacer estos dicernimientos y
necesitarán grandes abilidades en revisiones de código. Además, el
tercero deberá estimar el risgo asociado con la falla en el contexto
especifico de la empresa cliente.

Una ves que tienen una lista justificable de problemas de una fuente
independiente, ambas partes deben reunirse denuevo para crear un plan
para arreglarlas. El propósito de la junta debe ser identificar cuales
problemas los desarrolladores arreglarán, que tan difícil será
arreglarlas, y como van a pagar por los arreglos. Recuerden que si no
pueden encontrar un terreno neutral, ambas partes terminarán en la corte
donde solo los abogados ganarán.

## ¿Qué debería pasar en la corte?

Esta es una pregunta difícil, dado que hay muchas variables en juego.
Pero mi mejor apuesta es que la corte terminaría dividiendo la
diferencia de todas maneras. La mayoría de las cortes no van a entender
los problemas técnicos de estas vulnerabilidades, asi que buscarán a un
estándar externo y practica industrial. Esto terminará en una batalla de
tesigos expertos, algunos dicienco que esas vulnerabilidades ha sido
entendidas por 25 años, otros argumentando que la mayoria de los
desarrolladores no entienden la seguridad y que no hay estándares.
Ultimadamente, la corte no va a ser capaz de decidir quien es deponsable
de que. Ellos podrian decidir por el desarrollador, pensando que es
injusto que los desarrolladores se adieran a estándares que no estan
explícitamente establecidos y no son una práctica de la industria. Por
otro lado, ellos podrían fácilmente responsabilizar al cliente, bajo la
teoría de que el desarollador sabía o debió haber sabido sobre estas
vulnerabilidades, y por lo tanto debería haberse tomado las medidas
necesarias para evitarlas en el software.

`De cualquier manera, el costo de arreglar esas vulnerabilidades`
`sera minimizada por el de litigar el problema.`
`Asi que trabaja con tu compañero y arreglenlo.`

## ¿Qué debería pasar cuando el contrato no la menciona?

Cuando los contratos no contiene este problema, la ley llena los
términos faltantes con lo que piensa que la partes pretenderian. Estos
terminos predeterminados, vienen de estutos, la UCC, practicas de
comercio, y muchas otras fuentes. Pero la seguridad en aplicaciones es
tan nueva y en rápido movimiento que nadie adivinaría en que fuentes la
corte podria apoyarse para decidir el caso. Asi que solo por un momento,
vamos a ponernos en los zapatos de un legislador y tratar de decidir que
debería pasar.

Sería el mundo un mejor lugar si el término contractual predeterminado
fuera cero seguridad?. No, esta no puede ser la respuesta correcta. Esto
significaría que a menos que especificamente se pida, los
desarrolladores no tienen responsabilidad para hacer su código seguro.
Los desarrolladores no tendrian responsabilidad para evitar
vulnerabilidades bien conocidas. Esto pone toda la responsabilidad en el
comprador, quien no esta en una buena posición para saber que
vulnerabilidades podrían ocurrir. Asi que esta opción sería
estremadamente ineficiente economicamente hablando.

Pero imagine el extremo opuesto, cuando al desarrollador le es requerido
producir una aplicacion perfectamente segura si el contrato no lo
menciona. Esta no puede ser la respuesta correcta tampoco. En general,
poner responsabilidad en la mejor posición para evitar el problema
producirá los resultados mas ineficientes. Sin embargo, dao que crear
código perfectamente seguro es virtualmente imposible, esto crearía
responsabilidad ilimitada a los constructores de software. Obviamente,
esto tendría efectos dramaticos en la habilidad de los creadores de
software para practicar su arte. Entonses, las cortes tendrian que leer
algunos requerimiento basicos de seguridad en contratos que no lo
mencionan. La lista debería incluir requerimientos que ambas partes han
aceptado si el tema ha sido discutido. Las vulnerabilidades bien
conocidas como las del OWASP Top Ten son una punto de inicio razonable.
Pero seria mucho mejor si el comprado y el constructor trabajaran en
requerimientos reales de seguridad para el proyecto y los capturen en un
contrato, mas que confiar en lo que la corte puede soñar si se ignora el
enciso.

## ¿Y la próxima vez?

Ojalá, la mayoria de los lectores que no esten actualmente en esta
situación, y que solo quieren evitar que pase en el futuro. La manera
correcta es arreglar en terminos contractuales especificos sobre que tan
buena necesita se la seguridad para el proyecto.

Dave Thomas ha escrito que la calidad dberia ser parte de los
requerimientos que se negocian con el cliente desde le principio. La
NASA gasta algo mas que $1,000 dolares por linea de codigo. Para sus
necesidades no matemáticas. Esto es un millon de dolares por incluso un
trivial programa de 1000 lineas. Y aunque ellos tienen un fantastico
registro de calidad de software, ellos aun pierden ocacionalmente una
prueba or estrellan un coeste por problemas de software.

La Seguridad, como la calidad, es algo que los contructores de software
y los compradores deben discutir, dado que hay rasones legitimas de
negocio para aplicaciones web con diferentes niveles de seguridad. Los
compradores, por supuesto, estan inicialmente esperando software sin
vulnerabilidades. Esto, por supuesto, no es realista. Los contructores,
al menos si la historia no puede ser una guíá, quieren construir
software que cumpla los requerimientos funcionales y no se procupan
sobre la seguridad para nada. Dejar la seguridad completamente fuera de
la negociacion no es apropiado, dado que las reglas predeterminadas sin
bastante confusas.

El contructor de sofwate y el comprador necesitan tener una franca
discusión que trate preguntas como:

  - ¿Qué tipos de incidentes pueden ser considerados serios? (e.g.
    mostrar informacion, corrupción, negación de servicio)
  - ¿Todos los desarrolladores deben ser entrenados en seguridad?
  - ¿Quiere una politica de seguridad documentad y/o requerimientos de
    seguridad para la aplicación?
  - ¿Quiere documentación detallada de la documentacion de el diseño y
    mecanismos de seguridad?
  - ¿Quiere una revision de seguridad del diseño?
  - ¿Quiere pruebas de intrusión antes de la publicación?
  - ¿Quiere que el código se revise por expertos en seguridad?
  - ¿Quién toma el riesgo de arreglar los problemas de seguridad
    descubiertos después?

Los compradores deben esperar que haya algunos cambios adicionales para
incrementar la seguridad, y que ellos pueden tener un precio mas barato,
si rechazan estos servicios de seguridad. Como un punto de inicion
contractual, puede quere considerar el "draconian Code Integrity
Warranty" que pone todo el peso en los desarrolladores para cualquier
problema de cualquier tipo que afecte la seguridad. Al menos los
términos son muy claros, aunque la responsabilidad potencial para los
desarrolladores sería abrumadora.

## Conclusiones

Asi que si esta enviando su desarrollo de software a un tercero, hable
con los desarrolladores. Asegurece de que entienden sus necesidades de
seguridad. Asegurese de que los tiene en el contrato. Puede ser que
tenga que contestar algunas preguntas difíciles sobre que tanta
seguridad esta dispuesto a pagar. Si es un desarrollador de software,
este claro sobre que seguridad esta proveyendo, entonses hágalo.
Asegúrese de entender de quien será la responsabilidad si una
vulnerabilidad de seguridad es descubierta después que el software esté
en producción.

[Category:OWASP Legal Project](Category:OWASP_Legal_Project "wikilink")