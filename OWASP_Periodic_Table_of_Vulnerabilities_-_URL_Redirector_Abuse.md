[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## URL Redirector Abuse

### Root Cause Summary

Applications accept arbitrary user-defined URLs as input, which are then
used as targets for redirection. Users may be unwittingly rerouted to a
malicious site from a site they trust.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should expose a configurable white list of hosts and/or
paths that are acceptable targets for URL redirection. This might
include additional rules about stripping
[fragments](https://en.wikipedia.org/wiki/Fragment_identifier%7CURL) and
URL parameters from the redirection target. The default rule set should
allow only relative URLs, in order to prevent redirection away from the
original site.

The framework should prevent application code from directly modifying
Location, Refresh, or any other response headers that might be used by
the browser to load URL resources. The framework should prevent the use
of document.location and window.location in JavaScript. Instead, the
framework should expose an API for URL redirection which can accept an
arbitrary URL, but applies the white list rules and transformations
before allowing the redirect.

Session expiration code and code which handles unauthenticated deep
linking should automatically apply the white list when attempting to
redirect back to a requested URL after successful authentication.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

None

### References

[OWASP Top 10 2010 - A10 Unvalidated Redirects and
Forwards](Top_10_2010-A10-Unvalidated_Redirects_and_Forwards "wikilink")
[Redirector Abuse
(WASC)](http://projects.webappsec.org/w/page/13246981/URL%20Redirector%20Abuse%7CURL)
\[[http://cwe.mitre.org/data/definitions/601.html|CWE-601](http://cwe.mitre.org/data/definitions/601.html%7CCWE-601):
URL Redirection to Untrusted Site\]