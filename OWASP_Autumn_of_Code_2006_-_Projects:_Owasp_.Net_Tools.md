**AoC Candidate:** Boris

**Project Coordinator:** Dinis Cruz

**Project Progress:** 100% Complete - [Progress
Page](OWASP_Autumn_of_Code_2006_-_Projects:_Owasp_.Net_Tools_-_Progress "wikilink")

## Latest

Tiger 1.0 is available for download\! Get more details on the new
[official project page](OWASP_Tiger "wikilink").

## Background and Motivation

### History Behind Project

OWASP .NET Tools were originally created by Dinis Cruz as standalone
applications [ANSA](ANSA "wikilink"), [ANBS](ANBS "wikilink") and
[SAM'SHE](SAM'SHE "wikilink"). These tools are used to diagnose security
problems in shared hosting environments based on Microsoft's ASP.NET
platform.

### Motivation

The number of Web sites and applications is growing rapidly, as well as
number of platforms. Microsoft's Web platform is known for its high
level of developer productivity, ease of setup and administration and
great integration with other, often very widespread, Microsoft products.
So, the Microsoft Web platform may be very attractive to individuals and
various types of organizations. However, there are still many doubts
about how secure it is. Many of these doubts are not backed by specific,
measurable data and tests but instead on historical (but not necessarily
outdated) data and "word of mouth" type of evidence. Determining how
secure an application running on Microsoft's Web platform is usually
requires a lot of time and resources. There aren't many tools for
testing security aspects of Microsoft's Web platform that make things
easier. Even few are publicly available.

Another problem is that, due to a user-friendly nature of the tools
provided in Microsoft's products, administering Web sites and
applications may seem easier than it sometimes is. Many times these
tasks are delegated to people who are not aware of numerous
security-related problems (sometimes even not to professional IT
administrators) that may occur. As a result, many Web sites and
applications deployed are insecure.

### Problem to be Addressed

OWASP Tiger 1.0 (this project) is meant to improve and integrate ANSA,
ANBS and SAM'SHE into single (but versatile) tool and create both more
functionality and better user exeprience.

### Benefit to OWASP Members and Community

The deliverables of this project will (hopefully) help OWASP members and
community

  - be aware of vulnerabilities and risks involved with their
    applications before releasing them to general public
  - determine if their applications are deployed in a less than optimal
    security environment
  - ease patch/hotfix management of their OS/Web server software
  - perhaps even make decisions about the technology stack(s) used

## Goals and Deliverables

### Plan of Approach

  - Convert all [SAM'SHE](SAM'SHE "wikilink") and
    [ANSA](ANSA "wikilink") tests into [Owasp
    SiteGenerator](Owasp_SiteGenerator "wikilink") tests
  - Document and risk rate all tests using [Owasp Report
    Generator](ORG_\(OWASP_Report_Generator\) "wikilink")
  - Merge and update current [SAM'SHE](SAM'SHE "wikilink"),
    [ANSA](ANSA "wikilink") and [ANBS](ANBS "wikilink") user interface
    to reflect the new identity and funcionality

### Deliverables

The main deliverables of Tiger 1.0 will be:

  - Source code checked in a publicly available source code control
    system (most probably SourceForge.net)
  - Binaries (in the form of installer) posted on SourceForge.net
  - User documentation posted on SourceForge.net

## Risks and Rewards

### Main Risks

The biggest risks with this project are:

  - Lack of technical documentation for the current releases (so it's
    difficult to grasp and build upon the current system)
  - Envisioned functionality is not fully specified (yet). Ideally, we
    sould have a full-blown functional specification.

### Rewards of Successful Project

Hopefully, this project will help security professionals find and patch
security vulnerabilities much faster and easier than before. That will
in turn help the whole user community by making Web applications (well,
at least those deployed on the Microsoft platform) more reliable and
trustworthy.