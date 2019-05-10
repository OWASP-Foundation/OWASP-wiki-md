[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

## Objective

To produce applications which are secure out of the box.

## Platforms Affected

All.

## Relevant COBIT Topics

DS6 – Manage Changes – All sections should be reviewed

## Best Practices

Turn off all unnecessary features by default

  - Ensure that all switches and configuration for every feature is
    configured initially to be the safest possible choice.

<!-- end list -->

  - Inspect the design to see if the less safe choices could be designed
    in another way. For example, password reset systems are
    intrinsically unsound from a security point of view. If you do not
    ship this component, your application’s users will be safer.

<!-- end list -->

  - Do not rely on optionally installed features in the base code.

<!-- end list -->

  - Do not configure anything in preparation for an optionally
    deployable feature.

## Default passwords

Applications often ship with well-known passwords. In a particularly
excellent effort, NGS Software determined that Oracle’s “Unbreakable”
database server contained 168 default passwords out of the box.
Obviously, changing this many credentials every time an application
server is deployed is out of the question, nor should it be necessary.

### How to identify if you are vulnerable

  - Inspect the application’s manifest and ensure that no passwords are
    included in any form, whether within the source files, compiled into
    the code, or as part of the configuration.

<!-- end list -->

  - Inspect the application for usernames and passwords. Ensure that
    diagrams also do not have any.

### How to protect yourself

  - Do not ship the product with any configured accounts.

<!-- end list -->

  - Do not hard code any backdoor accounts or special access mechanisms.

## Secure connection strings

Connection strings to the database are rarely encrypted. However, they
allow a remote attacker who has shell access to perform direct
operations against the database or back end systems, thus providing a
leap point for total compromise.

### How to identify if you are vulnerable

  - Check your framework’s configuration file, registry settings, and
    any application based configuration file (usually config.php, etc)
    for clear text connection strings to the database.

### How to protect yourself

  - Sometimes, no password is just as good as a clear text password.

<!-- end list -->

  - On the Win32 platform, use “TrustedConnection=yes”, and create the
    DSN with a stored credential. The credential is stored as an LSA
    Secret, which is not perfect, but is better than clear text
    passwords.

<!-- end list -->

  - Develop a method to obfuscate the password in some form, such as
    “encrypting” the name using the hostname or similar within code in
    a non-obvious way.

<!-- end list -->

  - Ask the database developer to provide a library which allows remote
    connections using a password hash instead of a clear text
    credential.

## Secure network transmission

By default, no unencrypted data should transit the network.

### How to identify if you are vulnerable

  - Use a packet capture tool, such as Ethereal, and mirror a switch
    port near the database or application servers.

<!-- end list -->

  - Sniff the traffic for a while and determine your exposure to an
    attacker performing this exact same task.

### How to protect yourself

  - Use SSL, SSH and other forms of encryption (such as encrypted
    database connections) to prevent data from being intercepted or
    interfered with over the wire.

## Encrypted data

Some information security policies and standards require the database
on-disk data to be encrypted. However, this is essentially useless if
the database connection allows clear text access to the data. What is
more important is the obfuscation and one-way encryption of sensitive
data.

### How to identify if you are vulnerable

Highly protected applications:

  - Is there a requirement to encrypt certain data?

<!-- end list -->

  - If so, is it “encrypted” in such a fashion that allows a database
    administrator to read it without knowing the key?

If so, the “encryption” is useless and another approach is required.

### How to protect yourself

Highly protected applications and any application that has a requirement
to encrypt data:

  - Passwords should only be stored in a non-reversible format, such as
    SHA-256 or similar

<!-- end list -->

  - Sensitive data like credit cards should be carefully considered – do
    they have to be stored at all? **The PCI guidelines are very
    strict** **on the storage of credit card data**. '''We strongly
    recommend against it. '''

<!-- end list -->

  - Encrypted data should not have the key on the database server.

The last requirement requires the attacker to take control of two
machines to bulk decrypt data. The encryption key should be able to be
changed on a regular basis, and the algorithm should be sufficient to
protect the data in a temporal timeframe. For example, there is no point
in using 40 bit DES today; data should be encrypted using AES-128 or
better.

## PHP Configuration

## Global variables

`   Variables declared outside of functions are considered global by PHP. The opposite is that a variable declared inside a function, is considered to be in local function scope. PHP handles global variables quite differently than languages like C. In C, a global variable is always available in local scope as well as global, as long as it is not overridden by a local definition. In PHP things are different; to access a global variable from local scope you have to declare it global in that scope. The following example shows this:`

```

$sTitle = 'Page title'; // Global scope


function printTitle()

{

global $sTitle; // Declare the variable as global

    echo $sTitle; // Now we can access it just like it was a local variable

}
```

`   All variables in PHP are represented by a dollar sign followed by the name of the variable. The names are case-sensitive and must start with a letter or underscore, followed by any number of letters, numbers, or underscores.`

## register_globals

The register_globals directive makes input from GET, POST and COOKIE,
as well as session variables and uploaded files, directly accessible as
global variables in PHP. This single directive, if set in php.ini, is
the root of many vulnerabilities in web applications.

Let's start by having a look at an example:

```

if ($bIsAlwaysFalse)

{

    // This is never executed:

    $sFilename = 'somefile.php';

}''

//       ...

if ( $sFilename != '' )

{

    // Open $sFilename and send it's contents to the browser

    //      ...

}


```

If we were to call this page like: ***page.php?sFilename=/etc/passwd***
with register_globals set, it would be the same as to write the
following:

```

$sFilename = '/etc/passwd'; // This is done internally by PHP

if ( $bIsAlwaysFalse )

{       // This is never executed:

    $sFilename = 'somefile.php';

}

// ...

if ( $sFilename != '' )

{

    // Open $sFilename and send it's contents to the browser

    // ...

}
```

PHP takes care of the ***$sFilename = '/etc/passwd';*** part for us.
What this means is that a malicious user could inject his/her own value
for $sFilename and view any file readable under the current security
context.

We should always think of that “what if” when writing code. So turning
off register_globals might be a solution but what if our code ends up
on a server with register_globals on. We must bear in mind that all
variables in global scope could have been tampered with. The correct way
to write the above code would be to make sure that we always assign a
value to ***$sFilename***:

```

// We initialize $sFilename to an empty string

$sFilename = '';

if ( $bIsAlwaysFalse ) {

// This is never executed:

$sFilename = 'somefile.php';

}

...

if ( $sFilename != '' ) {

// Open $sFilename and send it's contents to the browser

...

}
```

Another solution would be to have as little code as possible in global
scope. Object oriented programming (OOP) is a real beauty when done
right and I would highly recommend you to take that approach. We could
write almost all our code in classes that is generally safer and
promotes reuse. Like we never should assume that register_globals is
off, we should never assume it is on. The correct way to get input from
GET, POST, COOKIE etc. is to use the superglobals that were added in PHP
version 4.1.0. These are the $_GET, $_POST, $_ENV, $_SERVER,
$_COOKIE, $_REQUEST $_FILES, and $_SESSION arrays. The term
superglobals is used since they are always available without regard to
scope.

'''register_globals '''

If set PHP will create global variables from all user input coming from
get, post and cookie. If you have the opportunity to turn off this
directive you should definitely do so. Unfortunately there is so much
code out there that uses it so you are lucky if you can get away with
it.

Recommended: off

'''safe_mode '''

The PHP safe mode includes a set of restrictions for PHP scripts and can
really increase the security in a shared server environment. To name a
few of these restrictions: A script can only access/modify files and
folders which has the same owner as the script itself. Some
functions/operators are completely disabled or restricted, like the
backtick operator.

'''disable_functions '''

This directive can be used to disable functions of our choosing.

'''open_basedir '''

Restricts PHP so that all file operations are limited to the directory
set here and its subdirectories.

'''allow_url_fopen '''

With this option set PHP can operate on remote files with functions like
include and fopen.

Recommended: off

'''error_reporting '''

We want to write as clean code as possible and thus we want PHP to throw
all warnings, etc. at us.

Recommended: E_ALL

'''log_errors '''

Logs all errors to a location specified in php.ini.

Recommended: on

'''display_errors '''

With this directive set, all errors that occur during the execution of
scripts, with respect to error_reporting, will be sent to the browser.
This is desired in a development environment but not on a production
server, since it could expose sensitive information about our code,
database or web server.

Recommended: off (production), on (development)

'''magic_quotes_gpc '''

Escapes all input coming in from post, get and cookie. This is something
we should handle on our own.

This also applies to **magic_quotes_runtime**.

Recommended: off

'''post_max_size, upload_max_filesize and memory_limit '''

These directives should be set at a reasonable level to reduce the risk
of resource starvation attacks.

## Database security

Data obtained from the user needs to be stored securely. In nearly every
application, insufficient care is taken to ensure that data cannot be
obtained from the database itself.

### How to identify if you are vulnerable

  - Does the application connect to the database using low privilege
    users?

<!-- end list -->

  - Are there different database connection users for application
    administration and normal user activities? If not, why not?

<!-- end list -->

  - Does the application make use of safer constructs, such as stored
    procedures which do not require direct table access?

<!-- end list -->

  - Highly protected applications:
      - Is the database is on another host? Is that host locked down?
      - All patches deployed and latest database software in use?
      - Does the application connect to the database using an encrypted
        link? If not, is the application server and database server in a
        restricted network with minimal other hosts, particularly
        untrusted hosts like desktop workstations?

### How to protect yourself

  - The application should connect to the database using as low
    privilege user as is possible.

<!-- end list -->

  - The application should connect to the database with different
    credentials for every trust distinction (e.g., user, read-only user,
    guest, administrators) and permissions applied to those tables and
    databases to prevent unauthorized access and modification.

<!-- end list -->

  - The application should prefer safer constructs, such as stored
    procedures which do not require direct table access. Once all access
    is through stored procedures, access to the tables should be
    revoked.

<!-- end list -->

  - Highly protected applications:
      - The database should be on another host, which should be locked
        down with all current patches deployed and latest database
        software in use.
      - The application should connect to the database using an
        encrypted link. If not, the application server and database
        server must reside in a restricted network with minimal other
        hosts.
      - Do not deploy the database server in the main office network.

## Further Reading

  - ITIL – Change Management <http://www.itil.org.uk/>

## ColdFusion Components (CFCs)

This section provides guidance on using ColdFusion components (CFCs)
without exposing your web application to unnecessary risk. ColdFusion
provides two ways of restricting access to CFCs; role-based security and
access control.

Role-based security is implemented by the ***roles*** attribute of the
<cffunction> tag. The attribute contains a comma-delimited list of
security roles that can call this method.

Access control is implemented by the ***access*** attribute of the
<cffunction> tag. The possible values of the attribute in order of most
restricted behavior are: private (strongest), package, public (default),
and remote (weakest).

**Private:** The method is accessible only to methods within the same
component. This is similar to the Object Oriented Programming (OOP)
private identifier.

**Package:** The method is accessible only to other methods within the
same package. This is similar to the OOP protected static identifier.

**Public:** The method is accessible to any CFC or CFM on the same
server. This is similar to the OOP public static identifier.

**Remote:** Allows all the privileges of public, in addition to
accepting remote requests from HTML forms, Flash, or a web services.
This option is required, to publish the function as a web service.

**Best Practices**

  - Do not use THIS scope inside a component to expose properties. Use a
    getter or setter function instead. For example, instead of using
    THIS.myVar create a public function that sets the variable (i.e.
    setMyVar(value)).

<!-- end list -->

  - Do not omit the role attribute as ColdFusion will not restrict user
    access to the function.

<!-- end list -->

  - Avoid using Access=”Remote” if you do not intend to call the
    component directly from a URL.

## Configuration

The following section describes some of the server-wide security-related
options available to a ColdFusion administrator via the ColdFusion MX 7
Administrator console web application
(http://servername:port/CFIDE/administrator/index.cfm). If the console
application is unavailable, you can modify these options by editing the
XML files in the cf_root/lib/ (Server configuration) or
cf_web_root/WEB-INF/cfusion/lib (J2EE configuration) directory;
however, editing these files directly is not recommended.

'''Best Practice '''

  - CF Admin Password screen

<!-- end list -->

  - Enable a strong Administrator password
      - **The ColdFusion Administrator is the default interface for
        configuring the ColdFusion application server. It is secured by
        a single password. Ensure that the Administrator security is
        enabled and the password is strong and stored in a secure
        place.**
      - Ensure the checkbox is filled
      - Enter and confirm a strong password string of 8 characters or
        more
      - Click Submit Changes

**Sandbox Security screen**

Enable Sandbox Security

**The ColdFusion Sandbox allows you to place access security
restrictions on files, directories, methods, and data sources. Sandboxes
make the most sense for a hosting provider or corporate intranet where
multiple applications share the same server. Enable this option.**

**Next, a sandbox needs to be configured, because if not all code in all
directories will execute without restriction. Code in a directory and
its subdirectories inherits the access controls defined for the sandbox.
For example, if ABC Company creates multiple applications within their
directory all applications will have the same permissions as the parent.
A sandbox applied to ABC-apps will apply to app1 and app2. A sample
directory structure is shown below:**

**D:\\inetpub\\wwwroot\\ABC-apps\\app1**

**D:\\inetpub\\wwwroot\\ABC-apps\\app2**

**Note: if a new sandbox is created for app2 then it will not inherit
settings from ABC-apps.**

**Sandbox security configurations are application specific; however,
there are general guidelines that should be followed:**

Create a default restricted sandbox and copy setting to each subsequent
sandbox removing restrictions as needed by the application. Except in
the case of files/directories where access is granted rather than
restricted.

Restrict access to data sources that should not be accessed by the
sandboxed application.

Restrict access to powerful tags, for example CFREGISTRY and CFEXECUTE.

Restrict file and directory access to limit the ability of tags and
functions to perform actions to specified paths.

***Every*** application should have a sandbox.

In multi-homed environments disable Java Server Pages (JSP) as
ColdFusion is unable to restrict the functionality of the underlying
Java server.

**RDS Password screen**

Enable a strong RDS password

**Developers can access ColdFusion resources (files and data sources)
over HTTP from Macromedia Dreamweaver MX and HomeSite+ through
ColdFusion’s Remote Development Services (RDS). This feature is password
protected should only be enabled in secure development environments.**

Ensure the checkbox is filled

Enter and confirm a strong password string of 8 characters or more

Click Submit Changes

Use RDS over SSL - During development, you should use SSL v3 to encrypt
all RDS communications between Dreamweaver MX and the ColdFusion server.
This includes remote access to server data sources and drives, provided
that both are accessed through RDS.

Disable RDS in Production

**In production environments, you should not use RDS. In earlier
versions of ColdFusion, RDS ran as a separate service or process and
could be disabled by disabling the service. In ColdFusion MX, RDS is
integrated into the main service. To disable it, you must disable the
RDSServlet mapping in the web.xml file. The following procedure assumes
that ColdFusion is installed in the default location.**

**1. Back up the C:\\CFusionMX7\\wwwroot\\WEB-INF\\web.xml file.**

**2. Open the web.xml file for editing.**

**3. Comment out the RDSServlet mapping, as follows:**

**\<\!—**

'''<servlet-mapping> '''

'''<servlet-name>RDSServlet</servlet-name> '''

'''<url-pattern>/CFIDE/main/ide.cfm</url-pattern> '''

**</servlet-mapping>**

'''--\> '''

**4. Save the file.**

**5. Restart ColdFusion.**

Settings Screen

Enable a Request Timeout

**ColdFusion processes requests simultaneously and queues all requests
above the configured maximum number of simultaneous requests. If
requests run abnormally long, this can tie up server resources and lead
to DoS attacks. This setting will terminate requests when the configured
timeout is reached.**

Fill the checkbox next to “Timeout Request after (seconds)”

Enter the number of seconds for ColdFusion to allow threads to run

**To allow a valid template request to run beyond the configured
timeout, place a <cfsetting> atop the base ColdFusion template and
configure the RequestTimeout attribute for the necessary amount of time
(in seconds).**

Use UUID for cftoken

**Best practice calls for J2EE session management. In the event that
only ColdFusion session management is available, strong security
identifiers must be used. Enable this setting to change the default
8-character CFToken security token string to a UUID.**

Enable Global Script Protection - This is a new security feature in
ColdFusion MX 7 that isn’t available in other web application platforms.
It helps protect Form, URL, CGI, and Cookie scope variables from
cross-site scripting attacks.

Specify a Site-wide Error Handler

**Prevent information leaks through verbose error messages. Specifying a
site-wide error handler covers you when cftry/cfcatch are not used. This
page should be a generic error message that you return to the user.
Also, if the error handler displays user-input, it should be reviewed
for potential cross-site scripting issues.**

Specify a Missing Template Handler

**Provide a custom message page for HTTP 404 errors when the server
cannot find the requested ColdFusion template.**

Configure a memory throttling

**To prevent file upload DoS attacks, Macromedia added new configuration
settings to ColdFusion MX 7.0.1 that allow administrators to restrict
the total upload size of HTTP POST operations. Configure these settings
accordingly.**

maximum size for post data

**This is the total size that ColdFusion will accept for any single HTTP
POST request (including file uploads). ColdFusion will reject any
request whose Content-size header exceeds this setting.**

Request Throttle Threshold

**HTTP POST requests larger than this setting (default is 4MB) are
included in the total concurrent request memory size and get queued if
they exceed the Request Throttle Memory setting.**

Request Throttle Memory

'''This sets the total amount of memory (MB) ColdFusion reserves for
concurrent HTTP POST requests. Any requests exceeding this limit are
queued until enough memory is available. '''

**Memory Variables screen**

Enable J2EE Session Management and Use J2EE session variables.

Best practice requires J2EE sessions because they are more secure than
regular ColdFusion sessions. (See Session Management section)

Select checkbox next to “Enable Session Variables”

Select checkbox next to “Enable J2EE session variables”

Set the maximum session timeout to 20 minutes to limit the window of
opportunity for session hijacking.

Set the default session timeout to 20 minutes to limit the window of
opportunity for session hijacking. (The default value is 20 minutes.)

The session-timeout parameter in the cf_root/WEB-INF/web.xml file
establishes the maximum J2EE session timeout. This setting should always
be greater-than or equal-to ColdFusion’s Maximum Session Timeout value.

Set the maximum application timeout to 24 hours.

Set the default application timeout to 8 hours.

**Data Sources screen**

Do not use an administrative account to connect ColdFusion to a data
source. For example, do not use SA account to connect to a MS SQL
Server. The account accessing the database should be granted specific
privileges to the objects it needs to access. In addition, the account
created to connect the database should be an OS-based, not a SQL
account. Operating system accounts have many more auditing, password,
and other security controls associated with them. For example, account
lockouts and password complexity requirements are built into the Windows
operating system; however, a database would need custom code to handle
these security-related tasks.

Disable the following Allowed SQL options for all data sources:

Create

Drop

Grant

Revoke

Alter

**As an administrator, you do not have control over what a developer
sends to the database; however, there should be no circumstance where
the previous commands need to be sent to a database from a web
application.**

**Debugging Settings screen**

Disable Robust Exception for production servers. (Default)

Disable Debugging for production servers. (Default)

**Debugging IP Addresses**

Ensure only the addresses of trusted clients are in the IP list.

Only allow the localhost IP (127.0.0.1) in the list on production
machines

**Mail screen**

Require a user name and password to authenticate to your mail server.

Set the connection timeout to 60 seconds (The default value is 60
seconds.)

## Links

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")
[category:Deployment](category:Deployment "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Secure Lifecycle](Category:Activity "wikilink")