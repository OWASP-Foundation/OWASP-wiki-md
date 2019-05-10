OWASP is currently requesting proposals for all the following OWASP
projects.

Proposals for these projects are typically submitted via OWASP Season of
Code grants. Your proposal is the key factor in deciding whether to
award funds - unprofessional applications will not be accepted. The
typical project delivery time is 5 months and the payment will be made
in two 50% parts (one at the 50% mark and one at 100% mark as judged by
an independent reviewer).

You can, of course, submit an unsolicited proposal for any idea that
will help OWASP achieve its mission. The requested projects should help
you understand the range and depth of projects that are likely to be
funded by the OWASP Foundation.

## Global Project Requirements

  - The project must achieve [Beta
    Quality](:Category:OWASP_Project_Assessment "wikilink") per OWASP's
    guidelines.
  - Projects must not advocate the use of any particular product,
    although classes of tools may be referenced.

## Project Requests

#### P001 - OWASP Open Threat Modeling Process

  - **Project description**: Document a methodology for threat modeling
    that is simple, consistent, and reproduceable. The documentation
    should make it possible for a developer to create a threat model and
    begin to identify risks. The threat model should produced should
    include the security relevant details of the application
    architecture, the threat agents, attack vectors, vulnerabilities,
    security controls, technical impacts and business impacts. All the
    common security areas should be represented across identity and
    authentication, session management, access control, input
    validation, encoding and canonicalization, error handling, logging
    and intrusion detection, availability, integrity, concurrency,
    etc...
      - While some level of expertise in application security is
        required to identify risks, the approach should allow anyone to
        gather all the relevant information, organize it, and prepare
        for an expert's participation.
      - The result should include several 'standard' threat models for
        common scenarios that users can start with, such as internet
        facing multi-user web application, internal client-server
        application, etc.
      - The approach should make it possible for risks to be identified
        by starting with threat agents (Microsoft approach), or by
        starting from business impacts and working backwards
        (threat/attack trees). The approach should also allow for a
        security controls oriented approach (like NIST 800-53).
      - The project could (as an option) include an open threat modeling
        tool like Microsoft's but not so cumbersome. A visual threat
        modeling approach is greatly preferred to spreadsheet or
        quantitative approaches.
      - The project should build on the information in the [OWASP
        Application Security Desk
        Reference](:Category:OWASP_ASDR_Project "wikilink").

#### P006 - OWASP Corporate Application Security Rating Guide

  - **Project description**: Help us benchmark the application security
    practices of the corporate world. Assess the top 50 companies and
    top 50 software companies for their practices. The goal is to make
    public what companies are doing in this area. [OWASP Corporate
    Application Security Rating
    Guide](OWASP_Corporate_Application_Security_Rating_Guide "wikilink")
    has some sample materials for this project.
      - The project will assess all public materials (interviews,
        presentations, briefings) for details
      - The project will link to all source material used in creating
        the rating

#### P007 - OWASP Security Facts Label

  - **Project description**: Design a [security facts
    label](Types_of_application_security_metrics "wikilink") methodology
    and supporting tool. Define a set of concrete measurable factors to
    include in the label
      - Factors should cover the application itself as well as the
        people, teams, processes, tools, libraries, and supporting
        technologies that created it.
      - Build a survey application to gather data and store in an XML
        file. Also create a label generation program that reads the XML
        and creates a compelling label.

#### P008 - OWASP Security Test Automation

  - **Project description**: Create a tool that generates, records, and
    plays back security test cases (think JUnit) to enable regression
    testing for security. This could be based on WebScarab, Selenium,
    HTTPUnit or something else. But it would create test cases that are
    custom for a particular application, not a generic scanner.
      - The tool should have wizards for common security related use
        cases, such as login, change password, authorized access,
        unauthorized access, etc... The tool should combine these
        security use cases with a set of predefined security tests to
        generate a custom set of security tests for an application. A
        simple example is that the tool would record the login
        transaction, and generate a security test to verify that the
        session cookie is changed (to defeat session fixation).
      - The tool needs to be able to detect the success or failure of
        each test, not just repeat the actions required to perform the
        security relevant function.
      - The tool could also use the output from static analysis to
        create test cases. A smaller scale project would be a research
        paper that shows exactly how one can use the details from static
        analysis to generate scanner/pentest cases.

