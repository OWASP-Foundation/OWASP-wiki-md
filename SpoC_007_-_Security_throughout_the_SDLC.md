**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: Caseydk

**Project coordinator**: Dinis Cruz

**Project Progress**: 0% Complete, [Progress
Page](SpoC_007_-_Security_throughout_the_SDLC_-_Progress_Page "wikilink")

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

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**