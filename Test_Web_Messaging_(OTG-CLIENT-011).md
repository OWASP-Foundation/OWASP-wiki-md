## Summary

Web Messaging (also known as Cross Document Messaging) allows
applications running on different domains to communicate in a secure
manner. Before the introduction of web messaging the communication of
different origins (between iframes, tabs and windows) was restricted by
the same origin policy and enforced by the browser, however developers
used multiple hacks in order to accomplish these tasks, most of them
were mainly insecure.

This restriction within the browser is in place to restrict a malicious
website to read confidential data from other iframes, tabs, etc, however
there are some legitimate cases where two trusted websites need to
exchange data between each other. To meet this need, Cross Document
Messaging was introduced within the WHATWG HTML5 draft specification and
was implemented in all major browsers. It enables secure communications
between multiple origins across iframes, tabs and windows.

The Messaging API introduced the postMessage() method, with which
plain-text messages can be sent cross-origin. It consists of two
parameters, message and domain.

There are some security concerns when using '\*' as the domain that we
discuss below. Then, in order to receive messages the receiving website
needs to add a new event handler, and has the following attributes:

  - data: The content of the incoming message
  - origin: The origin of the sender document
  - source: source window

An example:

    Send message:

    iframe1.contentWindow.postMessage(“Hello world”,”http://www.example.com”);

    Receive message:

    window.addEventListener(“message”, handler, true);
    function handler(event) {
    if(event.origin === 'chat.example.com') {
         /* process message (event.data) */
    } else {
        /* ignore messages from untrusted domains */
    }
    }

### Origin Security Concept

The origin is made up of a scheme, host name and port and identifies
uniquely the domain sending or receiving the message, it does not
include the path or the fragment part of the url. For instance,
<https://example.com/> will be considered different from
<http://example.com> because the schema in the first case is https and
in the second http, same applies to web servers running in the same
domain but different port.

From a security perspective we should check whether the code is
filtering and processing messages from trusted domains only, normally
the best way to accomplish this is using a whitelist. Also within the
sending domain, we also want to make sure they are explicitly stating
the receiving domain and not '\*' as the second argument of
postMessage() as this practice could introduce security concerns too,
and could lead to, in the case of a redirection or if the origin changes
by other means, the website sending data to unknown hosts, and
therefore, leaking confidential data to malicious servers.

In the case the website fails to add security controls to restrict the
domains or origins that are allowed to send messages to a website, it is
most likely that a security risk will be introduced. This makes it a
very interesting part of the code from a penetration testing point of
view. We should scan the code for message event listeners and get the
callback function from the addEventListener method to further analyse,
as domains must always be verified prior to data manipulation.

### event.data Input Validation

Input validation is also important, even though the website is accepting
messages from trusted domains only, it needs to treat the data as
external untrusted data and apply the same level of security controls to
it. We should analyze the code and look for insecure methods, in
particular if data is being evaluated via

    eval()

or inserted into the DOM via the

    innerHTML

property as that would create a DOM-based XSS vulnerability.

## How to Test

### Black Box testing

Black box testing for vulnerabilities on Web Messaging is not usually
performed since access to the source code is always available as it
needs to be sent to the client to be executed.

### Gray Box testing

Manual testing needs to be conducted and the JavaScript code analyzed
looking for how Web Messaging is implemented. In particular we should be
interested in how the website is restricting messages from untrusted
domain and how the data is handled even for trusted domains. Below are
some examples:

Vulnerable code example:

In this example, access is needed for every subdomain (www, chat,
forums, ...) within the owasp.org domain. The code is trying to accept
any domain ending on .owasp.org:

    window.addEventListener(“message”, callback, true);

    function callback(e) {
         </b>if(e.origin.indexOf(".owasp.org")!=-1) {<b>
              /* process message (e.data) */
         }
    }

The intention is to allow subdomains in this form:

    www.owasp.org
    chat.owasp.org
    forums.owasp.org
    ...

Insecure code. An attacker can easily bypass the filter as
www.owasp.org.attacker.com will match.

Example of lack of origin check, very insecure as will accept input from
any domain:

    window.addEventListener(“message”, callback, true);

    function callback(e) {
         /* process message (e.data) */
    }

Input validation example: Lack of security controls lead to Cross-Site
Scripting (XSS)

    window.addEventListener(“message”, callback, true);

    function callback(e) {
         if(e.origin === "trusted.domain.com") {
              element.innerHTML= e.data;
         }
    }

This code will lead to Cross-Site Scripting (XSS) vulnerabilities as
data is not being treated properly, a more secure approach would be to
use the property textContent instead of innerHTML.

## Tools

  - **OWASP Zed Attack Proxy (ZAP)** -
    <https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project>

ZAP is an easy to use integrated penetration testing tool for finding
vulnerabilities in web applications. It is designed to be used by people
with a wide range of security experience and as such is ideal for
developers and functional testers who are new to penetration testing.
ZAP provides automated scanners as well as a set of tools that allow you
to find security vulnerabilities manually.

## References

**OWASP Resources**

  - **OWASP HTML5 Security Cheat Sheet**:
    <https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet>

**Whitepapers**

  - **Web Messaging Specification**:
    <http://www.whatwg.org/specs/web-apps/current-work/multipage/web-messaging.html>