#### P009 - OWASP Security Unit Test Framework

  - **Project description**: Create a wizard that will generate
    security-specific JUnit test cases for all the security controls in
    your security library. The tool should ask questions about security
    methods and generate appropriate test cases.
      - At a minimum, the tool should be able to generate test cases
        that validate that the validation methods canonicalize and
        encode properly, that the encoder does not use a blacklist, that
        the logging methods handle injection, that the hash algorithm is
        salted, that logout invalidates the user's session.
      - The tool's coverage should roughly line up with the security
        methods defined in the [OWASP ESAPI](esapi "wikilink") project.

#### P010 - OWASP Client-Side Browser Fingerprint Project

  - **Project description**: Develop and document a technology that will
    create a "fingerprint" for a user's host/browser that can be used to
    detect when an attacker attempts to hijack their account. The server
    application can track changes to the client-generated fingerprint
    and request additional authentication if the fingerprint changes too
    radically. Such a technique can serve as an additional
    authentication factor in order to help prevent accounts from being
    hijacked due to authentication credential or session token theft.
      - The tool should be configurable to tolerate expected changes in
        host/browser configuration, such as a browser update. The tool
        should flag when the host/browser changes in an unexpected way.

#### P011 - OWASP CLASP Refresh

  - **Project description**: Reorganize and update the materials in the
    [OWASP CLASP project](:Category:OWASP_CLASP_Project "wikilink") to
    be more complete and comprehensive. Each of the activities must
    include detailed methodologies, so that they can be practiced
    repeatably by anyone with the appropriate background.
      - The activities should include all the related job aides and
        materials to perform the activity, such as worksheets, report
        formats, databases, etc...
      - No proprietary methodologies can be used as a part of
        [CLASP](:Category:OWASP_CLASP_Project "wikilink").

