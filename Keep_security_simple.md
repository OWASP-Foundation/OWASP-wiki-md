

## Description

Attack surface area and simplicity go hand in hand. Certain software
engineering fads prefer overly complex approaches to what would
otherwise be relatively straightforward and simple code. Developers
should avoid the use of double negatives and complex architectures when
a simpler approach would be faster and simpler.

## Examples

### Entity Beans vs. Global Variables

  -
    Although it might be fashionable to have a slew of singleton entity
    beans running on a separate middleware server, it is more secure and
    faster to simply use global variables with an appropriate mutex
    mechanism to protect against race conditions.

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")

## Related [Controls](Controls "wikilink")

  - [Controls 1](Controls_1 "wikilink")

## References

  - See [How to write insecure
    code](How_to_write_insecure_code "wikilink") for a tongue-in-cheek
    discussion of keeping security simple.

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")