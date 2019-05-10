## The XSS/CRLF Injection plugin

### Overview

The XSS/CRLF plugin examines suspicious HTTP requests for cross-site
scripting and CRLF injection (HTTP response splitting) vulnerabilities.
Unlike other tools, the plugin doesn't crawl the site trying to discover
vulnerable URLs, instead it passively analyzes all HTTP conversations
passing through WebScarab. The plugin will inspect each request and
response to check if:

  - Any value of the GET/POST parameters is reflected in the body of the
    HTTP response, which indicates a potential for a reflected XSS
    vulnerability;
  - Any value of the GET/POST parameters is reflected in the HTTP
    headers of the HTTP response, which indicates a potential for a CRLF
    injection vulnerability;

The table in the upper half of the plugin's window will show all
suspicious HTTP requests. By clicking the "Check" button, the plugin
will attempt to perform a test to check whether the test strings for XSS
and CRLF injection vulnerabilities pass through successfully. If check
on a particular conversation was successful (i.e. test string went
through or new HTTP header was created) the conversation will appear in
the table below. If none of the test were successful lower table will be
empty.

**NOTE:** depending on vulnerability specifics and application,
automated testing may not produce reliable results (e.g. less than and
greater than characters are filtered, however exploitation of XSS is
still possible without use of these characters, for example if XSS
occurs within the 'script' tag).

For XSS, the plugin will send a user-controlled XSS test string as the
value of a potentially vulnerable parameter and check the response body
for the presence of the test string, if the string was discovered it may
indicate that application is vulnerable to cross-site scripting
vulnerability.

For CRLF injection (HTTP response splitting), the plugin will again send
the user-controlled CRLF test string, which is supposed to create a new
HTTP header, as a value of a potentially vulnerable parameter and check
the response HTTP headers for the presence of the new HTTP header
created by CRLF test string. If the header is present it may indicated
that application is vulnerable to response splitting.

### Limitations

Stored cross-site scripting vulnerabilities aren't supported yet.

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink") [Category:OWASP
Testing Project](Category:OWASP_Testing_Project "wikilink")