#### P014 - OWASP Security Refactoring Tool Project

  - **Project description**: Create a tool that refactors existing code
    to use safer versions of dangerous methods. The tool should rewrite
    the code to use safer calls and mark the changes in a way that they
    can easily be found and verified manually. A data-driven approach is
    preferred (similar to the Jackpot engine in NetBeans, but not
    required.
      - For Java EE/JSP the code can be rewritten to use the safer
        alternatives available for many calls and patterns in the [OWASP
        ESAPI](esapi "wikilink") project.
      - For .NET, converters from unmanaged code to managed code (i.e.
        C++ to C\#, VB6 to VB.Net, etc…).

#### P015 - OWASP BlackTop - Runtime Coverage Analysis Tool

  - **Project description**: Develop and document a "blackbox" pen
    testing code analysis solution capable of providing runtime coverage
    analysis for applications written in Java and .NET. In order to
    ensure the solution does not require access to the applications'
    source code, the solution should use (for example) the AspectJ and
    PostSharp bytecode weaving frameworks.
      - The tool should provide code level details and call trace
        information of all ingress and egress points of the application
        and be able to identify gaps in the "blackbox" testing to
        facilitate more accurate and complete pen testing. All output
        and configuration should be done using an open format (such as
        XML) and enable command line execution of the application.
      - Either the Eclipse Public License or the Mozilla Public license
        is allowable.
      - Funds available: 10,000 USD
      - Sponsor: Ounce Labs

#### P016 - OWASP .NET Access Control Tool

  - **Project description**: Create a tool that enables the easy
    development and use of CAS (Code Access Security) and RBS (Role Base
    Security) and frameworks for securing an application’s
    Business-Logic (for example using a CAS to prevent the user
    account’s from being changed, or an bank account from being
    accessed)

#### P019 - OWASP ColdFusion Security Project

  - **Project description**: Create a guide and supporting tools to
    support people charged with securing ColdFusion web applications.
    The coverage should include all of the OWASP Top Ten and other
    important topics from OWASP, such as those included in the [OWASP
    ESAPI](ESAPI "wikilink") project.

#### P020 - OWASP JUnit Static Analysis Integration Project

  - **Project description**: Create an extension to JUnit that invokes a
    "static analyzer" as a test case. The specific static analysis
    technique doesn't matter, could be based on grep, BCEL, the Eclipse
    Model, FindBugs, or PMD. This will enable developers to detect
    software problems during development.
      - You fail the test case if you use certain banned APIs. Or even
        better, if you have better static analysis, you fail the test
        case if you fail to do something more complex - like not logging
        in the method that calls isUserInRole().

#### P021 - OWASP Server Side Security Scanner

  - **Project description**: Build a server-side scanner in a Java
    Filter. The idea is that you can scan (or fuzz) way more effectively
    from inside the web container. The filter can generate multiple HTTP
    requests. This approach to scanning can be more effective than
    external scanners, since it can parse web.xml, analyze the
    filesystem, do bytecode analysis, and more to generate an attack
    plan. It can also start scanning many times faster than a normal
    scanner.
      - This approach to scanning can be more effective because it has
        access to the the session object, log files, filesystem,
        database and other system resources. This allows the scanner to
        test whether the attack actually worked or not, which is
        impossible for external scanners.

#### P023 - OWASP Code Review Tree

  - **Project description**: Build a simple Eclipse plugin to build a
    "Reverse API" tree navigation system. The tree should be organized
    by Packages -\> Classes -\> Methods -\> callsites. This will allow
    code reviewers to see exactly what calls are used in the
    application. For example, the user could quickly check to see if the
    application calls Runtime.exec(). This also makes it easy to find
    out what type of backend systems the application uses.
      - Include a separate tree to search for non-method call security
        progress. This could include:
          - List Entry Points (from web.xml and webcontent folders)
          - Better search window that allows you to see the matching
            line of code
          - An analysis work tree based on search (similar to the call
            tree/hierarchy)
          - Simple findings & dangerous calls
          - Concurrency issues (class member variable in Servlet,
            threadlocals)

`    Category            Name               Description                Regex`
`    ---------------     ---------------    --------------             -----------`
`    Code Quality        Fixme              Unfinished code            (fixme`

|hack |bug)

`    Authentication      Password           All access to credentials  (password`

|username |credentials |key |certificate)

`    Access Control      JavaEE             Possible authorization     (isAdmin)`
`    Obscenity           !$??%@*#$          Frustrated developers      (censored)`

#### P024 - OWASP Attack Surface Metric

  - **Project description**: Define a useful method for describing the
    attack surface of a typical web application and produce tools or an
    easy methodology for calculating it on a real application.
      - The attack surface metric should take into account the public
        URL space. And for each part of the URL space, the number of
        parameters/headers/cookies used. And for each
        parameter/header/cookie, how well is it validated and what is it
        used for. Does the input go to an interpreter, used in business
        logic, as a reference to private information.
      - For example, adding a parameter that is used to make a boolean
        decision should affect the metric only a tiny bit. But an
        unvalidated parameter used in a call to the operating system
        should dramatically increase the attack surface.
      - The methodology must be easily repeatable in a mechanical way. A
        tool to calculate the metric is highly preferred.

#### P026 - OWASP Java Sandbox Policy Tool

  - **Project description**: Create a tool that facilitates the creation
    of accurate, useful Java security policy files.
      - The tool should support a "learn" mode like a host based
        firewall that asks about any accesses it doesn't know about. You
        can do this by implementing an intercepting SecurityManager
        (instead of one that throws SecurityExceptions). The interface
        should allow the user to "generalize" the specific policy
        request to make a more general rule. For example if the request
        is for "/temp/file123.xls" you might want to generalize the
        policy to allow all access to the "/temp" directory.
      - The tool should produce machine readable security.policy files
        that can be deployed with the application.