## Summary

This project involving creating a process for integrating the Fortify
Open Review Process into the OWASP project development lifecycle and
working with Fortify to develop and test their new Open Review site at
<http://owasp.fortify.com/>. The [OWASP EU Summit
presentation](https://www.owasp.org/images/c/c9/OWASPEU_SourceReview.ppt)
contains a more detailed summary of the project.

## Goals

The goals of this project were to:

1.  Create a process for integrating the Fortify Open Review into open
    source development, so that source code review can be a required
    step in OWASP development.
2.  Test functionality of the new Fortify Open Review site introduced in
    Summer 2008.
3.  Scan 10 OWASP projects with the Fortify Open Review to verify the
    site's functionality and establish a baseline.
4.  Scan 25 popular open source PHP projects to verify the site's
    ability to handle large scale projects and establish a baseline.

## Process

The purpose of this workflow is to integrate and automate SCA into the
development cycle of open source applications for the sole purpose of
decreasing software vulnerabilities. This effort can, and should, be
supplemented by a manual code review as described in the OWASP Open
Review Project. The workflow diagrams can be found in
[Workflow.zip](https://www.owasp.org/index.php/Image:Workflow_July_11a.zip).
Within the ZIP file, overview.pdf describes the relationships between
the different parts of the workflow. The file start.pdf describes the
first step of the workflow which verifies that the project is an OWASP
project. If it is not then the project is added as a new OWASP project
![Image:Workflow_Draft1.pdf\#file](Workflow_Draft1.pdf#file
"Image:Workflow_Draft1.pdf#file"). Once the project is established as an
OWASP project, it can be added by an OWASP administrator (contact the
project mailing list below to contact an OWASP administrator) to the
Fortify Open Review (reference createProject.pdf).

As described in the [Fortify Open Review
process](http://www.owasp.org/index.php/Category:OWASP_Open_Review_Project_owasp.fortify.com_FAQ),
the Project Lead or Source Code Review Lead can choose between a
continuous evaluation, where the project is checked out from its
repository and the Open Review scan is updated on a weekly basis, or a
one time analysis as part of their usual development process (see
waterfall.pdf and iterative.pdf) after unit testing and prior to final
system testing. The single analysis requires the evaluator to produce
and upload a Fortify FPR scan file, which requires either that the
evaluator uses their own copy of Fortify SCA or contacts an OWASP
administrator via the project mailing list to request a scan. In order
to track project progress over time, single analyses of major project
versions will be maintained on the project web site so that software
vulnerability metrics can be tracked. The continuous evaluation is
automated, does not require the developer have a Fortify SCA license.
There are additional open source static analysis tools that can be used
as part of a project's development lifecycle on a regular basis, such as
FindBugs (see findBugs.pdf) and OWASP Orizon.

Of course, once vulnerabilities are detected, they need to be either
fixed or marked as false positives through the Fortify Open Review site
interface. See the [OWASP Code Review
Guide](http://www.lulu.com/content/1415989) for information on how to
fix common vulnerabilities.

## OWASP Projects Scanned

AntiSamy

CSRFGuard

CSRFTester

DirBuster

JBroFuzz

Lapse

Stinger

Webekci

WebGoat

WebScarab

Non-OWASP projects scanned in MediaWiki, WordPress, and many others. See
[owasp.fortify.com](https://owasp.fortify.com/) for details.

## Get involved

We need OWASP project leaders to submit their projects for review. We
will work with you to upload your project and review the findings, so
that we can get each OWASP project to show zero defects.

Please go to
<https://lists.owasp.org/mailman/listinfo/owasp-scode-review-owasp-projects>
to subscribe to the list to contact us. You can post to the mailing list
by emailing
[1](mailto:owasp-scode-review-owasp-projects@lists.owasp.org).

## People

Project lead: [James Walden](User:Walden "wikilink")

Contributors: Maureen Doyle, Grant Welch, Michael Whelan

Reviewers: Marco Morano, Alex Fry

[Fortify Software](http://www.fortify.com) has generously made their
Source Code Analyzer (SCA) technology available for use by open source
projects at [owasp.fortify.com](http://owasp.fortify.com/).

[Source Code Review OWASP Projects
Project](Category:OWASP_Project "wikilink") [Category:OWASP
Document](Category:OWASP_Document "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Release
Quality Document](Category:OWASP_Release_Quality_Document "wikilink")