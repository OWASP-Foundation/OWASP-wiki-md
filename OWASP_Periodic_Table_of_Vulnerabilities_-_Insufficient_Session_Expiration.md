[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Session Expiration

### Root Cause Summary

The application either does not implement an inactivity timeout or an
absolute timeout, or the timeouts are too long to provide sufficient
risk mitigation. The application does not provide a logout feature, or
the feature does not actively terminate the user's session.

### Browser / Standards Solution

Currently, session management is normally implemented with cookies and
web frameworks that are custom to each solution. There is work underway
to define a new standard for instructing the browser about session
timeouts and how to handle them.

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide a configurable option for setting the
inactivity and absolute timeouts for sessions. Timeouts should have
secure defaults (e.g. 20 minutes of inactivity, 8 hours absolute
lifetime). The framework should provide a configuration option to
automatically save session state and allow the session to continue if
the user successfully reauthenticates after the session times out.

The application should provide the user the option to log out and
destroy the session immediately without waiting for either timer to
expire.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Although most web frameworks support idle timeout and few web frameworks
support absolute timeout, there are cases where both of these
conjectures are not true. Custom session handling mechanisms require
much of this logic to be implemented "by hand". Problem space overlap
current working group specifications for HTTPAuth and WebSec.

### References

[Session Management Cheat
Sheet](https://www.owasp.org/index.php/Session_Management_Cheat_Sheet)
[Insufficient Session Expiration
(WASC)](http://projects.webappsec.org/w/page/13246944/Insufficient%20Session%20Expiration)
[Insufficient Session Expiration
(CWE)](http://cwe.mitre.org/data/definitions/613.html)