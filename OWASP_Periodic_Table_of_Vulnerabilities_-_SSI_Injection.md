[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### SSI Injection

## Root Cause Summary

The root cause of server-side includes/injection is the application's
failure to validate data before it is inserted into a server-side
interpreted HTML file. Some Web servers allow entering dynamic code to
static HTML pages making it possible for an attacker to send code to a
web application that will get executed by the web server and possibly
gain access to files or other exploits similiar to cross site scripting.

## Browser / Standards Solution

None

## Perimeter Solution

None

## Generic Framework Solution

Do not support SSI with dynamic file names.

## Custom Framework Solution

None

## Custom Code Solution

None

## Discussion / Controversy

SSI Injection is sometimes called Server-side Include

## References

[OWASP – Server-Side Includes (SSI)
Injection](https://www.owasp.org/index.php/Server-Side_Includes_\(SSI\)_Injection)

[OWASP - Testing for SSI Injection
(OWASP-DV-009)](https://www.owasp.org/index.php/Testing_for_SSI_Injection_\(OWASP-DV-009\))

[WASC - SSI
Injection](http://projects.webappsec.org/w/page/13246964/SSI%20Injection)

[CAPEC 101: Server Side Include (SSI)
Injection](http://capec.mitre.org/data/definitions/101.html)

[CWE-97: Improper Neutralization of Server-Side Includes (SSI) Within a
Web Page](http://cwe.mitre.org/data/definitions/97.html)