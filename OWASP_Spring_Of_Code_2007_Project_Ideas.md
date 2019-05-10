This page contains project ideas for submissions to the
[OWASP_Spring_Of_Code_2007](OWASP_Spring_Of_Code_2007 "wikilink").
Current OWASP project leaders should use this as a place to put their
'wish-list' for their projects.

We are looking for great projects that will help make the world a place
where insecure software is the exception, not the rule. We'll consider
any kind of project including tools, knowledgebase, process, marketing,
etc...

## OWASP Projects

See the current project list at [OWASP
Projects](:Category:OWASP_Project "wikilink") and contact the project's
leaders if you have specific ideas

## SpoC 007

  - Help with SpoC 007 initiative
      - project manage SpoC 007 projects
      - ensure all projects are going smoothly

## General Ideas

  - Develop a JavaScript library to fingerprint a good guy browser
    connection as opposed to a bot or other bad guy attacker.
  - OWASP Honeycomb Project: Normalize the CLASP and VulnCat data and
    help to release the Honeycomb user's guide
  - Help to Complete V2.0 of WebScarab and package it as product
  - Integrate WebGoat with with SiteGenerator
  - Complete the 'Owasp membership pack'
  - Create the next version of 'Owasp Live CD'

<!-- end list -->

  - Organize the 'OWASP branding project' and make a 1st pass at the
    current abuses of the OWASP brand
  - Create Training materials for OWASP projects (from tools to guides)

<!-- end list -->

  - **[AppSec Principles](:Category:Principle "wikilink")** - do some
    research and flesh out one of the OWASP principles. Talk about how
    the principle works in general, and then examine how it is applied
    in various contexts

<!-- end list -->

  - **[Attacks](:Category:Attack "wikilink")** - flesh out the list of
    attacks, develop each one with content and links

<!-- end list -->

  - **[Vulnerabilities](:Category:Vulnerability "wikilink")** - work to
    fill out writeups of vulnerabilities and clean up the vulnerability
    lists. There's lots of linking to other articles here needed. We're
    integrating CLASP, CWE, Fortify, and other sources of
    vulnerabilities to make the best resource anywhere.

<!-- end list -->

  - **[Countermeasures](:Category:Countermeasure "wikilink")** - general
    cleanup and linking of these articles. Probably some stubs in there
    that need significant writing

<!-- end list -->

  - **[Java Project](:Category:OWASP_Java_Project "wikilink")** - great
    opportunity to do research and bring together all the best
    information in one place for Java developers

## Medium or Large Projects

  - **[OWASP Corporate Application Security Rating
    Guide](OWASP_Corporate_Application_Security_Rating_Guide "wikilink")**
    - Help us examine the application security practices of the
    corporate world. How about assessing the top 50 companies and top 50
    software companies for their practices. The goal is to make it
    public what companies are doing in this area. The link is just an
    idea of how it might work\!

