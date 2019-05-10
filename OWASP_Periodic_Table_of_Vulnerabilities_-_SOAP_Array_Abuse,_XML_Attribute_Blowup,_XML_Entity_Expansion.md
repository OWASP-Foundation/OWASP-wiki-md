[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## SOAP Array Abuse, XML Attribute Blowup, XML Entity Expansion

### Root Cause Summary

Some features of the XML specification can be abused if XML parsers do
not safely handle recursive element definitions or array declarations.

### Browser / Standards Solution

None

### Perimeter Solution

Perimeter technologies should perform strict schema validation against
all incoming XML documents. The validation process should enforce the
following configurable limits on XML object definitions:

  - The maximum array size (as a product of the number of rows and
    columns)
  - The maximum number of elements
  - The maximum number of attributes per element
  - The maximum size of entity definitions
  - The maximum number of references to entity definitions

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[SOAP Array Abuse
(WASC)](http://projects.webappsec.org/w/page/13246962/SOAP%20Array%20Abuse)
[XML Attribute Blowup
(WASC)](http://projects.webappsec.org/w/page/13247001/XML%20Attribute%20Blowup)
[XML Entity Expansion
(WASC)](http://projects.webappsec.org/w/page/13247002/XML%20Entity%20Expansion)