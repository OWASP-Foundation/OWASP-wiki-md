[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Brute Force (Generic) / Insufficient Anti-automation

### Root Cause Summary

Applications do not define or detect when request rates are outside the
bounds of normal, acceptable use.

### Browser / Standards Solution

None

### Perimeter Solution

Perimeter technologies including geocaching/proxy services must support
automatic and/or manual "panic button" anti-automation, enforcing
progressive CAPTCHA for unvalidated requests, triggering on excessive
5XX responses, or direct signal from application.

### Generic Framework Solution

Provide configurable per-user/session request rate limits. For
authenticated transactions, limits should be configurable on a per-user
or per-session basis. Configuration should allow combining multiple
limits of the form "\# of requests per time period". For example, an
administrator should be allowed to combine "10 requests per minute" with
"500 requests per day" in order to simultaneously apply policies which
prevent users from automatic crawling/screen scraping as well as
longer-term slow leeching activities.

### Custom Framework Solution

Provide a common configuration functionality available to any
feature/function. Configuration settings should allow multiple per-user
rate limits as well as global rate limits to prevent denial of service.

### Custom Code Solution

Any feature sensitive to high transaction rates should expose
configurable rate limits per user or globally per feature.

### Discussion / Controversy

Generic framework solution requires too much overhead to track request
limits. Request rate limiting should be done in perimeter, not
framework. Should combine with Denial of Service (Application-Based)?
Custom Code solution is the same as Custom Framework Solution; Custom
Code solution should be pushed into framework.

### References

[Insufficient Anti-automation (WASC
TC)](http://projects.webappsec.org/w/page/13246938/Insufficient%20Anti-automation)
[Brute Force (WASC
TC)](http://projects.webappsec.org/w/page/13246915/Brute%20Force)
[Testing for Brute Force (OWASP Testing
Guide)](Testing_for_Brute_Force_\(OWASP-AT-004\) "wikilink")