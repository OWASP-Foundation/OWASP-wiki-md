[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Path Traversal

### Root Cause Summary

File resources are accessed using references constructed from
user-supplied data, allowing a malicious user to access files outside
the web root that were not intended to be exposed.

### Browser / Standards Solution

None

### Perimeter Solution

Perimeter and platform technologies should canonicalize all URLs and
path references, replacing relative paths with absolute paths wherever
possible.

The platform should be deployed with permissions that prevent the web
server process from accessing files outside the web root.

### Generic Framework Solution

The framework should provide safe libraries for accessing the file
system that canonicalize path references, enforce proper access control,
and prevent direct access to the filesystem. The libraries should have
the following features:

  - Canonicalization of file and path names, properly transforming null
    bytes and relative paths before all other processing takes place
  - A configuration-based whitelist of directories that are allowed to
    be accessed by the application
  - A role-based access control list to further limit access to
    whitelisted directories
  - A configuration-based whitelist of file extensions that may be
    accessed

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[Path Traversal](Path_Traversal "wikilink")
[Path Traversal
(WASC)](http://projects.webappsec.org/w/page/13246952/Path%20Traversal)
[Path Traversal (CWE)](http://cwe.mitre.org/data/definitions/22.html)