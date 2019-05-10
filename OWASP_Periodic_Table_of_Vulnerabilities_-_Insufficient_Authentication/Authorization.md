[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Authentication/Authorization

### Root Cause Summary

Incorrect verification of identity and permissions can result in an
unauthorized attacker accessing sensitive data or functionality.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Enforce a proven authentication and authorization framework scheme which
emphasizes policy-based configuration files over hard-coded
authentication/authorization checks wherever possible.

Deny all access by default, and explicitly grant access per resource.

Enforce data storage outside of web roots to prevent requests which
bypass the application's access control policy.

### Custom Framework Solution

None

### Custom Code Solution

Always apply least-privilege principle to all transactions and data
access. Define access control matrix for all features and implement
policy before implementing the feature.

### Discussion / Controversy

None

### References

[Guide to Authorization
(OWASP)](https://www.owasp.org/index.php/Guide_to_Authorization)
[Failure to Restrict URL Access
(OWASP)](https://www.owasp.org/index.php/Top_10_2010-A8-Failure_to_Restrict_URL_Access)
[Insufficient Authentication
(WASC)](http://projects.webappsec.org/w/page/13246939/Insufficient%20Authentication)