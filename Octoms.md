<table style="width:100%;">

<tr>

<td width=50%>

__TOC__

</td>

<td width=50%>

[<http://www.octoms.com/octoms-logo-medium.png>](http://www.octoms.com)

</td>

</tr>

</table>

# About

OctoMS is a general-use lightweight PHP framework and a Project
Management Tool.

# Goals

` * Better application debugging`

<code>

` // The "wizard" loads on error:`
` trigger_error("String",123);`
` // Or on an uncaught exception:`
` throw new Exception("Foo",1);`
` // Or on call anywhere inside your controller:`
` help("Search term");`
` $this->__invoke("Search term"); # if the current class extends octoms{}`
` $this("Search term"); # same as above; available from PHP 5.3+`
` // Or by adding ?debug:{user email} on any page you wish to debug`
` # The browser thus loads an AJAX interface instead of the normal output, `
` # which serves debugging information and project mgmt. tools.`

</code>

` * Self-documentation: the framework reads its sourcecode in search of user-provided keywords`
` * Online support through the wizard interface`
` * _more to come_`

# Status

OctoMS is in public Beta.

# Demo

You can access a demo of the ["Wizard" interface
here](http://octoms.com/framework/?debug:mail@address.com).

# Links

The OctoMS PHP Framework's source code can be viewed at

` * `[`OctoMS``   ``PHP``   ``Framework``   ``Google``   ``Code``
 ``page`](http://code.google.com/p/octoms)
` * `[`OctoMS``   ``PHP``   ``Framework``   ``Home``
 ``page`](http://octoms.com)

This is the list of projects developed with the OctoMS framework so far:

` * `[`Fervoare``   ``-``   ``The``   ``Startup``
 ``Tool`](http://code.google.com/p/fervoare-cms)
` * `[`DesignJotter``   ``-``   ``WordPress``   ``theme``
 ``framework`](http://code.google.com/p/designjotter)

# Project About

[Category:OWASP Project](Category:OWASP_Project "wikilink")