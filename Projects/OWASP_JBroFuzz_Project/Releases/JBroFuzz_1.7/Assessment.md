<small>[Click here to return to project's main
page](:Category:OWASP_JBroFuzz "wikilink")</small>

## Stable Release Review of the OWASP JBroFuzz Project - Release 1.7

#### Project Leader for this Release

***[Subere](mailto:yiannis@owasp.org)'s Pre-Assessment Checklist:***

{{ Pre-Assessment Questions - Tools | 1. Is this release associated with
a project containing at least the [Project Wiki Page Minimum
Content](Assessing_Project_Health#Project_Wiki_Page_Minimal_Content "wikilink")
information? = Yes; there a lot of information regarding how to use
JBroFuzz, an FAQ section a Help section as well as an online tutorial
that still needs a lot of work\!

| 2. Is your tool licensed under an open source license? = GNU GPL v3

| 3. Is the source code and any documentation available in an online
project repository? = For the source code:
<http://jbrofuzz.svn.sourceforge.net/viewvc/jbrofuzz/>

| 4. Is there working code? = Yes; currently in its 179 revision,
according to the subversion repository.

| 5. Is there a roadmap for this project release which will take it from
Alpha to Stable release? = Yes; most of the roadmap has now being
delivered with the continuous addition of enhancements (e.g. the encoder
window)

| 6. Are the Alpha pre-assessment items complete? = I believe so, yes.

| 7. Is there an installer or stand-alone executable? = Both an
installer and a stand-alone executable as well as a jar standalone
executable.

| 8. Is there user documentation on the OWASP project wiki page? = An
FAQ section and a Help section, as well as an ongoing tutorial guide
that can be found:
<http://www.owasp.org/index.php/OWASP_JBroFuzz_Tutorial>

| 9. Is there an "About box" or similar help item which lists the
following? = Yes, the about box carries version information, production
alias email, the license as well as a disclaimer.

| 10. Is there documentation on how to build the tool from source
including obtaining the source from the code repository? = Yes; using
apache ant and running '\>ant' after the source code has been
downloading. This is also documented on the website.

| 11. Is the tool documentation stored in the same repository as the
source code? = Yes; the faq and help sections are stored in the same
repository as the source code. The java-doc is derived from the source
code. The fuzzing payloads are stored within the repository.

| 12. Are the Alpha and Beta pre-assessment items complete? = I would
say, yes.

| 13. Does the tool include documentation built into the tool? = Yes;
under Help -\> FAQ and Help -\> Topics

| 14. Does the tool include build scripts to automate builds? = Yes;
using apache ant and a standard build.xml file

| 15. Is there a publicly accessible bug tracking system? = Yes.

| 16. Have any existing limitations of the tool been documented? = Yes;
for example running the tool from command line with more memory; running
the jar file in order to pass a SOCKS5 proxy configuration, etc.

}}

#### First Reviewer

***[Matt Tesauro](User:Mtesauro "wikilink")'s Review:***
<small>Ideally, reviewers should be an existing OWASP project leader or
chapter leader.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? = There is an
installer and downloads for Windows (.zip or .msi) as well as a .zip
file for other platforms (Linux, OS X, BSDs, Solaris, etc). The .msi
installer for Windows is very simple, has a wizard, and the usual
expected stuff. For Windows, the installer is very simple and automatic.
For non-Windows, its a matter of unzipping the provided file and running
the .sh script.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page? = Yes. The recently added tutorial is a great
addition. Please consider adding more content in future as time permits.
JBroFuzz can be an intimidating tool for new users so anything you can
do to ease that initial use, the better for your project.

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? = Yes. The window that
opens under Help -\> About has tabs for "About", "License",
"Disclaimer", and "Acknowledgments". Every thing is there and its easy
to find.

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? = Assuming
the target user is familiar with the common build tool for Java (Ant),
then it should be relatively straight forward to build the tool.
However, I'd suggest a minimal INSTALL file be included with the
distribution.

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? = There is a
help directory in svn which includes HTML version of the help files for
the tool. I'd suggest also including a basic README file in the root
directory of the source since most people expect to find such a file
with basic overview type information.

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? = No.

| 7. Does the tool substantially address the application security issues
it was created to solve? = Yes. Its a highly effective HTTP fuzzer with
a ton of existing payloads.

| 8. Is the tool reasonably easy to use? = Yes. This is even more true
since a Tutorial has been created on the OWASP website.

| 9. Does the documentation meet the needs of the tool users and is
easily found? = The tools has a "Help" menu item which includes both
topics and a FAQ. It also has an option to go to the Project website for
further information.

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. = Yes. The tool was easy to build if you
know Ant. See note above about a simple INSTALL file. Though there isn't
a "One-click" build, there is a one-command build which is equivalent in
my mind.

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) = Yes. Both source
and bug tracking are hosted on Sourceforge.

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. = There's not the ability to change the
location JBroFuzz stores its data. This is a minor issue.

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? = Absolutely. In doing the review, I ended up finding some
issues with applications at my day job. After you spend a few minutes
getting used to how it works, you begin to want to fuzz everything.

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? = See my [review
notes](https://docs.google.com/Doc?docid=0ATb3QwFMHCXrZGdubjI3ZHNfNWhkejdkY2Rj&hl=en)
for some general suggestions and observations I noted while reviewing
JBroFuzz. While there is a bunch of stuff on that page, it DOES NOT mean
that JBroFuzz is not of sufficient quality to be rated as Stable in my
opinion. Mostly those are minor tweaks to make a great project a bit
better.

}}

