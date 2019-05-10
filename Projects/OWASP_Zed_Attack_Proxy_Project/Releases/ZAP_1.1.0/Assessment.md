<small>[Click here to return to project's main
page](:OWASP_Zed_Attack_Proxy_Project "wikilink")</small>

## Stable Release Review of the OWASP Zed Attack Proxy Project - [Release ZAP 1.1.0](Projects/OWASP_Zed_Attack_Proxy_Project/Releases/ZAP_1.1.0 "wikilink")

#### Project Leader for this Release

***[Psiinon](User:Psiinon "wikilink")'s Pre-Assessment Checklist:***

{{ Pre-Assessment Questions - Tools | 1. Is this release associated with
a project containing at least the [Project Wiki Page Minimum
Content](Assessing_Project_Health#Project_Wiki_Page_Minimal_Content "wikilink")
information? = I believe so

| 2. Is your tool licensed under an open source license? = Yes - Apache
License 2.0, referenced on both
<http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project> and
<http://code.google.com/p/zaproxy/>

| 3. Is the source code and any documentation available in an online
project repository? = Yes -
<http://code.google.com/p/zaproxy/source/checkout>

| 4. Is there working code? = Yes -
<http://code.google.com/p/zaproxy/source/checkout>

| 5. Is there a roadmap for this project release which will take it from
Alpha to Stable release? = Yes -
<http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project#tab=Roadmap>

| 6. Are the Alpha pre-assessment items complete? = I believe so

| 7. Is there an installer or stand-alone executable? = Yes, for
Windows, Linux and Mac OS (being generated now) -
<http://code.google.com/p/zaproxy/downloads/list>

| 8. Is there user documentation on the OWASP project wiki page? = There
is some documentation on the project page
<http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project>, but
this also references the Google Code page which includes the full user
guide: <http://code.google.com/p/zaproxy/wiki/HelpIntro>, the latter is
generated from the java help pages - migrating it to the OWASP wiki
could prove tricky

| 9. Is there an "About box" or similar help item which lists the
following? = Yes - there is an about box which include things like the
license and OWASP project page link. The credits are in the help file
and online here: <http://code.google.com/p/zaproxy/wiki/HelpCredits>

| 10. Is there documentation on how to build the tool from source
including obtaining the source from the code repository? = Yes -
<http://code.google.com/p/zaproxy/wiki/Building>

| 11. Is the tool documentation stored in the same repository as the
source code? = Yes -
<http://code.google.com/p/zaproxy/source/browse/#svn/wiki>

| 12. Are the Alpha and Beta pre-assessment items complete? = I believe
so

| 13. Does the tool include documentation built into the tool? = Yes - a
full help file is included which is also available online:
<http://code.google.com/p/zaproxy/wiki/HelpIntro>

| 14. Does the tool include build scripts to automate builds? = Yes -
<http://code.google.com/p/zaproxy/source/browse/trunk/build/build.xml>

| 15. Is there a publicly accessible bug tracking system? = Yes -
<http://code.google.com/p/zaproxy/issues/list>

| 16. Have any existing limitations of the tool been documented? = Yes -
all known limitations raised as bugs

}}

#### First Reviewer

***[Yiannis](User:Yiannis "wikilink")'s Review:***
<small>Ideally, reviewers should be an existing OWASP project leader or
chapter leader.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? =Yes. A
stand-alone executable exists; it installs the files correctly with the
corresponding shortcuts in place.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page?

# Yes. Pressing F1 triggers the OWASP ZAP User Guide window to appear. The documentation is also at:

<http://code.google.com/p/zaproxy/wiki/HelpReleases1_1_0>

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? =Yes.

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? =Yes. It
took less than 2 minutes to build after import into eclipse.

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? =Yes. Standard
JavaDoc format is also present.

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? =No. This is definately a project that
should be in beta, if not release\!

| 7. Does the tool substantially address the application security issues
it was created to solve? =There is room for improvement around key
functionality that will make the tool unique in terms of the features
that it offers. This is on the roadmap for it's next release.

| 8. Is the tool reasonably easy to use? =Yes. Carrying a port of paros
also helps in this matter.

| 9. Does the documentation meet the needs of the tool users and is
easily found? =Yes.

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. =Yes. A few warning do come back from
javac, but they are minor.

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) =Yes. There is 40 or
some defects on the list, addressed at a priority, etc.

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. =A few in terms of memory requirements
around proxying and spidering. This is more on the side of "know what
you are doing" then "the tool brakes".

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? =Yes. I want to see more functionality though\!

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? =Nothing; this can move to beta.

}}

#### Second Reviewer

***[Markus](User:Dr._Markus_Maria_Miedaner "wikilink")'s Review:***
<small>It is recommended that an OWASP board member or Global Projects
Committee member be the second reviewer on Quality releases. The board
has the initial option to review the project, followed by the Global
Projects Committee.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? =It is easy to
use and installs smoothly. No Problems here.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page? =Sufficient documentation exists.

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? =OK\!

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? =No problems
to compile it within in eclipse - fine\!

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? =JAVADOC

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? =NO

| 7. Does the tool substantially address the application security issues
it was created to solve? =It definitely needs more work - ideas pointing
in an interesting direction can be found on the roadmap

| 8. Is the tool reasonably easy to use? =Yes

| 9. Does the documentation meet the needs of the tool users and is
easily found? =Yes

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. =Yes

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) =Yes (GoogleCode)

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. =Quite memory consuming sometimes

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? =Yes

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? =Not for moving into BETA. For a release - more functionality
would be nice to see.

}}

__NOTOC__ <headertabs/>