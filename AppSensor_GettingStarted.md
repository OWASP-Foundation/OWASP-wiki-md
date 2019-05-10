# Marked for deletion

This page is marked for deletion. All information has been centralized
in the [AppSensor Developer
Guide](http://www.owasp.org/index.php/AppSensor_Developer_Guide)

# Getting Started with AppSensor

The [AppSensor Project](:Category:OWASP_AppSensor_Project "wikilink")
describes an application layer intrusion detection system, both the
concepts involved as well as offering a collection of helpful detection
points to be implemented into your application. This document describes
how to begin using the Java implementation of AppSensor as part of your
application.

*Note: This document assumes you are planning to use ESAPI as your
authentication/authorization system. This is absolutely NOT required by
AppSensor, but there are reference implementations that come with
AppSensor that make this usage simple and it works "out-of-the-box". If
you choose to use some other mechanism to provide these functions,
please also see the documentation regarding [AppSensor Developer
Guide](AppSensor_Developer_Guide "wikilink").*

## Adding AppSensor to your project

#### Dependencies

AppSensor has the following dependencies:

  - OWASP ESAPI Java library
  - JavaMail libraries (activation and mail jar files)
  - Servlet/JSP libraries
  - Logging API library (log4j by default)

-----

#### With Maven

If you use maven as the build system for your application, then adding
AppSensor to your project is very simple and requires 4 basic steps.

1.  Add the following configuration into the **dependencies** section of
    your POM:
    :
        :<dependency>
        :  <groupId>org.owasp.appsensor</groupId>
        :  <artifactId>AppSensor</artifactId>
        :  <version>PUT_YOUR_VERSION_HERE</version>
        :</dependency>
        :
2.  Add the ESAPI jar into your local maven repository manually using
    the **mvn install** command. This will add ESAPI to the project.
    *Note: This process will change in the future once ESAPI is fully
    setup in the central maven repository. At that time, AppSensor's POM
    will add ESAPI as a dependency, and this step will go away.*
3.  Add the **.esapi** folder to your project in a location that ESAPI
    can find it. The easiest way to do this is to add the folder under
    the root of your **src** folder. Additionally, you will need to
    place 3 files in the .esapi folder:
      - ESAPI.properties
      - validation.properties
      - appsensor.properties
4.  Modify the following line in the ESAPI.properties file:
      -

            ESAPI.IntrusionDetector=org.owasp.esapi.reference.DefaultIntrusionDetector

        The line above should be changed to:

            ESAPI.IntrusionDetector=org.owasp.appsensor.intrusiondetection.AppSensorIntrusionDetector
5.  Customize the configuration files listed above (those in the .esapi
    folder) to suit your own project.
6.  **TODO:** Add example appsensor configuration or examples

At this point you should have the project configured to work properly.

-----

#### Without Maven

If you use some mechanism other than maven as the build system for your
application, then adding AppSensor requires downloading and adding all
required libraries to your project manually in addition to the other
basic steps, and this process is outlined below:

1.  Download the libraries described as dependencies above, and add them
    to your project (likely in the **WEB-INF/lib** folder of your
    application).
2.  Add the **.esapi** folder to your project in a location that ESAPI
    can find it. The easiest way to do this is to add the folder under
    the root of your **src** folder. Additionally, you will need to
    place 3 files in the .esapi folder:
      - ESAPI.properties
      - validation.properties
      - appsensor.properties
3.  Modify the following line in the ESAPI.properties file:
      -

            ESAPI.IntrusionDetector=org.owasp.esapi.reference.DefaultIntrusionDetector

        The line above should be changed to

            ESAPI.IntrusionDetector=org.owasp.appsensor.intrusiondetection.AppSensorIntrusionDetector
4.  Customize the configuration files listed above (those in the .esapi
    folder) to suit your own project.

At this point you should have the project configured to work properly.

-----

## Using AppSensor in your project

Once your project is properly configured to use AppSensor, using
AppSensor is very simple. It takes only 2 basic steps: **Intrusion
Detection Code** and **Intrusion Threshold Configuration**.

-----

#### Intrusion Detection Code

Here are a couple of very simple examples.

The following example involves creating an AppSensorException by hand in
your application:

    //This example snippet might be placed on a jsp that handles HTTP 404 errors.
    //When the page is accessed, this code notifies AppSensor that an invalid page request was made.
    //Notice that the exception is created, not thrown

    new AppSensorException("ACE3", "Invalid request", "Attacker is requesting a non-existent (404) page (" + requestedURI + ")");

The following example relies on the AttackDetectorUtils class to create
the exception. This class contains various methods that handle common
detection points.

    //This example snippet might be placed in request handling code that expects a form POST to occur (not a GET, not a PUT, etc).
    //This code notifies AppSensor that an type of HTTP request was made.

    AttackDetectorUtils.verifyValidRequestMethod(request, AttackDetectorUtils.POST);

-----

#### Intrusion Threshold Configuration

Here the salient points to note are that the configuration can vary
depending on what response actions are desired as well as what threshold
is required. Additionally, you have control over these settings and can
tune them to produce the desired effect. These configurations can be set
in the appsensor.properties file in your .esapi folder. *Note: While
these threshold configurations can be set in the ESAPI.properties in the
.esapi folder, it is not recommended for AppSensor so that the
configuration can be kept together in one place. Also note some
thresholds may already be configured for subclasses of ESAPI's
EnterpriseSecurityException in the ESAPI.properties file - please be
aware of that when setting up the configuration for your application.*

Below are two sample threshold configurations for two separate detection
points.

    # http://www.owasp.org/index.php/AppSensor_DetectionPoints#ACE2:_Modifying_Parameters_Within_A_POST_For_Direct_Object_Access_Attempts
    # number of intrusions in a specified segment of time that constitutes the upper threshold - once crossed, it's considered an "attack"
    IntrusionDetector.ACE2.count=3
    # segment of time (in seconds)
    IntrusionDetector.ACE2.interval=3
    # list of actions you want executed in the specified order as the threshold for this intrusion is met - ie. log the first time, logout the user the second time, etc.
    IntrusionDetector.ACE2.actions=log,logout,disable,disableComponent
    # some integer - duration of time to disable
    IntrusionDetector.ACE2.disableComponent.duration=30
    # some measure of time, currently supported are s,m,h,d (second, minute, hour, day)
    IntrusionDetector.ACE2.disableComponent.timeScale=m
    # some integer - duration of time to disable
    IntrusionDetector.ACE2.disableComponentForUser.duration=30
    # some measure of time, currently supported are s,m,h,d (second, minute, hour, day)
    IntrusionDetector.ACE2.disableComponentForUser.timeScale=m

    # http://www.owasp.org/index.php/AppSensor_DetectionPoints#RE3:_GET_When_Expecting_POST
    # number of intrusions in a specified segment of time that constitutes the upper threshold - once crossed, it's considered an "attack"
    IntrusionDetector.RE3.count=3
    # segment of time (in seconds)
    IntrusionDetector.RE3.interval=300
    # list of actions you want executed in the specified order as the threshold for this intrusion is met - ie. log the first time, logout the user the second time, etc.
    IntrusionDetector.RE3.actions=log,logout,disable

-----

This document shows that AppSensor is very simple to configure as well
as to use. Once setup, you simply add detection points to your code and
add and/or modify the appropriate configuration information in the
ESAPI.properties and appsensor.properties files in order to let
AppSensor know your appropriate thresholds for each detection point.
That's it\!

[Category:OWASP AppSensor
Project](Category:OWASP_AppSensor_Project "wikilink")