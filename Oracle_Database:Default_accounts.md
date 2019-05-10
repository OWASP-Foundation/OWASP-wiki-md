## Status

WIP 14/11/2008

## Overview

Oracle default accounts can be created for many different reasons. They
are created by Oracle itself when the database is created. For instance
the accounts SYS and SYSTEM, DBSNMP and OUTLN are often created by
default when a database is created. If the database is created by using
the wizard the problem can be much bigger with 10s 0r 20s of accounts
being created simply as part of the database creation. Further default
accounts can be created after the initial database creation by running
scripts that live in the $ORACLE_HOME/rdbms/admin or other directories.
These scripts can be run to add an additional feature or function or to
add example code to the database (You never do this is production do
you?). Further Oracle default users can be created when third party
software is installed for use such as BAAN or SAP. The same issues of
default users being added to the database can occur when third party
development or maintenance tools are added such as TOAD or PL/SQL
Developer. Problems can also occur when employees run examples from
books, or documentation (official and non-official), books or web sites.

## Resources

  - \[1\] [Pete Finnigan's default password MS Excel
    sheet](http://www.petefinnigan.com/default/oracle_default_passwords.xls)

[Category:OWASP Oracle
Project](Category:OWASP_Oracle_Project "wikilink")