## Feature Overview (in Version 2.0)

  - Be able to distinguish initial login and subsequent login after
    session timeout (working)

<!-- end list -->

  - To Change session ID after a successful login with optional session
    content replication so that a timed out user can continue where
    he/she has left off (working)

<!-- end list -->

  - Safe session management functions that will reject invalid session
    requests. For example, a request for session contents on an expired
    session should be rejected until the session is reactivated.

<!-- end list -->

  - Automatic CSRF token validation in a centralized location.

<!-- end list -->

  - A collection of anti-CSRF tags that can automatically incorporate
    CSRF token in forms when used in JSP pages

TODO

## Possible Enhancements

  - Add a secure form tag that does CSRF as well as other form
    protections like autocomplete

<!-- end list -->

  - Separate session management API and CSRF from the Authentication and
    HTTP utilities

<!-- end list -->

  - Add a flag to the changeSessionIdentifier method to not copy session
    content

<!-- end list -->

  - Consider whether ESAPI can provide CSRF protection without the User
    object - can we break the dependency