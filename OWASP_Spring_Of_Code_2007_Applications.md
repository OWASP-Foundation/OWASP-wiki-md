\[10th April 2006\] : UPDATE: the submission period is now closed and
this page is locked for editing. The OWASP board will now evaluate the
proposals and publish the results as soon as possible

This page contains project Applications to the
[OWASP_Spring_Of_Code_2007](OWASP_Spring_Of_Code_2007 "wikilink")

**If you want to apply for a SpoC 007 sponsorship you HAVE TO USE THIS
PAGE for your application**

See
[OWASP_Spring_Of_Code_2007\#How_To_Participate](OWASP_Spring_Of_Code_2007#How_To_Participate "wikilink")
for what do to one you completed your Application

-----

**Proposed template:** {for longer proposals, in addition to these
details you can create a PDF}:

## {Your first name or Alias} - {Project name}

Please remember that projects will be selected and funded based on how
well they meet the [Selection
Criteria](OWASP_Spring_Of_Code_2007_:_Selection "wikilink").

You can propose your project in any form you wish, but the best
proposals will be well thought out, clear and concise, and reflective of
your passion for the topic. We strongly suggest that you include the
following information in your proposal.

  - Your educational and professional background

<!-- end list -->

  - Application security experience and accomplishments

<!-- end list -->

  - Participation and leadership in open communities

<!-- end list -->

  - The opportunity, challenges, issues or need your proposal addresses

<!-- end list -->

  - Objectives or ways in which you will meet the goal(s)

<!-- end list -->

  - Specific activities and who will carry out these activities

<!-- end list -->

  - Specific deliverables and a rough project schedule so we can track
    progress

<!-- end list -->

  - Long-term vision for the project

<!-- end list -->

  - Any other reasons why you and your project should be selected

## Buanzo - Enigform: Firefox Addon for OpenPGP signing of HTTP requests

I am a 25 year old Independent security consultant from Buenos Aires,
Argentina, that has contributed to the world of information systems
security since 1994, when BBSes and Linux still lived together.

A quick search for buanzo on google
[1](http://www.google.com/search?hl=en&q=buanzo&btnG=Google+Search) will
provide all necessary details about my professional and community
background. For comprobable experience, you could also check my Rent a
Coder
profile.[2](http://www.rentacoder.com/RentACoder/SoftwareCoders/showBioInfo.asp?lngAuthorId=735204).

In my free time I like playing with my Punk-Pop band
[3](http://www.purevolume.com/futurabandapunkpop), Futurabanda.
[4](http://www.futurabanda.com.ar), and maintaining my Restaurants,
Wines and Recipes site. [5](http://www.vivamoslavida.com.ar). I have to
admit that my first priorities are my beloved son
[6](http://www.fotolog.com/buanzo) and my wonderful wife
[7](http://www.fotolog.com/buanzo).

### Accomplishments

I've contributed scripts, fixes and translations to the Nmap project.
I've also acted as Expert Contributor for SANS TOP-20 2004, 2005 and
2006. I've developed tools that can be found in Freshmeat, like mprl (a
getty enhancement to allow remote logins from the login: prompt of the
console). I've also written the Unix chapter of the OISSG's Information
Systems Security Assessment Framework, v0.1
[8](http://www.oissg.org/content/view/71/71/). I'm currently writing an
Internet Draft to be proposed for RFC regarding Enigform.

### Community

I run the official 2600 meetings site for Argentina
[9](http://www.2600.com/meetings/pages.html), I've been proposed, but I
refused, for President of the Argentinian Free Software group called
SOLAR \[www.solar.org.ar\]. I'm an active member of the FLOSS community
since 1996, having written articles in magazines
<http://www.net-security.org/dl/articles/Detecting_and_Understanding_rootkits.txt>,
made TV, radio and newspaper appearances
[10](http://codigoabierto.bitacoras.com/archivos/2005/04/01/buanzo-hacks)
and led different security research groups of Spain, Mexico and
Argentina. Currently I contribute time thorugh my sites, forums and
blogs, answering questions in mailing lists and helping coordinate some
local LUGs. I do also manager the Linux Counter for Argentina
[11](http://counter.li.org/reports/place.php?place=AR).

### My Project

Enigform [12](http://enigform.mozdev.org) is a Firefox extension that
enhances HTTP with OpenPGP functionality. It digitally signs outgoing
HTTP requests so that a web server can authenticate the identity and
data of the incoming request. It is a Web Security tool because it can,
if correctly implemented as any OpenPGP based technology, render man in
the middle attacks useless. I think OpenPGP already speaks for itself
regarding eMail. Imagine the same benefits for http and web
applications. I think Enigform can fit into the OWASP Validation Project
[13](http://www.owasp.org/index.php/Category:OWASP_Validation_Project).

Enigform is the reference implementation of the Internet Draft I'm
working on, in discussion with members of the IETF's OpenPGP Working
Group.

Some simple PHP code is enough to make a web application Enigform-aware
[14](http://enigformtest.buanzo.com.ar). The Smutty PHP MVC Framework
already supports Enigform [15](http://smutty.pu-gh.com/demo/enigform).

### Long Term

Have the Draft be proposed as a Standards Track RFC document, have
Enigform support directly in Apache and IIS, and port Enigform to other
browsers and/or programming languages, and also provide OpenPGP
De/Encryption support.

### Why should I be selected

I have the experience, security awareness and means to make this project
THE web security project of the decade. I am a respected member of the
international security community, and I firmly believe Enigform is my
greatest idea so far.

## Eoin Keary - Code review Project

  - **Executive Summary**:

I am proposing that I complete the OWASP Code review guide during this
period. The code review guide was started by me in 2005 and has much
information on reviewing code for common vulnerabilities. It is
frequently accessed (looking at the stats on the OWASP site) and
therefore is useful to practitioners.

I believe the code review guide is an integral part of the OWASP BOK
(Body of Knowledge). Ensuring secure development is key to secure
applications and code review is of paramount importance in this domain.

There are many sections still to be added and more to be readjusted and
rewritten to reflect the current state of the security world. Much needs
to be written on Web 2.0 technologies and distributed B2B technologies
such as Webservices.

The Code review process and procedure needs also to be covered. A guide
to establishing a mature code review process also needs to be done. Code
review methodologies also need to be discussed.

  - **Objectives and Deliverables**:

Update of the code review guide:

  - Add additional areas relating to the code review process such as:
      - Benefits and pitfalls
      - Methodology
      - The code review process
          - Transactional analysis
          - Managing the code review process
          - Assigning risk to findings

<!-- end list -->

  -   - Technical guides
          - Language specific best practice
          - Java
          - .NET
          - PHP
          - MySQL
          - Stored Procs
          - C/C++

<!-- end list -->

  -   - Code review by vulnerability:
          - Reviewing Code for Buffer Overruns and Overflows
          - Reviewing Code for OS Injection
          - Reviewing Code for SQL Injection
          - Reviewing Code for Data Validation
          - Reviewing code for XSS issues
          - Reviewing Code for Error Handling
          - Reviewing Code for Logging Issues
          - Reviewing The Secure Code Environment
          - Reviewing code for Authorization Issues
          - Reviewing code for Authentication Issues
          - Reviewing code for Session Integrity
          - Reviewing code for Cross Site Request Forgery
          - Reviewing code for Cryptography implementation issues
          - Reviewing code Dangerous HTTP Methods (Deployment)
          - Race Conditions

The areas of code are structured giving a brief explanation, the
anti-pattern (vulnerable pattern to look for) and a suggested fix.

  - **Why I should be sponsored for the project**:

I used to head up the code review team as part of the application
security group in fidelity investments and have 5+ years of the secure
code review process. I also was the lead of the Testing guide until V2
was published via the Autumn of Code.

I have always delivered any work I have volunteered for on time.

I have been involved in OWASP projects for 2/3 years now and have always
been an active contributor.

## Paolo Perego - Owasp Orizon Project

  - **Executive Summary**:

Owasp Orizon
[16](http://www.owasp.org/index.php/Category:OWASP_Orizon_Project)
Project born in 2006 as answer to the lack of common engine and library
usable by opensource code review related tools.

I'm proposing that, during the Spring of Code 2007 period, I'll complete
static analisys API and java source code enforment objects.

Sometimes a complete code review approach is not suitable for most
customers who wants to harden their code which is being approaching
release stage. For such a reason, I started writing Java objects that
embeds most of the security checks against common web vulnerabilities
(XSS, SQL injection, Session handling, ...) so that source code can be
hardened with a small effort in terms of code rewriting.

I do believe that a common set of API and a common safe coding best
practices library is one of the most important goals to bring
application security to the developers.

  - **Objectives and Deliverables**:

Completing the static code review API section

  - improving programming language to XML translator
  - improving security best practices code review scan library
  - improving secure coding fashion best practices library
  - writing the pattern matching scan using the aformentioned libraries

Writing the java source code enforment objects

  - writing an object to handle form data values to avoid XSS
  - writing an object to handle form data values to avoid SQL Injection
  - writing an object to handle HttpRequest and HttpSession objects

<!-- end list -->

  - **Why I should be sponsored for the project**:

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

## Sebastien Deleersnyder - OWASP Education Project

  - **Executive Summary**:

This Education project aims to provide in building blocks of web
application security information. These modules can be combined together
in education tracks targeting different audiences.

Web Application Security Education and Awareness is needed throughout
the entire organization, each area and level of organizations have
specific needs and requirements regarding education. A manager needs
other information than a security professional or developer. Novices to
the profession require other training than people with several years of
experience.

  - **Objectives and Deliverables**:

Currently the project goals are to create Educational Tracks:

  - Complete the [consolidation page of OWASP
    presentations](OWASP_Education_Presentation "wikilink") performed in
    the past
  - A "Web Application Security Primer" Track for beginners (4 hours)
  - A "What developers should know on Web Application Security" Track
    for developers (4 hours)

<!-- end list -->

  - **Why you should be sponsored for the project**:

I started the successful Belgian Chapter 3 years ago and have actively
contributed to OWASP since then. I also co-organized the European
conference last year in Belgium.

This is the first separate project that I started, originating from a
local demand to set up educational tracks for people that are new to Web
Application Security. There are literally hundreds of presentations and
an enormous amount of information on the OWASP web site. The goal of
this project is to restructure pieces of that information in reusable
modules that can be combined in educational tracks. It is my believe
that awareness is an important cornerstone of building secure web
applications, and this project will actively support that.

If we are granted Spoc 007 participation, I will be sharing the budget
with all active participants. This will be an extra motivation for
project participation. I will reinvest my part in the project to set up
a web conferencing / web casting solution to be used to disseminate the
project results and make them available for later use.

  - **More details**:

The detailed [road map](OWASP_Education_Project_Roadmap "wikilink") can
be found here. The SpoC 007 goal is to finish Sub Goals 1, 2, 3 and 4.
If time permits we can start with sub goal 5.

## Subere - OWASP JBroFuzz Project

#### Overview

JBroFuzz is a stateless network protocol fuzzer that emerged from the
needs of penetration testing. The purpose of this application is to
provide a single, portable application that offers stable cross-platform
network protocol fuzzing capabilities. At the same time, JBroFuzz
attempts to keep the User Interface (UI) as intuitive as possible.

#### Fuzzing

As seen by the emphasis given on the subject of fuzzing in the 2007
Testing Guide (v2), network protocol fuzzing serves as a fundamental
cornerstone of application security testing. For this, many different
categories and types of fuzzing have been defined.

#### Objectives

JBroFuzz needs to expand and grow in order to cover network fuzzing in a
more complete manner. Its modular implementation allows for the addtion
of new functionality by means of independent tabs. The key tabs proposed
to be added during the spring of code 2007 are (details in next
section):

  - **Open Source Tab**
  - **NTLM Brute Force over HTTP/S Tab**
  - **Pure HTTP/S Fuzzing using HTTPClient**
  - **Blind SQL Injection Fuzzing Tab**

At the same time, the following existing tabs need to be updated and
made more robust (details in next section):

  - **TCP Fuzzing tab allowing graph outputs**
  - **TCP Sniffing tab update thread Agent Queue**
  - **Update Generators file format**
  - **Include SOAP and XML fuzzing**

This expansion process relates to stabilising code that is presently
included in JBroFuzz, thus allowing it to run for extensive periods of
time (24h+) as well as adding more functionality in terms of the three
new tabs.

#### Deliverables

Based on the above, the new code elements that will be added are as
follows:

  - **Open Source Tab:** *Provide the ability to enumerate e-mails from
    newsgroups without breaching google automated search rules*
  - **NTLM Brute Force over HTTP/S Tab:** *Provide the ability to
    enumerate NTLM as well as brute over HTTP/S NTLM.*
  - **Pure HTTP/S Fuzzing:** *Implement a fuzzing tab utilising
    HTTPClient from Jakarta that will also allow for multi-threading*
  - **Blind SQL Fuzzing Tab** *Implement a tab that extracts information
    from a blind SQL injection point identified on web server over
    HTTP/HTTPS.*

For updating existing code elements that require a partial rewrite, the
following areas of focus are presented in detail:

  - **TCP Fuzzing tab allowing graph outputs:** *Provide the ability to
    graph fuzzing results during a particular session run. This will
    give the ability to integrate and pickup potential fuzzing
    patterns.*
  - **TCP Sniffing tab update thread Agent Queue:** *Update the code of
    the sniffing panel in order to handle threaded agents in a more
    memory efficient way.*
  - **Update Generators file format:** *Update the generators file
    format to allow for the parsing and creation of recursive
    generators.*
  - **Include SOAP and XML fuzzing:** *Include an up to date list of
    SOAP and XML fuzzing templates.*

Overall, the above two lists of changes should provide sufficient
complexity and output for the spring of code 2007, forming a challenging
implementation project.

#### Background

In its short life, the OWASP JBroFuzz Project has attracted the interest
of the online security community with a total of appr. 5000 downloads in
the last months.

Coming from a strong java background (5+ years) I decided to implement
and release JBroFuzz in order to initially simplify penetrations testing
processes that relate to web application and network protocol fuzzing.

I see the spring of code 2007 as a unique opportunity to industrialise
network protocol fuzzing (and in particular HTTP/S fuzzing) within a
single application, residing within OWASP.

#### Why should JBroFuzz be sponsored?

Centralising fuzzing resources into one application that has the ability
to handle network protocol fuzzing over HTTP and HTTPS in a simple and
intuitive manner forms an area of focus that should not be dismissed in
building secure software applications.

Keep the code platform independent adds a huge advantage.

Receving an OWASP grant from the spring of code 2007 will trigger a
share in the budget with all active participants depending on their
level of involvement. This will be a direct function of the number of
tabs and/or user functionality that they have assisted in implementing.

## Joshua Perrymon - OWASP LiveCD Project

  - **Executive Summary**:

I am proposing that I complete the second version of the OWASP LiveCD
during this period. The first version of the LiveCD is now available and
include many of the current OWASP documents and tools. I believe the
LiveCD is one of the best mediums to promote OWASP tools and
documentation. It is portable and already being used by thousands of
security proffesionals to perform application testing and training.

In the current state the CD is stable and contains a lot of tools.
However, this is just the beginning. There is a LOT of work that needs
to be completed. The entire CD experience needs to be branded using
OWASP graphics. This shouls start with the boot screen and carry all the
way through to the icons and desktop graphics. The CD should also
inlcude the wiki and ALL the tools developed for OWASP.

  - **Objectives and Deliverables**:

Update of the LiveCD:

  - Complete OWASP branding
  - Add OWASP wiki
  - Add encryption capabilities
  - Add more OWASP tools
  - Add more pen-test tools such as;

`VOIP, RFID, BlueTooth, Wireless, etc..`

  - **Why I should be sponsored for the project**:

I had the idea of the LiveCD about a year ago and have worked very hard
to get the first version developed. This was driven by my vision to make
all of the OWASP tools available on a portable medium. The main
difference in the OWASP liveCD vs. other live CDs is going to be the
regularity of updates. If sponsorship can be obtained the CD could be
updated on a monthly basis. Not once a year like other liveCDs. The CD
will also include specialty tools and documentation to perform VOIP,
RFID,Bluetooth, and wireless security assessments.

-----

## Mark Curphey – The OWASP Web Security Certification Framework

**Problem**

PCI DSS is attracting a lot of criticism for a lot of valid reasons.

<http://securitybuddha.com/2007/03/23/the-problems-with-the-pci-data-security-standard-part-1/>

<http://blogs.csoonline.com/node/210>

<http://www.computerweekly.com/blogs/stuart_king/2007/03/more-on-pci---the-audit-guide.html>

The list is of course long and not appropriate here……and while its easy
to knock PCI, there is nothing better out there.

**Solution and Deliverables**

As opposed to me continuing saying what’s wrong with PCI DSS, it seems
to me that OWASP is a perfect forum to simply create and publish a
“better criteria”. This can either be adopted and implemented by an
organization like OWASP or considered to be incorporated into the PCI or
other security standards. We won't get bogged down in the politics
up-front, but hold something good up to the world for people to adopt.
This project would of course draw on and bring together many of the
other OWASP Projects including the Guide (What is a secure web app),
Testing Guides (How to test for a secure web app), WebGoat (part of how
to certify an individual understands and can find web app issues) etc.
Many of those projects may not be complete or a perfect fit today, but
this project can bring a common connecting theme to a lot of very
valuable IP that OWASP has built over the years. I will also create it
in such as way that a corporate could adopt/adapt it themseles as well
as an industry. Where other OWASP projects are not complete or currently
suitable I will build a requirements doc that can be considered by those
teams if they feel appropriate.

This project would address the;

**Standard**

  - A complete auditable (important) web site security standard suitable
    for modern e-commerce companies including
      - The technical things people should care about
      - The operational / management things people should care about

**Certification Model**

  - A complete framework for certification (ongoing) and implementation
    (including certifying auditors, ongoing validation etc). This will
    include for example the model for certifying auditors (including the
    actual test program); checklists and forms for auditors to complete
    and other supporting material.

Essentially its a complete blueprint for an organisation like OWASP or a
regulatory body need to run a web site security certification program
complete with the supporting material to implement it.

Note: This is no trivial task to get right. I would need to ensure I can
commit to completing the work to a good quality. I think this will take
at least 2 months from start to finish to complete but I think is very
important for the industry and for potentially for OWASP. I wanted to
gauge the interest by first posting this.

## Erwin Geirnaert - OWASP Java Project

  - **Executive Summary**:

I would like to help the OWASP Java Project to gather all Java security
related information and to document any domains that lack documentation.

  - **Objectives and Deliverables**:

The main objective I see is to gather all information in one place,
where security experts and developers can find the information they
need. In order to get there, I need to collect all information in the
OWASP Wiki, ask people if they want to donate it to OWASP so that we can
include it as public material, add URLs, white-papers, references to
books, ... And if time permits, write some documentation myself.

One deliverable is the OWASP Top 10 for J2EE applications with clear
examples of vulnerabilities and mitigations.

  - **Why you should be sponsored for the project**:

I have more then 10 years experience in Java and J2EE and the last 6
years I have tested and broke a lot of web applications. I gave also
some very successful J2EE security courses and web security courses. I
spoke at different conferences about application security in Europe. And
I am responsible for the security track at Javapolis, one of the biggest
Jave conferences in Europe. I am the co-founder of ZION SECURITY where
we do security testing, code review, design reviews, training,... I'm
also member of the OWASP Belgium board that started in March 2007.

## Erwin Geirnaert - OWASP WebGoat Solutions Guide

  - **Executive Summary**:

WebGoat is used by a lot of people to learn about web application
security and the different vulnerabilities. But it takes a lot of time
to grasp how the tools like WebScarab work and how to use them
effectively in WebGoat. I propose to create a walkthrough of the lessons
in WebGoat so that people can learn from the solutions, without spoiling
the fun.

  - **Objectives and Deliverables**:

The WebGoat Solutions Guide is a document that can be bundled with
WebGoat. Each lesson contains a detailed solution with screenshots and
tools. I created a PDF with the solution for WebGoat 4.0 but this is too
big to load (15 MB) and is not very practical.

After a discussion with Bruce about this, we think that the solutions
should be made like the existing Lessons Plan so it is easier to
maintain and update when a lesson changes. This means that there will be
documentation folder and an individual solution for each lesson.

  - **Why you should be sponsored for the project**:

I have more then 10 years experience in Java and J2EE and the last 6
years I have tested and broke a lot of web applications. I gave also
some very successful J2EE security courses and web security courses. I
spoke at different conferences about application security in Europe. And
I am responsible for the security track at Javapolis, one of the biggest
Jave conferences in Europe. I am the co-founder of ZION SECURITY where
we do security testing, code review, design reviews, training,... I'm
also member of the OWASP Belgium board that started in March 2007.

## Bunyamin Demir – OWASP WeBekci Project

#### Executive Summary:

Web application firewalls (WAF) are gaining importance among the
information security technologies designed to protect web sites from
attack. WAF solutions prevent attacks that network firewalls and
intrusion detection systems can't and they require no modification of
application source code. ModSecurity [17](http://www.modsecurity.org/)
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

#### Objectives and Deliverables:

  - **Configuration** : Will add all configuration parameter
  - **Rule Generator**: Will write all the Rules in Rule Language
  - **Logging** : Auditlog and debuglog will be added.
  - **Multiple-DB** : Will add PostgreSql and Sqlite support.

#### Why I should be sponsored for the project:

I am involved with OWASP Turkey
[18](http://www.owasp.org/index.php/Turkey) and interested very much in
WAF. Even though this is my first project for OWASP, I am very much
interested in every aspect of ModSecurity. With SpoC007’s support I will
finalize my work on OWASP WeBekci
[19](http://www.owasp.org/index.php/Category:OWASP_WeBekci_Project).

## Eric Sheridan and Dr. Goran Trajkovski - The Scholastic Application Security Assessment Project

### ABSTRACT

One of the major goals of the Open Web Application Security Project is
to educate developers in the field of application software security.
Understanding the risks and threats associated with web application
software is pivotal in building a mature application security process.
While OWASP has made a significant impact in the professional industry,
more time and energy should be focused towards the academic community.
It is an unfortunate fact that most universities do not require a
stringent software security course for their computer science students.
Consequently, most young developers do not have the ability to assess
and mitigate the risks and threats for their own applications. It is for
this reason that we believe the Open Web Application Security Project
should fund an initiative to encourage the adaptation of application
software security methodologies in the academic course curriculum.

The Scholastic Application Security Project is intended to be the first
step towards integrating security requirements in academic course
curriculums. The primary goal of the project is to give students
hands-on experience performing application security assessments using
the tools and documentation found at <http:///www.owasp.org>. The
assessment, lead by an application security professional, will
demonstrate to students how the information and tools found at OWASP can
be used to assess and ultimately increase the overall security posture
of a web application.

This project contributes towards bridging the gap between academia and
industry, by equipping students with hands-on ready-for-the-job-market
skills in the application software securing industry.

### PARTICIPANTS

The Scholastic Application Security Assessment Project requires that
college level students, lead by an application security professional,
perform a security audit on an open source web application using the
tools and information available at OWASP.

::\***Application Security Professional** – Eric Sheridan ([Aspect
Security](http://www.aspectsecurity.com))

::\***Towson University (TU) Partner** – Dr. Goran Trajkovski, Towson
University (http://www.towson.edu)

::\***Students** – Students of TU’s Application Software Security Course
(COSC 458), nominated by the TU Partner

::\***Web Application** – The Open WebMail Project
(http://openwebmail.org/)

### OWASP UTILIZATION

The Scholastic Application Security Assessment Project requires heavy
utilization of existing OWASP tools and utilities. Through this
requirement, the project will illustrate the fact that existing OWASP
resources can be used and heavily relied upon in a professional security
audit. The following is a list of notable OWASP resources whose use will
be documented throughout the assessment:

::\***OWASP Top Ten 2007** - The security critical areas that the
students will assess in the review

::\***OWASP Testing Guide v2** – The primary resource for building
penetration testing cases

::\***OWASP Guide** – The primary resource for technical details
pertaining to a technology and/or vulnerability

::\***OWASP WebScarabNG** – The primary proxy utility used throughout
the assessment

### THE FINAL REPORT

Students are required to follow the principle of “responsible
disclosure” during the course of the security assessment. The
developers of the open source application will be notified if any
significant issues are found. Once the assessment is complete, a final
report will be delivered to the application developers and the
appropriate OWASP Spring of Code personnel. For each finding in the
report, the students will be required to describe how the tools and
information found at OWASP were used in the discovery.

### HOW DOES OWASP BENEFIT?

The Scholastic Application Security Assessment Project is specifically
designed to benefit the OWASP brand:

*The OWASP Community…*

::\*will be provided a case study proving that the resources available
at OWASP can be utilized in an academic environment, that can be later
used in advertising the OWASP efforts to similar programs as the one at
TU.

::\*will be providing students a hands on experience in learning and
testing for the latest web application security threats, thus
potentially enlarging the OWASP community of contributors and
supporters.

::\*will be addressing the need to educate developers in the security
critical areas.

::\*will be seen as offering a professional level service to another
open source project.

::\*will be addressing one of the root causes of application software
insecurity.

### BACKGROUND

**Eric Sheridan:**

::\*Earned a Bachelor’s of Science in Computer Science from Towson
University

::\*Graduate Student in Information Security at Johns Hopkins University

::\*Application Security Engineer at Aspect Security

::\*Lead of the OWASP Stinger Project and the OWASP Validation Project

**Goran Trajkovski, PhD:**

::\*Has been teaching the Application Software Security course for the
Computer Security undergraduate and master-level majors at TU since 2004
(TU has been a Center of Excellence in Information Assurance, designated
by the NSA since 2002).

::\*Assistant professor of Computer and Information Sciences at Towson
University, and Director of its Cognitive Agency and Robotics Lab
(CARoL).

::\*Has lead curricular efforts in integrating application software
security topics throughout the Computer Science and Computer Information
Sciences curriculum

::\*12 years of full time teaching experience in higher ed.

## Boris - OWASP Site Generator

OWASP Site Generator is a great tool, but it could be even better and
more widespread. There’s a lot room for improvements to both its
functionality and user experience. The way I see it, main user needs to
be addressed and specific development objectives for the next release of
OWASP Site Generator would be:

### User Needs

  - Create multiple types of sites easily
  - Track and analyze requests easily
  - Change the look and feel of the resulting sites easily
  - Create sites for multiple web backend technologies easily
  - Learn how to use OWASP Site Generator easily

### Development Objectives

  - Create a vulnerability library that can be used for web services,
    HTML forms, AJAX, etc. instead of having to craft the same attack
    for each
  - Add support for logging of all received requests, as well as
    querying resulting log files
  - "Templatize" the code generation process, so it can support skinning
    of the resulting sites
  - "Templatize" the code generation process, so it can support
    different backend web technologies
  - Fix all significant defects in the current release of OWASP Site
    Generator
  - Redesign the GUI to make it more efficient and user friendly
  - Create a smooth setup program which would install both client and
    server components as effortlessly as possible
  - Write documentation and articles about it
  - Make the development process open to the public and, hopefully,
    driven by its feedback from day one

### Why should I be sponsored for this project

Well, probably because of my past work on AoC (I just hope that won’t be
the reason for me *not* to be sponsored :)

## Boris - OWASP Report Generator

There is no doubt that OWASP Report Generator is a very handy tool for
penetration testers and other security researchers, but it would be even
better if some enhancements were made:

### User Needs

  - More robustness
  - Ease of use (more efficient and intuitive GUI)
  - Automated reporting for some typical (or not so typical) scenarios
  - More documentation
  - More samples

### Development Objectives

  - Redesign the GUI to make it more efficient and user friendly
  - Clean up the code
  - Add functionality to import, execute and create reports for OWASP
    Tiger automated tests
  - Create some samples
  - Create a smooth setup program
  - Write documentation and articles about it
  - Make the development process open to the public and, hopefully,
    driven by its feedback from day one

### Why should I be sponsored for this project

Well, probably because of my past work on AoC (I just hope that won’t be
the reason for me *not* to be sponsored :)

## Boris - OWASP Tiger

OWASP Tiger project is at its very beginning. Some new features are
needed in order for it to become more useful. Here’s a short list:

### User Needs

  - Easier editing of test projects
  - Support for testing sites that require authentication
  - Support for testing sites that require use of cookies
  - An easy way of specifying vulnerability data, ideally an automated
    one
  - More flexible reporting
  - More project templates
  - More documentation

### Development Objectives

  - Add support for cookies
  - Add support for standard authentication schemes
  - Add support for importing vulnerability data from a test definition
    (or a vulnerability library)
  - Make use of OWASP Report Generator for more advanced reports
  - Create a setup program that would install both client and project
    templates and also allow for adding new templates after the initial
    installation
  - Write documentation and articles about it
  - Make the development process open to the public and, hopefully,
    driven by its feedback from day one

### Why should I be sponsored for this project

Well, probably because of my past work on AoC (I just hope that won’t be
the reason for me *not* to be sponsored :)

## Heiko - Web Application Security put into practice

I'm trying to make the OWASP Top Ten and Guide project known in the
programming community, but I understand that clear examples in the
specific programming language and best practices with explanation
educate the best. I'm at the chair for secure software at my university
and I want to contribute practical examples, because I believe not to
teach secure programming is a great oversight in today's education. Not
only the programmers in large companies have to be aware of security
impacts, but also their future employees and their freelance
programmers. I'm with a large organization of freelance programmers,
which I want to make aware of security flaws.

The Ruby on Rails Security project [20](http://www.rorsecurity.info/)
started this year and is the only security initiative for Ruby on Rails.
Ruby is the fastest growing level A programming language, according to
the Tiobe programming community index
[21](http://www.tiobe.com/tpci.htm), partly because of its advertised
simplicity. This is dangerous, as programmers could be enticed to do
cargo cult programming
[22](http://en.wikipedia.org/wiki/Cargo_cult_programming) without
knowing the security impacts. I found several security holes in popular
modules, and even the Rails framework itself generates potentially
insecure code. Nevertheless, Rails provides good means against many of
the OWASP Top Ten security flaws, but I believe these means have to be
popularized much more.

### Objectives and Deliverables

  - Create a security guide to the most popular web server software,
    Apache
      - Installation
      - secure configuration, emphasis on Rails, but not limited to it
      - file system privileges for Rails and Apache
      - anti profiling techniques for Apache
      - Modules and Mod_security configuration

<!-- end list -->

  - Create a security guide to the popular database software, MySQL, as
    practical contribution to the OWASP Top 10 Insecure storage section
      - Installation
      - secure configuration, emphasis on Rails, but not limited to it
      - file system privileges for Rails and MySQL
      - MySQL access restriction techniques
      - encryption methods

<!-- end list -->

  - Ruby on Rails security guide and code examples, with at least the
    following topics:
      - Anti profiling techniques
      - Rails routes security
      - error handling and presentation, as in OWASP Top 10 Improper
        Error Handling
      - OWASP Top 10: XSS in Rails
      - OWASP Top 10: SQL injection in Rails
      - OWASP Top 10: Parameter injection in Rails
      - OWASP Top 10: Session handling in Rails
      - OWASP Top 10: Access control in Rails
      - handling of files
      - integrity
      - encryption and SSL
      - logging flaws
      - Ajax security

<!-- end list -->

  - Code & other
      - means to check the security of MySQL
      - input validation guide, and implement it in Ruby
      - update the poorly documented guide at
        <http://manuals.rubyonrails.com/read/chapter/40> which is the
        only official guide to security
      - usage guide for OWASP tools, also in connection with Rails
      - make the results known in the several communities I'm in
      - if applicable: submit code to Rails for security holes found

### Why I should be sponsored for the project

I have been programming professionally for 10 years and created several
software products, including Internet applications, and I always focused
on security. I am currently graduating university, my thesis is about
web application security. Recently, I started the Ruby on Rails security
project, which is the only security project for Rails. I have always
delivered my work on time, and I believe I have the knowledge to deliver
good quality.

### Long-term vision for the project

Make it available to the community and accept security notices and best
practices from other users to constantly improve it.

### Benefits to the OWASP

  - practical guides on how to put security into practice: the most
    popular web server software Apache and the popular database software
    MySQL
  - if applicable: additional examples and chapters for the OWASP Guide
  - the first and only fully-fledged security guide to a programming
    language and framework which is used by many large companies
  - security awareness of future employees and freelancers
  - more exposure of the OWASP

## Denis – Python Tainted Mode

I am graduate student of Moscow State University, department of
Computational Mathematics and Cybernetics. My graduate work is dedicated
to web-application security. The goal of my graduate work is to combine
dynamic code analysis with penetration testing to provide more precise
analysis. This work will help to find security vulnerabilities in
web-applications. I successfully presented parts of my work at
university conferences.

### My Project

The goal of my project is to create analog of Perl’s Taint Mode for
Python programming language. Taint mode is successfully used in Perl,
PHP, and Ruby to find input validation vulnerabilities in
web-applications (see for ex.
PHPRevent[23](http://dependability.cs.virginia.edu/info/PHPrevent)).
Unfortunately there is no implementation of Taint Mode for Python
language despite of wide spread of Python-based web-applications. Taint
Mode for Python is highly claimed. I plan to modify Python interpreter
and add Taint label propagation. Then I’ll add three configuration
lists:

  - List of sources. All data emanating from sources must be marked
    tainted.
  - List of critical functions, that shouldn’t receive tainted data.
  - List of sanitizing functions that untaints data.

These three lists are dependent on technology that is used between
web-server and web-applications in web server. In my project I plan to
build such lists for mod_python and then broaden for other
technologies. With switched on taint mode web-application will receive
exceptions when critical function receives tainted data.

### Why should I be selected

I have strong mathematical & computer science background. I’m familiar
with research publications on dynamic analysis and with implementation
of taint mode in Perl and PHP (PHPrevent Project). This project is part
of my work at university. It will be made under mentoring of my
scientific advisor. This work is already practically done that’s why I’m
sure I will finish my project in time. I have strong skills in
developing projects with Python, Java, C, C++, and Assembler. Then I
plan to support, develop and enhance my project and increase its quality
with penetration testing.

If you have any questions or would like further information, feel free
to contact me.

Yours faithfully, Denis

## Darren Edmonds - WebScarab NG Security Test Automation

### Background

I am a 28 year old software developer from the UK with a background in
java based web development and application security testing. I have
strong mathematical skills, a degree in software engineering, a SCJP
qualification and 8 years of commercial development experience. I have
created many web based and standalone applications delivering on time
and adhering to common software practices. I'm an avid supporter of open
source software and try to use it whenever possible in a commercial
environment. I've made contributions to the Geotools mapping project,
written a securing tomcat article for OWASP and developed a full
modification for the first person shooter Quake 3.

### Project Details

Having used numerous penetration testing applications I believe there is
a need for an open source application which supports some, or all, of
the features of the more expensive commercial products. I propose to
make WebScarab generate, record, and playback security test cases so
that regression testing is possible. If time permits I would also like
to include some extra automated tests that are not always feasible
during manual testing; searching for backup files (\~, Copy of X),
checking non-authorised access to authorised areas, common and brute
force name directory searching, etc. Perhaps include the ability to read
the test database of other scanning tools such as nikto. I have already
made contact with Rogan Dawes, original WebScarab NG author, to discuss
some initial ideas. I believe it is important that Rogan is consulted
during the initial planning phase to make sure the project keeps to a
set of consistent guidelines.

### Milestones

  - Research regression testing features in other applications
  - Create a functional specification
  - Build testing framework (possible inclusion of scripting language
    for user defined tests)
  - Testing

### Why I Should be Sponsored

I believe I am an ideal candidate to develop the proposed additions to
WebScarab NG, not just because of my qualifications and experience, but
because I plan to use WebScarab NG in my work to help perform the
initial testing of web applications. As well as my own time my current
employer will allocate me a set amount of time to ensure the project
achieves its milestones. The end result will make WebScarab NG a much
more powerful testing tool and will be a great asset to the OWASP
community. With continued development and input from the community I see
no reason why WebScarab NG cannot rival commercial testing application
features, usability, and business benefit. Increasing WebScarab's
features will result in increased community awareness bringing in extra
developers, ensuring continual development and so the cycle starts
again.

## Bernardo - sqlmap

  - **Executive Summary**

[sqlmap](http://sqlmap.sourceforge.net) is an automatic blind SQL
injection tool, developed in python, capable to perform an active
database fingerprint, to enumerate entire remote database and much more.
The aim of this project is to implement a fully functional database
mapper tool which takes advantages of web application programming
security flaws which lead to SQL injection vulnerabilities.

  - **Objectives and Deliverables**
      - Add support for Oracle database management system;
      - Add support to extract database users password hash;
      - Extend inband SQL injection functionality to all other possible
        queries;
      - Add Microsoft SQL Server database fingerprint;
      - Add a fuzzer class with the aim to parse html page looking for
        standard database error messages consequently improving database
        fingerprinting;
      - Add support for SQL injection on HTTP *Cookie* and *User-Agent*
        headers;
      - Add support for query ETA (Estimated Time of Arrival) real time
        calculation;
      - Improve Google dorking support to take advantage of remote hosts
        affected by SQL injection to perform other command line argument
        actions;
      - Improve logging functionality.

<!-- end list -->

  - **Long-term vision for the project**

Make sqlmap available as an easy-to-use enumeration and penetration
testing tool to the OWASP community extending its functionality to
exploit SQL injection vulnerabilities to provide a remote shell on the
affected web application database server when possible. In the long run
I would also like to develop a graphical user interface.

  - **Why I should be sponsored for the project**

I have good python programming skills and some years of experience in
computer networks security. I spent most of the last year researching on
web application insecurity taking over the [sqlmap
development](http://sqlmap.svn.sourceforge.net/viewvc/sqlmap/) since
December 2006. Actually I work as software developer at an information
security company in Italy where I mostly deal with vulnerability
assessment.

## Jim - Best Practices & Countermeasures

### Community

I have been running the Buffalo, NY OWASP chapter since 2004. I have
been President of ISACA WNY since 2005. I have delivered presentations
at Buffalo ISSA, Rochester ISSA, ISACA WNY, and Buffalo OWASP meetings
on the topic of Web Application Security.

### My Project

The Best Practices & Countermeasures project will outline best practices
that should be followed to address/prevent known web application
security issues. The best practices will be divided up into related
sections. For instance, there will be an "Authentication" section that
would have best practices as follows: 1) Require strong passwords 2) For
sensitive sites, require two-factor authentication 3) For intranet
sites, tie authentication into existing authentication directory server,
such as LDAP. 4) Implement account lock-out after 5 failed login
attempts 5) Add a log entry and/or an alert to IDS operators after 5
failed login attempts 6) etc.

Each best practice could also have links to language-specific code
constructs that show how to implement each best practice.

### Long Term

It is my hope that this project can be used not only by developers, but
also by IT auditors and security professionals during audits &
assessments

### Why should I be selected

I have 15 years experience in IT, with 10 years experience in IT
Security. I have a bachelor's degree in Computer Science and
professional experience as a programmer/developer.

## Arshan Dabirsiaghi - OWASP The Anti-Samy Project

My name is Arshan Dabirsiaghi and I am a 25 year old security
consultant. I want to open the door for web sites to allow users to
supply their own HTML without exposing them to cross-site scripting
attacks.

### Background

B.S., M.S. in Computer Science (focus on Information Security)

2.5 years security engineer/consultant experience

4 years of web and systems development

8 years of security hobbying

### Challenge

Many sites today would enjoy the ability to allow users to provide their
own HTML in order to customize their page layout and general user
experience. Because of the concerns regarding XSS, it is generally
thought of as 'too dangerous' to allow them to input any HTML at all.
Sites like MySpace who have been brave enough to provide this
functionality have no standardized, proven solution to validate user
HTML. In many cases, it's easier to disallow everything that looks HTML
or to output encode all user input. Not coincidentally, those sites have
been the targets of complex attacks. Many sites today don't offer this
type of functionality because of concerns for XSS and dangerous HTML.

### Objectives

The first goal is to conduct a survey of existing browsers and compare
their respective behavior regarding JavaScript (both well-formed and
not) inside HTML with regards to W3C specifications

The second goal is to create a software library (versions in both .Net
and J2EE) that can accomplish the following goals:

`- provide an input validation utility that can detect non-obvious JavaScript inside user-provided HTML`
`- provide a filtering utility that can take blocks of HTML and strip any JavaScript inside of it while retaining all formatting-related code`
`- provide these capabilities even when dealing with realistically dirty HTML`
`- build on the mountain of research available for parsing broken HTML`
`- provide feedback information to the user to help them tune their source to fall within acceptable values`
`- provide these capabilities in an API that's simple and portable`
`- utilize an XML engine file that can be used in various language implementations (.Net/J2EE/PHP)`

I envision the project requiring 3 man-months, with a few milestones to
be established at reasonable intervals, such as:

`- 3 months out: Begin browser/W3C survey.`
`- 2 months out: Finish survey and begin development of API.`
`- 1 month  out: Complete initial API in both Java and .Net`
`- Near release: Perform intense QA on API, fix any remaining bugs.`

### Long Term Vision

My goal is to create a peer-reviewed and eventually time-tested solution
for detecting and filtering JavaScript from user input. By doing so, we
can enable web applications to provide users with richer, more
interactive experiences without sacrificing security. This tool will not
only provide an input validation component to sites who are currently
facing this challenge, but it will also act as an enabler to sites who
wished to embrace the new age of user-generated content but were unable
to do so because of the risk of XSS.

## Josh Sweeney - OWASP LiveCD Education Project

### Executive Summary

`   I am proposing a new project that will educate current OWASP LiveCD users and assist in generating more LiveCD users. The education will be conducted by creating documentation and media using popular tutorial techniques such as Challenges, text tutorials, and video tutorials. The tutorials will help guide all types of users through using the OWASP LiveCD and its tools. After the completion of this project we propose that all of the media be added to the LiveCD so that users have a single all encompassing package to expand their knowledge of application security. This project will effectively bring together documentation for many OWASP projects into one deliverable that can be used at conferences, trade shows, and by educators. The key to promoting a live security distribution is helping the community learn to love every aspect of it.`

### Objective

`   The objective is to produce multiple quality instructor led video tutorials and text tutorials that educate users on using the LiveCD and tools within. This will also include in assisting to make sure that the LiveCD is not only an array of tools but a powerful medium for education. `

### Deliverables

`   - 5 Full screen video tutorials on using the LiveCD and the OWASP tools on it. `

`   - 5 Text tutorials using the LiveCD and the OWASP tools on it. `

`   - 3 Guided challenge scenarios that help a user learn more about the LiveCD.`

`   - A Morphix module with all educational data included to be added to the LiveCD.`
`   `
`   Each deliverable will be OWASP branded so that any distribution ( With OWASP approval )of the material will help bring in new OWASP users.`

### Why should the OWASP LiveCD Education Project be sponsored?

`   The LiveCD Education Project should be sponsored because it will help educate current and new users on many OWASP tools in a popular format. Videos are one of the hottest mediums used on the web, the possibilities of reaching people with the deliverables from this project are endless. This can be proven by searching YouTube for BackTrack or by going to other popular security tutorial sites like IronGeek. `

### Why I should be sponsored.

`   I currently operate a website ( SecurityDistro.com ) dedicated towards getting the word out and educating people on using live security distributions. Through managing this site I have developed experience in promoting, educating, and writing about live security distributions. I have a continuing interest as well as a tremendous time investment in helping live security distributions succeed. `

`   Before my current full time position in web application security I worked in a managed security services environment where I managed firewalls, IDS, IPS, and various other security devices for companies of all sizes.`

## NSRAV Security Research Group - Attacks Reference Guide

### Background Information

NSRAV [24](http://nsrav.lsi.usp.br) is a security research center
located at University of Sao Paulo[25](http://www.usp.br), Brazil, with
more than 10 years on the information security field. Our team is formed
by PhDs, MSc, graduate and post-graduate students and security
specialists with GIAC/SANS and CISSP certifications.

We develop research and consulting activities in almost every field of
information security, focused on EHT, Web applications, IDS/IPS and
detection techniques, grid security, among others. The group is leaded
by Leonardo Cavallari Militelli [26](http://www.lsi.usp.br/~leonardo)
and Matteo Nava.

### Our expectations

We recently started contributing to OWASP and we are developing a
Portuguese translated version of Testing guide v2 in order to spread it
out to the ones who has potential language barrier.

The maintenance of attacks and vulnerability information is very close
to our activities. We believe that we have the specific knowledge and
expertise to develop this project.

### Executive Summary

We are proposing that we will research about new types of attacks and
techniques that aim to Web application/server and report all details
about each one. We are intended to explain in details each attack,
classify by severity, likelihood of exploitation and impact (when
possible), cite references and means of circumvent.

The present OWASP Attacks reference guide lists a great quantity of
attacks, but lots of them are lacking explanation and references. For
instances, SQL Injection
[27](http://www.owasp.org/index.php/SQL_Injection) is completely
referenced, while Format string
[28](http://www.owasp.org/index.php/Format_string_attack) has only the
topics but no description at all.

Also, we plan to categorize the attacks according to testing guide
categories, in order to give a better view of the attacks related to
certain test category.

We believe that the Attack reference guide is very important to OWASP
since it describes theoretical and practical all the threats a Web
application can be susceptible, it gives the reason for OWASP existence.

The vulnerability reference guide is important as well and we will be
constantly contributing to maintain it up to date, since it misses lots
of information and references on the items. Also, it has almost 600
vulnerabilities and we are quite sure that there are some redundant or
even out-of-date items.

### Specific activities

As long we will be participating as a group, the activities will be
divided as following steps:

  - Identify all existent attacks at OWASP site.
  - Research new attacks and techniques
  - Create test scenarios and exploitation, in order to acquire
    evidences to be published (when needed)
  - Detail and reference each attacks, with most known and reliable
    sources.

### Long-term vision for the project

We expect that with a worldwide contribution, the Attack and
Vulnerability reference guides can become the most complete and updated
security reference available. Also, we expect to create cross-reference
among OWASP documents, using the same concepts, definitions, and
categories in order to inter-link all the documents.

## Przemyslaw 'rezos' Skowron - Refresh [Attacks](:Category:Attack "wikilink") list

### \* My educational and professional background

I'm 24 year old system administrator/it security specialist with 6 years
experience. Also I'm speaker at many different meetings about IT
Security (e.g. at OWASP Poland Local Chapter in April 2007) and student
Computer Science (last year).

### \* Application security experience

I have 5 years experience in security audits. Mainly applications for
linux/win32 platform, but since 2 years I'm _interested_ web security.
I know many attacks vectors, what and how I can do it with security bug
and how correct (e.g. changes in code, configuration or something else).
In 2004 year I wrote my first article about bugs in code. Currently I
preparing presentation at FIRST\! OWASP Poland Local Chapter Meeting
about "secure programming in practice".

### \* Participation and leadership in open communities

I'm member of ISACA Poland and (I hope so\!) OWASP Poland Local Chapter.

### \* Objectives or ways in which you will meet the goal(s)

1\) flesh out any item complete from
[Attacks](:Category:Attack "wikilink") list 2) complete any item which
is not complete or is blank 3) refresh
[Attacks](:Category:Attack "wikilink") list, everyday is new for new
vectors attacks

### \* Specific activities and who will carry out these activities

Security education for newbie, medium-advanced and advanced people.
Currently mainly via presentation on ISACA Poland meetings. My protector
in this education is Shadow (sorry, I don't know in this moment if I
mind operate his (first/last)name).

### \* Specific deliverables and a rough project schedule so we can track progress

My goals list (3 points) is good for make progress bar. First and second
goals this is base what I want do it. Third goal is a little research
working, but this is what I WANT do it in my life :)

### \* Long-term vision for the project

If [Attacks](:Category:Attack "wikilink") list is complete (9th July) in
cycle on one year this work must be refresh. Very important is update
[Attacks](:Category:Attack "wikilink") list every time when you hired
about new vector attacks. Why? Because when description about this news
vector attacks is not complete, in the next year you don't must making 3
goals, just 2 (first and second). Perfectly when any new item at
[Attacks](:Category:Attack "wikilink") list is develop at moment emerge
or even though max. 3 months for someone wrote it.

### \* Any other reasons why you and your project should be selected

Why I? Because I have experience, skills, goodwill and free time. Why
this project? Because this is strong base for education for any
programmer, administrator and many others professionals. Knowledge
attacks vectors... this is helpful for more secure not only (e-)world.

## EdFinkler - A comprehensive input retrieval/filtering system for PHP

### About Me

I received a Bachelor's Degree in English from Indiana University in
1997. I've been a web developer since 1996, and a PHP developer since
1999. I worked for four years as Supervisor of Web Development at Golden
Dome Media, and have spent my last six years as Web and Security Archive
Administrator for CERIAS, the Center for Education and Research in
Information Assurance and Security (<http://www.cerias.purdue.edu>), at
Purdue University.

I am a member of the PHP Security Consortium (<http://phpsec.org>), and
creator/project lead on PHPSecInfo, a PHP environment security auditing
tool (<http://phpsecinfo.com>). I regularly speak on web application
security issues, and am an advocate of secure programming practices via
CERIAS and as a member of the PHP and larger web development community.

### The state of PHP application development

The state of application development in PHP is worrisome. Reviewing the
NIST NVD data from 2006 reveals that **over 40% of all vulnerabilities
reported were PHP application vulnerabilities** -- not vulnerabilities
in the language itself, but errors in proper coding practice. I believe
that to address the widespread problem of insecure PHP application
development, new development paradigms are required. The typical
approach of easy, direct interaction with input is inherently
problematic, even for a programmer with strong security practices. The
developer should be forced to consider his or her expectations for the
data, and apply appropriate filtering/validation to ensure that those
expectations are correct. For the cases where raw input is required, the
developer should be forced to **demonstrate clear intent**, much moreso
than simply using the assignment operator. This will, I believe, make it
**easier to develop secure applications in PHP**, and **harder to
develop insecure ones**.

### Creating a new paradigm

We have a strong foundation for a new paradigm in Zend_Filter_Input
(<http://funkatron.com/wp/wp-content/ZFI_docs.pdf>), a component of the
Zend Framework developed by PHP security expert Chris Shiflett
(<http://shiflett.org>). Disappointingly, the component was dropped from
the framework, a move I and many others strongly disagreed with. After
some discussions with Chris and others, I feel that the best approach
would be to resurrect Zend_Filter_Input, making it
framework-independent and addressing existing limitations.

### The details and examples

Essentially, this system would act as a sort of "firewall" API between
user input and the rest of the application. By default, the constructor
would take an array, assign it to an internal property, and set the
passed array to NULL. By setting up filter objects from the standard
user input superglobals, developers would be forced to access all data
via the filter system's API. A developer must demonstrate clear intent
in order to get unfiltered data.

#### Usage examples

Note that in these examples, I've used the name "InputFilter" for the
filter system. This will likely change when I can come up with something
snazzier.

    // Typical ZFI-style usage
    $f_post = new InputFilter($_POST);


    // $_POST['searchtext'] == "<strong>hello</strong>";
    $comment = $f_post->noTags('comment');
    // $comment === "hello";
    $comment_raw = $f_post->getRaw('comment');
    //$comment_raw === "<strong>hello</strong>";


    // makePostFilter would be a helper method that retrieves the $_POST array,
    // wraps the data in an InputFilter, and nullifies the $_POST array
    $f_post = InputFilter::makePostFilter();


    // get email
    if ( $email = $f_post->isEmail('email') ) {
          echo "Valid email address";
    } else {
        echo "Not a valid email address";
    }

    // automatically strip all html tags and bbcode tags from POST input.
    // This kind of input restriction would also be configurable via
    // external conf files
    $restrictions = array('noHTML','stripBBCode');
    $f_post = InputFilter::makePostFilter($restrictions);

#### Bootstrap file example

    <?php
        // standard bootstrap file
        require '/path/to/inputfilterclass.php';

        $if = new InputFilter();
        $if->loadConfig('/path/to/configfile/inputfilter.conf');
        $if->buildStandardFilters(); // builds from $_GET, $_POST, $_COOKIE, $_SERVER

        // the make*Filter methods use a singleton pattern to retrieve prebuilt filter objects
        $f_post = $if->makePostFilter();
        $f_get  = $if->makeGetFilter();
        $f_cookie = $if->makeCookieFilter();
        $f_server = $if->makeServerFilter();

        // $_POST, $_GET, $_COOKIE and $_SERVER are now all NULL
        // Only way to access this data is via the $f_* objects

    ?>

#### Key improvements over Zend_Filter_Input

  - Provide retrieval and filtering support for multidimensional arrays
  - Provide solutions for scoping issues (avoid the need for "global"
    keywords everywhere)
  - A variety of helper methods to reduce code verbosity
  - Block deprecated HTTP_\*_VARS and other ways to grab input data
    without filtering
  - Auto-restrictions on input defined programatically or via
    configuration files
  - Compatible with PHP4 and PHP5
  - Self contained; not reliant on external libraries
  - Able to work with a wide variety of frameworks and app
    architectures; easily "pluggable" into any given web app

### Responsibilities

I expect to be responsible for all development and documentation. I will
rely on the expertise of various members of the PHP security community
for input and criticism, and hope to receive advocacy support from them
as well. The development process will be open, and I intend to release
code throughout to gather feedback.

### Development milestones

*Dates assume an April 9th start*

  - April 16th: Untethering the Zend_Filter_Input code from the Zend
    Framework
  - April 23rd: Rewriting PHP5-specific portions to work in PHP4
  - May 1st: Development of approach to address scoping issues (a big
    plus of the $_\* superglobals is that they are always available in
    all scopes automatically)
  - May 3rd: Initial release of code (continues throughout at
    appropriate points)
  - May 10th: Addition of a variety of "helper" methods to make filtered
    input object creation and interaction easier
  - May 20th: Addition of automatic input "restriction" filters
  - July 1st: Addition of input filtering system configuration via
    external config files
  - July 1st: Full API doc generated from phpDoc-style documentation
  - July 9th: Detailed usage documentation, including examples of
    bootstrapping and methods of integration with various frameworks.
    Example source code included.
  - July 9th: PEAR channel for packaged distribution
  - Ongoing: Advocacy. PR via interviews and news items about releases;
    writing articles demonstrating the system for various sources;
    presentations via the web and at major PHP conferences.
  - Ongoing: Work with major PHP app devs and framework devs to
    integrate the system -- or encourage the development of similar
    approaches -- within their projects.

## Caseydk - Security throughout the SDLC

### Educational and professional background

I have a BS in Electrical Engineer which although I rarely use it, I
have been told that I "write code like an engineer". I value simplicity
and functionality and work to refactor regularly to make my code reflect
these principles. I am a core contributor to dotProject - LAMP-based
Project Management System - and prior to starting my own company worked
at the Department of Justice with the SDLC on a daily basis. During my
time there, I provided Independent Verification and Validation, Risk
Management, and Technical Review for various projects related to
internal systems and homeland security. Most of these projects were
inter-Departmental and required the coordination and involvement of
numerous stakeholders from numerous organizations.

### Participation and leadership in open communities

In terms of Open Source, I have been a core contributor to dotProject
since 2004 and have recently joined the Zend Framework project. Within
the dotProject community, I have been a big proponent of ease of use
while simultaneously working to close various issues related to
security, permissions, and general suitability of the system. While this
is simple when you have complete control over your environment, the vast
majority of our community is using shared hosting and therefore we have
to secure the system multiple ways simultaneously to cover every
possibility. My specific contributions were the implementation of
additional permissions types - previously View and Edit were often
confused - and the implementation of .htaccess to lock down all
sub-directories, many extraneous files, and still allow for a variety of
access methods. While I don't consider it perfect, I believe we have
made huge strides in the past year or two.

### The opportunity, challenges, issues or need your proposal addresses

Currently, security across the SDLC is often viewed as an item to
checkoff. While this may have worked in the past where access to a
system required physical presence, it is short-sighted and dangerous in
our currently connected world. The concept of "the seven touchpoints" is
a step forward and offer a model of active security processes and
procedures, but once again, these are often treated as items to checkoff
the list. I propose a research effort to develop and support a
compelling call to action so that organizations see that they must
implement the practices and procedures out of their own best interest.
Recent examples such as the Department of Veterans' Affairs, TJ Maxx,
and many others show that organizations with bad practices put us all at
risk.

### Objectives or ways in which you will meet the goal(s)

I see this effort working out into two major pieces. While there is a
fundamental need to understand the security perspective, there's the
secondary aspect of getting in the mind of an Evil Guy(tm). First, there
is the research and documentation phase. I propose to gather a series of
real-world security policies, operations, and practices. While this in
itself may not be interesting to most, I further propose to supplement
this information with real-world examples of these practices in action
with a focus on the local Federal Agencies and their supporting
organizations. I believe this perspective is something that should
provide for interesting discussion and comparison. Out of these various
policies and actions, I hope to combine this to identify how "real
practices" compare with "best practices" and discuss areas where these
differences do and do not make sense. This portion of the project will
be entirely done by me.

The second and more interesting part of this project is an Abuse Case
Repository (ACR). Many system architects and developers have a single
view of their system: How it's supposed to be used. By having a
repository of Abuse Cases, I hope to provide a one-stop-shop for
nefarious thoughts and practices to get minds rolling and ideas flowing.
Hopefully by seeding this with a number of real-world examples and small
explanatory code snippets, this will encourage other people to make
contributions and suggestions... not only on new and interesting
security problems, but also potential solutions. Yes, this sort of
repository has the ability to be used for evil purposes. In order to
reasonably protect contributors, code snippets would have to be scrubbed
to remove system-identifying variables and information. This effort
would be started by me but would include anyone with information and
ideas to share.

### Specific deliverables and a rough project schedule so we can track progress

Milestones:

  - April 9th - Notification / Kickoff
  - April 23rd - Draft Outline of Document
  - April 28th - Abuse Case Repository (ACR) Design/Draft/RFC
  - April 30th - Gathering information on practices, policies, etc
  - June 1st - ACR Launch
  - June 4th - Evaulate real-world information gathered, determine
    value, usefulness, and targets for completion
  - June 15th - Draft of final report, status report on ACR
  - July 9th - Project "complete"
  - Ongoing - Convincing people to participate in the ACR effort.

### Long-term vision for the project

I believe the most valuable aspect to come out of this project will be
ACR and I see it outliving this effort as time goes on and more
individuals become aware of the risks and challenges they face. Since it
will not solve their problems and simply identify potential holes, I
believe it can only grow as new attack vectors, technologies, and
problems arise. Developing a normalized notation for these risks will be
key in the effort.

### Any other reasons why you and your project should be selected

I believe that my involvement in the local Washington, DC development
community - NoVaLUG, DCLUG, DCPHP, NoVaJUG, NoVaRUG - puts me in a
special position to gather this information. Yes, dome of it can be
found online in various documents, but there are volumes of information
in the hands of the developers and system administrators. This
information will not be classified, sensitive, etc, but may be
considered embarrassing and therefore would will never see the light of
day. In addition, I am active with a number of groups and have
connections to various security researchers who may be able to help seed
and potentially promote the effort.

## Paulo Coimbra: Organize the 'OWASP branding project' and make a 1st pass at the current abuses of the OWASP brand

I propose to give a contribution to the OWASP Branding Project, by
working on the following issues:

1.  Accordingly to the established rules now in place for the
    utilization of the OWASP Brand, I intend:
    1.  To identify the users of the Brand and their pattern of
        utilization;
    2.  To identify cases where misusing occurs: which rules are mostly
        broken and what processes are used to break them;
    3.  To create a typified profile of inadequate utilization of the
        OWASP Brand;
2.  Based on the previous survey, I intend:
    1.  To contribute for the enhancement and stabilization of a
        political and economical concept for the Brand and for what it
        represents in terms of market positioning;
    2.  Having as a base the Brand’s enhanced concept, to establish a
        set of rules whereby the circumstances of use of the Brand are
        objectively controlled and measured.