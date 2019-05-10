## Status

''' \* Content should provide a link and references to ''' <s> -
SecureTomcat - <http://securetomcat.googlecode.com></s> Released
14/1/2007 Updated 10/7/2014

<https://tomcat.apache.org/tomcat-7.0-doc/security-howto.html>

<https://tomcat.apache.org/tomcat-8.0-doc/security-howto.html> is almost
the same...

## Authors

Darren Edmonds

Jacques Le Roux

## Introduction

Most weaknesses in [Apache Tomcat](http://tomcat.apache.org/) come from
incorrect or inappropriate configuration. It is nearly always possible
to make Tomcat more secure than the default out of the box installation.
What follows documents best practices and recommendations on securing a
production Tomcat server, whether it be hosted on a Windows or Unix
based operating system. *Please note that the section ordering is not a
representation of the section importance.*

## Software Versions

The first step is to make sure you are running the latest stable
releases of software;

  - Java Runtime Environment (JRE) or SDK
  - Tomcat
  - Third-party libraries

Many software projects, including Tomcat and Java, maintain multiple
branches. New features are added to more recent branches, the older
branches receive only bug-fixes and security updates. This allows
developers to advance the software without disrupting production
environments. Be aware of which branch you have deployed, and track new
releases within that branch.

For example, if you are running Tomcat 5.5.**26**, you should watch for
new versions within the 5.5 branch (e.g. 5.5.**27**) and upgrade to this
bug-fix version. If you are content to stick with the Tomcat 5.5 branch
then it is not necessary to upgrade to a new **6.0**.18 version.

You should subscribe to announcement lists for Tomcat, and any other
software you deploy, to stay abreast of new versions released due to
security issues. As soon as a security issue is disclosed, potential
attackers will begin trying to exploit that vulnerability. It is
important that you upgrade your software before an attacker uses the
vulnerability against you.

## Installation of Apache Tomcat

### UNIX

  - Create a tomcat user/group
  - Download and unpack the core distribution (referenced as
    **CATALINA_HOME** from now on)
  - Change **CATALINA_HOME** ownership to tomcat user and tomcat group
  - Change files in **CATALINA_HOME**/conf to be readonly (400)
  - Make sure tomcat user has read/write access to /tmp and write (300 -
    yes, only write/execute) access to **CATALINA_HOME**/logs

### Windows

  - Download the core windows service installer
  - Start the installation, click *Next* and *Agree* to the licence
  - Untick *native*, *documentation*, *examples* and *webapps* then
    click *Next*
  - Choose an installation directory (referenced as **CATALINA_HOME**
    from now on), preferably on a different drive to the OS.
  - Choose an administrator username (NOT admin) and a secure password
    that complies with your organisations password policy.
  - Complete tomcat installation, but do not start service.

### Common

  - Remove everything from **CATALINA_HOME**/webapps (ROOT, balancer,
    jsp-examples, servlet-examples, tomcat-docs, webdav)

<!-- end list -->

  - Remove everything from **CATALINA_HOME**/server/webapps
    (host-manager, manager). Note that it can be useful to keep the
    manager webapp installed if you need the ability to redeploy without
    restarting Tomcat. If you choose to keep it please read the section
    on Securing the Manager WebApp.

<!-- end list -->

  - Remove **CATALINA_HOME**/conf/Catalina/localhost/host-manager.xml
    and **CATALINA_HOME**/conf/Catalina/localhost/manager.xml (again,
    if you are keeping the manager application, do not remove this).

<!-- end list -->

  - Make sure the default servlet is configured **not** to serve index
    pages when a welcome file is not present. In
    **CATALINA_HOME**/conf/web.xml

` `<servlet>
`   `<servlet-name>`default`</servlet-name>
`   `<servlet-class>`org.apache.catalina.servlets.DefaultServlet`</servlet-class>
`   `<init-param>
`     `<param-name>`debug`</param-name>
`     `<param-value>`0`</param-value>
`   `</init-param>
`   `<init-param>
`     `<param-name>`listings`</param-name>
`     `<param-value>**`false`**</param-value>`  `
`   `</init-param>
`   `<load-on-startup>`1`</load-on-startup>
` `</servlet>

  - Remove version string from HTTP error messages by repacking
    **CATALINA_HOME**/server/lib/catalina.jar with an updated
    ServerInfo.properties file. Note that making this change may prevent
    [Lambda Probe](http://www.lambdaprobe.org) (popular Tomcat
    monitoring webapp) to initialise as it cannot determine the Tomcat
    version. A solution to this can be found on the [Lambda Probe
    Forum](http://www.lambdaprobe.org/forum2/message.jspa?messageID=477).
    An alternative to repackaging the JAR is available on the
    [Discussion](https://www.owasp.org/index.php/Talk:Securing_tomcat)
    page.

<!-- end list -->

  -
    unpack catalina.jar

` cd CATALINA_HOME/server/lib`
` jar xf catalina.jar org/apache/catalina/util/ServerInfo.properties`

  -
    update ServerInfo.properties by changing server.info line to
    server.info=Apache Tomcat
    repackage catalina.jar

` jar uf catalina.jar org/apache/catalina/util/ServerInfo.properties`

  -
    remove CATALINA_HOME/server/lib/org (created when extracting the
    ServerInfo.properties file)

<!-- end list -->

  - Replace default error page (default is stacktrace) by adding the
    following into **CATALINA_HOME**/conf/web.xml. The default error
    page shows a full stacktrace which is a disclosure of sensitive
    information. Place the following within the *web-app* tag (after the
    *welcome-file-list* tag is fine). *The following solution is not
    ideal as it produces a blank page because Tomcat cannot find the
    file specified, but without a better solution this, at least,
    achieves the desired result. A well configured web application will
    override this default in
    CATALINA_HOME/webapps/APP_NAME/WEB-INF/web.xml so it won't cause
    problems.*

` `<error-page>
`   `<exception-type>`java.lang.Throwable`</exception-type>
`   `<location>`/error.jsp`</location>
` `</error-page>

  - Rename **CATALINA_HOME**/conf/server.xml to
    **CATALINA_HOME**/conf/server-original.xml and rename
    **CATALINA_HOME**/conf/server-minimal.xml to
    **CATALINA_HOME**/conf/server.xml. The minimal configuration
    provides the same basic configuration, but without the nested
    comments is much easier to maintain and understand. Do not delete
    the original file as the comments make it useful for reference if
    you ever need to make changes - e.g. enable SSL.

<!-- end list -->

  - Replace the server version string from HTTP headers in server
    responses, by adding the server keyword in your Connectors in
    **CATALINA_HOME**/conf/server.xml

` <Connector port="8080" ...`
`             server="Apache" />    `

  - Start Tomcat, deploy your applications into
    **CATALINA_HOME**/webapps and hope it works\!

## Protecting the Shutdown Port

Tomcat uses a port (defaults to 8005) as a shutdown port. What this
means is that to stop all webapps and stop Tomcat cleanly the shutdown
scripts make a connection to this port and send the *shutdown* command.
This is not as huge a security problem as it may sound considering the
connection to the port must be made from the machine running tomcat and
the *shutdown* command can be changed to something other than the string
*SHUTDOWN*. However, it's wise to take the following precautions;

  - if you are running a publicly accessible server make sure you
    prevent external access to the shutdown port by using a suitable
    firewall.
  - change the shutdown command in **CATALINA_HOME**/conf/server.xml
    and make sure that file is only readable by the tomcat user.

` `<Server port="8005" shutdown="ReallyComplexWord">

  - if this is still a big problem for you then check [this
    thread](http://marc.theaimsgroup.com/?l=tomcat-user&m=104400608619118&w=2),
    from the Tomcat mailing list, for alternatives (they all involve
    code customisation though).

## Securing Manager WebApp

  - By default there are no users with the manager role. To make use of
    the manager webapp you need to add a new role and user into the
    **CATALINA_HOME**/conf/tomcat-users.xml file.

` `<role rolename="manager"/>
` `<user username="darren" password="ReallyComplexPassword" roles="manager"/>

  - When you access the password-protected manager webapp, the password
    you enter will be sent over the network in (nearly) plain text, ripe
    for interception. By using an SSL connection instead, you can
    transport the password securely. Fortunately, this is simple to
    accomplish. After configuring an SSL Connector in server.xml (see
    your Tomcat documentation), simply add the following to
    **CATALINA_HOME**/webapps/manager/WEB-INF/web.xml inside of the
    <security-constraint></security-constraint> tags.

`  `<user-data-constraint>
`     `<transport-guarantee>`CONFIDENTIAL`</transport-guarantee>
`  `</user-data-constraint>

  -
    This will force an SSL connection to be used when accessing the
    manager webapp. Plus, with a little more work, the SSL Connector can
    be configured to require a client certificate.

<!-- end list -->

  - Using a
    [valve](http://tomcat.apache.org/tomcat-5.5-doc/config/valve.html)
    to filter by IP or hostname to only allow a subset of machines to
    connect (i.e. LAN machines). Add one of the following within the
    Context tag in
    **CATALINA_HOME**/conf/Catalina/localhost/manager.xml

` `<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="192.168.1.*" />

` `<Valve className="org.apache.catalina.valves.RemoteHostValve"
         allow="*.localdomain.com" />

  - Rename the manager webapp.

<!-- end list -->

  -
    This is 'security through obscurity'. Although widely maligned,
    obscurity is a useful adjunct security measure on a one-off basis. A
    would-be attacker seeking to gain access to the manager webapp will
    look for it in its usual location. By renaming it, you force the
    attacker to guess URLs or assume that it is not installed. It is
    important to note that you are not *relying* upon this obscurity for
    security, but rather using it as a backup measure in case someone
    finds a way around the remote valve filter you have configured as
    described above.

<!-- end list -->

  -
    To rename the manager webapp, decide on the new name (we'll use
    *foobar* in this example), and:

<!-- end list -->

  -   - Move **CATALINA_HOME**/conf/Catalina/localhost/**manager.xml**
        to **CATALINA_HOME**/conf/Catalina/localhost/**foobar.xml**
      - Update the **docBase** attribute within
        **CATALINA_HOME**/conf/Catalina/localhost/**foobar.xml** to
        ${catalina.home}/server/webapps/foobar
      - Move **CATALINA_HOME**/server/webapps/**manager** to
        **CATALINA_HOME**/server/webapps/**foobar**

## Logging

As of tomcat 5.5 logging is now handled by the commons-logging framework
allowing you to choose your preferred logging implementation - log4j or
standard JDK logging. By default the standard JDK logging is used (or a
compatible extension called juli to be more precise), storing daily log
files in **CATALINA_HOME**/logs.

By default additional webapp log entries are added to
**CATALINA_HOME**/logs/catalina.YYYY-MM-DD.log and
System.out/System.err are redirected to
**CATALINA_HOME**/logs/catalina.out. To place webapp log entries in
individual log files create a *logging.properties* file similar to the
following within **CATALINA_HOME**/webapps/*APP_NAME*/WEB-INF/classes
(change the *APP_NAME* value to create a unique file for each webapp)

` handlers = org.apache.juli.FileHandler, java.util.logging.ConsoleHandler`
` org.apache.juli.FileHandler.level = ALL`
` org.apache.juli.FileHandler.directory = ${catalina.base}/logs`
` org.apache.juli.FileHandler.prefix = APP_NAME.`

Further details on logging configuration can be found in the [tomcat
logging
documentation.](http://tomcat.apache.org/tomcat-5.5-doc/logging.html)

If you find you get logging output duplicated in catalina.out, you most
likely have unnecessary entries for *java.util.logging.ConsoleHandler*
in your logging configuration file.

## Encryption

  - SSL for password or other sensitive data exchange (*bordering on
    application security, not specific to tomcat*)
  - SSL for connections (JDBC, LDAP, etc ..)
  - The Tomcat documentation clearly explains how to [enable
    SSL.](http://tomcat.apache.org/tomcat-5.5-doc/ssl-howto.html)

### Sample Configuration - Good Security

Balance between compatibility and security. Supports blocking IO. Tested
on Tomcat 7.0.54 and JVM 1.7.0_60-b19. Supported clients include:

  - Android 4.0.4 and later
  - Chrome 37 and later
  - Firefox 24 and later
  - IE 7 and later EXCEPT on Win XP
  - IE Mobile 10 and later
  - Java 7u25 and later
  - Safari 5.1.9 and later

`   `<Connector port="443"
               protocol="org.apache.coyote.http11.Http11Protocol"
               SSLEnabled="true"
               maxThreads="150"
               scheme="https"
               secure="true"
               keystoreFile="..\ssl\keystore"
               keystorePass="yourpasswordgoeshere"
               clientAuth="false"
               sslProtocol="TLSv1.2"
               sslEnabledProtocols="TLSv1.2,TLSv1.1,TLSv1"
               ciphers="TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384,
                        TLS_ECDH_RSA_WITH_AES_256_GCM_SHA384,TLS_ECDH_ECDSA_WITH_AES_256_GCM_SHA384,
                        TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256,
                        TLS_ECDH_RSA_WITH_AES_128_GCM_SHA256,TLS_ECDH_ECDSA_WITH_AES_128_GCM_SHA256,
                        TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384,TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384,
                        TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA,
                        TLS_ECDH_RSA_WITH_AES_256_CBC_SHA384,TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA384,
                        TLS_ECDH_RSA_WITH_AES_256_CBC_SHA,TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA,
                        TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256,
                        TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA,
                        TLS_ECDH_RSA_WITH_AES_128_CBC_SHA256,TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA256,
                        TLS_ECDH_RSA_WITH_AES_128_CBC_SHA,TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA"
    />

### Sample Configuration - Better Security

Sacrifices compatibility for security. Supports non-blocking IO. Tested
on Tomcat 7.0.54 and JVM 1.7.0_60-b19.

Supports:

  - Android 4.4.2 and later
  - Firefox 32 and later
  - IE 11 and later
  - IE Mobile 11 and later
  - Java 8 b132
  - Safari 7 and later

`   `<Connector port="443"
               protocol="org.apache.coyote.http11.Http11NioProtocol"
               SSLEnabled="true"
               maxThreads="150"
               scheme="https"
               secure="true"
               keystoreFile="..\ssl\keystore"
               keystorePass="yourpasswordgoeshere"
               clientAuth="false"
               sslProtocol="TLSv1.2"
               sslEnabledProtocols="TLSv1.2"
               ciphers="TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384,
                        TLS_ECDH_RSA_WITH_AES_256_GCM_SHA384,TLS_ECDH_ECDSA_WITH_AES_256_GCM_SHA384,
                        TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256,
                        TLS_ECDH_RSA_WITH_AES_128_GCM_SHA256,TLS_ECDH_ECDSA_WITH_AES_128_GCM_SHA256,
                        TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384,TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384,
                        TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA,
                        TLS_ECDH_RSA_WITH_AES_256_CBC_SHA384,TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA384,
                        TLS_ECDH_RSA_WITH_AES_256_CBC_SHA,TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA,
                        TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256,
                        TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA,
                        TLS_ECDH_RSA_WITH_AES_128_CBC_SHA256,TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA256,
                        TLS_ECDH_RSA_WITH_AES_128_CBC_SHA,TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA"
    />

## Java Security

### Running Tomcat with a Security Manager

The default Tomcat configuration provides good protection for most
requirements, but does not prevent a malicious application from
compromising the security of other applications running in the same
instance. To prevent this sort of attack, Tomcat can be run with a
Security Manager enabled which strictly controls access to server
resources. Tomcat documentation has a good section on [enabling the
Security
Manager.](http://tomcat.apache.org/tomcat-5.5-doc/security-manager-howto.html)

It's always a good idea to start tomcat with the "-security" parameter.
This also makes sure (among other things), that a webapplication isn't
able to read/write/execute any file on the local filesystem without
enabling it in the catalina.policy file. This effectively stops web
shells like described
[here](http://www.nruns.com/_downloads/Whitepaper-Hacking-jBoss-using-a-Browser.pdf)
from working.

## Miscellaneous

  - [Tomcat Security FAQ](http://tomcat.apache.org/faq/security.html)

### Using Port 80

If you are on a Windows machine you will be able to change the port
attribute of the connector within the *Catalina* service from 8080 to
80. This allows you to use tomcat directly to serve all requests.
Depending on your requirements it may not be good enough to serve
directly from Tomcat so you may like to consider;

  - Use IIS / Apache running on port 80 and mod_jk to proxy requests to
    Tomcat

On a UNIX machine only root is allowed to run services on ports below
1024 (kernel recompilation can overcome this). It is a very bad idea to
run Tomcat as root, so the options are (in no particular order);

  - Use Apache running on port 80 and mod_jk (or mod_proxy_ajp) to
    proxy requests to Tomcat
  - Run Tomcat as root, but in a chroot jail
  - Use a tool like authbind to enable a non root user to bind to ports
    below 1024
  - Use a port forwarder such as
    [Iptables](http://www.netfilter.org/projects/iptables/index.html) to
    redirect incoming requests from 8080 to 80. This has the
    disadvantage that internal redirects still need to use 8080.
  - Run [Squid](http://www.squid-cache.org/) as a web accelerator in
    front of Tomcat
  - Use JSVC/procrun

Each of the above options **may** bring extra security concerns which
are outside the scope of this document.

### Cleartext Passwords in CATALINA_HOME/conf/server.xml

When configuring a resource, such as a JDBC pool, it is necessary to
include clear text username and password in
CATALINA_HOME/conf/server.xml Best practices advice us never to store
clear text passwords, but the following paragraphs highlight it is very
difficult to avoid.

If one way encryption was used on the password it must be possible for a
database connection to be established using a username and encrypted
password - so the encrypted password is just as valuable as the clear
text one to an attacker.

If two way encryption was used a keyfile is needed which must also live
on the filesystem. To make it more secure a passphase is added to the
keyfile which then has to be stored in the configuration as clear text -
no improvement.

Encoding is security by obscurity and offers no form of protection
(algorithms can be reverse engineered). What encoding does do is make
huge amounts of overhead work - you need to customise Tomcat and the
commons digester it uses to parse the config files. You'd also need a
way to create encoded passwords.

In the case of a JDBC pool what you can do is;

  - make sure the database user only has access to the databases and
    tables they need (also limit rights as necessary).
  - make sure the raw database files are only accessible to the user
    running the database services (e.g. mysql/postgresql user)
  - make sure the Tomcat configuration files are only accessible to the
    tomcat user

## Acknowledgements

The author would like to thank Kris Easter, Michel Prunet and Stephen
More for their valuable input.

[Category:Java](Category:Java "wikilink")