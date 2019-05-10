[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Cross-Site Scripting (XSS)

### Root Cause Summary

Cross-Site Scripting (aka XSS or CSS) is an injection attack that is
possible when an application accepts untrusted data and includes it in
the context of an HTML page. Specially-formatted attacks take on
functional meaning, allowing data to be executed with the same
privileges as the containing web site.

### Browser / Standards Solution

Browser vendors and standards bodies should agree on markup for elements
to contain dynamic content (e.g. Flash, JavaScript, HTML, etc.) inline
without allowing the dynamic content to perform malicious actions such
as navigating the parent window, reading or writing data across trust
boundaries, or other undesirable behaviors as determined by the owner of
the containing page.

### Perimeter Solution

None

### Generic Framework Solution

Automatically sanitize any dynamic content before writing it into HTML,
XML, or other documents that might be rendered by user agents that
execute active content. If dynamic content must include dangerous
elements, provide APIs which filter and sanitize potentially dangerous
attributes of these elements. Exceptions and attribute configurations
should be described by a policy file instead of hard-coded into the
framework itself or into function calls. Legal attributes and elements
should be whitelisted (as opposed to blacklisted) in order to prevent
future browser features or HTML extensions from exposing new security
holes.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

The generic framework solution isn't fully generalizable to enable
certain classes of applications, especially content management systems
(CMSes) and inlined 3rd-party scripts. Thus, changes to standards and
new browser features are necessary to fully address all functional use
cases.

Until standards changes are implemented, performance tradeoffs between
encoding at the time of each page load and encoding data in the
model/database may require tighter coupling between application
frameworks and database solutions for applications which generate HTML
pages dynamically (as opposed to "Web 2.0" applications which serve a
static view and load dynamic content via XHR, rendering dynamic views
client-side).

### References

[OWASP Cross-site Scripting
(XSS)](https://www.owasp.org/index.php/Cross-site_Scripting_\(XSS\))
[OWASP – XSS (Cross Site Scripting) Prevention Cheat
Sheet](https://www.owasp.org/index.php/XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet)
[The Web Application Security Consortium – Cross Site
Scripting](http://projects.webappsec.org/w/page/13246920/Cross%20Site%20Scripting)
[Common Attack Pattern Emulation and Classification – CAPEC-341: WASC
Threat Classification 2.0 – WASC-8 – Cross-Site
Scripting](http://capec.mitre.org/data/definitions/341.html)
[cgisecurity - The Cross-Site Scripting (XSS)
FAQ](http://www.cgisecurity.com/xss-faq.html)
[CSP 1.0 Standard](http://www.w3.org/TR/CSP/)
[CSP 1.1 Draft](http://www.w3.org/TR/CSP11/)