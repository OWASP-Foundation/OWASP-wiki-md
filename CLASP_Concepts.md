## Concepts View

[CLASP](Glossary#CLASP "wikilink") is the outgrowth of years of
extensive field work in which system resources of many development
lifecycles were methodically decomposed in order to create a
comprehensive set of security requirements. These resulting requirements
form the basis of CLASP’s best practices which allow organizations to
systematically address vulnerabilities that, if exploited, can result in
the failure of basic security services — e.g., confidentiality,
authentication, and access control.

### Adaptability of CLASP to Existing Development Processes

[CLASP](Glossary#CLASP "wikilink") is designed to allow you to easily
integrate its security-related activities into your existing application
development processes. Each [CLASP](Glossary#CLASP "wikilink") activity
is divided into discrete process components and linked to one or more
specific project roles. In this way, [CLASP](Glossary#CLASP "wikilink")
provides guidance to project participants — e.g., project managers,
security auditors, developers, architects, testers, and others — that is
easy to adopt to their way of working; this results in incremental
improvements to security that are easily achievable, repeatable, and
measurable.

### CLASP Vulnerability Lexicon

[CLASP](Glossary#CLASP "wikilink") also contains a comprehensive
Vulnerability Lexicon that helps development teams avoid/remediate
specific designing/coding errors that can lead to exploitable security
services. The basis of this Lexicon is a highly flexible taxonomy —
i.e., classification structure — that enables development teams to
quickly locate Lexicon information from many perspectives: e.g., problem
types (i.e., basic causes of vulnerabilities); categories of problem
types; exposure periods; avoidance and mitigation periods; consequences
of exploited vulnerabilities; affected platforms and programming
languages; risk assessment.

### Automated Analysis Tool

Much of the information in the [CLASP](Glossary#CLASP "wikilink")
Vulnerability Lexicon can be enforced through use of automated tools
using techniques of static analysis of source code.

## Overview of CLASP Process

This section provides an overview of
[CLASP](Glossary#CLASP "wikilink")’s structure and of the dependencies
between the [CLASP](Glossary#CLASP "wikilink") process components and is
organized as follows:

  - CLASP Views
  - CLASP Resources
  - Vulnerability Use Cases

### CLASP Views

The [CLASP](Glossary#CLASP "wikilink") process is presented through five
high-level perspectives called [CLASP](Glossary#CLASP "wikilink") Views.
These views are broken down into activities which in turn contain
process components. This top-down organization by View \> Activity \>
Process Component allows you to quickly understand the
[CLASP](Glossary#CLASP "wikilink") process, how
[CLASP](Glossary#CLASP "wikilink") pieces interact, and how to apply
them to your specific software development lifecycle. These are the
[CLASP](Glossary#CLASP "wikilink") Views:

  - Concepts View
  - Role-Based View
  - Activity-Assessment View
  - Activity-Implementation View
  - Vulnerability View

See figure 1.

![CLASP_Views.gif](CLASP_Views.gif "CLASP_Views.gif")

### CLASP Resources

The [CLASP](Glossary#CLASP "wikilink") process supports planning,
implementing and performing security-related software development
activities. The [CLASP](Glossary#CLASP "wikilink") Resources provide
access to artifacts that are especially useful if your project is using
tools to help automate [CLASP](Glossary#CLASP "wikilink") process
pieces. This table lists the name and location of
[CLASP](Glossary#CLASP "wikilink") Resources delivered with
[CLASP](Glossary#CLASP "wikilink") and indicates which
[CLASP](Glossary#CLASP "wikilink") Views they can support:

| CLASP Resources                                                                                                     | Location   |
| ------------------------------------------------------------------------------------------------------------------- | ---------- |
| Basic Principles in Application Security (all Views)                                                                |            |
| Example of Basic Principle: Input Validation (all Views)                                                            |            |
| Example of Basic-Principle Violation: Penetrate-and-Patch Model (all Views)                                         |            |
| Core Security Services (all Views; especially III)                                                                  |            |
| Sample Coding Guideline Worksheets (Views II, III & IV) Note: Each worksheet can be pasted into a MS Word document. | Resource E |
| System Assessment Worksheets (Views III & IV) Note: Each worksheet can be pasted into a MS Word document.           | Resource F |
| Sample Road Map: Legacy Projects (View III)                                                                         |            |
| Sample Road Map: New-Start Projects (View III)                                                                      |            |
| Creating the Process Engineering Plan (View III)                                                                    |            |
| Forming the Process Engineering Team (View III)                                                                     |            |
| Glossary of Security Terms (all Views)                                                                              |            |
|                                                                                                                     |            |

### Vulnerability Use Cases

The [CLASP](Glossary#CLASP "wikilink") Vulnerability Use Cases depict
conditions under which security services can become vulnerable in
software applications. The Use Cases provide
[CLASP](Glossary#CLASP "wikilink") users with easy-to-understand,
specific examples of the cause-and-effect relationship between
security-unaware design/source coding and possible resulting
vulnerabilities in basic security services — e.g., authentication
authorization, confidentiality, availability, accountability, and
non-repudiation. The [CLASP](Glossary#CLASP "wikilink") Vulnerability
Use Cases are based on the following common component architectures:

  - Monolithic UNIX
  - Monolithic mainframe
  - Distributed architecture (HTTP\[S\] & TCP/IP)

It is recommended to understand the [CLASP](Glossary#CLASP "wikilink")
Use Cases as a bridge from the Concepts View of
[CLASP](Glossary#CLASP "wikilink") to the Vulnerability Lexicon (in the
Vulnerability View) since they provide specific examples of security
services becoming vulnerable in software applications See figure 2.
![CLASP_Vulnerability_Use_Cases.gif](CLASP_Vulnerability_Use_Cases.gif
"CLASP_Vulnerability_Use_Cases.gif")

### CLASP Best Practices

The foundation of CLASP is in seven key Best Practices for application
security. See [CLASP Best
Practices](:Category:CLASP_Best_Practice "wikilink").

1.  [Institute awareness
    programs](:Category:BP1_Institute_awareness_programs "wikilink")
2.  [Perform application
    assessments](:Category:BP2_Perform_application_assessments "wikilink")
3.  [Capture security
    requirements](:Category:BP3_Capture_security_requirements "wikilink")
4.  [Implement secure development
    practices](:Category:BP4_Implement_secure_development_practices "wikilink")
5.  [Build vulnerability remediation
    procedures](:Category:BP5_Build_vulnerability_remediation_procedures "wikilink")
6.  [Define and monitor
    metrics](:Category:BP6_Define_and_monitor_metrics "wikilink")
7.  [Publish operational security
    guidelines](:Category:BP7_Publish_operational_security_guidelines "wikilink")

## CLASP and Security Policies

A high-level view of [CLASP](Glossary#CLASP "wikilink") can help
increase awareness of the importance of implementing application
security on these organizational levels, from the bottom up: \> best
practices of application-security \> application-security policy \> IT
security policy \> operations security policy \> corporate security
policy.
![CLASP_and_Security_Policies.gif](CLASP_and_Security_Policies.gif
"CLASP_and_Security_Policies.gif")

## What is a Security Vulnerability

[CLASP](Glossary#CLASP "wikilink") defines a security vulnerability as a
flaw in a software environment — especially in an application — that
allows an attacker to assume privileges within the user's system,
utilize and regulate its operation, compromise the data it contains,
and/or assume trust not granted to the attacker. A security
vulnerability occurs in a software application when any part of it
allows a breach of the security policy governing it.
[CLASP](Glossary#CLASP "wikilink") identifies 104 underlying problem
types that form the basis of security vulnerabilities in application
source code. An individual problem type in itself is often not a
security vulnerability; frequently it is a combination of problems that
create a security condition leading to a vulnerability in the source
code. [CLASP](Glossary#CLASP "wikilink") divides the 104 problem types
into 5 high-level categories. Each problem type may have more than one
parent category. [CLASP](Glossary#CLASP "wikilink") defines a
consequence of an exploited or exploitable vulnerability as a failure in
one or more of these basic security services:

  - Authorization (resource access control)
  - Confidentiality (of data or other resources)
  - Authentication (identity establishment and integrity)
  - Availability (denial of service)
  - Accountability
  - Non-repudiation

The following figure shows in which phases of the software development
lifecycle a security-related vulnerability can occur and also which
points in an operational system an attack can target.
![CLASP_Vulnerabilities_SDLC_Phases.gif](CLASP_Vulnerabilities_SDLC_Phases.gif
"CLASP_Vulnerabilities_SDLC_Phases.gif")

## Overview of CLASP Taxonomy

The [CLASP](Glossary#CLASP "wikilink") taxonomy is a high-level
classification of the [CLASP](Glossary#CLASP "wikilink") process,
divided into the following classes for better evaluation and resolution
of security vulnerabilities in source code:

  - **Problem types** underlying security-related vulnerabilities.
  - **Categories** into which the problem types are divided for
    diagnostic and resolution purposes.
  - **Exposure periods** (i.e., SDLC phases) in which vulnerabilities
    can be inadvertently introduced into application source code.
  - **Consequences** of exploited vulnerabilities for basic security
    services.
  - **Platforms** and programming languages which may be affected by a
    vulnerability.
  - **Resources** required for attack against vulnerabilities.
  - **Risk assessment** of exploitable/exploited vulnerabilities.
  - **Avoidance and mitigation periods** (i.e., SDLC phases) in which
    preventative measures and countermeasures can be applied.

See figure 6. ![CLASP_Taxonomy.gif](CLASP_Taxonomy.gif
"CLASP_Taxonomy.gif")

## Applying CLASP Components

This page describes a possible sequence for applying
[CLASP](Glossary#CLASP "wikilink") components, using the Sample Coding
Guidelines ([CLASP](Glossary#CLASP "wikilink") Resource E) as a basis.
See figure 7.
![CLASP_Applying_Components.gif](CLASP_Applying_Components.gif
"CLASP_Applying_Components.gif") The steps below describe a possible
sequence for applying [CLASP](Glossary#CLASP "wikilink") components
depicted in the figure above:

  - Read the [CLASP](Glossary#CLASP "wikilink") Concepts View to gain an
    overview of the [CLASP](Glossary#CLASP "wikilink") process.
  - In the Concepts View, pay special attention to the page Description
    of [CLASP](Glossary#CLASP "wikilink") Process. This page contains a
    diagram showing, among other things, the location of the 104
    [CLASP](Glossary#CLASP "wikilink") problem types (i.e., basic causes
    of vulnerabilities), the five high-level, source-code-related
    categories by which they are organized, and the consequences of
    exploitable security vulnerabilities for security services.
  - Read the [CLASP](Glossary#CLASP "wikilink") Sample Coding Guidelines
    thoroughly and select a subset of them relevant to your specific
    software development project. These guidelines contain a set of
    security-related coding standards to be applied to your project.
  - Apply the remaining [CLASP](Glossary#CLASP "wikilink") Resources
    throughout the planning, design, construction, and testing process,
    as needed.
  - Use the Sample Coding Guidelines to select a subset of the 104
    [CLASP](Glossary#CLASP "wikilink") problem types (i.e., basic causes
    of vulnerabilities) — located in the
    [CLASP](Glossary#CLASP "wikilink") Vulnerability View — which are
    most important to your project.
  - Familiarize yourself with the [CLASP](Glossary#CLASP "wikilink")
    Role-Based View, which provides an overview of the project roles
    associated with applying the selected subset of Sample Coding
    Guidelines, and assign these guidelines to your relevant project
    personnel — e.g., designer, security auditor, implementers.
  - Consider the subset of vulnerabilities selected in part though the
    Sample Coding Guidelines when using the Activity-Assessment View to
    assess and select the desired subset of 24 activities contained in
    the Activity-Implementation View.

## CLASP and IT Internal Controls

A significant number of the internal controls required by the
Sarbanes-Oxley Act for assurance of accurate and reliable corporate
financial reporting are located in the IT area. The figure below shows
how [CLASP](Glossary#CLASP "wikilink") can help secure the IT internal
controls that are necessary to assure the integrity of data in financial
applications within the scope of security-related software development
projects.
![CLASP_IT_Internal_Controls.gif](CLASP_IT_Internal_Controls.gif
"CLASP_IT_Internal_Controls.gif")