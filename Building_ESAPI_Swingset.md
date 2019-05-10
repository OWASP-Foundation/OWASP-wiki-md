This page will describe how to build the [ESAPI
Swingset](ESAPI_Swingset "wikilink") in Eclipse.

These instructions assume you already have Eclipse, a JDK, Maven,
m2clipse, and subclipse installed.

## Downloading the current trunk

  - In Eclipse, select File -\> New -\> Project.
  - Select "Checkout projects from SVN" and click "Next."
  - Click "Next" to "Create a new repository location."
  - Enter
    **<http://owasp-esapi-java-swingset.googlecode.com/svn/trunk/webapp>**
    in the URL field and click "Next." If you are a committer, use
    https.
  - Click the top-level entity in the tree, and click "Next."
  - Change the project name if you so desire, and click "Finish."

## Satisfying dependencies

  - After "installing" Maven by extracting it, you must add the bin
    directory to your PATH (System -\> Advanced -\> Environment
    Variables)
  - You must also set the JAVA_HOME environment variable to your JDK
    path (eg. C:\\Program Files\\Java\\jdk1.5.0_22)
  - Now you need to import the ESAPI jar into the Maven repository.
    Download or build the ESAPI jar.
  - Execute: **mvn install:install-file -DgroupId=OWASP
    -DartifactId=ESAPI -Dversion=2.0 -Dpackaging=jar -Dfile=ESAPI.jar**,
    changing the filename if necessary.
  - In Eclipse, go to Window -\> Preferences -\> Maven -\>
    Installations. Click "Add" and select the directory in which you
    extracted maven. This directory should have the bin directory
    inside.
  - Tick the checkbox next to the new entry in the list. Click OK.

## Building the WAR

  - In Eclipse, right-click the Swingset project and go to Run As -\>
    Run Configurations
  - Double click on "Maven Build" in the left-hand pane to create a new
    configuration. Change the name to something like "Swingset Build."
  - For the base directory, click "Browse workspace" and select the
    swingset project.
  - Set the goal to be "package"
  - Click "Run"
  - If the build was successful, the WAR should be in the target
    directory under the project folder

## Getting the Tomcat Bundle

  - Download the tomcat bundle from SVN: **svn checkout
    <http://owasp-esapi-java-swingset.googlecode.com/svn/trunk/tomcat_bundle/>
    tomcat_bundle**
  - Copy the WAR you made in the step above to
    **tomcat_bundle\\apache-tomcat-6.0.18\\webapps\\ROOT.war**
    (changing its name)
  - Do any necessary setup outlined in the README for tomcat, like
    setting JAVA_HOME in the batch file
  - Run the batch file to start the server