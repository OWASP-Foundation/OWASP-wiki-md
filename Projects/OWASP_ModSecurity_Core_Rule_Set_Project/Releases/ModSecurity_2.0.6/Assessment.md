<small>[Click here to return to project's main
page](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")</small>

## Stable Release Review of the OWASP ModSecurity Core Rule Set Project - Release ModSecurity 2.0.6

#### Project Leader for this Release

***[Ryan Barnett](User:Rcbarnett "wikilink")'s Pre-Assessment
Checklist:***

{{ Pre-Assessment Questions - Tools | 1. Is this release associated with
a project containing at least the [Project Wiki Page Minimum
Content](Assessing_Project_Health#Project_Wiki_Page_Minimal_Content "wikilink")
information? = (answer \#1)

`  1. have an up to date project template with current project information? - YES`
`  2. have a conference style presentation that describes the tool/document in at least 3 slides? - YES`
`  3. have a one sheet overview document about the project? - NO`
`  4. have a link to a working mail list? - YES`
`  5. have a statement of the application security issue the project addresses? - YES`
`  6. have a project roadmap? - YES`
`  7. project leaders and main contributors have a wiki account (with its user page containing contact details about the user and if possible his CV) - YES`

| 2. Is your tool licensed under an open source license? = (answer \#2)

<http://www.gnu.org/licenses/old-licenses/gpl-2.0.html>

| 3. Is the source code and any documentation available in an online
project repository? = (answer \#3)

<http://mod-security.svn.sourceforge.net/viewvc/mod-security/crs/>

| 4. Is there working code? = (answer \#4)

<http://sourceforge.net/projects/mod-security/files/modsecurity-crs/>

| 5. Is there a roadmap for this project release which will take it from
Alpha to Stable release? = (answer \#5)

<http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project_-_Roadmap>

| 6. Are the Alpha pre-assessment items complete? = (answer \#6)

`YES`

| 7. Is there an installer or stand-alone executable? = (answer \#7)

`Not applicable. CRS is not a standalone project that can be installed with an installer.`

| 8. Is there user documentation on the OWASP project wiki page? =
(answer \#8)

`YES`
<http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Installation>
<http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Documentation>

| 9. Is there an "About box" or similar help item which lists the
following? = (answer \#9)

`YES - `<http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Project_Details>

`# Project Name - ModSecurity Core Rule Set (CRS)`
`# Short Description - The Core Rule Set (CRS) provides critical protections against web attacks.  Unlike intrusion detection and prevention systems, which rely on signatures specific to known vulnerabilities, `
`                      the CRS is based on generic rules which focus on attack payload identification in order to provide protection from zero day and unknown vulnerabilities often found in web applications, `
`                      which are in most cases custom coded. `
`# Project Release Lead and contact information (e.g. email address) - Ryan Barnett ryan.barnett@breach.com`
`# Project Release Contributors (if any) - Brian Rectanus`
`# Project Release License - GNU General Public License - Version 2.0`
`# Project Release Sponsors (if any) - Breach Security Labs`
`# Release status and date assessed as Month-Year (e.g. March 2009) - Not Yet Reviewed by OWASP.  An important point to consider is that the CRS is not the typical OWASP project.  Most projects start out as ideas, then move to documentation`
`                                                                     and eventually working code.  The CRS is in the opposite position in that Breach Security Labs developed these rules over the past 3-4 years.  So, we brought a project with`
`                                                                     fully working code that is running on thousands of web servers.  The code itself is well tested.  What was lacking was documentation which as since been updated.`
`# Link to OWASP Project Page - `<http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project>

| 10. Is there documentation on how to build the tool from source
including obtaining the source from the code repository? = (answer \#10)

`Not applicable, as no building is needed.`

| 11. Is the tool documentation stored in the same repository as the
source code? = (answer \#11)

`YES - there is also extensive new documentation/comments inside the files themselves describing the Rule Logic and Reference links.`

| 12. Are the Alpha and Beta pre-assessment items complete? = (answer
\#12)

`YES`

| 13. Does the tool include documentation built into the tool? = (answer
\#13)

`YES - there is also extensive new documentation/comments inside the files themselves describing the Rule Logic and Reference links.`

| 14. Does the tool include build scripts to automate builds? = (answer
\#14)

`Not applicable, as no building is needed.`

| 15. Is there a publicly accessible bug tracking system? = (answer
\#15)

`YES - JIRA Ticket System:`
<https://www.modsecurity.org/tracker/browse/CORERULES>` `

| 16. Have any existing limitations of the tool been documented? =
(answer \#15) }}

#### First Reviewer

***[Ivan Ristic](User:Ivanr "wikilink")'s Review:***
<small>Ideally, reviewers should be an existing OWASP project leader or
chapter leader.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? = Not applicable.
ModSecurity rules cannot be installed with an installer.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page? = Yes.

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? = Not applicable. The
rules do use the SecComponentSignature to identify themselves, which is
the closest thing to having an “About box” in these circumstances.

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? = Not
applicable. Building is not necessary as the rules are evaluated at
runtime.

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? = Yes.

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? = No.

| 7. Does the tool substantially address the application security issues
it was created to solve? = Yes.

| 8. Is the tool reasonably easy to use? = Yes.

| 9. Does the documentation meet the needs of the tool users and is
easily found? = Yes.

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. = Not applicable. No building is necessary.

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) = The bug tracking
system is very much usable. JIRA is pretty much the best tracking system
available. It is hosted elsewhere, but that’s a big plus in this case
(because the code is hosted at SourceForge, and its tracking systems are
all bad.)

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. = No.

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? = Yes. The Core Rules are a substantial piece of work that
provides significant security qualities. Nothing similar is available
elsewhere. It’s easily the best rule set there is.

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? = I don’t believe anything else is required for a stable
release. Of course, the rules can be improved, but that’s a matter of
new research. There are two areas in which I would like to see
improvement: • More involvement from the community. For the rules to
flourish, there must be a sustained community involvement. Ryan is
already very clear about leading the project into this direction (as
demonstrated by his messages on the mailing list). • Transparency. This
is always a difficult goal to achieve with WAF rules. I would like to
see clear justification of every rule in the set, explanation of the
attack it was designed to handle, and explanation of the way in which it
works. In talking to Ryan, it is clear that there already are activities
under way to address both of the above points.

}}

#### Second Reviewer

***[Leonardo Cavallari](User:Leocavallari "wikilink")'s Review:***
<small>It is recommended that an OWASP board member or Global Projects
Committee member be the second reviewer on Quality releases. The board
has the initial option to review the project, followed by the Global
Projects Committee.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? = There's no need
for an installer, just to unpack the package in proper directory. It
could have a more detailed explanation about this process on
Installation page.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page? = Yes, except by installation procedure. Although
the project is about a rule set that only needs to be unpacked, I missed
Mod Security installation and basic configuration procedures or, at
least, relevant links that point to it, since the project by itself
makes no sense without a running Mod Security installation.

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? = Yes. Users can find
latest improvements into CHANGELOG and README files.

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? = There\`s
no need for this information.

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? = Yes.

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? = No.

| 7. Does the tool substantially address the application security issues
it was created to solve? = Yes.

| 8. Is the tool reasonably easy to use? = Yes, there's no need to
operate it, since it runs as an Apache module. The logs are reported in
a format that could be more comprehensive and easy to parse/read without
a proprietary solution.

| 9. Does the documentation meet the needs of the tool users and is
easily found? = Yes.

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. = Yes. The process is based on extract and
copy files to proper directory.

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) = Yes. It uses the
well know JIRA.

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. = Yes, not related to CRS by itself, but
to Mod Security. It was impossible to coexist Mod Security with 2 of 5
real world applications I tested during my review, even with specific
configurations.

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? = Yes, it a very comprehensive rules set to detect/block
webapp attacks.

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? = No, nothing is missing. The Core Rules Set is very mature and
easy to use.

}}

__NOTOC__ <headertabs/>