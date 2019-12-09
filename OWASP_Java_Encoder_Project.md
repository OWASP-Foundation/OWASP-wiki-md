# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![Incubator_big.jpg](Incubator_big.jpg "Incubator_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_java_encoder_project">OWASP Java Encoder Project</h2>
<p>The OWASP Java Encoder is a Java 1.5+ simple-to-use drop-in high-performance encoder class with no dependencies and little baggage. This project will help Java web developers defend against Cross Site Scripting!</p>
<p>Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts (primarily JavaScript) are injected into otherwise trusted web sites. You can read more about Cross Site Scripting here: <a href="Cross-site_Scripting_%28XSS%29" title="wikilink">Cross-site_Scripting_%28XSS%29</a>. One of the primary defenses to stop Cross Site Scripting is a technique called <i>Contextual Output Encoding</i>. <b>WARNING</b>: Please note that XSS prevention requires other defensive strategies besides encoding! For more information, please read about Cross Site Scripting prevention here: <a href="XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet" title="wikilink">XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet</a>.</p>
<p>As of September 16, 2018 there are no security issues submitted against this project! <a href="https://github.com/OWASP/owasp-java-encoder/issues"><a href="https://github.com/OWASP/owasp-java-encoder/issues">https://github.com/OWASP/owasp-java-encoder/issues</a></a>. We actively track project issues and seek to remediate any issues that arise. The project owners feel this project is stable and ready for production use and are seeking project status promotion.</p>
<h2 id="introduction">Introduction</h2>
<p><i>Contextual Output Encoding</i> is a computer programming technique necessary to stop <a href="https://www.owasp.org/index.php/XSS_Prevention_Cheat_Sheet">Cross Site Scripting</a>. This project is a Java 1.5+ simple-to-use drop-in high-performance encoder class with no dependencies and little baggage. It provides numerous encoding functions to help defend against XSS in a variety of different HTML, JavaScript, XML and CSS contexts.</p>
<h2 id="quick_overview">Quick Overview</h2>
<p>The OWASP Java Encoder library is intended for quick contextual encoding with very little overhead, either in performance or usage. To get started, simply add the encoder-1.2.2.jar, import org.owasp.encoder.Encode and start encoding.</p>
<p>Please look at the <a href="http://search.maven.org/remotecontent?filepath=org/owasp/encoder/encoder/1.2.2/encoder-1.2.2-javadoc.jar">javadoc for Encode</a> to see the variety of contexts for which you can encode. Tag libraries and JSP EL functions can be found in the encoder-jsp-1.2.2.jar.</p>
<p>Happy Encoding!</p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP Java Encoder is free to use under the <a href="http://opensource.org/licenses/BSD-3-Clause">New BSD License</a>.</p></td>
<td><h2 id="what_is_this">What is this?</h2>
<p>The OWASP Java Encoder provides:</p>
<ul>
<li>Output Encoding functions to help stop XSS</li>
<li>Java 1.5+ standalone library</li>
</ul>
<h2 id="important_links">Important Links</h2>
<p><a href="https://github.com/OWASP/owasp-java-encoder/">Java Encoder at GitHub</a><br />
<a href="https://github.com/owasp/owasp-java-encoder/issues">Issue Tracker</a></p>
<h2 id="mailing_list">Mailing List</h2>
<p><a href="https://lists.owasp.org/mailman/listinfo/owasp-java-encoder-project">Java Encoder Mailing List</a></p>
<h2 id="project_leaders">Project Leaders</h2>
<p>Author: Jeff Ichnowski <a href="mailto:jeff.ichnowski@gmail.com">@</a><br />
<a href="https://www.owasp.org/index.php/User:Jmanico">Jim Manico</a> <a href="mailto:jim.manico@owasp.org">@</a><br />
<a href="https://www.owasp.org/index.php/User:Jeremy_Long">Jeremy Long</a> <a href="mailto:jeremy.long@owasp.org">@</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet" title="wikilink">XSS (Cross Site Scripting) Prevention Cheat Sheet</a></li>
<li><a href="OWASP_Java_HTML_Sanitizer_Project" title="wikilink">OWASP Java HTML Sanitizer Project</a></li>
<li><a href="OWASP_JSON_Sanitizer" title="wikilink">OWASP JSON Sanitizer</a></li>
<li><a href="OWASP_Dependency_Check" title="wikilink">OWASP Dependency Check</a></li>
<li><a href="https://github.com/sourceclear/headlines">Sourceclear Headlines</a></li>
<li><a href="https://code.google.com/p/keyczar/">Google KeyCzar</a></li>
<li><a href="http://shiro.apache.org/">Apache SHIRO</a></li>
</ul></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://search.maven.org/remotecontent?filepath=org/owasp/encoder/encoder/1.2.2/encoder-1.2.2.jar">encoder-1.2.2.jar</a></li>
<li><a href="https://search.maven.org/remotecontent?filepath=org/owasp/encoder/encoder-jsp/1.2.2/encoder-jsp-1.2.2.jar">encoder-jsp-1.2.2.jar</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[14 September 2018] 1.2.2 Released!</li>
<li>[19 February 2017] 1.2.1 Released!</li>
<li>[11 June 2016] No reported issues and library use is strong!</li>
<li>[1 May 2015] Moved to GitHub</li>
<li>[12 Apr 2015] 1.2 Released!</li>
<li>[10 Apr 2015] GitHub move</li>
<li>[1 Feb 2015] Removed ThreadLocal</li>
<li>[20 Mar 2014] Doc additions</li>
<li>[5 Feb 2014] New Wiki</li>
<li>[4 Feb 2014] 1.1.1 Released</li>
</ul>
<h2 id="in_print">In Print</h2>
<p>We will be releasing a user guide soon!</p></td>
</tr>
</tbody>
</table>

