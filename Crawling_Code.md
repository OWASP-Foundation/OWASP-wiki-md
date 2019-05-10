__TOC__

Crawling code is the practice of scanning a code base of the review
target in question. It is, in effect, looking for key pointers wherein a
possible security vulnerability might reside. Certain APIs are related
to interfacing to the external world or file IO or user management,
which are key areas for an attacker to focus on. In crawling code we
look for APIs relating to these areas. We also need to look for business
logic areas which may cause security issues, but generally these are
bespoke methods which have bespoke names and can not be detected
directly, even though we may touch on certain methods due to their
relationship with a certain key API.

We also need to look for common issues relating to a specific language;
issues that may not be \*security\* related but which may affect the
stability/availability of the application in the case of extraordinary
circumstances. Other issues when performing a code review are areas such
a simple copyright notice in order to protect one’s intellectual
property.

Crawling code can be done manually or in an automated fashion using
automated tools. Tools as simple as grep or wingrep can be used. Other
tools are available which would search for key words relating to a
specific programming language.

The following sections shall cover the function of crawing code for
Java/J2EE, .NET and Classic ASP. This section is best used in
conjunction with the [transactional
analysis](Security_Code_Review_Coverage "wikilink") section also
detailed in this guide.

## Searching for Key Indicators

The basis of the code review is to locate and analyse areas of code
which may have application security implications. Assuming the code
reviewer has a thorough understanding of the code, what it is intended
to do, and the context in which it is to be used, firstly one needs to
sweep the code base for areas of interest.

This can be done by performing a text search on the code base looking
for keywords relating to APIs and functions. Below is a guide for .NET
framework 1.1 & 2.0

## Searching for Code in .NET

Firstly one needs to be familiar with the tools one can use in order to
perform text searching, following this one needs to know what to look
for.

In this section we will assume you have a copy of Visual Studio (VS)
.NET at hand. VS has two types of search "Find in Files" and a cmd line
tool called Findstr.

The test search tools in XP is not great in my experience and if one has
to use this make sure SP2 in installed as it works better. To start off,
one should scan thorough the code looking for common patterns or
keywords such as "User", "Password", "Pswd", "Key", "Http", etc... This
can be done using the "Find in Files" tool in VS or using findstring as
follows:

findstr /s /m /i /d:c:\\projects\\codebase\\sec "http" \*.\*

## HTTP Request Strings

Requests from external sources are obviously a key area of a security
code review. We need to ensure that all HTTP requests received are data
validated for composition, max and min length, and if the data falls
with the realms of the parameter white-list. Bottom-line is this is a
key area to look at and ensure security is enabled.

request.accepttypes
request.browser
request.files
request.headers
request.httpmethod
request.item
request.querystring
request.form
request.cookies
request.certificate
request.rawurl
request.servervariables
request.url
request.urlreferrer
request.useragent
request.userlanguages
request.IsSecureConnection
request.TotalBytes
request.BinaryRead
InputStream
HiddenField.Value
TextBox.Text
recordSet

## HTML Output

Here we are looking for responses to the client. Responses which go
unvalidated or which echo external input without data validation are key
areas to examine. Many client side attacks result from poor response
validation. XSS relies on this somewhat.

response.write
\<% =
HttpUtility
HtmlEncode
UrlEncode
innerText
innerHTML

## SQL & Database

Locating where a database may be involved in the code is an important
aspect of the code review. Looking at the database code will help
determine if the application is vulnerable to SQL injection. One aspect
of this is to verify that the code uses either SqlParameter,
OleDbParameter, or OdbcParameter(System.Data.SqlClient). These are typed
and treat parameters as the literal value and not executable code in the
database.

exec sp_executesql
execute sp_executesql
select from
Insert
update
delete from where
delete
exec sp_
execute sp_
exec xp_
execute sp_
exec @
execute @
executestatement
executeSQL
setfilter
executeQuery
GetQueryResultInXML
adodb
sqloledb
sql server
driver
Server.CreateObject
.Provider
.Open
ADODB.recordset
New OleDbConnection
ExecuteReader
DataSource
SqlCommand
Microsoft.Jet
SqlDataReader
ExecuteReader
GetString
SqlDataAdapter
CommandType
StoredProcedure
System.Data.sql

## Cookies

Cookie manipulation can be key to various application security exploits,
such as session hijacking/fixation and parameter manipulation. One
should examine any code relating to cookie functionality, as this would
have a bearing on session security.

System.Net.Cookie
HTTPOnly
document.cookie

## HTML Tags

Many of the HTML tags below can be used for client side attacks such as
cross site scripting. It is important to examine the context in which
these tags are used and to examine any relevant data validation
associated with the display and use of such tags within a web
application.

HtmlEncode
URLEncode
<applet>

