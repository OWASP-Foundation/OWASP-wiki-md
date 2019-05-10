[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Cross-Site Request Forgery (CSRF)

## Root Cause Summary

A vulnerable application processes a transaction using an existing
session, without verifying that the transaction was intended to be
initiated by the user and not a malicious 3rd-party site. CSRF is also
known as Session Riding or Confused Deputy.

## Browser / Standards Solution

Change default browser behavior to look for policy file for cross-domain
writes instead of "default allow", transitioning through CSP framework.

## Generic

None

## Framework Solution

None

## Perimeter Solution

None

## Generic Framework Solution

Automatically generate and check tokens for all POST requests by
default, following the Synchronizer Token Pattern with
configuration-based exclusion list for transactions which must not or
need not be protected against CSRF. Disallow state changes via GET
requests, enforcing RFC.

## Custom Framework Solution

None

## Custom Code Solution

None

## Discussion / Controversy

CSRF tokens would be made obsolete by a browser/standards solution that
allows a site owner to specify which external web sites are allowed to
initiate transactions. (The current HTTP specification by design allows
any web site to initiate POST requests to any other web site on the
behalf of its users.) Default deny for cross-domain writes will likely
never pass standards review. Even policy files to control cross-domain
writes are strongly disfavored.

## References

[OWASP - Top 10 2013-A8-Cross-Site Request Forgery
(CSRF)](https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_\(CSRF\))

[OWASP - Cross-Site Request Forgery
(CSRF)](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_\(CSRF\))

[OWASP - Cross-Site Request Forgery (CSRF) Prevention Cheat
Sheet](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet)

[OWASP - OWASP CSRF Tester
Project](https://www.owasp.org/index.php/CSRFTester)

[OWASP - Testing for CSRF
(OWASP-SM-005)](https://www.owasp.org/index.php/Testing_for_CSRF_\(OWASP-SM-005\))

[CWE-352: Cross-Site Request Forgery
(CSRF)](http://cwe.mitre.org/data/definitions/352.html)

[WASC - Cross Site Request
Forgery](http://projects.webappsec.org/w/page/13246919/Cross%20Site%20Request%20Forgery)

[CAPEC-62:Cross Site Request Forgery (aka Session
Riding)](http://capec.mitre.org/data/definitions/62.html)

[Cross-Origin Resource Sharing Draft](http://www.w3.org/TR/cors/)