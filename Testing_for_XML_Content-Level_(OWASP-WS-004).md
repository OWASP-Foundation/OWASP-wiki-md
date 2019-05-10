## Brief Summary

Content-level attacks target the server hosting a web service and any
applications that are utilized by the service, including web servers,
databases, application servers, operating systems, etc. Content-level
attack vectors include 1) SQL Injection or XPath injection 2) Buffer
Overflow and 3) Command Injection.

## Description of the Issue

Web Services are designed to be publicly available to provide services
to clients using the Internet as the common communication protocol.
These services can be used to leverage legacy assets by exposing their
functionality via SOAP using HTTP. SOAP messages contain method calls
with parameters, including textual data and binary attachments,
requesting the host to perform some function - database operations,
image processing, document management, etc. Legacy applications exposed
by the service may be vulnerable to malicious input that when previously
limited to a private network was not an issue. In addition, because the
server hosting the Web Service will need to process this data, the host
server may be vulnerable if it is unpatched or otherwise unprotected
from malicious content (e.g., plain text passwords, unrestricted file
access).

An attacker can craft an XML document (SOAP message) that contains
malicious elements in order to compromise the target system. Testing for
proper content validation should be included in the web
application-testing plan.

## Black Box testing and example

**Testing for SQL Injection or XPath Injection vulnerabilities**

1\. Examine the WSDL for the Web Service.
[WebScarab](OWASP_WebScarab_Project "wikilink"), an OWASP tool for many
web application testing functions, has a WebService plugin to execute
web services functions.

![`Image:482WebScarab1.png`](482WebScarab1.png
"Image:482WebScarab1.png")

2\. In WebScarab, modify the parameter data based on the WSDL definition
for the parameter.

![`Image:482WebScarab2.png`](482WebScarab2.png
"Image:482WebScarab2.png")

Using a single quote ('), the tester can inject a conditional clause to
return true, 1=1 when the SQL or XPath is executed. If this is used to
log in, if the value is not validated, the login will succeed because
1=1.

The values for the operation:

<userid>myuser</userid> <password>' OR 1=1</password>

could translate in SQL as: WHERE userid = 'myuser' and password = '' OR
1=1 and in XPath as: //user\[userid='myuser' and password='' OR 1=1\]

**Result Expected:**

A tester can then continue using the web service in a higher privilege
if authenticated, or execute commands on the database.

**Testing for buffer overflow vulnerabilities:**

It is possible to execute arbitrary code on vulnerable web servers via a
web service. Sending a specially-crafted HTTP request to a vulnerable
application can cause an overflow, and allow an attacker to execute
code. Using a testing tool like Metasploit or developing your own code,
it is possible to craft a reusable exploit test. MailEnable
Authorization Header Buffer Overflow is an example of an existing Web
Service Buffer Overflow exploit, and is available from Metasploit as
"mailenable_auth_header." The vulnerability is listed at the Open
Source Vulnerability Database.

**Result Expected:**

Execution of arbitrary code to install malicious code.

## Grey Box testing and examples

1\. Are parameters checked for invalid content - SQL constructs, HTML
tags, etc.? Use the [OWASP XSS
guide](Cross-site_Scripting_\(XSS\) "wikilink") or the specific language
implementation, such as htmlspecialchars() in PHP and never trust user
input.

2\. To mitigate buffer overflow attacks, check the web server,
application servers, and database servers for updated patches and
security (antivirus, malware, etc.).

## References

**Whitepapers**
\* OSVDB - <http://www.osvdb.org>

**Tools**
\* [OWASP WebScarab](OWASP_WebScarab_Project "wikilink"): Web Services
plugin

\[\[Category:FIXME|link not working

  - NIST Draft publications (SP800-95): "Guide to Secure Web Services" -
    <http://csrc.nist.gov/publications/drafts/Draft-SP800-95.pdf>

<!-- end list -->

  - MetaSploit - <http://www.metasploit.com>

Note: this site is mentioned in the text, so a change to the text is
needed

\]\]

[these images are blurry, can we replace
them?](Category:FIXME "wikilink")