[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Information Leakage

### Root Cause Summary

The application discloses sensitive/classified data or useful data about
the application that can be used for targeted attacks, even though the
developer did not intend for the data to be disclosed.

### Browser / Standards Solution

None

### Perimeter Solution

  - Alert, block, or automatically sanitize classified data in
    responses.

<!-- end list -->

  - Automatically scrub HTML, JavaScript, CSS, and other data formats of
    comment data.

<!-- end list -->

  - Configure the platform to return generic error codes by default and
    log locally.

<!-- end list -->

  - Disable stack traces in production; show a generic error page
    instead.

### Generic Framework Solution

  - Provide common error-handling framework and APIs which take two
    error messages as parameters: one to be displayed to the user and
    one to be written to logs.

<!-- end list -->

  - Provide configurable content expiration/caching interface; default
    to no-cache, no-store.

<!-- end list -->

  - Provide common methods to mask data in responses based on
    configurable rules for varying levels of data classification.

<!-- end list -->

  - Block classified information from being sent as URL parameters or
    logged as part of a GET request.

<!-- end list -->

  - Block file paths from being displayed by default.

### Custom Framework Solution

None

### Custom Code Solution

  - Don't leak information via error parity mismatches. For example, a
    login form should return the same error message regardless of
    whether the username or password is incorrect, in order to prevent
    account enumeration.

<!-- end list -->

  - Only send back data in the response to the client that is needed.

### Discussion / Controversy

None

### References

[Information Leakage
(WASC)](http://projects.webappsec.org/w/page/13246936/Information%20Leakage)
[Information Exposure
(CWE)](http://cwe.mitre.org/data/definitions/200.html)