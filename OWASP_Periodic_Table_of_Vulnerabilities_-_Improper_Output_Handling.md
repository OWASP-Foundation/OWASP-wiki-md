[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Improper Output Handling

## Root Cause Summary

The root cause of improper output handling is an application passing
along data and not interrogated consistently through mechanisms such as
filtering or sanitization. Improper output handling can occur while
passing data to applications or between tiers within an application
architecture. Not validating output data may allow an application to
pass along improper output encoding or escaping, invalid data, incorrect
data, or malicious content to the consumer.

## Browser / Standards Solution

None

## Perimeter Solution

None

## Generic Framework Solution

Provide context-sensitive encoders for all common data types in all
output contexts, ensuring no custom code can write directly to output.

## Custom Framework Solution

Provide context-sensitive encoders for all custom data types in all
output contexts, ensuring no custom code can write directly to output.

## Custom Code Solution

None

## Discussion / Controversy

None

## References

[WASC - Improper Output
Handling](http://projects.webappsec.org/w/page/13246934/Improper%20Output%20Handling)