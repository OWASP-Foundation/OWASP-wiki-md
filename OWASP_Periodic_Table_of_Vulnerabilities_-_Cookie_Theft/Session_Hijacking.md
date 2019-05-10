[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Cookie Theft/Session Hijacking

### Root Cause Summary

It's possible for an attacker to steal and reuse session identifiers or
other sensitive cookie values when they are stored or transmitted
insecurely.

### Browser / Standards Solution

Define a new standard for transmitting session identifiers and managing
them within the browser, such as a new request/response header to be
used instead of cookies. The standard should include a mechanism to tie
the session identifier to the SSL session on both the browser and the
server.

### Perimeter Solution

  - Make sure that all session identifiers are transmitted over an
    encrypted protocol.
  - Terminate/regenerate the session if the session token is transmitted
    insecurely (either in clear text or as part of the URL), or signal
    to the application to do so.
  - Enforce the Secure and HttpOnly flags on sensitive cookies using a
    Web Application Firewall.
  - Ensure that session identifiers are transmitted only using the SSL
    session where they originated. Track sessions across SSL
    renegotiations and integrate with framework solutions to support
    common SSL termination/reencryption architectures.

### Generic Framework Solution

The framework should prevent leakage of session tokens as much as
possible, using the following strategies:

  - The framework should provide a centralized cookie management API
    which prevents direct access to cookies. By default, cookies should
    be handled according to the following rules, which must be
    explicitly overridden if a developer has a specific need for a
    cookie with unsafe properties.
      - Apply Secure and HttpOnly flags.
      - Set the Domain and Path parameters for the cookie correctly.
      - Automatically check for cookie support and instruct the user how
        to enable cookies or upgrade the browser to a version that
        supports the required cookie features.
      - Provide a configurable option to support "cookieless sessions",
        by passing the session ID as a POST parameter on every form.
      - Expose a simple administrative interface for setting P3P rules.
      - Automatically validate and signal when the number of cookies in
        use or the size of cookie data exceeds that which is commonly
        supported by browsers.
      - Prevent application code from overwriting or otherwise
        manipulating the session cookie. Possibly prohibit the
        application from accessing the session token at all.
  - The framework should prevent session tokens from being included in
    URLs or accepted as URL parameters.

The framework should detect evidence of session hijacking and
proactively terminate compromised sessions using the following
strategies:

  - Alert the user and deauthorize the oldest session when multiple
    simultaneous logins are detected. Multiple simultaneous logins are
    prohibited by default, but may be enabled by changing a
    configuration setting.
  - Terminate session and send security SNMP trap or other configurable
    message if User-Agent string or other client fingerprinting changes.
  - Tie the session ID to the SSL session and provide configurable
    options for actions to take if the session ID is transmitted over a
    new SSL session. Expose integration points with perimeter
    technologies to facilitate SSL termination, renegotiation, and other
    transitions.
  - Provide the option to the user when logging in to pin the session to
    the originating IP.

The framework should provide a configurable option for automatically
changing the session identifier transparently during a session: never,
after a set time period, or a set number of requests.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Enforcing short session timeouts helps to mitigate the risk of Session
Hijacking, but this is addressed by [Insufficient Session
Expiration](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Session_Expiration "wikilink").

### References

[Session Management Cheat
Sheet](Session_Management_Cheat_Sheet "wikilink")
[Insufficient Session Expiration
(WASC)](http://projects.webappsec.org/w/page/13246944/Insufficient%20Session%20Expiration)
[Insufficient Session Expiration
(CWE)](http://cwe.mitre.org/data/definitions/613.html)
[IETF Session Continuation
Proposal](https://tools.ietf.org/html/draft-ietf-websec-session-continue-prob-00)