[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Fingerprinting

### Root Cause Summary

One or several components of the underlying software and framework leak
version information. This could help an attacker to identify which
components are vulnerable. This issue is mitigated by removing all
version information.

### Browser / Standards Solution

None

### Perimeter Solution

Infrastructure should not leak information which can be used to identify
the specific version of platform or infrastructure technology. Perimeter
technologies should strip all such version information from outgoing
responses.

### Generic Framework Solution

  - URL structure should not reveal the underlying technology. Default
    content should be removed when possible.
  - Make sure that only generic error pages are shown without showing
    any information of the underlying system.
  - Remove all development and debugging tools.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[Information Exposure Through Sent Data (CWE-201,
MITRE)](http://cwe.mitre.org/data/definitions/201.html)
[File and Directory Information Exposure (CWE-538,
MITRE)](http://cwe.mitre.org/data/definitions/538.html)