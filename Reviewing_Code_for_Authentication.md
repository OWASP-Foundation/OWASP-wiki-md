## **Introduction**

“Who are you?” Authentication is the process where an entity proves the
identity of another entity, typically through credentials, such as a
user name and password.

Depending on your requirements, there are several available
authentication mechanisms to choose from. If they are not correctly
chosen and implemented, the authentication mechanism can expose
vulnerabilities that attackers can exploit to gain access to your
system.

## **Authentication**

In the .NET, there is Authentication tags in the configuration file.

The \<**authentication**\> element configures the authentication mode
that your applications use.

\<**authentication**\>

The appropriate authentication mode depends on how your application or
Web service has been designed. The default Machine.config setting
applies a secure Windows authentication default as shown below.

''' authentication Attributes:mode="\[Windows|Forms|Passport|None\]" '''

<authentication mode="Windows" />

''' Forms Authentication Guidelines ''' To use Forms authentication, set
mode=“Forms” on the <authentication> element. Next, configure Forms
authentication using the child <forms> element. The following fragment
shows a secure <forms> authentication element configuration:

<authentication mode="Forms">
<forms loginUrl="Restricted\login.aspx"      Login page in an SSL protected folder
       protection="All"                      Privacy and integrity
       requireSSL="true"                     Prevents cookie being sent over http
       timeout="10"                          Limited session lifetime
       name="AppNameCookie"                  Unique per-application name
       path="/FormsAuth"                     and path
       slidingExpiration="true" > Sliding session lifetime </forms>
</authentication>

Use the following recommendations to improve Forms authentication
security:

  - Partition your Web site.
  - Set protection=“All”.
  - Use small cookie time-out values.
  - Consider using a fixed expiration period.
  - Use SSL with Forms authentication.
  - If you do not use SSL, set slidingExpiration = “false”.
  - Do not use the <credentials> element on production servers.
  - Configure the <machineKey> element.
  - Use unique cookie names and paths.

For classic ASP pages, authentication is usually performed manually by
including the user information in session variables after validation
against a DB, so you can look for something like:

`Session ("UserId") = UserName`
`Session ("Roles") = UserRoles`

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")