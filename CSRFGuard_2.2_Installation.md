**UNDER DEVELOPMENT**

## Overview

OWASP CSRFGuard 2.2 offers several advantages over previous releases.
One such advantage is the partial automation of the installation
process. The purpose of this document is to describe all of the steps,
both automated and manual, required to successfully install CSRFGuard
within your web application.

## Ant Installation Script

This release contains an Ant build script that includes a "deploy"
target. The purpose of this target is to compile and deploy all of the
necessary OWASP CSRFGuard artifacts in a web application deployment
directory. Successfully running the target requires the developer to
simply modify a couple Ant properties. The following describes the
process of configuring the Ant build script for a fictitious web
application.

**Application Name:** TestApp **Root Location:** /usr/local/www/TestApp

**`Step``   ``1:``   ``Specify``   ``the``   ``location``   ``of``
 ``WEB-INF``   ``Using``   ``the``   ``deploy.webinf``   ``Property`**

The deploy.webinf property should point to the WEB-INF folder of your
J2EE web application. A small number of configuration files will be
deployed to this directory. For our sample application, we would set the
deploy.webinf property to "/usr/local/www/TestApp/WEB-INF" as follows:
<property name="deploy.webinf" location="/usr/local/www/TestApp/WEB-INF" />

**`Step``   ``2:``   ``Specify``   ``the``   ``location``   ``of``
 ``WEB-INF/lib``   ``Using``   ``the``   ``deploy.webinf.lib``
 ``Property`**

The deploy.webinf.lib property should point to the WEB-INF/lib folder of
your J2EE web application. The OWASP CSRFGuard Jar file and dependencies
will be copied to this folder. For our sample application, we would set
the deploy.webinf.lib property as follows:
<property name="deploy.webinf.lib" location="${deploy.webinf}/lib" />

**`Step``   ``3:``   ``Configure``   ``CSRFGuard.properties``   ``For``
 ``Your``   ``Environment`**

The latest CSRFGuard release contains a number of new configuration
operations. For the detailed list of configuration options and their
purpose, please check out the
[CSRFGuard_2.2_Configuration_Manual](CSRFGuard_2.2_Configuration_Manual "wikilink").

**Note:** The Ant installation script assumes the properties file you
wish to use is located at ./conf/CSRFGuard.properties. If you wish to
change this, you must modify the guard.properties Ant property.

**`Step``   ``4:``   ``Run``   ``the``   ``Ant``   ``'deploy'``
 ``Target`**

At this point, you are ready to run the Ant 'deploy' target to copy all
necessary files to your web application. To run the 'deploy' target,
either double-click the 'deploy' target in the 'Ant View' within Eclipse
or execute the command manually as follows: ant deploy.

## Application Deployment Descriptor

Java EE filters provide the ability to intercept, view, and modify both
the request and associated response for the requesting client. In order
for our application to make use of the OWASP CSRFGuard filter, we must
modify the application's web.xml file. First we must declare the filter
and the 'config' initialization parameter. By default (i.e. using the
vanilla Ant 'deploy' script), the configuration file is found at
WEB-INF/CSRFGuard.properties.

The following is a sample entry used to test CSRFGuard in TestApp:

<filter>
`  `<filter-name>`CSRFGuard`</filter-name>
`  `<filter-class>`org.owasp.csrfguard.CSRFGuardFilter`</filter-class>
`    `<init-param>
`      `<param-name>`config`</param-name>
`      `<param-value>`WEB-INF/CSRFGuard.properties`</param-value>
`    `</init-param>
</filter>

After declaring the filter in the descriptor, we must specify what
resources this filter should handle. We can instruct the filter to
handle requests for entire servlets or specific URL patterns. The
following example instructs the OWASP CSRFGuard to handle all requests
to the 'HelloWorld' servlet as well as any requests ending in a .jsp:

<filter-mapping>
` `<filter-name>`CSRFGuard`</filter-name>
` `<servlet-name>`HelloWorld`</servlet-name>
</filter-mapping>

<filter-mapping>
` `<filter-name>`CSRFGuard`</filter-name>
` `<url-pattern>`*.jsp`</url-pattern>
</filter-mapping>

If you wish to have OWASP CSRFGuard monitor requests for every resource,
use the following configuration:

<filter-mapping>
` `<filter-name>`CSRFGuard`</filter-name>
` `<url-pattern>`/*`</url-pattern>
</filter-mapping>

**Note:** By default, all resources monitored by OWASP CSRFGuard are
protected. To modify OWASP CSRFGuard's behavior with respect to your web
application resources, consult the
[CSRFGuard_2.2_Configuration_Manual](CSRFGuard_2.2_Configuration_Manual "wikilink").

**Note:** If you map OWASP CSRFGuard to a resource that does not contain
nor generate HTML (ex. images, Javascript source, etc.), you will may
get runtime exceptions depending on the selected ResponseHandler\!