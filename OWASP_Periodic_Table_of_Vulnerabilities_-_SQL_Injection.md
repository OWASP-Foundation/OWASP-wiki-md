[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## SQL Injection

### Root Cause Summary

Applications that have insufficient output encoding or non-validated
literal strings concatenated into a dynamic SQL statement and
subsequently interpreted as code by the SQL engine.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

  - **Parameterized Queries** - Use parameterized queries to execute any
    SQL commands
  - **Input Validation** - Validate all inputs that are passed to the
    SQL statement for accuracy of datatypes, boundary limits and
    accepted character set
  - **Escape Sequences** - In cases where it is not possible to use
    parametric queries (like legacy code), ensure that the SQL engine
    sensitive characters are escaped appropriately. \[ [To provide a
    separate link for
    this](To_provide_a_separate_link_for_this "wikilink") \]

### Custom Framework Solution

None

### Custom Code Solution

  - When building custom solutions, make sure that SQL queries are
    constructed dynamically with table names and views after thorough
    and proper validation of the schema and the table/view.
  - As a precautionary measure, ensure that all tables have appropriate
    access control through policies.
  - Whenever possible, when building custom solutions, use the
    underlying databases prepared queries library.
  - Stored procedures must not contain string-concatenated SQL queries,
    either.

### Discussion / Controversy

Web Application Firewalls (WAFs) can help in reducing SQL Injection
attacks by filtering popular and well known attack inputs. WAFs are
driven by a set of predefined rules that can help mitigate SQL Injection
attacks to a certain extent. However, ultimately all injection flaws
need to be solved as close to the point where the injection actually
affects the target systems. In this case, that is as close to the
construction of the SQL query as possible, in the application framework.

### References

[SQL Injection](SQL_Injection "wikilink")
[SQL Injection
(WASC)](http://projects.webappsec.org/w/page/13246963/SQL%20Injection)
[SQL Injection (CWE)](http://cwe.mitre.org/data/definitions/89.html)