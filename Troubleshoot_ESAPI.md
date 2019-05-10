### I am not receiving any compilation errors in Eclipse, but my web server can't find ESAPI

  - Be sure that ESAPI is being exported to your web server when the
    server starts. To do this:

<!-- end list -->

1.  Right-click your project in the Navigator and choose "Properties".
2.  Select "Java EE Module Dependencies" from the list on the left.
3.  If the ESAPI JAR is already listed, be sure it is checked off on the
    list.
4.  If the ESAPI JAR is not listed, add it with "Add JAR" or "Add
    External JAR".
5.  Save and restart your web server.

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")