## HTTP Request/Response Smuggling

### Root Cause Summary

Malformed HTTP requests and responses are interpreted differently by
proxies, web servers, or other systems which process HTTP along the
request/response path. This can allow a request or response to bypass
proxy filters or rules, poison caches, or cause the response from one
request to be incorrectly matched with another.

### Browser / Standards Solution

Tighten RFC standards to describe precise behavior for malformed
request/response data, including rules for handling duplicate headers.

### Perimeter Solution

  - Sanitize all HTTP headers, especially duplicates, by enforcing
    strict adherence to RFC
  - Sanitize both HTTP requests and response bodies, ensuring exact
    correspondence between Content-Length headers and body lengths
  - Avoid HTTP connection sharing
  - Enforce SSL to prevent proxy tampering
  - Provide configuration option to silently sanitize malformed data or
    return a 5XX error response

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Framework-level solutions for enforcing correct CRLF behavior and
preventing header manipulation are addressed by [OWASP Periodic Table of
Vulnerabilities - HTTP Response
Splitting](OWASP_Periodic_Table_of_Vulnerabilities_-_HTTP_Response_Splitting "wikilink").
Tangentially described by the [end-to-end
principle](http://www.ietf.org/rfc/rfc3724.txt). May require solving the
multiple parser problem and enforcement of end-to-end principle all the
way through frameworks and custom code.

### References

[HTTP Request
Smuggling](http://www.securiteam.com/securityreviews/5GP0220G0U.html)
[HTTP Message Splitting, Smuggling and Other Animals (Amit Klein,
OWASP)](http://www.owasp.org/images/1/1a/OWASPAppSecEU2006_HTTPMessageSplittingSmugglingEtc.ppt)
[Message Header Extensions (RFC)](http://www.ietf.org/rfc/rfc2047.txt)
[Response Smuggling
(WASC)](http://projects.webappsec.org/w/page/13246930/HTTP%20Response%20Smuggling)