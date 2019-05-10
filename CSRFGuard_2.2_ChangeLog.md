**UNDER CONSTRUCTION**

## Overview

OWASP CSRFGuard 2.2 offers several advantages over previous releases.
The purpose of this document is to briefly describe these changes and
why they were required for a more robust and flexible implementation of
a portable unique request token mechanism.

## Detailed Change List

**`OWASP``   ``CSRFGuard``   ``Comes``   ``With``   ``a``   ``Custom``
 ``JSP``   ``Tag``   ``Library``   ``For``   ``Token``   ``Insertion`**

One of the coolest updates to the OWASP CSRFGuard is the inclusion of a
JSP tag library that developers can use to place the CSRF token in their
HTML. This is especially useful for Ajax-y, Web 2.0 application that
contain boat loads of background requests. In previous releases, the
ability to actually use CSRFGuard was dependent on whether or not it
could successfully put the token in the HTML response. With the
introduction of the custom JSP tag library, this is no longer the case.
Developers can use the JSP tag library to place the token in the
appropriate locations of all HTML and JavaScript content. Such a feature
should aide in the use of OWASP CSRFGuard in more modern and edge-y HTML
and JavaScript based J2EE web applications.

While I would love to take credit for this idea, although in good
conscience I cannot. A buddy of mine at the OWASP San Jose conference
suggested the idea after [I gave my talk about CSRFTester and
CSRFGuard](http://www.owasp.org/images/c/c9/CSRF_DangerDetectionDefenses.ppt).
I must say - it is an honor to be around so many smart people in this
community\!

**`JavaScript``   ``Handler``   ``Processes``   ``All``   ``DOM``
 ``Elements`**

Previous releases of CSRFGuard iterated over a set of DOM elements
*known* to contain an 'href' or 'src' attribute that required the token.
This approach is extremely flawed for two reasons: 1) there was at least
one tag identified that was not *known* and 2) the release of the HTML 5
spec further complicates the management of *known* elements. Rather than
implementing a black-list of dangerous tags, the JavaScript handler now
iterates over and processes **all** tags in the DOM. Any tag containing
a 'href' or 'src' attribute will have the token appended.

**`Developer``   ``Can``   ``Define``   ``Entry``   ``Point``
 ``Pages`**

Consider the case when we have an unprotected page that links to a
resource protected by CSRFGuard. That link on the unprotected page will
not have the required unique request token to pass the CSRF defense. As
a result, there were a number of false CSRF attacks detected in previous
releases. To address this issue, the latest version of CSRFGuard allows
the developer to define "entry point" pages. These are pages for which
the existence of a token should never be validated but for which the
token must always be inserted.

**`Developer``   ``Can``   ``Define``   ``Unprotected``   ``Pages`**

There are a number of scenarios why certain pages or resources should
not be protected by OWASP CSRFGuard. In fact, fine-grain specification
of protected resources can help overcome the overhead introduced through
the use of CSRFGuard. Developers using the latest version of CSRFGuard
can now specify pages that should not be protected. These pages are not
validated for the existence of the token and they do not get the token
inserted in their HTML.

**`Optionally``   ``Verify``   ``Token``   ``If``   ``Parameters``
 ``Exist``   ``in``   ``the``   ``Request`**

Previous versions of CSRFGuard would validate every single request sent
to a protected resource. Consider the case when you click the "Refresh"
button or when you click a book mark. When these actions occur, no valid
token will exist in the GET request. As a result, CSRFGuard will
incorrectly detect an attack. To counter this issue, developers can
configure OWASP CSRFGuard to only validate the request if there are one
or more parameters in the request. This is achieved through the use of
the "org.owasp.csrfguard.ParameterlessValidation" directive. If set to
false, CSRFGuard will only validate if there is one or more parameters.
If set to true, CSRFGuard will mark a parameterless request for a
protected resource as a possible attack. Please understand the potential
consequences of this configuration. There are many web applications (Ex.
Drupal, <http://www.drupal.org>) that invoke server-side actions using
parameterless requests. If your application has this behavior, then I
would highly recommend you consider validating all requests by setting
"ParameterlessValidation" to true. If your web application(s) does not
invoke server-side actions using parameterless requests, consider
setting "ParameterlessValidation" to false to increase overall user
experience.

**`Developer``   ``Can``   ``Specify``   ``Initial``   ``Landing``
 ``Page``   ``Upon``   ``Token``   ``Creation`**

Previous releases of OWASP CSRFGuard had a very innocuous bug that
allowed for a one-time CSRF attack against a particular session. In
previous versions, when the first request came in for a session, the
token was created and the request (valid or forged\!) would be allowed
through. As a result, there existed the possibility of performing a CSRF
attack against an unauthenticated and session-less user. To counter this
particular deficiency, developers can specify a "landing page" for the
initial request when the CSRF token is being created. Rather than
allowing the initial request through after token creation, the user can
be optionally redirected to a safe landing page.

**`Fixed``   ``a``   ``Number``   ``of``   ``Code``   ``Quality``
 ``Bugs`**

The OWASP CSRFGuard 2.0 release was a bit rushed as I was trying to get
all of the latest features implemented in time for the OWASP San Jose
conference last year. As a result, a number of code quality bugs slipped
by me. One such issue was an endless loop in the FilterOutputStream
object. To address this issue, three major changes were implemented for
this release - the appropriate use of a unit testing framework (jUnit),
the use of code quality static analyzer(s) (FindBugs, PMD), and a more
stringent peer review. OWASP CSRFGuard 2.0 users are strongly encouraged
to update to the latest release.

**`The``   ``RegExHandler``   ``is``   ``Deprecated`**

Sorry guys - that class was a complete hack since day one of CSRFGuard.
That "buildLinkParameters" method is quite possibly the ugliest code
I've written since working on a particular VBA application. There are so
many better and more useful options that I've decided not to spend my
limited energy improving this response handler. If someone would like to
lead the development of the RegExHandler, shoot me an email.