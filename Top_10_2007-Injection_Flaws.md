Injection flaws, particularly SQL injection, are unfortunately very
common in web applications. There are many types of injections:
[SQL](http://cwe.mitre.org/data/definitions/89.html), [Hibernate Query
Language (HQL)](http://cwe.mitre.org/data/definitions/564.html),
[LDAP](http://cwe.mitre.org/data/definitions/90.html),
[XPath](http://cwe.mitre.org/data/definitions/91.html),
[XQuery](http://cwe.mitre.org/data/definitions/652.html),
[XSLT](http://cwe.mitre.org/data/definitions/91.html),
[XML](http://cwe.mitre.org/data/definitions/91.html), [OS command
injection](http://cwe.mitre.org/data/definitions/78.html) and many more.

Injection occurs when user-supplied data is sent to an interpreter as
part of a command or query. Attackers trick the interpreter into
executing unintended commands via supplying specially crafted data.
Injection flaws allow attackers to create, read, update, or delete any
arbitrary data available to the application. In the worst case scenario,
these flaws allow an attacker to completely compromise the application
and the underlying systems, even bypassing deeply nested firewalled
environments.

## Environments Affected

All web application frameworks that use interpreters or invoke other
processes are vulnerable to injection attacks. This includes any
components of the framework, that might use back-end interpreters.

## Vulnerability

If user input is passed into an interpreter without validation or
encoding, the application is vulnerable. Check if user input is supplied
to dynamic queries, such as:

*`PHP:`*
`   $sql = "SELECT * FROM table WHERE id = '" . $_REQUEST['id'] . "'";`

*`Java:`*
`   `<code>`String query = "SELECT user_id FROM user_data WHERE `
`        user_name = '" + req.getParameter("userID") + "' and `
`        user_password = '" + req.getParameter("pwd") +"'";`</code>

## Verifying Security

The goal is to verify that user data cannot modify the meaning of
commands and queries sent to any of the interpreters invoked by the
application.

Automated approaches: Many vulnerability scanning tools search for
injection problems, particularly SQL injection. Static analysis tools
that search for uses of unsafe interpreter APIs are useful, but
frequently cannot verify that appropriate validation or encoding might
be in place to protect against the vulnerability. If the application
catches 501 / 500 internal server errors, or detailed database errors,
it can significantly hamper automated tools, but the code may still be
at risk. Automated tools may be able to detect LDAP / XML injections /
XPath injections.

Manual approaches: The most efficient and accurate approach is to check
the code that invokes interpreters. The reviewer should verify the use
of a safe API or that appropriate validation and/or encoding has
occurred. Testing can be extremely time-consuming and with low
coverageand spotty because the attack surface of most applications is so
large.

## Protection

Avoid the use of interpreters when possible. If you must invoke an
interpreter, the key method to avoid injections is the use of safe APIs,
such as strongly typed parameterized queries and object relational
mapping (ORM) libraries that are immune to injection (be careful here -
Hibernate, for example is NOT immune to injection by itself. You have to
use named parameters to be safe in Hibernate). These interfaces handle
all data escaping, or do not require escaping. Note that while safe
interfaces solve the problem, validation is still recommended in order
to detect attacks.

Using interpreters is dangerous, so it's worth it to take extra care,
such as the following:

  - **Input validation.** Use a standard input validation mechanism to
    validate all input data for length, type, syntax, and business rules
    before accepting the data to be displayed or stored. Use an "accept
    known good" validation strategy. Reject invalid input rather than
    attempting to sanitize potentially hostile data. Do not forget that
    error messages might also include invalid data
  - **Use strongly typed parameterized query APIs** with placeholder
    substitution markers, even when calling stored procedures
  - **Enforce least privilege** when connecting to databases and other
    backend systems
  - **Avoid detailed error messages** that are useful to an attacker
  - **Show care when using stored procedures** since they are generally
    safe from SQL Injection. However, be careful as they can be
    injectable (such as via the use of exec() or concatenating arguments
    within the stored procedure)
  - **Do not use dynamic query interfaces** (such as mysql_query() or
    similar)
  - **Do not use simple escaping functions**, such as PHP's addslashes()
    or character replacement functions like str_replace("'", "''").
    These are weak and have been successfully exploited by attackers.
    For PHP, use mysql_real_escape_string() if using MySQL, or
    preferably use PDO which does not require escaping
  - When using simple escape mechanisms, note that*' simple escaping
    functions cannot escape table names*'\! Table names must be legal
    SQL, and thus are completely unsuitable for user supplied input
  - **Watch out for canonicalization errors.** Inputs must be decoded
    and canonicalized to the application's current internal
    representation before being validated. Make sure that your
    application does not decode the same input twice. Such errors could
    be used to bypass whitelist schemes by introducing dangerous inputs
    after they have been checked

Language specific recommendations:

  - Java EE - use strongly typed PreparedStatement, or ORMs such as
    Spring or named parameters within Hibernate.
  - .NET - use strongly typed parameterized queries, such as SqlCommand
    with SqlParameter, or named parameters within Hibernate.
  - PHP - use PDO with strongly typed parameterized queries (using
    bindParam()).

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5121>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4953>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4592>

## Related Sites

  - [SQL Injection](SQL_Injection "wikilink")
  - [Guide to SQL Injection](Guide_to_SQL_Injection "wikilink")
  - [SQL Injection Prevention Cheat
    Sheet](SQL_Injection_Prevention_Cheat_Sheet "wikilink")
  - [Reviewing Code for SQL
    Injection](Reviewing_Code_for_SQL_Injection "wikilink")
  - [Testing for SQL
    Injection](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")

## References

  - CWE: CWE-89 (SQL Injection), CWE-77 (Command Injection), CWE-90
    (LDAP Injection), CWE-91 (XML Injection), CWE-93 (CRLF Injection),
    others.
  - WASC Threat Classification: [(1) SQL
    Injection](http://www.webappsec.org/projects/threat/classes/sql_injection.shtml)
    [(2) LDAP
    Injection](http://www.webappsec.org/projects/threat/classes/ldap_injection.shtml)
    [(3) OS
    Commanding](http://www.webappsec.org/projects/threat/classes/os_commanding.shtml)
  - Advanced SQL Injection,
    <http://www.ngssoftware.com/papers/advanced_sql_injection.pdf>
  - More Advanced SQL Injection,
    <http://www.nextgenss.com/papers/more_advanced_sql_injection.pdf>
  - Hibernate, an advanced object relational manager (ORM) for J2EE and
    .NET, <http://www.hibernate.org/>
  - J2EE Prepared Statements,
    <http://java.sun.com/docs/books/tutorial/jdbc/basics/prepared.html>
  - How to: Protect from SQL injection in ASP.Net,
    <http://msdn2.microsoft.com/en-us/library/ms998271.aspx>
  - PHP PDO functions, <http://php.net/pdo>
  - SQL Injection,
    <http://packetstorm.codar.com.br/papers/general/SQLInjectionWhitePaper.pdf>

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")