# Use the Java Encoder Project

The general API pattern is to utilize the Java Encoder Project in your
user interface code and wrap all variables added dynamically to HTML
with a proper encoding function. The encoding pattern is
<b>"Encode.forContextName(untrustedData)"</b>, where "ContextName" is
the name of the target context and "untrustedData" is untrusted output.

## Basic HTML Context

<body>

\<%= <b>Encode.forHtml(UNTRUSTED)</b> %\>

</body>

## HTML Content Context

<textarea name="text">

\<%= <b>Encode.forHtmlContent(UNTRUSTED)</b> %\>

</textarea>

## HTML Attribute context

<input type="text" name="address" value="<%= <b>`Encode.forHtmlAttribute(UNTRUSTED)`</b>` %>" />`

Generally <b>Encode.forHtml(UNTRUSTED)</b> is also safe but slightly
less efficient for the above two contexts (for textarea content and
input value text) since it encodes more characters than necessary but
might be easier for developers to use.

## CSS contexts

<div style="width:<= <b>Encode.forCssString(UNTRUSTED)</b> %>">

<div style="background:<= <b>Encode.forCssUrl(UNTRUSTED)</b> %>">

## Javascript Block context

<script type="text/javascript">

` var msg = "<%= `<b>`Encode.forJavaScriptBlock(UNTRUSTED)`</b>` %>";`
` alert(msg);`
` `

</script>

## Javascript Variable context

` `<button
  onclick="alert('<%= <b>Encode.forJavaScriptAttribute(UNTRUSTED)</b> %>');">
` click me`</button>

JavaScript Content Notes: <b>Encode.forJavaScript(UNTRUSTED)</b> is safe
for the above two contexts, but encodes more characters and is less
efficient.

## Encode URL parameter values

<a href="/search?value=<%= <b>Encode.forUriComponent(UNTRUSTED)</b> %>&order=1#top">

## Encode REST URL parameters

<a href="/page/<%= <b>Encode.forUriComponent(UNTRUSTED)</b> %>">

## Handling a Full Untrusted URL

When handling a full URL with the OWASP Java encoder, first verify the
URL is a legal URL.

`String url = validateURL(untrustedInput);`

Then encode the URL as an HTML attribute when outputting to the page.
Note the linkable text needs to be encoded in a different context.

` `<a href="<%= <b>Encode.forHtmlAttribute(untrustedUrl)</b> %>">
` <%= `<b>`Encode.forHtmlContent(untrustedLinkName)`</b>` %>`
` `</a>

## To use in a JSP with EL

`<%@page contentType="text/html" pageEncoding="UTF-8"%>`
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"`
`   "http://www.w3.org/TR/html4/loose.dtd">`
`<%@taglib prefix="e" uri="https://www.owasp.org/index.php/OWASP_Java_Encoder_Project" %>`

