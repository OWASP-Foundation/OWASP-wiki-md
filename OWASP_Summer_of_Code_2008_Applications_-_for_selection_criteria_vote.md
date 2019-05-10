# OWASP Summer of Code 2008 Applications - for selection criteria vote

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

## OWASP Live CD 2008 Project

  - Matt Tesauro

**Introduction**

The previous OWASP Live CD project distributions have laid a good
foundation for the 2008 Project. I'd like to take the existing Live CD
and further enhance it. I see the 2008 Live CD as filling the Web App
Sec niche not the more general Pen Tester niche. I'd concede general Pen
Testing to Backtrack [4](http://www.remote-exploit.org/backtrack.html).
However, Backtrack has a different audience and is not specifically
tailored for web application security professionals. This is the role I
think this Live CD could fulfill with great success. I'd like to take
the OWASP Live CD 2008 Project in that direction and see the OWASP Live
CD become to Web App Sec what Backtrack is to Pen Testing.

**Proposal**

I'd like to take the existing applications and documentation in the
current Live CD and add significantly more tools and documentation
specifically focused on Web application security. I think OWASP's
Phoenix/Tools page [5](http://www.owasp.org/index.php/Phoenix/Tools)
would be a good starting point for potential tools. I'd also like to use
WASC [6](http://www.webappsec.org/) and ISECOM/OSSTMM
[7](http://www.isecom.org/) as sources for material.

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