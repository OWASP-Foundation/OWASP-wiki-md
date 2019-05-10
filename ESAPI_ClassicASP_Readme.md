**OWASP ESAPI - Classic ASP Edition ReadMe**

Release 0.9

March 2009
**Welcome to the Classic ASP Edition of OWASP ESAPI v0.9**

This document provides information about the Classic ASP Edition of
OWASP ESAPI. The topics below cover system requirements, additional
product information, and application notes.

For information about the new features of this release, known issues,
resolved issues, and limitations, refer to the Release notes.


**System Requirements**

  - Microsoft .NET Framework 2.0


**Other Requirements**

The Classic ASP Edition of OWASP ESAPI includes a reference
implementation (look for `default.asp.zip` file at
[Classic_ASP_Security_Project](Classic_ASP_Security_Project "wikilink"))
which may be tailored or replaced, according to your organization's
needs.


**Server Recommendations**

There is no specific recommendation


**Obtaining the Classic ASP Edition of OWASP ESAPI**

You can download the latest release of the Classic ASP Edition of OWASP
ESAPI from the [Google Code download
page](http://code.google.com/p/owasp-esapi-classicasp/)

When you download the source files, make sure that you keep the
directory structure.


\---- **OWASP ESAPI - Classic ASP Edition Release Notes**

Release 0.9

March 2009


**Welcome to the Classic ASP Edition of OWASP ESAPI v0.9**

This document provides information about Classic ASP Edition of OWASP
ESAPI v0.9. Browse through the topics below to find out about new
features, known issues and limitations for this release.


**New features**

This release includes the following new features:

  - Implementation of most of the ESAPI .NET version for Classic ASP
    technology, including those for Access Control, Encoding, Input
    Validation, Encryption and much more (Authentication class was fully
    implemented yet)
  - Sample Classic ASP page demonstrating the use of the different
    classes and methods


**Fixed in this release**

  - Not applicable. This is the first release\!


**Known issues**

  - You might receive a compilation error when instantiating the
    `AccessController` class
  - You have to copy the web.config file to the IIS worker folder. For
    example to `C:\Windows\System32\inetsrv\w3wp.exe.config` in Windows
    Vista


**Upgrading from earlier releases**

  - Not applicable. This is the first release\!



[Category: OWASP Enterprise Security
API](Category:_OWASP_Enterprise_Security_API "wikilink")