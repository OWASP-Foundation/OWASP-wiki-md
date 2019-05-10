Last revision (mm/dd/yy): **//**



## Description

Every feature that is added to an application adds a certain amount of
risk to the overall application. The aim for secure development is to
reduce the overall risk by reducing the attack surface area.

For example, a web application implements online help with a search
function. The search function may be vulnerable to SQL injection
attacks. If the help feature was limited to authorized users, the attack
likelihood is reduced. If the help feature’s search function was gated
through centralized data validation routines, the ability to perform SQL
injection is dramatically reduced. However, if the help feature was
re-written to eliminate the search function (through better user
interface, for example), this almost eliminates the attack surface area,
even if the help feature was available to the Internet at large.

## Examples

### Short example name

  -
    A short example description, small picture, or sample code with
    [links](http://www.site.com)

### Short example name

  -
    A short example description, small picture, or sample code with
    [links](http://www.site.com)

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")
  - [Vulnerabiltiy 2](Vulnerabiltiy_2 "wikilink")

## Related [Controls](Controls "wikilink")

  - [Controls 1](Controls_1 "wikilink")
  - [Controls 2](Controls_2 "wikilink")

## References

  - <http://www.link1.com>
  - [Title for the link2](http://www.link2.com)

__NOTOC__

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")