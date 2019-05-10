## Feature Overview

The ESAPI Logger should promote secure logging functionality while
allowing organizations to choose their own logging framework. The
primary benefit of the ESAPI Logger is the addition of relevant security
information to the log message and the use of specific tags that allow
log messages to be identified as SECURITY related (as opposed to
FUNCTIONAL, PERFORMANCE, etc).

## Possible Enhancements

  - Remove LogFactory interface. The ESAPI is a factory itself that can
    be used to select a logging implementation.

<!-- end list -->

  - Change default log behavior to use classes rather than module names.

<!-- end list -->

  - Remove success/failure parameter and replace that with
    SECURITY_SUCCESS, SECURITY_FAILURE, etc. event types.

<!-- end list -->

  - Create a 'filter' or some other drop in replacement that can be used
    in existing logging frameworks to make them safer (like against log
    injection) without changing the interface that they are using today.