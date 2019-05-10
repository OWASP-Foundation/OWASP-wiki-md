`    <td ``>Consider anyone who can send untrusted data to the system, including external users, internal users, and administrators.`

</td>

`    <td ``>Attacker sends simple text-based attacks that exploit the syntax of the targeted interpreter. Almost any source of data can be an injection vector, including internal sources`

</td>

`    <td colspan=2  ``>Injection flaws occur when an application sends untrusted data to an interpreter. Injection flaws are very prevalent, particularly in legacy code, often found in SQL queries, LDAP queries, XPath queries, OS commands, program arguments, etc. Injection flaws are easy to discover when examining code, but more difficult via testing. Scanners and fuzzers can help attackers find them.`

</td>

`    <td ``>Injection can result in data loss or corruption, lack of accountability, or denial of access. Injection can sometimes lead to complete host takeover.`

</td>

`    <td ``>Consider the business value of the affected data and the platform running the interpreter. All data could be stolen, modified, or deleted. Could your reputation be harmed?`

</td>

The best way to find out if an application is vulnerable to injection is
to verify that all use of interpreters clearly separates untrusted data
from the command or query. For SQL calls, this means using bind
variables in all prepared statements and stored procedures, and avoiding
dynamic queries.

Checking the code is a fast and accurate way to see if the application
uses interpreters safely. Code analysis tools can help a security
analyst find the use of interpreters and trace the data flow through the
application. Manual penetration testers can confirm these issues by
crafting exploits that confirm the vulnerability.

Automated dynamic scanning which exercises the application may provide
insight into whether some exploitable injection problems exist. Scanners
cannot always reach interpreters and can have difficulty detecting
whether an attack was successful.  Preventing injection requires keeping
untrusted data separate from commands and queries.

1.  The preferred option is to use a safe API which avoids the use of
    the interpreter entirely or provides a parameterized interface.
    Beware of APIs, such as stored procedures, that appear
    parameterized, but may still allow injection under the hood.
2.  If a parameterized API is not available, you should carefully escape
    special characters using the specific escape syntax for that
    interpreter. [OWASP's ESAPI](ESAPI "wikilink") has some of these
    [escaping
    routines](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html).
3.  Positive or "whitelist" input validation with appropriate
    canonicalization also helps protect against injection, but is
    **not** a complete defense as many applications require special
    characters in their input. [OWASP's ESAPI](ESAPI "wikilink") has an
    extensible library of [white list input validation
    routines](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Validator.html).

The application uses untrusted data in the construction of the following
vulnerable SQL call: <span style="color:red;">String query = "SELECT \*
FROM accounts WHERE custID='" + request.getParameter("id") +"'";</span>
The attacker modifies the 'id' parameter in their browser to send: ' or
'1'='1. This changes the meaning of the query to return all the records
from the accounts database, instead of only the intended customer's.
http://example.com/app/accountView?id=<span style="color: red;">' or
'1'='1</span> In the worst case, the attacker uses this weakness to
invoke special stored procedures in the database, allowing a complete
takeover of the database host.

  - [OWASP SQL Injection Prevention Cheat
    Sheet](SQL_Injection_Prevention_Cheat_Sheet "wikilink")
  - [OWASP Injection Flaws Article](Command_Injection "wikilink")
  - [ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
  - [ESAPI Input Validation
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Validator.html)
  - [ASVS: Output Encoding/Escaping Requirements
    (V6)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [OWASP Testing Guide: Chapter on SQL Injection
    Testing](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")
  - [OWASP Code Review Guide: Chapter on SQL
    Injection](Reviewing_Code_for_SQL_Injection "wikilink")
  - [OWASP Code Review Guide: Command
    Injection](Reviewing_Code_for_OS_Injection "wikilink")

<!-- end list -->

  - [CWE Entry 77 on Command
    Injection](http://cwe.mitre.org/data/definitions/77.html)
  - [CWE Entry 89 on SQL
    Injection](http://cwe.mitre.org/data/definitions/89.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")