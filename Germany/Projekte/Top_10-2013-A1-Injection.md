`    <td ``>Consider anyone who can send untrusted data to the system, including external users, internal users, and administrators.`

</td>

`    <td ``>Attacker sends simple text-based attacks that exploit the syntax of the targeted interpreter. Almost any source of data can be an injection vector, including internal sources.`

</td>

`    <td colspan=2  ``>`[`Injection``
 ``flaws`](http://www.owasp.org/index.php/Injection_Flaws)` occur when an application sends untrusted data to an interpreter. Injection flaws are very prevalent, particularly in legacy code.  They are often found in SQL, LDAP, Xpath, or NoSQL queries; OS commands; XML parsers, SMTP Headers, program arguments, etc. Injection flaws are easy to discover when examining code, but frequently hard to discover via testing. Scanners and fuzzers can help attackers find injection flaws.`

</td>

`    <td ``>Injection can result in data loss or corruption, lack of accountability, or denial of access. Injection can sometimes lead to complete host takeover.`

</td>

`    <td ``>Consider the business value of the affected data and the platform running the interpreter. All data could be stolen, modified, or deleted.  Could your reputation be harmed?`

</td>

The best way to find out if an application is vulnerable to injection is
to verify that all use of interpreters clearly separates untrusted data
from the command or query. For SQL calls, this means using bind
variables in all prepared statements and stored procedures, and avoiding
dynamic queries.

Checking the code is a fast and accurate way to see if the application
uses interpreters safely. Code analysis tools can help a security
analyst find the use of interpreters and trace the data flow through the
application. Penetration testers can validate these issues by crafting
exploits that confirm the vulnerability.

Automated dynamic scanning which exercises the application may provide
insight into whether some exploitable injection flaws exist. Scanners
cannot always reach interpreters and have difficulty detecting whether
an attack was successful. Poor error handling makes injection flaws
easier to discover  Preventing injection requires keeping untrusted data
separate from commands and queries.

1.  The preferred option is to use a safe API which avoids the use of
    the interpreter entirely or provides a parameterized interface. Be
    careful with APIs, such as stored procedures, that are
    parameterized, but can still introduce injection under the hood.
2.  If a parameterized API is not available, you should carefully escape
    special characters using the specific escape syntax for that
    interpreter. [OWASP’s ESAPI](https://www.owasp.org/index.php/ESAPI)
    provides many of these [escaping
    routines](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html).
3.  Positive or “white list” input validation is also recommended, but
    is not a complete defense as many applications require special
    characters in their input. If special characters are required, only
    approaches 1. and 2. above will make their use safe. [OWASP’s
    ESAPI](https://www.owasp.org/index.php/ESAPI) has an extensible
    library of [white list input validation
    routines](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Validator.html).

**Scenario \#1:** The application uses untrusted data in the
construction of the following **vulnerable** SQL call:

<span style="color:red;"> String query = "SELECT \* FROM accounts WHERE
custID='" + request.getParameter("id") + "'";

</span> **Scenario \#2:** Similarly, an application’s blind trust in
frameworks may result in queries that are still vulnerable, (e.g.,
Hibernate Query Language (HQL)): <span style="color:red;"> Query
HQLQuery = session.createQuery(“FROM accounts WHERE custID='“ +
request.getParameter("id") + "'");'''

</span> In both cases, the attacker modifies the ‘id’ parameter value in
her browser to send: <span style="color:red;">' or '1'='1</span>. For
example:

<span style="color:red;"> http://example.com/app/accountView?id=' or
'1'='1 </span> This changes the meaning of both queries to return all
the records from the accounts table. More dangerous attacks could modify
data or even invoke stored procedures.

  - [OWASP SQL Injection Prevention Cheat
    Sheet](https://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet)
  - [OWASP Query Parameterization Cheat
    Sheet](https://www.owasp.org/index.php/Query_Parameterization_Cheat_Sheet)
  - [OWASP Command Injection
    Article](https://www.owasp.org/index.php/Command_Injection)
  - [OWASP XML eXternal Entity (XXE) Reference
    Article](https://www.owasp.org/index.php/XXE)
  - [ASVS: Output Encoding/Escaping Requirements
    (V6)](https://www.owasp.org/index.php/ASVS)
  - [OWASP Testing Guide: Chapter on SQL Injection
    Testing](https://www.owasp.org/index.php/Testing_for_SQL_Injection_\(OWASP-DV-005\))

<!-- end list -->

  - [CWE Entry 77 on Command
    Injection](http://cwe.mitre.org/data/definitions/77.html)
  - [CWE Entry 89 on SQL
    Injection](http://cwe.mitre.org/data/definitions/89.html)
  - [CWE Entry 564 on Hibernate
    Injection](http://cwe.mitre.org/data/definitions/564.html)