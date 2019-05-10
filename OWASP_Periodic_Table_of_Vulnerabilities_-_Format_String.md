[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Format String

## Root Cause Summary

The root cause of the format string is attacker having the ability to
control or write completely the format string used to format data input
for some C,C++, and Assembly functions such as fprintf, printf, sprintf,
setproctitle, and syslog, potentially leading to buffer overflows or
data representation problems.

## Browser / Standards Solution

None

## Perimeter Solution

Alert and/or block on known format string signatures Generic Framework
Solution Prohibit access to vulnerable APIs and provide safe wrappers of
those APIs instead.

## Generic Framework Solution

Prohibit access to vulnerable APIs and provide safe wrappers of those
APIs instead.

## Custom Framework Solution

None

## Custom Code Solution

None

## Discussion / Controversy

None

## References

[OWASP - Format String](https://www.owasp.org/index.php/Format_String)

[OWASP Format string
attack](http://www.owasp.com/index.php?title=Format_string_attack&setlang=es)

[OWASP - Testing for Format
String](http://owasp.com/index.php?title=Testing_for_Format_String&setlang=es)

[WASC - Format
String](http://projects.webappsec.org/w/page/13246926/Format%20String)

[CAPEC-339: WASC Threat Classification 2.0 - WASC-06 - Format
String](http://capec.mitre.org/data/definitions/339.html)

[CWE-134: Uncontrolled Format
String](http://cwe.mitre.org/data/definitions/134.html)