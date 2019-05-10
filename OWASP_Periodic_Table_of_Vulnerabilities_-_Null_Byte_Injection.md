[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Null Byte Injection

### Root Cause Summary

Null Byte Injection is an exploitation technique which uses URL-encoded
null byte characters (i.e. %00, or 0x00 in hex) to the user-supplied
data. This injection process can alter the intended logic of the
application and allow malicious adversary to get unauthorized access to
the system files.

### Browser / Standards Solution

None

### Perimeter Solution

Null bytes are rarely if ever needed in user input for web applications.
Perimeter defenses can simply look for null bytes in user input and
reject such requests safely.

### Generic Framework Solution

Programming languages and frameworks should provide safe functions and
libraries that automatically encode dynamic data in any context which
uses null bytes as control characters. In many cases, API's should fail
or otherwise remove null bytes from API input.

### Custom Framework Solution

None

### Custom Code Solution

Null bytes are rarely if ever needed in user input for web applications.
Perimeter defenses can simply look for null bytes in user input and
reject such requests safely.

### Discussion / Controversy

None

### References

[WASC Null Byte
Injection](http://projects.webappsec.org/w/page/13246949/Null%20Byte%20Injection)