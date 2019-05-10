[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## OS Commanding

### Root Cause Summary

OS-level calls are constructed using dynamic data, allowing an attacker
to append additional function calls or manipulate parameters of the
original call.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

None

### Custom Framework Solution

Build safe wrappers for system calls which prevent dynamic data from
changing the intended meaning of the call.

### Custom Code Solution

None

### Discussion / Controversy

Many common system calls already have safe wrappers in generic
application frameworks. Thus, most unsafe calls are likely to be made in
the attempt to access application-specific batch processes or system
features, and so must have a custom framework wrapper to ensure that the
intended syntax is generated safely.

### References

[Command Injection](Command_Injection "wikilink")
[OS Commanding
(WASC)](http://projects.webappsec.org/w/page/13246950/OS%20Commanding)
[OS Command Injection
(CWE)](http://cwe.mitre.org/data/definitions/78.html)