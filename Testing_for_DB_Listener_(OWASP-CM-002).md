## Brief Summary

The database (DB) listener is a network daemon unique to Oracle
databases. It waits for connection requests from remote clients. This
daemon can sometimes be compromised and hence can affect the
availability of the database or the validity of data stored within it.

## Description of the Issue

The DB listener is the entry point for remote connections to an Oracle
database. It listens for connection requests and handles them
accordingly. The testing outlined in this section is possible if the
tester can access this service -- the test should be done from the
Intranet (major Oracle installations don't expose this service to the
external network). The listener, by default, listens on port 1521 (port
2483 is the new officially registered port for the TNS Listener and 2484
for the TNS Listener using SSL). It is a good practice to change the
listener from this port to another arbitrary port number. If this
listener is "turned off" remote access to the database is not possible.
If this is the case, one's application would fail, resulting in a denial
of service.

**Potential areas of attack:**

  - Stop the Listener - Create a DoS attack.
  - Set a password and prevent others from controlling the Listener -
    Hijack the DB.
  - Write trace and log files to any file accessible to the process
    owner of tnslnsr (usually Oracle) - Possible information leakage.
  - Obtain detailed information on the Listener, database, and
    application configuration.

## Black Box testing and example

Upon discovering the port on which the listener resides, one can assess
the listener by running a tool developed by Integrigy:

<center>

![Image:Listener_Test.JPG](Listener_Test.JPG "Image:Listener_Test.JPG")

</center>

The tool above checks the following:
**Listener Password** On many Oracle systems, the listener password may
not be set. The tool above verifies this. If the password is not set, an
attacker could set the password and hijack the listener, albeit the
password can be removed by locally editing the Listener.ora file.

**Enable Logging** The tool above also tests to see if logging has been
enabled. If it has not, one would not detect any change to the listener
or have a record of it. Also, detection of brute force attacks on the
listener would not be audited.

**Admin Restrictions** If Admin restrictions are not enabled, it is
possible to use the "SET" commands remotely.

**Example** If you find a TCP/1521 open port on a server, you may have
an Oracle Listener that accepts connections from the outside. If the
listener is not protected by an authentication mechanism, or if you can
find easily a credential, it is possible to exploit this vulnerability
to enumerate the Oracle services. For example, using LSNRCTL(.exe)
(contained in every Client Oracle installation), you can obtain the
following output:

    TNSLSNR for 32-bit Windows: Version 9.2.0.4.0 - Production
    TNS for 32-bit Windows: Version 9.2.0.4.0 - Production
    Oracle Bequeath NT Protocol Adapter for 32-bit Windows: Version 9.2.0.4.0 - Production
    Windows NT Named Pipes NT Protocol Adapter for 32-bit Windows: Version 9.2.0.4.0 - Production
    Windows NT TCP/IP NT Protocol Adapter for 32-bit Windows: Version 9.2.0.4.0 - Production,,
    SID(s): SERVICE_NAME = CONFDATA
    SID(s): INSTANCE_NAME = CONFDATA
    SID(s): SERVICE_NAME = CONFDATAPDB
    SID(s): INSTANCE_NAME = CONFDATA
    SID(s): SERVICE_NAME = CONFORGANIZ
    SID(s): INSTANCE_NAME = CONFORGANIZ

The Oracle Listener permits you to enumerate default users on Oracle
Server:

    User name   Password
    OUTLN          OUTLN
    DBSNMP         DBSNMP
    BACKUP         BACKUP
    MONITOR        MONITOR
    PDB            CHANGE_ON_INSTALL

In this case, we have not found privileged DBA accounts, but OUTLN and
BACKUP accounts hold a fundamental privilege: EXECUTE ANY PROCEDURE.
This means that it is possible to execute all procedures, for example
the following:

`exec dbms_repcat_admin.grant_admin_any_schema('BACKUP');`

The execution of this command permits one to obtain DBA privileges. Now
the user can interact directly with the DB and execute, for example:

`select * from session_privs ;`

The output is the following screenshot:

<center>

![Image:ToadListener2.PNG](ToadListener2.PNG "Image:ToadListener2.PNG")

</center>

The user can now execute a lot of operations, in particular:
DELETE ANY TABLE
DROP ANY TABLE
**Listener default ports** During the discovery phase of an Oracle
server one may discover the following ports. The following is a list of
the default ports:

`1521: Default port for the TNS Listener. `
`1522 – 1540: Commonly used ports for the TNS Listener`
`1575: Default port for the Oracle Names Server`
`1630: Default port for the Oracle Connection Manager – client connections`
`1830: Default port for the Oracle Connection Manager – admin connections`
`2481: Default port for Oracle JServer/Java VM listener`
`2482: Default port for Oracle JServer/Java VM listener using SSL`
`2483: New port for the TNS Listener`
`2484: New port for the TNS Listener using SSL`

## Gray Box testing and example

**Testing for restriction of the privileges of the listener**: It is
important to give the listener least privilege so it cannot read or
write files in the database or in the server memory address space.

The file *Listener.ora* is used to define the database listener
properties. One should check that the following line is present in the
Listener.ora file: **ADMIN_RESTRICTIONS_LISTENER=ON**
**Listener password**: Many common exploits are performed due to the
listener password not being set. By checking the Listener.ora file, one
can determine if the password is set:

The password can be set manually by editing the Listener.ora file. This
is performed by editing the following: PASSWORDS_<listener name>. This
issue with this manual method is that the password stored in cleartext,
and can be read by anyone with acess to the Listener.ora file. A more
secure way is to use the LSNRCTRL tool and invoke the *change_password*
command.

`LSNRCTL for 32-bit Windows: Version 9.2.0.1.0 - Production on 24-FEB-2004 11:27:55`
`Copyright (c) 1991, 2002, Oracle Corporation.  All rights reserved.`
`Welcome to LSNRCTL, type "help" for information.`
`LSNRCTL> set current_listener listener`
`Current Listener is listener`
`LSNRCTL> change_password`
`Old password:`
`New password:`
`Reenter new password:`
`Connecting to `

<ADDRESS>

`Password changed for listener`
`The command completed successfully`
`LSNRCTL> set password`
`Password:`
`The command completed successfully`
`LSNRCTL> save_config`
`Connecting to `

<ADDRESS>

`Saved LISTENER configuration parameters.`
`Listener Parameter File   D:\oracle\ora90\network\admin\listener.ora`
`Old Parameter File   D:\oracle\ora90\network\admin\listener.bak`
`The command completed successfully`
`LSNRCTL>`

## References

**Whitepapers**

  - Oracle Database Listener Security Guide -
    <http://www.integrigy.com/security-resources/whitepapers/Integrigy_Oracle_Listener_TNS_Security.pdf>

**Tools**

  - TNS Listener tool (Perl) -
    <http://www.jammed.com/%7Ejwa/hacks/security/tnscmd/tnscmd-doc.html>
  - Toad for Oracle - <http://www.quest.com/toad>