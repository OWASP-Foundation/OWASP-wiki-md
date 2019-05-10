# Overview

The most important aspect of deploying OWASP CSRFGuard is configuration
of the Owasp.CsrfGuard.properties file. There are a minimum number of
configuration settings that users should review and specify before
running an instance of OWASP CSRFGuard. Such configurations include
specifying the new token landing page, enabling Ajax support for
applications making use of XMLHttpRequest, capturing pages that should
not be protected, as well as configuring one or more actions that should
be invoked when a CSRF attack is identified. The purpose of this article
is to provide an overview of key OWASP CSRFGuard configuration settings.

# Logger

The logger property (org.owasp.csrfguard.Logger) defines the qualified
class name of the object responsible for processing all log messages
produced by CSRFGuard. The default CSRFGuard logger is
org.owasp.csrfguard.log.ConsoleLogger. This class logs all messages to
System.out which JavaEE application servers redirect to a vendor
specific log file. Developers can customize the logging behavior of
CSRFGuard by implementing the org.owasp.csrfguard.log.ILogger interface
and setting the logger property to the new logger's qualified class
name. The following configuration snippet instructs OWASP CSRFGuard to
capture all log messages to the console:

`org.owasp.csrfguard.Logger=org.owasp.csrfguard.log.ConsoleLogger`

# New Token Landing Page

The new token landing page property
(org.owasp.csrfguard.NewTokenLandingPage) defines where to send a user
if the token is being generated for the first time. This request is
generated using auto-posting forms and will only contain the CSRF
prevention token parameter, if applicable. All query-string or form
parameters sent with the original request will be discarded. If this
property is not defined, CSRFGuard will instead auto-post the user to
the original context and servlet path. The following configuration
snippet instructs OWASP CSRFGuard to redirect the user to
/Owasp.CsrfGuard.Test/index.html when the user visits a protected
resource without having a corresponding CSRF token present in the
HttpSession object:

`org.owasp.csrfguard.NewTokenLandingPage=/Owasp.CsrfGuard.Test/index.html`

# Unique Token Per Page

The unique token per-page property (org.owasp.csrfguard.TokenPerPage) is
a boolean value that determines if CSRFGuard should make use of unique
per-page (i.e. URI) prevention tokens as opposed to unique per-session
prevention tokens. When a user requests a protected resource, CSRFGuard
will determine if a page specific token has been previously generated.
If a page specific token has not yet been previously generated,
CSRFGuard will verify the request was submitted with the per-session
token intact. After verifying the presence of the per-session token,
CSRFGuard will create a page specific token that is required for all
subsequent requests to the associated resource. The per-session CSRF
token can only be used when requesting a resource for the first time.
All subsequent requests must have the per-page token intact or the
request will be treated as a CSRF attack. Use of the unique token per
page property is currently experimental but provides a significant
amount of improved security. Consider the exposure of a CSRF token using
the legacy unique per-session model. Exposure of this token facilitates
the attacker's ability to carry out a CSRF attack against the victim's
active session for any resource exposed by the web application. Now
consider the exposure of a CSRF token using the experimental unique
token per-page model. Exposure of this token would only allow the
attacker to carry out a CSRF attack against the victim's active session
for a small subset of resources exposed by the web application. Use of
the unique token per-page property is a strong defense in depth strategy
significantly reducing the impact of exposed CSRF prevention tokens. The
following configuration snippet instructs OWASP CSRFGuard to utilize the
unique token per-page model:

`org.owasp.csrfguard.TokenPerPage=true`

# Token Rotation

The rotate token property (org.owasp.csrfguard.Rotate) is a boolean
value that determines if CSRFGuard should generate and utilize a new
token after verifying the previous token. Rotation helps minimize the
window of opportunity an attacker has to leverage the victim's stolen
token in a targeted CSRF attack. However, this functionality generally
causes navigation problems in most applications. Specifically, the
'Back' button in the browser will often cease to function properly. When
a user hits the 'Back' button and interacts with the HTML, the browser
may submit an old token causing CSRFGuard to incorrectly believe this
request is a CSRF attack in progress (i.e. a 'false positive'). Users
can prevent this scenario by preventing the caching of HTML pages
containing FORM submissions using the cache-control header. However,
this may also introduce performance problems as the browser will have to
request HTML on a more frequent basis. The following configuration
snippet disables token rotation:

`org.owasp.csrfguard.Rotate=false`

# Ajax and XMLHttpRequest Support

