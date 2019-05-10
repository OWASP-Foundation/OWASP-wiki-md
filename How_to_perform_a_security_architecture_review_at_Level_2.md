If you are performing an application security verification according to
the [OWASP Application Security Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
verification requirements, then you will need to perform an analysis of
the application’s security architecture. The ASVS Level 2 security
architecture requirements read in part:

*“... the web application shall be defined by grouping its components
into a high-level architecture … Components may be defined in terms of
either individual or groups of source files, libraries, and/or
executables. At Level 2, the relationship between components or groups
of components need not be defined… At Level 2, the path or paths a given
end user request may take within the application must be documented…”*

The level of detail, and corresponding depth and breadth of analysis, is
the same for ASVS Levels 2, 2A, and 2B. The above requirements can be
met by performing three basic steps.

The first step is to identify web application and IT environment
components. Please see the ASVS article [How to perform a security
architecture review at Level
1](How_to_perform_a_security_architecture_review_at_Level_1 "wikilink").

The next step is to organize web application and IT environment
components identified into the previous step into a high-level
architecture. One way to accomplish this is to draw a block diagram that
can be understood without knowing, for example, Unified Modeling
Language (UML).

  - Draw blocks that correspond to web application components, possibly
    omitting IT environment components for clarity
  - Arrange blocks such that a line can be drawn through the blocks to
    depict an application request without lifting your pen from the
    paper
  - Arrange blocks such that a line can be drawn through the blocks to
    depict an application response without lifting your pen from the
    paper

The last step is to identify call stacks for application requests, using
the block diagram from the previous step as guidance.

Helpful hints:

  - If you’re working from code without the assistance of documentation
    or the application developers, the second and third steps may be
    reversed.
  - Keep in mind that security architecture analysis is an iterative,
    on-going process.
  - Learning how to identify and group components to obtain a desired
    level of abstractions is an art form in and of itself.
  - Corrections and additional detail are typically added as more
    information about the implementation is discovered over the course
    of the verification.

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")