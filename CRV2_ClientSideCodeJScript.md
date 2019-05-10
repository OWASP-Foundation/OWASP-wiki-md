JavaScript has several known security vulnerabilities, with HTML5 and
JavaScript becoming more prevalent in web sites today and with more web
sites moving to responsive web design with its dependence on JavaScript
the code reviewer needs to understand what vulnerabilities to look for.

The most significant vulnerabilities in JavaScript is cross-site
scripting (XSS) and Document Object Model, DOM-based XSS.

Detection of DOM-based XSS can be challenging. This is cause by the
following reasons.

  - JavaScript is often obfuscated to protect intellectual property.
  - JavaScript is often compressed out of concerned for bandwidth.

In both of these cases it is strongly recommended the code review be
able to review the JavaScript before it has been obfuscated and or
compressed.

Another aspect that makes code review of JavaScript challenging is its
reliance of large frameworks such as Microsoft .Net and Java Server
Faces and the use of JavaScript frameworks, such as JQuery, Knockout,
Angular, Backbone. These frameworks aggravate the problem because the
code can only be fully analyzed given the source code of the framework
itself. These frameworks are usually several orders of magnitude larger
then the code the code reviewer needs to review. Because of time and
money most companies simple accept that these frameworks are secure or
the risks are low and acceptable to the organization.

Because of these challenges we recommend a hybrid analysis for
JavaScript. Manual source to sink validation when necessary, static
analysis with black-box testing and taint testing.

First use a static analysis. Code Reviewer and the organization needs to
understand that because of event-driven behaviors, complex dependencies
between HTML DOM and JavaScript code, and asynchronous communication
with the server side static analysis will always fall short and may show
both positive, false, false –positive, and positive-false findings.

Black-box traditional methods detection of reflected or stored XSS needs
to be preformed. However this approach will not work for DOM-based XSS
vulnerabilities.

Taint analysis needs to be incorporated into static analysis engine.
Taint Analysis attempts to identify variables that have been 'tainted'
with user controllable input and traces them to possible vulnerable
functions also known as a 'sink'. If the tainted variable gets passed to
a sink without first being sanitized it is flagged as vulnerability.

Second the code reviewer needs to be certain the code was tested with
JavaScript was turned off to make sure all client sided data validation
was also validated on the server side.

Code examples of JavaScript vulnerabilities.

<html>

<script type=”text/javascript”>

`var pos=document.URL.indexOf(“name=”)+5;`
`document.write( document.URL.substring(pos,document.URL.length));`

</script>

<html>

Explanation: An attacker can send a link such as
“http://hostname/welcome.html\#name=

<script>

alert(1)

</script>

to the victim resulting in the victim’s browser executing the injected
client-side code.

`var url = document.location.url;`
`var loginIdx = url.indexOf(‘login’);`
`var loginSuffix = url.substring(loginIdx);`
`url = ‘http://mySite/html/sso/’ + loginSuffix;`
`document.location.url = url;`

Line 5 may be a false-positive and prove to be safe code or it may be
open to “Open redirect attack” with taint analysis the static analysis
should be able to correctly identified if this vulnerability exists. If
static analysis relies only on black-box component this code will have
flagged as vulnerable requiring the code reviewer to do a complete
source to sink review.

## Additional examples and potential security risks

`Source: document.url`
`Sink: document.write()`
`Results: document.write(“`

<script>

malicious code

</script>

Cybercriminal may controlled the following DOM elements
including…document.url,document.location,document.referrer,window.location

`Source: document.location`
`Sink: windon.location.href`
`Results: windon.location.href = `<http://www.BadGuysSite>`; - Client sode open redirect.`

`Source: document.url`
`Storage: windows.localstorage.name`
`Sink: elem.innerHTML`
`Results: elem.innerHTML = `<value>` =Stored DOM-based Cross-site Scripting`

eval() is prone to security threats, and thus not recommended to be
used.

Consider these points:

1.  Code passed to the eval is executed with the privileges of the
    executer. So, if the code passed can be affected by some malicious
    intentions, it leads to running malicious code in a user's machine
    with your website's privileges.
2.  A malicious code can understand the scope with which the code passed
    to the eval was called.
3.  You also shouldn’t use eval() or new Function() to parse JSON data.

The above if used may raise security threats. JavaScript when used to
dynamically evaluate code will create a potential security risk.

eval('alert("Query String ' + unescape(document.location.search) +
'");'); eval(untrusted string); Can lead to code injection or
client-side open redirect.

JavaScripts “new function” also may create potential security risk.

\==Three points of validity are required for <Javascript:==>

1.  Have all the logic server-side, Javascript validation be turned off
    on the client
2.  Check for all sorts of XSS DOM Attacks, never trust user data, know
    your source and sinks
3.  Check for insecure Javascript libraries and update them frequently.

References:

1.  <http://docstore.mik.ua/orelly/web/jscript/ch20_04.html>
2.  <https://www.owasp.org/index.php/Static_Code_Analysis>
3.  <http://www.cs.tau.ac.il/~omertrip/fse11/paper.pdf>
4.  <http://www.jshint.com/about/>
5.  <https://github.com/mozilla/doctorjs>