#### Second Reviewer

***[Leonardo Cavallari Militelli](User:Leocavallari "wikilink")'s
Review:***
<small>It is recommended that an OWASP board member or Global Projects
Committee member be the second reviewer on Quality releases. The board
has the initial option to review the project, followed by the Global
Projects Committee.</small>

{{ Assessment Questions - Tools

| 1. Is an installer for the tool available and easy to use? How close
does it reach the goal of a fully automated installer? = Yes, in a form
of Java executable jar file and a MSI Installable package for Windows.

| 2. Is the end user documentation complete, relevant and presented on
the OWASP wiki page? = Yes. I recommend to link the tutorial and FAQ to
main link section on Project Details, while the videos linked on Main
links sections are outdated and do not present the current version.
Also, the tutorial and documentation have gaps to be improved.

|3. Does the tool have an “About box” or similar help item which allows
the end user to get an overview of the state of this tool? Is this
information readily available and easy to find? = Yes

| 4. Does the documentation on building the source provide the necessary
information and detail to allow someone to build the tool? Is there
sufficient detail and information for the target user? Is there any
domain specific knowledge that is assumed and not provided? = No. The
documentation regarding the source code was not found in the wiki, tool
repository (sourceforge), or within the downloadable files. It assumes
that the user already know what's a fuzzer and how to use it.

| 5. Is the tool's documentation available with the source code and
would it readily discoverable by a new user of the tool? = No. The
documentation is only available into the Wiki and doesn't explain how to
build from source code.

| 6. Is there anything missing that is critical enough to keep the
release at a alpha quality? = No.

| 7. Does the tool substantially address the application security issues
it was created to solve? = Yes.

| 8. Is the tool reasonably easy to use? = Yes.

| 9. Does the documentation meet the needs of the tool users and is
easily found? = Yes.

| 10. Do the build scripts work as expected? Can you build the tool? The
goal is a “One-click” build. =

| 11. Is the bug tracking system usable? Is it hosted at the same place
as the source code? (e.g. Google Code, Sourceforge) = Yes, at
Sourceforge

| 12. Have you noted any limitations of the tool that are not already
documented by the project lead. = No.

| 13. Would you consider using this tool in your day to day work
assuming your professional work includes a reason to use this tool? Why
or why not? = Yes, since it helps on fuzzing values during an
application security assessment, thus automatizing attack variants
discovery.

| 14. What, if anything, is missing which would make this a more useful
tool? Is what is missing critical enough to keep the release at a beta
quality? = The tool is doing very well, but I missed documentation about
source code and a more concise user guide. It can go up the ladder for
Release Quality, but I'd like to see a improved documentation when
possible.

}}

__NOTOC__ <headertabs/>