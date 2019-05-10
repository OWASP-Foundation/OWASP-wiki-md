[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Weak HTTP Authentication Methods

### Root Cause Summary

Usage of weak HTTP authentication methods makes it easy for an attacker
to intercept login credentials, replay them to other hosts, and trick
users into providing the credentials to the wrong location. Basic and
Digest are considered weak authentication methods: Basic has a weak
'encryption' mechanism and is the least favorable authentication method
of the two.

### Browser / Standards Solution

Define a replacement for HTTP authentication methods that includes at
least the following properties:

  - Clearly identifies the host that is requesting authentication
    credentials
  - Does not allow authentication over clear-text channels unless the
    authentication protocol specifically addresses eavesdropping.
  - Does not allow authentication transactions to be replayed or
    authorization tokens to be reused
  - Provides chrome which is hard to spoof, with provisions for
    user-specific images similar to SiteKey or other implementations.
    Images may be specified by the requesting site, the user profile on
    the browser, or both.
  - Does not allow cross-domain authentication requests by default. If
    cross-domain authentication is desired by a parent site, a white
    list of domains which are allowed to be authenticated should be
    defined by CSP or similar site policy.

### Perimeter Solution

Disable and block all authentication methods so that only forms-based
authentication and SSL client certificates are allowed.

Whitelist or proxy all inlined content in order to block malicious
authentication requests.

### Generic Framework Solution

Implement support for features of new standards-based solution, as
necessary.

Require a whitelist for all inlined 3rd-party content, or load the
content by proxy in order to block malicious authentication requests.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

SiteKey is a server-side technique for authentication of the server.

### References

[HTTP Authentication: Basic and Digest Access Authentication
(IETF)](http://tools.ietf.org/html/rfc2617)
[Authentication Cheat Sheet
(OWASP)](https://www.owasp.org/index.php/Authentication_Cheat_Sheet)
[BofA Site
Key](https://www.bankofamerica.com/privacy/online-mobile-banking-privacy/sitekey.go)
[IETF RESTful auth
proposal](https://tools.ietf.org/html/draft-williams-http-rest-auth-01)
[IETF HTTP Authentication
Proposals](http://datatracker.ietf.org/wg/httpauth/)
[Fast Identity Online (FIDO) Alliance](http://fidoalliance.org/)