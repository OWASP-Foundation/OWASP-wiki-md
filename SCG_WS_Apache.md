**NEEDS TO BE REVIEWED, SEE REFERENCES BELOW FOR ANY QUERIES\!**

## Summary

The Apache HTTP Server Project is a collaborative software development
effort aimed at creating a robust, commercial-grade, featureful, and
freely-available source code implementation of an HTTP (Web) server. The
project is jointly managed by a group of volunteers located around the
world, using the Internet and the Web to communicate, plan, and develop
the server and its related documentation. This project is part of the
Apache Software Foundation. In addition, hundreds of users have
contributed ideas, code, and documentation to the project. This file is
intended to briefly describe the history of the Apache HTTP Server and
recognize the many contributors.

## Important Files of Apache Server

### Apache Global Server Configuration Files

Debian

    /etc/apache2/apache2.conf

RHEL / Red Hat / CentOS / Fedora Linux

    /etc/httpd/conf/httpd.conf

FreeBSD

    /usr/local/etc/apache2X/httpd.conf

Note:X represents the version number

### Apache Module Files

Debian

    /etc/apache2/mods-enabled

RHEL / Red Hat / CentOS / Fedora Linux

    /etc/httpd/conf/conf.d

### Apache Port Configuration File

Debian

    /etc/apache2/ports.conf

RHEL / Red Hat / CentOS / Fedora Linux

    /etc/httpd/conf/conf.d

### Apache Error Files

Debian

    /var/log/apache2/error.log

RHEL / Red Hat / CentOS / Fedora Linux

    var/log/httpd/error_log

FreeBSD

    /var/log/httpd-error.log

## Apache Server Information Leakage

### Server Token Directive

#### Description

This Directive Controls wheather Server response field is sent back to
clients includes a description of Generic OS Type of the Server.

    Server: Apache/2.2.14 (Unix) mod_ssl/2.2.14 OpenSSL/0.9.8e-fips-rhel5

This allows attackers to identify web servers details greatly and
increases the efficiency of any attack,as security vulnerabilities are
dependent upon specific software versions.

#### How to test

In order to test for ServerToken configuration, one should check the
Apache configuration file.

#### Misconfiguration

    ServerTokens Full

#### Remediation

Configure the ServerTokens directive in the Apache configuration to
value of Prod or ProductOnly. This tells Apache to only return "Apache"
in the Server header, returned on every page request.

    ServerTokens Prod
    or
    ServerTokens ProductOnly

### Server Signature

#### Description

This Apache directive allows the configuration of a trailing footer line
under server-generated documents.

#### How to test

In order to test for ServerSignature configuration, one should check the
Apache configuration file.

#### Misconfiguration

    ServerSignature On

#### Remediation

Configure the ServerSingature directive in the Apache configuration to
value of "Off". This tell Apache not to display the server version on
error pages, or other pages it generates.

```
 ServerSignature Off
```

## Operating System Privileges for Apache

### Run Apache with least privilege user

#### Description

Apache typically is started with root privileges in order to listen on
port 80 and 443. One of the best ways to reduce your exposure to attack
when running a web server is to create a unique, unprivileged userid and
group for the web daemon to execute. The “nobody” or “daemon” userid &
group that come default on Unix variants should NOT be used to run the
web server as these principals are commonly used by other daemon
services. Instead, create a user and group that are exclusively used by
the web service so as to not give unnecessary access to other services.
The userid used for the apache user should be a unique value between 1
and 499 as these lower values are reserved for the special system
accounts. A more secure alternative is to bind Apache web service to an
unprivileged port so it is not necessary to start Apache as root.

#### How to test

Ensure the apache account is unique and has been created with a UID
between1-499 with the apache group and configured in the Apache
Configuration File.

#### Misconfiguration

#### Remediation

If the Apache user and group does exist, create the account and group as
a unique system account.

Example:

    # groupadd –r apache
    # useradd apache -r -g apache -d /var/www -s /sbin/nologin

2\. Configure the Apache user and group in the Apache configuration
file.

    User apache
    Group apache

### Restrict Shell Access for Apache User

#### Description

The Apache account must not be used as a regular login account, and
should be assigned an invalid or nologin shell to ensure that the
account cannot be used to login.

#### How to test

#### Misconfiguration

Check the apache login shell in the /etc/password file for Linux
Systems.

    # grep apache /etc/passwd

#### Remediation

The below command will configure the apache user with "nologin"
restrictions.

    #chsh -s /usr/sbin/nologin apache

Expected Output

    Command to chec:
    #cat/etc/passwd
    Expected Output:
    apache:x:48:48:Apache:/var/www:usr/sbin/nologin

### Lock Apache user account

#### Description

The user account under which Apache runs, should have a valid password,
but should be locked.

