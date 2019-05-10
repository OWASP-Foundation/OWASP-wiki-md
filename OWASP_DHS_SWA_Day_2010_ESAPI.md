## The presentation

![Owasp_logo_normal.jpg](Owasp_logo_normal.jpg
"Owasp_logo_normal.jpg")A presentation about the OWASP Enterprise
Security API, or ESAPI

This presentation is given as part of [OWASP Software Assurance
Day](OWASP_Software_Assurance_Day_DC_2010 "wikilink") at the [| 13th
Annual Software Assurance
Forum](https://buildsecurityin.us-cert.gov/bsi/events/1133-BSI.html).

[Download the
presentation](Media:Jeff_Williams_2010-09_OWASP_DHS_SWA_Day_-_ESAPI.pptx "wikilink")

## The speaker

Jeff Williams is the founder and CEO of Aspect Security, specializing
exclusively in application security professional services. Jeff also
serves as the volunteer Chair of the Open Web Application Security
Project (OWASP). He has made extensive contributions to the application
security community through OWASP, including writing the Top Ten,
WebGoat, Secure Software Contract Annex, Enterprise Security API, OWASP
Risk Rating Methodology, and starting the worldwide local chapters
program. If nothing else, Jeff is probably the tallest application
security expert in the world and likes nothing better than discussing
new ideas for changing the way we build software.

## Notes

  - [OWASP Enterprise Security API (ESAPI)
    Project](:Category:OWASP_Enterprise_Security_API "wikilink")

ESAPI is a free and open collection of all the security methods that a
developer needs to build a secure web application. (Assessment Criteria
v1.0)

Several years ago, Williams was asked to review applications supported
by a development shop. He discovered that every developer was
reinventing code, and doing it incorrectly, sometimes multiple distinct
solutions for the same problems. We looked at the application
vulnerabilities. Scanning is valuable but it will not distinguish why
applications are broken. His findings were:

  - 35% of vulnerabilities had no controls.
  - 30 percent of application controls were broken and ineffective.
  - 20 percent were ignored. This is harder than just giving developers
    the controls. So we need to make the controls easier to use.
  - 15 percent of controls were not used correctly. Ease of use is
    necessary for this case as well.

**Security Controls are Hard**

There are 1.6 quadrillion or 785 ways to encode a character in canonical
form. We need to make it simpler for the developers to use the controls.
We want to pull the controls out of the code and put them in a
application security control library for the developers to use. We want
to manage security instead of insecurity. Controls instead of threats.
Patterns instead of vulnerabilities. If you manage vulnerabilities and
patches, the problems quickly become unmanageable. If you manage
assurance, you can get ahead of the vulnerabilities by stamping large
classes of vulnerabilities at a time. We identified 100 methods with a
common application programming interface (API).

  - [OWASP Enterprise Security API (ESAPI)
    Project](:Category:OWASP_Enterprise_Security_API "wikilink")

ESAPI (The OWASP Enterprise Security API) is a free, open source, web
application security control library that makes it easier for
programmers to write lower-risk applications. The ESAPI libraries are
designed to make it easier for programmers to retrofit security into
existing applications. The ESAPI libraries also serve as a solid
foundation for new development. You cant just download ESAPI and use it
out of the wrapper. Each organization needs to create its own security
library.

Allowing for language-specific differences, all OWASP ESAPI versions
have the same basic design:

  - There is a set of security control interfaces. They define for
    example types of parameters that are passed to types of security
    controls.
  - There is a reference implementation for each security control. The
    logic is not organization specific and the logic is not application
    specific. An example: string based input validation.
  - There are optionally your own implementations for each security
    control. There may be application logic contained in these classes
    which may be developed by or for your organization. An example:
    enterprise authentication.

There are ESAPI tools for Java, .NET, PHP, Cold Fusion, ASP, Python,
AJAX (Javascript on the client side), Ruby, C, and Salesforce.com. Also,
with ESAPI each application could have its own web application firewall.
The WAF can implement a virtual patch, check session states, user
authentication, and other application characteristics.

When an attack comes out, we can review our code and make patches so
that all developers using ESAPI will benefit. Taking an assurance case
perspective, we built almost a thousand test cases. We have tests for
canonicalization, output escaping. Also we can establish user
identification and access control. We have run Fortify, AppScan (Once
Labs), and PMD. The output from FindBugs is interesting. Do all my
Sturts action make sequential calls to authentication and logger?

Why invest in application security? There is a business and ROI. Also
appsec enables innovation, it allows organizations to do things they
can’t do today.

Q. What is the training requirement? A. It is difficult to teach
developers to teach all about application security. It is far easier to
teach an API in their own language. ESAPI simplifies the learning
process. You can cover ESPAI in a day for a decent Java developer.

See the [The Design and Evaluation of INFOSEC Systems: The Computer
Security
Contribution](http://www.csirt.org/color_%20books/C-TR-32-92.pdf) in the
rainbow series by Mario Tinto

In order for the firewall to determine if the request is malevolent. The
application understands the business rules whereas the firewall does
not. ESAPI makes the code a lot simpler and easier to figure out what
the policy being enforced.

\--[Walter Houser](User:Walter_Houser "wikilink") 22:19, 5 October 2010
(UTC)

[Category:OWASP_Conference_Presentations](Category:OWASP_Conference_Presentations "wikilink")