<html>

<head>

<title>

<b><e:forHtml value="${param.title}" /></b>

</title>

</head>

<body>

<h1>

<b>${e:forHtml(param.data)}</b>

</h1>

</body>

</html>

Other contexts can be found in the [org.owasp.Encode class
methods](https://owasp.github.io/owasp-java-encoder/encoder/apidocs/index.html?index-all.html),
including XML contexts and more.

# How To Handle Numbers

Numbers don’t need encoding since they cannot cause XSS. There are no
numbers that will break out of a javascript context. <b>If (and only if)
‘javaNumber’ is a numeric type (primitive or box wrapper), just use:</b>

`var javaScriptNumber = <%= javaNumber %>;`

This is true even for the special cases of
java.lang.Double.POSITIVE_INFINITY, NEGATIVE_INFINITY, NaN, and
java.lang.Float equivalents.

On the other hand, if ‘javaNumber’ is some user provided data that is
NOT a numeric type, then you should either (1) convert it to a number on
the java side, or (2) encode it to a string and handle it on the
javascript side. E.g.

`<% // option (1)`
`String javaNumber = (untrusted data);`
`Double actualNumber = Double.parseDouble(javaNumber); // don’t forget to catch NumberFormatException`
`%>`

<script>

`var jsNumber = <%= actualNumber %>;`

</script>

<b>-- OR --</b>

`<% // option (2)`
`String javaNumber = (untrusted data);`
`%>`

<script>

`var jsNumber = parseInt("<%=Encode.forJavaScript(javaNumber)%>");`

</script>

# Deploy the Java Encoder Project

The OWASP Java Encoder version 1.2.2 is now available in central\!

[OWASP Encoder at Maven
Central](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.owasp.encoder%22).

## Core

Direct Download:
[encoder-1.2.2.jar](http://search.maven.org/remotecontent?filepath=org/owasp/encoder/encoder/1.2.2/encoder-1.2.2.jar)

### Maven

<dependency>
`   `<groupId>`org.owasp.encoder`</groupId>
`   `<artifactId>`encoder`</artifactId>
`   `<version>`1.2.2`</version>
</dependency>

## JSP Tag Library

Direct Download:
[encoder-jsp-1.2.2.jar](https://search.maven.org/remotecontent?filepath=org/owasp/encoder/encoder-jsp/1.2.2/encoder-jsp-1.2.2.jar)

### Maven

<dependency>
`   `<groupId>`org.owasp.encoder`</groupId>
`   `<artifactId>`encoder-jsp`</artifactId>
`   `<version>`1.2.2`</version>
</dependency>

# Grave Accent Issue

The following describes the Grave Accent XSS issue with unpatched
versions of Internet Explorer. Thank you to <b>Rafay Baloch</b> for
bringing this to our attention and to <b>Jeff Ichnowski</b> for the
workaround.

## Introduction

The grave accent (\`), ASCII 96, hex 60
([wikipedia](http://en.wikipedia.org/wiki/Grave_accent)) is subject to a
critical flaw in unpatched Internet Explorer. There is no possible
encoding of the character that can avoid the issue. For a more in depth
presentation on the issue discussed herein, please see [Mario Heidrech's
presentation](http://www.slideshare.net/x00mario/the-innerhtml-apocalypse).

## Background

In Internet Explorer, the grave accent is usable as an HTML attribute
quotation character, equivalent to single and double quotes.
Specifically, IE treats the following as equivalent:

<input value="this is the value">
``<input value=`this is the value`>``

It is an IE extension, is not in HTML specifications
([HTML4](http://www.w3.org/TR/REC-html40/intro/sgmltut.html#h-3.2.2),
[HTML5](http://www.w3.org/TR/html5/syntax.html#attributes-0)), and is
probably not well supported in other browsers.

## The Issue

The following HTML snippet, demonstrates the cross-site scripting
vulnerability related to grave accents on unpatched Internet Explorer:

<div id=a>

<input value="``onmouseover=alert(1)">

</div>

<div id=b>

</div>

<script>

b.innerHTML=a.innerHTML

</script>

When this snippet is run in Internet Explorer the following steps
happen:

1.  Two div elements are created with id's "a" and "b"
2.  The script executes "a.innerHTML" which returns:

<input value=``onmouseover=alert(1)>

1.  The script sets "b.innerHTML" to the value from (2) and is converted
    to the DOM equivalent of

<input value="" onmouseover="alert(1)">

The XSS issue arises from IE returning a value from innerHTML that it
does not parse back into the original DOM. Patched version of IE fix
this issue by returning the XSS value as a double-quoted attribute. The
issue is complicated by the fact that no possible encoding of the grave
accent can avoid this issue.

When...

<input value="``onmouseover=alert(1)">

...is the input, "a.innerHTML" returns the same XSS vector as it does
without the encoding.

## Recommend Solution

Our recommended workaround is to update any JavaScript based innerHTML
read to replace the accent grave with a numeric entity encoded form:
"\`". As an example, the following change to the XSS vulnerable code
above fixes the issue:

<script>

a.innerHTML=b.innerHTML.replace(/\`/g, "\`");

</script>

This can be done in any library code that reads the innerHTML. To follow
how this addresses the issue, the innerHTML from step 2 of the issue is
converted to:

<input value=&#96;&#96;onmouseover=alert(1)>

Since the browser will no longer see the grave accents as an empty
attribute, it will convert the input back to a copy of its original DOM.

## Other Possible Solutions

As there is no encoding option available, the following options are
available to web application authors:

1.  Do not use innerHTML copies
2.  Filter out the accent grave from any user input
3.  Clean up grave accents when using an innerHTML copy

## OWASP Java Encoder Library Related Changes

The OWASP Java Encoder Library at its core is intended to be a XSS safe
_encoding_ library. The grave accent is a legitimate and frequently
used character, that cannot be encoded to avoid this bug in unpatched
versions of IE. With enough user feedback, we may update the library to
include one of the following options: (1) alternate, drop-in build that
filters grave accents, with unchanged API, (2) new filtering methods.

# Encoding and Template Literals

Several users of the Java Encoder have asked how to properly use the
OWASP Java Encoder in combination with template literals.

The best way to encode template literal variables is to first escape the
untrusted data in a JavaScript variable and then place that variable in
the template literal.

`var user = "<%= Encode.forJavaScript(user) %>";`
`` `Hello ${user}, here is your total: ${total}` ``

Another method is to properly escape the variable in-line.

`` `Hello ${"<%= Encode.forJavaScript(user) $>"}, here is your total ${total}` ``

# Roadmap

## 2017-2018 Roadmap

  - Add decoders and canonicalization
  - Write a users guide including more complex examples
  - Build a mature test site
  - Optimize encoding to use new Java 8+ performance String utilities

__NOTOC__ <headertabs />

[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[OWASP Java Encoder Project](Category:OWASP_Project "wikilink")