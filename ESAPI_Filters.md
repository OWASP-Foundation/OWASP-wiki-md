## Feature Overview

ESAPI currently employs filters to accomplish a number of security
features, including authentication and CSRF protection. However, the
idea was broached that an ESAPI filter could be established to perform
other security functions.

## Possible Enhancements

  - ESAPI WAF

One of the core ideas was introducing a filter that optionally performs
virtual patching and other capability typically found in commercial and
open source web application firewalls. While the goal of ESAPI wouldn't
be to compete directly with any projects dedicated to WAF functionality,
it could still perform many important WAF types of functions without a
large amount of code introduced.

Customers who have automated penetrate-and-patch operations could
optimize their use of ESAPI with this functionality. Although the filter
itself would be relatively small, there will need to be a web
application to manage its rules that will require more work.

  - See the Session Management section for new, smarter, CSRF
    capabilities that may be introduced by a filter