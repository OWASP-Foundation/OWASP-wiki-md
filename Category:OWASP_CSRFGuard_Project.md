# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_flagship_big.jpg](_flagship_big.jpg "_flagship_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_csrfguard">OWASP CSRFGuard</h2>
<p>Welcome to the home of the OWASP CSRFGuard Project! OWASP CSRFGuard is a library that implements a variant of the <a href="http://www.corej2eepatterns.com/Design/PresoDesign.htm">synchronizer token pattern</a> to mitigate the risk of <a href="Cross-Site_Request_Forgery" title="wikilink">Cross-Site Request Forgery</a> (CSRF) attacks.</p>
<h2 id="introduction">Introduction</h2>
<p>The OWASP CSRFGuard library is integrated through the use of a JavaEE Filter and exposes various automated and manual ways to integrate per-session or pseudo-per-request tokens into HTML.</p>
<h2 id="description">Description</h2>
<h4 id="overview">Overview</h4>
<p>OWASP CSRFGuard implements a variant of the synchronizer token pattern to mitigate the risk of CSRF attacks. In order to implement this pattern, CSRFGuard must offer the capability to place the CSRF prevention token within the HTML produced by the protected web application. CSRFGuard 3 provides developers more fine grain control over the injection of the token. Developers can inject the token in their HTML using either dynamic JavaScript DOM manipulation or a JSP tag library. CSRFGuard no longer intercepts and modifies the HttpServletResponse object as was done in previous releases. The currently available token injection strategies are designed to make the integration of CSRFGuard more feasible and scalable within current enterprise web applications. Developers are encouraged to make use of both the JavaScript DOM Manipulation and the JSP tag library strategies for a complete token injection strategy. The JavaScript DOM Manipulation strategy is ideal as it is automated and requires minimal effort on behalf of the developer. In the event the JavaScript solution is insufficient within a particular application context, developers should leverage the JSP tag library. The purpose of this article is to describe the token injection strategies offered by OWASP CSRFGuard 3.</p>
<h4 id="javascript_dom_manipulation">JavaScript DOM Manipulation</h4>
<p>OWASP CSRFGuard 3 supports the ability to dynamically inject CSRF prevention tokens throughout the DOM currently loaded in the user's browser. This strategy is extremely valuable with regards to server-side performance as it simply requires the serving of a dynamic JavaScript file. There is little to no performance hit when the fetched dynamic JavaScript updates the browser's DOM. Making use of the JavaScript token injection solution requires the developer map a Servlet and place a JavaScript HTML tag within all pages sending requests to protected application resources. Developers are strongly encouraged to leverage the JavaScript token injection strategy by default. This strategy requires minimal effort on behalf of the developer as most of the token injection logic is automated. In the event that the JavaScript automated solution may be insufficient for a specific application context, developers should leverage the OWASP CSRFGuard JSP tag library.</p>
<p><strong>Note:</strong> Use of JavaScript DOM Manipulation is required for Ajax support.</p>
<figure>
<img src="CSRGuard.PNG" title="CSRGuard.PNG" alt="CSRGuard.PNG" width="300" /><figcaption>CSRGuard.PNG</figcaption>
</figure>
<h2 id="what_is_csrfguard">What is CSRFGuard?</h2>
<p>OWASP CSRFGuard provides:</p>
<ul>
<li>A library that implements a variant of the synchronizer token pattern to mitigate the risk of Cross-Site Request Forgery (CSRF) attacks.</li>
<li>A JavaEE Filter and exposes various automated and manual ways to integrate per-session or pseudo-per-request tokens into HTML.</li>
</ul>
<h2 id="ohloh">Ohloh</h2>
<ul>
<li><a href="https://www.ohloh.net/p/OWASP-CSRFGuard">https://www.ohloh.net/p/OWASP-CSRFGuard</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="in_print">In Print</h2>
<p>This project can be purchased as a print on demand book from Lulu.com</p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-flagship-trans-85.png" title="Owasp-flagship-trans-85.png" alt="Owasp-flagship-trans-85.png" /><figcaption>Owasp-flagship-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Licensing

OWASP CSRFGuard 3.1 is offered under the BSD license