<frameset>



<embed>


<frame>

<html>


<iframe>
<img>

<style>


<layer>
<ilayer>

<meta>


<object>

<body>


\<frame security
\<iframe security

## Input Controls

The input controls below are server classes used to produce and display
web application form fields. Looking for such references helps locate
entry points into the application.

system.web.ui.htmlcontrols.htmlinputhidden
system.web.ui.webcontrols.hiddenfield
system.web.ui.webcontrols.hyperlink system.web.ui.webcontrols.textbox
system.web.ui.webcontrols.label system.web.ui.webcontrols.linkbutton
system.web.ui.webcontrols.listbox system.web.ui.webcontrols.checkboxlist
system.web.ui.webcontrols.dropdownlist

## WEB.Config

The .NET Framework relies on .config files to define configuration
settings. The .config files are text-based XML files. Many .config files
can, and typically do, exist on a single system. Web applications refer
to a web.config file located in the application’s root directory. For
ASP.NET applications, web.config contains information about most aspects
of the application’s operation.

requestEncoding
responseEncoding
trace
authorization
compilation
CustomErrors
httpCookies
httpHandlers
httpRuntime
sessionState
maxRequestLength
debug
forms protection
appSettings
ConfigurationSettings
appSettings
connectionStrings
authentication mode
allow
deny
credentials
identity impersonate
timeout
remote

## global.asax

Each application has its own Global.asax if one is required. Global.asax
sets the event code and values for an application using scripts. One
must ensure that application variables do not contain sensitive
information, as they are accessible to the whole application and to all
users within it.

Application_OnAuthenticateRequest
Application_OnAuthorizeRequest
Session_OnStart
Session_OnEnd

## Logging

Logging can be a source of information leakage. It is important to
examine all calls to the logging subsystem and to determine if any
sensitive information is being logged. Common mistakes are logging
userID in conjunction with passwords within the authentication
functionality or logging database requests which may contains sensitive
data.

log4net
Console.WriteLine
System.Diagnostics.Debug
System.Diagnostics.Trace

## Machine.config

Its important that many variables in machine.config can be overridden in
the web.config file for a particular application.

validateRequest
enableViewState
enableViewStateMac

## Threads and Concurrency

Locating code that contains multithreaded functions. Concurrency issues
can result in race conditions which may result in security
vulnerabilities. The Thread keyword is where new threads objects are
created. Code that uses static global variables which hold sensitive
security information may cause session issues. Code that uses static
constructors may also cause issues between threads. Not synchronizing
the Dispose method may cause issues if a number of threads call Dispose
at the same time, this may cause resource release issues.

Thread
Dispose

## Class Design

Public and Sealed relate to the design at class level. Classes which are
not intended to be derived from should be sealed. Make sure all class
fields are Public for a reason. Don't expose anything you don't need to.

Public
Sealed

## Reflection, Serialization

Code may be generated dynamically at runtime. Code that is generated
dynamically as a function of external input may give rise to issues. If
your code contains sensitive data, does it need to be serialized?

Serializable
AllowPartiallyTrustedCallersAttribute
GetObjectData
StrongNameIdentityPermission
StrongNameIdentity
System.Reflection

## Exceptions & Errors

Ensure that the catch blocks do not leak information to the user in the
case of an exception. Ensure when dealing with resources that the
finally block is used. Having trace enabled is not great from an
information leakage perspective. Ensure customised errors are properly
implemented.

catch{
Finally
trace enabled
customErrors mode

## Crypto

If cryptography is used then is a strong enough cipher used, i.e. AES or
3DES? What size key is used? The larger the better. Where is hashing
performed? Are passwords that are being persisted hashed? They should
be. How are random numbers generated? Is the PRNG "random enough"?

RNGCryptoServiceProvider
SHA
MD5
base64
xor
DES
RC2
System.Random
Random
System.Security.Cryptography

userid

username

password

pass

pwd

key

sharekey

code

encode

encrypt

enc

dec

decrypt

## Storage

If storing sensitive data in memory, I recommend one uses the following.

SecureString
ProtectedMemory

## Authorization, Assert & Revert

Bypassing the code access security permission? Not a good idea. Also
below is a list of potentially dangerous permissions such as calling
unmanaged code, outside the CLR.

.RequestMinimum
.RequestOptional
Assert
Debug.Assert
CodeAccessPermission
ReflectionPermission.MemberAccess
SecurityPermission.ControlAppDomain
SecurityPermission.UnmanagedCode
SecurityPermission.SkipVerification
SecurityPermission.ControlEvidence
SecurityPermission.SerializationFormatter
SecurityPermission.ControlPrincipal
SecurityPermission.ControlDomainPolicy
SecurityPermission.ControlPolicy

## Legacy Methods

printf
strcpy

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")