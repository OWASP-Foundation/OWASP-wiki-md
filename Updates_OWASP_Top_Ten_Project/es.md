  - ¿Que hay de nuevo?
    OWASP ha recorrido un largo camino desde que la última lista fuer
    publicada en Enero de 2003. Esta actualización incorpora todas las
    discuciones, puntos de vista, opiniones y debates en la comunidad
    OWASP de los ultimos 12 meses. En general, ha habido mejoras menores
    a todas las secciones de la lista y solo algunos cambios mayores:

<!-- end list -->

  - Alineación a WAS-XML
    Uno de los proyectos que inició en 2003 es el comité técnico de
    seguridad en aplicaciones Web (WAS TC por sus siglas en inglés) en
    OASIS. El propósito de el WAS TC es producir un esquema de
    clasificación para vulnerabilidades en aplicaciones Web, un modelo
    para proveer lineamientos para los ratings de las amenazas, impacto
    y riesgos. En un equema para describir las condiciones en seguridad
    Web que pueden ser usadas por herramientas de pruebas y protección.
    El proyecto de las 10 mayores de OWASP ha usado el WAS TC como
    referencia para reclasificar la lista y proveer una solución
    estandarizada sobre vulnerabilidades de seguridad en aplicaciones
    Web. El listado de WAS define un lenguaje estandar para discutir la
    seguridad en aplicaciones web, y nosotros adoptamos ese vocabulario
    aqui.

<!-- end list -->

  - Adición de negación de servicio
    La única categoria de alto nivel que cambió fue la adición de A9
    Negación de Servicio a la lista. Nuestra investigación mostro que un
    amplio espectro de organizaciones son susceptibles a este tipo de
    ataque. Basándonos en al probabilidad un ataque de negación de
    servicio y las consecuencias si el ataque es exitoso, hemos
    determinado que merece ser incluida en la lista. Para acomodar este
    nuevo tema, hemos combinado el A9 Fallas de administración remota
    del año padaso en la categoria A2 Control de acceso disfuncional
    dado que es un caso especial de esa categoría. Creemos que es
    apropiado, dado que los tipos de fallas en A2 son regularmente las
    mismas que en A9 y requieren el mismo tipo de remediación.

La tabla abajo ilustra la relación entre la nueva lista, la lista del
año pasado y la lista del WAS TC.

<table>
<tbody>
<tr class="odd">
<td><div align="center">
<p><strong>Nueva lista de las 10 mayores 2004</strong></p>
</div></td>
<td><div align="center">
<p><strong>Lista de las 10 mayores 2003</strong></p>
</div></td>
<td><div align="center">
<p><strong>Nueva lista de WAS</strong></p>
</div></td>
</tr>
<tr class="even">
<td><p>A1 Entradas no validadas</p></td>
<td><p>A1 Parámetros no validados</p></td>
<td><p>Validación de entradas</p></td>
</tr>
<tr class="odd">
<td><p>A2 Control de Accesso Disfuncional</p></td>
<td><p>A2 Control de Accesso Disfuncional<br />
(A9 Fallas de administración remota)</p></td>
<td><p>Control de Acceso</p></td>
</tr>
<tr class="even">
<td><p>A3 Autentificación y manejo de sesiones disfuncional</p></td>
<td><p>A3 Cuentas y manejo de sesiones disfuncional</p></td>
<td><p>Antentificación y manejo de sesiones</p></td>
</tr>
<tr class="odd">
<td><p>A4 Fallas de Secuencias de Comandos en Sitios Cruzados (XSS)</p></td>
<td><p>A4 Fallas de Secuencias de Comandos en Sitios Cruzados (XSS)</p></td>
<td><p>Validación de entradas -&gt; Secuencia de Comandos en Sitios Cruzados (XSS)</p></td>
</tr>
<tr class="even">
<td><p>A5 Desbordamientos de Memoria</p></td>
<td><p>A5 Desbordamientos de Memoria</p></td>
<td><p>Desbordamientos de Memoria</p></td>
</tr>
<tr class="odd">
<td><p>A6 Fallas de Inyección</p></td>
<td><p>A6 Fallas de inyección de comandos</p></td>
<td><p>Validación de Entrada -&gt; Inyección</p></td>
</tr>
<tr class="even">
<td><p>A7 Manejo inapropiado de errores</p></td>
<td><p>A7 Problemas de manejo de errores</p></td>
<td><p>Manejo de Errores</p></td>
</tr>
<tr class="odd">
<td><p>A8 Almacenamiento Inseguro</p></td>
<td><p>A8 Uso inseguro de criptografía</p></td>
<td><p>Protección de Datos</p></td>
</tr>
<tr class="even">
<td><p>A9 Negación de Servicio</p></td>
<td><p>N/A</p></td>
<td><p>Disponibilidad</p></td>
</tr>
<tr class="odd">
<td><p>A10 Gestión Insegura de Configuraciones</p></td>
<td><p>A10 Fallas de configuraciones en servidores Web y de applicación</p></td>
<td><p>Gestión de configuración de la aplicación<br />
Gestión de configuración de infraestructura</p></td>
</tr>
</tbody>
</table>

__NOEDITSECTION__

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")