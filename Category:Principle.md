This category is for tagging articles related to application security
principles.

## What is an application security principle?

Application security principles are collections of desirable application
properties, behaviors, designs and implementation practices that attempt
to reduce the likelihood of threat realization and impact should that
threat be realized. Security principles are language-independent,
architecturally-neutral primitives that can be leveraged within most
software development methodologies to design and construct applications.

Principles are important because they help us make security decisions in
new situations with the same basic ideas. By considering each of these
principles, we can derive security requirements, make architecture and
implementation decisions, and identify possible weaknesses in systems.

The important thing to remember is that in order to be useful,
principles must be evaluated, interpreted and applied to address a
specific problem. Although principles can serve as general guidelines,
simply telling a software developer that their software must "[fail
securely](fail_securely "wikilink")" or that they should do "[defense in
depth](defense_in_depth "wikilink")" won't mean that much.

## Some proven application security principles

  - Apply [defense in depth](defense_in_depth "wikilink") (complete
    mediation)
  - Use a [positive security model](positive_security_model "wikilink")
    (fail-safe defaults, minimize attack surface)
  - [Fail securely](Fail_securely "wikilink")
  - Run with [least privilege](least_privilege "wikilink")
  - [Avoid security by
    obscurity](Avoid_security_by_obscurity "wikilink") (open design)
  - [Keep security simple](Keep_security_simple "wikilink") (verifiable,
    economy of mechanism)
  - [Detect intrusions](Detect_intrusions "wikilink") (compromise
    recording)
  - [Don’t trust infrastructure](Don’t_trust_infrastructure "wikilink")
  - [Don’t trust services](Don’t_trust_services "wikilink")
  - [Establish secure defaults](Establish_secure_defaults "wikilink")
    (psychological acceptability)

## Applying security principles

Consider the exercise of designing a simple web application that allows
one to send email to a friend. By evaluating and interpreting each
principle, we can arrive at many of the threats to this application and
ultimately derive a set of protection requirements. We want to end up
with a complete list of what is required to offer this service securely.

## References

  - [Saltzer and
    Schroeder](http://web.mit.edu/Saltzer/www/publications/protection/Basic.html)
    (see section 3)
  - [The Six Dumbest Ideas in Computer
    Security](http://www.ranum.com/security/computer_security/editorials/dumb/index.html)
  - [Gary McGraw's 10 steps to secure
    software](http://www.zdnet.com/article/gary-mcgraw-10-steps-to-secure-software/)
  - [OWASP Development Guide Project](OWASP_Guide_Project "wikilink")
  - [Engineering Principles for Information Technology Security
    (EP-ITS), by Gary Stoneburner, Clark Hayden, and Alexis, NIST
    Special Publication (SP) 800-27
    (PDF)](http://csrc.nist.gov/publications/nistpubs/800-27A/SP800-27-RevA.pdf)
  - [Secure Design
    Principles](http://www.developer.com/java/data/article.php/10932_3667601_1)
    from "Foundations of Security: What Every Programmer Needs To Know"
    by Neil Daswani, Christoph Kern, and Anita Kesavan
    ([ISBN 1590597842](http://www.biblio.com/isbn/1590597842.html))
  - [High-Assurance Design](http://assuredbydesign.com/haa/) by Cliff
    Berg, 2005, Addison-Wesley. Foreword by Peter G. Neumann. Design
    principles and patterns for secure and reliable design.

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")