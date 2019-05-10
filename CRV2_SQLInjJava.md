# Java SQL Injections

SQL injections occur when input to a web application is not controlled
or sanitized before executing to the back-end database The attacker
tries to exploit this vulnerability by passing SQL commands in her/his
input and therefore will create a undesired response from the database
such as providing information that bypasses the authorization and
authentication programmed in the web application

An example of a vulnerable java code (Livshits and Lam, 2005)

`   HttpServletRequest request = ...;`
`   String userName = request.getParameter("name");`
`   Connection con  = ...`
`   String query    = "SELECT * FROM Users " + " WHERE name = '" + userName + "'";`
`   con.execute(query);`

The input parameter “name” is passed to the String query without any
proper validation or verification. The query ‘SELECT\* FROM users where
name" is equal to the string ‘username’ can be easily misused to bypass
something different that just the ‘name’. For example, the attacker can
attempt to pass instead

`"   OR  1=1.`

In this way accessing all user records and not only the one entitled to
the specific user

## More of SQL Injection Vulnerabilities

See the OWASP article on SQL Injection Vulnerabilities.
<http://www.owasp.org/index.php/SQL_Injection> See the OWASP article on
Blind_SQL_Injection Vulnerabilities.
<http://www.owasp.org/index.php/Blind_SQL_Injection>

## How to Avoid SQL Injection Vulnerabilities

See the OWASP Development Guide article on how to Avoid SQL Injection
Vulnerabilities. <http://www.owasp.org/index.php/Guide_to_SQL_Injection>

## How to Test for SQL Injection Vulnerabilities

See the OWASP Testing Guide article on how to Test for SQL Injection
Vulnerabilities.
<http://www.owasp.org/index.php/Testing_for_SQL_Injection>

## References

Livshits and Lam, 2005 "Finding Security Vulnerabilities in Java
Applications with Static Analysis" available at
<https://www.usenix.org/legacy/event/sec05/tech/full_papers/livshits/livshits_html/#sec:sqlinjexample>
Accessed on 3rd October, 2013