[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Clickjacking

### Root Cause Summary

User agents allow target sites to be framed and mouse clicks to be
intercepted/redirected to the target site. Users may believe they are
clicking on a visible UI element, but their click is actually redirected
to a different element on the target site.

### Browser / Standards Solution

CSP should define a white list of domains which are allowed to load the
site in a frame. Default should be SAMEORIGIN. Policy should allow
custom rules for specific URLs within the site, to allow a subset of
pages to have custom framing rules.

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide a configurable white list for domains
according to the requirements for the CSP standard. Until the CSP
standard is finalized, the framework should use the white list rules in
order to set the appropriate X-Frame-Options headers in each response.

The framework should detect the user-agent version; if the UA does not
support CSP or XFO, the framework should inject the appropriate
framebusting code automatically or redirect to a browser upgrade message
if the desired policy cannot be implemented without CSP/XFO.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Generic UI redressing problems may be too difficult to solve quickly,
but this would be a better long-term solution than framing policy rules
alone.

### References

[Clickjacking](Clickjacking "wikilink")
\[<https://developer.mozilla.org/en-US/docs/HTTP/X-Frame-Options>|
X-Frame-Options Specification\]
\[<http://seclab.stanford.edu/websec/framebusting/framebust.pdf>|
Framebusting research and recommendation\]
[IETF XFO Draft
Specification](http://tools.ietf.org/html/draft-ietf-websec-x-frame-options-08)
[W3 CSP UI Directives Draft
Specification](http://www.w3.org/TR/UISecurity/)