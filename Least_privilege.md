

## Description

The principle of least privilege recommends that accounts have the least
amount of privilege required to perform their business processes. This
encompasses user rights, resource permissions such as CPU limits,
memory, network, and file system permissions.

## Examples

### Administrative Priviledges Granted to a Middleware Server

  -
    For example, if a middleware server only requires access to the
    network, read access to a database table, and the ability to write
    to a log, this describes all the permissions that should be granted.
    Under no circumstances should the middleware be granted
    administrative privileges.

### Connecting to the Database as Root

  -
    In this example PHP code, only a SELECT statement from the database
    is issued. There is no reason to connect to the database as root.
    Instead, a user should be created with only the necessary access to
    the database that can be used to perform the SELECT query.

<?php
 $host = 'localhost';
 $userID = 'root';
 $password = 'password';
 $db = mysql_connect($host, $userID, $password) or die ('Error connecting to mysql');
 $name = 'testdatabase';
 mysql_select_db($name);
 $sql="SELECT * FROM theTable";
 $result=mysql_query($sql);
 ?>

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Failure to drop privileges when
    reasonable](Failure_to_drop_privileges_when_reasonable "wikilink")
  - [Failure to check whether privileges were dropped
    successfully](Failure_to_check_whether_privileges_were_dropped_successfully "wikilink")
  - [Least Privilege Violation](Least_Privilege_Violation "wikilink")

## Related [Controls](Controls "wikilink")

  - [Authorization](Authorization "wikilink")

## References

  - [The Protection of Information in Computer
    Systems](http://web.mit.edu/Saltzer/www/publications/protection/)

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")