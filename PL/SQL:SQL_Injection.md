## Status

WIP 13/11/2008

## Overview

As the name implies, SQL injection vulnerabilities allow an attacker to
inject (or execute) SQL commands within an application. It is one of the
most wide spread and dangerous application vulnerability. The CLASP
project provides a good overview of [SQL
injection](SQL_injection "wikilink").

## Attack

## Vunerabilities

### UNIONS

Append the output of one or more other statements

### SUBSELECTS

Blind SQL injection

### PACKAGES

functions

### DML

Insert, update and delete

### DDL

Alter .. in case of a dynamic query.

### Viewa

It is possible to update a view

### Database links

Query other databases with @database link

## Solution

The reason that SQL injection is possible, is that the SQL statement is
being generated from a language or enviroment that isn't working with
SQL natively. So it does not know the consequences. The same goes for
the database itself. As long as the SQL statement is syntactally correct
and user that performs it has the rights, the database will execute it.
There is no way for both side to determine what the impact would be.
When trying to figure that out your essentially blacklisting and any new
variant will be bypass your predetermined.

### Stored Procedures

We allready creating stored procedures since we are working with PL/SQL
and as you can see it is still possible to write vunerable code. Plus
there is an extra vunerabilty when running on the database,
[PL/SQL:Privilege escalation](PL/SQL:Privilege_escalation "wikilink")

### Obfuscation

Another solution often found is to obfuscate the table and columns. So
instead of using APPUSERS we call it CWO2HIF. Now this is not going to
work as one of the 13 rules that describe an Relational Database\[4\] is
that the metadata or catalog describing the database is stored in the
database. For instance a query on ALL_TAB_COLUMNS would return me all
the available tables, it columns and the types.

All of these just dont work or limit just a small part, so we need to
make the understand eachother better. We can do this by seperating the
data from the logic.

### Bind variables

As with all languages and databases, the seperation of the SQL logic and
the SQL data is the only way to prevent SQL injection. These are
placeholders we can use to tell the database these parts of the query
are dynamic and the rest is hardcoded. The communication is split up
into multiple packages

But this is how a database wants you to communicate with it. Whenever a
query passed to an Oracle database for execution, the first thing the
RDMS will do is make a hashvalue of the query. Next it will to find the
best way to collect the data that is needed and stores that in it's
memory. After he is done with that it will selects the data and pass it
on to the requester. A general rule is that if a query is responds
within several seconds it was probaly spending more time in optimisation
than the actual fetching.

When you are hardparsing each query, which is essentially the same but
using diffrent parameters or values to match, this will result in a
diffrent hash value for each statement. Thus the DBMS has to do it's
work again. When you are softparsing (ie. using bind variables) the
first time you execute the query it will take a fraction longer than the
hardparsed version as it needs to send more packages to the database.
But each time thereafter the database can skip that bit and just fetch
what is needed. And if it is still in the buffercache even give you the
results immediatly.

This is probably the only attackvector that when it is correctly fixed,
it will also give you an performance improvement :)

## Resources

  - \[1\] [Oracle's own paper on how to prevent SQL injection in PL/SQL,
    October 2008](http://www.oracle.com/technology/tech/pl_sql/pdf/how_to_write_injection_proof_plsql.pdf)
  - \[2\] [David Litchfield's presentation on SQL injection at Black
    Hat,
    May 2004](http://www.blackhat.com/presentations/bh-europe-04/bh-eu-04-litchfield.pdf)
  - \[4\] [Codd's 12 rules
    (0..12)](http://en.wikipedia.org/wiki/Codd's_12_rules)

[Category:OWASP Oracle
Project](Category:OWASP_Oracle_Project "wikilink")
[Category:SQL](Category:SQL "wikilink")