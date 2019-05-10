[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Denial of Service (Application Based)

## Root Cause Summary

The root cause of an Application Based denial of service is when an
attacker uses/exhausts/depletes all of the resources (such as bandwidth,
database connections, disk storage, CPU, memory, threads, or application
specific resources) on a system preventing legitimate users from using
the system. To prevent depletion of resources the application must
restrict the size or amount of resources that are requested or used.

## Browser / Standards Solution

None

## Perimeter Solution

Perimeter anti-automation for application-based DoS is identical to
[Generic Brute
Force](OWASP_Periodic_Table_of_Vulnerabilities_-_Brute_Force_\(Generic\)_/_Insufficient_Anti-automation "wikilink").

## Generic Framework Solution

None

## Custom Framework Solution

None

## Custom Code Solution

Profile resource-dependent transactions and build transaction queues and
alerting when queues reach thresholds. Enforce transaction-based rate
limits.

## Discussion / Controversy

Denial of service vulnerabilities have other names including “resource
exhaustion” and “resource depletion” and there are other types of denial
of service attacks different from application including network and
connection based.

## References

[OWASP - Application Denial of
Service](https://www.owasp.org/index.php/Application_Denial_of_Service)

[CWE-400: Uncontrolled Resource Consumption ('Resource
Exhaustion')](http://cwe.mitre.org/data/definitions/400.html)

[CAPEC -119: Resource
Depletion](http://capec.mitre.org/data/definitions/119.html)