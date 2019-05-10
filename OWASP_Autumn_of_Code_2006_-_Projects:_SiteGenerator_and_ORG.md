**AoC Candidate:** Mike de Libero

**Project Coordinator:** Dinis Cruz

**Project Progress:** 100% Complete - [Progress
Page](OWASP_Autumn_of_Code_2006_-_Projects:_SiteGenerator_and_ORG_-_Progress "wikilink")

## Background and Motivation

**History Behind Projects** OWASP Report Generator (ORG) and the Site
Generator (SG) were both projects started by Dinis Cruz. ORG was created
as a way for security individuals and teams to have a standard way to
report there findings to their customers. SG was created to tackle two
different issues:

  - A standard way to test web application security scanners
  - A teaching aide / way to demonstrate security issues to people

**Problems to be Addressed** Currently both of these applications need
some polishing. The major functions for both SG and ORG have been
finished. However, there are many issues with the programs from minimal
exception handling to lack of documentation. By creating documentation,
cleaning up the code and adding (or finishing) the remaining features it
will allow for these programs to be assets to the security community.
For SG the current communication architecture relies on shared memory
which limits its use to certain environments this will be changed to
network based communication allowing for it to be used in more
environments.

**Benefit to OWASP Members and Community** OWASP members and the
community will benefit by:

  - [ORG](Owasp_Report_Generator "wikilink")
      - Have a program that can be used to easily report findings to
        their customers
      - A reporting program built specifically with application security
        teams in mind
  - [SG](Owasp_SiteGenerator "wikilink")
      - A program that can be used to help easily teach peers security
        techniques and issues
      - A way to do standard testing for web application security
        scanners
      - A tool that can help confirm people’s competence in security
        areas

## Goals and Deliverables

**Plan of Approach** These programs will be started right away. I will
start to work on any errors that I come across with ORG while working on
the todo list that can be found on the [project
site](Owasp_Report_Generator "wikilink"). For Site Generator I will be
replacing the communication area first and during that time I will fix
errors I find and start the documentation. After the communication area
is done I will get with the project lead to figure out what else needs
to be done.

**Deliverables**

  - ORG source code checked into the OWASP CVS
  - SG source code checked into the OWASP CVS
  - ORG binaries and installers
  - SG binaries and installers
  - Documentation put onto the respective project sites

## Risks and Rewards

**Main Risks** The biggest risk for this project is that the tasks are
not defined for Site Generator so trying to figure out what tasks need
to be finished needs to get scoped out.

**Rewards of Successful Project** A successful project will give the
security community two useful programs that they can use in their day to
day operations in the security field. This will also bolster OWASPs
reputation for creating quality products and being dedicated to
furthering application security.

## Downloads

  - [ORG
    Installer](http://sourceforge.net/project/downloading.php?group_id=64424&use_mirror=osdn&filename=ORG_v0.88.msi)
  - Website installer:
    [SiteGenerator_IIS_Website_Setup.msi](http://umn.dl.sourceforge.net/sourceforge/owasp/SiteGenerator_IIS_Website_Setup_v0.80.msi)
  - Gui Installer:
    [Owasp_SiteGenerator.msi](http://umn.dl.sourceforge.net/sourceforge/owasp/SiteGenerator_GUI_Setup_v0.80.msi)