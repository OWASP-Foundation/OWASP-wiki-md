## Background

Oracle users can be authenticated in different ways, most commonly via
database authentication. When a user is created as create user ananda
identified by abc123, the only way the user can log in to database is by
passing its userid and password.

One alternative is operating system authentication, in which the user is
created as:

create user ops$ananda identified externally; If the host operating
system has a userid named "ananda", then Oracle does not check its
credentials anymore. It simply assumes the host must have done its
authentication and lets the user into the database without any further
checking.

That's where the problem lies. If the host operating system is strong in
authentication, it may be secure; but in some weak OSs, it is possible
to login as a user by cracking the password or entering without a
password:

sqlplus / Note the lack of userid and password—the string "/" instructs
the database to accept the connection of the userid ananda to the
database account ops$ananda.

This type of authentication commonly useful in shell scripts so that you
don't have to embed the password in the script, but simply call it as
sqlplus /. This is not only convenient but also somewhat secure, since
the password is not present. However, consider this scenario: In
weak-security OSs, someone can create an account called ananda and then
use it to log into account ops$ananda.

Must it be ops$? Not really; you can change it by setting an
initialization parameter. In the following example, I have set it to
osauthent$.

os_authent_prefix = 'osauthent$' You can find these users by using the
following query:

SQL\> select username, password from dba_users

` 2  where password = 'EXTERNAL'`
` 3  /`

USERNAME PASSWORD ------------------------------
------------------------------ OPS$ANANDA EXTERNAL OPS$ORACLE EXTERNAL

When the initialization parameter is set like this, the account
ops$ananda will not work; instead, you need to create those accounts
(OS-authenticated) as osauthent$ananda. In an interesting twist , you
can also set it to "" (null). In that case the OS user ananda will map
to Oracle user ananda. You can even set the password for this account:

alter user ops$ananda identified by oracle; In that case, the user can
log into the database in either manner:

sqlplus / sqlplus ops$ananda/oracle

So, what's wrong with that? Well, consider the situation. Suppose the
parameter os_authent_prefix is set to "" (null). In a weak OS, someone
can create a user called SYSTEM and login as

sqlplus / This will log the user as the Oracle user SYSTEM\! Once logged
in, the user can do anything they want—create users, drop data files,
look into sensitive data, and a lot of other things. Suddenly, something
that seemed like a convenience is a huge liability.

## Srategy

As you can see, the issue arises only in certain combination of
occurrences. One of them is the OS_AUTHENT_PREFIX being not null, and
the other one is setting the password for OS-authenticated accounts. So
the first thing to check is the OS authentication prefix.

SQL\> select value

` 2  from v$parameter`
` 3  where name = 'os_authent_prefix';`

VALUE

-----

ops$

If the above returns null, then you should make plans to change it. The
actual value is not important, but you must include some
non-alphanumeric character. That way, the OS-authenticated username will
never match an actual user.

Second, you need to make sure the OS-authenticated accounts are
authenticated exactly that way—by the OS—and never have a password. For
example, if your OS_AUTHENT_PREFIX were set to OPS$, you would use the
following query to find out whether or not the password is set:

SQL\> select username, password from dba_users

` 2  where username like 'OPS$%';`

USERNAME PASSWORD ------------------------------
------------------------------ OPS$ORACLE 17C96FEC14DC431F OPS$ANANDA
EXTERNAL

This shows that the user OPS$ORACLE cannot login through the OS
authentication route or the password route. This is exactly what you
want to avoid; there should be only one way to authenticate. To change
the mode of authentication of OPS$ORACLE, you should use:

alter user OPS$ORACLE identified externally; This changes the PASSWORD
column to EXTERNAL.

## Implications

The implications of these changes may be extensive depending on the
usage of these accounts. If you have any of these types of accounts,
scan the programs to find out how easily they can be changed. Action
Plan Find out which programs are using the OPS$ accounts. If none then

` Check initialization parameter os_authent_prefix`

If it's null then

`   Change it to OPS$ (database restart required) `
` Check password of OPS$ accounts`

If not EXTERNAL then

`   Change them to EXTERNAL `

If some then

` Check if they are using it as a password as well (e.g. OPS$ORACLE/mypass).`

If a password is used, remove it—e.g. the line sqlplus OPS$ORACLE/mypass
should become sqlplus /.