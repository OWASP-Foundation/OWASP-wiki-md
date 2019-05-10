## Prerequisites

  - JDK 1.6 or later [download
    here](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
    Note that you need the JDK and not just the JRE.
  - To support the latest versions of Maven, first download Maven
    [here](https://maven.apache.org/download.cgi). (Note: Maven 3.0 or
    later is required.)
  - Eclipse IDE for Java EE Developers 3.3.x or later [download
    here](http://www.eclipse.org/downloads/). Install EGit and m2e
    plug-ins via "Help-\>Install New Software...".
      - EGit Plug-in for Eclipse - Instructions on installing EGit
        plug-in can be found [here](https://eclipse.github.io/)
      - M2E - Maven Integration for Eclipse - You can install the latest
        version from within Eclipse using the following [update
        site](https://eclipse.org/m2e/)
      - Note that other git and Maven plug-in combinations for Eclipse
        are possible.

## Spring Tool Suite

STS is an eclipse distribution from the Spring foundation. If you just
care about getting up and running, and don't care about bloat, download
here: <https://spring.io/tools/sts/all>

On Windows and linux distros, all you should have to do after extracting
the main STS folder, is to navigate into the folder, and double-clicking
the file "STS" or "STS.exe"

It comes pre-packaged with a git plugin (so you can skip those
instructions below) as well as its own versions of Ant and Maven. You
should be able to follow the "EGit" section to clone/import ESAPI in STS
as soon as you have it running. It still has a minimum dependency of
java 1.6 jdk.

Detailed steps:

1\. Right click on the "Package Explorer" pane, and select "import."

2\. Filter on "git" and select "Projects from git."

3\. Select "Clone URI"

4\. Enter the URI: <https://github.com/ESAPI/esapi-java-legacy.git> (or,
if you wish to contribute to ESAPI via "pull requests", the URI where
you "forked" legacy ESAPI to, e.g.
<https://github.com/yourGitHubID/esapi-java-legacy>)

5\. Click "Next."

6\. Click "Next" again.

7\. Select where you want to store the cloned repo, it defaults to
%USERPROFILE%\\git\\esapi-java-legacy on windows.

8\. click "Next."

9\. On the import wizard, cancel.

10\. Right-click again on the package explorer, and click import, filter
on "Maven" and click on "Existing Maven Projects."

11\. Navigate to the folder you created in step 7. Select
"esapi-java-legacy" and click next.

12\. Click finish.

Congratulations\! You are ready to develop\!

## Configuration

  - For Winodws, create an Eclipse shortcut
  - Right-Click your Eclipse shortcut and select Properties
  - At the end of the line that says Target, add -vm "x" where x is the
    location of a JDK (e.g., "C:\\Program Files\\Java\\jdk7\\bin") -
    This step is necessary for the Maven plugin to work. (If you
    installed Eclipse under Linux distro after you already had a JDK
    installed, this probably was already done for you.)
  - Restart Eclipse using the edited shortcut.

## Importing the ESAPI Source

If you choose to use the ESAPI GitHub code,Import Existing Eclipse
projects." follow the instructions at
[ESAPI-Building](ESAPI-Building "wikilink"). Unless you have been added
to the ESAPI project as a contributor, please use the submit fixes using
[Git "pull
requests"](https://help.github.com/articles/using-pull-requests/).

If you are using EGit, as recommended, open Eclipse and:

  - Click *File* -\> *New* -\> *Other....*.
  - From the *Git Folder* select '"Checkout Projects from Git'' (this
    option will only be available if you have a Git plug-in installed)
    and hit *Next \>*.
  - Click the *Create a new repository location* radio button.
  - If you are not listed as a project contributor, insert
    *<https://github.com/ESAPI/esapi-java-legacy.git>* as the URL. If
    you are listed as a project contributor, check the github page for
    the URL to use.
  - Once the directory structure appears in the window, click the URL at
    the top to download everything. Then hit *Next \>*
  - Select your desired project options. For most people, the default
    options should be fine. When finished, click *Next \>*.
  - Select your desired workspace options, then click *Finish*. The
    latest ESAPI source files will then be downloaded to your workspace.
    This may take a few minutes.
  - After the source code is finished downloading, ensure that the
    character type of all source code is UTF-8. In Eclipse, right click
    on the project directory root. At the bottom of the right-click
    list, choose PROPERTIES. From the PROPERTIES window, select the
    RESOURCES section (which is selected by default). Ensure that the
    "Text file encoding" section is set to OTHER-\>UTF 8. If if it is
    not, change it and click APPLY-\>OK.

## Project Setup

Some configuration may be necessary for ESAPI to compile and build on
your system.

ESAPI requires the Java JRE 6 or later.

  - Once Java 6.0+ is installed, open the *Navigator view* in Eclipse.
    If this is currently hidden, from the toolbar click *Window* -\>
    *Show View* -\> *Navigator*.
  - Right-click on your ESAPI project in the Navigator, mouse over
    *Maven* and click *Enable Dependency Management*
      - *Note:* If Maven is not an option when you right-click on the
        project, be sure the Maven plugin for eclipse is installed, as
        described above.
      - *Note:* If *Enable Dependency Management* is not an option,
        dependency management is probably already enabled, So this step
        can be skipped.
  - *Right-click on the ESAPI project root folder* in the Navigator view
    and select *Properties*.
  - From the left column, select *Java Build Path*. Under the
    *Libraries* tab, be sure a JRE or JDK is listed next to *JRE System
    Library*. If there is a red X on next to the JRE, remove the current
    JRE and click *Add Library* and select an alternate JRE. If you are
    having trouble figuring out what version the current JRE is, select
    *Installed JREs* and look at the location to which each version is
    mapped.
  - The Libraries tab should list *JRE System Library* and *Maven
    Dependencies*. If anything else is listed, it is not necessary and
    should be removed. Maven now handles all dependencies.
  - From the left column, select *Java Compiler*. Be sure *Compiler
    compliance level*, *Generated .class files compatibility*, and
    *Source compatibility* are all set to *1.6*. (Note: Most of us use
    JDK 7 or JDK 8 to build ESAPI, but we use '-source 1.6 -target 1.6'
    when we compile to still support really old web applications still
    using JDK 1.6.)
  - Close the properties window.
  - *Right-click the ESAPI project root folder* and select *Refresh*.
  - From the toolbar, select *Project* -\> *Clean..* and select the
    ESAPI project. Click *OK*.
  - If errors remain, select *Maven* again, then *Update Dependencies*.
  - ESAPI should now be compiled.

## Building

Building ESAPI should be easy with the new Maven integration.

Once your environment is set up, as specified above:

  - Right-Click your ESAPI project root folder
  - Select *Run As...*
  - Select *Run Configurations*
  - Double Click "Maven Build" from the options on the left to create a
    new configuration.
  - Name your configuration at the top. This will be for building ESAPI
    without running JUnit tests.
  - The "Base directory" should point to the root of your project
  - The "Goals" field type "package"
  - Any options not mentioned should be left as their default
  - Click "Apply" to save your build configuration
  - Click "Run" to run your configuration

''NOTE: Jars created through building are located in the directory
called "target". ''

## Running Demo App

The ESAPI Demo application has been named *The ESAPI Swingset*. More
information about Swingset is available
[here](http://www.owasp.org/index.php/ESAPI_Swingset).

__NOTOC__

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")