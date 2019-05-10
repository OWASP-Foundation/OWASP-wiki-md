## Summary

This section describes how to check for Client Side URL Redirection,
also known as Open Redirection. It is an input validation flaw that
exists when an application accepts an user controlled input which
specifies a link that leads to an external URL that could be malicious.
This kind of vulnerability could be used to accomplish a phishing attack
or redirect a victim to an infection page.

## How to Test

This vulnerability occurs when an application accepts untrusted input
that contains an URL value without sanitizing it. This URL value could
cause the web application to redirect the user to another page as, for
example, a malicious page controlled by the attacker.

By modifying untrusted URL input to a malicious site, an attacker may
successfully launch a phishing scam and steal user credentials. Since
the redirection is originated by the real application, the phishing
attempts may have a more trustworthy appearance.

A phishing attack example could be the following:

    http://www.target.site?#redirect=www.fake-target.site

The victim that visits target.site will be automatically redirected to
fake-target.site where an attacker could place a fake page to steal
victim's credentials.

Moreover open redirections could also be used to maliciously craft an
URL that would bypass the application’s access control checks and then
forward the attacker to privileged functions that they would normally
not be able to access. 

### Black Box testing

Black box testing for Client Side URL Redirect is not usually performed
since access to the source code is always available as it needs to be
sent to the client to be executed. 

### Gray Box testing

**Testing for Client Side URL Redirect vulnerabilities:**
When testers have to manually check for this type of vulnerability they
have to identify if there are client side redirections implemented in
the client side code (for example in the JavaScript code).
These redirections could be implemented, for example in JavaScript,
using the “window.location” object that can be used to take the browser
to another page by simply assigning a string to it. (as you can see in
the following snippet of code).

    var redir = location.hash.substring(1);
    if (redir)
       window.location='http://'+decodeURIComponent(redir);

In the previous example the script does not perform any validation of
the variable “redir”, that contains the user supplied input via the
query string, and in the same time does not apply any form of encoding,
then this unvalidated input is passed to the windows.location object
originating a URL redirection vulnerability.

This implies that an attacker could redirect the victim to a malicious
site simply by submitting the following query string:

    http://www.victim.site/?#www.malicious.site

Note how, if the vulnerable code is the following:

    var redir = location.hash.substring(1);
    if (redir)
       window.location=decodeURIComponent(redir);

It also could be possible to inject JavaScript code, for example by
submitting the following query string:

    http://www.victim.site/?#javascript:alert(document.cookie)

When trying to check for this kind of issues, consider that some
characters are treated differently by different browsers.
Moreover always consider the possibility to try absolute URLs variants
as described here: <http://kotowicz.net/absolute/>

## Tools

  - DOMinator - <https://dominator.mindedsecurity.com/>

## References

**OWASP Resources**

  - [DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - DOMXSS.com - <http://www.domxss.com>

**Whitepapers**
\* Browser location/document URI/URL Sources -
<https://code.google.com/p/domxsswiki/wiki/LocationSources>

  -   - i.e., what is returned when you ask the browser for things like
        document.URL, document.baseURI, location, location.href, etc.

  - Krzysztof Kotowicz: "Local or External? Weird URL formats on the
    loose" - <http://kotowicz.net/absolute/>