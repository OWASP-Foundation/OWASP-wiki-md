# Code review on HTML5

HTML5 was created to replace HTLML4, XHTML and the HTML DOM Level 2.
Main purposes of this new standard is to provide dynamic content without
the use of extra proprietary plugins such as Silverlight. This allows
designers and developers to create exceptional sites providing a great
user experience without having to install any additional plug-ins into
the browser. Ideally users should have the latest web browser installed
but this does not happens as regularly as security experts advice,
therefore the website should implement 2 layer controls, one layer
independent from Browser type, second , as an additional control.

## What and where to look for in the code

# Communication APIs

## Web Messaging

`otherWindow.postMessage(message, targetOrigin, [transfer]);`

Web Messaging (also known as Cross Domain Messaging) provides a means of
messaging between documents from different origins in a way that is
generally safer than the multiple hacks used in the past to accomplish
this task. However, there are still some recommendations to keep in
mind:

  - When posting a message, explicitly state the expected origin as the
    second argument to `postMessage` rather than `*` in order to prevent
    sending the message to an unknown origin after a redirect or some
    other means of the target window's origin changing.
  - The receiving page should **always**:
      - Check the `origin` attribute of the sender to verify the data is
        originating from the expected location.
      - Perform input validation on the `data` attribute of the event to
        ensure that it's in the desired format.
  - Don't assume you have control over the `data` attribute. A single
    Cross Site Scripting flaw in the sending page allows an attacker to
    send messages of any given format.
  - Both pages should only interpret the exchanged messages as **data**.
    Never evaluate passed messages as code (e.g. via `eval()`) or insert
    it to a page DOM (e.g. via `innerHTML`), as that would create a
    DOM-based XSS vulnerability.
  - To assign the data value to an element, instead of using a insecure
    method like `element.innerHTML = data;`, use the safer option:
    `element.textContent = data;`
  - Check the origin properly exactly to match the FQDN(s) you expect.
    Note that the following code:
    `if(message.orgin.indexOf(".owasp.org")!=-1) { /* ... */ }` is very
    insecure and will not have the desired behavior as
    `www.owasp.org.attacker.com` will match.
  - If you need to embed external content/untrusted gadgets and allow
    user-controlled scripts (which is highly discouraged), consider
    using a JavaScript rewriting framework such as Google's Caja or
    check the information on

|sandboxed frames.

## Cross Origin Resource Sharing

`var myRequest = new XMLHttpRequest();`
`void open(`
`  DOMString method,`
`  DOMString url,`
`  optional boolean async,`
`  optional DOMString user,`
`  optional DOMString password`
`);`
`xmlhttp.open("GET","xmlhttp_info.txt",true);`
`xmlhttp.open.call(this, method, rewrittenUrl, async, user, pass);`

  - Validate URLs passed to `XMLHttpRequest.open`. Current browsers
    allow these URLs to be cross domain; this behavior can lead to code
    injection by a remote attacker. Pay extra attention to absolute
    URLs.
  - Ensure that URLs responding with `Access-Control-Allow-Origin: *` do
    not include any sensitive content or information that might aid
    attacker in further attacks. Use the `Access-Control-Allow-Origin`
    header only on chosen URLs that need to be accessed cross-domain.
    Don't use the header for the whole domain.
  - Allow only selected, trusted domains in the
    `Access-Control-Allow-Origin` header. Prefer whitelisting domains
    over blacklisting or allowing any domain (do not use `*` wildcard
    nor blindly return the `Origin` header content without any checks).
  - Keep in mind that CORS does not prevent the requested data from
    going to an unauthenticated location. It's still important for the
    server to perform usual Cross-Site Request Forgery prevention.
  - While the RFC recommends a pre-flight request with the `OPTIONS`
    verb, current implementations might not perform this request, so
    it's important that "ordinary" (`GET` and `POST`) requests perform
    any access control necessary.
  - Discard requests received over plain HTTP with HTTPS origins to
    prevent mixed content bugs.
  - Don't rely only on the Origin header for Access Control checks.
    Browser always sends this header in CORS requests, but may be
    spoofed outside the browser. Application-level protocols should be
    used to protect sensitive data.

## WebSockets

  - Drop backward compatibility in implemented client/servers and use
    only protocol versions above hybi-00. Popular Hixie-76 version
    (hiby-00) and older are outdated and insecure.
  - The recommended version supported in latest versions of all current
    browsers is rfc6455 RFC 6455 (supported by Firefox 11+, Chrome 16+,
    Safari 6, Opera 12.50, and IE10).
  - While it's relatively easy to tunnel TCP services through WebSockets
    (e.g. VNC, FTP), doing so enables access to these tunneled services
    for the in-browser attacker in case of a Cross Site Scripting
    attack. These services might also be called directly from a
    malicious page or program.
  - The protocol doesn't handle authorization and/or authentication.
    Application-level protocols should handle that separately in case
    sensitive data is being transferred.
  - Process the messages received by the websocket as data. Don't try to
    assign it directly to the DOM nor evaluate as code. If the response
    is JSON, never use the insecure eval() function; use the safe option
    JSON.parse() instead.
  - Endpoints exposed through the <ws://> protocol are easily reversible
    to plain text. Only <wss://> (WebSockets over SSL/TLS) should be
    used for protection against Man-In-The-Middle attacks.
  - Spoofing the client is possible outside a browser, so the WebSockets
    server should be able to handle incorrect/malicious input. Always
    validate input coming from the remote site, as it might have been
    altered.
  - When implementing servers, check the `Origin:` header in the
    Websockets handshake. Though it might be spoofed outside a browser,
    browsers always add the Origin of the page that initiated the
    Websockets connection.
  - As a WebSockets client in a browser is accessible through JavaScript
    calls, all Websockets communication can be spoofed or hijacked
    through [Cross Site
    Scripting](Cross_Site_Scripting_Flaw "wikilink"). Always validate
    data coming through a WebSockets connection.

