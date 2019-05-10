## Summary

[SQL Injection](SQL_Injection "wikilink") vulnerabilities occur whenever
input is used in the construction of a SQL query without being
adequately constrained or sanitized. The use of dynamic SQL (the
construction of SQL queries by concatenation of strings) opens the door
to these vulnerabilities. SQL injection allows an attacker to access the
SQL servers. It allows for the execution of SQL code under the
privileges of the user used to connect to the database.

*MySQL server* has a few particularities so that some exploits need to
be specially customized for this application. That's the subject of this
section.

## How to Test

When an SQL injection vulnerability is found in an application backed by
a MySQL database, there are a number of attacks that could be performed
depending on the MySQL version and user privileges on DBMS.

MySQL comes with at least four versions which are used in production
worldwide, 3.23.x, 4.0.x, 4.1.x and 5.0.x. Every version has a set of
features proportional to version number.

  - From Version 4.0: UNION
  - From Version 4.1: Subqueries
  - From Version 5.0: Stored procedures, Stored functions and the view
    named INFORMATION_SCHEMA
  - From Version 5.0.2: Triggers

It should be noted that for MySQL versions before 4.0.x, only Boolean or
time-based Blind Injection attacks could be used, since the subquery
functionality or UNION statements were not implemented.

From now on, we will assume that there is a classic SQL injection
vulnerability, which can be triggered by a request similar to the the
one described in the Section on [Testing for SQL
Injection](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink").

`http://www.example.com/page.php?id=2`

### The Single Quotes Problem

Before taking advantage of MySQL features, it has to be taken in
consideration how strings could be represented in a statement, as often
web applications escape single quotes.

MySQL quote escaping is the following:
''' 'A string with \\'quotes\\'' '''

That is, MySQL interprets escaped apostrophes (\\') as characters and
not as metacharacters.

So if the application, to work properly, needs to use constant strings,
two cases are to be differentiated:

1.  Web app escapes single quotes (' =\> \\')
2.  Web app does not escape single quotes (' =\> ')

Under MySQL, there is a standard way to bypass the need of single
quotes, having a constant string to be declared without the need for
single quotes.

Let's suppose we want to know the value of a field named 'password' in a
record, with a condition like the following:

\#: password like 'A%'

1.  The ASCII values in a concatenated hex:
    : password LIKE 0x4125
2.  The char() function:
      -
        password LIKE CHAR(65,37)

### Multiple mixed queries:

MySQL library connectors do not support multiple queries separated by
**';'** so there's no way to inject multiple non-homogeneous SQL
commands inside a single SQL injection vulnerability like in Microsoft
SQL Server.

For example the following injection will result in an error:

`1 ; update tablename set code='javascript code' where 1 --`

### Information gathering

#### Fingerprinting MySQL

Of course, the first thing to know is if there's MySQL DBMS as a back
end database. MySQL server has a feature that is used to let other DBMS
ignore a clause in MySQL dialect. When a comment block *('/\*\*/')*
contains an exclamation mark *('/\*\! sql here\*/')* it is interpreted
by MySQL, and is considered as a normal comment block by other DBMS as
explained in [MySQL
manual](http://dev.mysql.com/doc/refman/5.0/en/comments.html).

Example:

`1 /*! and 1=0 */`

**Result Expected:**
If MySQL is present, the clause inside the comment block will be
interpreted.

#### Version

There are three ways to gain this information:

1.  By using the global variable @@version
2.  By using the function
    [VERSION()](http://dev.mysql.com/doc/refman/5.0/en/information-functions.html)
3.  By using comment fingerprinting with a version number /\*\!40110 and
    1=0\*/
      -
        which means

`if(version >= 4.1.10) `
`   add 'and 1=0' to the query.`

These are equivalent as the result is the same.

In band injection:

`1 AND 1=0 UNION SELECT @@version /*`

Inferential injection:

`1 AND @@version like '4.0%'`

**Result Expected:**
A string like this:

`5.0.22-log`

#### Login User

There are two kinds of users MySQL Server relies upon.

1.  [USER()](http://dev.mysql.com/doc/refman/5.0/en/information-functions.html):
    the user connected to the MySQL Server.
2.  [CURRENT_USER()](http://dev.mysql.com/doc/refman/5.0/en/information-functions.html):
    the internal user who is executing the query.

There is some difference between 1 and 2. The main one is that an
anonymous user could connect (if allowed) with any name, but the MySQL
internal user is an empty name (''). Another difference is that a stored
procedure or a stored function are executed as the creator user, if not
declared elsewhere. This can be known by using **CURRENT_USER**.

In band injection:

`1 AND 1=0 UNION SELECT USER() `

Inferential injection:

`1 AND USER() like 'root%'`

**Result Expected:**
A string like this:

`user@hostname`

#### Database name in use

There is the native function DATABASE()

In band injection:

`1 AND 1=0 UNION SELECT DATABASE() `

Inferential injection:

`1 AND DATABASE() like 'db%'`

**Result Expected:**
A string like this:

`dbname`

#### INFORMATION_SCHEMA

From MySQL 5.0 a view named
[INFORMATION_SCHEMA](http://dev.mysql.com/doc/refman/5.0/en/information-schema.html)
was created. It allows us to get all informations about databases,
tables, and columns, as well as procedures and functions.

Here is a summary of some interesting Views.

|  |                                     |  |                                                    |
|  | ----------------------------------- |  | -------------------------------------------------- |
|  | **Tables_in_INFORMATION_SCHEMA** |  | **DESCRIPTION**                                    |
|  | ..\[skipped\]..                     |  | ..\[skipped\]..                                    |
|  | SCHEMATA                            |  | All databases the user has (at least) SELECT_priv |
|  | SCHEMA_PRIVILEGES                  |  | The privileges the user has for each DB            |
|  | TABLES                              |  | All tables the user has (at least) SELECT_priv    |
|  | TABLE_PRIVILEGES                   |  | The privileges the user has for each table         |
|  | COLUMNS                             |  | All columns the user has (at least) SELECT_priv   |
|  | COLUMN_PRIVILEGES                  |  | The privileges the user has for each column        |
|  | VIEWS                               |  | All columns the user has (at least) SELECT_priv   |
|  | ROUTINES                            |  | Procedures and functions (needs EXECUTE_priv)     |
|  | TRIGGERS                            |  | Triggers (needs INSERT_priv)                      |
|  | USER_PRIVILEGES                    |  | Privileges connected User has                      |
|  |                                     |  |                                                    |

All of this information could be extracted by using known techniques as
described in SQL Injection section.

### Attack vectors

#### Write in a File

If the connected user has **FILE** privileges and single quotes are not
escaped, the 'into outfile' clause can be used to export query results
in a file.

`Select * from table into outfile '/tmp/file'`

Note: there is no way to bypass single quotes surrounding a filename. So
if there's some sanitization on single quotes like escape (\\') there
will be no way to use the 'into outfile' clause.

This kind of attack could be used as an out-of-band technique to gain
information about the results of a query or to write a file which could
be executed inside the web server directory.

Example:

`1 limit 1 into outfile '/var/www/root/test.jsp' FIELDS ENCLOSED BY '//'  LINES TERMINATED BY '\n<%jsp code here%>';`

**Result Expected:**
Results are stored in a file with rw-rw-rw privileges owned by MySQL
user and group.

Where */var/www/root/test.jsp* will contain:

`//field values//`
`<%jsp code here%>`

#### Read from a File

Load_file is a native function that can read a file when allowed by the
file system permissions. If a connected user has **FILE** privileges, it
could be used to get the files' content. Single quotes escape
sanitization can by bypassed by using previously described techniques.

`load_file('filename')`

**Result Expected:**
The whole file will be available for exporting by using standard
techniques.

### Standard SQL Injection Attack

In a standard SQL injection you can have results displayed directly in a
page as normal output or as a MySQL error. By using already mentioned
SQL Injection attacks and the already described MySQL features, direct
SQL injection could be easily accomplished at a level depth depending
primarily on the MySQL version the pentester is facing.

A good attack is to know the results by forcing a function/procedure or
the server itself to throw an error. A list of errors thrown by MySQL
and in particular native functions could be found on [MySQL
Manual](http://dev.mysql.com/doc/refman/5.0/en/error-messages-server.html).

### Out of band SQL Injection

Out of band injection could be accomplished by using the ['into
outfile'](#Write_in_a_File "wikilink") clause.

### Blind SQL Injection

For blind SQL injection, there is a set of useful function natively
provided by MySQL server.

  - String Length:
      -
        *LENGTH(str)*
  - Extract a substring from a given string:
      -
        *SUBSTRING(string, offset, \#chars_returned)*
  - Time based Blind Injection: BENCHMARK and SLEEP
      -
        *BENCHMARK(\#ofcycles,action_to_be_performed )*
        The benchmark function could be used to perform timing attacks,
        when blind injection by boolean values does not yield any
        results.
        See. SLEEP() (MySQL \> 5.0.x) for an alternative on benchmark.

For a complete list, refer to the MySQL manual at
<http://dev.mysql.com/doc/refman/5.0/en/functions.html>

## Tools

  - Francois Larouche: Multiple DBMS SQL Injection tool -
    <http://www.sqlpowerinjector.com/index.htm>
  - ilo--, Reversing.org -
    [sqlbftools](http://packetstormsecurity.org/files/43795/sqlbftools-1.2.tar.gz.html)
  - Bernardo Damele A. G.: sqlmap, automatic SQL injection tool -
    <http://sqlmap.org/>
  - Muhaimin Dzulfakar: MySqloit, MySql Injection takeover tool -
    <http://code.google.com/p/mysqloit/>
  - <http://sqlsus.sourceforge.net/>

## References

**Whitepapers**
\* Chris Anley: "Hackproofing MySQL" -
<http://www.databasesecurity.com/mysql/HackproofingMySQL.pdf>

**Case Studies**
\* Zeelock: Blind Injection in MySQL Databases -
<http://archive.cert.uni-stuttgart.de/bugtraq/2005/02/msg00289.html>