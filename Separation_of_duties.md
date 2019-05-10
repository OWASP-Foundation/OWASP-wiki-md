

## Description

The rule of thumb for separation of duties is that the entity that
approves an action, the entity that carries out an action, and the
entity that monitors that action must be separate. Separation of duties
is a prevalent control in both the accounting and IT communities. The
goal is to eliminate the possibility of a single user from carrying out
and concealing a prohibited action. By separating the authorization,
implementation and monitoring roles, fraud can only be successfully
carried out through the collusion of multiple parties. Support for
segregation of duties should be found in both application features
(e.g., role-based access), and should be built into the System
Development Lifecycle of the application (e.g., restricting developer
access to production libraries). Certain roles have different levels of
trust than normal users. In particular, Administrators are different
from normal users. In general, administrators should not be users of the
application.

## Examples

### Equipment Purchase

  -
    Someone who requests a computer cannot also sign for it, nor should
    they directly receive the computer. This prevents the user from
    requesting many computers, and claiming they never arrived.

### System User/Administrator

  -
    An administrator should be able to turn the system on or off, set
    password policy but shouldn’t be able to log on to the storefront as
    a super privileged user, such as being able to “buy” goods on behalf
    of other users.

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Log Forging](Log_Forging "wikilink")
  - [Least Privilege Violation](Least_Privilege_Violation "wikilink")

## Related [Controls](Controls "wikilink")

  - [Access control](Access_control "wikilink")
  - [Authorization](Authorization "wikilink")

## References

  - [ISACA Separation of Duties
    Matrix](http://www.isaca.org/Content/ContentGroups/Certification3/CISA1/Segregation-Of-Duties.pdf)

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")