<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

#### Main

*Please see the [Discussion]({{TALKPAGENAME}} "wikilink") page for an
update on the status of this project.*

## Overview

**SWAAT** is an open source web application source code analysis tool.
SWAAT searches through source code and analyzes against the database of
potentially dangerous strings given in the .xml files. Thus it does NOT
positively identify the existence of a vulnerability - this generally
requires application contextual knowledge. It identifies the usage of
functions / strings / SQL that could lead to a finding. All potentially
dangerous code references are included in the output report.

The current version of SWAAT works only with server pages. Expect to see
enhanced functionality in future versions of the application.

## Goals

The aim of SWAAT is to help developers, testers, security staff, and
auditors locate potentially dangerous portions of source code; it is
designed to assist source code review.

After reviewing millions of lines of source code, most security
professionals believe that automated run-time analysis tools are useful
at identifying simple, common vulnerabilities. In most cases, however,
the vast majority of vulnerabilities require human intelligence and
knowledge of the application. SWAAT helps to reduce the burden of source
code review by identifying potentially dangerous functions and strings
in code and explaining both how they may be dangerous and how to
mitigate potential risks.

## Download

You can download the source here:
<http://www.securitycompass.com/swaat/swaat_source.zip>

## System Requirements

SWAAT was designed for the
\[<http://msdn2.microsoft.com/en-us/netframework/aa731542.aspx>. NET
Framework\] 1.1.4322 or lower. SWAAT has been successfully tested on
both Windows and Linux using
[Mono.](http://www.mono-project.com/Main_Page)

## Execution

SWAAT is a command-line driven program for Windows and under Mono for
Linux. In this first release, SWAAT must be run from within its
installation directory.

The scenario below shows a simple execution of SWAAT:

`       c:\program files\swaat> swaat ..\myapp`

Here we are running SWAAT on all files in the "c:\\program files\\myapp"
directory.

You can optionally execute swaat on specific files:

`       c:\program files\swaat> swaat ..\myApp\somefile.php`

Results of the analysis are listed by default in a file called
SWAAT-<year month day time>.html (e.g. SWAAT-20060723164024.html). If
you wish to specify a different file use the –o option:

`       c:\program files\swaat> swaat –o myOutput.html ..\myApp`

You may optionally turn off the xsl transform and simply save the raw
xml results by using the –x option:

`       c:\program files\swaat> swaat –x ..\myApp\*.php`

By running SWAAT you agree to the license terms described in license.txt

## Additional Options

SWAAT allows for two other options, the “–a lang” option and the “–i”
option:

  - The “-a lang” allows you to force all extensions to be mapped to a
    particular language.

c:\\program files\\swaat\> swaat –a PHP ..\\myApp\\

Note: Please ensure the language type must be in upper case (ASP, JSP,
PHP).

  - The –I option ignores case when reading the content of the files as
    well as while reading the functions provided in the signature files.

## Configuration

This version of SWAAT works on JSP, ASP .Net, and PHP. It also searches
for generic indicators such as "SQL" and "Password", so it may provide
some value on other platforms. Singatures for ASP, JSP and PHP functions
are in their respective asp.xml, jsp.xml and php.xml files. Each
signature file has mandatory XML tags "vuln match" and "type" and
optional tags "severity" and "alt".

`   * "vuln match" contains the string token to search for`
`   * "type" masp to a type of vulnerability as described in the "msg name" tags in msg.xml (e.g. userinput, racecondition, OSScripting, etc.)`
`   * "severity" specifies the risk level (high, medium, or low)`
`   * "alt" is a suggestion for an alternative, lower risk function to use (e.g. SecureRandom instead of Random)`

In addition, the file embedded.xml looks for expressions across all
three types of files (Java, ASP, and PHP). All "vuln match" tags in
embedded.xml must start and end with ".\*" wild card characters.

Regular expression searches can be added to any of the above-mentioned
xml files.

The "vuln match" must contain the regular expression to search for. The
following characters must be escaped with with a '\\' character to be
interpreted literally: ^ $ | ? . ( ) \\ + \* (e.g. "=".\*\\^" would find
the literal string "^foobar").

## Future Development

Future releases of SWAAT will include:

  - a graphical user interface (GUI)
  - integrated development environment (IDE) plug-ins
  - more sophisticated functionality and logic (for example to work with
    .java source)

## Feedback and Participation

We hope you find the OWASP SWAAT Project useful. Please contribute to
the Project by volunteering for one of the Tasks, sending your comments,
questions, and suggestions to owasp@owasp.org. An OWASP SWAAT Project
mailing list currently does not exist, but please check back here at a
later date.

If you do make any additions to the configuration files or have any
contributions to the findings database, please send them to
owasp@owasp.org so they can be included in the next release.

## Project Sponsors

SWAAT was generously donated by
[<http://www.securitycompass.com/images/logo_small.JPG>](http://www.securitycompass.com)

#### Project Details

__NOTOC__ <headertabs />

[SWAAT Project](Category:OWASP_Project "wikilink")