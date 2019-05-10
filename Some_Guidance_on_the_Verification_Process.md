Verifying an application against the ASVS detailed verification
requirements can be a complex task. Here is some guidance for certain
situations.

  - **Automated Verifications** - Automated tools are *generally*
    signature based, where those signatures look for patterns of bad
    behavior which indicate there is a likely flaw in the application.
    Such tools do not usually perform a positive analysis on the
    application to verify that it is correct throughout the application
    with regard to the particular vulnerability being looked for. For
    example, tools may be good at finding certain types of cross site
    scripting (XSS) vulnerabilities, but may not be good at finding all
    types, or may have difficulty when certain technologies are used,
    like AJAX. We don’t expect automated tools to be able detect all
    flaws in any of these areas. For Level 1, if an application passes
    the signatures, then it passes. The verifier simply needs to explain
    what the signatures actually do in the report so the reader can
    understand the benefit of the tool(s) used for each particular
    verification requirement.

<!-- end list -->

  - **Assessment of Off-The-Shelf Components as part of Automated or
    Manual Code Review (LEVELS 1B & 2B)** - If you are performing a code
    review and you do not have access to the code for the security
    control being used, then you need to review the control’s
    documentation and (for Level 2B) any security configuration in order
    to verify that the security control meets the specified requirement.
    Similarly, if you do have access to the code, but the security
    control is data driven, you also have to review the configuration
    data (for Level 2B) to make sure the control is configured properly
    for this application, not just that the security mechanism works
    generically. The results of your documentation analysis and any
    configuration data review should be documented in the verification
    report.

<!-- end list -->

  - **Assessment of generic applications** - If you are performing a
    review of a generic instance of an application rather than an
    application in a specific target environment, then the verification
    effort needs to make sure that the provided security controls work
    as advertised. This means determining what the provided security
    controls are supposed to be capable of, and then verifying that they
    work correctly in a variety of common configurations. If the generic
    application does not provide or only partially provides security
    controls in certain areas, and expects the deployment environment to
    provide them, then the verification report should state for each
    affected verification requirement what the application does or does
    not provide. The report should also state whether the current state
    of practice makes it reasonable to expect a deployment environment
    to provide the expected capabilities. It is expected that only a few
    ASVS requirements could be completely met by externally provided
    controls.

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")