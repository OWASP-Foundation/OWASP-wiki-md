## Overview

This article’s focus is to define, where practical, nomenclature and
definitions of the differing security **Assessment Techniques**.
Agreement and establishment of these definitions are foundational to
establishing the **Assessment Levels** later within this project.

## Techniques

The following assessment techniques are proposed (in assessment depth
order):

  - Application Security Threat Assessment
  - Application Security Architecture Review
  - Automated External Application Scanning (Tool Based)
  - Automated Source Code Analysis (Tool-Based Static Code Analysis)
  - Manual Penetration Testing (Security Test Specialist)
  - Manual Security-Focused Code Review (Software Security Specialist)

NOTE: these should probably link to full articles on each subject

\[Semi Agree. Detail on each technique is needed to establish
definitions baseline for assessment levels component of project (the
guts). OK with moving to full articles if can maintain one master
article (need to build in this one) that demonstrates relationships
between techniques, commonalities, and relative building of assessment
depth from technique to technique\]

## Application Security Threat Assessment

Analyzes application architectural information to develop a threat
profile for the application components.

  - Identify the nature of the threats – the likely vulnerabilities of
    the given application and business.

<!-- end list -->

  - Estimate the probability that those vulnerabilities might lead to a
    disruption and the type of impact – both expected and worst case –
    that might arise.

<!-- end list -->

  - Analyze the different consequences and their likelihood of
    occurrence and determine which should be dealt with and what
    priority should be attached to mitigate.

While the threats to each asset within the Application can be
individually developed and mapped, a more efficient approach is to
develop a master list of threat types and identify how these can be used
to launch an attack on the Application and/or its components and
potentially in turn the business itself. A single threat may exploit a
vulnerability to damage different types of assets. Conversely, several
threat types may exploit disparate vulnerabilities in order to attack a
single critical asset. Given the many-to-many relationships between
threats and assets, it is best to use a simple representation of threat
to asset mapping by listing threat types by each critical asset
identified.

A threat assessment should categorize threat types and threat agents but
should focus on malicious threats and will not cover accidental and
natural threats. The source of Malicious Threats (the attacker or
perpetrator, in this context) can be classified as unauthorized and
authorized. Threat vectors and operating environment more fully define
how and why a particular “user” falls into one of these categories:

Unauthorized:

  - An attacker who does not have credentials to legitimately access the
    application

Authorized:

  - A legitimate user of the application
  - A malicious insider
  - A previously unauthorized user who has gained authorized access
    through compromise of a valid account or user session

While the threat agents may have similar intent, varying reasons for
engaging in illegal activities motivates them. Some authorized employees
may willfully commit fraud for financial gain or engage in sabotage in
order to disrupt routine operations. Theft, vandalism, intentional
corruptions and alteration of information are also categorized as
malicious threats.

*Advantages:*

  - Aids in focusing testing activities and defining true targets in
    large scale enterprise level applications.
  - By using results from a threat assessment, the end-client is able to
    focus assessment (testing) activities based on business requirements
    and operational reality.
  - Allows vulnerabilities discovered in other assessment types to be
    weighted and prioritized based on threat probability vs. raw
    vulnerability finding.

*Disadvantages:*

  - Cannot guarantee that all possible security threats will be
    uncovered.
  - End-client must evaluate analysis and determine responses(s).
  - Requires existence of application architecture documentation.
  - Often confused with Risk Assessments, which weigh asset value,
    threat, and vulnerability in order to determine business risk.
    Threat assessments focus on identifying only the threat component
    (vector(s) and probability).

Recommended use:

  - Best as a precursor to development activities allowing best use of
    security resources (i.e., “bake in” security during application
    development begets higher return on investment vs. “bolting on”
    application security fixes post production).
  - Best utilized to determine the need and extent for further
    assessment (testing) activities (e.g., automated testing, expert
    testing, code review, etc.).

## Application Security Architecture Review

Typically a table-top design level review and analysis of the
application to identify critical assets, sensitive data stores and
business critical interconnections. The purpose of architecture reviews
is to also aid in determining potential attack vectors, which could be
used in testing. Thus many organizations will blend this activity with
Threat Assessment. The review of the application and its
interconnections should include both a network- and application-level
evaluation. Evaluation should identify areas of potential and actual
vulnerability from these levels. This includes areas of vulnerability in
the network and application architecture, in addition to a high-level
measure of risk of each of those areas.

