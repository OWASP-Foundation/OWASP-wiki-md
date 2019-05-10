`    <td ``>`

Consider anonymous external attackers as well as users with their own
accounts that may attempt to compromise the system. Also consider
insiders wanting to disguise their actions.

</td>

`    <td ``>`

Attacker accesses default accounts, unused pages, unpatched flaws,
unprotected files and directories, etc. to gain unauthorized access to
or knowledge of the system.

</td>

`    <td colspan=2  ``>`

Security misconfiguration can happen at any level of an application
stack, including the platform, web server, application server, database,
framework, and custom code. Developers and system administrators need to
work together to ensure that the entire stack is configured properly.
Automated scanners are useful for detecting missing patches,
misconfigurations, use of default accounts, unnecessary services, etc.

</td>

`    <td ``>`

The system could be completely compromised without you knowing it. All
of your data could be stolen or modified slowly over time.

Recovery costs could be expensive

</td>

`    <td ``>`

The system could be completely compromised without you knowing it. All
your data could be stolen or modified slowly over time.

Recovery costs could be expensive.

</td>

1.  Is your application missing the proper security hardening across any
    part of the application stack? Including:
2.  Is any of your software out of date? This includes the OS, Web/App
    Server, DBMS, applications, and all code libraries (see new A9).
3.  Are any unnecessary features enabled or installed (e.g., ports,
    services, pages, accounts, privileges)?
4.  Are default accounts and their passwords still enabled and
    unchanged?
5.  Does your error handling reveal stack traces or other overly
    informative error messages to users?
6.  Are the security settings in your development frameworks (e.g.,
    Struts, Spring, ASP.NET) and libraries not set to secure values?

Without a concerted, repeatable application security configuration
process, systems are at a higher risk.

The primary recommendations are to establish all of the following: A
repeatable hardening process that makes it fast and easy to deploy
another environment that is properly locked down. Development, QA, and
production environments should all be configured identically (with
different passwords used in each environment). This process should be
automated to minimize the effort required to setup a new secure
environment. A process for keeping abreast of and deploying all new
software updates and patches in a timely manner to each deployed
environment. This needs to include **all code libraries as well (see new
A9)**. A strong application architecture that provides effective, secure
separation between components. Consider running scans and doing audits
periodically to help detect future misconfigurations or missing patches.
 **Scenario \#1:** The app server admin console is automatically
installed and not removed. Default accounts aren’t changed. Attacker
discovers the standard admin pages are on your server, logs in with
default passwords, and takes over.

**Scenario \#2:** Directory listing is not disabled on your server.
Attacker discovers she can simply list directories to find any file.
Attacker finds and downloads all your compiled Java classes, which she
decompiles and reverse engineers to get all your custom code. She then
finds a serious access control flaw in your application.

**Scenario \#3:** App server configuration allows stack traces to be
returned to users, potentially exposing underlying flaws. Attackers love
the extra information error messages provide.

**Scenario \#4:** App server comes with sample applications that are not
removed from your production server. Said sample applications have well
known security flaws attackers can use to compromise your server.

  - [OWASP Development Guide: Chapter on
    Configuration](https://www.owasp.org/index.php/Configuration)
  - [OWASP Code Review Guide: Chapter on Error
    Handling](https://www.owasp.org/index.php/Error_Handling)
  - [OWASP Testing Guide: Configuration
    Management](https://www.owasp.org/index.php/Testing_for_configuration_management)
  - [OWASP Testing Guide: Testing for Error
    Codes](https://www.owasp.org/index.php/Testing_for_Error_Code_\(OWASP-IG-006\))
  - [OWASP Top 10 2004 - Insecure Configuration
    Management](https://www.owasp.org/index.php/A10_2004_Insecure_Configuration_Management)

For additional requirements in this area, see the [ASVS requirements
area for Security Configuration
(V12)](https://www.owasp.org/index.php/ASVS).

  - [PC Magazine Article on Web Server
    Hardening](http://www.pcmag.com/article2/0,2817,11525,00.asp)
  - [CWE Entry 2 on Environmental Security
    Flaws](http://cwe.mitre.org/data/definitions/2.html)
  - [CIS Security Configuration
    Guides/Benchmarks](http://benchmarks.cisecurity.org/downloads/benchmarks/)