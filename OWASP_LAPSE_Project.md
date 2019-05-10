# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

## OWASP Lapse Project

![LapseLogo.png](LapseLogo.png "LapseLogo.png") The OWASP Lapse Project
is **LAPSE+: The Security Scanner for Java EE Applications**. **OWASP
LAPSE Project** is an initiative to make available to developers and
auditors a tool for detecting vulnerabilities in Java EE Applications.
The project aims to put at their disposal a tool based on the static
analysis of code, due to the importance and difficulty of this type of
analysis to detect security flaws in Java EE Applications. The
difficulty of this analysis increases when they face applications
consisting of thousands of lines of code or having a complex structure
with many Java classes. Hence, OWASP LAPSE Project offers a tool that
helps the developer and auditor to carry out the static analysis of code
in the most effective and efficient way. The tool that is provided and
gives the name to the project is LAPSE+.

## Introduction

**LAPSE+** is a security scanner for detecting vulnerabilities of
untrusted data injection in Java EE Applications. It has been developed
as a plugin for Eclipse Java Development Environment, working
specifically with Eclipse Helios and Java 1.6 or higher. LAPSE+ is based
on the GPL software LAPSE, developed by [Benjamin
Livshits](http://suif.stanford.edu/~livshits/) as part of the [Griffin
Software Security
Project](http://suif.stanford.edu/~livshits/work/griffin/). This new
release of the plugin developed by [Evalues
Lab](http://www.evalues.es/index.php/en.html) of [Universidad Carlos III
de Madrid](http://www.uc3m.es) provides more features to analyze the
propagation of the malicious data through the application and includes
the identification of new vulnerabilities.

**LAPSE+** is based on the static analysis of code to detect the source
and the sink of a vulnerability. The source of a vulnerability refers to
the injection of untrusted data, e.g. in the parameters of an HTTP
request or a Cookie. The sink of a vulnerability refers to the process
of data modification to manipulate the behaviour of the application,
such as a servlet response or a HTML page. The vulnerability sources can
lead to sinks by simple assignments, method calls or parameters passing.
When it is possible to reach a vulnerability sink from a vulnerability
source then we have a vulnerability in our application.

## Description

![LapsePlusScreenshot.png](LapsePlusScreenshot.png
"LapsePlusScreenshot.png")

**The vulnerabilities detected by LAPSE+** are related to the injection
of untrusted data to manipulate the behavior of the application. This
type of vulnerabilities are the most common in web applications. The
vulnerability categories detected by LAPSE+ are enumerated below:

  - Parameter Tampering.
  - URL Tampering.
  - Header Manipulation.
  - Cookie Poisoning.
  - SQL Injection.
  - Cross-site Scripting (XSS).
  - HTTP Response Splitting.
  - Command Injection.
  - Path Traversal.
  - XPath Injection.
  - XML Injection.
  - LDAP Injection.

**Three steps are needed in LAPSE+** for the detection of this kind of
vulnerabilities:

  - **Vulnerability Source.** The first step involves the detection of
    the points of code that can be source of an attack of untrusted data
    injection.
  - **Vulnerability Sink.** After detecting the points of code that can
    be target of data injection, LAPSE+ identifies the points that can
    propagate the attack and manipulate the behaviour of the
    application.
  - **Provenance Tracker.** Finally, we check if it is *possible to
    reach a Vulnerability Source from a Vulnerability Sink* performing
    the backward propagation through the different assignations. If this
    occurs, *we have a security vulnerability* in our code.

## Licensing

The OWASP Lapse Project is free to use. It is licensed under the GNU
General Public License version 3.0 (GPLv3).

| valign="top" style="padding-left:25px;width:200px;border-right: 1px
dotted gray;padding-right:25px;" |

## What is the OWASP Lapse Project?

The OWASP Lapse Project provides:

  - Static Analysis (code analysis) for Java EE Applications

## Code

LAPSE+ on Google Code <https://code.google.com/p/lapse-plus/>.

## Project Leader

Gregory Disney-Leugers

## Related Projects

  - [OWASP_CISO_Survey](OWASP_CISO_Survey "wikilink")

| valign="top" style="padding-left:25px;width:200px;" |

## Quick Download

  - LAPSE+ can be downloaded at <http://evalues.es/?q=node/14>

## News and Events

  - 2/16/2014 - Gregory Disney-Leugers adopts the OWASP LAPSE Project
  - 4/15/2011 - [LAPSE+](http://evalues.es/?q=node/14) released.
  - 8/23/2006 -
    [LAPSE 2.5.5](http://suif.stanford.edu/~livshits/work/lapse/download.html)
    released.
  - 8/22/2006 - OWASP LAPSE Project Created.

## In Print

This project can be purchased as a print on demand book from Lulu.com

## Classifications

|                                                     |                                                                                              |                                         |                                                                                  |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------- | -------------------------------------------------------------------------------- |
| align="center" valign="top" width="50%" rowspan="2" | ![Owasp-incubator-trans-85.png](Owasp-incubator-trans-85.png "Owasp-incubator-trans-85.png") | align="center" valign="top" width="50%" | ![Owasp-builders-small.png](Owasp-builders-small.png "Owasp-builders-small.png") |
| align="center" valign="top" width="50%"             | ![Owasp-defenders-small.png](Owasp-defenders-small.png "Owasp-defenders-small.png")          |                                         |                                                                                  |
| colspan="2" align="center"                          | ![Cc-button-y-sa-small.png](Cc-button-y-sa-small.png "Cc-button-y-sa-small.png")             |                                         |                                                                                  |
| colspan="2" align="center"                          | ![Project_Type_Files_TOOL.jpg](Project_Type_Files_TOOL.jpg "Project_Type_Files_TOOL.jpg") |                                         |                                                                                  |

|}

# FAQs

  - Q1: What should you do to avoid these vulnerabilities in your
    code?'' - ''How do we protect Web applications from exploits?
    A1: The proper way to deal with these types of attacks is by
    **sanitizing the tainted input.** Please refer to the [OWASP
    Guide](http://www.owasp.org/index.php/OWASP_Guide_Project#tab=Home)
    to find out more about Web Application Security.''

LAPSE+ is inspired by existing lightweight security auditing tools such
as [FlawFinder](http://www.dwheeler.com/flawfinder/). Unlike this tool,
however, LAPSE+ addresses vulnerabilities in Web Applications. LAPSE+ is
not intended as a comprehensive solution for Web Application Security,
but rather as an aid in the code review process. Those looking for more
comprehensive tools are encouraged to look at some of the tools produced
by Fortify or Ounce Labs.

  - Q2
    A2

# Acknowledgements

## Volunteers

The OWASP Lapse Project is developed by a worldwide team of volunteers.
The primary contributors to date have been:

  - Gregory Disney-Leugers

## Others

  - Pablo Martin Perez
  - Jose Maria Sierra

# Road Map and Getting Involved

As of February 2014, the priorities are:

  - We hope you find the OWASP LAPSE Project useful. Please contribute
    to the Project by volunteering for one of the Tasks, sending your
    comments, questions, and suggestions to owasp@owasp.org. To join the
    OWASP LAPSE Project mailing list or view the archives, please visit
    the [subscription
    page.](https://lists.owasp.org/mailman/listinfo/owasp-lapse)

Involvement in the development and promotion of OWASP Lapse Project is
actively encouraged\! You do not have to be a security expert in order
to contribute. Some of the ways you can help:

  - xxx
  - xxx

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:SAMM-CR-2](Category:SAMM-CR-2 "wikilink")