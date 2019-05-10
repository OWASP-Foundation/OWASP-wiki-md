[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Race Conditions

### Root Cause Summary

Two simultaneous transactions (HTTP requests, database storage/retrieval
commands, etc.) perform operations on the same data in a non-atomic
fashion, resulting in an inconsistent state.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Some application frameworks, such as J2EE, use a pattern where a single
class is loaded once, and used simultaneously by multiple
request-processing threads. This class is called a singleton. The
framework must prevent singletons from instantiating or accessing any
volatile class-scope objects.

The framework must obtain a lock on any shared resources and complete
any write/update/delete operations during an atomic transaction after
obtaining the lock. The framework must maintain a task queue for
transactions that are likely to take a long time to complete to avoid
blocking on other related IO.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

It may not be possible to implement a framework pattern for all possible
transaction types that an application might need. Some transactions may
need to be implemented as part of Custom Framework development.
Techniques such as data sharding may be highly dependent on the
individual application, and similarly force customization of the
framework to be implemented correctly.

### References

[Race Conditions](Race_Conditions "wikilink")
[Race Condition (CWE)](http://cwe.mitre.org/data/definitions/362.html)