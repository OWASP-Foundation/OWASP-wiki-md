__TOC__

## Introduction

An SQL injection Attack consists of injecting sql query portions in the
back-end database system via the client interface in the web
application. The consequence of a successful exploitation of an SQL
injection varies from just reading data to modifying data or executing
system commands. SQL Injection in PHP remains the number one attack
vector, and also the number on reason for DATA COMPROMISES

## Data Validation and prepared statements

It is as simple as this the absence of data validation and prepared
statements or stored procedures will increase the possibility that your
code contain SQL injections. If your application gives the users the
possibility to change parameters and those parameters are not verified
and inserted in an unprepared statement than your code contain an SQL
Injection.

Example 1 :

<?php
 $pass=$_GET["pass"];
 $con = mysql_connect('localhost', 'owasp', 'abc123');
 mysql_select_db("owasp_php", $con);
 $sql="SELECT card FROM users WHERE password = '".$pass."'";
 $result = mysql_query($sql);
 ?>

## Suspicious Validation

The most common ways to prevent SQL Injection in PHP are using functions
such as addslashes() and mysql_real_escape_string() but those
function can always cause SQL Injections in some cases.

**addslashes :**

you will avoid Sql injection using addslashes() only in the case when
you wrap the query string with quotes.The following example would still
be vulnerable

<?php

 $id = addslashes( $_GET['id'] );
 $query = 'SELECT title FROM books WHERE id = ' . $id;

 ?>

**mysql_real_escape_string():**

mysql_real_escape_string() is a little bit more powerful than
addslashes() as it calls MySQL's library function
mysql_real_escape_string, which prepends backslashes to the following
characters: \\x00, \\n, \\r, \\, ', " and \\x1a. As with addslashes(),
mysql_real_escape_string() will only work if the query string is
wrapped in quotes. A string such as the following would still be
vulnerable to an SQL injection:

<?php

 $bid = mysql_real_escape_string( $_GET['id'] );
 $query = 'SELECT title FROM books WHERE id = ' . $bid;

 ?>

## Recommendation

the formula for Sql-injection-free code:

`Good Data Validation + Prepared Statement`

The PHP Data Objects (PDO) extension defines an abstract database
interface that offers parameterized queries for prepared statements and
stored procedures. It is available from PHP 5. Use of PDO::prepare will
provide good SQL injection defenses, with some exceptions

Example:

<?php
 $id = htmlspecialchars($_GET["id"]); //Validation
 $sql = 'SELECT * FROM users WHERE id = :calories';
 $sth = $dbh->

prepare($sql, array(PDO::ATTR_CURSOR =\> PDO::CURSOR_FWDONLY));
//prepared statement

`$sth->execute(array(':id' => $id));`
`$red = $sth->fetchAll();`
`?>`

## References

[PDO](http://www.php.net/manual/en/book.pdo.php)

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")