| valign="top" style="padding-left:25px;width:200px;border-right: 1px
dotted gray;padding-right:25px;" |

# Presentation & Manual

Link to presentation

<https://www.owasp.org/index.php/CSRFGuard_3_Token_Injection>

# Project Leader

The CSRFGuard project is run by [Azzeddine
RAMRAMI](mailto:azzeddine.ramrami\(at\)owasp.org).

The project co-leader is [Sébastien
Gioria](mailto:sebastien.gioria\(at\)owasp.org).

With the active participation of:

` `[`Ahamed``
 ``Nafeez`](mailto:ahamednafeez\(at\)gmail.com)` : Security Tester & Bug Finder`
` `[`Trent``
 ``Schmidt`](mailto:Trent.schmidt\(at\)gmail.com)` : Release & Maven Central helper `

## Related Projects

:\*[OWASP
CSRFTester](http://www.owasp.org/index.php/Category:OWASP_CSRFTester_Project)
- utility to assist in the testing and generating PoC for CSRF attacks.

:\*[OWASP CSRF Prevention Cheat
Sheet](Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet "wikilink")
- provides a more holistic overview of CSRF prevention strategies and
associated frameworks.

:\*<http://www.owasp.org/index.php/PHP_CSRF_Guard> - project
implementing CSRFGuard style solution for PHP.

:\*<http://www.thespanner.co.uk/2007/10/19/jsck/> - project implementing
CSRFGuard style solution for PHP and JavaScript.

:\*<http://www.owasp.org/index.php/.Net_CSRF_Guard> - project
implementing CSRFGuard style solution for ASP.NET.

:\*<https://www.owasp.org/index.php/CSRFProtector_Project> - CSRF
Protector Project - Implements new Anti CSRF method in web applications

# Source Code Download

Download and build the latest source code from GitHub :

  - <https://github.com/aramrami/OWASP-CSRFGuard>

Download and build the latest source code from GitHub -
<https://github.com/aramrami/OWASP-CSRFGuard-3>

[Deprecated Releases](CSRFGuard_Deprecated_Releases "wikilink") -
article containing several download references to deprecated and
officially unsupported releases

## CSRFGuard Binary in Maven Central

You can download a binary version from Maven Central here:

  - <https://oss.sonatype.org/#nexus-search;gav>\~\~csrfguard

Thanks to Trent Schmidt and Joel Orlina (JIRA) for there help.

## User Manual(s)

[OWASP CSRFGuard v3](CSRFGuard_3_User_Manual "wikilink") - series of
articles describing the installation, configuration, and deployment of
OWASP CSRFGuard v3.

# News and Events

  - \[08 Fev 2014\] A security fix has been published. See details on
    GitHub
  - \[10 Feb 2014\] Release 3.1 of CSRFGuard project is now available
    for download
  - \[28 Jul 2014\] A new Github repository called "OWASP CSRFGuard-3"
    with issues management has been created

# FAQs

Here a complete CSRF attacks FAQ:

  - <http://www.cgisecurity.com/csrf-faq.html>

# Acknowledgements

## Volunteers

CSRFGuard is developed by a worldwide team of volunteers. The primary
contributors to date have been:

  - Ahamed Nafeez, Security Engineer.
  - Christa Erwin, Security, Programmer/Analyst.
  - Trent Schmidt, Release & Maven Central helper

## Others

  - Eric Sheridan was the original designer of CSRFGuard until 3.0
    version.

# Road Map and Getting Involved

As of CSRFGuard the priorities are:

  - Address any security vulnerabilities around javascript prototype
    hijacking
  - Support for Internet Explorer
  - Addressing outstanding issues listed in GitHub
  - Support for Multi-part requests
  - Add support for the 'Origin' header

Involvement in the development and promotion of CSRFGurd is actively
encouraged\! You do not have to be a security expert in order to
contribute. Some of the ways you can help:

  - Make fix to the actual version
  - Propose a security enhcement
  - Write a complete Architecture Folder for CSRFGurd
  - Add an IA engine to detect unknown attacks.

# Contact US

You can sign up for the OWASP CSRFGuard email list at
<https://lists.owasp.org/mailman/listinfo/owasp-csrfguard>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:SAMM-SA-2](Category:SAMM-SA-2 "wikilink")