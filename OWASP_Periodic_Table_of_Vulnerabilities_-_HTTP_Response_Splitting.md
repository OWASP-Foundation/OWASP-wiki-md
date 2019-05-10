[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## HTTP Response Splitting

### Root Cause Summary

The application allows CRLF characters to be injected into HTTP response
headers, which allows an attacker to inject a malicious response body in
place of the intended response or force a redirect to a malicious
resource.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Encode all CRLF pairs in dynamic data before writing the data in the
context of an HTTP response header. Prevent direct access to response
headers by forcing all header write requests to use a safe API.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Perimeter solutions for enforcing strict HTTP compliance are addressed
by [OWASP Periodic Table of Vulnerabilities - HTTP Request/Response
Smuggling](OWASP_Periodic_Table_of_Vulnerabilities_-_HTTP_Request/Response_Smuggling "wikilink").

[Should String Be An Abstract Class (John
Wilander)](http://appsandsecurity.blogspot.com.au/2013/05/should-string-be-abstract-class.html)

### References

[HTTP Response Splitting](HTTP_Response_Splitting "wikilink")
[HTTP Response Splitting
(WASC)](http://projects.webappsec.org/w/page/13246931/HTTP%20Response%20Splitting)