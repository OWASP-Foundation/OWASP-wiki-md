__TOC__

## Understanding the Attack Surface

*“For every input there will be an equal and opposite output (Well sort
of)”*

![Image:Transactional_Analysis.jpg](Transactional_Analysis.jpg
"Image:Transactional_Analysis.jpg")

A major part of actually performing a security code review is performing
an analysis of the attack surface. An application takes inputs and
produces output of some kind. Attacking applications is like using the
streams for input and trying to sail a battleship up them that the
application is not expecting. Firstly, all input to the code needs to be
identified. Input, for example, can be:

  - Browser input
  - Cookies
  - Property files
  - External processes
  - Data feeds
  - Service responses
  - Flat files
  - Command line parameters
  - Environment variables

Exploring the attack surface includes dynamic and static data flow
analysis: Where and when variables are set and how the variables are
used throughout the workflow, how attributes of objects and parameters
might affect other data within the program. It determines if the
parameters, method calls, and data exchange mechanisms implement the
required security.

All transactions within the application need to be identified and
analyzed along with the relevant security functions they invoke. The
areas that are covered during transaction analysis are:

  - Data/Input Validation of data from all untrusted sources
  - Authentication
  - Session Management
  - Authorization
  - Cryptography (Data at rest and in transit)
  - Error Handling /Information Leakage
  - Logging /Auditing
  - Secure Code Environment

## Understand What You Are Reviewing

Many modern applications are developed on frameworks. These frameworks
provide the developer less work to do, as the framework does much of the
“Housekeeping”. The objects developed by the development team shall
extend the functionality of the framework. <u>It is here that the
knowledge of a given framework, and language in which the framework and
application is implemented, is of paramount importance. </u> Much of the
transactional functionality may not be visible in the developer’s code
and handled in “Parent” classes.

The analyst must be aware and knowledgeable of the underlying framework.

### Java

In struts the *struts-config.xml* and the *web.xml* files are the core
points to view the transactional functionality of an application.

<?xml version="1.0" encoding="ISO-8859-1" ?>

`<!DOCTYPE struts-config PUBLIC`
`         "-//Apache Software Foundation//DTD Struts Configuration 1.0//EN"`
`         "`<http://jakarta.apache.org/struts/dtds/struts-config_1_0.dtd>`">`
<struts-config>
` `
` `<form-beans>
`   `<form-bean name="login" type="test.struts.LoginForm" />
` `</form-beans>
` `
` `<global-forwards>
` `</global-forwards>
` `
` `<font color="blue"><action-mappings>
`   `<action
        path="/login"
        type="test.struts.LoginAction" >
`           `<forward name="valid" path="/jsp/MainMenu.jsp" />
`           `<forward name="invalid" path="/jsp/LoginView.jsp" />
`   `</action>
` `</action-mappings></font>

<font color="red"><plug-in className="org.apache.struts.validator.ValidatorPlugIn"></font>
` `<set-property property="pathnames"
 value="/test/WEB-INF/validator-rules.xml, /WEB-INF/validation.xml"/>
</plug-in>
</struts-config>

The *struts-config.xml* file contains the action mappings for each HTTP
request while the *web.xml* file contains the deployment descriptor.

**Example**: The struts framework has a validator engine, which relies
on regular expressions to validate the input data. The beauty of the
validator is that no code has to be written for each form bean. (Form
bean is the Java object which received the data from the HTTP request).
The validator is not enabled by default in struts. To enable the
validator, a plug-in must be defined in the <plug-in> section of
struts-config.xml in Red above. The property defined tells the struts
framework where the custom validation rules are defined (validation.xml)
and a definition of the actual rules themselves (validation-rules.xml).

Without a proper understanding of the struts framework, and by simply
auditing the Java code, one would not see any validation being executed,
and one does not see the relationship between the defined rules and the
Java functions.

The action mappings in Blue define the action taken by the application
upon receiving a request. Here, above we can see that when the URL
contains /login the LoginAction shall be called. From the action
mappings we can see the transactions the application performs when
external input is received.

### .NET

ASP.NET / IIS applications use an optional XML-based configuration file,
named *web.config*, to maintain application configuration settings.This
covers issues such as authentication, authorization, Error pages, HTTP
settings, debug settings, web service settings, etc.

Without knowledge of these files, a transactional analysis would be very
difficult and not accurate.

Optionally, you may provide a file *web.config* at the root of the
virtual directory for a web application. If the file is absent, the
default configuration settings in *machine.config* will be used. If the
file is present, any settings in *web.config* will override the default
settings.

Example of a web.config file:

<authentication mode="Forms">
`  `<forms name="name"
          loginUrl="url"
          protection="Encryption"
          timeout="30" path="/" >
`         requireSSL="true`

|"

`         slidingExpiration="false">`
`     `<credentials passwordFormat="Clear">
`        `<user name="username" password="password"/>
`     `</credentials>
`  `</forms>
`  `<passport redirectUrl="internal"/>
</authentication>

From this config file snippet we can see:

**authentication mode**: The default authentication mode is ASP.NET
forms-based authentication.

'''loginUrl: '''Specifies the URL where the request is redirected for
login if no valid authentication cookie is found.

'''protection: '''Specifies that the cookie is encrypted using 3DES or
DES but DV is not performed on the cookie. Beware of plaintext
attacks\!\!

'''timeout: '''Cookie expiry time in minutes

The point to make here is that many of the important security settings
are not set in the code per se, but in the framework configuration
files. Knowledge of the framework is of paramount importance when
reviewing framework-based applications.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")