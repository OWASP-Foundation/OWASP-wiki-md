**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Subere

**Project coordinator**: Dinis Cruz

**Project Progress**: 100% Complete, [Progress
Page](SpoC_007_-_OWASP_JBroFuzz_Project_-_Progress_Page "wikilink")

## Subere - OWASP JBroFuzz Project

### Overview

JBroFuzz is a stateless network protocol fuzzer that emerged from the
needs of penetration testing. The purpose of this application is to
provide a single, portable application that offers stable cross-platform
network protocol fuzzing capabilities. At the same time, JBroFuzz
attempts to keep the User Interface (UI) as intuitive as possible.

### Fuzzing

As seen by the emphasis given on the subject of fuzzing in the 2007
Testing Guide (v2), network protocol fuzzing serves as a fundamental
cornerstone of application security testing. For this, many different
categories and types of fuzzing have been defined.

### Objectives

JBroFuzz needs to expand and grow in order to cover network fuzzing in a
more complete manner. Its modular implementation allows for the addtion
of new functionality by means of independent tabs. The key tabs proposed
to be added during the spring of code 2007 are

  - Open Source Tab
  - NTLM Brute Force over HTTP/S Tab
  - Pure HTTP/S Fuzzing using HTTPClient
  - Blind SQL Injection Fuzzing Tab

At the same time, the following existing tabs need to be updated and
made more robust (details in next section):

  - TCP Fuzzing tab allowing graph outputs
  - TCP Sniffing tab update thread Agent Queue
  - Update Generators file format
  - Include SOAP and XML fuzzing

This expansion process relates to stabilising code that is presently
included in JBroFuzz, thus allowing it to run for extensive periods of
time (24h+) as well as adding more functionality in terms of the three
new tabs.

### Deliverables

Based on the above, the new code elements that will be added are as
follows:

  - Open Source Tab: Provide the ability to enumerate e-mails from
    newsgroups without breaching google automated search rules
  - NTLM Brute Force over HTTP/S Tab: Provide the ability to enumerate
    NTLM as well as brute over HTTP/S NTLM.
  - Blind SQL Fuzzing Tab Implement a tab that extracts information from
    a blind SQL injection point identified on web server over
    HTTP/HTTPS.

For updating existing code elements that require a partial rewrite, the
following areas of focus are presented in detail:

  - TCP Fuzzing tab allowing graph outputs: Provide the ability to graph
    fuzzing results during a particular session run. This will give the
    ability to integrate and pickup potential fuzzing patterns.
  - TCP Sniffing tab update thread Agent Queue: Update the code of the
    sniffing panel in order to handle threaded agents in a more
  - Update Generators file format: Update the generators file format to
    allow for the parsing and creation of recursive generators.
  - Include SOAP and XML fuzzing: Include an up to date list of SOAP and
    XML fuzzing templates.

Overall, the above two lists of changes should provide sufficient
complexity and output for the spring of code 2007, forming a challenging
implementation project.

### Background

In its short life, the OWASP JBroFuzz Project has attracted the interest
of the online security community with a total of appr. 5000 downloads in
the last months.

Coming from a strong java background (5+ years) I decided to implement
and release JBroFuzz in order to initially simplify penetrations testing
processes that relate to web application and network protocol fuzzing.

I see the spring of code 2007 as a unique opportunity to industrialise
network protocol fuzzing (and in particular HTTP/S fuzzing) within a
single application, residing within OWASP.

### Why I should be sponsored for the project

Centralising fuzzing resources into one application that has the ability
to handle network protocol fuzzing over HTTP and HTTPS in a simple and
intuitive manner forms an area of focus that should not be dismissed in
building secure software applications.

Keep the code platform independent adds a huge advantage.

Receving an OWASP grant from the spring of code 2007 will trigger a
share in the budget with all active participants depending on their
level of involvement. This will be a direct function of the number of
tabs and/or user functionality that they have assisted in implementing.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**