*Advantages:*

  - Aids in focusing testing activities and defining true targets in
    large scale enterprise level applications.
  - Provides more depth to the development rationale of various
    functionality in the application life cycle.
  - By using results from Architecture Review, the assessment (testing)
    team is able to follow development logic in the “how” and “why”
    business and security requirements were integrated into application
    behavior and security controls/constraints.

*Disadvantages:*

  - Cannot guarantee identification of all possible security threats.
  - Because the scope of an architectural assessment is far more complex
    than the limited perspective of an application layer assessment,
    recommendations are similarly complex, sometimes involving
    “political” changes (i.e., security department’s level of
    involvement in the SDLC).
  - Requires on-site discussions with application principals.

Recommended use:

  - Best as a precursor to development activities allowing best use of
    security dollars (i.e., incorporate security in beginning begets
    higher return on investment vs. fixing applications post
    production).
  - Best utilized to determine the need and extent for further
    assessment (testing) activities (e.g., automated testing, expert
    testing, code review, etc.).

## Automated External Application Scanning

Utilizing automated open source or commercial software to discover known
application layer vulnerabilities.

*Advantages:*

  - Able to quickly identify default content, misconfigurations and
    error conditions resulting from improper input.
  - Ability to be run on automated, regular basis to provide baseline
    and ongoing vulnerability management metrics.
  - Can reduce the time required to assess large applications.
  - Lower cost to operate/execute (excluding initial capital cost if
    using commercial testing software).

*Disadvantages:*

  - Not designed to determine the extent to which the vulnerabilities
    can be exploited to compromise the data the application handles.
  - Requires appropriate skills/knowledge to use, configure, and
    interpret results (despite “point and click” vendor marketing
    claims).
  - Requires extensive configuration and customization to emulate a user
    session.
  - Limited ability to correlate events and correlate minor issues that
    may lead to larger exposure.
  - Inability to adapt to dynamic responses in business logic flows.
  - Unable to find vulnerabilities that only become apparent after
    performing a sequence of steps (e.g., business logic flow bypass,
    session state compromise, etc.).
  - Unable to figure out “how deep the rabbit hole goes” – No means to
    interpret security implications, express extent of potential
    compromise, or identify seriousness of business and information
    exposure.
  - Tools will often be confused by some aspect of an application's
    behavior, causing a particular class of test to generate a false
    positive. Because most tools lack intelligence and cannot adapt to
    such conditions, test results include a large number of identical
    false positives.
      - For valid findings, the tools will often find dozens or hundreds
        of nearly identical findings, each with the same root cause.
  - Tool based findings are only indications of problems. Manual review
    (by someone well versed in web application testing) is usually
    necessary to draw the necessary parallels between different
    findings, and determine which findings identify unique problems, and
    which represent repetition.

Recommended use:

  - Handling routine, manually intensive steps (e.g., input validation,
    field “fuzzing”, etc.) in an assessment is useful, particularly in
    large applications. However, scanner-based results can be used as
    the starting point from which expert testing can take over.
  - Testing less critical applications (i.e., applications that do not
    contain/handle business sensitive data and/or are not critical to
    business operation) where the perceived lower risk does not warrant
    performing hands-on testing.
  - Testing critical applications as a prelude to expert testing or code
    reviews.

If a tool is used, it is important to define the technical limitations
of the tool when the findings are presented. An example of this may
involve noting the potential for SQL injection attacks based upon
verbose SQL error messages, but also the tool’s inability to produce the
correct syntax needed to extract specific information from the
vulnerable database. A failure to convey the differences between
automated and expert testing increases the risk that the application
assessment results will be interpreted (particularly by management) as
being more “secure” than they actually are.

## Automated Source Code Analysis

