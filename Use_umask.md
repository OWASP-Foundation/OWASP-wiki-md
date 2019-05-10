## Background

As you know, you can change permissions in \*nix using the chmod
command. However, as chmod works on existing files only, how can you
make sure that files created later have the same permissions?

To illustrate the point, suppose you want all the files in the directory
to have permission r--r--r-- (or 444). You could easily do that by
issuing:

$ chmod 444 \* Now create a simple file on the directory without
contents, and check its permissions.

$ touch a_file.txt $ ls -l a_file.txt -rw-r--r-- 1 orasoft dba 0 Oct
21 13:44 a_file.txt

The permissions are set to Read+Write for owner, Read for group, and
Read for others (or 644), not 444 as you wanted. Why not?

The exact permissions set on a newly created file is dictated by a
special parameter called umask. The umask is a set of values that is
subtracted from the all-permissions to arrive at the permission value of
the new file. For example, if you have umask set to 777, it's subtracted
from the overall permission value 777, resulting in 000—no permissions
on the new file. Let's see an example:

$ umask 777 $ touch b_file.txt $ ls -l ?_file.txt -rw-r--r-- 1 oracrmp
dba 0 Oct 21 13:44 a_file.txt ---------- 1 oracrmp dba 0 Oct 21 13:53
b_file.txt

Note the permission on the file b_file.txt; it's 000, or ---------.
Also note that the file previously created—a_file.txt—is still set to
its original permissions. The setting of umask—777—resulted in the
permissions on the new file.

The umask is a powerful and effective way to set permissions for the
different files Oracle will create.

## Strategy

The overall umask of the Oracle software owner should be 022, which
results in the files as Read+Write by owner and Read by all others. You
can place this in the login profile file of the user so that it takes
effect at all times.

There are many different types of files used by Oracle—data files, redo
log files, trace files, and so on. Datafiles may be known beforehand and
you can easily change their permissions, but tracefiles are generated at
runtime. Thus, you should use umask to ensure the files are not exposed
to any external users—trace files contain a variety of confidential
information that can be exploited by hackers. For instance, someone
could theoretically steal data files by copying them, mount them on a
separate server, and bring the database up to rifle through its
contents.

Set the umask for the directories as shown below:

Directory

`Description `
`umask `

Directory specified by the initialization parameter
background_dump_dest

`Some trace files are generated here as well as the database alert log. Permissions should be rw------- (Read+Write by Oracle software owner only). `
`0177 `

Directory specified by the initialization parameter user_dump_dest

`Trace files are generated here. Permissions should be the same as above. `
`0177 `

$ORACLE_HOME/rdbms/log

`Some database log files are generated here. Permissions should be the same as above. `
`0177 `

$ORACLE_HOME/rdbms/audit

`Audit trails of database audit are stored here by default, unless you have set the audit_file_dest initialization parameter. Permissions should be the same as above. Even if you have DB audit trail, some common events such as SYSDBA connections and database startup/shutdown are always audited and placed here. `
`0177 `

Directory specified by the initialization parameter audit_file_dest

`Audit trails of database audit are stored here by default, unless you have set the audit_file_dest initialization parameter. Permissions should be the same as above. `
`0177 `

## Implications

Setting the umask in this manner might prevent some developers from
accessing the session trace files, which are generated in the
user_dump_dest directory and fed to tkprof to be formatted. Therefore,
you may want to relax the rules on that directory only.

## Action Plan

Change umask on background_dump_dest to 0177. Change umask on
$ORACLE_HOME/rdbms/log to 0177. Change umask on
$ORACLE_HOME/rdbms/audit to 0177. Change umask on audit_file_dest to
0177. (Optional) Change umask on user_dump_dest to 0177.