#### How to test

#### Misconfiguration

The below is the misconfiguration for an Apache user.

Command

    # passwd -S apache

Expected Output:

    apache P 09/07/2015 0 99999 7 -1

#### Remediation

    # passwd -l apache

Validate the Configuration using the below command in Linux.

    #passwd -S apache

Expected Output:

    apache LK 2015-09-09 0 99999 7 -1

### Apache Directory Ownership and Permissions

#### Description

All of the Apache Software directories and files installed should be
owned by root user and root group.This will help in mitigate exploration
severity and information disclosure.

Apache Web Document folders like "/var/www/html" need a designated group
to allow web content to be updated.

#### How to test

Type the below command to check the User and Group associated with a
file.The file varies in Between Debian,RHEL/CentOS/Fedora,FreeBSD.

Example:

    # ls -l /usr/share/apache2

#### Misconfiguration

`In the Below example the apache2 folder is owned by a user name "alice" and group "sysadmin" which can be considered as a misconfiguration.`

    drwxr-xr-x    6 alice sysadmin 4096 Sep  7 13:20 apache2

#### Remediation

The below command will set a Directory named "apache2" with root user
and root group recursively.

    #chown –R root:root /usr/local/apache2

### Apache File Ownership and Permissions

#### Description

Setting the appropriate permissions on the Apache files and directories
can help to prevent/mitigate exploitation severity and information
disclosure.

Preventing execution of Apache binaries with limited permission will
decrease the attack surface.

Permission of the Apache directories and files should be rwxr-xr-x and
they can change if it is Apache binary or executable file.

#### How to test

Run the below command to check the file permissions.

    #ls -l /var/www/html

#### Misconfiguration

Other than rwxr-xr-x would be considered as a mis configuration.

#### Remediation

Permission of the Apache directories and files should be rwxr-xr-x and
they can change if it is Apache binary or executable file.

## Access Control List in Apache

### Restrict OS Root directory access using Allow,Deny Directive

#### Description

Apache will serve any file mapped from an URL to clients with efault
configuration.

It is better to create a deny policy that will not allow access to
Operating system directoories or files.

A small modification in the configuration will allow access to tthe
required files.

The order of the directive is important as it provides for otherr Allow
diectives to override the default deny.

#### How to test

1\. Find the appropriate Apache configuration file in your Server. 2.
Ensure there is a single Order directive and set the value to deny,
allow 3. Ensure there is a Deny directive, and set the value to "from
all". 4. Remove any Allow directives from the root <Directory> element.

#### Misconfiguration

    <Directory />
     . . .
     Order allow,deny
     Allow from all
     . . .
    </Directory>

#### Remediation

    <Directory />
     . . .
     Order deny,allow
     Deny from all
     . . .
    </Directory>

### Restrict WebSite Content using Allow,Deny Directive

#### Description

Appropriate access to various files,directories, locations and virtual
hosts that contains web site content can make attack surface strong.

Based up on the requirement you can provide allow access or you can
deny.

#### How to test

1\. Find the appropriate Apache configuration file in your Server.
2\. Ensure there is a single Order directive and set the value to deny,
allow
3\. Ensure there is a Deny directive, and set the value to "from all".
4\. Remove any Allow directives from the root <Directory> element.

#### MisConfiguration

    <Directory "/var/www/html">
     . . .
     Order deny,allow
     Allow from all
    </Directory>

#### Remediation

    <Directory "/var/www/html/">
    Order deny,allow
    deny from all
    allow from 172.16.5.0/24
    </Directory>

### AllowOverride Directive

#### Description

#### How to test

#### Misconfiguration

    <Directory /var/www/html>
    AllowOverride All
    </Directory>

#### Remediation

    <Directory /var/www/html>
    AllowOverride None
    </Directory>

## Apache Features

### Limit HTTP Request Methods

#### Description

Apache Server is capable of accepting and processing
GET,HEAD,POST,OPTIONS,PUT,DELETE HTTP request methods. If we use
<LimitExcept> directive then Apache will not process the unnecessary
HTTP request methods. The primary security concerened is to disable the
unnecessary HTTP request methods. Apache <LimitExcept> directive does
not deny the TRACE request method.

#### How to test

#### Misconfiguration

By default all the HTTP request methods are accepted by Apache Server.

#### Remediation

```

<Directory "/usr/local/apache2/cgi-bin">
 . . .
 # Limit HTTP methods
    <LimitExcept GET POST OPTIONS>
            deny from all
    </LimitExcept>
</Directory>
```

### Disable HTTP Trace Method

#### Description

HTTP Trace Method is enabled by default on the Apache Web Server. This
method intended for diagnostics purposes.

#### How to test

Method 1: 1. Locate the Apache configuration files and included
configuration files. 2. Verify there is a single TraceEnable directive
configured with a value of off.

