__TOC__

## Introduction

Cookies can be used to maintain a session state. This identifies a user
whilst in the middle of using the application. Session IDs are a popular
method of identifying a user. A "secure" session ID should be at least
128 bits in length and sufficiently random. Cookies can also be used to
identify a user, but care must be taken in using cookies. Generally it
is not recommended to implement a SSO (Single Sign On) solution using
cookies; they were never intended for such use. Persistent cookies are
stored on a user's hard disk and are valid depending on the expiry date
defined in the cookie. The following are pointers when reviewing cookie
related code.

## How to Locate the Potentially Vulnerable Code

If the cookie object is being set with various attributes apart from the
session ID, check that the cookie is set only to transmit over
HTTPS/SSL. In Java this is performed by the method:

`cookie.setSecure() (Java)`
`cookie.secure = secure; (.NET) `
`Response.Cookies("CookieKey").Secure = True (Classic ASP)`

### HTTP Only Cookie

This is adhered to in IE6 and above. HTTP Only cookie is meant to
provide protection against XSS by not letting client side scripts access
the cookie. It's a step in the right direction but not a silver bullet.

`cookie.HttpOnly = true (C#)`

Here the cookie should only be accessible via ASP.NET.

Note that HTTPOnly property is not supported in Classic ASP pages.

### Limiting Cookie Domain

Ensure cookies are limited to a domain such as example.com; therefore
the cookie is associated to example.com. If the cookie is associated
with other domains the following code performs this:

`Response.Cookies["domain"].Domain = "support.example.com"; (C#)`
`Response.Cookies("domain").Domain = "support.example.com" (Classic ASP)`

During the review, if the cookie is assigned to more than one domain,
make note of it and query why this is the case.

### Displaying Data to User from Cookie

Make sure that data being displayed to a user from a cookie is HTML
encoded. This mitigates some forms of Cross Site Scripting.

`LabelX.Text = Server.HtmlEncode(Request.Cookies["userName"].Value); (C#)`
`Response.Write Server.HtmlEncode (Request.Cookies("userName")) (Classic ASP)`

## Session Tracking/Management Techniques

### HTML Hidden Field

The HTML Hidden field could be used to perform session tracking. Upon
each HTTP POST request, the hidden field is passed to the server
identifying the user. It would be in the form of

<INPUT TYPE="hidden" NAME="user"VALUE="User001928394857738000094857hfduekjkksowie039848jej393">` `

Server-side code is used to perform validation on the VALUE in order to
ensure the used is valid. This approach can only be used for POST/Form
requests.

### URL Rewriting

URL rewriting approaches session tracking by appending a unique ID
pertaining to the user at the end of the URL.

<A HREF="/smackmenow.htm?user=User001928394857738000094857hfduekjkksowie039848jej393">`Click Here`</A>

## Leading Practice Patterns for Session Management/Integrity

HTTPOnly Cookie: Prevents cookie access via client side script. Not all
browsers support such a directive.

**Valid Session checking**:

Upon any HTTP request the framework should check if the user pertaining
to the HTTP request (via session ID) is valid.

**Successful Authentication**:

Upon a successful login the user should be issued a new session
identifier. The old session ID should be invalidated. This prevents
session fixation attacks and the same browser also sharing the same
session ID in a multi user environment. Sometimes the session ID is per
browser, and the session remains valid while the browser is alive.

**Logout**: This also leads to the idea of why a logout button is so
important. The logout button should invalidate the user’s session ID
when it is selected.

## Related Articles

[OWASP cookies database](:Category:OWASP_Cookies_Database "wikilink")
<http://msdn2.microsoft.com/en-us/library/ms533046.aspx>
<http://java.sun.com/j2ee/sdk_1.3/techdocs/api/javax/servlet/http/Cookie.html>

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")
[Category:Session Management](Category:Session_Management "wikilink")