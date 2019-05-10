

## Description

Once a security issue has been identified, it is important to develop a
test for it, and to understand the root cause of the issue. When design
patterns are used, it is likely that the security issue is widespread
amongst all code bases, so developing the right fix without introducing
regressions is essential.

## Examples

### Integration Testing

  -
    A user has found that they can see another user’s balance by
    adjusting their cookie. The fix seems to be relatively
    straightforward, but as the cookie handling code is shared amongst
    all applications, a change to just one application will trickle
    through to all other applications. The fix must therefore be tested
    on all affected applications.

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")

## Related [Controls](Controls "wikilink")

  - [Controls 1](Controls_1 "wikilink")

## References

  -
[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")