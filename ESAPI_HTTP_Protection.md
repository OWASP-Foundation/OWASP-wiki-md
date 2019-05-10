## Feature Overview

This request wrapper simply overrides unsafe methods in the
HttpServletRequest API with safe versions that return canonicalized data
where possible. The wrapper returns a safe value when a validation error
is detected, including stripped or empty strings.

The SafeRequest class implements HttpServletRequest and seamlessly adds
HTTP protection.

## Possible Enhancements

  - Jeff created this so perfectly that it does not necessitate
    additional enhancements.