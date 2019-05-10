## Secure Deployment Configuration

Web applications do not execute in isolation. They typically are
deployed within an application server framework, running within an
operating system on a physical host, within a network.

Secure operating system configuration (also called hardening) is not
typically within the scope of code review. For more information, see the
[Center for Internet Security operating system
benchmarks](http://benchmarks.cisecurity.org/downloads/browse/index.cfm?category=benchmarks.os).

Networks today consist of much more than routers and switches providing
transport services. Filtering switches, VLANs (virtual LANs), firewalls,
WAFs (Web Application Firewall), and various middle boxes (e.g. reverse
proxies, intrusion detection and prevention systems) all provide
critical security services when configured to do so. This is a big
topic, but outside the scope of this web application code review guide.
For a good summary, see the SANS (System Administration, Networking, and
Security) Institute [Critical Control 10: Secure Configurations for
Network Devices such as Firewalls, Routers, and
Switches](http://www.sans.org/critical-security-controls/control.php?id=10).

Application server frameworks have many security related capabilities.
These capabilities are enabled and configured declaratively. Declarative
configuration is usually done via static configuration files, typically
in XML format, but may also be expressed as annotations within the code.

Some security capabilities are accessible from within a Java program.
Programmatic security is done within the web application, using
framework specific or standard Java EE APIs.

### Declarative Configuration

When implemented using the Java Enterprise Edition (JEE) framework, the
[JEE security
model](http://docs.oracle.com/javaee/6/tutorial/doc/bnbwk.html) may be
used. JEE uses a role-based security model, in which access to
application resources is granted based on the security role. The
security role is a logical grouping of principals (authenticated
entities, usually a user), and access is declared by specifying a
*security constraint* on the role.

#### Deployment Descriptor Configuration

The constraints and roles are expressed as *deployment descriptors*
expressed as XML elements. Different types of components use different
formats, or schemas, for their deployment descriptors:

  - Web components may use a web application deployment descriptor in
    the file *web.xml*
  - Enterprise JavaBeans components may use an EJB deployment descriptor
    named *META-INF/ejb-jar.xml*

In summary, the deployment descriptor can define resources (e.g.
servlets accessible via a specific URL), which roles are authorized to
access the resource, and how access is constrained (e.g. via GET but not
POST).

The following example web component descriptor, included in the
"web.xml" file, defines a Catalog servlet, a "manager" role, a SalesInfo
resource within the servlet accessible via GET and POST requests, and
specifies that only users with "manager" role, using SSL and
successfully using HTTP basic authentication should be granted access:

<?xml version="1.0" encoding="ISO-8859-1"?>

<web-app ns="http://java.sun.com/xml/ns/j2ee"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee
    http://java.sun.com/xml/ns/j2ee/web-app_2_5.xsd" version=?2.5?>

`    `<display-name>`A Secure Application`</display-name>
`    `<servlet>
`      `<servlet-name>`catalog`</servlet-name>
`      `<servlet-class>`com.mycorp.CatalogServlet`</servlet-class>
`      `<init-param>
`        `<param-name>`catalog`</param-name>
`        `<param-value>`Spring`</param-value>
`      `</init-param>

`      <!-- Define Security Roles -->`
`      `<security-role-ref>
`        `<role-name>`MGR`</role-name>
`        `
`        `<role-link>`manager`</role-link>
`      `</security-role-ref>
`    `</servlet>

`    `<security-role>
`      `<role-name>`manager`</role-name>
`    `</security-role>
`    `<servlet-mapping>
`      `<servlet-name>`catalog`</servlet-name>
`      `<url-pattern>`/catalog/*`</url-pattern>
`    `</servlet-mapping>

`    <!-- Define A Security Constraint -->`
`    `<security-constraint>

`    <!-- Specify the Resources to be Protected -->`
`    `<web-resource-collection>
`      `<web-resource-name>`SalesInfo`</web-resource-name>
`      `<url-pattern>`/salesinfo/*`</url-pattern>
`      `<http-method>`GET`</http-method>
`      `<http-method>`POST`</http-method>
`     `</web-resource-collection>

`    <!-- Specify which Users Can Access Protected Resources -->`
`    `<auth-constraint>
`      `<role-name>`manager`</role-name>
`    `</auth-constraint>

`    <!-- Specify Secure Transport using SSL (confidential guarantee) -->`
`    `<user-data-constraint>
`      `<transport-guarantee>`CONFIDENTIAL`</transport-guarantee>
`    `</user-data-constraint>
`    `</security-constraint>

`    <!-- Specify HTTP Basic Authentication Method -->`
`    `<login-config>
`      `<auth-method>`BASIC`</auth-method>
`      `<realm-name>`file`</realm-name>
`    `</login-config>
</web-app>

Security roles can also be declared for enterprise Java beans in the
"ejb-jar.xml" file. For example:

` `<ejb-jar>
`    `
`    `<assembly-descriptor>
`        `<security-role>
`            `<description>`The single application role`</description>
`            `<role-name>`TheApplicationRole`</role-name>
`        `</security-role>
`    `</assembly-descriptor>
</ejb-jar>

For beans, however, rather than specifying access to resources within
servlets, access to bean methods is specified. The following example
illustrates several types of method access constraints for several
beans:

<ejb-jar>
`    `<assembly-descriptor>
`        `<method-permission>
`            `<description>`The employee and temp-employee roles may access any`
`                method of the EmployeeService bean `</description>
`            `<role-name>`employee`</role-name>
`            `<role-name>`temp-employee`</role-name>
`            `<method>
`                `<ejb-name>`EmployeeService`</ejb-name>
`                `<method-name>`*`</method-name>
`            `</method>
`        `</method-permission>
`        `<method-permission>
`            `<description>`The employee role may access the findByPrimaryKey,`
`                getEmployeeInfo, and the updateEmployeeInfo(String) method of`
`                the AardvarkPayroll bean `</description>
`            `<role-name>`employee`</role-name>
`            `<method>
`                `<ejb-name>`AardvarkPayroll`</ejb-name>
`                `<method-name>`findByPrimaryKey`</method-name>
`            `</method>
`            `<method>
`                `<ejb-name>`AardvarkPayroll`</ejb-name>
`                `<method-name>`getEmployeeInfo`</method-name>
`            `</method>
`            `<method>
`                `<ejb-name>`AardvarkPayroll`</ejb-name>
`                `<method-name>`updateEmployeeInfo`</method-name>
`                `<method-params>
`                    `<method-param>`java.lang.String`</method-param>
`                `</method-params>
`            `</method>
`        `</method-permission>
`        `<method-permission>
`            `<description>`The admin role may access any method of the`
`                EmployeeServiceAdmin bean `</description>
`            `<role-name>`admin`</role-name>
`            `<method>
`                `<ejb-name>`EmployeeServiceAdmin`</ejb-name>
`                `<method-name>`*`</method-name>
`            `</method>
`        `</method-permission>
`        `<method-permission>
`            `<description>`Any authenticated user may access any method of the`
`                EmployeeServiceHelp bean`</description>
`            `<unchecked/>
`            `<method>
`                `<ejb-name>`EmployeeServiceHelp`</ejb-name>
`                `<method-name>`*`</method-name>
`            `</method>
`        `</method-permission>
`        `<exclude-list>
`            `<description>`No fireTheCTO methods of the EmployeeFiring bean may be`
`                used in this deployment`</description>
`            `<method>
`                `<ejb-name>`EmployeeFiring`</ejb-name>
`                `<method-name>`fireTheCTO`</method-name>
`            `</method>
`        `</exclude-list>
`    `</assembly-descriptor>
</ejb-jar>

`Source: `[`JBoss``   ``Enterprise``   ``Application``   ``Platform``
 ``Common``   ``Criteria``   ``Certification``
 ``5`](https://access.redhat.com/site/documentation/en-US/JBoss_Enterprise_Application_Platform_Common_Criteria_Certification/5/html/Security_Guide/index.html)
`             `[`Security``
 ``Guide`](https://access.redhat.com/site/documentation/en-US/JBoss_Enterprise_Application_Platform_Common_Criteria_Certification/5/html/Security_Guide/index.html)

If XML deployment descriptors are used to secure the application, code
review should include the "web.xml" and "ejb-jar.xml" files to ensure
that access controls are properly applied to the correct roles, and
authentication methods are as expected.

#### Annotations

JEE annotations for security are defined in the
[javax.annotation.security](http://docs.oracle.com/javaee/6/api/javax/annotation/security/package-summary.html)
package. The available annotations are:

`@DeclareRoles`
`@DenyAll - no roles may invoke the method`
`@PermitAll - all roles may invoke the method`
`@RolesAllowed - roles permitted to invoke the method`
`@RunAs - dynamically run the method as a particular role`

For example, the following code snippet allows employees and managers to
add movies to the persistent store, anyone to list movies, but only
managers may delete movies:

`public class Movies {`

`    private EntityManager entityManager;`

`    @RolesAllowed({"Employee", "Manager"})`
`    public void addMovie(Movie movie) throws Exception {`
`        entityManager.persist(movie);`
`    }`

`    @RolesAllowed({"Manager"})`
`    public void deleteMovie(Movie movie) throws Exception {`
`        entityManager.remove(movie);`
`    }`

`    @PermitAll`
`    public List`<Movie>` getMovies() throws Exception {`
`        Query query = entityManager.createQuery("SELECT m from Movie as m");`
`        return query.getResultList();`
`    }`
`}`

Code review should look for such annotations. If present, ensure they
reflect the correct roles and permissions, and are consistent with any
declared role permissions in the "ejb-jar.xml" file.

#### Framework Specific Configuration

Some application server frameworks offer additional or enhanced security
configurations. Consult the documentation for the particular framework
you are using. Information on some of the more common frameworks follow.

##### Apache Tomcat

The [Tomcat
server.xml](http://tomcat.apache.org/tomcat-7.0-doc/security-howto.html#server.xml)
file defines many security related parameters:

  - Server - shutdown port
  - Connectors - maxPostSize, maxParameterCount, server, SSLEnabled,
    secure, ciphers
  - Host - autoDeploy, deployOnStartup, deployXML
  - Context - crossContext, privileged, allowLinking
  - Filter - Tomcat provides a number of *filters* which may be
    configured to incoming requests

Filters are especially powerful, and a code review should validate they
are used unless there is a compelling reason not to. See [Container
Provided
Filters](http://tomcat.apache.org/tomcat-7.0-doc/config/filter.html) for
detailed information.

The server.xml file should be reviewed to ensure security related
parameters are configured as expected.

More guidelines on securely deploying Apache Tomcat can be found in the
[CIS Apache Tomcat 5.5/6.x Server Benchmark
v1.0.0](http://benchmarks.cisecurity.org/downloads/show-single/?file=tomcat.100).

##### Jetty

Jetty adds several security enhancements:

  - Limiting form content
  - Obfuscating passwords

The maximum form content size and number of form keys can be configured
at server and web application level in the "jetty-web.xml" file:

<Configure class="org.eclipse.jetty.webapp.WebAppContext">
` `
`  ...`
`  `
`  `<Set name="maxFormContentSize">`200000`</Set>
`  `<Set name="maxFormKeys">`200`</Set>
</Configure>`    `

<configure class="org.eclipse.jetty.server.Server">
` `
`  ...`
` `
`  `<Call name="setAttribute">
`    `<Arg>`org.eclipse.jetty.server.Request.maxFormContentSize`</Arg>
`    `<Arg>`100000`</Arg>
`   `</Call>
`  `<Call name="setAttribute">
`    `<Arg>`org.eclipse.jetty.server.Request.maxFormKeys`</Arg>
`    `<Arg>`2000`</Arg>
`   `</Call>
</configure>`      `

Jetty also supports the use of obfuscated passwords in jetty XML files
where a plain text password is usually needed. Here's an example setting
the password for a JDBC Datasource with obfuscation (the obfuscated
password is generated by Jetty org.eclipse.jetty.util.security.Password
utility):

<New id="DSTest" class="org.eclipse.jetty.plus.jndi.Resource">
`   `<Arg></Arg>
`   `<Arg>`jdbc/DSTest`</Arg>
`   `<Arg>
`     `<New class="com.jolbox.bonecp.BoneCPDataSource">
`       `<Set name="driverClass">`com.mysql.jdbc.Driver`</Set>
`       `<Set name="jdbcUrl">`jdbc:mysql://localhost:3306/foo`</Set>
`       `<Set name="username">`dbuser`</Set>
`       `**<Set name="password">**
`          `**<Call class="org.eclipse.jetty.util.security.Password" name="deobfuscate">**
`                `**<Arg>`OBF:1ri71v1r1v2n1ri71shq1ri71shs1ri71v1r1v2n1ri7`</Arg>**
`          `**</Call>**
`       `**</Set>**
`       `<Set name="minConnectionsPerPartition">`5`</Set>
`       `<Set name="maxConnectionsPerPartition">`50`</Set>
`       `<Set name="acquireIncrement">`5`</Set>
`       `<Set name="idleConnectionTestPeriod">`30`</Set>
`    `</New>
`  `</Arg>
</New>

##### JBoss AS

JBoss Application Server, like Jetty, allows password obfuscation
(called password masking in JBoss) in its XML configuration files. After
using JBoss password utility to create password mask, replace any
occurrence of a masked password in XML configuration files with the
following annotation:

<annotation>`@org.jboss.security.integration.password.Password`
`                     (securityDomain=MASK_NAME,methodName=setPROPERTY_NAME)`
</annotation>

See [Masking Passwords in XML
Configuration](http://docs.jboss.org/jbosssecurity/docs/6.0/security_guide/html_single/#Masking_Passwords)
in the [JBoss AS Security
Guide](http://docs.jboss.org/jbosssecurity/docs/6.0/security_guide/html_single/).

##### Oracle WebLogic

WebLogic server supports additional deployment descriptors in the
"weblogic.xml" file:

  - externally-defined - role to principal mappings are externally
    defined in WebLogic Admin Console
  - run-as-principal-name - assign a principal to a role when running as
    that role
  - run-as-role-assignment - contains the run-as-principal-name
    descriptor
  - security-permission - contains security-permission-spec descriptor
  - security-permission-spec - specify application permissions as per
    [Java policy file
    syntax](http://docs.oracle.com/javase/1.5.0/docs/guide/security/PolicyFiles.html#FileSyntax)
  - security-role-assignment - explicitly assign principals to a role

More information on WebLogic additional deployment descriptors may be
found at [weblogic.xml Deployment
Descriptors](http://docs.oracle.com/cd/E11035_01/wls100/security/thin_client.html#wp1046262).

For general guidelines on securing web applications running within
WebLogic, see [Programming WebLogic
Security](http://docs.oracle.com/cd/E11035_01/wls100/security/) and the
NSA's [BEA WebLogic Platform Security
Guide](http://www.nsa.gov/ia/_files/webs/I33-004R-2005.pdf).

##### Microsoft IIS

Microsoft Internet Information Server is not based on a JEE framework.
Security features can be configured in IIS using the Web.config
(application level) or ApplicationHost.config (server level) file, in
the \<system.webServer\><security> section. The types of features that
may be configured include:

  - Permitted authentication methods
  - Authorization rules
  - Request filters and limits
  - Use of SSL
  - Source IP address filtering

The Web.config and ApplicationHost.config files should be included in
code review. The \<system.webServer\><security> sections should be
reviewed to ensure all security configuration is as expected.

For guidelines on securing the overall configuration of Microsoft IIS,
see the [CIS Microsoft IIS 7 Benchmark
v1.3.0](http://benchmarks.cisecurity.org/downloads/show-single/?file=iis7.130).

###### Authentication Methods

IIS supports basic, client certificate, digest, IIS client certificate,
and Windows authentication methods. It is configured in the
\<system.webServer\><security><authentication> section. The following
example disables Anonymous authentication for a site named MySite, then
enables both Basic authentication and Windows authentication for the
site:

<location path="MySite">
`   <system.webServer>`
`      `<security>
`         `<authentication>
`            `<anonymousAuthentication enabled="false" />
`            `<basicAuthentication enabled="true" defaultLogonDomain="MySite" />
`            `<windowsAuthentication enabled="true" />
`          `</authentication>
`      `</security>
`   </system.webServer>`
</location>

###### Authorization

IIS authorization configuration allows specification of users access to
the site or server. It is configured in the
\<system.webServer\><security><authorization> section. The following
example removes the default IIS authorization settings, which allows all
users access to Web site or application content, and then configures an
authorization rule that allows only users with administrator privileges
to access the content:

<configuration>
`   <system.webServer>`
`      `<security>
`         `<authorization>
`            `<remove users="*" roles="" verbs="" />
`            `<add accessType="Allow" users="" roles="Administrators" />
`         `</authorization>
`      `</security>
`   </system.webServer>`
</configuration>

###### Request Filters and Limits

IIS supports filtering, including enforcing limits, on incoming HTTP
requests. The following may be configured:

  - denyUrlSequences - list of prohibited URL patterns
  - fileExtensions - allowed or prohibited file extensions
  - hiddenSegments - URLs that cannot be browsed
  - requestLimits - URL, content, query string, and HTTP header length
    limits
  - verbs - allowed or prohibited verbs
  - alwaysAllowedUrls - URLs always permitted
  - alwaysAllowedQueryStrings - query strings always allowed
  - denyQueryStringSequences - prohibited query strings
  - filteringRules - custom filtering rules

It is configured in the \<system.webServer\><security><requestFiltering>
section. The following example

  - Denies access to two URL sequences. The first sequence prevents
    directory transversal and the second sequence prevents access to
    alternate data streams.
  - Denies access to unlisted file name extensions and unlisted HTTP
    verbs.
  - Sets the maximum length for a URL to 2KB and the maximum length for
    a query string to 1KB.

<configuration>
`   <system.webServer>`
`      `<security>
`         `<requestFiltering>
`            `<denyUrlSequences>
`               `<add sequence=".." />
`               `<add sequence=":" />
`            `</denyUrlSequences>
`            `<fileExtensions allowUnlisted="false" />
`            `<requestLimits maxUrl="2048" maxQueryString="1024" />
`            `<verbs allowUnlisted="false" />
`         `</requestFiltering>
`      `</security>
`   </system.webServer>`
</configuration>

###### Use of SSL

IIS allows specifying whether SSL is supported, is required, whether
client authentication is supported or required, and cipher strength. It
is configured in the \<system.webServer\><security><access> section. The
following example specifies SSL as required for all connections to the
site MySite:

<location path="MySite">
`   <system.webServer>`
`      `<security>
`         `<access sslFlags="ssl">
`      `</security>
`   </system.webServer>`
</location>

###### Source IP address filtering

IIS allows restrictions on source IP addresses or DNS names. It is
configured in the \<system.webServer\><security><ipSecurity> section.
The following example denies access to the IP address 192.168.100.1 and
to the entire 169.254.0.0 network:

<location path="Default Web Site">
`   <system.webServer>`
`      `<security>
`         `<ipSecurity>
`            `<add ipAddress="192.168.100.1" />
`            `<add ipAddress="169.254.0.0" subnetMask="255.255.0.0" />
`         `</ipSecurity>
`      `</security>
`   </system.webServer>`
</location>

Detailed information on IIS security configuration can be found at [IIS
Security
Configuration](http://www.iis.net/configreference/system.webserver/security).
Specific security feature configuration information can be found at
[Authentication](http://www.iis.net/configreference/system.webserver/security/authentication),
[Authorization](http://www.iis.net/configreference/system.webserver/security/authorization),
[SSL](http://www.iis.net/configreference/system.webserver/security/access#001),
[Source
IP](http://www.iis.net/configreference/system.webserver/security/ipsecurity),
[Request
Filtering](http://www.iis.net/configreference/system.webserver/security/requestfiltering#005),
and [Custom Request
Filtering.](http://www.iis.net/configreference/system.webserver/security/requestfiltering/filteringrules)

### Programmatic Configuration

#### JEE

The JEE API for programmatic security consists of methods of the
EJBContext interface and the HttpServletRequest interface. These methods
allow components to make business-logic decisions based on the security
role of the caller or remote user (there are also methods to
authenticate users, but that is outside the scope of secure deployment
configuration).

The JEE APIs that interact with JEE security configuration include:

  - *getRemoteUser*, which determines the user name with which the
    client authenticated
  - *isUserInRole*, which determines whether a remote user is in a
    specific security role.
  - *getUserPrincipal*, which determines the principal name of the
    current user and returns a java.security.Principal object

Use of these programmatic APIs should be reviewed to ensure consistency
with the configuration. Specifically, the security-role-ref element
should be declared in the deployment descriptor with a role-name
subelement containing the role name to be passed to the *isUserInRole*
method.

The following code demonstrates the use of programmatic security for the
purposes of programmatic login and establishing identities and roles.
This servlet does the following:

  - displays information about the current user.
  - prompts the user to log in.
  - prints out the information again to demonstrate the effect of the
    login method.
  - Iogs the user out.
  - prints out the information again to demonstrate the effect of the
    logout method.

`package enterprise.programmatic_login;`

`import java.io.*;`
`import java.net.*;`
`import javax.annotation.security.DeclareRoles;`
`import javax.servlet.*;`
`import javax.servlet.http.*;`

`@DeclareRoles("javaee6user")`
`public class LoginServlet extends HttpServlet {`

`    /** `
`     * Processes requests for both HTTP GET and POST methods.`
`     * @param request servlet request`
`     * @param response servlet response`
`     */`
`    protected void processRequest(HttpServletRequest request, `
`                 HttpServletResponse response)`
`            throws ServletException, IOException {`
`        response.setContentType("text/html;charset=UTF-8");`
`        PrintWriter out = response.getWriter();`
`        try {`
`            String userName = request.getParameter("txtUserName");`
`            String password = request.getParameter("txtPassword");`
`            `
`            out.println("Before Login" + "<br><br>");`
`            out.println("IsUserInRole?.." `
`                        + request.isUserInRole("javaee6user")+"<br>");`
`            out.println("getRemoteUser?.." + request.getRemoteUser()+"<br>");`
`            out.println("getUserPrincipal?.." `
`                        + request.getUserPrincipal()+"<br>");`
`            out.println("getAuthType?.." + request.getAuthType()+"<br><br>");`
`            `
`            try {`
`                request.login(userName, password); `
`            } catch(ServletException ex) {`
`                out.println("Login Failed with a ServletException.." `
`                    + ex.getMessage());`
`                return;`
`            }`
`            out.println("After Login..."+"<br><br>");`
`            out.println("IsUserInRole?.." `
`                        + request.isUserInRole("javaee6user")+"<br>");`
`            out.println("getRemoteUser?.." + request.getRemoteUser()+"<br>");`
`            out.println("getUserPrincipal?.." `
`                        + request.getUserPrincipal()+"<br>");`
`            out.println("getAuthType?.." + request.getAuthType()+"<br><br>");`
`            `
`            request.logout();`
`            out.println("After Logout..."+"<br><br>");`
`            out.println("IsUserInRole?.." `
`                        + request.isUserInRole("javaee6user")+"<br>");`
`            out.println("getRemoteUser?.." + request.getRemoteUser()+"<br>");`
`            out.println("getUserPrincipal?.."`
`                        + request.getUserPrincipal()+"<br>");`
`            out.println("getAuthType?.." + request.getAuthType()+"<br>");`
`        } finally {`
`            out.close();`
`        }`
`    }`
`    ...`
`}`

More detailed information can be found in the Java EE Tutorial: [Using
Programmatic Security with Web
Applications](http://docs.oracle.com/javaee/6/tutorial/doc/gjiie.html).

#### IIS

Microsoft IIS security configuration can also be programmatically set
from various languages:

  - appcmd.exe set config ...
  - C\#
  - Visual Basic
  - JavaScript

For example, disabling Anonymous authentication for a site named MySite,
then enabling both Basic authentication and Windows authentication for
the site (as done via configuration in the section above) can be
accomplished programmatically as follows:

**In a command script using appcmd.exe**

`appcmd.exe set config "MySite" -section:system.webServer/security/authentication`
`      /anonymousAuthentication /enabled:"False" /commit:apphost`
`appcmd.exe set config "MySite" -section:system.webServer/security/authentication`
`     /basicAuthentication /enabled:"True" /commit:apphost`
`appcmd.exe set config "MySite" -section:system.webServer/security/authentication`
`    /windowsAuthentication /enabled:"True" /commit:apphost`

**Using C\#**

`using System;`
`using System.Text;`
`using Microsoft.Web.Administration;`

`internal static class Sample {`

`   private static void Main() {`

`      using(ServerManager serverManager = new ServerManager()) { `
`         Configuration config = serverManager.GetApplicationHostConfiguration();`

`         ConfigurationSection anonymousAuthenticationSection =`
`           config.GetSection("system.webServer/security/authentication`
`                              /anonymousAuthentication", "MySite");`
`         anonymousAuthenticationSection["enabled"] = false;`

`         ConfigurationSection basicAuthenticationSection =`
`           config.GetSection("system.webServer/security/authentication`
`                               /basicAuthentication", "MySite");`
`         basicAuthenticationSection["enabled"] = true;`

`         ConfigurationSection windowsAuthenticationSection =`
`           config.GetSection("system.webServer/security/authentication`
`                             /windowsAuthentication", "MySite");`
`         windowsAuthenticationSection["enabled"] = true;`

`         serverManager.CommitChanges();`
`      }`
`   }`
`}`

When reviewing source code, special attention should be paid to
configuration updates in security sections.