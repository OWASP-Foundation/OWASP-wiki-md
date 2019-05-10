''' 4.8 Input Validation Testing '''

-----

The most common web application security weakness is the failure to
properly validate input coming from the client or from the environment
before using it. This weakness leads to almost all of the major
vulnerabilities in web applications, such as cross site scripting, SQL
injection, interpreter injection, locale/Unicode attacks, file system
attacks, and buffer overflows.

Data from an external entity or client should never be trusted, since it
can be arbitrarily tampered with by an attacker. "All Input is Evil",
says Michael Howard in his famous book "Writing Secure Code". That is
rule number one. Unfortunately, complex applications often have a large
number of entry points, which makes it difficult for a developer to
enforce this rule. This chapter describes Data Validation testing. This
is the task of testing all the possible forms of input to understand if
the application sufficiently validates input data before using it.

Input validation testing is split into the following categories:
**Testing for Cross site scripting**
Cross Site Scripting (XSS) testing checks if it is possible to
manipulate the input parameters of the application so that it generates
malicious output. Testers find an XSS vulnerability when the application
does not validate their input and creates an output that is under their
control. This vulnerability leads to various attacks, for example,
stealing confidential information (such as session cookies) or taking
control of the victim's browser. An XSS attack breaks the following
pattern: Input -\> Output == cross-site scripting.

In this guide, the following types of XSS testing are discussed in
details:
[4.8.1 Testing for Reflected Cross Site Scripting
(OTG-INPVAL-001)](Testing_for_Reflected_Cross_site_scripting_\(OTG-INPVAL-001\) "wikilink")
[4.8.2 Testing for Stored Cross Site Scripting
(OTG-INPVAL-002)](Testing_for_Stored_Cross_site_scripting_\(OTG-INPVAL-002\) "wikilink")
Client side XSS testing, such as DOM XSS and Cross site Flashing is
discussed in the Client Side testing section.

**Testing for HTTP Verb Tampering and Parameter Pollution** HTTP Verb
Tampering tests the web application's response to different HTTP methods
accessing system objects. For every system object discovered during
spidering, the tester should attempt accessing all of those objects with
every HTTP method. HTTP Parameter Pollution tests the applications
response to receiving multiple HTTP parameters with the same name. For
example, if the parameter *username* is included in the GET or POST
parameters twice, which one is honoured, if any.

HTTP Verb Tampering is described in

[4.8.3 Testing for HTTP Verb Tampering
(OTG-INPVAL-003)](Testing_for_HTTP_Verb_Tampering_\(OTG-INPVAL-003\) "wikilink")

and HTTP Parameter testing techniques are presented in

[4.8.4 Testing for HTTP Parameter pollution
(OTG-INPVAL-004)](Testing_for_HTTP_Parameter_pollution_\(OTG-INPVAL-004\) "wikilink")

**[4.8.5 SQL Injection
(OTG-INPVAL-005)](Testing_for_SQL_Injection_\(OTG-INPVAL-005\) "wikilink")
** SQL injection testing checks if it is possible to inject data into
the application so that it executes a user-controlled SQL query in the
back-end database. Testers find an SQL injection vulnerability if the
application uses user input to create SQL queries without proper input
validation. A successful exploitation of this class of vulnerability
allows an unauthorized user to access or manipulate data in the
database. Note that application data often represents the core asset of
a company. An SQL Injection attack breaks the following pattern: Input
-\> Query SQL == SQL injection

SQL Injection testing is further broken down by product or vendor:
[4.8.5.1 Oracle Testing](Testing_for_Oracle "wikilink")
[4.8.5.2 MySQL Testing](Testing_for_MySQL "wikilink")
[4.8.5.3 SQL Server Testing](Testing_for_SQL_Server "wikilink")
[4.8.5.4 Testing
PostgreSQL](OWASP_Backend_Security_Project_Testing_PostgreSQL "wikilink")
[4.8.5.5 MS Access Testing](Testing_for_MS_Access "wikilink")
[4.8.5.6 Testing for NoSQL
injection](Testing_for_NoSQL_injection "wikilink")

**[4.8.6 LDAP Injection
(OTG-INPVAL-006)](Testing_for_LDAP_Injection_\(OTG-INPVAL-006\) "wikilink")
** LDAP injection testing is similar to SQL Injection testing. The
differences are that testers use the LDAP protocol instead of SQL and
the target is an LDAP Server instead of a SQL Server. An LDAP Injection
attack breaks the following pattern:
Input -\> Query LDAP == LDAP injection

