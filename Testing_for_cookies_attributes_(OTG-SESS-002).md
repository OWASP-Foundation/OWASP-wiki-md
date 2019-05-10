## Summary

Cookies are often a key attack vector for malicious users (typically
targeting other users) and the application should always take due
diligence to protect cookies. This section looks at how an application
can take the necessary precautions when assigning cookies, and how to
test that these attributes have been correctly configured.

The importance of secure use of Cookies cannot be understated,
especially within dynamic web applications, which need to maintain state
across a stateless protocol such as HTTP. To understand the importance
of cookies it is imperative to understand what they are primarily used
for. These primary functions usually consist of being used as a session
authorization and authentication token or as a temporary data container.
Thus, if an attacker were able to acquire a session token (for example,
by exploiting a cross site scripting vulnerability or by sniffing an
unencrypted session), then they could use this cookie to hijack a valid
session.

Additionally, cookies are set to maintain state across multiple
requests. Since HTTP is stateless, the server cannot determine if a
request it receives is part of a current session or the start of a new
session without some type of identifier. This identifier is very
commonly a cookie although other methods are also possible. There are
many different types of applications that need to keep track of session
state across multiple requests. The primary one that comes to mind would
be an online store. As a user adds multiple items to a shopping cart,
this data needs to be retained in subsequent requests to the
application. Cookies are very commonly used for this task and are set by
the application using the Set-Cookie directive in the application's HTTP
response, and is usually in a name=value format (if cookies are enabled
and if they are supported, as is the case for all modern web browsers).
Once an application has told the browser to use a particular cookie, the
browser will send this cookie in each subsequent request. A cookie can
contain data such as items from an online shopping cart, the price of
these items, the quantity of these items, personal information, user
IDs, etc.

Due to the sensitive nature of information in cookies, they are
typically encoded or encrypted in an attempt to protect the information
they contain. Often, multiple cookies will be set (separated by a
semicolon) upon subsequent requests. For example, in the case of an
online store, a new cookie could be set as the user adds multiple items
to the shopping cart. Additionally, there will typically be a cookie for
authentication (session token as indicated above) once the user logs in,
and multiple other cookies used to identify the items the user wishes to
purchase and their auxiliary information (i.e., price and quantity) in
the online store type of application.

Once the tester has an understanding of how cookies are set, when they
are set, what they are used for, why they are used, and their
importance, they should take a look at what attributes can be set for a
cookie and how to test if they are secure. The following is a list of
the attributes that can be set for each cookie and what they mean. The
next section will focus on how to test for each attribute.

  - secure - This attribute tells the browser to only send the cookie if
    the request is being sent over a secure channel such as HTTPS. This
    will help protect the cookie from being passed over unencrypted
    requests. If the application can be accessed over both HTTP and
    HTTPS, then there is the potential that the cookie can be sent in
    clear text.

<!-- end list -->

  - HttpOnly - This attribute is used to help prevent attacks such as
    cross-site scripting, since it does not allow the cookie to be
    accessed via a client side script such as JavaScript. Note that not
    all browsers support this functionality.

<!-- end list -->

  - domain - This attribute is used to compare against the domain of the
    server in which the URL is being requested. If the domain matches or
    if it is a sub-domain, then the path attribute will be checked next.

Note that only hosts within the specified domain can set a cookie for
that domain. Also the domain attribute cannot be a top level domain
(such as .gov or .com) to prevent servers from setting arbitrary cookies
for another domain. If the domain attribute is not set, then the host
name of the server that generated the cookie is used as the default
value of the domain.

For example, if a cookie is set by an application at app.mydomain.com
with no domain attribute set, then the cookie would be resubmitted for
all subsequent requests for app.mydomain.com and its sub-domains (such
as hacker.app.mydomain.com), but not to otherapp.mydomain.com. If a
developer wanted to loosen this restriction, then he could set the
domain attribute to mydomain.com. In this case the cookie would be sent
to all requests for app.mydomain.com and its sub domains, such as
hacker.app.mydomain.com, and even bank.mydomain.com. If there was a
vulnerable server on a sub domain (for example, otherapp.mydomain.com)
and the domain attribute has been set too loosely (for example,
mydomain.com), then the vulnerable server could be used to harvest
cookies (such as session tokens).

  - path - In addition to the domain, the URL path that the cookie is
    valid for can be specified. If the domain and path match, then the
    cookie will be sent in the request. Just as with the domain
    attribute, if the path attribute is set too loosely, then it could
    leave the application vulnerable to attacks by other applications on
    the same server. For example, if the path attribute was set to the
    web server root "/", then the application cookies will be sent to
    every application within the same domain.

<!-- end list -->

  - expires - This attribute is used to set persistent cookies, since
    the cookie does not expire until the set date is exceeded. This
    persistent cookie will be used by this browser session and
    subsequent sessions until the cookie expires. Once the expiration
    date has exceeded, the browser will delete the cookie.
    Alternatively, if this attribute is not set, then the cookie is only
    valid in the current browser session and the cookie will be deleted
    when the session ends.

