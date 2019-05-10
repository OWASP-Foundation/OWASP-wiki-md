[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Improper Input Handling

## Root Cause Summary

The root cause of improper input handling is the application trusting,
not validating or not correctly validating inputs. All inputs should be
considered untrusted as they can come from a variety of mechanisms
including human, browsers or devices, transferred in various formats and
come in many formats. Accepting untrusted input may leave the
application vulnerable to attacks such as Buffer Overflows, SQL
Injection, OS Commanding, or Denial of Service.

## Browser / Standards Solution

None

## Perimeter Solution

None

## Generic Framework Solution

Provide canonicalization and positive validation APIs for common data
types, with configurable rules to reject or sanitize bad data.

## Custom Framework Solution

Provide canonicalization and positive validation APIs for custom data
types, strictly enforcing business rules, with configurable rules to
reject or sanitize bad data.

## Custom Code Solution

Never use primitives in custom code.

## Discussion / Controversy

None

## References

[WASC - Improper Input
Handling](http://projects.webappsec.org/w/page/13246933/Improper%20Input%20Handling)

[CWE-20: Improper Input
Validation](http://cwe.mitre.org/data/definitions/20.html)