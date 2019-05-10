**Soc 08 proposals for direct vote**

## OWASP Code review guide, V1.1

  - Eoin Keary,

**Code Review Guide Proposal**:

**Introduction:**The code review guide is currently at version RC 2.0
and the second best selling OWASP book. I have received many positive
comments regarding this initial version and believe it’s a key enabler
for the OWASP fight against software insecurity.

It has even inspired individuals to build tools based on its information
and I have convinced such people (Alessio Marziali) to open source their
tool and make it an OWASP project.

The combination of a book on secure code review and a tool to support
such an activity is very powerful as it gives the developer community a
place to start regarding secure application development.

**Proposal:** I am proposing that I improve the code review guide from a
number of aspects. This should place the guide as a de facto secure code
review guide in the application security industry.

**Additional and expanded Chapters:**
**Transactional analysis**
Expand chapter.
Examples via diagrams.
**Threat Modeling and Analysis**
The approach to examining an application to be reviewed.
Focusing on areas of interest.
**Example reports and how to write one**
How to determine the risk level of a finding.
**Automated code review**
Code crawler documentation and usage.
**Rich Internet Applications**
Expanded chapters on Flash, Ajax.
**The OWASP ESAPI (Enterprise Security API)**
What it is, Why use it. What to review.
**Code review Metrics:**
How to compile, use and analyse metrics.
Rolling out metrics in the Enterprise.
**Integrating Code review with an existing SDLC** Integration of Secure
Code review with an existing SDLC.
Secure Code review roadmap definition.
Documentation requirements.
Scope definition.
SDLC steering comittee establishment.
Performace criteria, benchmarks and metrics.
Integration of SDLC results into key IT governance areas.
Critical success factors.

## The Ruby on Rails Security Guide v2

Heiko Webers

