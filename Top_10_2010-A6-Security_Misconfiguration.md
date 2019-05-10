`    <td ``>Consider anonymous external attackers as well as users with their own accounts that may attempt to compromise the system. Also consider insiders wanting to disguise their actions.`

</td>

`    <td ``>Attacker accesses default accounts, unused pages, unpatched flaws, unprotected files and directories, etc. to gain unauthorized access to or knowledge of the system.`

</td>

`    <td colspan=2  ``>Security misconfiguration can happen at any level of an application stack, including the platform, web server, application server, framework, and custom code. Developers and network administrators need to work together to ensure that the entire stack is configured properly. Automated scanners are useful for detecting missing patches, misconfigurations, use of default accounts, unnecessary services, etc.`

</td>

`    <td ``>Such flaws frequently give attackers unauthorized access to some system data or functionality. Occasionally, such flaws result in a complete system compromise.`

</td>

`    <td ``>The system could be completely compromised without you knowing it. All your data could be stolen or modified slowly over time.`

`Recovery costs could be expensive.`

</td>

Have you performed the proper security hardening across the entire
application stack?

1.  Do you have a process for keeping all your software up to date? This
    includes the OS, Web/App Server, DBMS, applications, and all code
    libraries.
2.  Is everything unnecessary disabled, removed, or not installed (e.g.
    ports, services, pages, accounts, privileges)?
3.  Are default account passwords changed or disabled?
4.  Is your error handling set up to prevent stack traces and other
    overly informative error messages from leaking?
5.  Are the security settings in your development frameworks (e.g.,
    Struts, Spring, ASP.NET) and libraries understood and configured
    properly?

A concerted, repeatable process is required to develop and maintain a
proper application security configuration.  The primary recommendations
are to establish all of the following:

1.  A repeatable hardening process that makes it fast and easy to deploy
    another environment that is properly locked down. Development, QA,
    and production environments should all be configured identically.
    This process should be automated to minimize the effort required to
    setup a new secure environment.
2.  A process for keeping abreast of and deploying all new software
    updates and patches in a timely manner to each deployed environment.
    This needs to include <u>all code libraries as well</u>, which are
    frequently overlooked.
3.  A strong application architecture that provides good separation and
    security between components.
4.  Consider running scans and doing audits periodically to help detect
    future misconfigurations or missing patches.

<u>Scenario \#1</u>: Your application relies on a powerful framework
like Struts or Spring. XSS flaws are found in these framework components
you rely on. An update is released to fix these flaws but you don’t
update your libraries. Until you do, attackers can easily find and
exploit these flaws in your app.

<u>Scenario \#2</u>: The app server admin console is automatically
installed and not removed. Default accounts aren’t changed. Attacker
discovers the standard admin pages are on your server, logs in with
default passwords, and takes over.

<u>Scenario \#3</u>: Directory listing is not disabled on your server.
Attacker discovers she can simply list directories to find any file.
Attacker finds and downloads all your compiled Java classes, which she
reverse engineers to get all your custom code. She then finds a serious
access control flaw in your application.

<u>Scenario \#4</u>: App server configuration allows stack traces to be
returned to users, potentially exposing underlying flaws. Attackers love
the extra information error messages provide.

  - [OWASP Development Guide: Chapter on
    Configuration](Configuration "wikilink")
  - [OWASP Code Review Guide: Chapter on Error
    Handling](Error_Handling "wikilink")
  - [OWASP Testing Guide: Configuration
    Management](Testing_for_configuration_management "wikilink")
  - [OWASP Testing Guide: Testing for Error
    Codes](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")
  - [OWASP Top 10 2004 - Insecure Configuration
    Management](A10_2004_Insecure_Configuration_Management "wikilink")

For additional requirements in this area, see the [ASVS requirements
area for Security Configuration
(V12)](http://www.owasp.org/index.php/ASVS#tab=Download)

  - [PC Magazine Article on Web Server
    Hardening](http://www.pcmag.com/article2/0,2817,11525,00.asp)
  - [CWE Entry 2 on Environmental Security
    Flaws](http://cwe.mitre.org/data/definitions/2.html)
  - [CIS Security Configuration
    Guides/Benchmarks](http://cisecurity.org/en-us/?route=downloads.benchmarks)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")