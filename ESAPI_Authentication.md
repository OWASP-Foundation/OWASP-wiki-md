## Feature Overview

TODO

## Possible Enhancements

  - Wrap Principal don't extend (a "principal" is an authenticated user
    in Java. Typically, a 'claimant' would be an unauthenticated user.
    User could be either authenticated or unauthenticated, depending on
    the context.)

<!-- end list -->

  - Work to make compatible with container based authentication

<!-- end list -->

  - Should work with more generic Credential type rather than assuming
    username / password. That would allow certificates, smart cards, and
    other more advanced means of authentication.

<!-- end list -->

  - Provide a reauthentication API

<!-- end list -->

  - consider mechanisms provided by vm to associate authentication state
    with the invocation (e.g. Java AccessControlContext including
    Subject)