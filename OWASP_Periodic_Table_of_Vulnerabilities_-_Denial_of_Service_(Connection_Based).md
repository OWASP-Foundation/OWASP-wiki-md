[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Denial of Service (Connection-Based)

### Root Cause Summary

Applications are generally not designed to recognize and handle
deliberately slowed connections or other abuses of HTTP below Layer 7.
Some types of attacks won't even reach the application code because they
prevent the web server from effectively processing requests.

### Browser / Standards Solution

None

### Perimeter Solution

Perimeter technologies should detect an event where many TCP or HTTP
connections are opened but no data are sent (or sent at very slow
speeds) over these connections. These connections should be dropped
during the event, only allowing normal-data-rate connections to persist
during the event.

Perimeter technologies should also detect an event where multiple
uniquely-identifiable clients open more than the two connections allowed
by HTTP standards and refuse these clients during the event. Clients can
be identified by a unique username/authorization token, or a combination
of unique attributes such as IP address and User-Agent.

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[OWASP HTTP Post Tool](OWASP_HTTP_Post_Tool "wikilink")
\[<http://ha.ckers.org/slowloris/>| slowloris\]