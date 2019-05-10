**This page contains project Applications to the [OWASP Summer Of Code
2008](OWASP_Summer_of_Code_2008 "wikilink")**

# A few notes

  - **If you want to apply for a SoC 2008 sponsorship you HAVE TO USE
    THIS PAGE for your application.**
      - See [How To
        Participate](OWASP_Summer_of_Code_2008#How_To_Participate_\(To_Developers\) "wikilink")
        for what to do once you completed your Application.
      - Please remember that projects will be selected and funded based
        on how well they meet the [Selection
        Criteria](OWASP_Summer_of_Code_2008#Jury_and_Selection_Criteria "wikilink").
      - Please see [AoC
        06](OWASP_Autumn_of_Code_2006_-_Applications "wikilink") and
        [SpoC 07](OWASP_Spring_Of_Code_2007_Applications "wikilink") for
        examples of Applications.
  - '''You can propose your project in any form you wish, but the best
    proposals will be well thought out, clear and concise, and
    reflective of your passion for the topic. We strongly suggest that
    you include [this information in your
    proposal](OWASP_Summer_of_Code_2008_Applications_-_Proposal_Type "wikilink").

'''

# Applications - {Fill in below}

## The Application Security Desk Reference - ASDR

  - Leonardo Cavallari Militelli
  - Proposal: Make [OWASP ASDR Project](OWASP_ASDR_Project "wikilink") a
    release quality document.

The ASDR is a reference volume that contains basic information about all
the foundational topics in application security. It intends to replace
and refresh [Honeycomb Project](OWASP_Honeycomb_Project "wikilink") with
a new structure for articles and relationship between categories, thus
making it a release quality doc.

This idea raised while finishing the [Attack Reference
Guide](Attack "wikilink") for [OWASP Spring Of Code
2007](OWASP_Spring_Of_Code_2007 "wikilink"), where it was identified
that OWASP reference articles needed some special attention. Jeff
Williams is totally supporting this project.

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

  - Road Map: A complete project roadmap can be found on
    **[OWASP_ASDR_Workplan](OWASP_ASDR_Workplan "wikilink")**.
    Basically, the following activities should be performed, some of
    them already started:
      - Define articles templates for each reference type
      - Define subcategories for articles classification
      - Compile first DRAFT version of ASDR Book
      - Articles development & Call for Volunteers
      - Articles revision
      - First version of OWASP ASDR book

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

## Code Crawler

  - Alessio Marziali (aka nTze)

**Description**
This tool is aimed at assisting code review practitioners. It is a
static code review tool which searches for key topics within .NET and
J2EE/JAVA code. The aim of the tool is to accompany the OWASP Code
review Guide and to implement a total code review solution for
"everyone"; Where "everyone" means "more" companies performing secure
software activities.

Key areas of improvement:
**Reporting**
\- PDF - Microsoft Office Compatible Word Document - HTML

**Scanning**
\- Multiple File scanned at the same time
\-- Open Microsoft Visual Studio's Solutions
**Bigger Database**
Which will provide more information about the threats such vulnerability
type (XSS,SQL Injection, Remote File Inclusion etc).
**Security Software Life Cycle**
A feature that will let you save the threats for each project/document,
so the reviewer can check how the development is going from a “security
prospective” during the entire software lifecycle.
Improvement of the code scan system.

## The Owasp Orizon Project

  - Paolo Perego (aka thesp0nge),
  - The Owasp Orizon Project,

**Introduction**

The [Owasp Orizon
Project](http://www.owasp.org/index.php/Category:OWASP_Orizon_Project)
born in 2006 in order to provide a framework to all Owasp projects
developing code review services.

The project is in a quite stable stage and it is usable for Java static
code review and some dynamic tests against XSS. Owasp Orizon includes
also APIs for code crawling, usable for code crawling tools.

[Milk](http://milk.sf.net) project is a java code review tool I'm
writing using Orizon as background engine. Its goal is to show engine
capabilities.

**Objectives and deliverables**

  - plugin architecture for static code review library: this planned
    feature will be announced (hopefully, if my CFP will be accepted) to
    next Owasp European App conf.
  - starting C\# support
  - upgrade from Alpha quality project to Beta quality project in accord
    to [Owasp Project Assessment
    criteria](http://www.owasp.org/index.php/Category:OWASP_Project_Assessment)

**Why I should be sponsored for the project**

Owasp Orizon is the first Owasp project I'm involved in. I'm also
contributor of Owasp Italian chapter managed by Matteo Meucci and I'm
talking at various speeches about application security and safe coding
best practices.

I'm a security consultant working in ethical hacking and we're
approaching code review and safe topics right now. I'm a developer too
so I understand also the "dark side" of the problem developing code with
security in mind.

I work using the "release early release often" paradigm so to be
concrete and let other people having something usable to work with.

In the last year Owasp Orizon evolved a lot with a good static code
review engine and a lot of code was written to give Owasp guys the best
framework as possible to be used for writing code review tools. I hope
to pursuit my goals again with SoC 2008.

## Skavenger

  - Matthias Rohr

**Introduction**

Skavenger is a web application security assessment toolkit which arised
from many years of professional experience in the web application
assessment field and is the result of nearly one your of work.

It passively analyzes traffic logged by various MITM proxies (such as
WebScarab and Burp) as well as other sources (like Firefox's
LiveHTTPHeader plugin) and helps to identify various kinds of possible
vulnerabilities (such as XSS, CRLF injection, an insecure session
management and several kinds of information disclosure). Skavenger's
modular design allows the integration of custom scanning modules without
any knowledge about the tool at all.

Skavenger is completely written in Perl and can be downloaded from:
<https://sourceforge.net/projects/skavenger/>

**Objectives and deliverables**

Here are some ideas:

  - A GUI to monitor and analyze scanning results
  - More sophisticated scanner modules (e.g. for better backend
    identification and more platform specific tests)
  - Database integration
  - API's to integrate modules in other languages (such as Python or
    Java).
  - Better source integration with custom Firefox, Burp or (of course)
    WebScarab plugins

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

## OWASP Backend Security Project

  - Full name: Carlo Pelliccioni
  - Project: OWASP Backend Security Project
  - Project description:

<!-- end list -->

  -
    OWASP Backend Security Project is a new project created to improve
    and to collect the existant information about the backend security.
    The project is composed by three sections (security development,
    security hardening and security testing).
    The aim is to define the guidelines for the companies and IT
    professionals working in the security field into processes
    development and back-end components management/testing in the
    enterprise architecture.

<!-- end list -->

  - Objectives:

**`Overview`**
`Create a section with an introduction about the project (high-level description) explaining the main`
`goals.`

**`Development`**
`Include the writings already existant in OWASP wiki concerning PHP,`
`JAVA and ASP.NET and extend the projects' sections with new contents.`

**`Hardening`**
`Create new guidelines about the dbms hardening`

**`Testing`**
`Include the writings already existant in OWASP wiki about security testing.`
`Create new articles about security testing.`

## OWASP Classic ASP Security Project

  - Juan Carlos Calderon

**Executive Summary**
I am interested in making P018 - OWASP Classic ASP Security Project
happen, Classic ASP 2.0 and 3.0 applications are still largely used as
this technology is more than 10 years old and was largely used. there
are thousands of sites on the wild that need guidance on the security
arena. This is where OWASP can come up and provide help for “making the
Web a better place” and continue spreading the word on security. I have
always be a passionate of the technology (regardless of its
inconveniences such as being old and DLL-hell prone) and I am really
exited on the idea of sharing my knowledge of this area to the world and
what best that though OWASP.

**Objectives and Deliverables**
Create a secure framework for Classic ASP application by complementing
existing OWASP projects with documentation for this particular
technology and the creation of security libraries. More specifically:

  - Creation of a Common Object Repository for ASP applications based on
    OWASP ESAPI Project including objects and/or references to libraries
    for security applications all this aligned with OWASP Top10 and
    OWASP Guide .
  - Create Documentation aligned to OWASP Code Review Project Checklist
    providing additional technology-specific checks.
  - Addition of expression for Code Review Tool to support Classic ASP
    applications.
  - Implementation of Version 1 of Stinger for ASP either by using an
    installable COM library or ISAPI.
  - This same module will compliment the OWASP Validation Documentation
    Project.

**Why should I be sponsored for the project?**
I have 10 years of experience on Web technologies. During 8 years I have
performed and leaded hundreds of Security Source Code Reviews and Black
box testing on Web Applications. On my current job I lead 30 people in
diverse locations all of them working on the Application Security arena,
so I am accustomed to execute and deliver.

Also I’ve had close contact with OWASP since 2005
[1](https://lists.owasp.org/pipermail/owasp-spanish/2005-March/000069.html)
by making possible the translation of OWASP Top 10 2004
[2](http://www.owasp.org/index.php/Top_10_2004) and OWASP Testing Guide
V1.17 [3](http://www.owasp.org/docroot/owasp/misc/testing_spanish.pdf)
to Spanish.

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

## The Ruby on Rails Security Guide v2

Heiko Webers

The last security guide for Rails
[7](http://www.owasp.org/index.php/Category:OWASP_Web_Application_Security_Put_Into_Practice)
was a great success, with a lot of more secure web applications and
continued awareness in the community of security issues. The Ruby on
Rails Security Project [8](http://www.rorsecurity.info/) is the one and
only source of information about Rails security topics, and I keep the
community up-to-date with blog posts and conference talks in Europe. The
Guide and the Project has been mentioned in several Rails books and
web-sites.

Version 1 of the Ruby on Rails Security Guide was sponsored by the SpoC
07, set the standard for OWASP programming language specific guides in
terms of the topic outline and has been published as a book
[9](http://www.lulu.com/content/1412042). Nevertheless I'm convinced
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
  - Secure instant messaging application development, including patents

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

## GTK+ GUI for w3af project

*Facundo Batista*

**Your educational and professional background**

I'm Electronic Engineer with a Master in Engineer Innovation in Bologna
University, Italy. I live in Buenos Aires, Argentina, and love reading
books, playing tennis, and programming Python.

I worked in a mobile company for six years, in the Network Management
department, then I was Chief Developer of a Mobile Content Provider, and
now I'm Solution Architect in Multimedia & Systems Integration in
Ericsson. Also I was professor in several universities, high schools and
other institutions.

**Application security experience and accomplishments**

None, more than working in w3af. However, my proposal here is not
related to the security part of the product, but to its graphical
interface and usability.

**Participation and leadership in open communities**

I'm very involved in the free software and open source community. I'm a
Python Core Developer and member of the Python Software Foundation by
merit. I have a long history of talks given in several international
(PyCon, EuroPython) and national (a lot\!) conferences. I also teach
Python in educational institutions, enterprises and as a private
instructor. I founded Python Argentina, the national users groups, and
I'm a very active member of it.

I also lead other open source projects (SMPPy, SiGeFi, etc.) and
particpate in others (Docutils, w3af itself, etc.).

**The opportunity, challenges, issues or need your proposal addresses**

My main objective is to minimize the effort and learning curve of using
w3af, providing a very usable graphical interface.

Note that as the interface is cross platform, being usable also in the
win32 environment, it will help to popularize the w3af project.

This will allow users without information security knowledge to verify
that their web applications are correctly programmed and configured.

**Specific activities and who will carry out these activities**

I will carry the following activities, detailed later in smaller steps:

\- Design and code new windows and interfaces to increase the
functionality of the project.

\- Tuning of the process workflow, allowing a more intuitive way of
working.

\- Visual polishing for a more pleasant and intuitive tool.

\- Usability tests and improvements.

**Specific deliverables and a rough project schedule so we can track
progress**

*New features implemented in the pyGTK user interface:*

\- Local proxy to trap and modify requests and responses sent from a
browser.

\- Manually send a request and analyze the response.

\- Manually create a fuzzed requests based on tokens, so user can
construct easily differents HTTP request with a regex-like semantics.

\- Wizard to perform a vulnerability assessment.

\- Graphical display of site map and vulnerabilities.

\- Reload a plugin after its edited from within the pyGTK user
interface.

\- Embebed tool to encode/decode URL/Base64 and to hash sha1/md5.

\- HTTP response side by side content compare.

*Usability improvements in the pyGTK user interface:*

\- Meetings with a usability expert that the w3af team leader has
already contacted and worked with.

\- Kill all pending bugs and make a stable release.

*Documentation:*

\- Users guide for the pyGTK user interface.

\- Help system for the GUI itself

**Long-term vision for the project**

To provide the web application security community with a stable and
fully featured framework to perform all the tasks included in a
penetration test from within the project.

**Any other reasons why you and your project should be selected**

w3af is one of the most active web application security projects; the
community that supports it is growing and we need the support of already
established organizations like OWASP to keep working at the rate that we
want to.

## P025 OWASP Positive Security Project

by Eduardo Vianna de Camargo Neves

**Executive Summary**

A common approach on most companies is to increase the protection of
their assets after the occurrence of a considerable impact. However some
companies learned that a positive approach on IT Security is most
effective and can reduce the financial costs on responses to security
incidents. Benchmarking the application security practices on the
corporate world will allow us to understand what steps are required to
keep the IT environment protected, using this knowledge to support the
development of a campaign to spread a positive security posture in the
market. The liaison with companies that maintain good security practices
will help to start this initiative from a higher degree and involve
several actors on the security stage for the same direction to a market
were security is understood as a business value.

**Approach**

Assessing results from the Corporate Application Security Rating Guide
Project and other public sources will be used to support the development
of the Positive Security Project with facts from a real analysis.

**Benefits**

The whole community will be benefited from this initiatives. With the
adequate support from OWASP to maintain the project active and liaise
with big players on the market, we can expect the following:

• The community will receive a guide to practice the "Positive Approach"
that will allow them to compare their own security practices within the
market. As this will be a public document, suppliers and buyers
worldwide will share the same information allowing them to adequate the
expectations on the usage of security services and tools.

• Compliance and alignment with Positive Approach can be used as a
marketing tool by the companies, allowing them to sell security as a
business value and avoiding the old-fashion and inadequate FUD approach.

• The knowledge and relationship developed during the development will
support the Positive Security Project with real information, increasing
the credibility of the initiative for the market.

• The Security Rating Guide and the Positive Security Project can be
walk in parallel, merging their information to support a concise and
continuous marketing campaign to encourage a positive approach on the
market.

• As an open community free from commercial pressures, OWASP can use
both projects to support the evaluation of security products for the
market, allowing the organization to receive profits from these services
and support current and future projects.

**Summarized Work Breakdown Structure (WBS)**

All the activities will be leaded by Eduardo V. C. Neves, which will be
responsible as a single point of contact with the sponsors and to manage
a team of compromised volunteers from OWASP community and participants
from security communities and associations (i.e. ISSA, SANS and ISC2).

The activities will be carried on WBS summarized bellow. Dates presented
should be considered as deadlines for the activities:

• Criteria establishment and definition of the marketing material and
support documents (April 11)

• Approval of marketing templates for Positive Security Project (April
25) (1)

• Development of the Positive Security Project material (i.e. blog and
marketing sheets) (May 30)

• Liaison with the OWASP Members and analyzed companies to present the
project and negotiate their participation as supporters, sponsors or
contributors. (June 27)

• Update on Positive Security approach deliverables(July 4)

• Presentation of the Positive Security Project approach on the market
(July 31) (2)

• Conference calls with team members to evaluate the results of the
initiatives in all countries and produce project´s documents (i.e.
lessons learned, update on marketing material and evaluation of
alternative approaches for the future steps). (August 15)

• Prepare project documentation and present to the OWASP community on
the web site (August 31)

*(1) Support from OWASP Foundation and community are required to
evaluate adequate marketing templates and translate original documents
for their own languages*

*(2) Support from OWASP community is required to spread the word on all
countries were OWASP members are located.* '''''

**Project Control**

The project will be managed following PRINCE2 Process Model and all
control documents published for the OWASP community. The following
mandatory project control documents are planned:

• Project Initiation Document: To document project´s background,
definition, objectives, approach, etc.

• Communication Plan: To assure that OWASP Community are being
continuous communicated about project status and deliverables
achievement.

• Highlight Report: To provide the OWASP Community with a summary of the
project status, progress and potential problems or areas where help may
be required.

• End Project Report: To present project achievements. Should be
considered the final project report.

More documents may be included during project development to support the
control and assure a high quality level (i.e. issue log, project
approach).

**Long Range Plan**

The project should be used as a tool to support efforts to encourage and
make the positive approach a reality on the IT Security field. These
initiatives shall be supported by OWASP as long term plans and grow to a
continuous world-wide campaign in this direction that must achieve big
players on the market and be recognized by the community as a tool that
must be used to evaluate security enabled companies and products.

**Why me?**

Can be me, you or anyone that carries this project in a professional
fashion and assure that all deliverables are being achieved. The most
important parts is to make it happen, talk and get the support from
reputable associations and large companies (OWASP Members are a good
start) and lead it as a long range responsibility.

I am running to win this project because I believe in all of this. I see
both as very valuable initiatives that can help companies to make more
business; people to get more jobs and the whole community to win in a
scenario where our contributions on the security market are recognized
as business tools.

**About me**

Information Security professional and enthusiastic with 15 years
dedicated to achieve expressive results in the areas of IT, Information
Security, Compliance and Project Management. A CISSP in good stand and
Officer at the ISSA Brazilian Chapter, my professional career gave me
extensive knowledge in several fields of Information Security with
accumulated experience at consulting firms, as CSO at a world player
company on consumer goods market and now as an entrepreneur at Latin
American market.

*Application security experience and accomplishments*

My work experience is on Security Management, Risk Assessment, Business
Continuity and Disaster Recovery, Security Awareness and other
managed-related fields on our industry. I don’t have hands-on experience
on application security and this is the main reason why I am running to
be qualified on the project described bellow, where I believe that my
skills can be used to achieve an excellent result for the community.

*Participation and leadership in open communities*

• Member of OWASP Brazil where I made some small contributions in a
recent past.

• Member of ABNT/CB-21/SC02 committee, Brazilian ISO representative for
27001 and 17799 standards

• Officer of ISSA Brazil Chapter where I am responsible for the South
Region and as the editor of Antebellum, the ISSA Brazil Journal

• Founder and member of GISI-PR, an open community focused on discuss
and promote Information Security initiatives within Paraná State, Brazil

## P017 - OWASP AppSensor - Detect and Respond to Attacks from Within the Application

**Name**

Michael Coates

**Project**

P017 - OWASP AppSensor - Detect and Respond to Attacks from Within the
Application

'''The opportunity, challenges, issues or need your proposal addresses,
'''

As critical applications continue to become more accessible and
inter-connected, it is paramount that the information be protected. We
must also realize that our defenses may not be perfect. Given enough
time, attackers can identify security flaws in the design or
implementation of an application. In addition to implementing layers of
defense within an application, it is critical that we identify malicious
individuals before they are able to identify any gaps in our defenses.
The best place to identify malicious activity against the application is
within the application itself. Network based intrusion detection systems
are not appropriate to handle the custom and intricate workings of an
enterprise application and are ill-suited to detect attacks focusing on
application logic such as authentication, access control, etc. The
application itself is the best place to identify and respond to
malicious activity. This project will create the framework which can be
used to build a robust system of attack detection, analysis, and
response within an enterprise application

'''Objectives or ways in which you will meet the goal(s), '''

I plan to use a methodical approach throughout the creation of this
resource. I will reference my own professional experience, OWASP
resources, ESAPI, and academic materials to identify a robust set of
potential attacks and identification methods. Thresholds will be
recommended for each of the detected attacks. Each recommended threshold
value and response recommendation will be accompanied with additional
information to describe the purpose of the threshold and recommendation.
This additional information will allow the reader to determine if the
threshold is appropriate for their implementation.

'''Specific activities and who will carry out these activities, '''

I will complete the following activities: 1. Identify and define attack
patterns against applications 2. Document points of detection within the
application for the attack patterns & identify key information to log 3.
Create thresholds for generating security alerts 4. Define recommended
response actions for the security alerts

'''Specific deliverables and a rough project schedule so we can track
progress, '''

April 2, 2008 - Project Begins

April 2, 2008-April 12, 2008 - High level planning & design

April 12, 2008-May 1, 2008 - Identify and define attack patterns against
applications

May 1, 2008-June 1, 2008 - Document points of detection within the
application for the attack patterns & identify key information to log

June 1, 2008-June 13, 2008 - Peer Review & Revisions

June 15, 2008 - Status Report

June 16, 2008-Aug 15, 2008 - Create thresholds for generating security
alerts

June 16, 2008-Aug 15, 2008 - Define recommended response actions for the
security alerts

Aug 16, 2008-Aug 30, 2008 - Peer Review & Revisions

Aug 31, 2008 - Project Complete

'''Long-term vision for the project, '''

1\. I’d like to include a tiered type approach of thresholds and
responses. This is would be similar to the approach used by FISMA of
defining different controls for High, Medium, and Low systems.

2\. Building on item \#1, I want to eventually include a system which
lets the user provide information about their system. This information
could include rating or prioritizing different security concerns. a
customized set of monitoring points, thresholds and response actions can
be recommended for the application based on the provided data.

**About Me**

**Education & Professional Background**

Masters of Science in Computer, Information and Network Security –
DePaul University (Expected Graduation 2009) Bachelor of Science in
Computer Science – University of Illinois Extensive experience in
conducting black and white box security reviews of complex applications
and networks for major financial organizations and international
telecoms. I also have experience working as the primary investigator of
attacks against a multi-national organization with IDS sensors in
networks throughout the world. In addition, I have experience working
with several regulatory controls and security standards (FISMA, NIST,
GLBA etc). My experience as an ethical hacker and incident responder
puts me in an excellent position to tackle this project.

**Application security experience and accomplishments**

I am a Senior Computer Security Engineer with Aspect Security where I
perform security code reviews and application security testing against a
variety of platforms. Prior to working with Aspect Security, I was
heavily involved in the discovery and exploitation of application
vulnerabilities during black box ethical hacking assessments for
numerous clients.

**Participation and leadership in open communities**

I am a member of OWASP and attend Chicago OWASP chapter meetings. I also
attend ChiSec, an informal meet-up of security professionals in the
Chicago area. In addition, I interact with the community through my
security blog. <http://michaelcoates.wordpress.com>.

'''Any other reasons why you and your project should be selected. '''

I created a similar framework while working within a Security Operation
Center. I created attack scenarios, identified relevant IDS events,
defined thresholds and appropriate response action for the Security
analysts.

**Requested Reviewer - Eric Sheridan, Application Security Consultant at
Aspect Security, Inc.**

Eric Sheridan is an Application Security Consultant at Aspect Security,
a consulting services company specializing in application security. At
Aspect Security, Eric specializes in execution of security verification
assessments and the establishment of security activities throughout the
development lifecycle. In addition, Eric is an instructor in Aspect’s
portfolio of Application Security Courses. Eric is also an active
participant in OWASP whose contributions include work with projects such
as WebGoat, Stinger, CSRFGuard, CSRFTester, and the SASAP project from
OWASP SPoC 2007. Eric was also a featured speaker at the 2007 OWASP/WASC
San Jose conference.

Contact Information: eric dot sheridan 'at' owasp dot org

## OWASP Interceptor Project - 2008 Update

by Justin Derry

<http://www.owasp.org/index.php/Category:OWASP_Interceptor_Project>

**Executive Summary**

The OWASP Interceptor project was originally written by myself and
donated to the OWASP project. Since it has been online numerous people
have downloaded the tools and used the code/toolkit. Currently the
industry has very limited “XML” or SOAP client testing tools that are
designed specifically to perform XML interception and manipulation. The
Objective of the Interceptor project is to provide a strong tool for
performing XML penetration tests against Web Service (or XML/SOAP)
endpoints. The tool should not replace other proxy interception tools
such as Charles, Web Scarab and so on, but be purely focused on handling
and reading XML structures from clients.

The Interceptor tool includes a “swiss-army” knife of features that will
help with decoding/hash generation and interpretation of XML code. The
key objective is to make a tool that can assist with the collection,
inspection and attack replay of XML requests against service endpoints.
This year it’s time for an update. The tool doesn’t run on Vista and
needs a number of back-end features addressed as well as some help files
etc. (Help to get the tool out of BETA status).

**Objectives this year**

This year I see the following objectives in the application code base. •
Get the Interface to run on all Window Platforms (.NET) Win2000, XP and
Vista;

• Update the TCP handle libraries to be faster

• Update the XML Parser engine to support the latest structures

• Provide a “default” attack database of known XML attack methods (this
is a big one)

• Write a number of help files on how to use the tool

• Update the toolkit BASE64 Decoder, XML Generators etc with further
tools

• Write a better “reporting” engine to show the result of simulated
attack responses

• Better HTTP support for Manipulation, Authentication and Header
Injection etc

• Better support for interception and handling AJAX XML requests

These are the core features I would like to introduce, with also further
to probably come as a part of the project.

**Why should I be sponsored for the project?**

The current development cycle stopped due to limited time and the need
to purchase the IDE tools to develop the interface in .NET. As a Summer
of Code 2008 sponsored project we can get the IDE interface tools to
implement “Vista” features that will see the tool run on all .NET
platforms (Win2000, XP and Vista). Recent changes in my job will allow
me to spend more time on developing the toolkit.

Over a number of years I have been involved with OWASP, whilst most
recently getting involved with running the OWASP Australia Security
Conference for 2008, as well as the Brisbane Chapter. I am also working
in the Asia Pacific RIM to further increase the awareness of OWASP and
Application Security. My Conference duties for the year have finished up
(till planning starts again in a couple of months) so my time can be
invested in updating the toolkit.

I believe during the previous years, i have shown OWASP that i am
willing and able to produce a quality outcome and i am prepared to put
the effort into OWASP to acheive the goals set out for this project.

Some of the Sponsorship money for the project would go to purchasing a
specific toolkit for the UI. (The UI is important simply because we want
the application to be user friendly). Xceed Components provide a Smart
UI as well as some of the decoding and compression features the tool
needs. This would require us to approach them upfront for a “free”
licence or use some of the Sponsorship money to buy the toolkit. But we
can tackle that problem when we come to it.

## SQL Injector Benchmarking Project (SQLiBENCH)

by Mesut Timur & Bedirhan Urgun

**Prelude**

There're a lot of and great open source tools (takeover/dumpers/hybrid)
for taking advantage of an sql injection vulnerability both used by web
application security specialists and attackers. Techniques used,
databases supported, algorithms employed and abilities implemented by
these "sql injectors" greatly varies. Standardization is one of the
abstract goals of OWASP and we think it's important to standardize
general vulnerability techniques exists in web applications and one of
the biggest one is sql manipulation. In our effort, we aim to produce a
standardization of techniques used in exploiting sql injection by
automatic tools.

**Proposal**

The goal of the project is to create a detailed set of benchmarking
criterias for automatic sql injection tools and applying these to a set
of open source sql injectors, producing analysis/benchmarking reports.
Additionaly, in a semi-academic manner, algorithms used by several sql
injectors will be analyzed both implementation and complexity vise.

**Deliverables And Project Schedule Milestones**

Two set of documents will be produced. One of them will include the
benchmarking criterias and the other will comprise of analysis of
selected sql injectors against the benchmarking criterias. Moreover, an
interactive visual data flow diagram, giving hints to testers about
which tool should be used under which circumstances, will be implemented
with web-based technologies such as jquery library.

April 03 Project Kickoff

April 03-30 Determination of the benchmarking criterias

May 01-15 Producing a test environment image with 5-6 rdbms (MSSQL
Express, Oracle Express, DB2 Express, MySQL, PgSQL, etc.) and a
vulnerable application (which will support different sql injection
types, databases and include logging capabilities)

May 15-31 Selecting and installing automatic sql injectors onto the test
system and starting to use them on vulnerable application

June 01-30 Analysing tools and applying benchmarking criterias,
contacting the authors as we proceed

July 01-31 Producing reports for benchmarking criterias and tool
analysis

**About Us**

We're part of OWASP-Turkey. [Mesut Timur](http://www.h-labs.org) is a
junior in the Computer Engineering Dept. of [University of
GYTE](http://www.gyte.edu.tr) and [Bedirhan
Urgun](http://www.webguvenligi.org) is a web/application security
specialist in [TUBITAK-UEKAE](http://www.uekae.tubitak.gov.tr).

## OWASP-WeBekci Project

by Bunyamin Demir

<http://www.owasp.org/index.php/Category:OWASP_WeBekci_Project>

**Executive Summary**

Web application firewalls (WAF) are gaining importance among the
information security technologies designed to protect web sites from
attack. WAF solutions prevent attacks that network firewalls and
intrusion detection systems can't and they require no modification of
application source code. ModSecurity [10](http://www.modsecurity.org/)
is an open source web application firewall that runs as an Apache
module. It is an embeddable web application firewall and it provides
protection from a range of attacks against web applications. It is an
open source project available to everyone; it however does not come with
an admin panel.

I decided to provide this essential tool with a control panel which I
believe will ease and thus encourage its usage.

ModSecurity allows for HTTP traffic monitoring and real-time analysis
with no changes to existing infrastructure. My main goal is to analyze
attacks and generate rules to change the configuration of the
ModSecurity accordingly.

ModSecurity has a feature called “flexible rule engine” as its heart of
Attack Prevention capability . It uses ModSecurity’s “Rule Language,” (a
programming language designed to work with HTTP transaction data). It is
easy to use and flexible; yet the system administrators need to learn
its own rules to create what is called “Certified ModSecurity Rules” to
be implemented. My control panel will automate the major code-generation
in Rule Language.

**Objectives and Deliverables**

  - **Configuration** : Most of the configuration parameters will be
    managed through the web interface
  - **Rule Generator** : Basic rules will be generated using the web
    interface
  - **Core Rule Integration**: Core rules will be added to the database
    for use
  - **Logging and Reporting**: Apache error log and modsec_audit log
    will be parsed and presented to the user thru the web interface
  - **DB Support** : MySQL

**Why I should be sponsored for the project** Being a SpoC2007 project,
it couldn't be implemented mainly due to a job change and therefore lack
of time. With the help of Bedirhan Urgun we'll be able to produce a
quality web admin panel GUI for a same host modsec installation
infrastructure. We are both part of OWASP Turkey
[11](http://www.owasp.org/index.php/Turkey) and tried to produce a great
deal of awareness both about web security and OWASP with both
documents/chapter meetings/email list and mini-conferences.

## Teachable Static Analysis Workbench

By Dmitry Kozlov, Igor Konnov

**Introduction:**

This application covers two OWASP Project proposals: P002 Teachable
Static Analysis Workbench and P023 Code Review Tree. These project
proposals look complementary and the key idea was to create ONE tool for
code review instead of number non-integrated tools. Note: this project
is very close to P024 Attack Surface Metric too – based on web
application entry points and used backends it is easy to compute such a
metric.

**Project objectives and deliverables:**

Project is intended two deliverables: research technical report
(publication ready article) and a workbench prototype.

The research will be intended to answer the following questions:

  - Can we integrate existing open source static analysis tools (OWASP
    and third-party) to work altogether? We plan analysis to cover the
    following tools: LAPSE, Orizon, ESAPI, FindBugs.
  - How static analysis workbench can be taught by security analyst?
  - How static analysis workbench can support web-applications built
    using MVC frameworks?

Workbench prototype will be Java-based Eclipse plug-in which aim is to
help security analyst/code reviewer validation of web application. At
prototype step we suggest to analyze J2EE Web tier applications build on
Java Servlets, JSP (without business logic in it) and one MVC framework
(Apache Struts). We plan workbench prototype to have the following
functionality:

  - Input validation vulnerabilities analysis: identification of web
    application entry points (aka attack surface in P024), call graph
    for each entry point (see “Packages -\> Classes -\> Methods -\>
    callsites” in P023), identification of data validation routines,
    teachable taint analysis.
  - Authentification and access control analysis: identification of code
    related to access control and it’s analysis.
  - Pattern-based code analysis.
  - Teachability: analyst indicates security-related code (sources of
    tainted data, sensitive sinks, input validation and sanitizing
    functions, access control code, etc.) and workbench automatically
    recomputes possible vulnerabilities list. The second idea is to
    spread knowledge gathered from analyst to other web applications.

Project budget: $10K (note: this project combines two OWAPS Project
Proposals)

**Future development:**

Further, workbench can be extended to support various Java web
application frameworks and to support Python web applications (it seems
to us that teachable tool is much more valuable for Python and other
languages where the notion of web application is not so formal as in
J2EE).

'''Background: '''

Dmitry Kozlov is a postdoc researcher at Moscow State University. Since
2003 he leads a group performing research in the area of web application
security. In 2007 this group took part in OWASP Spring of Code on
project "Python Dynamic Analysis". This project was implemented mostly
by Dmitry’s PhD student Andrew Petukhov. Also in 2007 this group created
static analysis tool for Python language, based on Pixy PHP analyser
(publication is upcoming).

Igor Konnov is PhD student at Moscow State University he has strong
background in program analysis and verification.

## OpenPGP Extensions for HTTP - Enigform and mod_openpgp

By Arturo 'Buanzo' Busleiman

### Introduction to the project

My name is Arturo Busleiman, a.k.a Buanzo. Last year I worked with OWASP
to take Enigform (The OpenPGP Firefox Extension) and mod_openpgp (The
Apache counterpart) to an usable level. This year, I want to focus on
mod_openpgp and Secure Session Management, presenting a working
web-site using this new authentication methodology in such a way that it
will attract security professionals and web-developers to this new mix
of two good'ol protocols: HTTP and OpenPGP.

For that to happen, OWASP support is essential. I'm very happy to submit
my application for Summer of Code 2008.

### About Buanzo

I am a 26 year old Independent security consultant from Buenos Aires,
Argentina, that has contributed to the world of information systems
security since 1994. Linux and Security are my life.

A quick search for buanzo on google
[12](http://www.google.com/search?hl=en&q=buanzo&btnG=Google+Search)
will provide all necessary details about my professional and community
background. For comprobable experience, you could also check my Rent a
Coder
profile.[13](http://www.rentacoder.com/RentACoder/SoftwareCoders/showBioInfo.asp?lngAuthorId=735204)
or my "Customer Comments" page at [14](http://www.buanzo.com.ar/pro/).

I've contributed scripts, fixes and translations to the Nmap project.
I've also acted as Expert Contributor for SANS TOP-20 2004, 2005, 2006
and 2007. I've developed tools and written documentation that can be
found in Freshmeat, mozdev.org and addons.mozilla.org. Also I've written
the Unix chapter of the OISSG's Information Systems Security Assessment
Framework, v1.0 [15](http://www.oissg.org/content/view/71/71/).

In my free time, I "run" the 2600 Argentina meetings, write articles,
give talks and play the guitar.

I'm an active member of the FLOSS community since 1996, having written
articles in magazines
<http://www.net-security.org/dl/articles/Detecting_and_Understanding_rootkits.txt>,
made TV, radio and newspaper appearances
[16](http://codigoabierto.bitacoras.com/archivos/2005/04/01/buanzo-hacks)
and led different security research groups of Spain, Mexico and
Argentina. Currently I contribute time thorugh my sites, forums and
blogs, answering questions in mailing lists and helping coordinate some
local LUGs. I do also manager the Linux Counter for Argentina
[17](http://counter.li.org/reports/place.php?place=AR).

### About Enigform

The project has draw attention from the IETF OpenPGP Working Group, and
even Vinton Cerf (The Father of the Internet) said that Enigform and
mod_openpgp "\[this\] strikes me as a really interesting idea and I
hope you (Buanzo) will pursue it with the W3C." (February 18, 2008).
[18](http://en.wikipedia.org/wiki/Enigform)

## OWASP AntiSamy .NET

  - Arshan Dabirsiaghi

**Executive Summary**
The OWASP AntiSamy Project was well received at the OWASP/WASC San Jose
2007 conference, and the momentum carried forward as the project was
noted in several popular blogs and had its various distributions
downloaded in aggregate thousands of times.

All the platforms, not just Java, need this functionality. The Zend
group is currently working on getting a PHP version started, so
naturally the only platform remaining for major sites is .NET.
Therefore, I propose that OWASP sponsor me in creating a .NET version of
the OWASP AntiSamy Project. It should also be noted that the OWASP ESAPI
.NET project requires this API to be created.

**Background**
I'm currently a Senior Application Security Engineer at Aspect Security,
an industry leading application security company. I've delivered
tutorials all over the country at various commercial organizations and
conferences like OWASP and Blackhat.

**Proposed Project Reviewer: Jeff Williams/Dinis Cruz**
Jeff Williams will be the easiest reviewer due to proximity, but Dinis
Cruz's or another OWASP .NET project member's knowledge of .NET may
prove useful to the project.

**Objectives and Deliverables**
The aim of the project would be to deliver a functionally identical
version of the AntiSamy project in .NET. Secondarily, we would hope to
deliver a Release quality product by the end of the Summer of Code
timeframe in line with the Java version.

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

## Lockpick

  - Mark Roxberry

**Summary**

Lockpick is an open source penetration testing project management tool.
There are plenty of tools that do specific functions, or a range of
technical functions (NMAP, Nessus). However, there are not many open
source tools to help manage the scope of the testing a system. Lockpick
will fill that role. When I start a penetration test, Lockpick will
provide my checklists and script resources and update my tools. For
intelligence gathering, Lockpick will let me create profiles for target
companies and persons. I can shell out to my normal tool suite and
organize my log files and other output with the tool. Eventually, I can
use Lockpick to pull all of the testing data together and generate an
executive summary and detail report with the logs and profiles for
addenda.

**Project Roadmap**

April 2, 2008 - April 30, 2008 (Sprint 1)

  - Architecture, technical design (use cases, db design) and UI design

May 1, 2008 - May 31, 2008 (Sprint 2)

  - Project framework (modular design - use an dependency injection
    (IoC) architecture, so we can rip and replace components)
  - GUI framework
  - GUI for pen-test overview (use NIST or OSSTMM for process
    milestones)

June 1, 2008 - June 30, 2008 (Sprint 3)

  - Competitive intelligence feature (Company and individual profile
    builder)

July 1, 2008 - July 31, 2008 (Sprint 4)

  - Checklist and scripting repository feature (with rss synchronization
    feed)

(Unit Tests, Code, and QA)

July 15, 2008 Project Status Report

August 1, 2008 - August 31, 2008 (Sprint 5)

  - 3rd Party tool integration (shell out and log management)

**Project Wishlist**

  - Report generator (integrated with open office, google docs)
  - OVAL (Open Vulnerability and Assessment Language) database reader
  - Testing log GUI

**Project Team**

Mark Roxberry, CISSP, CEH, MCP - independent software vendor. I've been
writing code since infancy. It would be great to have OWASP sponsor the
project and give me the opportunity to create something that other
testers can use.

## OWASP Live CD 2008 Project

  - Matt Tesauro

**Introduction**

The previous OWASP Live CD project distributions have laid a good
foundation for the 2008 Project. I'd like to take the existing Live CD
and further enhance it. I see the 2008 Live CD as filling the Web App
Sec niche not the more general Pen Tester niche. I'd concede general Pen
Testing to Backtrack [19](http://www.remote-exploit.org/backtrack.html).
However, Backtrack has a different audience and is not specifically
tailored for web application security professionals. This is the role I
think this Live CD could fulfill with great success. I'd like to take
the OWASP Live CD 2008 Project in that direction and see the OWASP Live
CD become to Web App Sec what Backtrack is to Pen Testing.

**Proposal**

I'd like to take the existing applications and documentation in the
current Live CD and add significantly more tools and documentation
specifically focused on Web application security. I think OWASP's
Phoenix/Tools page [20](http://www.owasp.org/index.php/Phoenix/Tools)
would be a good starting point for potential tools. I'd also like to use
WASC [21](http://www.webappsec.org/) and ISECOM/OSSTMM
[22](http://www.isecom.org/) as sources for material.

The project would first enumerate a list of tools to include on the CD
where licensing, supported OS and space will determine what is included
on the Live CD. After determining a reasonable list of tools, the next
phase would be to create modules for the tools and merge these modules
with the Live CD. Then documentation and tutorials would be added (also
as space allows) followed by any remaining OWASP branding. Additional
polishing could include pre-installation (license permitting) of the
VMware tools.

**Deliverables**

April 2 to May 15, 2008

  - Enumerated tools and reference material for installation verifying
    that the software license allows permits distribution.

May 16 to July 4, 2008

  - Create modules for each tool and begin to merge the modules with the
    base distribution.
  - Begin testing of the Live CD.

July 5 to August 31, 2008

  - Complete the merging of modules and install any remaining
    documentation.
  - Further testing of the Live CD particularly installation of
    new/updated modules.

**Challenges / Outstanding Issues**

While the current Live CD is base on Morphix – a Knoppix derivative
created to allow easy creation of custom Live CDs, I'm not sure it it
provides the flexibility needed to keep the CD tools updated. While I'm
fine with keeping the Live CD on Morphix, I also see value in switching
to another distribution: SLAX. Here's the brief pros and cons of each as
I see them.

Pros of Mophix:

  - no change to current LiveCD - principally just updates to existing
    and augment.
  - Modular Live CD
  - Based on Knoppix which is the granddaddy of live CDs (tons of
    documentation)

Cons of Morphix:

  - While modular, uses a modular structure which isn't compatible with
    other well established live CDs - particularly Backtrack
  - Modules are not as granular as SLAX (lower ease of updating)

Pros of SLAX:

  - Modular Live CD (more modular then Morphix though I'm more familiar
    with SLAX then Morphix from using/modifying Backtrack)
  - Same modular format as Backtrack and other SLAX variants. This
    allows module sharing between OWASP and other live CDs
  - As tools are updated, only the module for that tools would need to
    be updated - not the entire live CD.

Con of SLAX:

  - Would have to re-do the work done for the current Live CD

As said above, I'm not sold on either distro but I do think going
forward, the more granular modules of SLAX will allow for easier updates
of the included tools and documentation. Backtrack is a good example of
this. I think the migration would represent a short term loss for a long
term gain.

**A bit about me**

I've been using Linux since somewhere around 1996 when I got my first
“Mega Distro pack” which included 6+ distro CDs, a bumper sticker and
a t-shirt for $29.95. I think it was in the RedHat 5.2 time frame. I've
had Linux as my primary OS since 2000 and have used many, many different
distros. Also, I am a RHCE (\#803005588313799) as well as Linux+
certified so I believe I'm qualified the Linux aspects of the project.

I got started with creating static HTML pages in 1999 and my first job
out of college was a Web application developer for an international
telecom company in 2000. Later, I took a developer job at Texas A\&M
University and also taught Web application development courses at the
undergraduate and graduate level. Next, I spent some time as a Pen
Tester where I discovered WHAX, Auditor and Backtrack live CDs and
realized how useful they can be. Currently, I work on Web Application
Security for an agency with \~75 internally developed web apps and
500,000+ users. I'm involved in application development from preliminary
design reviews to pre-production security testing. I also have a CISSP
(Cert \# 67636) and CEH (Certified Ethical Hacker) security
certifications. I've been enjoying OWASP since I first discovered Web
Goat (then at version 3.7) and thought it was high time I gave something
back to OWASP.

## OWASP Education Project

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

## Fortify Code Review Project

  - David Rook

'''Your educational and professional background: '''

I have worked in IT for over 8 years now with 5 years Information
Security experience. I have obtained and taught many IT certifications
in my career so far.

'''Application security experience and accomplishments: '''

Work experience as an Information Security Analyst implementing
application security in a highly sensitive environment. I'm currently
contributing to an OWASP project (Code Review guide) and spoken on the
subject of Application Security at a developers conference.

'''Participation and leadership in open communities: '''

As mentioned above I'm currently contributing to one other OWASP
project.

'''The opportunity, challenges, issues or need your proposal addresses:
'''

My proposal is to help Fortify and OWASP achieve the goals set out in
the objectives for this project. The project has the ability to deliver
a clear guide on static analysis and subsequently how to add this into
the SDLC. The auditing of open source software can help to enhance the
security of this software and possibly improve its ability to increase
its user base.

'''Milestones and objectives: '''

Process all OWASP Java developments through the Fortify scanner Review
the output of the Fortify scans on the OWASP projects that have been
submitted Produce the first draft of the three documents that need to be
delivered Liaise with OWASP/major Java Open Source project contacts to
involve them in reviewing the output of Fortify scans of their
developments Provide final documentation

'''Specific activities and who will carry out these activities: '''

I will carry out all the activities for this project myself.

Research current methods of static analysis in the application security
arena and combine this with my own knowledge. This research will allow
me to define a workflow which illustrates how static analysis will be
integrated into the SDLC.

Identify which OWASP applications have been submitted for analysis and
identify which other projects can be scanned. I will contact the
relevant project leads to get them to submit the projects for review.

Review the results of the scans and analyse any issues found. I will
provide feedback on any issues found to the relevant project lead.

Identify major Open Source Java projects and liaise with these projects
to involve them in scans of their code. We will provide feedback on the
results and ensure that future code revisions are also scanned by the
Fortify system.

Provide revised guides based on feedback from the draft documents and
the use of the Fortify system.

'''Specific deliverables and a rough project schedule so we can track
progress: '''

The deliverables for this project would see me firstly provide draft
guides once I have used the Fortify system to review any recently
scanned OWASP projects.

I would also seek to involve major java Open Source projects in the
Fortify project which will help the Fortify Scanner become part of many
Open Source developments.

Providing report documents to the relevant OWASP project leads which
would explain any issues found in the Fortify scan of their code

Deliver the final guides for review

'''Long-term vision for the project: '''

I would see this project firstly serving as a focal point for anyone
wishing to implement Static Analysis into their own SDLC. Secondly I see
this project as a launching pad for the Fortify scanner to increase its
use by Open Source projects.

'''Any other reasons why you and your project should be selected: '''

I'm very passionate about Application Security and I want to use this
passion to help the Application Security community. I think the project
should be selected so that the objectives of both the OWASP and Fortify
can be achieved.

**Project Plan:**

My project plan can be found here:
<http://docs.google.com/Present?docid=dcd4c73_0ghsncvcf&skipauth=true>

## Source Code Review OWASP Projects

  - James Walden

'''Educational and professional background: '''

I am an assistant professor of computer science at Northern Kentucky
University, and I previously worked as a visiting assistant professor at
the University of Toledo. Before entering academia, I worked for Intel
as a software engineer for five years. I hold a Ph.D. in theoretical
physics from Carnegie Mellon University.

'''Application Security experience: '''

My primary area of interest in research and teaching is application
security. I have worked with application security issues since 1993 when
I was developing secure CGI scripts in perl at CMU, and much of my work
at Intel involved application security. I have used Fortify's Source
Code Analysis tool in my teaching and research since 2005, and I served
as a technical reviewer for the book *Secure Programming with Static
Analysis* by Brian Chess and Jakob West.

I have developed workshops on secure programming, software security, and
web application security, including both slides and demonstration web
applications, which I have taught to computer science faculty at
conferences since 2005 and to software developers through my university
since 2006. I have given many talks on application security during the
last three years to local professional groups like IEEE, ISACA, and ISSA
and at conferences such as the Ohio Information Security Conference and
Recent Advances in Information Assurance, Network and Software Security
2007.

'''Open Communities: '''

I have contributed to the OWASP Guide and OWASP Code Review Guide, and I
participate in the OWASP Cincinnati chapter. I have also submitted a
number of small patches to fix bugs in open source projects over the
years.

**Opportunity and Challenges**

There will be other contributors to this project, including one
professor and several students. Dr. Maureen Doyle will work with one
student to develop and document the workflow to incorporate Fortify Java
Open Source static analysis into the SDLC. Anticipated issues include
detecting false positives that result from the analysis and reporting
the security errors to the appropriate developers for future correction
(e.g., through Bugzilla or similar system). It is uncertain how much of
the workflow can be automated. The workflow documentation will require
that static analysis be a part of the SDLC.

Dr. Doyle has twenty years of industry experience working with various
development lifecycles and has implemented software processes at General
Electric and Alphatech, Inc. Dr. Doyle keeps current on software
development paradigms as part of her course preparation for graduate and
undergraduate software engineering courses. Dr. James Walden, whose
background is described above, will lead the auditing task and
collaborate on the workflow development.

**Milestones and Objectives**

The objectives of this project are:

  - Develop and document a workflow for open source projects to
    incorporate static analysis into the Software Development Life Cycle
    (SDLC).
  - Apply the above workflow as a required step for OWASP projects.
  - Aid in auditing select open source projects to create a baseline for
    comparing security amongst open source projects.

The milestones for this project are:

  - **Three projects** selected for initial analysis by May 1.
  - **Project 1** submitted to Fortify Java Open Review Project by June
    1
  - **Workflow** sent out for review by June 1
  - **Projects 2 and 3** submitted to Fortify Java Open Review Project
    by July 1
  - **Additional projects** identified for analysis with the revised
    workflow by July 1.
  - **Workflow** available at OWASP by August 15
  - **Additional projects** submitted to Fortify Java Open Review by
    August 15

**Project Schedule**

  - May 1, 2008: Team finalized, three projects selected for initial
    analysis.
  - June 1, 2008: Team of workflow reviewers finalized, preliminary
    workflow sent out for review, project 1 analysis complete using
    initial workflow.
  - July 1, 2008: Project 2 and 3 analysis completed, workflow
    finalized, additional projects selected for creating baseline.
  - August 15, 2008: Analysis of projects for baseline security measures
    complete, workflow documented on OWASP web site.

**Long Term Vision**

We would like to analyze the classes of security bugs found through
static analysis to determine if patterns exist, so that we could develop
measures to prevent the introduction of such bugs into projects. We
would also like to implement a security metrics collection process for
projects, recording data on static analysis usage, number of security
bugs, lifetime of security bugs, and so forth.

**Supporting Information**

Dr. Walden and Dr. Doyle bring a combination of industrial and academic
experience to this task. They both regularly mentor undergraduate
students working on research projects, and they have already recruited
students to work on a project using static analysis tools. The funds
offered by OWASP will be used solely to fund our undergraduate students.

## P022 - OWASP Access Control Rules Tester

By Andrew Petukhov

**Introduction:**

I believe that web application business logic vulnerabilities will be
under increasing attention in near future. Although input validation
vulnerabilities (XSS, SQLI) are in overwhelming majority nowadays, many
automated approaches have emerged that deal with them. On the contrary,
there are no known approaches (and methodologies for security experts)
to classify or even detect business logic vulnerabilities. Besides,
business logic flaws usually expose web application to great risks
(according to OWASP Testing Guide). My proposal is to create a
systematic approach that addresses business logic vulnerabilities.

**Project objectives and deliverables:**

Project is intended two deliverables: research technical report
(publication ready article) and an Access Control Rules Tester tool.

The research will be intended to answer the following questions:

  - Is there a reasonable classification of business logic
    vulnerabilities?
  - Is it possible to generalize some cases into methodology or even an
    algorithm for an automated tool?
  - Is it possible to build precise access control matrix for a web
    application and how?

Access Control Rules Tester (AcCoRuTe) tool will be Java-based
application. As proposed inP022, AcCoRuTe will have the following
functionality:

  - Site spider. Basic features: Javascript (and AJAX) is interpreted by
    Rhino in order to get more site links; forms are filled in by
    operator.
  - Sitemap generator. Sitemap is presented to operator; he can make it
    more precise/complete.
  - Sitemaps analyzer. This component intersects different sitemaps in
    order to determine possible flaws. The result is test case, which
    verifies, whether vulnerability really exists or not.

I am PhD student at Moscow State University. In 2007 I took part in
OWASP Spring of Code on project "Python Dynamic Analysis". I have strong
background in programming and I beleive that I also have creative
approach to existing scientific problems.

## Python Static Analysis

By Georgy Klimov

**Introduction:**

During 2007 Dmitry Kozlov, Igor Konnov and Georgy Klimov prototyped
taint-style static analysis for Python web applications. This tool is
based on Pixy project. It is able to find input validation security
vulnerabilities in Python-based web applications. This tool is currently
in alfa release. It supports limited subset of Python: functions,
modules, classes and data structures, but not generators,
comprehensions, lambda-functions etc. And it has support only
mod_python web applications.

**Project objectives:**

The aim of this project is to bring this project to at least beta
quality to become OWASP open source project:

  - full language support,
  - other Python frameworks support,
  - analysis improvement,
  - reporting capability,
  - documentation,
  - promotion materials: publication-ready article and presentation.

**Future directions of development:**

Integration of this tool into teachable static analysis workbench
applied to SoC 2008 by Dmitry Kozlov and Igor Konnov. Additional
languages support.

**Why should I be sponsored for this project:**

I’m 5-th year graduate student at Moscow State University and my
scientific work concern with static program analysis. I’m very good in
programming Java and Python (this tool is written mostly in Java). This
tool was written by me and my scientific advisors: Dmitry Kozlov and
Igor Konnov.

## P003/P013 - OWASP Application Security Tool Benchmarking Environment and Site Generator refresh.

\= submitted by Dmitry Kozlov (see below about project team)

**Introduction** In my opinion it is not good idea to start two new
different projects concerning to Benchmarking Environment. OWASP already
has "Insecure Web App Project", Foundstone created couple of similar
applications, our group created similiar application in Python (by the
way: Does OWASP need it to be published?). OWASP SiteGenerator is
another different tool but very platform-bound. Moreover NIST is also
working in this direction.

**Project description** My idea is to split destination web application
technology from the three reusable libraries: library of navigational
elements, library of vulnerabilities and library of language constructs.
Library of navigational elements is required to assess spidering
features and library of language constructs is required to assess source
code scanners this constructs can be in programming language or
preferable in language-independent form of Abstract Syntax Tree.
Navigation and vulnerability libraries are independent from technology
web application built in. This make is possible to create web
applications with similar vulnerabilities in different technologies.

User can create target XML application configuration similar to
SiteGenerator's in terms of site structure, navigational elements and
vulnerabilities. After that web application can be generated using
technology specific generator. Generators can create source code or
binary application but not a stub like SiteGenerator. This allows static
and dynamic code analysis to be performed on web application and
penetration testing too.

I think this tool and components library should be platform-independent
unlike SiteGenerator. And only technology-specific generators may be
platform-dependent. Such technology-specific generators can be source
code generators or can be binary application template.

If you are interested in we can perform such project by our students
under scientific advisory by Dmitry Kozlov and Andrew Petukhov, but it
seems to me this tool will be delivered in about 6-7 month. During
SoC2007 it was about 7 month between start and finish of projects.

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

## P006 - OWASP Corporate Application Security Rating Guide

**\*Project Application submitted by: Parvathy Iyer**

Educational and professional background: CIA, CISA with over seven years
experience in information technology and application security audits.

Application security experience and accomplishments : I have experience
in ensuring that equity application solution conforms to security
compliance requirements of the stock exchanges and the Security Exchange
Board of India.

Participation and leadership in open communities : Member of ISACA and
IIA, NJ Chapters.

The opportunity, challenges, issues or need your proposal addresses :
The project will be the first of its kind that I have ever attempted and
in that sense its my first challenge. The project will help me organize
and structure publicly available data that large companies will share of
the lessons learned about how to organize an application security
initiative, best practices for training and testing, and more.

Objectives or ways in which you will meet the goal(s) : Analysis of
publicly available data such as interviews, presentations, briefings for
details. The project will link to all source material used in creating
the rating. The rating will involve application security and awareness
training; defining security requirements and verification for each
application; establishing a dedicated application team and process for
responding to security issues and allocating points to each issues.

Specific activities and who will carry out these activities :
Parvathy.N.Iyer will carry out the entire analysis and rating. Neal
Kirschner, Director of IT services at Eisner LLP with over 20 years work
experience will be the reviewer on the project.

Specific deliverables and a rough project schedule so we can track
progress : A project update will be provided on May 31, 2008 and the
project shall be completed by August 31, 2008.

Long-term vision for the project: The project will be used as a guide
for rating applications.

Any other reasons why you and your project should be selected: I feel
that I should be selected for the project is because this would be a fun
challenge for me and also because I am competent and committed to doing
this project.

Project Application submitted by: Parvathy Iyer

Current occupation: IT Audit- Senior, Eisner LLP

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

## OWASP Book Cover & Sleeve Design

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