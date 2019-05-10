## Summary

ASP.NET server-side Web application framework designed for Web
development to produce dynamic Web pages. It was developed by Microsoft
to allow programmers to build dynamic web sites, web applications and
web services. It was first released in January 2002 with version 1.0 of
the .NET Framework, and is the successor to Microsoft's Active Server
Pages (ASP) technology. ASP.NET is built on the Common Language Runtime
(CLR), allowing programmers to write ASP.NET code using any supported
.NET language. The ASP.NET SOAP extension framework allows ASP.NET
components to process SOAP messages. ASP.NET is in the process of being
re-implemented as a modern and modular web framework, together with
other frameworks like Entity Framework. The new framework will make use
of the new open-source .NET Compiler Platform (code-name "Roslyn") and
be cross platform. ASP.NET MVC, ASP.NET Web API, and ASP.NET Web Pages
(a platform using only Razor pages) will merge into a unified MVC
6.\[3\] The project is called "ASP.NET vNext".

## Common Misconfigurations

### Tracing misconfiguration

#### Description

Trace.axd is an Http Handler for .NET  that can be used to view the
trace details for an application. ASP.NET tracing enables you to view
diagnostic information about a single request for an ASP.NET page.
ASP.NET tracing enables you to follow a page's execution path, display
diagnostic information at run time, and debug your application. When
it's enabled in a production environment, it poses a disclosure risk by
exposing information about the internal operation of the page. A request
to this file through a browser displays the trace log of the last n
requests in time-order, where n is an integer determined by the value
set by requestLimit="\[n\]" in the application’s configuration file.

#### How to test

Make a request

