[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Session Fixation

### Root Cause Summary

An attacker can force a victim to use a session ID that is already known
to the attacker; if the application does not change the ID when the
privileges associated with the session change, the attacker then has
access to those privileges via the known session ID.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework must not create new sessions using session IDs supplied by
the HTTP client.

The framework must discard an existing session ID and generate a new
token for a session any time the privilege level of the session changes.
Examples of privileges changing include:

  - A user logging in after starting an anonymous session
  - An administrator authorizing access to secure features during a
    session where only user-level privileges are being used
  - A user switching to a different user account during an active
    session with another account
  - An anonymous user submitting sensitive data which will be stored in
    session state and later echoed back to the user

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[Session Management Cheat
Sheet](https://www.owasp.org/index.php/Session_Management_Cheat_Sheet)
[OWASP Session Fixation
Page](https://www.owasp.org/index.php/Session_fixation)
[Session Fixaction
(WASC)](http://projects.webappsec.org/w/page/13246960/Session%20Fixation)