Method 2: Telnet on the port your web server is running and request for
“TRACE / HTTP/1.0” if you get a positive reply it means TRACE is
enabled on your system. The output of a server with TRACE enabled will
look like:

#### Misconfiguration

Below is an example of MisConfiguration.

    TraceEnable on

#### Remediation

1.Locate the main Apache configuration file such as httpd.conf. 2.Add a
TraceEnable directive to the server level configuration with a value of
off as shown

    TraceEnable off

### HTTP Protocol Version

#### Description

Many attacks in the process of enumeration they use Vulnerability
Scanners,Automated Programs and other fingerprinting tools to send
abnormal HTTP protocol version to check how Web Server responds and it
is very important that we need to deny these requests.

#### How to test

1.Locate the Apache configuration files and included configuration
files.
2.Verify that below module is loaded.

    mod_rewrite.so

#### Misconfiguration

By default this module is not loaded.So we need to load the module.

#### Remediation

Method1:
While compiling the Apache for installation we can enable this module
and then install it.

    #./configure --enable-rewrite

If the Apache is installed with default parameter then we can also use
the below Method
Method2:
1.Locate the Apache configuration files and included configuration
files.
2.Add the following line to the Configuration file.

    LoadModule rewrite_module modules/mod_rewrite.so

3.Add/change the RewriteEngine directive to the configuration as shown.

    RewriteEngine On
    RewriteCond %{THE_REQUEST} !HTTP/1\.1$
    RewriteRule .* - [F]

### Restrict access to .htaccess files

#### Description

The following configuration prevent .htaccess and .htpasswd files from
being viewed by Web clients.

#### How to test

Verify the below recommended configuration is present in the Apache
config file and make sure they are not commented out.

#### Misconfiguration

Below is the Misconfiguration

    <FilesMatch "^\.ht">
    Order allow
    </FilesMatch>

#### Remediation

1.Locate the Apache configuration files and included configuration
files. 2.Add the following line to the Configuration file.

    <FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy All
    </FilesMatch>

### Restrict file extensions

#### Description

There are many files that are often left within the web server document
root that could provide an attacker with sensitive information. Most
often these files are mistakenly left behind after installation,
trouble-shooting, or backing up files before editing. We use FilesMatch
directive to restrict access to only those file extensions that are
appropriate for the web server.

#### How to test

Verify the below recommended configuration is present in the Apache
config file and make sure they are not commented out.

#### Misconfiguration

Block all files by default, unless specifically allowed.

    <FilesMatch "^.*$">
    Order Deny,Allow
    Deny from all
    </FilesMatch>

#### Remediation

1.Locate the Apache configuration files and included configuration
files.
2.Add the following line to the Configuration file so that Web Server
Allow files with specifically approved file extensions such as
"css,htm,html,js,pdf,txt,xml,xsl"

    <FilesMatch "^.*\.(css
    |html?
    |js
    |pdf
    |txt
    |xml
    |xsl
    |gif
    |ico
    |jpe?g
    |png)$">
    Order Deny,Allow
    Allow from all
    </FilesMatch>

Note: File extensions should be matched carefully and should be changed
based upon the reqruiement.

### Remove Default HTML Page

#### Description

All of the Web Servers comes with a default page which is not required .

#### How to test

Review all pre-installed web pages and remove content which is not
required from root directory of the Web Server.

#### Misconfiguration

Post installation of the Web Server if the below items exits in Server
then that is considered as a Misconfiguration. 1.Default Index Pages
2.Welcome Page
3.Apache User Manul
4.Server Information Handlers and Status Handlers.

#### Remediation

1.Remove the default index pages like ( index.html,default.html)
2.Remove the Welcome pages.
3.Remove the Apache User manuals.
4.Remove any Server Information Handlers and Status Handlers with
configuration.

## Apache Module Configuration

### Authentication and Authorization Modules

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Status and Info Modules

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### AutoIndex Module

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Proxy Module

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### User Directory Moudule

## SSL / TLS Configuration

### Install a valid certificate

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Restric weak SSL Protocols and Ciphers

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Install mod_ssl Module

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Avoid Insecure SSL Renogitation

#### Description

#### How to test

#### Misconfiguration

#### Remediation

## Attack Migigation

### DOS

#### Description

#### How to test

#### Misconfiguration

#### Remediation

### Buffer Overflow

#### Description

#### How to test

#### Misconfiguration

#### Remediation

## References

<https://httpd.apache.org/docs/current/misc/security_tips.html>

<https://wiki.debian.org/Apache/Hardening>

<https://wiki.apache.org/httpd/CommonMisconfigurations>

<http://projects.webappsec.org/w/page/13246959/Server%20Misconfiguration>