Automated source code analysis involves the use of special software
"tools" to conduct [Static Code
Analysis](http://en.wikipedia.org/wiki/Static_code_analysis) on software
source code to identify potential vulnerabilities within the code.

*Advantages:*

  - can be very effective method for identifying defects in code
    functionality and syntax errors
  - most automated source code analysis tools are highly scalable
  - expedites code review process (can review 400-500 LOC/hr via manual
    review vs. up to 10,000 LOC/hr using automated source code scanning
    tools)
  - helps teams focus their manual code review activities on flagged,
    high-risk areas

*Disadvantages:*

  - most automated source code analysis tools generate false positives
  - some automated source code analysis tools have a significant
    learning curve
  - some coding languages (such as ASP) are not supported by the tools
  - results of automated scans are basically "blueprints" of source code
    vulnerabilities, so they must be properly protected
  - Most of the automated source code analysis tools available on the
    market today can not identify logic errors, timing errors, resource
    conflicts, data errors and configuration errors.

Recommended use:

  - Automated source code analysis tools can be used to enhance and
    improve an organization’s overall efforts to find and eliminate
    security vulnerabilities within software applications. However, they
    should not be viewed as a "silver bullet". Manual code reviews must
    still be conducted to identify false positives and security-related
    defects that tools can not identify.

## Manual Penetration Testing

Manual Penetration Testing involves application analysis performed by an
experienced analyst, usually using a combination of open source
automated utilities (either self created or through security community)
for performing task-specific functions and hands-on analysis to attempt
to further ‘hack’ the application as an attacker.

*Advantages:*

  - Open source tools utilized by the expert tester are developed
    usually for specific purposes rather than wrapping multiple
    functionality into a GUI. Typically are one of many components in
    the testers toolkit.
  - “Expert testing” is an intuitive approach (Business logic analysis),
    with the ability to identify flaws in business logic that automated
    scanners are usually incapable of finding.
  - Addresses many of the disadvantages noted in Automated Testing.
  - Ability to correlate events and minor issues that may lead to larger
    exposure. This is a critical advantage of hands-on testing and
    simulates how a real attacker would operate.
  - Ability to communicate complex technical findings in a manner that
    all can understand. The job is not done until the assessment
    end-client understands the nature of the vulnerability discovered
    and its security implications.
      - The analysis phase of expert testing provides “root cause”
        identification and recommendations based upon the unique,
        developmental characteristics of an application. Results from an
        automated tool cannot provide customized, specific
        recommendations tailored for each application and the
        end-client’s requirements.

*Disadvantages:*

  - Often confused with Automated Testing – Marketing of commercial
    tools uses terms such as “expert” and “intuitive”, normally
    associated with an assessment performed by an experienced analyst.
  - Inability of most end-client organizations to determine if tester
    has appropriate application security skills required. There are no
    community accepted credentials/certifications established for this
    area of security.
  - Cost to conduct will be higher though there is no upfront capital
    cost.
  - Without establishing clear metrics up front, ongoing testing to
    determine trends within business environment or iterations of
    application is difficult.

Recommended use:

  - Testing critical applications (i.e., applications that do
    contain/handle business sensitive data and/or are critical to
    business operation) where the perceived higher risk does not warrant
    performing automated testing.
  - Best suited for B2B, B2C and/or any transactional based and/or
    multi-level access application.

## Manual Security-Focused Code Review

Review of the software source code to identify source code-level issues,
which may enable an attacker to compromise an application, system, or
business functionality. Web applications in particular are likely to
have these vulnerabilities, as they are frequently developed quickly in
an environment that does not allow for much security planning and
testing. This should not be viewed as simply a generic software audit.
Security-focused code reviews should be specifically tailored to find
common vulnerabilities in applications.

*Advantages:*

  - If integrated into the [Software Development Life Cycle
    (SDLC)](http://en.wikipedia.org/wiki/Software_development_life_cycle),
    coding issues can be resolved earlier in the development process.
    (which is much less expensive to fix than a post-production revision
    of the code).
  - Provides the ability to identify and address serious coding issues
    (e.g., input validation, hard-coded credentials, debugging features,
    etc.) prior to production.
  - Enables development teams to identify and correct insecure coding
    techniques that could lead to security vulnerabilities or possible
    incidents.
  - Helps developers learn from each other and share knowledge on secure
    coding techniques, best practices and common solutions.

*Disadvantages:*

  - can be very time consuming and costly if automated tools are not
    available to help augment the review process
  - If conducted solely by tools, results will be mostly static
    signature matching though some tools claim to walk codepath (follow
    nested loops and other regression through objects).
  - Even applications that exhibit strong and thorough software
    development practices (e.g., documentation, seamless modularity,
    string checking to prevent buffer overflows, etc.) can fall victim
    to attack if the underlying business logic doesn’t follow security
    requirements.
  - Requires specific programming expertise (e.g., Java, .NET, PHP,
    etc.) that many application testers do not have.

Recommended use:

  - Security-focused code reviews should be conducted as part of the
    normal SDLC. Reviews may also be needed during or after security
    testing, prior to implementing system upgrades, prior to making
    system configuration changes, when new security bulletins are
    released, or immediately following any reported security incidents.

## References/Sources

  - Testing Taxonomy & Testing Tools Classification :
    <http://www.owasp.org/index.php/Image:AppSec2005DC-Arian_Evans_Tools-Taxonomy.ppt>

[Category:OWASP Application Security Assessment Standards
Project](Category:OWASP_Application_Security_Assessment_Standards_Project "wikilink")