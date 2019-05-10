[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## XML External Entities

### Root Cause Summary

The XML parser is configured to process an unsafe DTD which includes
external references to resources on the filesystem or other internal
resources.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Disable external entity processing in the XML parser. Use strict,
static, internally-defined DTDs and discard DTDs defined by XML
documents. Force the application to load external content safely using
framework file access code, instead of delegating the work to the XML
parser.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

XXE is an unsafe development pattern and should be discarded in favor of
safer methods of building documents from multiple sources.

### References

[XML External Entity
Processing](XML_External_Entity_\(XXE\)_Processing "wikilink")
[XML External Entity (XXE) Prevention Cheat
Sheet](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")
\[<http://projects.webappsec.org/w/page/13247003/XML%20External%20Entities>|
XML External Entities (WASC)\]
\[<http://cwe.mitre.org/data/definitions/611.html>| CWE-611: Improper
Restriction of XML External Entity Reference ('XXE')\]