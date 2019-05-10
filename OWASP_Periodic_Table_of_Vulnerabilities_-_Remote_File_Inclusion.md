[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Remote File Inclusion

### Root Cause Summary

The application loads data from an attacker-controlled resource at
runtime, enabling a variety of malicious activities. Either the source
address or the resource itself (or both) may be under the attacker's
control.

### Browser / Standards Solution

Define a standard for safe inclusion of 3rd-party code and content which
enforces namespace separation and mediates namespace/DOM access.

The standard should provide support for the following content types:

  - 3rd-party images
  - Active content such as Flash, Applets, ActiveX or other OBJECT
    content
  - IFRAMEd content
  - 3rd-party SCRIPT

The standard should allow for the content to be safely rendered in both
of the following scenarios:

1.  The content is loaded by the browser after the containing page is
    fully constructed by the web server.
2.  The content is embedded in the containing page by the web server
    before it is served to the browser.

### Perimeter Solution

None

### Generic Framework Solution

Provide a configurable white list of 3rd-party domains which are allowed
to serve inline content, and block file inclusion from all other
domains.

Provide a proxy library to sanitize/sandbox third-party code and content
for safe inclusion (e.g. Caja).

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

This issue is closely related to [Weak Authentication
Methods](OWASP_Periodic_Table_of_Vulnerabilities_-_Weak_Authentication_Methods "wikilink"),
which allows malicious third parties to trick users into giving away
login credentials. The standards solution is also closely related to
[Cross-Site
Scripting](OWASP_Periodic_Table_of_Vulnerabilities_-_Cross-Site_Scripting_\(XSS\) "wikilink").
Most use cases may be already solved by `seamless` and `sandbox`
attributes of `IFRAME` elements.

### References

[Top 10 2007-Malicious File
Execution](Top_10_2007-Malicious_File_Execution "wikilink")
[PHP File Inclusion](PHP_File_Inclusion "wikilink")
[Remote File Inclusion
(WASC)](http://projects.webappsec.org/w/page/13246955/Remote%20File%20Inclusion)
[PHP Remote File Include
(CWE)](http://cwe.mitre.org/data/definitions/98.html)
[Content Security
Policy](https://developer.chrome.com/extensions/contentSecurityPolicy.html)
[Google Caja](https://developers.google.com/caja/)
[IFRAME HTML Element Living
Standard](http://www.whatwg.org/specs/web-apps/current-work/multipage/the-iframe-element.html)