__TOC__

## Introduction

As part of the code review, you may need to step outside the code review
box to assess the security of a database such as MySQL. The following
covers areas which could be looked at.

### Privileges

**Grant_priv**: Allows users to grant privileges to other users. This
should be appropriately restricted to the DBA and Data (Table) owners.
Give specific permissions on an as needed basis and use different logins
for different purposes.

`Select * from user `
`where Grant_priv = 'Y'; `

`Select * from db `
`where Grant_priv = 'Y';`

`Select * from host `
`where Grant_priv = 'Y';`

`Select * from tables_priv`
`where Table_priv = 'Grant';`

**Alter_priv**: Determine who has access to make changes to the
database structure (alter privilege) at a global, database, and table
level.

`Select * from user `
`where Alter_priv = 'Y';`

`Select * from db `
`where Alter _priv = 'Y';`

`Select * from host`
`where Alter_priv = 'Y';`

`Select * from tables_priv`
`where Table_priv = 'Alter';`

#### MySQL Configuration File

Check for the following:

`a) skip-grant-tables`
`b) safe-show-database`
`c) safe-user-create`

**a)** This option causes the server not to use the privilege system at
all. All users have full access to all tables.

**b)** When the **SHOW DATABASES** command is executed, it returns only
those databases for which the user has some kind of privilege. Default
since MySQL v4.0.2.

**c)** With this enabled a user can't create new users with the GRANT
command as long as the user does not have the **INSERT** privilege for
the **mysql.user table**.

#### User Privileges

Here we can check which users have access to perform potentially
malicious actions on the database. "Least privilege" is the key point
here:

`Select * from user where `
`Select_priv  = 'Y' or Insert_priv  = 'Y'`
`or Update_priv = 'Y' or Delete_priv  = 'Y'`
`or Create_priv = 'Y' or Drop_priv    = 'Y'`
`or Reload_priv = 'Y' or Shutdown_priv = 'Y'`
`or Process_priv = 'Y' or File_priv    = 'Y'`
`or Grant_priv   = 'Y' or References_priv = ‘Y'`
`or Index_priv = 'Y' or Alter_priv = 'Y';`

`Select * from host `
`where Select_priv  = 'Y' or Insert_priv  = 'Y'`
`or Create_priv = 'Y' or Drop_priv    = 'Y'`
`or Index_priv = 'Y' or Alter_priv = 'Y'; `
`or Grant_priv   = 'Y' or References_priv = ‘Y'`
`or Update_priv = 'Y' or Delete_priv  = 'Y'`

`Select * from db `
`where Select_priv  = 'Y' or Insert_priv  = 'Y'`
`or Grant_priv   = 'Y' or References_priv = ‘Y'`
`or Update_priv = 'Y' or Delete_priv  = 'Y'`
`or Create_priv = 'Y' or Drop_priv    = 'Y'`
`or Index_priv = 'Y' or Alter_priv = 'Y';`

### Default MySQL Accounts

The default account in MySQL is "root"/"root@localhost" with a blank
password. We can check if the root account exists by:

`SELECT User, Host `
`FROM user`
`WHERE User = 'root';`

Set a password for "root" user. But don't run MySql as root. Create
separate user for the Database connection with only required privileges.

### Remote Access

MySQL by default listens on port 3306. If the app server is on localhost
also, we can disable this port by adding **skip-networking** to the
\[mysqld\] in the my.cnf file.

Also you should change the Default port number from 3306 to some other
port. Additionally, you can use **bind= local_ip** in /etc/my.cnf file.
this will ensure that you DB is not accessible on Public IP.

### Additional Chacks

1\. Avoid " SELECT \* " in queries.

2\. Create views to simplify commonly-used Table joins.

3\. Strictly avoid plain text passwords in Scripts and tables.

4\. Avoid using FQDN or hostnames when granting access.

5\. Use phpMyAdmin to add a user.

6\. Check for CHANGE LOG file to see if patches are applied.

7\. Remove test database and access to it.

8\. Do not create demo or test databases on production servers, keep it
clean and safe.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")