[`http://[target]/trace.axd`](http://%5Btarget%5D/trace.axd)

Tracing does not appear to be ON as the request didn't return a page
with a heading called "Application Trace".
![<File:TraceAXD.png>](TraceAXD.png "File:TraceAXD.png")

#### Remediation

Trace can be disabled inside web.config file.

<configuration>
`  <system.web>`
`    `<trace enabled="false"/>
`  </system.web>`
</configuration>

Trace can be configured at page level with @Page directive, so when
going to production remove those settings from pages or turn them off.

-----

### Custom errors misconfiguration

#### Description

Custom errors are used to ensure that internal error messages are not
exposed to end users. Custom errors can include Framework version, Stack
Trace. This information can be leveraged to exploit the application as
it discloses potentially sensitive information about the internal
implementation of the website. Instead, a custom error message should be
returned which provides a friendlier user experience and keeps
potentially sensitive internal implementation information away from
public view.

#### How to test

Make a request

[`http://[target]/`](http://%5Btarget%5D/)<random_page>`.aspx`

Another way is if Page receive param (like ID) you can duplicate this
param in request ID=1\&ID=1 That will cause framework to show error
page.

If custom error mode in turned off you will see detailed error
description formed by ASP.NET framework.

#### Remediation

Turn ON CustomErrors mode that will prevent disclosure of technical
information.

<configuration>
`  <system.web>`
`    `<customErrors mode="On">
`  </system.web>`
</configuration>

-----

### Hash DoS misconfiguration

#### Description

The hash table denial of service vulnerability (hash DoS) allows an
attacker to make a POST request with a very large number of parameters
constructed to cause hash collisions when parsed by ASP.NET. These
collisions are very computationally expensive and could subsequently
cause the CPU utilization to spike thus disallowing it to process
legitimate requests. Microsoft patched the risk in security update
MS11-100 then resolved it permanently with the release of .NET 4.5.

#### How to test

A POST request with 1,001 form parameters named "0" through to "1000".
Check if any differences occurs when web-application process such
requests. Time differences, some error responses.

#### Remediation

Install MS11-100 patch

-----

### ELMAH log misconfiguration

#### Description

ELMAH is used extensively by ASP.NET websites for error logging and
handling. When improperly configured, ELMAH error logs can be easily
viewed without any access controls thus exposing potentially sensitive
information about the website.

#### How to test

Request

[`http://[target]/elmah.axd`](http://%5Btarget%5D/elmah.axd)

You should see page with "Error Log for" text

#### Remediation

In order to provide a customization mechanism for the features ELMAH
requires the configuration file to contain specific sections
declarations under the root configuration node, as shown in the
following snippet.

`  `
`<configSections>     `
`   <sectionGroup name="elmah">`
`     <section name="security" requirePermission="false" type="Elmah.SecuritySectionHandler, Elmah" />     `
`   </sectionGroup>     `
`</configSections>`

There's a default section group named elmah which contains custom
configuration sections to tune several aspects concerning security.

Notice the presence of the requirePermission attribute declaration.
Note: The requirePermission attribute is new to ASP.NET 2.0 and it's not
recognized by ASP.NET 1.x, thus it must be omitted in that environment.

Configure ELMAH Log access.

<elmah>`  `
`  `<security allowRemoteAccess="0" />`  `
</elmah>` `

-----

### Excessive headers misconfiguration

#### Description

By default, excessive information about the server and frameworks used
by an ASP.NET application are returned in the response headers. These
headers can be used to help identify security flaws which may exist as a
result of the choice of technology exposed in these headers.

#### How to test

Make a request to web-application and check HTTP response headers. You
can use Fiddler, Burp, ZAP or other web-proxy.
![<File:Headers.png>](Headers.png "File:Headers.png")

#### Remediation

Configuring the application to not return unnecessary headers keeps this
information silent and makes it significantly more difficult to identify
the underlying frameworks.

`<system.web>`
`  `<httpRuntime enableVersionHeader="false" />
`</system.web>`

Go into the IIS configuration of the website and locate the “HTTP
Response Headers”  And remove X-Power-By header.

The MVC version is also easy, although it does require us to touch code.
Over in the Global.asax, we want to jump into the Application_Start
event and add the following:

`MvcHandler.DisableMvcResponseHeader = true;`

-----

### HTTP only cookies misconfiguration

#### Description

Cookies not flagged as "HttpOnly" may be read by client side script and
are at risk of being interpreted by a cross site scripting (XSS) attack.
Whilst there are times where a cookie set by the server may be
legitimately read by client script, most times the "HttpOnly" flag is
missing it is due to oversight rather than by design.

#### How to test

Make a request to web-application and check HTTP response headers. You
can use Fiddler, Burp, ZAP or other web-proxy. All cookie values in
response must contain HttpOnly option (like in example below).
![<File:HttpOnly.png>](HttpOnly.png "File:HttpOnly.png")

#### Remediation

Unless the cookie legitimately needs to be read by JavaScript on the
client, the "HttpOnly" flag should always be set to ensure it cannot be
read by the client and used in an XSS attack.

<httpCookies httpOnlyCookies="true" />

-----

### Secure cookies misconfiguration

#### Description

Cookies served over HTTPS but not flagged as "secure" may be sent over
an insecure connection by the browser. Often this may be a simple
request for an asset such as a bitmap file but if it's on the same
domain as the cookie is valid for then it will be sent in an insecure
fashion. This poses a risk of interception via a man in the middle
attack.

#### How to test

Make a request to web-application and check HTTP response headers. You
can use Fiddler, Burp, ZAP or other web-proxy. All cookie values in
response must contain secure option (like in example below).

![<File:Secure.png>](Secure.png "File:Secure.png")

#### Remediation

The "secure" flag should always be set to ensure that cookie values
can't be exposed over unprotected communication.

<httpCookies requireSSL="true" />

-----

### Clickjacking misconfiguration

#### Description

Websites are at risk of a clickjacking attack when they allow content to
be embedded within a frame. An attacker may use this risk to invisibly
load the target website into their own site and trick users into
clicking on links which they never intended to. An "X-Frame-Options"
header should be sent by the server to either deny framing of content,
only allow it from the same origin or allow it from a trusted URIs.

#### How to test

Make a request to web-application and check HTTP response headers. You
can use Fiddler, Burp, ZAP or other web-proxy. All cookie values in
response must contain X-Frame-Option header (like in example below).
![<File:XFrame.png>](XFrame.png "File:XFrame.png")

#### Remediation

Go into the IIS configuration of the website and locate the “HTTP
Response Headers”  And add X-Frame-Options header with DENY or
SAMEORIGIN value. Or inside Web.config:

`  `
`<system.webServer>`
`<httpProtocol>`
`    <customHeaders>`
`      <add name="X-Frame-Options" value="DENY `
`| SAMEORIGIN" />`
`    </customHeaders>`
`  </httpProtocol>`
`</system.webServer>`

-----

### View state MAC misconfiguration

#### Description

MAC (message authentication code) is used to ensure the integrity of
view state by hashing the contents with a private key then validating
the hash when the view state is posted back to the server. Disabling
view state removes this validation process and may pose significant
risks to the application's security profile if an attacker is able to
manipulate the view state and post it back to the web site.

#### How to test

1.  Intercept request to web-site with Burp or Fiddler and remove
    __VIEWSTATE param if web-site responds with Validation Error then
    MAC Validation is ON
2.  Inside web page source code find __VIEWSTATE param, decode its
    value with base64. Check last bytes that follows "dd", if exists
    then there is VIEWSTATE validation is on. Example:

<input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="..." />

#### Remediation

Turn on ViewState validation mode in web.config or at specific page.
(Note: MachineKey also should be defined in a secure way - please read
more at Cryptography Page)

`  `
`<configuration>`
`  <system.web>`
`    <pages enableViewStateMac="true"/>`
`  `
`<configuration>`
`  <system.web>`
`    <machineKey validation="AES" validationKey="AutoGenerate,IsolateApps" />`

-----

### ViewState Encryption misconfiguration

#### Description

To reduce the chance of someone intercepting the information stored in
the ViewState, it is good design to encrypt the ViewState. Unencrypted
ViewState can expose and leak secret information.

#### How to test

Inside web page source code find __VIEWSTATE param, decode its value
with base64. Check if it can be decoded from base64. If not then its
encrypted.

Example:

<input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="..." />

#### Remediation

Configure following options inside web.config.

`  `
`<machineKey validationKey="AutoGenerate,IsolateApps"  decryptionKey="AutoGenerate,IsolateApps" validation="HMACSHA256"`
`  decryption="AES" />`
`  `
`<system.web>`
`  <pages viewStateEncryptionMode="Auto" />`
`</system.web>`

-----

### Request validation misconfiguration

#### Description

In a web forms site, request validation ensures all requests to the
website do not contain a potentially malicious payload. This protects
against the likelihood of cross site scripting (XSS) vulnerabilities
being exploited on the site.

#### How to test

Intercept request to web-site with Burp or Fiddler and put some
suspicions XSS payload to one of params (like - \<xss 'test=" /\>) If
web-site responds with exception then everything is OK.

#### Remediation

Turn on RequestValidation in web.config.

`  `
`<configuration>`
`  <system.web>`
`    <pages validateRequest="true" />`

-----

### Event validation misconfiguration

#### Description

When web-site actively uses extended controls like ListBox, ComboBox etc
All control states are saved between request in __EVENTVALIDATION
param. For security reasons to prevent manipulation with those params
ASP.NET has Event Validation scheme that signs __EVENTVALIDATION param
with HMAC like __VIEWSTATE.

#### How to test

1.  Intercept request to web-site with Burp or Fiddler and remove
    __EVENTVALIDATION param if web-site responds with Validation Error
    then MAC Validation is ON
2.  Inside web page source code find __EVENTVALIDATION param, decode
    its value with base64. Check last bytes that follows "dd", if exists
    then there is EVENTVALIDATION validation is on.

#### Remediation

Turn on EventValidation in web.config.

`  `
`<configuration>`
`  <system.web>`
`    <pages enableEventValidation="true"/>`
`  `
`<configuration>`
`  <system.web>`
`    <machineKey validation="AES" validationKey="AutoGenerate,IsolateApps" />`

-----

### Debug mode misconfiguration

#### Description

Application in debug mode expose lot of system information inside error
messages if any exception occurs.

#### How to test

1.  Make a request

[`http://[target]/`](http://%5Btarget%5D/)<random_page>`.aspx`

1.  Another way is if Page receive param (like ID) you can duplicate
    this param in request ID=1\&ID=1. That will cause framework to show
    error page.

If custom error mode in turned off you will see detailed error
description formed by asp.net framework. And if debug mode is ON then
inside stack trace of error you will see even line of code where error
occurred

#### Remediation

Turn off Debug Mode in web.config

<compilation debug="false" />` `

-----

### ASP.NET Padding Oracle Vulnerability (POET) misconfiguration

#### Description

The vulnerability could allow information disclosure. An attacker who
successfully exploited this vulnerability could read data, such as the
view state, which was encrypted by the server. This vulnerability can
also be used for data tampering, which, if successfully exploited, could
be used to decrypt and tamper with the data encrypted by the server.
Microsoft .NET Framework versions prior to Microsoft .NET Framework 3.5
Service Pack 1 are not affected by the file content disclosure portion
of this vulnerability.

#### How to test

Use padBuster.pl script to test your web site.

#### Remediation

Install patch for MS10-70 security update.

-----

### References

  - <https://asafaweb.com>
  - <http://msdn.microsoft.com/en-us/library/bb386420.aspx>
  - <http://carnal0wnage.attackresearch.com/2012/05/from-low-to-pwned-12-traceaxd.html>
  - <http://www.ucertify.com/article/what-is-traceaxd.html>
  - <https://msdn.microsoft.com/ru-ru/library/h0hfz6fc(v=vs.85>).aspx
  - <https://msdn.microsoft.com/en-us/library/h0hfz6fc(v=vs.100>).aspx
  - <http://www.troyhunt.com/2011/12/has-hash-dos-patch-been-installed-on.html>
  - <https://technet.microsoft.com/en-us//library/security/ms11-100>
  - <http://code.google.com/p/elmah/>
  - <http://www.troyhunt.com/2012/01/aspnet-session-hijacking-with-google.html>
  - <http://stackoverflow.com/questions/1245364/securing-elmah-in-asp-net-website>
  - <https://code.google.com/p/elmah/wiki/SecuringErrorLogPages>
  - <https://code.google.com/p/elmah/wiki/DotNetSlackersArticle#Declaring_configuration_sections>
  - <http://www.troyhunt.com/2012/02/shhh-dont-let-your-response-headers.html>
  - <http://www.troyhunt.com/2013/03/c-is-for-cookie-h-is-for-hacker.html>
  - <http://www.troyhunt.com/2013/05/clickjack-attack-hidden-threat-right-in.html>
  - <http://www.troyhunt.com/2013/09/understanding-and-testing-for-view.html>
  - <https://msdn.microsoft.com/en-us/magazine/gg309184.aspx>
  - <https://msdn.microsoft.com/en-us/library/aa479501.aspx>
  - <https://msdn.microsoft.com/ru-ru/library/vstudio/w8h3skw9(v=vs.100>).aspx
  - <https://msdn.microsoft.com/en-us/magazine/gg309184.aspx>
  - <http://odetocode.com/blogs/scott/archive/2006/03/21/asp-net-event-validation-and-invalid-callback-or-postback-argument-again.aspx>
  - <https://msdn.microsoft.com/en-us/library/system.web.ui.page.enableeventvalidation.aspx>
  - <https://msdn.microsoft.com/en-us/magazine/gg309184.aspx>
  - <https://msdn.microsoft.com/en-us/library/e8z01xdh.aspx>
  - <http://blog.gdssecurity.com/labs/2010/10/4/padbuster-v03-and-the-net-padding-oracle-attack.html>
  - <https://technet.microsoft.com/library/security/ms10-070>
  - <http://blogs.technet.com/b/srd/archive/2010/09/17/understanding-the-asp-net-vulnerability.aspx>
  - <http://blog.mindedsecurity.com/2010/10/breaking-net-encryption-with-or-without.html>
  - <http://blog.mindedsecurity.com/2010/09/investigating-net-padding-oracle.html>