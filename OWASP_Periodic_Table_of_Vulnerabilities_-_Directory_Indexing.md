[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Directory Indexing

### Root Cause Summary

A misconfigured server can show a directory listing, which could
potentially yield sensitive information to an attacker.

### Browser / Standards Solution

None

### Perimeter Solution

  - Disable directory listings in the web- or application-server
    configuration by default.
  - Restrict access to unnecessary directories and files.
  - Create an index (default) file for each directory.

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[Information Exposure Through Directory Listing
(Mitre)](http://cwe.mitre.org/data/definitions/548.html)
[Security Misconfiguration
(OWASP)](https://www.owasp.org/index.php/Top_10_2010-A6-Security_Misconfiguration)
[Insecure Indexing
(OWASP)](https://www.owasp.org/index.php/File_System#Insecure_Indexing)