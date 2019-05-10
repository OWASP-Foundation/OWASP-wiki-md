*This is a copy of the ASVS list of security requirements. For the
project, see [:Category:OWASP Application Security Verification Standard
Project](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink").*

# OWASP Application Security Verification Standard (Version 2.0)

## V2: Authentication Verification Requirements

<span id="2.1">2.1.</span> Verify all pages and resources require
authentication except those specifically intended to be public
(Principle of complete mediation).

<span id="2.2">2.2.</span> Verify all password fields do not echo the
user’s password when it is entered.

<span id="2.4">2.4.</span> Verify all authentication controls are
enforced on the server side.

<span id="2.5">2.5.</span> Verify all authentication controls (including
libraries that call external authentication services) have a centralized
implementation.

<span id="2.6">2.6.</span> Verify all authentication controls fail
securely to ensure attackers cannot log in.

<span id="2.7">2.7.</span> Verify password entry fields allow or
encourage the use of passphrases, and do not prevent long passphrases or
highly complex passwords being entered, and provide a sufficient minimum
strength to protect against the use of commonly chosen passwords.

<span id="2.8">2.8.</span> Verify all account identity authentication
functions (such as registration, update profile, forgot username, forgot
password, disabled / lost token, help desk or IVR) that might regain
access to the account are at least as resistant to attack as the primary
authentication mechanism.

<span id="2.9">2.9.</span> Verify users can safely change their
credentials using a mechanism that is at least as resistant to attack as
the primary authentication mechanism.

<span id="2.12">2.12.</span> Verify that all authentication decisions
are logged. This should include requests with missing required
information, needed for security investigations.

<span id="2.13">2.13.</span> Verify that account passwords are salted
using a salt that is unique to that account (e.g., internal user ID,
account creation) and use bcrypt, scrypt or PBKDF2 before storing the
password.

<span id="2.16">2.16.</span> Verify that credentials, and all other
identity information handled by the application(s), do not traverse
unencrypted or weakly encrypted links.

<span id="2.17">2.17.</span> Verify that the forgotten password function
and other recovery paths do not reveal the current password and that the
new password is not sent in clear text to the user.

<span id="2.18">2.18.</span> Verify that username enumeration is not
possible via login, password reset, or forgot account functionality.

<span id="2.19">2.19.</span> Verify there are no default passwords in
use for the application framework or any components used by the
application (such as “admin/password”).

<span id="2.20">2.20.</span> Verify that a resource governor is in place
to protect against vertical (a single account tested against all
possible passwords) and horizontal brute forcing (all accounts tested
with the same password e.g. “Password1”). A correct credential entry
should incur no delay. Both these governor mechanisms should be active
simultaneously to protect against diagonal and distributed attacks.

<span id="2.21">2.21.</span> Verify that all authentication credentials
for accessing services external to the application are encrypted and
stored in a protected location (not in source code).

<span id="2.22">2.22.</span> Verify that forgot password and other
recovery paths send a link including a time-limited activation token
rather than the password itself. Additional authentication based on
soft-tokens (e.g. SMS token, native mobile applications, etc.) can be
required as well before the link is sent over.

<span id="2.23">2.23.</span> Verify that forgot password functionality
does not lock or otherwise disable the account until after the user has
successfully changed their password. This is to prevent valid users from
being locked out.

<span id="2.24">2.24.</span> Verify that there are no shared knowledge
questions/answers (so called "secret" questions and answers).

<span id="2.25">2.25.</span> Verify that the system can be configured to
disallow the use of a configurable number of previous passwords.

<span id="2.26">2.26.</span> Verify re-authentication, step up or
adaptive authentication, SMS or other two factor authentication, or
transaction signing is required before any application-specific
sensitive operations are permitted as per the risk profile of the
application.

## V3: Session Management Verification Requirements

<span id="3.1">3.1.</span> Verify that the framework’s default session
management control implementation is used by the application.

<span id="3.2">3.2.</span> Verify that sessions are invalidated when the
user logs out.

<span id="3.3">3.3.</span> Verify that sessions timeout after a
specified period of inactivity.

<span id="3.4">3.4.</span> Verify that sessions timeout after an
administratively-configurable maximum time period regardless of activity
(an absolute timeout).

<span id="3.5">3.5.</span> Verify that all pages that require
authentication to access them have logout links.

<span id="3.6">3.6.</span> Verify that the session id is never disclosed
other than in cookie headers; particularly in URLs, error messages, or
logs. This includes verifying that the application does not support URL
rewriting of session cookies.

<span id="3.7">3.7.</span> Verify that the session id is changed on
login to prevent session fixation.

<span id="3.8">3.8.</span> Verify that the session id is changed upon
re-authentication.

<span id="3.10">3.10.</span> Verify that only session ids generated by
the application framework are recognized as valid by the application.

<span id="3.11">3.11.</span> Verify that authenticated session tokens
are sufficiently long and random to withstand session guessing attacks.

<span id="3.12">3.12.</span> Verify that authenticated session tokens
using cookies have their path set to an appropriately restrictive value
for that site. The domain cookie attribute restriction should not be set
unless for a business requirement, such as single sign on.

<span id="3.14">3.14.</span> Verify that authenticated session tokens
using cookies sent via HTTP, are protected by the use of "HttpOnly".

<span id="3.15">3.15.</span> Verify that authenticated session tokens
using cookies are protected with the "secure" attribute and a strict
transport security header (such as Strict-Transport-Security:
max-age=60000; includeSubDomains) are present.

<span id="3.16">3.16.</span> Verify that the application does not permit
duplicate concurrent user sessions, originating from different machines.

## V4: Access Control Verification Requirements

<span id="4.1">4.1.</span> Verify that users can only access secured
functions or services for which they possess specific authorization.

<span id="4.2">4.2.</span> Verify that users can only access secured
URLs for which they possess specific authorization.

<span id="4.3">4.3.</span> Verify that users can only access secured
data files for which they possess specific authorization.

<span id="4.4">4.4.</span> Verify that direct object references are
protected, such that only authorized objects or data are accessible to
each user (for example, protect against direct object reference
tampering).

<span id="4.5">4.5.</span> Verify that directory browsing is disabled
unless deliberately desired.

<span id="4.8">4.8.</span> Verify that access controls fail securely.

<span id="4.9">4.9.</span> Verify that the same access control rules
implied by the presentation layer are enforced on the server side for
that user role, such that controls and parameters cannot be re-enabled
or re-added from higher privilege users.

<span id="4.10">4.10.</span> Verify that all user and data attributes
and policy information used by access controls cannot be manipulated by
end users unless specifically authorized.

<span id="4.11">4.11.</span> Verify that all access controls are
enforced on the server side.

<span id="4.12">4.12.</span> Verify that there is a centralized
mechanism (including libraries that call external authorization
services) for protecting access to each type of protected resource.

<span id="4.14">4.14.</span> Verify that all access control decisions
are be logged and all failed decisions are logged.

<span id="4.16">4.16.</span> Verify that the application or framework
generates strong random anti-CSRF tokens unique to the user as part of
all high value transactions or accessing sensitive data, and that the
application verifies the presence of this token with the proper value
for the current user when processing these requests.

<span id="4.17">4.17.</span> Aggregate access control protection –
verify the system can protect against aggregate or continuous access of
secured functions, resources, or data. For example, possibly by the use
of a resource governor to limit the number of edits per hour or to
prevent the entire database from being scraped by an individual user.

## V5: Malicious Input Handling Verification Requirements

<span id="5.1">5.1.</span> Verify that the runtime environment is not
susceptible to buffer overflows, or that security controls prevent
buffer overflows.

<span id="5.3">5.3.</span> Verify that all input validation failures
result in input rejection.

<span id="5.4">5.4.</span> Verify that a character set, such as UTF-8,
is specified for all sources of input.

<span id="5.5">5.5.</span> Verify that all input validation or encoding
routines are performed and enforced on the server side.

<span id="5.6">5.6.</span> Verify that a single input validation control
is used by the application for each type of data that is accepted.

<span id="5.7">5.7.</span> Verify that all input validation failures are
logged.

<span id="5.8">5.8.</span> Verify that all input data is canonicalized
for all downstream decoders or interpreters prior to validation.

<span id="5.10">5.10.</span> Verify that the runtime environment is not
susceptible to SQL Injection, or that security controls prevent SQL
Injection.

<span id="5.11">5.11.</span> Verify that the runtime environment is not
susceptible to LDAP Injection, or that security controls prevent LDAP
Injection.

<span id="5.12">5.12.</span> Verify that the runtime environment is not
susceptible to OS Command Injection, or that security controls prevent
OS Command Injection.

<span id="5.13">5.13.</span> Verify that the runtime environment is not
susceptible to XML External Entity attacks or that security controls
prevents XML External Entity attacks.

<span id="5.14">5.14.</span> Verify that the runtime environment is not
susceptible to XML Injections or that security controls prevents XML
Injections.

<span id="5.16">5.16.</span> Verify that all untrusted data that are
output to HTML (including HTML elements, HTML attributes, JavaScript
data values, CSS blocks, and URI attributes) are properly escaped for
the applicable context.

<span id="5.17">5.17.</span> If the application framework allows
automatic mass parameter assignment (also called automatic variable
binding) from the inbound request to a model, verify that security
sensitive fields such as “accountBalance”, “role” or “password” are
protected from malicious automatic binding.

<span id="5.18">5.18.</span> Verify that the application has defenses
against HTTP parameter pollution attacks, particularly if the
application framework makes no distinction about the source of request
parameters (GET, POST, cookies, headers, environment, etc.)

<span id="5.19">5.19.</span> Verify that for each type of output
encoding/escaping performed by the application, there is a single
security control for that type of output for the intended destination.

## V7: Cryptography at Rest Verification Requirements

<span id="7.1">7.1.</span> Verify that all cryptographic functions used
to protect secrets from the application user are implemented server
side.

<span id="7.2">7.2.</span> Verify that all cryptographic modules fail
securely.

<span id="7.3">7.3.</span> Verify that access to any master secret(s) is
protected from unauthorized access (A master secret is an application
credential stored as plaintext on disk that is used to protect access to
security configuration information).

<span id="7.6">7.6.</span> Verify that all random numbers, random file
names, random GUIDs, and random strings are generated using the
cryptographic module’s approved random number generator when these
random values are intended to be unguessable by an attacker.

<span id="7.7">7.7.</span> Verify that cryptographic modules used by the
application have been validated against FIPS 140-2 or an equivalent
standard.

<span id="7.8">7.8.</span> Verify that cryptographic modules operate in
their approved mode according to their published security policies.

<span id="7.9">7.9.</span> Verify that there is an explicit policy for
how cryptographic keys are managed (e.g., generated, distributed,
revoked, expired). Verify that this policy is properly enforced.

## V8: Error Handling and Logging Verification Requirements

<span id="8.1">8.1.</span> Verify that the application does not output
error messages or stack traces containing sensitive data that could
assist an attacker, including session id and personal information.

<span id="8.2">8.2.</span> Verify that all error handling is performed
on trusted devices

<span id="8.3">8.3.</span> Verify that all logging controls are
implemented on the server.

<span id="8.4">8.4.</span> Verify that error handling logic in security
controls denies access by default.

<span id="8.5">8.5.</span> Verify security logging controls provide the
ability to log both success and failure events that are identified as
security-relevant.

<span id="8.6">8.6.</span> Verify that each log event includes: a
timestamp from a reliable source, severity level of the event, an
indication that this is a security relevant event (if mixed with other
logs), the identity of the user that caused the event (if there is a
user associated with the event), the source IP address of the request
associated with the event, whether the event succeeded or failed, and a
description of the event.

<span id="8.7">8.7.</span> Verify that all events that include untrusted
data will not execute as code in the intended log viewing software.

<span id="8.8">8.8.</span> Verify that security logs are protected from
unauthorized access and modification.

<span id="8.9">8.9.</span> Verify that there is a single
application-level logging implementation that is used by the software.

<span id="8.10">8.10.</span> Verify that the application does not log
application-specific sensitive data that could assist an attacker,
including user’s session identifiers and personal or sensitive
information. The length and existence of sensitive data can be logged.

<span id="8.11">8.11.</span> Verify that a log analysis tool is
available which allows the analyst to search for log events based on
combinations of search criteria across all fields in the log record
format supported by this system.

<span id="8.13">8.13.</span> Verify that all non-printable symbols and
field separators are properly encoded in log entries, to prevent log
injection.

<span id="8.14">8.14.</span> Verify that log fields from trusted and
untrusted sources are distinguishable in log entries.

<span id="8.15">8.15.</span> Verify that logging is performed before
executing the transaction. If logging was unsuccessful (e.g. disk full,
insufficient permissions) the application fails safe. This is for when
integrity and non-repudiation are a must.

## V9: Data Protection Verification Requirements

<span id="9.1">9.1.</span> Verify that all forms containing sensitive
information have disabled client side caching, including autocomplete
features.

<span id="9.2">9.2.</span> Verify that the list of sensitive data
processed by this application is identified, and that there is an
explicit policy for how access to this data must be controlled, and when
this data must be encrypted (both at rest and in transit). Verify that
this policy is properly enforced.

<span id="9.3">9.3.</span> Verify that all sensitive data is sent to the
server in the HTTP message body (i.e., URL parameters are never used to
send sensitive data).

<span id="9.4">9.4.</span> Verify that all cached or temporary copies of
sensitive data sent to the client are protected from unauthorized access
or purged/invalidated after the authorized user accesses the sensitive
data (e.g., the proper no-cache and no-store Cache-Control headers are
set).

<span id="9.5">9.5.</span> Verify that all cached or temporary copies of
sensitive data stored on the server are protected from unauthorized
access or purged/invalidated after the authorized user accesses the
sensitive data.

<span id="9.6">9.6.</span> Verify that there is a method to remove each
type of sensitive data from the application at the end of its required
retention period.

<span id="9.7">9.7.</span> Verify the application minimizes the number
of parameters sent to untrusted systems, such as hidden fields, Ajax
variables, cookies and header values.

<span id="9.8">9.8.</span> Verify the application has the ability to
detect and alert on abnormal numbers of requests for information or
processing high value transactions for that user role, such as screen
scraping, automated use of web service extraction, or data loss
prevention. For example, the average user should not be able to access
more than 5 records per hour or 30 records per day, or add 10 friends to
a social network per minute.

## V10: Communications Security Verification Requirements

<span id="10.1">10.1.</span> Verify that a path can be built from a
trusted CA to each Transport Layer Security (TLS) server certificate,
and that each server certificate is valid.

<span id="10.2">10.2.</span> Verify that failed TLS connections do not
fall back to an insecure HTTP connection.

<span id="10.3">10.3.</span> Verify that TLS is used for all connections
(including both external and backend connections) that are authenticated
or that involve sensitive data or functions.

<span id="10.4">10.4.</span> Verify that backend TLS connection failures
are logged.

<span id="10.5">10.5.</span> Verify that certificate paths are built and
verified for all client certificates using configured trust anchors and
revocation information.

<span id="10.6">10.6.</span> Verify that all connections to external
systems that involve sensitive information or functions are
authenticated.

<span id="10.7">10.7.</span> Verify that all connections to external
systems that involve sensitive information or functions use an account
that has been set up to have the minimum privileges necessary for the
application to function properly.

<span id="10.8">10.8.</span> Verify that there is a single standard TLS
implementation that is used by the application that is configured to
operate in an approved mode of operation (See
<http://csrc.nist.gov/groups/STM/cmvp/documents/fips140-2/FIPS1402IG.pdf>
).

<span id="10.9">10.9.</span> Verify that specific character encodings
are defined for all connections (e.g., UTF-8).

## V11: HTTP Security Verification Requirements

<span id="11.2">11.2.</span> Verify that the application accepts only a
defined set of HTTP request methods, such as GET and POST and unused
methods are explicitly blocked.

<span id="11.3">11.3.</span> Verify that every HTTP response contains a
content type header specifying a safe character set (e.g., UTF-8).

<span id="11.6">11.6.</span> Verify that HTTP headers in both requests
and responses contain only printable ASCII characters.

<span id="11.8">11.8.</span> Verify that HTTP headers and / or other
mechanisms for older browsers have been included to protect against
clickjacking attacks.

<span id="11.9">11.9.</span> Verify that HTTP headers added by a
frontend (such as X-Real-IP), and used by the application, cannot be
spoofed by the end user.

<span id="11.10">11.10.</span> Verify that the HTTP header,
X-Frame-Options is in use for sites where content should not be viewed
in a 3rd-party X-Frame. A common middle ground is to send SAMEORIGIN,
meaning only websites of the same origin may frame it.

<span id="11.12">11.12.</span> Verify that the HTTP headers do not
expose detailed version information of system components.

## V13: Malicious Controls Verification Requirements

<span id="13.1">13.1.</span> Verify that no malicious code is in any
code that was either developed or modified in order to create the
application.

<span id="13.2">13.2.</span> Verify that the integrity of interpreted
code, libraries, executables, and configuration files is verified using
checksums or hashes.

<span id="13.3">13.3.</span> Verify that all code implementing or using
authentication controls is not affected by any malicious code.

<span id="13.4">13.4.</span> Verify that all code implementing or using
session management controls is not affected by any malicious code.

<span id="13.5">13.5.</span> Verify that all code implementing or using
access controls is not affected by any malicious code.

<span id="13.6">13.6.</span> Verify that all input validation controls
are not affected by any malicious code.

<span id="13.7">13.7.</span> Verify that all code implementing or using
output validation controls is not affected by any malicious code.

<span id="13.8">13.8.</span> Verify that all code supporting or using a
cryptographic module is not affected by any malicious code.

<span id="13.9">13.9.</span> Verify that all code implementing or using
error handling and logging controls is not affected by any malicious
code.

<span id="13.10">13.10.</span> Verify all malicious activity is
adequately sandboxed.

<span id="13.11">13.11.</span> Verify that sensitive data is rapidly
sanitized from memory as soon as it is no longer needed and handled in
accordance to functions and techniques supported by the
framework/library/operating system.

## V15: Business Logic Verification Requirements

<span id="15.1">15.1.</span> Verify the application processes or
verifies all high value business logic flows in a trusted environment,
such as on a protected and monitored server.

<span id="15.2">15.2.</span> Verify the application does not allow
spoofed high value transactions, such as allowing Attacker User A to
process a transaction as Victim User B by tampering with or replaying
session, transaction state, transaction or user IDs.

<span id="15.3">15.3.</span> Verify the application does not allow high
value business logic parameters to be tampered with, such as (but not
limited to): price, interest, discounts, PII, balances, stock IDs, etc.

<span id="15.4">15.4.</span> Verify the application has defensive
measures to protect against repudiation attacks, such as verifiable and
protected transaction logs, audit trails or system logs, and in highest
value systems real time monitoring of user activities and transactions
for anomalies.

<span id="15.5">15.5.</span> Verify the application protects against
information disclosure attacks, such as direct object reference,
tampering, session brute force or other attacks.

<span id="15.6">15.6.</span> Verify the application has sufficient
detection and governor controls to protect against brute force (such as
continuously using a particular function) or denial of service attacks.

<span id="15.7">15.7.</span> Verify the application has sufficient
access controls to prevent elevation of privilege attacks, such as
allowing anonymous users from accessing secured data or secured
functions, or allowing users to access each other’s details or using
privileged functions.

<span id="15.8">15.8.</span> Verify the application will only process
business logic flows in sequential step order, with all steps being
processed in realistic human time, and not process out of order, skipped
steps, process steps from another user, or too quickly submitted
transactions.

<span id="15.9">15.9.</span> Verify the application has additional
authorization (such as step up or adaptive authentication) for lower
value systems, and / or segregation of duties for high value
applications to enforce anti-fraud controls as per the risk of
application and past fraud.

<span id="15.10">15.10.</span> Verify the application has business
limits and enforces them in a trusted location (as on a protected
server) on a per user, per day or daily basis, with configurable
alerting and automated reactions to automated or unusual attack.
Examples include (but not limited to): ensuring new SIM users don’t
exceed $10 per day for a new phone account, a forum allowing more than
100 new users per day or preventing posts or private messages until the
account has been verified, a health system should not allow a single
doctor to access more patient records than they can reasonably treat in
a day, or a small business finance system allowing more than 20 invoice
payments or $1000 per day across all users. In all cases, the business
limits and totals should be reasonable for the business concerned. The
only unreasonable outcome is if there are no business limits, alerting
or enforcement.

## V16: Files and Resources Verification Requirements

<span id="16.1">16.1.</span> Verify that URL redirects and forwards do
not include unvalidated data.

<span id="16.2">16.2.</span> Verify that file names and path data
obtained from untrusted sources is canonicalized to eliminate path
traversal attacks.

<span id="16.3">16.3.</span> Verify that files obtained from untrusted
sources are scanned by antivirus scanners to prevent upload of known
malicious content.

<span id="16.4">16.4.</span> Verify that parameters obtained from
untrusted sources are not used in manipulating filenames, pathnames or
any file system object without first being canonicalized and input
validated to prevent local file inclusion attacks.

<span id="16.5">16.5.</span> Verify that parameters obtained from
untrusted sources are canonicalized, input validated, and output encoded
to prevent remote file inclusion attacks, particularly where input could
be executed, such as header, source, or template inclusion

<span id="16.6">16.6.</span> Verify remote IFRAMEs and HTML5
cross-domain resource sharing does not allow inclusion of arbitrary
remote content.

<span id="16.7">16.7.</span> Verify that files obtained from untrusted
sources are stored outside the webroot.

<span id="16.8">16.8.</span> Verify that web or application server is
configured by default to deny access to remote resources or systems
outside the web or application server.

<span id="16.9">16.9.</span> Verify the application code does not
execute uploaded data obtained from untrusted sources.

<span id="16.10">16.10.</span> Verify if Flash, Silverlight or other
rich internet application (RIA) cross domain resource sharing
configuration is configured to prevent unauthenticated or unauthorized
remote access.

## V17: Mobile Verification Requirements

<span id="17.1">17.1.</span> Verify that the client validates SSL
certificates

<span id="17.2">17.2.</span> Verify that unique device ID (UDID) values
are not used as security controls.

<span id="17.3">17.3.</span> Verify that the mobile app does not store
sensitive data onto shared resources on the device (e.g. SD card or
shared folders)

<span id="17.4">17.4.</span> Verify that sensitive data is not stored in
SQLite database on the device.

<span id="17.5">17.5.</span> Verify that secret keys or passwords are
not hard-coded in the executable.

<span id="17.6">17.6.</span> Verify that the mobile app prevents leaking
of sensitive data via auto-snapshot feature of iOS.

<span id="17.7">17.7.</span> Verify that the app cannot be run on a
jailbroken or rooted device.

<span id="17.8">17.8.</span> Verify that the session timeout is of a
reasonable value.

<span id="17.9">17.9.</span> Verify the permissions being requested as
well as the resources that it is authorized to access (i.e.
AndroidManifest.xml, iOS Entitlements) .

<span id="17.10">17.10.</span> Verify that crash logs do not contain
sensitive data.

<span id="17.11">17.11.</span> Verify that the application binary has
been obfuscated.

<span id="17.12">17.12.</span> Verify that all test data has been
removed from the app container (.ipa, .apk, .bar).

<span id="17.13">17.13.</span> Verify that the application does not log
sensitive data to the system log or filesystem.

<span id="17.14">17.14.</span> Verify that the application does not
enable autocomplete for sensitive text input fields, such as passwords,
personal information or credit cards.

<span id="17.15">17.15.</span> Verify that the mobile app implements
certificate pinning to prevent the proxying of app traffic.

<span id="17.16">17.16.</span> Verify no misconfigurations are present
in the configuration files (Debugging flags set, world readable/writable
permissions) and that, by default, configuration settings are set to
their safest/most secure value.

<span id="17.17">17.17.</span> Verify any 3rd-party libraries in use are
up to date, contain no known vulnerabilities.

<span id="17.18">17.18.</span> Verify that web data, such as HTTPS
traffic, is not cached.

<span id="17.19">17.19.</span> Verify that the query string is not used
for sensitive data. Instead, a POST request via SSL should be used with
a CSRF token.

<span id="17.20">17.20.</span> Verify that, if applicable, any personal
account numbers are truncated prior to storing on the device.

<span id="17.21">17.21.</span> Verify that the application makes use of
Address Space Layout Randomization (ASLR).

<span id="17.22">17.22.</span> Verify that data logged via the keyboard
(iOS) does not contain credentials, financial information or other
sensitive data.

<span id="17.23">17.23.</span> If an Android app, verify that the app
does not create files with permissions of MODE_WORLD_READABLE or
MODE_WORLD_WRITABLE

<span id="17.24">17.24.</span> Verify that sensitive data is stored in a
cryptographically secure manner (even when stored in the iOS keychain).

<span id="17.25">17.25.</span> Verify that anti-debugging and reverse
engineering mechanisms are implemented in the app.

<span id="17.26">17.26.</span> Verify that the app does not export
sensitive activities, intents, content providers etc. on Android.

<span id="17.27">17.27.</span> Verify that mutable structures have been
used for sensitive strings such as account numbers and are overwritten
when not used. (Mitigate damage from memory analysis attacks).

<span id="17.28">17.28.</span> Verify that any exposed intents, content
providers and broadcast receivers perform full data validation on input
(Android).