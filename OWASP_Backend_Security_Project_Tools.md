# Tools

The aim of this section is to enumerate and quickly describe the tools
used to find and exploit some vulnerabilities concerning database
management systems.

## SQL Ninja

SQL Ninja is a tool, written in Perl, which helps a penetration tester
to gain a shell on a system running Microsoft SQL server, exploiting a
web application resulted vulnerable to SQL Injection.

<http://sqlninja.sourceforge.net>

## SQLMap

sqlmap is an open source command-line automatic SQL injection tool. Its
goal is to detect and take advantage of SQL injection vulnerabilities in
web applications. Once it detects one or more SQL injections on the
target host, the user can choose among a variety of options to perform
an extensive back-end database management system fingerprint, retrieve
DBMS session user and database, enumerate users, password hashes,
privileges, databases, dump entire or user's specified DBMS
tables/columns, run his own SQL statement, read or write either text or
binary files on the file system, execute arbitrary commands on the
operating system, establish an out-of-band stateful connection between
the attacker box and the database server via Metasploit payload stager,
database stored procedure buffer overflow exploitation or SMB relay
attack and more.

<http://sqlmap.sourceforge.net>

## OWASP SQLiX

SQLiX is a tool, written in Perl, able to identify the back-end
database, find blind and normal injection and also execute system
commands on a Microsoft SQL Server. It was also successfully tested on
MySQL and PostgreSQL.

<http://www.owasp.org/index.php/Category:OWASP_SQLiX_Project>

## Scuba

Scuba is a Database vulnerability scanner able to find vulnerabilities
like unpatched software, unsafe processes and weak password on Oracle,
DB2, Microsoft SQL Server and Sybase.

<http://www.imperva.com/products/scuba.html>

## SQID SQL Injection Digger

SQL injection digger is a command line program, written in
[ruby](http://www.ruby-lang.org/), that looks for SQL injections and
common errors in websites. It can perform the following operations:

  - Look for SQL injection in a webpage, by looking for links
  - Submit forms in a webpage to look for SQL injection
  - Crawl a website to perform the above listed operations
  - Perform a google search for a query and look for SQL injections in
    the urls found

<http://sqid.rubyforge.org>

## SqlDumper

Exploiting a SQL injection vulnerability SqlDumper can make dump of any
file in the file system. It work only with DBMS MySql.

<http://www.ictsc.it/site/IT/projects/sqlDumper/sqlDumper.php>

## SQL Power Injector

SQL Power Injector is a .Net 1.1 application used to find and exploit
SQL Injection vulnerability through a vulnerable web application which
uses SQL Server, MySql, Sybase/Adaptive Server and DB2 Database
Management Systems as backend. It’s main feature is the support for
multithreaded automation of the injection.

<http://www.sqlpowerinjector.com>

## BobCat

BobCat is a tool based on “Data Thief” and realized in .NET 2.0. It
permits to take full advantage of SQL Injection vulnerability discovered
in a web application to steal data, gain a shell or a reverse shell on
the database management system machine. It has been tested on MSDE2000.

<http://www.northern-monkee.co.uk/index.html>

[Category:OWASP Backend Security
Project](Category:OWASP_Backend_Security_Project "wikilink")