**[4.8.7 ORM Injection
(OTG-INPVAL-007)](Testing_for_ORM_Injection_\(OTG-INPVAL-007\) "wikilink")
** ORM injection testing is similar to SQL Injection Testing. In this
case, testers use a SQL Injection against an ORM-generated data access
object model. From the tester's point of view, this attack is virtually
identical to a SQL Injection attack. However, the injection
vulnerability exists in the code generated by an ORM tool.

**[4.8.8 XML Injection
(OTG-INPVAL-008)](Testing_for_XML_Injection_\(OTG-INPVAL-008\) "wikilink")
** XML injection testing checks if it possible to inject a particular
XML document into the application. Testers find an XML injection
vulnerability if the XML parser fails to make appropriate data
validation.
An XML Injection attack breaks the following pattern:
Input -\> XML doc == XML injection

**[4.8.9 SSI Injection
(OTG-INPVAL-009)](Testing_for_SSI_Injection_\(OTG-INPVAL-009\) "wikilink")
** Web servers usually give developers the ability to add small pieces
of dynamic code inside static HTML pages, without having to deal with
full-fledged server-side or client-side languages. This feature is
incarnated by Server-Side Includes (SSI) Injection. In SSI injection
testing, testers check if it is possible to inject into the application
data that will be interpreted by SSI mechanisms. A successful
exploitation of this vulnerability allows an attacker to inject code
into HTML pages or even perform remote code execution.

**[4.8.10 XPath Injection
(OTG-INPVAL-010)](Testing_for_XPath_Injection_\(OTG-INPVAL-010\) "wikilink")
** XPath is a language that has been designed and developed primarily to
address parts of an XML document. In XPath injection testing, testers
check if it is possible to inject data into an application so that it
executes user-controlled XPath queries. When successfully exploited,
this vulnerability may allow an attacker to bypass authentication
mechanisms or access information without proper authorization.

**[4.8.11 IMAP/SMTP Injection
(OTG-INPVAL-011)](Testing_for_IMAP/SMTP_Injection_\(OTG-INPVAL-011\) "wikilink")
** This threat affects all the applications that communicate with mail
servers (IMAP/SMTP), generally web mail applications. In IMAP/SMTP
injection testing, testers check if it possible to inject arbitrary
IMAP/SMTP commands into the mail servers, due to input data not properly
sanitized.
An IMAP/SMTP Injection attack breaks the following pattern:
Input -\> IMAP/SMTP command == IMAP/SMTP Injection

**[4.8.12 Code Injection
(OTG-INPVAL-012)](Testing_for_Code_Injection_\(OTG-INPVAL-012\) "wikilink")
** Code injection testing checks if it is possible to inject into an
application data that will be later executed by the web server.
A Code Injection attack breaks the following pattern:
Input -\> malicious Code == Code Injection

**[4.8.13 OS Commanding
(OTG-INPVAL-013)](Testing_for_Command_Injection_\(OTG-INPVAL-013\) "wikilink")
** In command injection testing testers will try to inject an OS command
through an HTTP request into the application.
An OS Command Injection attack breaks the following pattern:
Input -\> OS Command == OS Command Injection

**[4.8.14 Buffer overflow
(OTG-INPVAL-014)](Testing_for_Buffer_Overflow_\(OTG-INPVAL-014\) "wikilink")
** In these tests, testers check for different types of buffer overflow
vulnerabilities. Here are the testing methods for the common types of
buffer overflow vulnerabilities:
[4.8.14.1 Heap overflow](Testing_for_Heap_Overflow "wikilink")
[4.8.14.2 Stack overflow](Testing_for_Stack_Overflow "wikilink")
[4.8.14.3 Format string](Testing_for_Format_String "wikilink")
In general Buffer overflow breaks the following pattern:
Input -\> Fixed buffer or format string == overflow

**[4.8.15 Incubated vulnerability
(OTG-INPVAL-015)](Testing_for_Incubated_Vulnerability_\(OTG-INPVAL-015\) "wikilink")
** Incubated testing is a complex testing that needs more than one data
validation vulnerability to work.

[4.8.16 Testing for HTTP Splitting/Smuggling
(OTG-INPVAL-016)](Testing_for_HTTP_Splitting/Smuggling_\(OTG-INPVAL-016\) "wikilink")
Describes how to test for an HTTP Exploit, as HTTP Verb, HTTP Splitting,
HTTP Smuggling.

In every pattern shown, the data should be validated by the application
before it's trusted and processed. The goal of testing is to verify if
the application actually performs validation and does not trust its
input.