The Ajax property (org.owasp.csrfguard.Ajax) is a boolean value that
indicates whether or not OWASP CSRFGuard should support the injection
and verification of unique per-session prevention tokens for
XMLHttpRequests. To leverage Ajax support, the user must not only set
this property to true but must also reference the [JavaScript DOM
Manipulation](CSRFGuard_3_Token_Injection#JavaScript_DOM_Manipulation "wikilink")
code using a script element. This dynamic script will override the send
method of the XMLHttpRequest object to ensure the submission of an
X-Requested-With header name value pair coupled with the submission of a
custom header name value pair for each request. The name of the custom
header is the value of the token name property and the value of the
header is always the unique per-session token value. This custom header
is analogous to the HTTP parameter name value pairs submitted via
traditional GET and POST requests. If the X-Requested-With header was
sent in the HTTP request, then CSRFGuard will look for the presence and
ensure the validity of the unique per-session token in the custom header
name value pair. Note that verification of these headers takes
precedence over verification of the CSRF token supplied as an HTTP
parameter. More specifically, CSRFGuard does not verify the presence of
the CSRF token if the Ajax support property is enabled and the
corresponding X-Requested-With and custom headers are embedded within
the request. The following configuration snippet instructs OWASP
CSRFGuard to support Ajax requests by verifying the presence and
correctness of the X-Requested-With and custom headers:

`org.owasp.csrfguard.Ajax=true`

# Unprotected Pages

The unprotected pages property (org.owasp.csrfguard.unprotected.\*)
defines a series of pages that should not be protected by CSRFGuard.
Such configurations are useful when the CsrfGuardFilter is aggressively
mapped (ex: /\*). The syntax of the property name is
org.owasp.csrfguard.unprotected.\[PageName\], where PageName is some
arbitrary identifier that can be used to reference a resource. The
syntax of defining the uri of unprotected pages is the same as the
syntax used by the JavaEE container for uri mapping. Specifically,
CSRFGuard will identify the first match (if any) between the requested
uri and an unprotected page in order of declaration. Match criteria is
as follows:

  -
    Case 1: exact match between request uri and unprotected page
    Case 2: longest path prefix match, beginning / and ending /\*
    Case 3: extension match, beginning \*.
    Default: requested resource must be validated by CSRFGuard

The following code snippet illustrates the three use cases over four
examples. The first two examples (Tag and JavaScriptServlet) look for
direct URI matches. The third example (Html) looks for all resources
ending in a .html extension. The last example (Public) looks for all
resources prefixed with the URI path /MySite/Public/\*.

`org.owasp.csrfguard.unprotected.Tag=/Owasp.CsrfGuard.Test/tag.jsp`
`org.owasp.csrfguard.unprotected.JavaScriptServlet=/Owasp.CsrfGuard.Test/JavaScriptServlet`
`org.owasp.csrfguard.unprotected.Html=*.html`
`org.owasp.csrfguard.unprotected.Public=/MySite/Public/*`

# Actions: Responding to Attacks

The actions directive (org.owasp.csrfguard.action.\*) gives the user the
ability to specify one or more actions that should be invoked when a
CSRF attack is detected. Every action must implement the
org.owasp.csrfguard.action.IAction interface either directly or
indirectly through the org.owasp.csrfguard.action.AbstractAction helper
class. Many actions accept parameters that can be specified along with
the action class declaration. These parameters are consumed at runtime
and impact the behavior of the associated action.

The syntax for defining and configuring CSRFGuard actions is relatively
straight forward. Let us assume we wish to redirect the user to a
default page when a CSRF attack is detected. A redirect action already
exists within the CSRFGuard bundle and is available via the class name
org.owasp.csrfguard.actions.Redirect. In order to enable this action, we
capture the following declaration in the Owasp.CsrfGuard.properties
file:

**`syntax:`**` org.owasp.csrfguard.action.[actionName]=[className]`
**`example:`**` org.owasp.csrfguard.action.class.Redirect=org.owasp.csrfguard.actions.Redirect`

The aforementioned directive declares an action called "Redirect" (i.e.
\[actionName\]) referencing the Java class
"org.owasp.csrfguard.actions.Redirect" (i.e. \[className\]). Anytime a
CSRF attack is detected, the Redirect action will be executed. You may
be asking yourself, "but how do I specify where the user is
redirected?"; this is where action parameters come into play. In order
to specify the redirect location, we capture the following declaration
in the Owasp.CsrfGuard.properties file:

**`syntax:`**` org.owasp.csrfguard.action.[actionName].[parameterName]=[parameterValue]`
**`example:`**` org.owasp.csrfguard.action.Redirect.ErrorPage=/Owasp.CsrfGuard.Test/error.html`

The aforementioned directive declares an action parameter called
"ErrorPage" (i.e. \[parameterName\]) with the value of
"/Owasp.CsrfGuard.Test/error.html" (i.e. \[parameterValue\]) for the
action "Redirect" (i.e. \[actionName\]). The Redirect action expects the
"ErrorPage" parameter to be defined and will redirect the user to this
location when an attack is detected.

There are several "out of the box" actions made available with the OWASP
CSRFGuard distributable.

## org.owasp.csrfguard.action.Log

Creates a customized log message whenever a CSRF attack is detected by
OWASP CSRFGuard. The log message is captured using the logger mechanism
defined by the *org.owasp.csrfguard.Logger* directive in the
Owasp.CsrfGuard.properties file. Log accepts the following action
parameters:

**org.owasp.csrfguard.action.Log.Message**

Allows the user to define the format of the log message to be recorded.
The Message parameter supports several formatting options to aide in the
customization of the message to the particular attack. The following
formatting options are supported:

**`%exception%`**` - String representation of the CsrfGuardException thrown by the CsrfGuard class.`
**`%exception_message%`**` - Localized exception message of the class CsrfGuardException thrown by the CsrfGuard class.`
**`%remote_ip%`**` - Remote IP address of the client that sent the CSRF attack to the server.`
**`%remote_host%`**` - Remote host name of the client that sent the CSRF attack to the server.`
**`%remote_port%`**` - Remote port of the client that sent the CSRF attack to the server.`
**`%local_ip%`**` - Local IP address of the server that detected the CSRF attack.`
**`%local_host%`**` - Local host name of the server that detected the CSRF attack.`
**`%local_port%`**` - Local port of the server that detected the CSRF attack.`
**`%request_uri%`**` - Request URI for which the CSRF attack was targeting.`
**`%request_url%`**` - Request URL for which the CSRF attack was targeting.`
**`%user%`**` - User information as made available by the javax.servlet.http.HttpServletRequest.getRemoteUser() method invocation.`

## org.owasp.csrfguard.action.Invalidate

Invalidate any existing HttpSession associated with the current
HttpServletRequest. Note that this is the session of the victim for
which the CSRF attack was targeting. Invalidating the JavaEE container's
session generally results in the user having to re-authenticate. There
are no parameters associated with this action.

## org.owasp.csrfguard.action.Redirect

Redirects the user to the URI specified in the Page action parameter.
Attempting to utilize this action in combination with Forward will
generally result in the JavaEE container throwing IllegalStateException.
The action accepts the following action parameters:

**org.owasp.csrfguard.action.Redirect.Page**

Defines the URI for which the user is redirected when a CSRF attack is
detected.

## org.owasp.csrfguard.action.Forward

Forwards the user to the URI specified in the Page action parameter.
Attempting to utilize this action in combination with Redirect will
generally result in the JavaEE container throwing IllegalStateException.
The action accepts the following action parameters:

**org.owasp.csrfguard.action.Forward.Page**

Defines the URI for which the user is forwarded when a CSRF attack is
detected.

## org.owasp.csrfguard.action.RequestAttribute

Makes the CsrfGuardException thrown by the CsrfGuard class when an
attack is detected programmatically available as an attribute in the
HttpServletRequest object. The action accepts the following action
parameters:

**org.owasp.csrfguard.action.RequestAttribute.AttributeName**

Defines the attribute name that should be used when placing the
CsrfGuardException in the HttpServletRequest attributes collection.

## org.owasp.csrfguard.action.SessionAttribute

Makes the CsrfGuardException thrown by the CsrfGuard class when an
attack is detected programmatically available as an attribute in the
HttpSession object. The action accepts the following action parameters:

**org.owasp.csrfguard.action.SessionAttribute.AttributeName**

Defines the attribute name that should be used when placing the
CsrfGuardException in the HttpSession attributes collection.

## org.owasp.csrfguard.action.Rotate

Invalidates and re-generates any existing CSRF prevention tokens
associated with the current HttpSession. This action helps minimize the
risk of a malicious user attempting to brute force a user's prevention
tokens through timing based side channel attacks. Note that this action
has no effect when used in conjunction with the Invalidate action. There
are no parameters associated with this action.

# Miscellaneous Configurations

## Token Name

The token name property (org.owasp.csrfguard.TokenName) defines the name
of the HTTP parameter to contain the value of the OWASP CSRFGuard token
for each request. The following configuration snippet sets the CSRFGuard
token parameter name to the value OWASP_CSRFTOKEN:

`org.owasp.csrfguard.TokenName=OWASP_CSRFTOKEN`

## Session Key

The session key property (org.owasp.csrfguard.SessionKey) defines the
string literal used to save and lookup the CSRFGuard token from the
session. This value is used by the filter and the tag libraries to
retrieve and set the token value in the session. Developers can use this
key to programmatically lookup the token within their own code. The
following configuration snippet sets the session key to the value
OWASP_CSRFTOKEN:

`org.owasp.csrfguard.SessionKey=OWASP_CSRFTOKEN`

## Token Length

The token length property (org.owasp.csrfguard.TokenLength) defines the
number of characters that should be found within the CSRFGuard token.
Note that characters are delimited by dashes (-) in groups of four. For
cosmetic reasons, users are encourage to ensure the token length is
divisible by four. The following configuration snippet sets the token
length property to 32 characters:

`org.owasp.csrfguard.TokenLength=32`

## Pseudo-Random Number Generator

The pseudo-random number generator property (org.owasp.csrfguard.PRNG)
defines what PRNG should be used to generate the OWASP CSRFGuard token.
Always ensure this value references a cryptographically strong
pseudo-random number generator algorithm. The following configuration
snippet sets the pseudo-random number generator to SHA1PRNG:

`org.owasp.csrfguard.PRNG=SHA1PRNG`

[Category:OWASP CSRFGuard
Project](Category:OWASP_CSRFGuard_Project "wikilink")