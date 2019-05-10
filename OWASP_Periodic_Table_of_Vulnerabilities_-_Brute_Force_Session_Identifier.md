[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Brute Force Session Identifier / Session Prediction

### Root Cause Summary

Session tokens are generated in a predictable fashion or from a key
space that is too small to prevent guessing a token in reasonable time.
The application does not detect and prevent session brute forcing
attempts.

### Browser / Standards Solution

Define a new session management scheme which allows applications to
force session identifiers to be linked to SSL/TLS sessions or
client-side certificates, if available. Even if an attacker manages to
guess an active session ID, the ID won't be usable except over the
original negotiated SSL connection or a renegotiated SSL connection for
which the client is able to provide the HTTP session ID on the first
try. A session ID must not be valid over two currently active SSL
connections at the same time.

### Perimeter Solution

None

### Generic Framework Solution

Ensure that session identifiers are created using a secure random
algorithm, with enough entropy to make guessing infeasible during the
average lifetime of a session. The framework should check that an active
session does not already exist with the same ID as a newly generated
session token before issuing the token.

The application should be configurable to tie session IDs to SSL
sessions, tracking those sessions across renegotiations. Any token which
is sent over an SSL connection that isn't currently tied to the token
should be expired immediately and the associated session terminated or
suspended until the client successfully reauthenticates.

The application should be configurable to tie session IDs to source IP
addresses, and terminate/suspend any active session if subsequent
requests originate from a different IP. The configuration should allow
the setting to be enabled globally, or on a per-user or per-session
basis. (Users may choose to "opt in" to the restriction if they know
their IP address is unlikely to change during the session.)

The application should track the number of requests made with
invalid/expired session IDs and alert or block requests based on a
configurable rate limit. Malicious actors may be identified by source IP
address, a combination of browser fingerprinting features, or other
configurable fraud metrics.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

There are often perfectly legitimate reasons for a client IP to change
during a session, including IP NAT pooling and short DHCP lease periods.
A strict setting may only be appropriate for intranet applications or
extremely high-security features.

### References

[Insufficient Session-ID
Length](Insufficient_Session-ID_Length "wikilink")
[Brute Force
(WASC)](http://projects.webappsec.org/w/page/13246915/Brute%20Force)
[Credential and Session Prediction
(WASC)](http://projects.webappsec.org/w/page/13246918/Credential%20and%20Session%20Prediction)
[Insufficient Entropy
(CWE)](http://cwe.mitre.org/data/definitions/331.html)
[Current IETF State Management
(RFC 6265)](http://tools.ietf.org/html/rfc6265)
[IETF Session Continuation Problem
Statement](http://tools.ietf.org/html/draft-ietf-websec-session-continue-prob-00)
[IETF Channel ID
Proposal](http://tools.ietf.org/html/draft-balfanz-tls-channelid-01)