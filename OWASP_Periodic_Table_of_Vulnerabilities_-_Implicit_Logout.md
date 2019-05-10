[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Implicit Logout

### Root Cause Summary

Web applications have no simple way to know when a user has browsed away
from the site without explicitly logging out. In a shared computing
environment, a user can easily access the previous users' sensitive
data, even though those users might believe they had performed some
action that was the equivalent of logging out (closing the browser,
navigating to another site, clicking the home button, etc.).

### Browser / Standards Solution

Long term: define a new session management scheme to replace cookies,
which specifies how to handle implicit logout.

Short term: CSP should define a logout page or function which accepts
the session token value as a POST parameter (to prevent CSRF logout). If
the user no longer has any open pages on the site for any reason, the
browser should submit the session token from the session cookie
specified by the CSP as a cleanup activity. By default, the browser
should also discard any session cookies whenever there are no longer any
open pages on the corresponding site(s), as well.

### Perimeter Solution

None

### Generic Framework Solution

LONG TERM: Expose a handler for CSP policy.

SHORT TERM: Deploy JavaScript checks for onUnload handlers to
distinguish between a user leaving the site, closing the browser, and
navigating within the site. Automatically submit a logout form and
delete session cookies when the user leaves the site or closes the
browser window.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

JavaScript detection for onUnload events is extremely intrusive to
implement for applications that aren't already using XHR for page
updates instead of traditional navigation. Except for applications with
very sensitive data that must be used in "kiosk" scenarios, it may be
preferable to wait for browser changes to address this issue, and
instead simply warn users not to use the application in a shared
computing environment. Users and site owners may have different
expectations about logout behavior, suggesting per-site policy
configuration and possibly custom user agent settings.

### References

[Session Management Cheat
Sheet](Session_Management_Cheat_Sheet#Force_Session_Logout_On_Web_Browser_Window_Close_Events "wikilink")
[IETF HTTP Authentication
drafts](http://datatracker.ietf.org/wg/httpauth/)