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

# Main

**Welcome to the WebScarab Project**

WebScarab is a framework for analysing applications that communicate
using the HTTP and HTTPS protocols. It is written in Java, and is thus
portable to many platforms. WebScarab has several modes of operation,
implemented by a number of plugins. In its most common usage, WebScarab
operates as an intercepting proxy, allowing the operator to review and
modify requests created by the browser before they are sent to the
server, and to review and modify responses returned from the server
before they are received by the browser. WebScarab is able to intercept
both HTTP and HTTPS communication. The operator can also review the
conversations (requests and responses) that have passed through
WebScarab.

You may also be interested in testing the [Next Generation of
WebScarab](OWASP_WebScarab_NG_Project "wikilink").

## Screenshots

Here's the main window of WebScarab. Check the [WebScarab Getting
Started](WebScarab_Getting_Started "wikilink") guide for more
screenshots of WebScarab in action.

![Image:WebScarab after browsing.png](WebScarab_after_browsing.png
"Image:WebScarab after browsing.png")

## Overview

There is no shiny red button on WebScarab, it is a tool primarily
designed to be used by people who can write code themselves, or at least
have a pretty good understanding of the HTTP protocol. If that sounds
like you, welcome\! Download WebScarab, sign up for the mailing list on
the [OWASP subscription
page](http://lists.owasp.org/mailman/listinfo/owasp-webscarab), and
enjoy\! You can read a [brief tutorial](WebScarab_Tutorial "wikilink")
to explain the basic workings.

WebScarab is designed to be a tool for anyone who needs to expose the
workings of an HTTP(S) based application, whether to allow the developer
to debug otherwise difficult problems, or to allow a security specialist
to identify vulnerabilities in the way that the application has been
designed or implemented.

## Download

The canonical source repository for WebScarab is at
[GitHub](https://github.com/OWASP/OWASP-WebScarab). A zip archive of the
tip of tree can be downloaded
[here](https://github.com/OWASP/OWASP-WebScarab/archive/master.zip).

Historical Versions:

Alternatively, you can download older builds of WebScarab from the
[OWASP Source Code Center at
Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=61823).
Then install them likewise:

  - Linux: `java -jar ./webscarab-selfcontained-[numbers].jar`
  - Windows: double-click the installer jar file [(complete installation
    instructions)](http://www.acsac.org/2007/downloads/t5-webscarab-instructions.pdf))

## Features

A framework without any functions is worthless, of course, and so
WebScarab provides a number of plugins, mainly aimed at the security
functionality for the moment. Those plugins include:

  - Fragments - extracts Scripts and HTML comments from HTML pages as
    they are seen via the proxy, or other plugins

<!-- end list -->

  - Proxy - observes traffic between the browser and the web server. The
    WebScarab proxy is able to observe both HTTP and encrypted HTTPS
    traffic, by negotiating an SSL connection between WebScarab and the
    browser instead of simply connecting the browser to the server and
    allowing an encrypted stream to pass through it. Various proxy
    plugins have also been developed to allow the operator to control
    the requests and responses that pass through the proxy.

<!-- end list -->

  - Manual intercept - allows the user to modify HTTP and HTTPS requests
    and responses on the fly, before they reach the server or browser.

<!-- end list -->

  - Beanshell - allows for the execution of arbitrarily complex
    operations on requests and responses. Anything that can be expressed
    in Java can be executed.

<!-- end list -->

  - Reveal hidden fields - sometimes it is easier to modify a hidden
    field in the page itself, rather than intercepting the request after
    it has been sent. This plugin simply changes all hidden fields found
    in HTML pages to text fields, making them visible, and editable.

<!-- end list -->

  - Bandwidth simulator - allows the user to emulate a slower network,
    in order to observe how their website would perform when accessed
    over, say, a modem.

<!-- end list -->

  - Spider - identifies new URLs on the target site, and fetches them on
    command.

<!-- end list -->

  - Manual request - Allows editing and replay of previous requests, or
    creation of entirely new requests.

<!-- end list -->

  - SessionID analysis - collects and analyzes a number of cookies to
    visually determine the degree of randomness and unpredictability.
    Note that this analysis is rather trivial, and does not do any
    serious checks, such as FIPS, etc.

<!-- end list -->

  - Scripted - operators can use BeanShell (or any other BSF supported
    language found on the classpath) to write a script to create
    requests and fetch them from the server. The script can then perform
    some analysis on the responses, with all the power of the WebScarab
    Request and Response object model to simplify things.

<!-- end list -->

  - Parameter fuzzer - performs automated substitution of parameter
    values that are likely to expose incomplete parameter validation,
    leading to vulnerabilities like Cross Site Scripting (XSS) and SQL
    Injection.

<!-- end list -->

  - Search - allows the user to craft arbitrary BeanShell expressions to
    identify conversations that should be shown in the list.

<!-- end list -->

  - Compare - calculates the edit distance between the response bodies
    of the conversations observed, and a selected baseline conversation.
    The edit distance is "the number of edits required to transform one
    document into another". For performance reasons, edits are
    calculated using word tokens, rather than byte by byte.

<!-- end list -->

  - SOAP - There is a plugin that parses WSDL, and presents the various
    functions and the required parameters, allowing them to be edited
    before being sent to the server. **NOTE**: This plugin is
    deprecated, and may be removed in the future.
    [SOAPUI](http://www.soapui.org) is streets beyond anything that
    Webscarab can do, or will ever do, and is also a free tool.

<!-- end list -->

  - Extensions - automates checks for files that were mistakenly left in
    web server's root directory (e.g. .bak, \~, etc). Checks are
    performed for both, files and directories (e.g. /app/login.jsp will
    be checked for /app/login.jsp.bak, /app/login.jsp\~, /app.zip,
    /app.tar.gz, etc). Extensions for files and directories can be
    edited by user.

<!-- end list -->

  - XSS/CRLF - passive analysis plugin that searches for user-controlled
    data in HTTP response headers and body to identify potential CRLF
    injection (HTTP response splitting) and reflected cross-site
    scripting (XSS) vulnerabilities.

## Training Material

Aung Khant (YGN Ethical Hacker Group, Myanmar) has created a series of
WebScarab movies which can be found
[here](http://yehg.net/lab/pr0js/training/webscarab.php).

There are slides of the presentation "Uncovering Webscarab's Hidden
Treasures", given at the OWASP EU Summit 2008, available
[here](https://www.owasp.org/images/8/88/OWASP_EU_Summit_2008_WebScarab_treasures.ppt).

## Future development

Features will probably include:

  - Combining the Search and Compare plugins, so that you can compare
    only specific responses

<!-- end list -->

  - Improving the fuzzer, adding ability to follow redirects, or to
    specify the number of threads to use. Also, adding the ability to
    define what is (or isn't) interesting in the fuzz results, and save
    only interesting conversations to the summary.

## Extensibility

As a framework, WebScarab is extensible. Each feature above is
implemented as a plugin, and can be removed or replaced. New features
can be easily implemented as well. The sky is the limit\! If you have a
great idea for a plugin, please let us know about it on the list.

## Project Contributors

The WebScarab project is run by Rogan Dawes. He can be contacted at
rogan AT dawes.za.net

# Project About

__NOTOC__ <headertabs />

[WebScarab Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Download](Category:OWASP_Download "wikilink")
[Category:OWASP Release Quality
Tool](Category:OWASP_Release_Quality_Tool "wikilink")