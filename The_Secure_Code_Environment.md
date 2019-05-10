[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

Contact author: [Eoin Keary](mailto:eoinkeary@owasp.org)

## Secure Code Environment

Another important thing to be aware of is when you receive the code make
sure it is identical in deployment layout to what would go to
production. Having well-written code is a great start, but deploying
that great code in unprotected folders on the application server is not
a great idea. Attackers do code reviews also and what better than to
code review the potential target application. For example: try in
“***Google***”:
<u><http://www.google.com/search?q=%0D%0Aintitle%3Aindex.of+WEB-INF></u>

This lists exposed “*Web-Inf*” directories on WebSphere®, Tomcat and
other app servers.

''The WEB-INF directory tree contains web application classes,
pre-compiled JSP files, server side libraries, session information and
files such as **web.xml** and **webapp.properties**. ''

So be sure the code base is identical to production. Ensuring that we
have a “*secure code environment*” is also an important part of an
application secure code inspection.

The code may be “bullet proof” but if it is accessible to a user this
may cause other problems. Remember the developer is not the only one to
perform code reviews, attackers also do this. The only visible surface
that a user should see are the “suggestions” rendered by the browser
upon receiving the HTML from the backend server. Any request to the
backend server outside the strict context of the application should be
refused and not be visible. Generally think of *“That which is not
explicitly granted is denied”*.

Example of the Tomcat web.xml to prevent directory indexing:

<servlet>
<servlet-name>`default`</servlet-name>
<servlet-class>`org.apache.catalina.servlets.DefaultServlet`</servlet-class>
<init-param>
<param-name>`debug`</param-name>
<param-value>`0`</param-value>
</init-param>
<init-param>
<param-name>`listings`</param-name>
<param-value>`false`</param-value>
</init-param>
<init-param>
<param-name>`readonly`</param-name>
<param-value>`true`</param-value>
</init-param>
<load-on-startup>`1`</load-on-startup>
</servlet>

So to deny access to all directories we put:

<Directory />
`Order Deny,Allow`
`Deny from All`
</Directory>

And then override this for the directories we require access to:

Also in Apache HTTP server to ensure directories like WEB-INF and
META-INF are protected the following should be added to the
*httpd.conf*, the main configuration file for the Apache web server

`<Directory /usr/users/*/public_html> `
`Order Deny,Allow `
`Allow from all `
</Directory>` `
<Directory /usr/local/httpd>` `
`Order Deny,Allow `
`Allow from all `
</Directory>

On Apache servers, if we wish to specify permissions for a directory and
subdirectories we add a ***.htaccess*** file.

To protect the .htaccess file itself we palce:

`<Files .htaccess>`
`order allow,deny`
`deny from all`
</Files>

To stop directory indexing we place the following directive into the
.htaccess file: **IndexIgnore \*** The \* is a wildcard to prevent all
files from being indexed.

## Protecting JSP pages

If using the Struts framework we do not want users access any JSP page
directly. Accessing the JSP directly without going through the request
processor can enable the attacker to view any server-side code in the
JSP. Lets say initial page can is a HTML document. So the HTTP GET from
the browser retrieves this page. Any subsequent page must go through the
framework. Add the following lines to the **web.xml** file to prevent
users from accessing any JSP page directly:

<web-app>
`  ...`
` `<security-constraint>
`   `<web-resource-collection>
`     `<web-resource-name>`no_access`</web-resource-name>
`     `<url-pattern>`*.jsp`</url-pattern>
`   `</web-resource-collection>
`   `<auth-constraint/>
` `</security-constraint>
` ...`
</web-app>

With this directive in **web.xml** a HTTP request for a JSP page
directly will fail.

## A clean environment

When reviewing the environment we must see if the directories contain
any artefacts from development. These files may not be referenced in any
way and hence the application server gives no protection to them. Files
such as .**bak, .old, .tmp** etc should be removed as they contain
source code.

Source code should not go into production directories. The complied
class files are all that is required in most cases. All source code
should be removed and only the “executables” should remain.

No development tools should be present on a production environment. For
example a java application should only need a JRE (Java Runtime
Environment) and not a JDK (Java Development Kit) to function.

Test and debug code should be removed from all source code and
configuration files. Even commented out code should be removed as a
precaution. Test code can contain backdoors that circumvent the workflow
in the application and at worst contain valid authentication credentials
or account details.

Comments on code and Meta tags pertaining to the IDE used or technology
used to develop the application should be removed. Some comments can
divulge important information regarding bugs in code or pointers to
functionality. This is particularly important with client side code such
as JSP’s and ASP files.

A copyright and confidentiality statement should be at the top of every
file. This mitigates any confusion regarding who owns the code. This may
seem trivial but it is important to state who owns the code.

To sum up, code review includes looking at the configuration of the
application server and not just the code. Knowledge of the server in
question is important and information is easily available on the web.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:OWASP
Code Review Project](Category:OWASP_Code_Review_Project "wikilink")
[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")