<!-- end list -->

  - **[AppSec Metrics](:Category:OWASP_Metrics_Project "wikilink")** -
    this project is harder, but desperately needed. Could involve paper
    exercises or actual tools. Currently people stop at SLOC count.
    Build a tool that generates something like this label
    (http://www.owasp.org/index.php/Types_of_application_security_metrics)
    and it could get a lot of attention.

<!-- end list -->

  - **Static Analysis to Pentest** - Write a tool that takes the output
    of static analysis and turns it into penetration test cases

<!-- end list -->

  - **Security Test Automation** - Make WebScarab generate, record, and
    playback security test cases (think JUnit) so that you can do
    regression security testing

<!-- end list -->

  - **Open Threat Modeling** - Build an open threat modeling tool like
    Microsoft's but not so cumbersome

<!-- end list -->

  - **Data Flow** - Adding true data flow analysis to LAPSE. Check out
    the jDFA project at sourceforge to see whether that can be applied
    to find tainted data attacks like XSS and SQL injection (as well as
    others)

<!-- end list -->

  - **Security Across the SDLC** - Integrated security activities across
    the lifecycle. Currently people are talking about “touchpoints” and
    “activities” but there’s no unifying line of sight or theme.

<!-- end list -->

  - **Honeycomb** - It seems simple, but when you start trying to
    organize ALL the information that’s out there it gets incredibly
    difficult. The simple taxonomies are wrong, bad, and misleading.
    Honeycomb is using a folksonomy approach that I hope will allow us
    to do something new here. But it really needs someone to think it
    through – perfect for a thesis.

<!-- end list -->

  - **Honeycomb+Tools** - Integrating the Honeycomb information into
    tools would be incredibly helpful. Things like the OWASP report
    generator need it. Threat modeling tools need it. Scanners need it.
    We need to prepare the information there for tool use.

<!-- end list -->

  - **LiveCD Education Project** - The LiveCD project is a phenomenal
    idea. What it needs to really take flight is information that
    educates the user on every aspect. This project will generate text
    tutorials, video tutorials, and other learning media that will help
    users learn how to use the LiveCD along with the tools which it
    encompasses.

## OWASP .Net Project

  - Organize the current OWASP .NET Project in a similar way to the Java
    Project

<!-- end list -->

  - Cross reference the .NET material in the other OWASP projects
    (Testing Guide, HoneyComb,etc...) and add more articles specific to
    .NET security

<!-- end list -->

  - Expand Dinis Cruz' research on .Net partial trust and create a Proof
    of Concept application showing how .Net's Partial Trust Sandbox can
    be used to mitigate against most Web Application Attacks (extra
    bonus points if a Java demo is also delivered :)

#### OWASP Site Generator

  - Add more vulnerabilties (and document them using ORG)

<!-- end list -->

  - Implement the new engine (http based using interfaces) which allows
    the use of any backend web technology

<!-- end list -->

  - Add ability to save / log all requests receive

<!-- end list -->

  - Write documentation and articles about it

#### OWASP Site Generator

  - Fix bugs in the OWASP version

<!-- end list -->

  - Add multiple Sample Reports (namely for the current OWASP tools)

<!-- end list -->

  - Write documentation and articles about it

#### .NET Tools to develop

  - Dynamically calculate required CAS permissions (don’t get me started
    on PermCalc)

<!-- end list -->

  - Refactor code that requires higher permissions into separate
    assemblies (so that only 1% of the code will need to run outside the
    Sandbox)

<!-- end list -->

  - Converters of unmanaged code to managed code (i.e. C++ to C\#, VB6
    to VB.Net, etc…)

<!-- end list -->

  - Source code audit tools that identify vulnerabilities or areas that
    might have vulnerabilities

<!-- end list -->

  - ".Net Time-machine (ala Flight Recorder)" - ability to record the
    entire state of all objects during a .Net Execution and allow the
    execution, debugging and fuzzing from any arbitrary point (see
    Java’s DeJaVu and JaRec Projects (I remember seeing another PoC of
    this type of tool, but can’t seem to be able to find the link))

<!-- end list -->

  - Smart fuzzers (to find run-time vulnerabilities)

<!-- end list -->

  - ‘Security rating calculators’ which will give a product (or dll) a
    rating based on the ‘threat profile of that application’ (for
    example the more unmanaged code, the worse rating) . This will be a
    very important part of the ‘Partial Trust Brand’

<!-- end list -->

  - Development environments that allow the development of complex and
    feature rich partial Trust applications like IE in managed code

<!-- end list -->

  - New execution environments (aka mini CLRs) that allow the execution
    of Managed/Verifiable code in : Services, Drivers, plug-ins etc…

<!-- end list -->

  - New Virtual PC Execution environments that allow the safe execution
    of ‘potential malicious applications’ whose interface with the
    user’s assets are controlled by a managed/verifiable application
    (and CAS policies)

<!-- end list -->

  - ‘What is going on’ tools. When I run an application I need to know
    EVERYTHING it does. And if the application somehow escapes the
    ‘execution monitoring system’ I want to know that it did. Now that
    Microsoft bought SysInternals, can we have a massive boast on those
    tools capabilities?. This tools must also build CAS polices based on
    what they detected the target application needs.

<!-- end list -->

  - Tools that allow the easy development and use of CAS and RBS (Role
    Base Security) and frameworks for securing an application’s
    Business-Logic (for example using a CAS to prevent the user
    account’s from being changed, or an bank account from being
    accessed)

<!-- end list -->

  - Code Coverage Tools - To know how much of an application has been
    tested, fuzzed or executed

<!-- end list -->

  - ‘Real time Hot Patching of Jitted methods (without using the .NET
    profiler)’ - For advanced defence solutions we will need the
    capability to make changes to jitted code (i.e . writing patches in
    C\#)

#### ASP.NET

  - WAF (Web Application Firewalls) with pluggable modules for: Data
    Validation, Authentication, Authorization, Anti-CSRF, DoS,
    Business-Logic vulnerabilities, etc…

<!-- end list -->

  - A framework similar to Struts (which force the developers to do the
    right thing (i.e. explicitly define all inputs into their
    application)

<!-- end list -->

  - IDS (Intrusion Detection Systems) with the capability to change the
    application’s behaviour when under attack

<!-- end list -->

  - Native Http Pipeline for IIS 5 and 6 (similar to what seems that
    will happen in IIS 7). This will be very important to protect ASP
    Classic pages

<!-- end list -->

  - CAS demands for dangerous methods (for example methods and classes
    that allow SQL Injections, XSS, etc…). The current CAS permission’s
    model is designed to protect the server and the other co-hosted
    applications. This needs to be extended so that CAS can be used to
    protect the actual application from vulnerabilities in its code

<!-- end list -->

  - CAS demands for methods or code that ’should’ exist (for example
    data valiation checks, authorization, etc….)

__NOTOC__