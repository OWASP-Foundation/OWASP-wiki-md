[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## XPath/XQuery Injection

### Root Cause Summary

The application unsafely incorporates user data into an XQuery or XPath
pattern which can change the logic of the query.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide a safe wrapper for XML search operations
which canonicalizes and parameterizes patterns or avoids injection
pitfalls altogether. Use only safe XQuery and XPath libraries or a
subset of those libraries which is not vulnerable to injection.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[OWASP Top 10 2010 - A1
Injection](Top_10_2010-A1-Injection "wikilink")
[XPath Injection](XPATH_Injection "wikilink")
\[<http://projects.webappsec.org/w/page/13247006/XQuery%20Injection>|
XQuery Injection (WASC)\]