## How to Test

### Black Box Testing

**Testing for cookie attribute vulnerabilities:**
By using an intercepting proxy or traffic intercepting browser plug-in,
trap all responses where a cookie is set by the application (using the
Set-cookie directive) and inspect the cookie for the following:

  - Secure Attribute - Whenever a cookie contains sensitive information
    or is a session token, then it should always be passed using an
    encrypted tunnel. For example, after logging into an application and
    a session token is set using a cookie, then verify it is tagged
    using the ";secure" flag. If it is not, then the browser would agree
    to pass it via an unencrypted channel such as using HTTP, and this
    could lead to an attacker leading users into submitting their cookie
    over an insecure channel.

<!-- end list -->

  - HttpOnly Attribute - This attribute should always be set even though
    not every browser supports it. This attribute aids in securing the
    cookie from being accessed by a client side script, it does not
    eliminate cross site scripting risks but does eliminate some
    exploitation vectors. Check to see if the ";HttpOnly" tag has been
    set.

<!-- end list -->

  - Domain Attribute - Verify that the domain has not been set too
    loosely. As noted above, it should only be set for the server that
    needs to receive the cookie. For example if the application resides
    on server app.mysite.com, then it should be set to ";
    domain=app.mysite.com" and NOT "; domain=.mysite.com" as this would
    allow other potentially vulnerable servers to receive the cookie.

<!-- end list -->

  - Path Attribute - Verify that the path attribute, just as the Domain
    attribute, has not been set too loosely. Even if the Domain
    attribute has been configured as tight as possible, if the path is
    set to the root directory "/" then it can be vulnerable to less
    secure applications on the same server. For example, if the
    application resides at /myapp/, then verify that the cookies path is
    set to "; path=/myapp/" and NOT "; path=/".

<!-- end list -->

  - Expires Attribute - If this attribute is set to a time in the future
    verify that the cookie does not contain any sensitive information.
    For example, if a cookie is set to "; expires=Sun, 31-Jul-2016
    13:45:29 GMT" and it is currently July 31st 2014, then the tester
    should inspect the cookie. If the cookie is a session token that is
    stored on the user's hard drive then an attacker or local user (such
    as an admin) who has access to this cookie can access the
    application by resubmitting this token until the expiration date
    passes.

**Testing for cookie authentication replay:**
Some vulnerable sites are simply using Cookie as authentication token
without further checking on Web server side. This may result
authentication token vulnerable to attackers if cookies are stolen by
either malware or JavaScript injection. Therefore, the following testing
steps can help to identify if the website simply use cookie for
authentication token without other checking on web site.

  - Step 1 - Use Chrome Extension Cookie Editor (i.e. Chrome
    EditThisCookie) to view existsng cookie name/value.
  - Step 2 - Use Chrome Login the target testing website
  - Step 3 - Use Chrome Extension Cookie Editor to view cookie again.
    Identify those newly added or updated cookie. These can be
    authentication cookie.
  - Step 4 - Use Firefox to visit the target testing website and
    manually add all previous 3 identified cookies by FireFox Cookie
    Editor (i.e. Firefox Extension Advanced Cookie Manager)
  - Step 5 - Check Firefox browser exisitng website login status to see
    if current web page can get authenticated and login without username
    and password

## Tools

**Intercepting Proxy:**

  - **[:OWASP Zed Attack Proxy
    Project](:OWASP_Zed_Attack_Proxy_Project "wikilink")**

**Browser Plug-in:**

  - "TamperIE" for Internet Explorer -

<http://www.bayden.com/TamperIE/>

  - Adam Judson: "Tamper Data" for Firefox -

<https://addons.mozilla.org/en-US/firefox/addon/966>

  - "FireSheep" for FireFox

<https://github.com/codebutler/firesheep>

<https://github.com/codebutler/firesheep/downloads>

  - "EditThisCookie" for Chrome

<https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en>

  - "Advanced Cookie Manager" for FireFox

<https://addons.mozilla.org/en-US/firefox/addon/cookie-manager/>

## References

**Whitepapers**

  - RFC 2965 - HTTP State Management Mechanism -
    <http://tools.ietf.org/html/rfc2965>

<!-- end list -->

  - RFC 2616 – Hypertext Transfer Protocol – HTTP 1.1 -
    <http://tools.ietf.org/html/rfc2616>

<!-- end list -->

  - The important "expires" attribute of Set-Cookie
    <http://seckb.yehg.net/2012/02/important-expires-attribute-of-set.html>

<!-- end list -->

  - HttpOnly Session ID in URL and Page Body
    <http://seckb.yehg.net/2012/06/httponly-session-id-in-url-and-page.html>