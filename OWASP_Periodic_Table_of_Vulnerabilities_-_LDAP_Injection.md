[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## LDAP Injection

### Root Cause Summary

LDAP queries are formed using dynamic data without performing proper
encoding, allowing the data to change the functional meaning of the
query.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide safe libraries for interacting with LDAP
servers which automatically encode unsafe data. The framework should not
allow application code to directly interact with LDAP servers.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[LDAP injection](LDAP_injection "wikilink")
[LDAP Injection
(WASC)](http://projects.webappsec.org/w/page/13246947/LDAP%20Injection)
[LDAP Injection (CWE)](http://cwe.mitre.org/data/definitions/90.html)