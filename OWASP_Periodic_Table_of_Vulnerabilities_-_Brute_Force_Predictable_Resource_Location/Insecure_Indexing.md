[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Brute Force Predictable Resource Location/Insecure Indexing

### Root Cause Summary

Server-side resources including admin pages, file backups, uploaded
files, logs, and sample files exist in easy-to-guess locations. Data
resources are referenced by their auto-incremented primary key, making
it easy for attackers to guess other valid values or infer transaction
volumes.

### Browser / Standards Solution

None

### Perimeter Solution

The perimeter should detect spikes in 40X HTTP responses from the web
server or application server. If the requests are authenticated, the
perimeter should send an account lockout signal to the application. If
the requests are unauthenticated, the perimeter should introduce a
CAPTCHA, JavaScript challenge, or similar anti-automation measure.

### Generic Framework Solution

The framework should provide a random GUID obfuscator for all parameter
values to hide the underlying object identifiers.

The framework should proxy all requests for dynamic file content (as
opposed to static content) with random GUID identifiers.

The framework should segregate administrative interfaces from user
interfaces using IP source address whitelisting, client-side
certificates, and other restrictions.

The framework should be designed to store all configuration files,
uploaded files, and any other content that does not need to be served
directly by the web server outside the web root or on a separate
database server accessible only via application APIs.

### Custom Framework Solution

The custom framework should enforce authentication/authorization checks
on all dynamic content. Custom administrative interfaces should be built
on top of generic framework administrative access platform, segregated
from user interfaces.

### Custom Code Solution

None

### Discussion / Controversy

GUID obfuscators are a form of security through obscurity, and prevent
only the information leakage aspect of auto-incremented object
identifiers. Authentication and authorization must still be enforced in
order to prevent unwanted access to resources, even if they are no
longer predictable.

[Directory
indexing](OWASP_Periodic_Table_of_Vulnerabilities_-_Directory_Indexing "wikilink")
is a separate topic; indexing in this case refers to object identifiers,
not directory listings.

### References

[Forceful browsing](Forced_browsing "wikilink")
\[<http://projects.webappsec.org/w/page/13246953/Predictable%20Resource%20Location>|
Predictable Resource Location (WASC)\]
\[<https://en.wikipedia.org/wiki/Globally_unique_identifier>| Globally
Unique Identifier (GUID)\]