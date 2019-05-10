# Overview

The purpose of this article is to provide guidance around the
installation of OWASP CSRFGuard within a JavaEE web application.
Installation of OWASP CSRFGuard 3 is very straight forward requiring
three simple steps. First, you must copy the Owasp.CsrfGuard.jar file to
your application's classpath. After copying over the OWASP CSRFGuard
library, declare and map the CsrfGuardFilter in your application's
web.xml deployment descriptor. This instructs the application server to
initialize the OWASP CSRFGuard Filter protecting those resources that
match the Filter mapping. Finally, customize the
Owasp.CsrfGuard.properties file as you see fit. You'll need to make sure
you tell CsrfGuardFilter the location of your CSRFGuard properties file
via a JavaEE Filter init-param directive. Please refer to the following
sub-sections for more detailed information on each of the aforementioned
installation steps.

# Copy Owasp.CsrfGuard.jar to Classpath

The first thing you need to do is copy the Owasp.CsrfGuard.jar library
into your classpath. The most common classpath location to place
Owasp.CsrfGuard.jar is within the lib directory of the web application's
WEB-INF folder. OWASP CSRFGuard 3 has no additional dependencies outside
of the traditional JavaEE runtime environment.

# Declare CsrfGuard in Deployment Descriptor

After placing Owasp.CsrfGuard.jar in your application's classpath,
you'll need to declare CsrfGuard context parameters along with a
HttpSessionListener and a Filter. The following web.xml snippet was
extracted from the
[Owasp.CsrfGuard.Test](https://github.com/aramrami/OWASP-CSRFGuard/tree/master/csrfguard-test)
web application:

`       `<listener>
`            `<listener-class>`org.owasp.csrfguard.CsrfGuardServletContextListener`</listener-class>
`       `</listener>
`       `<listener>
`            `<listener-class>`org.owasp.csrfguard.CsrfGuardHttpSessionListener`</listener-class>
`       `</listener>
`       `<context-param>
`             `<param-name>`Owasp.CsrfGuard.Config`</param-name>
`             `<param-value>`WEB-INF/Owasp.CsrfGuard.properties`</param-value>
`       `</context-param>
`       `<context-param>
`             `<param-name>`Owasp.CsrfGuard.Config.Print`</param-name>
`             `<param-value>`true`</param-value>
`       `</context-param>

The code snippet defines two context parameters: Owasp.CsrfGuard.Config
and Owasp.CsrfGuard.Config.Print. The Owasp.CsrfGuard.Config parameter
is required and specifies the location of the CSRFGuard properties file.
CSRFGuard will search for the properties file specified by searching the
following locations in order of appearance: the application's classpath,
a directory accessible by the container, or an arbitrary absolute path.
The Owasp.CsrfGuard.Config.Print parameter is optional and simply
instructs CSRFGuard to display the parsed properties to the application
server log file. Finally, we declare and enable the CSRFGuard
HttpSessionListener with a class name of
org.owasp.csrfguard.CsrfGuardListener. The CsrfGuardListener class is
responsible for consuming context parameters and initializing CsrfGuard
context for all newly created HttpSessions.

Now that we have the CsrfGuard context initialization facilities in
place, we'll need to declare and map the enforcement mechanism:
CsrfGuardFilter. CsrfGuardFilter is responsible for facilitating the
integration of the CsrfGuard object and associated token verification
logic within the JavaEE web application. The following web.xml snippet
was extracted from the
[Owasp.CsrfGuard.Test](https://github.com/aramrami/OWASP-CSRFGuard/tree/master/csrfguard-test)
web application:

`   `<filter>
`       `<filter-name>`CSRFGuard`</filter-name>
`       `<filter-class>`org.owasp.csrfguard.CsrfGuardFilter`</filter-class>
`   `</filter>
`   `<filter-mapping>
`       `<filter-name>`CSRFGuard`</filter-name>` `
`       `<url-pattern>`/*`</url-pattern>
`   `</filter-mapping>

We create a filter with the name of CSRFGuard and specify a classname of
org.owasp.csrfguard.CsrfGuardFilter. At this point, we need to mapp the
CSRFGuard Filter to all resources that we want to protect from attack.
The following web.xml snippet was extracted from the
[Owasp.CsrfGuard.Test](https://github.com/aramrami/OWASP-CSRFGuard/tree/master/Owasp.CsrfGuard.Test)
web application:

`   `<filter-mapping>
`       `<filter-name>`CSRFGuard`</filter-name>
`       `<url-pattern>`/*`</url-pattern>
`   `</filter-mapping>

The aforementioned code snippet maps CSRFGuard to every resource served
by the application server. You can more specifically map the filter
through the use of the "servlet-name" and "url-pattern" directives.

# Configure Owasp.CsrfGuard.properties

The Owasp.CsrfGuard.properties file controls how OWASP CSRFGuard behaves
at runtime. CSRFGuard looks for the file in the following locations in
order: application's classpath, servlet context directory, and current
directory. You are encouraged to make use of the sample
Owasp.CsrfGuard.properties file bundled with CSRFGuard to help
kick-start your deployment efforts. There are various properties
supported by CSRFGuard. At a minimum, you'll want to configure the new
token landing page and the action properties. [Click
here](CSRFGuard_3_Configuration "wikilink") for more information
regarding the configuration of OWASP CSRFGuard.

[Category:OWASP CSRFGuard
Project](Category:OWASP_CSRFGuard_Project "wikilink")