The last security guide for Rails
[1](http://www.owasp.org/index.php/Category:OWASP_Web_Application_Security_Put_Into_Practice)
was a great success, with a lot of more secure web applications and
continued awareness in the community of security issues. The Ruby on
Rails Security Project [2](http://www.rorsecurity.info/) is the one and
only source of information about Rails security topics, and I keep the
community up-to-date with blog posts and conference talks in Europe. The
Guide and the Project has been mentioned in several Rails books and
web-sites.

Version 1 of the Ruby on Rails Security Guide was sponsored by the SpoC
07, set the standard for OWASP programming language specific guides in
terms of the topic outline and has been published as a book
[3](http://www.lulu.com/content/1412042). Nevertheless I'm convinced
that a more compact design and a "question-and-answer" style of writing
will reach an even larger audience. Of course the new Guide will still
include answers to the OWASP Top Ten security vulnerabilities.

A lot has changed since the publishing of the first Guide. Some new
security holes have been found, there are new advises and most
importantly Rails version 2.0 has been released. The new Ruby on Rails
Security Guide aims at providing an up-to-date coding and configuration
guide for the Rails community.

In the new Rails Security Guide I'd like to

  - update the entire book to match Rails 2.0
  - cover new topics, including, but not limited to:
      - Intranet and administration interface security,
      - phishing,
      - real-world attack situations,
      - short excursus on server monitoring,
      - the new CookieStore session management,
      - vulnerabilities in popular plug-ins,
      - denial-of-service attacks
  - cover all OWASP Top Ten security vulnerabilities
  - a more compact writing style, more examples and
    "questions-and-answers"
  - introduce the OWASP and Rails security to a greater audience

## P028 - OWASP UI Component Verification Project (a.k.a. OWASP JSP Testing Tool)

Submitted by Jason Li

### Personal Background

Jason is an Application Security Engineer at Aspect Security during
which time he has performed code reviews, penetration testing and
training at a variety of financial, commercial, and government
institutions. He is a certified GIAC Secure Software Programmer in Java
and before joining Aspect, he was a Java Software Developer and a Java
course instructor for Johns Hopkins University. He also assisted Arshan
Dabirsiaghi with the coding of OWASP AntiSamy. Jason received his
Master's and B.S from Cornell University (both in Computer Science). He
has recently completed the degree requirements for his Post-Master's in
Computer Science with a concentration in Information Security, which
will be conferred in May 2008 by Johns Hopkins University.

### Project Motivation

Cross-site scripting is one of the most pervasive web application
security vulnerabilities present in today's applications, ranking at the
top of the most recent OWASP Top Ten (2007). Recently, UI frameworks
have emerged that allow application developers to create web components
quickly and effortlessly. Java EE facilitates this ability by providing
JSP tags that can be conglomerated as a tag library, such as was done
with Java Server Faces (JSF). These tags allow developers to create rich
user interfaces by parameterizing attributes of the web component. With
the advent of this design, a unique opportunity arises to prevent
cross-site scripting. If tag libraries offered built-in protection from
cross-site scripting, then using parameterized web components to prevent
cross-site scripting could become analogous to using parameterized
queries to prevent SQL injection. However, security is not always in
mind when such tag libraries are developed and thus it is not clear
which libraries, if any, offer such built-in protection. This project
would allow developers to quickly determine the protection mechanisms
provided by any tag libraries they develop or of any third-party tag
libraries they are considering using for their application. This will
enable a push to parameterize web components which will serve to make
web applications safer.

### Objectives

The goal of this project is to create an easy to use, freely available
tool that can be used to quickly ascertain the level of protection that
each component of a JSP tag library offers. This information can serve
two purposes:

1.  It provides a means for projects to create a coding standard. By
    identifying which components are safe or unsafe, a project can
    establish a preference order of useable components. For those
    components identified as unsafe, extra security requirements can be
    imposed on any pages using those components
2.  It provides tag library providers development guidance. Providers
    can target security enhancements to the components that are most
    susceptible to cross-site scripting attacks. They can also use these
    results to demonstrate their performance relative to other competing
    tag libraries. It also provides feedback for developers that create
    small custom tag libraries for internal development usage.

Ideally, the input to the tool will be the Tag Library Descriptor file
along with a compiled version of the tag library. The resulting output
will be a report of all tags in the library and their associated
attributes with annotations for each attribute indicating whether or not
it safely handles tainted input. Additionally, the framework for this
tool should be robust enough to enable the functionality indicated by
the future work section.

### Development Stages

The following initial steps should be made to create a first run draft
of the project:

  - **Identify or Create Tag Library Parser**: The first step of this
    project is to determine a way to parse tag libraries and instantiate
    tag objects for testing. The Java EE API includes interfaces to
    parse and instantiate JSP tags so an initial investigation into
    existing implementations of tag parsers may yield an adequate
    source. However, since the interfaces are specified as protected and
    application server implementation specific, the interdependencies
    may require the creation of such a parser from scratch
  - **Basic Test of Tags**: The second step is to use the parser and
    apply some basic initial test cases to test the protection of
    attributes from tainted input
  - **Design Report Format**: The third step is to tabulate the results
    and create a simple format to convey those results.

After this step, the project should be considered halfway towards its
goals. Additionally, the following steps should be made to move towards
project completion:

  - **Refine Tag Testing**: After initial proof of concept, significant
    effort should be made to vary the testing of tag attributes to give
    a reasonable level of assuredness regarding the accuracy of the
    results
  - **Refine Report Format**: Feedback should be solicited and
    improvements incorporated to the design of the report
  - **Documentation and Release**: Once test cases and report format
    have been improved, documentation for the project should be created
    and the project source code prepared for release.

### Future Vision

While tag libraries offer a means to parameterize web components and
potentially better protection from XSS, there are still applications
that use raw JSPs and scriptlets. With the insight gained from
generating test cases, the JSP Testing Tool should be enhanced to test
not only pages using JSP tag libraries, but also basic JSPs as well. One
possible strategy is to create a wrapper HttpServletRequest class that
overrides methods to provide input directly from test cases generated
from the earlier stages of this project. A similar wrapper
HttpServletResponse class can then be used to test the results. The tool
could then be used to quickly test the XSS protection level of any Java
EE application that uses JSP technology. Unlike automated web scanners,
this tool enhancement would have the benefit of internal insight to the
application to determine injectable parameters. Additionally, this tool
enhancement would be an improvement to static code analysis as it could
reduce the number of false positives with the ability to invoke actual
rendering of the HTTP response.

## Internationalization Guidelines and OWASP-Spanish Project

  - Juan Carlos Calderon

**Executive Summary**
The main goal of OWASP is to spread the word about security (“Our
mission is to make application security "visible," so that people and
organizations can make informed decisions about application security
risks.”) and OWASP has done great work so far :). And now it’s time for
a next big step.

The number of native and secondary speakers in the world for Chinese,
Spanish, French, Russian, Arabic and Indi languages are estimated in
similar number to English speaking or even more (Some References at
[Ethnologue](http://en.wikipedia.org/wiki/Ethnologue_list_of_most_spoken_languages),
[Encarta](http://encarta.msn.com/media_701500404/Languages_Spoken_by_More_Than_10_Million_People.html),
[Wikipedia](http://en.wikipedia.org/wiki/List_of_languages_by_number_of_native_speakers)).
I think is a good time for OWASP to reach those that do not speak
English to have full access to all the OWASP materials, not just a
couple of documents.

OWASP, while open to translations, do not have clear guidelines on how
to translate OWASP contents and (AFAIK) there is no multi-language
support in OWASP.org site. This is understandable as there is no formal
project for internationalization so far.

**Oportunity and Effort**
This is great opportunity to make Spanish the first language on which
the OWASP site and documentation is fully translated and at the same
time share the experience with other people interested in the same
objective, Bring OWASP to the world. And this is something I’ve being
pushing for some time ago and that could be possible “at once” via SoC
2008.

I understand this is significant effort so to have it done I will count
with the help of 6 people (friend of mine, all of them Security auditors
with excellent English level) plus a few well known contributors from
OWASP-Spanish effort, so the founding will be divided among the people
involved in the same proportion of the work they do for the completion
of this effort. This, to encourage delivery.

**Objectives and Deliverables**
\* Team up with Larry Casey to implement Multilanguage support in
OWASP.org Mediawiki.

  - General Guidelines on minimum/recommended requirements to start a
    new language translation for OWASP Document and Site Pages
  - General Guidelines on minimum/recommended requirements to implement
    internationalization and localization
    ([i18n](http://www.w3.org/International/)) on OWASP Software
  - Full translation to Spanish of all the release-level document
    projects. Those are:
      - Top 10 2007
      - Guide 2 (Already translated)
      - Testing Guide (Already Translated)
      - Legal
      - FAQ
  - Full Translation of major sections of OWASP Site
      - Project Main Pages (Release, Beta and Alpha levels for both
        documents and tools projects)
      - Principles
      - References Section
      - Conferences
      - News (Those currently displayed in OWASP site)
      - About OWASP
  - Evaluation of Spanish translation approach for WebGoat and WebScarab
    and delivery of this document to Bruce and Rogan for possible
    implementation in near future.
  - Leverage for deploy of es.owasp.org, the domain already exists but
    is not redirecting correctly.
  - Create a Communication strategy to help and keep track on new pages
    or changes in significant pages so all the translations are in sync.

**Out of Scope**
Translation of the following sections are NOT in Scope

  - Local Chapters Pages
  - Presentations
  - Conferences
  - Videos
  - Blogs
  - All the projects deliverables in Alpha and Beta Stages
  - All the documentation “on development” like Guide Version 3.0
  - Translation of Pages, documentation or tools to other language other
    than Spanish according to the stated in above section.

**Why should I be sponsored for the project?**
I’ve being part of contributions to OWASP documents on the translation
arena since 2005
[4](https://lists.owasp.org/pipermail/owasp-spanish/2005-March/000069.html),
a few of them by making possible the translation of OWASP Top 10 2004
[5](http://www.owasp.org/index.php/Top_10_2004) and OWASP Testing Guide
V1.17 [6](http://www.owasp.org/docroot/owasp/misc/testing_spanish.pdf)
to Spanish. It is time to make the full job done :).

I have 10 years of experience on Web technologies. During 8 years I have
performed and leaded hundreds of Security Source Code Reviews and Black
box testing on Web Applications. On my current job I lead 30 people in
diverse locations all of them working on the Application Security arena,
so I am accustomed to execute and deliver.

## The Application Security Desk Reference - ASDR

  - Leonardo Cavallari Militelli
  - Proposal: Make [OWASP ASDR Project](OWASP_ASDR_Project "wikilink") a
    release quality document.

The ASDR is a reference volume that contains basic information about all
the foundational topics in application security. It intends to replace
and refresh [Honeycomb Project](OWASP_Honeycomb_Project "wikilink") with
a new structure for articles and relationship between categories, thus
making it a release quality doc.

This idea raised when finished the [Attack Reference
Guide](Attack "wikilink") for [OWASP Spring Of Code
2007](OWASP_Spring_Of_Code_2007 "wikilink"), where it was identified
that OWASP reference articles need some special attention. Jeff Williams
is totally supporting this project.

We already have defined which type of article we should include on Desk
Reference, as follows:

  - [Principles](:Category:Principle "wikilink")
  - [Threat Agents](:Category:Threat_Agent "wikilink")
  - [Attacks](:Category:Attack "wikilink")
  - [Vulnerabilities](:Category:Vulnerability "wikilink")
  - [Countermeasures](:Category:Countermeasure "wikilink")
  - [Technical Impacts](:Category:Technical_Impact "wikilink")
  - [Business Impacts](:Category:Business_Impact "wikilink")

<!-- end list -->

  - Road Map: A complete project roadmap can be found on **[ASDR Table
    of Contents](ASDR_Table_of_Contents "wikilink")**. Basically, the
    following activities should be performed, some of them already
    started:
      - Define articles templates for each reference type
      - Define subcategories for articles classification
      - Compile first DRAFT version of ASDR Book
      - Articles development & Call for Volunteers
      - Articles revision
      - First version of OWASP ASDR book

## OWASP .NET Project Leader

  - Mark Roxberry

**Project Proposal**

This proposal is to request approval for leading the OWASP .NET project.
The project will contain information, materials and software that are
relevant to building secure .NET web applications and services. The goal
of the project is to provide deep content for all roles related to .NET
web applications and services including:

  - Architectural guidance
  - Developer tools, information and checklists
  - IT professional content (for those that deploy and maintain .NET
    websites)
  - Penetration testing resources
  - Incident response resources

The OWASP .NET Project Leader will actively recruit .NET contributors,
including personnel from Microsoft, but others throughout the .NET
ecosystem. Including experts from communities from large companies to
ISVs, from enterprise architects to ALT.NET developers will be important
for the overall reach of the OWASP .NET project. Other communities to
consider include developers who use Mono (.NET for Linux), including
Moonlight (Silverlight for Linux).

The OWASP .NET Project Leader will actively contribute to the OWASP
projects that require .NET resources, by recruiting resources or
contributing to the project.

**Deliverables**

April 2, 2008 - May 3, 2008

  - Project site layout reorganization
  - Presentation materials for OWASP chapters for integrating the OWASP
    .NET project tools and references into a project life cycle
  - Bullet points for community and media outreach plans

April 13, 2008 - May 16, 2008

  - Community outreach - contact .NET user groups, OWASP chapters to get
    feedback about tools and references that are needed for security in
    their fields of expertise. Distribute materials for integrating
    OWASP .NET into their project plans and toolboxes.
  - Media outreach - contact .NET media resources to talk about the .NET
    project and request content and contributors
  - Start a special projects section for emerging projects in the .NET
    space, including Silverlight (Moonlight), WPF XBAP applications,
    Windows Communication Foundation, ADO.NET Data Services, Enterprise
    Library 4.0, Policy and Dependency Injection, Agile methodologies.

May 17, 2008 - June 14, 2008

  - Reach out to other SoC .NET projects, try to find resources if the
    projects need them.
  - Contribute to other SoC .NET projects, where needed.
  - Gather feedback and follow up from first round of outreach effort.

June 15, 2008

  - Status report for Project

June 16, 2008 - August 31, 2008

  - Expand community and media outreach efforts.
  - Continue to recruit and help other OWASP projects with resources.
  - Update promotional materials to include emerging projects.

August 31, 2008

  - Retrospective of the first 5 months of the OWASP .NET Project.

**Long Term Vision**

The OWASP .NET Project will be a valuable resource for securing .NET
applications and services. I want people to think of this project first
when they need to gather information or find tools for designing,
developing, maintaining, pen-testing software developed with .NET. This
project will be the hub for all .NET security resources, and of course
with content created and maintained by the Open Source community.

**Why I should be sponsored for the project**

I have previously contributed to the OWASP Test Guide v2 project,
providing content and reviewed content. I have used the OWASP Top 10 to
teach developers about vulnerabilities in web applications and the OWASP
WebScarab tool for vulnerability analysis. As a security practictioner,
I care about the OWASP mission and I want to contribute to securing the
Internet for everyone.

I have 15 years of technical leadership experience using Microsoft
technologies. I have lead software development teams as a technical
lead, lead developer and architect on small and large projects. I am a
Certified Information Systems Security Professional (CISSP) and a
Certified Ethical Hacker (C |EH). I am on top of current trends and I am
required to be up to speed regarding .NET web development and security.
I am personally interested in providing security resources to .NET
developers globally, specific and applicable to their projects.

## OWASP Education Project

`Dinis Comment: Please take into account the materials created here: `<http://www.owasp.org/index.php/Category:OWASP_Education_Project>` `
` and the PPTs in the ' OWASP Education Presentations' section of `<http://www.owasp.org/index.php/OWASP_Education_Presentation>

  - Martin Knobloch

**OWASP Education Project / OWASP Boot Camp**

The project will continuously deliver education material about OWASP
tooling and documentation. This aims to create an easy entrance towards
understanding application security and usage of the OWASP tooling. By
creating education documentation papers, screen scrape video courses and
setting up an OWASP Boot camp, a controlled education process of a
standardized quality can be created continuously. With the setup of a
OWASP Boot camp, the OWASP word can be spread in a controlled manner and
deliver high quality training., both inside and outside of the OWASP
community. The OWASP Education Project will setup and standardize OWASP
trainings manuals and materials to ensure a certain level of quality of
the trainings. Trainings about the OWASP tooling and projects will have
to be reviewed by the Projects.

'''Complexity - What is the project Complexity and Size? '''

Deliverables to focus on are, in first place, to set up an OWASP Boot
camp. For this the project will create a training and video (screen
scrape) training material about Application Security basics, using the
OWASP WebGoat and OWASP WebScarab tooling on the OWASP Top Ten
vulnerabilities. Next, creating training material on the main OWASP
Project's as the OWASP Guide and OWASP Testing Guide.

'''Member Value - How big is the potential added value to OWASP Members?
'''

The OWASP Education project ensures a common shared set of knowledge
about application security in general and the OWASP tooling in detail.
The OWASP Boot camp helps new OWASP members to get on track fast and on
a guaranteed quality level.

'''Brand Value - How big is the potential added value to the OWASP
Brand? '''

The OWASP Education projects Boot camp deliverable can help to spread
the OWASP word beyond the OWASP community. Holding OWASP Boot camps can
generate additional venue. The OWASP Education project will extend the
knowledge about the OWASP tooling and the usage of those. In the current
discussion of the OWASP certification, the OWASP Education project can
support and certify training. The OWASP certification can be supported
by special OWASP Certification Boot camps.

'''On the Candidate: '''

Past Work - Value of past contributions to OWASP Projects; previously,
as OWASP On The Move project lead, I was involved in setting up the
OWASP On The Move rules. I am involved in the Dutch local chapter inside
the chapter board, focusing on the content, speakers and feedback of the
local chapter meeting. On the AppSec Australia conference I was speaker
on the subject on what to consider when implementing a Secure
Development Process. On my daily job, being Software Architect at Sogeti
Nederland B.V., I have set up a Secure Development Taskforce. I have
succeeded to make Sogeti Nederland B.V. and member of the OWASP
community. Sogeti sponsored previous local Dutch chapter meetings and my
trip to Australia. The deliverables of the Sogeti Secure Development
Taskforce (PaSS, Proactive Security Strategy) are given to the OWASP
community, as we will continue to do in the future.

## The OWASP Testing Guide v3

  - Matteo Meucci
  - The OWASP Testing Guide v2 was a great success, with thousand
    downloads and many many Companies that have adopted it as standard
    for a Web Application Penetration Testing.

Now it's time to begin a new project that is based on v2 but improve it
and complete it.

In the OWASP Testing Guide v2 we have split the set of tests in 8
sub-categories:

`   * Information Gathering`
`   * Business logic testing`
`   * Authentication Testing`
`   * Session Management Testing`
`   * Data Validation Testing`
`   * Denial of Service Testing`
`   * Web Services Testing`
`   * AJAX Testing `

The following are my thoughts about the new OWASP Testing Guide v3:

1\) Authorization testing missing. As Jeff and Dave said many time
before it's important to create a new category. 2) Information gathering
is not a set of vulnerabilities --\> not in report --\> new category:
Passive mode analysis 3) Infrastructural test --\> new category 4) Web
Services section needs improvement 5) AJAX Testing section needs
improvement 6) New category: Client side Testing. AJAX and Flash Testing

  - This
    [document](http://www.owasp.org/index.php/Image:Planning_OTGv3.doc)
    analyze the OWASP Testing Guide v2 vulnerabilities and a plan for
    create the new v3.

## OWASP Application Security Verification Standard

  - Mike

**OWASP Application Security Verification Standard Proposal**

**Educational and professional background**

The applicant is a hands-on senior professional services manager with a
trademark of developing creative solutions to complex application
security-related technical problems.

**Application security experience and accomplishments**

The applicant has a background in trusted product evaluation:

  - CC evaluation
  - CC evidence development, including operating system test code
    development
  - CC project management
  - TCSEC evaluation
  - TCSEC project management
  - TEF management
  - CCTL management

The applicant also has a background in security-related software
development and integration:

  - PKI toolkit development
  - PK-E application integration
  - Secure web portal application development
  - Secure web portal integration
  - Secure instant messaging application development, including three
    patents

The applicant also has a background in cryptomodule testing:

  - FIPS 140 evaluation
  - FIPS 140 evidence development

**Participation and leadership in open communities**

The applicant does not have experience in contributing to open
communities.

**The opportunity, challenges, issues or need your proposal addresses**

OWASP is looking for a commercially-workable open standard for
performing application security verification efforts. The problem is
that there is a huge range in the coverage and level of rigor available
in the market, and consumers have no way to tell the difference between
someone just running a grep tool, and someone doing painstaking code
review and manual testing. So, a standard is needed.

**Objectives or ways in which you will meet the goal(s)**

The applicant’s proposal will address the above challenges as follows:

  - The applicant will define an evaluation framework that may be used
    to conduct OWASP Application Security Verification Standard
    certifications.
  - The applicant will define an OWASP Application Security Verification
    Standard which defines levels that applications may be certified
    against.

**Specific activities and who will carry out these activities**

The applicant will carry out these activities. Please see below for a
proposed list of specific deliverables.

**Specific deliverables and a rough project schedule so we can track
progress**

The applicant proposes the following deliverables:

  - **Scheme Overview document.** This will define the overall framework
    with roles, responsibilities, and processes.
  - **Evaluation and Certification document.** This will describe the
    evaluation and certification process.
  - **Conditions for the Use of Trademarks.** This will describe OWASP’s
    name, logo, and certificate may be used and referenced.
  - **Evaluation Report Content Requirements.** This will describe the
    content requirements of evaluation reports.
  - **OWASP Application Security Verification Standard.** This will
    define the levels that applications may be certified against.
  - **OWASP Application Security Verification Standard Appendix A.**
    This will define the required content of the OWASP Application
    Security Verification Standard Security Policy.
  - **Policy Letter \#1. Acceptance of Security Policies into OWASP
    Evaluation** This will define the requirements to be listed as in
    evaluation on the OWASP web site.

The applicant proposes the following rough project schedule:

  - 2nd April. Project kickoff.
  - 15th June. Alpha Quality drafts of Scheme Overview document and of
    OWASP Application Security Verification Standard document completed.
  - 31st August. Project completion. Beta Quality drafts of all
    documents completed.

**Long-term vision for the project**

The long-term vision for the project is to normalize the range in the
coverage and level of rigor available in the market when it comes to
performing application security verification.

**Any other reasons why you and your project should be selected.**

The applicant has a uniquely-qualified perspective given his experience
with TCSEC, TTAP, CC, FIPS 140-1, and FIPS 140-2 evaluation programs,
and his real-world perspective as a developer and integrator of
security-related applications.

## Online code signing and integrity verification service for open source community (OpenSign Server)

by *Phil Potisk* and *Richard Conway*

It is the opinion of this pair that there is a decided lack of code
signing and integrity checking support for the open source community.
The purpose of this project would be to build and host a feature-rich
server and suite of client utilities with adequate secure hardware to
ensure the integrity of code modules.

**Summary**
The service will allow all .NET and Java code modules to be uploaded to
the service to be signed by a community code signing key. Each community
(such as OWASP) will have a key and corresponding Software Publishing
Certificate (SPC) which can optionally be embedded in the code module
itself. Generally, however, the service is intended for developers and
the wider community of concerned users that want to ensure that their
downloaded portable executable is exactly what it purports to be. The
root key will be stored in an HSM and will sign an SPC from a locally
generated key-pair of which the public key will be sent to the service.
Key pair generation can be made and submitted using standard .NET delay
signing and jar signing tools distributed with the SDKs, however, the
project remit will ensure that a client-side graphical tool for each
environment is available to generate the keys pairs needed to sign code
with and allow submission to the code signing service for signing and
generation of SPC by the server's proprietary CA. Anonymity will not be
allowed so the project will include a database of users which will be
the basis of directory for SPCs.

There will be a web and web services interface using an online login and
WS-Security respectively which will allow the code to be uploaded on
demand and signed by a code signing key with the option to embed the
certificate or not.

**Problem domain**
\- Current download of portable executables inherently insecure with
only a CRC/MD5 check
\- No open source standard for code signing and delivery of portable
executables between developers to test for tamper evidence
\- No managed service for code signing outside of verisign or other paid
for X509 signing service
\- Process currently very mechanical with use of command line tools or
PKCS\#10 software requests which should be abstracted from developer
**Ideal Solution**
\- Ensure third party verification of code modules through a dedicated
PKI backbone
\- Educate the OWASP and wider open source community in the use of code
signing
\- Replace standard CRC/MD5 hash usage with some more secure that can be
repudiated if challenged - Use an internet infrastructure to allow the
dissemination of certificates (potentially multipurpose in later
versions)
\- Ensure accountability through actions logging and authentication
\- Standardise a set of open source client tools for the creation of
keys and manipulation of certificates
**Graphical Interfaces**
\- Client tool to generate RSA key pair and request signing certificate
by return via a secure connection, secure connection will authenticate
user after a dedicated registration process and also use mutual
authentication SSL to avoid man-in-the-middle - returning certificate to
user in real time. Registered developer can then submit their SPC online
to verify the SPC.
\- Client tool to download software that will do a proper verification
on the software against the code signing service
\- Website interface for the code signing service
\- Set of Admin tools to manage the code signing service, user and
certificate repository
**Added advantage**
Environment can be secured and tested regularly by members of Owasp to
ensure the security of the server and infrastructure haven't been
hijacked\! The project will only be as secure the server environment\!

**Breakdown of tasks**
\- Server setup and installation of OpenLDAP
\- Installation of Mock HSM (eAladdin token)
\- Creation of PKCS\#11 for key management and key creation activities
\- Installation of Java/.NET SDKs
\- Development of codebase for signing using SDK tools (later versions
will reverse engineer this into jar/assemblies directly)
\- Library for creating SPC (CA)
\- User registration, authentication, activity logging, database
support
\- OpenLDAP user/certificate repository, access using
mutual-authentication SSL
\- Development of client tool suite
\- Development of administrator tools
\- Procurement of FIPs compliant HSM and installation
\- Administrator/user manuals
\- Pen testing of solution by OWASP members
\- Go live\!
**Post July completion tasks**
\- Support for Microsoft office documents with macros and others
\- Full support for community management (i.e. OWASP differentiated from
other developer communities)
**Background and Experience of project team**
Richard Conway has 13 years commercial development experience in
messaging and financial/investment banking systems having managed teams
to deliver complex Agile solutions. He has degrees and PGDip in computer
science and another in physics (finishing 2009) and has taught at
Westminster university and written 7 books 3 of which are on security
related topics (and numerous articles).

Phil Potisk has an academic background from Graz university, degree and
masters and is currently looking at doing a pHD in the UK all on
computer science/information security. He has several years commercial
experience all in the security space for major companies in Austria and
the UK.

Both Richard and Phil have worked together for 4 years in the space of
ePassports/smart cards where they have an impact on ICAO standards and
have fulfilled consultancy and product development in the area of
passport inspection, cryptography, ePassport/smart card protocols
testing and more. They have a wealth of knowledge and experience in PKI
and development of applications using secure hardware and cryptography.

## Securing WebGoat using ModSecurity

Submitted by Stephen Evans

**Background:** ModSecurity is an open source web application firewall
that can work either embedded in an Apache web server or as a reverse
proxy. The new features in version 2.0 and version 2.5 (released in
February 2008) allow for a highly configurable capability that can
address vulnerabilities (e.g. discovered during black-box penetration
testing) on a per-application basis. ModSecurity provides for free a
broad set of generic Core Rulesets
(http://www.modsecurity.org/projects/rules/) that cover areas such as
protocol compliance, malicious client software detection, XML
protection, error detection, and generic attack detection ("Detect
application level attacks such as described in the OWASP top 10").
However, the Core Set rule documentation (see README in
modsecurity-core-rules_2.5-1.6.0.tar.gz) cautions that since attackers
may examine the freely-available core rules to get around them, some
core rules should be viewed more as a "nuisance reduction" mechanism
instead of a security mechanism.

The lessons in WebGoat 5.1 detail over 30 different types of attacks on
the WebGoat application (see the WebGoat v5 User & Install Guide).

**Purpose:** The purpose of my project is to create custom Modsecurity
rulesets that, in addition to the Core Set, will protect WebGoat 5.1
from as many of its vulnerabilities as possible (the goal is 90%)
without changing one line of source code. To ensure that it will be a
complete 'no touch' on WebGoat and its environment, ModSecurity will be
configured on Apache server as a remote proxy server.

For those vulnerabilities that cannot be prevented (partially or not at
all), I will document my efforts in attempting to protect them. Business
logic vulnerabilities will be particularly challenging to solve.

**The opportunity, challenges, issues or need your proposal addresses:**

  -   - Provides application-level protection for those web applications
        that cannot be touched
      - New custom rulesets can be added as new attack types are
        discovered
      - This solution is programming language and platform agnostic
      - With outside help from consultants, this solution can be used by
        companies that have zero knowledge of software security
      - A possible unintended side-effect: introduce software security
        awareness into an organization, which may lead to software
        security development lifecycle practices for future projects
      - An attempt will be made to address business logic
        vulnerabilities which will be a challenge

**Schedule, tasks and deliverables:**

April 01 to April 06: Set up and test the development environment. The
initial Reverse Proxy server OS will be Kubuntu 7.10.

April 07 to May 04: Identify WebGoat vulnerabilities and exploitation
methods. Publish to WIKI for review, feedback, and modification.

May 5 to May 25: Develop rulesets for 50% of the vulnerabilities,
starting with the low-hanging fruit. Deliver user documentation. Publish
progress to WIKI as each vulnerability is addressed. \[Milestone 1\]

May 26 to June 15: Develop rulesets for the 2nd 50% of the
vulnerabilities. Publish progress to WIKI as each vulnerability is
addressed.

June 16 to June 22: Test final rulesets and Modsecurity Reverse Proxy on
2 other Linux distros (Fedora Core and ???).

June 23 to June 29: Produce final rulesets and documentation.

June 30 to July 13: Peer review, feedback, modification, deliver final
product \[Project completion\]

**Future development:**

  -   - Demonstrate the same capability for a vulnerable, well-known
        ASP.NET application such as Hacme Bank
      - Add custom rulesets that address attack types not represented in
        WebGoat but identified in the OWASP 2007 Top 10 (e.g. CSRF) or
        any newly-discovered attack types

**Long term vision:**

  -   - Instead of only protection mechanisms, add alerting and forensic
        capabilities (this functionality is presently available in
        ModSecurity) which would move closer to the goal of an
        application being self-defending

**Proposed project reviewer:** Dinis Cruz Dinis seems to have a special
passion for Web Application Firewalls.

**Stephen’s background and experience:**

  -   - BSc in Computer Science and Mathematics, McGill University,
        Montreal, Quebec
      - 20+ years software developer
      - 4 years “officially” intensive information security professional
        since getting CISSP and joining a Big Security Vendor
      - Well-rounded infosec experience in areas such as CERT, security
        product deployment and training, vulnerability threat
        management, incident handling/response, antivirus scan engine
        customization.
      - Started up Big Security Vendor’s Secure Application Services (as
        sole consultant) for APAC region
      - Technical lead for a large APAC government project, building a
        software package assessment framework and workflow application
        based on an excellent, mature proprietary pentesting methodology
      - Numerous pentests/security assessments/risk assessments, mostly
        in the government space
      - Several SDLC projects, including a current one with an APAC
        government agency as the software security consultant throughout
        the entire SDLC for a field service type of mobile application
        using WinCE 5 & C\#

**Participation and leadership in open communities:** A founding member
of Singapore chapter of IASA (International Association of Architects);
gave “Security throughout the SDLC” presentation at IASA regional
conference in Kuala Lumpur, Malaysia, in 2006.

**Any other reasons why you and your project should be selected:**

  -   - This project is a huge “big-bang-for-the-buck” contribution from
        OWASP to the software development community
      - The results of this project, along with ModSecurity, can be a
        big aid to organizations that need a (free) Web Application
        Firewall to meet PCI-DSS requirements
      - I am very passionate about:
          - Making about 75% of the “security researchers” look for a
            new line of work
          - Altering the focus of software security from “audit mode”
            towards software security during the SDLC
          - Software security

## OWASP Book Cover & Sleeve Design

`DINIS Comment: I propose that for this first phase we only handle the OWASP Book Cover (and leave the Sleeve Design for later stage) `

**Book Cover Design Series Brief:**

LXstudios has had the pleasure of speaking with Dinis Cruz about OWASP
(book) publications. We discussed the current scenario and the potential
for stronger OWASP brand identity across publication lines, and the
packaging of these publications into book sleeves. We discussed the
importance of this effort as OWASP is growing exponentially. OWASP
produces many publications a year. Currently, the publications have
cover designs and good content. The cover designs are all different.
There is a lot of potential for these covers to look consistent from a
brand perspective, and adding end-user value to the purchase of a book.
There is also functional reason for the redesign, as Dinis would like to
identify the different release versions of a book and it’s quality of
content. As OWASP grows and produces more literature, a scalable cover
design strategy must be employed so that the publications stay
organized, easy to implement, easy to understand, increase brand
identity, and sell.

**Book Sleeve Design Brief:**

Dinis and I also discussed the delivery of these books in
professionally-produced book sleeves. This book sleeve would house
between 6-8 OWASP publications and create an identity for a suite of
books on a reader’s book shelf. As a reader’s collection of OWASP
literature grows, the organization of these books comes into play. The
other valuable reason to create a book sleeve is the individual and
corporate membership. When these members buy into OWASP, the
professional delivery of the publications is paramount. Bottom line --
in addition to functional book covers and securing shelf space -- OWASP
has an increasing and critical need to look as good or better than other
industry publications in circulation.

**Deliverables:**

  - Goal A Book Cover Series: Develop a scalable book cover series
    strategy for the OWASP publications that communicates content in a
    clear, clever and provoking manner. The strategy is also to simplify
    the design process so subsequent publications can work off a
    template design – thus saving time and money (and increasing brand
    image).
  - Goal B Book Sleeve: Develop a house to deliver the book series. The
    initial thoughts are around a chip-board produced book sleeve that
    works off the design cover strategy and can hold up to 10
    publications. The actual size needs to be determined.

**Why should OWASP invest in this project?**

Many reasons. The two most important:

1.  Make the publication production process simpler and over time more
    cost effective for the OWASP team. As the organization is growing,
    members need to spend time doing what they do best. Recreating
    artwork and cover designs on the fly is not the best use of time and
    money. The current approach is also diluting/damaging the OWASP
    brand.
2.  Increase awareness of OWASP brand identity in the industry. As the
    OWASP organization continues to grow in size and value (monetary and
    value to the industry), there is an increasing and critical need to
    look as good or better than competitor and affiliate publications in
    circulation. A consistent approach to publications will increase
    brand recognition and create brand stability - increasing product
    and organization perceived, intrinsic, and actual value.

**Proposed Design Budget**

  - '''Book Cover Series Design:$ 5,600 '''Design Development/Layout
    OWASP Brand Identity Book Cover Series; Layout 3 book covers in
    series identifying levels of quality “Release”, “Beta”, Alpha; 4th
    in series is “Bundle” - let’s discuss if this bundle would need it’s
    own identity or if it could be packaged in book sleeve; Image
    Research; Concept yields 3-4 ideas for presentation; Revisions;
    Production/Mechanicals - deliver high resolution book cover PDF
    files for OWASP implementation (through LuLu); Fee includes first 6
    books; Project Management
      - Additional book cover high resolution PDF files, estimated: $
        325 (text and/or color revisions only)
      - Materials, proofs, storage media: $ 150

'''Book Sleeve/Box Design: $ 3,360 '''

  - Book cover concept application to Box Sleeve; Box sleeve design
    construction; Prepare Mechanical files for box production; prepare
    graphic files for printed graphic wrap; Proof reviews; Project
    Management:
      - Materials, proofs, storage media: $ 10

'''LXstudios inc '''

[LXstudios](http://www.lxstudios.com) inc provides competitive branding,
corporate identity, collateral and web design solutions for technology,
financial services, medical, and management consulting clients.
Capabilities include, from concept through to production:

  - Branding, Restructuring, Key Messaging
  - Corporate Identity/Logos
  - Collateral (direct mail, brochures, event materials, newsletters)
  - Advertising
  - Tradeshow Design and Support
  - Web Design & Implementation/Development
  - Original Illustration & Photography
  - Electronic Presentation Media
  - Media Relations with strategic PR affiliates

## OWASP Individual & Corporate Member Packs, Conference Attendee Packs Brief

As OWASP increases to have more presence in the community, more and more
people are realizing the benefits of the organization and are interested
in becoming members. As OWASP reaches out to the community and continues
to communicate it’s messages via conferences, more and more people are
attending conferences. All of this visibility is driving a growing need
for a stronger OWASP brand identity across individual member, corporate
member and conference attendee audiences. The current scenario is a good
start with premiums including pens, tshirts, sweatshirts and OWASP
publications. How these items are packaged, delivered and managed will
support our umbrella campaign strategy to:

  - stay organized;
  - easily implement (stay cost effective and produce easily) packs;
  - increase OWASP brand identity;
  - increase OWASP perceived, intrinsic, and actual value;
  - increase memberships and conference attendance.

**Individual/Member Packs, Detail & Deliverable:**

The concept around the Individual and Member Pack is to deliver and
house 6-7 OWASP book publications, Member card, Tshirt(s), Pens, USB,
DVD and Welcome Letter/Card. We are hypothesizing all member kits are
delivered in a Tote Bag, big enough to house a large book sleeve (10
inch x 10 inch x 10 inch) – although specifications are still rough and
details need to be worked out. The other option is to shrink wrap book
sleeves and other content (gracefully) and ship out to individual and
corporate addresses not in totes.

**Conference Attendee Packs, Detail & Deliverable:**

The concept around the Attendee Pack is to provide fewer OWASP book
publications (4-6), Tshirt, & Pen. We are hypothesizing all attendee
kits are delivered in a Tote Bag. Specifications are still rough and
details need to be worked out. We are researching bags with a look and
feel that are as forward-thinking as OWASP.

**Why should OWASP invest in this project?**

1.  Enhance the value of individuals and corporations becoming OWASP
    members. Make the publication production process simpler and over
    time more cost effective for the OWASP team. As the organization is
    growing, members need to spend time doing what they do best.
    Procuring and creating materials on the fly is not the best use of
    time and money. The current approach could be stronger at supporting
    OWASP brand.
2.  Increase awareness of OWASP brand identity in the industry. As the
    OWASP organization continues to grow in size and value (monetary and
    value to the industry), there is an increasing and critical need to
    look as good or better than competitor and affiliates. A consistent
    and professionally-produced approach to member and attendee
    communications will increase brand recognition and create brand
    stability - increasing product and organization perceived,
    intrinsic, and actual value.

**Proposed Design Budget**

  - **Tote Bag** - Procurement: Fees determined after quantity is
    established

<!-- end list -->

  - '''Member Cards: $ 840 ''' - Design Development/Layout OWASP Brand
    Identity to Member Cards; Color code; Revisions; Test sheets to
    OWASP; Production/Mechanicals - Project Management:
      - Materials, proofs, storage media: $ 35

<!-- end list -->

  - '''Welcome Letter/Diecut Circle Cards: $ 840 ''' - Design
    Development/Layout OWASP Brand Identity to Welcome Letter/Card;
    Production/Mechanicals - Project Management:
      - Materials, proofs, storage media: $ 35

'''LXstudios inc '''

[LXstudios](http://www.lxstudios.com) inc provides competitive branding,
corporate identity, collateral and web design solutions for technology,
financial services, medical, and management consulting clients.
Capabilities include, from concept through to production:

  - Branding, Restructuring, Key Messaging
  - Corporate Identity/Logos
  - Collateral (direct mail, brochures, event materials, newsletters)
  - Advertising
  - Tradeshow Design and Support
  - Web Design & Implementation/Development
  - Original Illustration & Photography
  - Electronic Presentation Media
  - Media Relations with strategic PR affiliates