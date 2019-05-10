## Overview

The purpose of this article is to give a basic overview of the custom
JSP tag included with CSRFGuard. This JSP tag will simply insert the
OWASP CSRFGuard token name-value pair into JSP's when invoked.
Applications in development should consider using the JSP tag rather
than the other handlers as it gives developers more control. This
approach is particularly useful for rich Ajax applications that the
parser handlers may have trouble working with.

There is nothing really complex about the OWASP CSRFGuard custom JSP
tag. In fact, the examples and implementation will illustrate that it is
easily invoked and utilized. Developers should check out the [web
application that makes use of
CSRFGuard](http://www.owasp.org/index.php/Image:OWASP-CSRFGuard-TestApp-2.2-src.zip%7Csample)
for more examples. Look for a file called "tags.jsp" in the WebContent
folder.

## Relevant Files

The tag definition file can be found at: OWASP\\
CSRFGuard/conf/CSRFGuard.tld The tag implementation file can be founds
at: OWASP\\ CSRFGuard/src/org/owasp/csrfguard/tags/\*

## Display Token Name

In order to display the name of your OWASP CSRFGuard token in your JSP,
first ensure that you've imported the tag definition. The following
example assumes the CSRFGuard.tld file was copied to WEB-INF:

`<%@ taglib uri="/WEB-INF/CSRFGuard.tld" prefix="csrf" %>`

Once imported, you can display the name of the CSRFGuard token by
invoking the <csrf:token-name/> tag as follows:

`My token name is: `<csrf:token-name/>

## Display Token Value

In order to display the value of your OWASP CSRFGuard token in your JSP,
first ensure that you've imported the tag definition. The following
example assumes the CSRFGuard.tld file was copied to WEB-INF:

`<%@ taglib uri="/WEB-INF/CSRFGuard.tld" prefix="csrf" %>`

Once imported, you can display the value of the CSRFGuard token by
invoking the <csrf:token-value/> tag as follows:

`My token value is: `<csrf:token-value/>

## Display Token Name/Value Pair

In order to display the OWASP CSRFGuard name-value pair in your JSP,
first ensure that you've imported the tag definition. The following
example assumes the CSRFGuard.tld file was copied to WEB-INF:

`<%@ taglib uri="/WEB-INF/CSRFGuard.tld" prefix="csrf" %>`

Once imported, you can display the CSRFGuard token name-value pair by
invoking the <csrf:token/> tag as follows:

`My token name-value pair is: `<csrf:token/>