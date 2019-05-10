[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Integer Overflow / Underflow

### Root Cause Summary

Arithmetic operations cause a number to either grow too large to be
represented in the number of bits allocated to it, or too small. This
could cause a positive number to become negative or a negative number to
become positive, resulting in unexpected/dangerous behavior.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide safe object wrappers for numerical data
types, just as it does for other generic data types such as phone
numbers and email addresses. All arithmetic operations performed on
primitive numeric types in the framework should perform
overflow/underflow checks first.

### Custom Framework Solution

None

### Custom Code Solution

Never perform arithmetic operations on numeric primitives without strict
checking for overflow/underflow conditions.

### Discussion / Controversy

Static analysis can be quite helpful in checking for possible
overflow/underflow conditions.

Some runtime environments automatically check for overflow/underflow and
trigger exceptions, but no mainstream language runtimes used for web
application development currently do this except for some flavors of
Python. This vulnerability category may be a candidate to be completely
solved in the platform or framework if enough pressure can be placed on
language runtime developers to implement a solution.

### References

[Integer Overflow](Integer_Overflow "wikilink")
[Integer Overflows
(WASC)](http://projects.webappsec.org/w/page/13246946/Integer%20Overflows)
[Integer Overflow or Wraparound
(CWE)](http://cwe.mitre.org/data/definitions/190.html)