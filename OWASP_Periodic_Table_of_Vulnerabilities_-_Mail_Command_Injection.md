[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Mail Command Injection

### Root Cause Summary

An application includes dynamic data in SMTP communications without
sanitizing or encoding the data. The structure of the data changes the
meaning of the mail commands or allows an attacker to inject new
commands.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide safe libraries for interacting with mail
server systems which automatically encodes and escapes data to prevent
alterations to the intended functionality.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[Mail Command Injection
(WASC)](http://projects.webappsec.org/w/page/13246948/Mail%20Command%20Injection)
[IMAP/SMTP Command Injection
(CAPEC-183)](http://capec.mitre.org/data/definitions/183.html)