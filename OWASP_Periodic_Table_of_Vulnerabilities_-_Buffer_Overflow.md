[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Buffer Overflow

### Root Cause Summary

The application allows an attacker to supply more data than will fit in
a pre-allocated block of memory and overwrite existing instructions or
data.

### Browser / Standards Solution

None

### Perimeter Solution

The perimeter should defend applications from known worm/exploit
signatures such as Code Red and alert or block suspicious payloads (e.g.
thousands of characters or shellcode signatures).

### Generic Framework Solution

The framework should be built on a memory-managed platform which
prohibits direct memory access.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Even if the overhead of a managed platform costs a few extra CPUs, the
cost is vanishingly small compared to the extra cost of code review and
testing required to ensure that the application is secure against buffer
overflow bugs.

### References

[Buffer Overflow](Buffer_Overflow "wikilink")