`__NOTOC__`

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![Cheatsheets-header.jpg](Cheatsheets-header.jpg
"Cheatsheets-header.jpg")

</div>

# IMPORTANT

The Cheat Sheet Series project has been moved to
[GitHub](https://github.com/OWASP/CheatSheetSeries)\!

An [open
discussion](https://github.com/OWASP/CheatSheetSeries/issues/13) is
pending about to exclude or not this cheat sheet of the V2 of the
project.

# Introduction

`__TOC__`

The following is a developer-centric defensive cheat sheet for the 2013
release of the [OWASP Top Ten
Project](OWASP_Top_Ten_Project "wikilink"). It also presents a quick
reference based on [OWASP Testing
Project](OWASP_Testing_Project "wikilink") to help how to identify the
risks.

# OWASP Top Ten Cheat Sheet

## A1 Injection

### Presentation

*Render:*

  - Set a correct content type
  - Set safe character set (UTF-8)
  - Set correct locale

*On Submit:*

  - Enforce input field type and lengths.
  - Validate fields and provide feedback.
  - Ensure option selects and radio contain only sent values.

### Controller

**Canonicalize using correct character set** **Positive input validation
using correct character set**

(NR) Negative input validation. (LR) Sanitize input.

''Tip: updating a negative list (such as looking for "script", "sCrIpT",
"ßCrîpt", etc) will require expensive and constant deployments and will
'''always '''fail as attackers work out your list of "bad" words.
Positive validation is simpler, faster and usually more secure and needs
updating far less than any other validation mechanism. ''

### Model

  - **[Query Parameterization Cheat
    Sheet](Query_Parameterization_Cheat_Sheet "wikilink")**

<!-- end list -->

  - Object relational model (Hibernate).
  - Active Record design pattern.
  - Stored procedures.

<!-- end list -->

  - Escape mechanisms such as ESAPI's Encoder:
      - EncodeForLDAP()
      - Encoder.EncodeforOS()

''Tip: '''All '''SQL Injection is due to dynamic SQL queries. Strongly
consider prohibiting dynamic SQL queries within your organization ''

### Testing

  - [Testing for SQL Injection
    (OTG-INPVAL-005)](Testing_for_SQL_Injection_\(OTG-INPVAL-005\) "wikilink")
  - [Testing for LDAP Injection
    (OTG-INPVAL-006)](Testing_for_LDAP_Injection_\(OTG-INPVAL-006\) "wikilink")
  - [Testing for ORM Injection
    (OTG-INPVAL-007)](Testing_for_ORM_Injection_\(OTG-INPVAL-007\) "wikilink")
  - [Testing for XML Injection
    (OTG-INPVAL-008)](Testing_for_XML_Injection_\(OTG-INPVAL-008\) "wikilink")
  - [Testing for SSI Injection
    (OTG-INPVAL-009)](Testing_for_SSI_Injection_\(OTG-INPVAL-009\) "wikilink")
  - [Testing for XPath Injection
    (OTG-INPVAL-010)](Testing_for_XPath_Injection_\(OTG-INPVAL-010\) "wikilink")
  - [Testing for IMAP/SMTP Injection
    (OTG-INPVAL-011)](Testing_for_IMAP/SMTP_Injection_\(OTG-INPVAL-011\) "wikilink")
  - [Testing for Code Injection
    (OTG-INPVAL-012)](Testing_for_Code_Injection_\(OTG-INPVAL-012\) "wikilink")
  - [Testing for Command Injection
    (OTG-INPVAL-013)](Testing_for_Command_Injection_\(OTG-INPVAL-013\) "wikilink")
  - [Testing for Buffer Overflow
    (OTG-INPVAL-014)](Testing_for_Buffer_Overflow_\(OTG-INPVAL-014\) "wikilink")

## A2 Weak authentication and session management

### Presentation

*Render:*

  - Validate user is authenticated.
  - Validate role is sufficient for this view.
  - Set "secure" and "HttpOnly" flags for session cookies.
  - Send CSRF token with forms.

### Controller

*Design:*

  - Only use inbuilt session management.
  - Store secondary SSO / framework / custom session identifiers in
    native session object – do not send as additional headers or
    cookies.

<!-- end list -->

  - Validate user is authenticated.
  - Validate role is sufficient to perform this action.
  - Validate CSRF token.

### Model

Validate role is sufficient to create, read, update, or delete data

*Tip: Consider the use of a "governor" to regulate the maximum number of
requests per second / minute / hour that this user may perform. For
example, a typical banking user should not perform more than ten
transactions a minute, and one hundred per second is dangerous and
should be blocked.*

### Testing

  - [Test Role Definitions
    (OTG-IDENT-001)](Test_Role_Definitions_\(OTG-IDENT-001\) "wikilink")
  - [Test User Registration Process
    (OTG-IDENT-002)](Test_User_Registration_Process_\(OTG-IDENT-002\) "wikilink")
  - [Test Account Provisioning Process
    (OTG-IDENT-003)](Test_Account_Provisioning_Process_\(OTG-IDENT-003\) "wikilink")
  - [Testing for Account Enumeration and Guessable User Account
    (OTG-IDENT-004)](Testing_for_Account_Enumeration_and_Guessable_User_Account_\(OTG-IDENT-004\) "wikilink")
  - [Testing for Weak or unenforced username policy
    (OTG-IDENT-005)](Testing_for_Weak_or_unenforced_username_policy_\(OTG-IDENT-005\) "wikilink")
  - [Testing for Credentials Transported over an Encrypted Channel
    (OTG-AUTHN-001)](Testing_for_Credentials_Transported_over_an_Encrypted_Channel_\(OTG-AUTHN-001\) "wikilink")
  - [Testing for default credentials
    (OTG-AUTHN-002)](Testing_for_default_credentials_\(OTG-AUTHN-002\) "wikilink")
  - [Testing for Weak lock out mechanism
    (OTG-AUTHN-003)](Testing_for_Weak_lock_out_mechanism_\(OTG-AUTHN-003\) "wikilink")
  - [Testing for Bypassing Authentication Schema
    (OTG-AUTHN-004)](Testing_for_Bypassing_Authentication_Schema_\(OTG-AUTHN-004\) "wikilink")
  - [Testing for Vulnerable Remember Password
    (OTG-AUTHN-005)](Testing_for_Vulnerable_Remember_Password_\(OTG-AUTHN-005\) "wikilink")
  - [Testing for Browser cache weakness
    (OTG-AUTHN-006)](Testing_for_Browser_cache_weakness_\(OTG-AUTHN-006\) "wikilink")
  - [Testing for Weak password policy
    (OTG-AUTHN-007)](Testing_for_Weak_password_policy_\(OTG-AUTHN-007\) "wikilink")
  - [Testing for Weak security question/answer
    (OTG-AUTHN-008)](Testing_for_Weak_security_question/answer_\(OTG-AUTHN-008\) "wikilink")
  - [Testing for weak password change or reset functionalities
    (OTG-AUTHN-009)](Testing_for_weak_password_change_or_reset_functionalities_\(OTG-AUTHN-009\) "wikilink")
  - [Testing for Weaker authentication in alternative channel
    (OTG-AUTHN-010)](Testing_for_Weaker_authentication_in_alternative_channel_\(OTG-AUTHN-010\) "wikilink")
  - [Testing for Bypassing Authorization Schema
    (OTG-AUTHZ-002)](Testing_for_Bypassing_Authorization_Schema_\(OTG-AUTHZ-002\) "wikilink")
  - [Testing for Privilege escalation
    (OTG-AUTHZ-003)](Testing_for_Privilege_escalation_\(OTG-AUTHZ-003\) "wikilink")
  - [Testing for Session Management Schema
    (OTG-SESS-001)](Testing_for_Session_Management_Schema_\(OTG-SESS-001\) "wikilink")
  - [Testing for cookies attributes
    (OTG-SESS-002)](Testing_for_cookies_attributes_\(OTG-SESS-002\) "wikilink")
  - [Testing for Session Fixation
    (OTG-SESS-003)](Testing_for_Session_Fixation_\(OTG-SESS-003\) "wikilink")
  - [Testing for Exposed Session Variables
    (OTG-SESS-004)](Testing_for_Exposed_Session_Variables_\(OTG-SESS-004\) "wikilink")
  - [Testing for CSRF
    (OTG-SESS-005)](Testing_for_CSRF_\(OTG-SESS-005\) "wikilink")
  - [Testing for logout functionality
    (OTG-SESS-006)](Testing_for_logout_functionality_\(OTG-SESS-006\) "wikilink")
  - [Test Session Timeout
    (OTG-SESS-007)](Test_Session_Timeout_\(OTG-SESS-007\) "wikilink")
  - [Testing for Session puzzling
    (OTG-SESS-008)](Testing_for_Session_puzzling_\(OTG-SESS-008\) "wikilink")

## A3 XSS

### Presentation

*Render:*

  - Set correct content type
  - Set safe character set (UTF-8)
  - Set correct locale
  - Output encode all user data as per output context
  - Set input constraints

*On Submit:*

  - Enforce input field type and lengths.
  - Validate fields and provide feedback.
  - Ensure option selects and radio contain only sent values.

### Controller

**Canonicalize using correct character set** **Positive input validation
using correct character set**

(NR) Negative input validation (LR) Sanitize input

*Tip: Only process data that is 100% trustworthy. Everything else is
hostile and should be rejected.*

### Model

*Tip: Do not store data HTML encoded in the database. This prevents new
uses for the data, such as web services, RSS feeds, FTP batches, data
warehousing, cloud computing, and so on.*

*Tip: Use OWASP Scrubbr to clean tainted or hostile data from legacy
data*

### Testing

  - [Testing for Reflected Cross site scripting
    (OTG-INPVAL-001)](Testing_for_Reflected_Cross_site_scripting_\(OTG-INPVAL-001\) "wikilink")
  - [Testing for Stored Cross site scripting
    (OTG-INPVAL-002)](Testing_for_Stored_Cross_site_scripting_\(OTG-INPVAL-002\) "wikilink")
  - [Testing for DOM-based Cross site scripting
    (OTG-CLIENT-001)](Testing_for_DOM-based_Cross_site_scripting_\(OTG-CLIENT-001\) "wikilink")
  - [Testing for JavaScript Execution
    (OTG-CLIENT-002)](Testing_for_JavaScript_Execution_\(OTG-CLIENT-002\) "wikilink")
  - [Testing for HTML Injection
    (OTG-CLIENT-003)](Testing_for_HTML_Injection_\(OTG-CLIENT-003\) "wikilink")
  - [Testing for Cross site flashing
    (OTG-CLIENT-008)](Testing_for_Cross_site_flashing_\(OTG-CLIENT-008\) "wikilink")

## A4 Insecure Direct Object References

### Presentation

If data is from internal trusted sources, no data is sent.

Or

*Render:*

  - Send indirect random access reference map value.

### Controller

Obtain data from internal, trusted sources.

Or

Obtain direct value from random access reference access map.

### Model

Validate role is sufficient to create, read, update, or delete data.

### Testing

  - [Testing Directory traversal/file include
    (OTG-AUTHZ-001)](Testing_Directory_traversal/file_include_\(OTG-AUTHZ-001\) "wikilink")
  - [Testing for Insecure Direct Object References
    (OTG-AUTHZ-004)](Testing_for_Insecure_Direct_Object_References_\(OTG-AUTHZ-004\) "wikilink")
  - [Testing for Local File
    Inclusion](Testing_for_Local_File_Inclusion "wikilink")
  - [Testing for Remote File
    Inclusion](Testing_for_Remote_File_Inclusion "wikilink")

## A5 Security Misconfiguration

### Presentation

Ensure web servers and application servers are hardened.

PHP: Ensure allow_url_fopen and allow_url_include are both disabled
in php.ini. Consider the use of Suhosin extension

### Controller

Ensure web servers and application servers are hardened

XML: Ensure common web attacks (remote XSLT transforms, hostile XPath
queries, recursive DTDs, and so on) are protected by your XML stack. Do
not hand craft XML documents or queries – use the XML layer.

### Model

Ensure database servers are hardened

### Testing

  - [Fingerprint Web Server
    (OTG-INFO-002)](Fingerprint_Web_Server_\(OTG-INFO-002\) "wikilink")
  - [Fingerprint Web Application Framework
    (OTG-INFO-008)](Fingerprint_Web_Application_Framework_\(OTG-INFO-008\) "wikilink")
  - [Fingerprint Web Application
    (OTG-INFO-009)](Fingerprint_Web_Application_\(OTG-INFO-009\) "wikilink")
  - [Test Network/Infrastructure Configuration
    (OTG-CONFIG-001)](Test_Network/Infrastructure_Configuration_\(OTG-CONFIG-001\) "wikilink")
  - [Test Application Platform Configuration
    (OTG-CONFIG-002)](Test_Application_Platform_Configuration_\(OTG-CONFIG-002\) "wikilink")
  - [Test File Extensions Handling for Sensitive Information
    (OTG-CONFIG-003)](Test_File_Extensions_Handling_for_Sensitive_Information_\(OTG-CONFIG-003\) "wikilink")
  - [Review Old, Backup and Unreferenced Files for Sensitive Information
    (OTG-CONFIG-004)](Review_Old,_Backup_and_Unreferenced_Files_for_Sensitive_Information_\(OTG-CONFIG-004\) "wikilink")
  - [Enumerate Infrastructure and Application Admin Interfaces
    (OTG-CONFIG-005)](Enumerate_Infrastructure_and_Application_Admin_Interfaces_\(OTG-CONFIG-005\) "wikilink")
  - [Test HTTP Methods
    (OTG-CONFIG-006)](Test_HTTP_Methods_\(OTG-CONFIG-006\) "wikilink")
  - [Test RIA cross domain policy
    (OTG-CONFIG-008)](Test_RIA_cross_domain_policy_\(OTG-CONFIG-008\) "wikilink")
  - [Testing for Error Code
    (OTG-ERR-001)](Testing_for_Error_Code_\(OTG-ERR-001\) "wikilink")
  - [Testing for Stack Traces
    (OTG-ERR-002)](Testing_for_Stack_Traces_\(OTG-ERR-002\) "wikilink")

## A6 Sensitive Data Exposure

### Presentation

*Design:*

  - Use strong ciphers (AES 128 or better) with secure mode of
    operations (do not use ECB).
  - Use strong hashes (SHA 256 or better) with salts for passwords.
  - Protect keys more than any other asset.
  - Use TLS 1.2 or later for all web communications.
  - Buy extended validation (EV) certificates for public web servers.

*Tip: Use TLS 1.2 always – even internally. Most snooping is done within
corporate networks – and it is as easy and unethical as fishing with
dynamite.*

*Render:*

  - Do not send keys or hashes to the browser.

### Controller

*Design:*

  - Use strong ciphers (AES 128 or better) with secure mode of
    operations (do not use ECB).
  - Use strong hashes (SHA 256 or better) with salts for passwords.
  - Protect keys more than any other asset.
  - Mandate strong encrypted communications between web and database
    servers and any other servers or administrative users.

''Tip: Only certain personally identifiable information and sensitive
values MUST be encrypted. Encrypt data that would be embarrassing or
costly if it was leaked or stolen. ''

*Tip: It is best to encrypt data on the application server, rather than
the database server.*

### Model

*Design:*

  - Mandate strong encrypted communications with application servers and
    any other servers or administrative users.

''Tip: Do not use RDBMS database, row or table level encryption. The
data can be retrieved in the clear by anyone with direct access to the
server, or over the network using the application credentials. It might
even traverse the network in the clear despite being "encrypted" on
disk. ''

### Testing

  - [Testing for Weak SSL/TLS Ciphers, Insufficient Transport Layer
    Protection
    (OTG-CRYPST-001)](Testing_for_Weak_SSL/TLS_Ciphers,_Insufficient_Transport_Layer_Protection_\(OTG-CRYPST-001\) "wikilink")
  - [Testing for Padding Oracle
    (OTG-CRYPST-002)](Testing_for_Padding_Oracle_\(OTG-CRYPST-002\) "wikilink")
  - [Testing for Sensitive information sent via unencrypted channels
    (OTG-CRYPST-003)](Testing_for_Sensitive_information_sent_via_unencrypted_channels_\(OTG-CRYPST-003\) "wikilink")
  - [Test HTTP Strict Transport Security
    (OTG-CONFIG-007)](Test_HTTP_Strict_Transport_Security_\(OTG-CONFIG-007\) "wikilink")
  - [Testing for Credentials Transported over an Encrypted Channel
    (OTG-AUTHN-001)](Testing_for_Credentials_Transported_over_an_Encrypted_Channel_\(OTG-AUTHN-001\) "wikilink")

## A7 Missing Function Level Access Control

### Presentation

*Design:*

  - Ensure all non-web data is outside the web root (logs,
    configuration, etc).
  - Use octet byte streaming instead of providing access to real files
    such as PDFs or CSVs or similar.
  - Ensure every page requires a role, even if it is "guest".

*Pre-render:*

  - Validate user is authenticated.
  - Validate role is sufficient to view secured URL.

*Render:*

  - Send CSRF token.

### Controller

  - Validate user is authenticated.
  - Validate role is sufficient to perform secured action.
  - Validate CSRF token.

''Tip: It's impossible to control access to secured resources that the
web application server does not directly serve. Therefore, PDF reports
or similar should be served by the web application server using binary
octet streaming. ''

*Tip: Assume attackers **will** learn where "hidden" directories and
"random" filenames are, so do not store these files in the web root,
even if they are not directly linked.*

### Model

Validate role is sufficient to create, read, update, or delete data

### Testing

  - [Testing Directory traversal/file include
    (OTG-AUTHZ-001)](Testing_Directory_traversal/file_include_\(OTG-AUTHZ-001\) "wikilink")
  - [Testing for Bypassing Authorization Schema
    (OTG-AUTHZ-002)](Testing_for_Bypassing_Authorization_Schema_\(OTG-AUTHZ-002\) "wikilink")
  - [Testing for Bypassing Authentication Schema
    (OTG-AUTHN-004)](Testing_for_Bypassing_Authentication_Schema_\(OTG-AUTHN-004\) "wikilink")

## A8 Cross Site Request Forgery

### Presentation

*Pre-render:*

  - Validate user is authenticated
  - Validate role is sufficient for this view

*Render:*

  - Send CSRF token.
  - Set "secure" and "HttpOnly" flags for session cookies.

### Controller

  - Validate CSRF token.
  - Validate role is sufficient to perform this action.
  - Validate role is sufficient.

''Tip: CSRF is '''always *'possible if there is XSS, so make sure XSS is
eliminated within your application.*

### Model

Validate role is sufficient to create, read, update, or delete data

### Testing

  - [Testing for CSRF
    (OTG-SESS-005)](Testing_for_CSRF_\(OTG-SESS-005\) "wikilink")

## A9 Using Components with Known Vulnerabilities

### Presentation

### Controller

### Model

### Testing

  - [Enumerate Applications on Webserver
    (OTG-INFO-004)](Enumerate_Applications_on_Webserver_\(OTG-INFO-004\) "wikilink")

## A10 Unvalidated Redirects and Forwards

### Presentation

  - Design the app without URL redirection parameters.

or

*Render:*

  - Use random indirect object references for redirection parameters.

### Controller

  - Design the app without URL redirection parameters.

or

  - Obtain direct redirection parameter from random indirect reference
    access map.
  - (LR) Positive validation of redirection parameter.
  - (NR) Java – Do not forward() requests as this prevents SSO access
    control mechanisms.

### Model

  - Validate role is sufficient to create, read, update, or delete data.

### Testing

  - [Testing for Client Side URL Redirect
    (OTG-CLIENT-004)](Testing_for_Client_Side_URL_Redirect_\(OTG-CLIENT-004\) "wikilink")

# Authors and Primary Editors

  - Andrew van der Stock vanderaj\[at\]owasp.org
  - Ismael Rocha Gonçalves ismaelrg\[at\]gmail.com
  - Jorge Correa jacorream@gmail.com