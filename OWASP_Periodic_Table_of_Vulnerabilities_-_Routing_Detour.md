[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Routing Detour

### Root Cause Summary

This is a man in the middle type of attack, where (XML) content
processors can be injected to route sensitive information to an
attacker-controlled outside location. The attacker can modify the
contents of the package and send it back to the original processor,
unaware of the modifications.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Provide configuration-based whitelist for WS Routing destinations.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[XML Routing Detour Attacks
(MITRE)](http://capec.mitre.org/data/definitions/219.html)
[Routing Detour
(WASC)](http://projects.webappsec.org/w/page/13246956/Routing%20Detour)