The following is sample code of an application using Web Sockets

`[Constructor(in DOMString url, optional in DOMString protocol)] `
`interface WebSocket `
`{ readonly attribute DOMString URL; `
`// ready state const unsigned short CONNECTING = 0; `
`const unsigned short OPEN = 1; `
`const unsigned short CLOSED = 2; `
`readonly attribute unsigned short readyState; `
`readonly attribute unsigned long bufferedAmount;  `
`// networking `
`attribute Function onopen; `
`attribute Function onmessage; `
`attribute Function onclose; `
`boolean send(in DOMString data); `
`void close(); `
`}; `
`WebSocket implements EventTarget;`

`var myWebSocket = new WebSocket("`<ws://www.websockets.org>`");`

`myWebSocket.onopen = function(evt) { alert("Connection open ..."); }; `
`myWebSocket.onmessage = function(evt) { alert( "Received Message: " + evt.data); }; `
`myWebSocket.onclose = function(evt) { alert("Connection closed."); };`

## Server-Sent Events

  - Validate URLs passed to the `EventSource` constructor, even though
    only same-origin URLs are allowed.
  - As mentioned before, process the messages (`event.data`) as data and
    never evaluate the content as HTML or script code.
  - Always check the origin attribute of the message (`event.origin`) to
    ensure the message is coming from a trusted domain. Use a whitel

Many vulnerabilities are indeed patched through the implementation of
proper HTTP Headers. Part of these vulnerabilities include Cross Site
Scripting, Click jacking and Cross Site Forgery among others. For more
info regarding these vulnerabilities, please consult the OWASP Top 10.
The code reviewer must focus on looking for specific implementation of
certain features and code

## Client Side: Disable scripts

A known client side protection on the browser is the disabling of
scripts. The code should consider this scenarios and implement proper
code to allow the user understand why the code does not work properly on
his browser, if this is the case

<script>

`document.write("Hi!")`

</script>

<noscript>

browser does not support JavaScript\!

</noscript>

## Server side code implementation

Implementation of the code is also dependent on the type of web server
technology used, therefore the code might be implemented in
configuration files on the server side scripts (for example apache does
this in the httpd.conf file). Header always append X-Frame-Options
SAMEORIGIN

### PHP

<?php
 header("X-Frame-Options: SAMEORIGIN");
 ?>

### IIS (.NET)

`<system.webServer>`
`  ...`

`  `<httpProtocol>
`    `<customHeaders>
`      `<add name="X-Frame-Options" value="SAMEORIGIN" />
`    `</customHeaders>
`  `</httpProtocol>

`  ...`
`</system.webServer>`

### Ruby On Rails

Configure config/application.rb fil with the folowing code

`config.action_dispatch.default_headers.merge!({'X-Frame-Options' => 'ALLOWALL'})`

### Java (Spring Framework)

Add security dependencies by configuring this correctly in the pom.xml
configuration file

` pom.xml `

<dependencies>
`  `
`  `<dependency>
`    `<groupId>`org.springframework.security`</groupId>
`    `<artifactId>`spring-security-web`</artifactId>
`    `<version>`3.2.3.RELEASE`</version>
`  `</dependency>
`  `<dependency>
`    `<groupId>`org.springframework.security`</groupId>
`    `<artifactId>`spring-security-config`</artifactId>
`    `<version>`3.2.3.RELEASE`</version>
`  `</dependency>
</dependencies>

## Implementation of HTML5 Sandbox attribute

It is possible to set the sandbox attribute and this helps set
restrictions on content hosted in the iframe. The value must be
correctly implemented by setting an unordered unique space-separated
token which are ASCII case sensitive, these are allow-forms,
allow-pointer-lock, allow-popups, allow-same-origin, allow-scripts, and
allow-top-navigation.

Modern browsers including Chrome, Firefox, and IE10 Platform Preview are
based on the W3C IFrame Sandbox Attribute.

<iframe src="dontrtustthis.html" sandbox></iframe>

Keep in mind that these security restrictions can be easily lifted by
placing allow tokens in the attributes value such as this:

<iframe src=" dontrtustthis.html" sandbox="allow-scripts allow-forms"></iframe>

For more info on correct implementation of HTML5 Sandbox code please
visit
<http://www.whatwg.org/specs/web-apps/current-work/multipage/the-iframe-element.html#the-iframe-element>

## Sanitizer-to-Context Mapping

|                         |                                 |
| ----------------------- | ------------------------------- |
| HTML Tag Conext         | HTMLEncode,SimpleTextFormatting |
| Double Quoted Attribute | HTMLAttriEncode                 |
| Single Quoted Attribute | HTMLAttribEncode                |
| URL Path attribute      | URLPathEncode                   |
| URL Key-Value Pair      | URLKeyValueEncode               |
| In Script String        | EcmaScriptStringEncode          |
| CDATA                   | HTMLEncode                      |
| Style                   | Alpha - numerics                |

HTML Sink Context Correct sanitizer that suffices