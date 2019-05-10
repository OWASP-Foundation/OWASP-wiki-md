*This is a copy of the SCP checklist. For the project, see [OWASP Secure
Coding Practices - Quick Reference
Guide](OWASP_Secure_Coding_Practices_-_Quick_Reference_Guide "wikilink").*

## Input Validation

<span id="1">1.</span> Conduct all data validation on a trusted system
(e.g., The server)

<span id="2">2.</span> Identify all data sources and classify them into
trusted and untrusted. Validate all data from untrusted sources (e.g.,
Databases, file streams, etc.)

<span id="3">3.</span> There should be a centralized input validation
routine for the application

<span id="4">4.</span> Specify proper character sets, such as UTF-8, for
all sources of input

<span id="5">5.</span> Encode data to a common character set before
validating (Canonicalize)

<span id="6">6.</span> All validation failures should result in input
rejection

<span id="7">7.</span> Determine if the system supports UTF-8 extended
character sets and if so, validate after UTF-8 decoding is completed

<span id="8">8.</span> Validate all client provided data before
processing, including all parameters, URLs and HTTP header content (e.g.
Cookie names and values). Be sure to include automated post backs from
JavaScript, Flash or other embedded code

<span id="9">9.</span> Verify that header values in both requests and
responses contain only ASCII characters

<span id="10">10.</span> Validate data from redirects (An attacker may
submit malicious content directly to the target of the redirect, thus
circumventing application logic and any validation performed before the
redirect)

<span id="11">11.</span> Validate for expected data types

<span id="12">12.</span> Validate data range

<span id="13">13.</span> Validate data length

<span id="14">14.</span> Validate all input against a "white" list of
allowed characters, whenever possible

<span id="15">15.</span> If any potentially hazardous characters must be
allowed as input, be sure that you implement additional controls like
output encoding, secure task specific APIs and accounting for the
utilization of that data throughout the application. Examples of common
hazardous characters include: \< \> " ' % ( ) & + \\ \\' \\"

<span id="16">16.</span> If your standard validation routine cannot
address the following inputs, then they should be checked discretely

  - Check for null bytes (%00)

<!-- end list -->

  - Check for new line characters (%0d, %0a, \\r, \\n)

<!-- end list -->

  - Check for “dot-dot-slash" (../ or ..\\) path alterations characters.
    In cases where UTF-8 extended character set encoding is supported,
    address alternate representation like: %c0%ae%c0%ae/

(Utilize canonicalization to address double encoding or other forms of
obfuscation attacks)

## Output Encoding

<span id="17">17.</span> Conduct all encoding on a trusted system (e.g.,
The server)

<span id="18">18.</span> Utilize a standard, tested routine for each
type of outbound encoding

<span id="19">19.</span> Contextually output encode all data returned to
the client that originated outside the application's trust boundary.
HTML entity encoding is one example, but does not work in all cases

<span id="20">20.</span> Encode all characters unless they are known to
be safe for the intended interpreter

<span id="21">21.</span> Contextually sanitize all output of un-trusted
data to queries for SQL, XML, and LDAP

<span id="22">22.</span> Sanitize all output of un-trusted data to
operating system commands

## Authentication and Password Management

<span id="23">23.</span> Require authentication for all pages and
resources, except those specifically intended to be public

<span id="24">24.</span> All authentication controls must be enforced on
a trusted system (e.g., The server)

<span id="25">25.</span> Establish and utilize standard, tested,
authentication services whenever possible

<span id="26">26.</span> Use a centralized implementation for all
authentication controls, including libraries that call external
authentication services

<span id="27">27.</span> Segregate authentication logic from the
resource being requested and use redirection to and from the centralized
authentication control

<span id="28">28.</span> All authentication controls should fail
securely

<span id="29">29.</span> All administrative and account management
functions must be at least as secure as the primary authentication
mechanism

<span id="30">30.</span> If your application manages a credential store,
it should ensure that only cryptographically strong one-way salted
hashes of passwords are stored and that the table/file that stores the
passwords and keys is write-able only by the application. (Do not use
the MD5 algorithm if it can be avoided)

<span id="31">31.</span> Password hashing must be implemented on a
trusted system (e.g., The server).

<span id="32">32.</span> Validate the authentication data only on
completion of all data input, especially for sequential authentication
implementations

<span id="33">33.</span> Authentication failure responses should not
indicate which part of the authentication data was incorrect. For
example, instead of "Invalid username" or "Invalid password", just use
"Invalid username and/or password" for both. Error responses must be
truly identical in both display and source code

<span id="34">34.</span> Utilize authentication for connections to
external systems that involve sensitive information or functions

<span id="35">35.</span> Authentication credentials for accessing
services external to the application should be encrypted and stored in a
protected location on a trusted system (e.g., The server). The source
code is NOT a secure location

<span id="36">36.</span> Use only HTTP POST requests to transmit
authentication credentials

<span id="37">37.</span> Only send non-temporary passwords over an
encrypted connection or as encrypted data, such as in an encrypted
email. Temporary passwords associated with email resets may be an
exception

<span id="38">38.</span> Enforce password complexity requirements
established by policy or regulation. Authentication credentials should
be sufficient to withstand attacks that are typical of the threats in
the deployed environment. (e.g., requiring the use of alphabetic as well
as numeric and/or special characters)

<span id="39">39.</span> Enforce password length requirements
established by policy or regulation. Eight characters is commonly used,
but 16 is better or consider the use of multi-word pass phrases

<span id="40">40.</span> Password entry should be obscured on the user's
screen. (e.g., on web forms use the input type "password")

<span id="41">41.</span> Enforce account disabling after an established
number of invalid login attempts (e.g., five attempts is common). The
account must be disabled for a period of time sufficient to discourage
brute force guessing of credentials, but not so long as to allow for a
denial-of-service attack to be performed

<span id="42">42.</span> Password reset and changing operations require
the same level of controls as account creation and authentication.

<span id="43">43.</span> Password reset questions should support
sufficiently random answers. (e.g., "favorite book" is a bad question
because “The Bible” is a very common answer)

<span id="44">44.</span> If using email based resets, only send email to
a pre-registered address with a temporary link/password

<span id="45">45.</span> Temporary passwords and links should have a
short expiration time

<span id="46">46.</span> Enforce the changing of temporary passwords on
the next use

<span id="47">47.</span> Notify users when a password reset occurs

<span id="48">48.</span> Prevent password re-use

<span id="49">49.</span> Passwords should be at least one day old before
they can be changed, to prevent attacks on password re-use

<span id="50">50.</span> Enforce password changes based on requirements
established in policy or regulation. Critical systems may require more
frequent changes. The time between resets must be administratively
controlled

<span id="51">51.</span> Disable "remember me" functionality for
password fields

<span id="52">52.</span> The last use (successful or unsuccessful) of a
user account should be reported to the user at their next successful
login

<span id="53">53.</span> Implement monitoring to identify attacks
against multiple user accounts, utilizing the same password. This attack
pattern is used to bypass standard lockouts, when user IDs can be
harvested or guessed

<span id="54">54.</span> Change all vendor-supplied default passwords
and user IDs or disable the associated accounts

<span id="55">55.</span> Re-authenticate users prior to performing
critical operations

<span id="56">56.</span> Use Multi-Factor Authentication for highly
sensitive or high value transactional accounts

<span id="57">57.</span> If using third party code for authentication,
inspect the code carefully to ensure it is not affected by any malicious
code

## Session Management

<span id="58">58.</span> Use the server or framework’s session
management controls. The application should only recognize these session
identifiers as valid

<span id="59">59.</span> Session identifier creation must always be done
on a trusted system (e.g., The server)

<span id="60">60.</span> Session management controls should use well
vetted algorithms that ensure sufficiently random session identifiers

<span id="61">61.</span> Set the domain and path for cookies containing
authenticated session identifiers to an appropriately restricted value
for the site

<span id="62">62.</span> Logout functionality should fully terminate the
associated session or connection

<span id="63">63.</span> Logout functionality should be available from
all pages protected by authorization

<span id="64">64.</span> Establish a session inactivity timeout that is
as short as possible, based on balancing risk and business functional
requirements. In most cases it should be no more than several hours

<span id="65">65.</span> Disallow persistent logins and enforce periodic
session terminations, even when the session is active. Especially for
applications supporting rich network connections or connecting to
critical systems. Termination times should support business requirements
and the user should receive sufficient notification to mitigate negative
impacts

<span id="66">66.</span> If a session was established before login,
close that session and establish a new session after a successful login

<span id="67">67.</span> Generate a new session identifier on any
re-authentication

<span id="68">68.</span> Do not allow concurrent logins with the same
user ID

<span id="69">69.</span> Do not expose session identifiers in URLs,
error messages or logs. Session identifiers should only be located in
the HTTP cookie header. For example, do not pass session identifiers as
GET parameters

<span id="70">70.</span> Protect server side session data from
unauthorized access, by other users of the server, by implementing
appropriate access controls on the server

<span id="71">71.</span> Generate a new session identifier and
deactivate the old one periodically. (This can mitigate certain session
hijacking scenarios where the original identifier was compromised)

<span id="72">72.</span> Generate a new session identifier if the
connection security changes from HTTP to HTTPS, as can occur during
authentication. Within an application, it is recommended to consistently
utilize HTTPS rather than switching between HTTP to HTTPS.

<span id="73">73.</span> Supplement standard session management for
sensitive server-side operations, like account management, by utilizing
per-session strong random tokens or parameters. This method can be used
to prevent Cross Site Request Forgery attacks

<span id="74">74.</span> Supplement standard session management for
highly sensitive or critical operations by utilizing per-request, as
opposed to per-session, strong random tokens or parameters

<span id="75">75.</span> Set the "secure" attribute for cookies
transmitted over an TLS connection

<span id="76">76.</span> Set cookies with the HttpOnly attribute, unless
you specifically require client-side scripts within your application to
read or set a cookie's value

## Access Control

<span id="77">77.</span> Use only trusted system objects, e.g. server
side session objects, for making access authorization decisions

<span id="78">78.</span> Use a single site-wide component to check
access authorization. This includes libraries that call external
authorization services

<span id="79">79.</span> Access controls should fail securely

<span id="80">80.</span> Deny all access if the application cannot
access its security configuration information

<span id="81">81.</span> Enforce authorization controls on every
request, including those made by server side scripts, "includes" and
requests from rich client-side technologies like AJAX and Flash

<span id="82">82.</span> Segregate privileged logic from other
application code

<span id="83">83.</span> Restrict access to files or other resources,
including those outside the application's direct control, to only
authorized users

<span id="84">84.</span> Restrict access to protected URLs to only
authorized users

<span id="85">85.</span> Restrict access to protected functions to only
authorized users

<span id="86">86.</span> Restrict direct object references to only
authorized users

<span id="87">87.</span> Restrict access to services to only authorized
users

<span id="88">88.</span> Restrict access to application data to only
authorized users

<span id="89">89.</span> Restrict access to user and data attributes and
policy information used by access controls

<span id="90">90.</span> Restrict access security-relevant configuration
information to only authorized users

<span id="91">91.</span> Server side implementation and presentation
layer representations of access control rules must match

<span id="92">92.</span> If state data must be stored on the client, use
encryption and integrity checking on the server side to catch state
tampering.

<span id="93">93.</span> Enforce application logic flows to comply with
business rules

<span id="94">94.</span> Limit the number of transactions a single user
or device can perform in a given period of time. The transactions/time
should be above the actual business requirement, but low enough to deter
automated attacks

<span id="95">95.</span> Use the "referer" header as a supplemental
check only, it should never be the sole authorization check, as it is
can be spoofed

<span id="96">96.</span> If long authenticated sessions are allowed,
periodically re-validate a user’s authorization to ensure that their
privileges have not changed and if they have, log the user out and force
them to re-authenticate

<span id="97">97.</span> Implement account auditing and enforce the
disabling of unused accounts (e.g., After no more than 30 days from the
expiration of an account’s password.)

<span id="98">98.</span> The application must support disabling of
accounts and terminating sessions when authorization ceases (e.g.,
Changes to role, employment status, business process, etc.)

<span id="99">99.</span> Service accounts or accounts supporting
connections to or from external systems should have the least privilege
possible

<span id="100">100.</span> Create an Access Control Policy to document
an application's business rules, data types and access authorization
criteria and/or processes so that access can be properly provisioned and
controlled. This includes identifying access requirements for both the
data and system resources

## Cryptographic Practices

<span id="101">101.</span> All cryptographic functions used to protect
secrets from the application user must be implemented on a trusted
system (e.g., The server)

<span id="102">102.</span> Protect master secrets from unauthorized
access

<span id="103">103.</span> Cryptographic modules should fail securely

<span id="104">104.</span> All random numbers, random file names, random
GUIDs, and random strings should be generated using the cryptographic
module’s approved random number generator when these random values are
intended to be un-guessable

<span id="105">105.</span> Cryptographic modules used by the application
should be compliant to FIPS 140-2 or an equivalent standard. (See
<http://csrc.nist.gov/groups/STM/cmvp/validation.html>)

<span id="106">106.</span> Establish and utilize a policy and process
for how cryptographic keys will be managed

## Error Handling and Logging

<span id="107">107.</span> Do not disclose sensitive information in
error responses, including system details, session identifiers or
account information

<span id="108">108.</span> Use error handlers that do not display
debugging or stack trace information

<span id="109">109.</span> Implement generic error messages and use
custom error pages

<span id="110">110.</span> The application should handle application
errors and not rely on the server configuration

<span id="111">111.</span> Properly free allocated memory when error
conditions occur

<span id="112">112.</span> Error handling logic associated with security
controls should deny access by default

<span id="113">113.</span> All logging controls should be implemented on
a trusted system (e.g., The server)

<span id="114">114.</span> Logging controls should support both success
and failure of specified security events

<span id="115">115.</span> Ensure logs contain important log event data

<span id="116">116.</span> Ensure log entries that include un-trusted
data will not execute as code in the intended log viewing interface or
software

<span id="117">117.</span> Restrict access to logs to only authorized
individuals

<span id="118">118.</span> Utilize a master routine for all logging
operations

<span id="119">119.</span> Do not store sensitive information in logs,
including unnecessary system details, session identifiers or passwords

<span id="120">120.</span> Ensure that a mechanism exists to conduct log
analysis

<span id="121">121.</span> Log all input validation failures

<span id="122">122.</span> Log all authentication attempts, especially
failures

<span id="123">123.</span> Log all access control failures

<span id="124">124.</span> Log all apparent tampering events, including
unexpected changes to state data

<span id="125">125.</span> Log attempts to connect with invalid or
expired session tokens

<span id="126">126.</span> Log all system exceptions

<span id="127">127.</span> Log all administrative functions, including
changes to the security configuration settings

<span id="128">128.</span> Log all backend TLS connection failures

<span id="129">129.</span> Log cryptographic module failures

<span id="130">130.</span> Use a cryptographic hash function to validate
log entry integrity Data Protection:

<span id="131">131.</span> Implement least privilege, restrict users to
only the functionality, data and system information that is required to
perform their tasks

<span id="132">132.</span> Protect all cached or temporary copies of
sensitive data stored on the server from unauthorized access and purge
those temporary working files a soon as they are no longer required.

<span id="133">133.</span> Encrypt highly sensitive stored information,
like authentication verification data, even on the server side. Always
use well vetted algorithms, see "Cryptographic Practices" for additional
guidance

<span id="134">134.</span> Protect server-side source-code from being
downloaded by a user

<span id="135">135.</span> Do not store passwords, connection strings or
other sensitive information in clear text or in any
non-cryptographically secure manner on the client side. This includes
embedding in insecure formats like: MS viewstate, Adobe flash or
compiled code

<span id="136">136.</span> Remove comments in user accessible production
code that may reveal backend system or other sensitive information

<span id="137">137.</span> Remove unnecessary application and system
documentation as this can reveal useful information to attackers

<span id="138">138.</span> Do not include sensitive information in HTTP
GET request parameters

<span id="139">139.</span> Disable auto complete features on forms
expected to contain sensitive information, including authentication

<span id="140">140.</span> Disable client side caching on pages
containing sensitive information. Cache-Control: no-store, may be used
in conjunction with the HTTP header control "Pragma: no-cache", which is
less effective, but is HTTP/1.0 backward compatible

<span id="141">141.</span> The application should support the removal of
sensitive data when that data is no longer required. (e.g. personal
information or certain financial data)

<span id="142">142.</span> Implement appropriate access controls for
sensitive data stored on the server. This includes cached data,
temporary files and data that should be accessible only by specific
system users

## Communication Security

<span id="143">143.</span> Implement encryption for the transmission of
all sensitive information. This should include TLS for protecting the
connection and may be supplemented by discrete encryption of sensitive
files or non-HTTP based connections

<span id="144">144.</span> TLS certificates should be valid and have the
correct domain name, not be expired, and be installed with intermediate
certificates when required

<span id="145">145.</span> Failed TLS connections should not fall back
to an insecure connection

<span id="146">146.</span> Utilize TLS connections for all content
requiring authenticated access and for all other sensitive information

<span id="147">147.</span> Utilize TLS for connections to external
systems that involve sensitive information or functions

<span id="148">148.</span> Utilize a single standard TLS implementation
that is configured appropriately

<span id="149">149.</span> Specify character encodings for all
connections

<span id="150">150.</span> Filter parameters containing sensitive
information from the HTTP referer, when linking to external sites

## System Configuration

<span id="151">151.</span> Ensure servers, frameworks and system
components are running the latest approved version

<span id="152">152.</span> Ensure servers, frameworks and system
components have all patches issued for the version in use

<span id="153">153.</span> Turn off directory listings

<span id="154">154.</span> Restrict the web server, process and service
accounts to the least privileges possible

<span id="155">155.</span> When exceptions occur, fail securely

<span id="156">156.</span> Remove all unnecessary functionality and
files

<span id="157">157.</span> Remove test code or any functionality not
intended for production, prior to deployment

<span id="158">158.</span> Prevent disclosure of your directory
structure in the robots.txt file by placing directories not intended for
public indexing into an isolated parent directory. Then "Disallow" that
entire parent directory in the robots.txt file rather than Disallowing
each individual directory

<span id="159">159.</span> Define which HTTP methods, Get or Post, the
application will support and whether it will be handled differently in
different pages in the application

<span id="160">160.</span> Disable unnecessary HTTP methods, such as
WebDAV extensions. If an extended HTTP method that supports file
handling is required, utilize a well-vetted authentication mechanism

<span id="161">161.</span> If the web server handles both HTTP 1.0 and
1.1, ensure that both are configured in a similar manor or insure that
you understand any difference that may exist (e.g. handling of extended
HTTP methods)

<span id="162">162.</span> Remove unnecessary information from HTTP
response headers related to the OS, web-server version and application
frameworks

<span id="163">163.</span> The security configuration store for the
application should be able to be output in human readable form to
support auditing

<span id="164">164.</span> Implement an asset management system and
register system components and software in it

<span id="165">165.</span> Isolate development environments from the
production network and provide access only to authorized development and
test groups. Development environments are often configured less securely
than production environments and attackers may use this difference to
discover shared weaknesses or as an avenue for exploitation

<span id="166">166.</span> Implement a software change control system to
manage and record changes to the code both in development and production

## Database Security

<span id="167">167.</span> Use strongly typed parameterized queries

<span id="168">168.</span> Utilize input validation and output encoding
and be sure to address meta characters. If these fail, do not run the
database command

<span id="169">169.</span> Ensure that variables are strongly typed

<span id="170">170.</span> The application should use the lowest
possible level of privilege when accessing the database

<span id="171">171.</span> Use secure credentials for database access

<span id="172">172.</span> Connection strings should not be hard coded
within the application. Connection strings should be stored in a
separate configuration file on a trusted system and they should be
encrypted.

<span id="173">173.</span> Use stored procedures to abstract data access
and allow for the removal of permissions to the base tables in the
database

<span id="174">174.</span> Close the connection as soon as possible

<span id="175">175.</span> Remove or change all default database
administrative passwords. Utilize strong passwords/phrases or implement
multi-factor authentication

<span id="176">176.</span> Turn off all unnecessary database
functionality (e.g., unnecessary stored procedures or services, utility
packages, install only the minimum set of features and options required
(surface area reduction))

<span id="177">177.</span> Remove unnecessary default vendor content
(e.g., sample schemas)

<span id="178">178.</span> Disable any default accounts that are not
required to support business requirements

<span id="179">179.</span> The application should connect to the
database with different credentials for every trust distinction (e.g.,
user, read-only user, guest, administrators)

## File Management

<span id="180">180.</span> Do not pass user supplied data directly to
any dynamic include function

<span id="181">181.</span> Require authentication before allowing a file
to be uploaded

<span id="182">182.</span> Limit the type of files that can be uploaded
to only those types that are needed for business purposes

<span id="183">183.</span> Validate uploaded files are the expected type
by checking file headers. Checking for file type by extension alone is
not sufficient

<span id="184">184.</span> Do not save files in the same web context as
the application. Files should either go to the content server or in the
database.

<span id="185">185.</span> Prevent or restrict the uploading of any file
that may be interpreted by the web server.

<span id="186">186.</span> Turn off execution privileges on file upload
directories

<span id="187">187.</span> Implement safe uploading in UNIX by mounting
the targeted file directory as a logical drive using the associated path
or the chrooted environment

<span id="188">188.</span> When referencing existing files, use a white
list of allowed file names and types. Validate the value of the
parameter being passed and if it does not match one of the expected
values, either reject it or use a hard coded default file value for the
content instead

<span id="189">189.</span> Do not pass user supplied data into a dynamic
redirect. If this must be allowed, then the redirect should accept only
validated, relative path URLs

<span id="190">190.</span> Do not pass directory or file paths, use
index values mapped to pre-defined list of paths

<span id="191">191.</span> Never send the absolute file path to the
client

<span id="192">192.</span> Ensure application files and resources are
read-only

<span id="193">193.</span> Scan user uploaded files for viruses and
malware

## Memory Management

<span id="194">194.</span> Utilize input and output control for
un-trusted data

<span id="195">195.</span> Double check that the buffer is as large as
specified

<span id="196">196.</span> When using functions that accept a number of
bytes to copy, such as strncpy(), be aware that if the destination
buffer size is equal to the source buffer size, it may not
NULL-terminate the string

<span id="197">197.</span> Check buffer boundaries if calling the
function in a loop and make sure there is no danger of writing past the
allocated space

<span id="198">198.</span> Truncate all input strings to a reasonable
length before passing them to the copy and concatenation functions

<span id="199">199.</span> Specifically close resources, don’t rely on
garbage collection. (e.g., connection objects, file handles, etc.)

<span id="200">200.</span> Use non-executable stacks when available

<span id="201">201.</span> Avoid the use of known vulnerable functions
(e.g., printf, strcat, strcpy etc.)

<span id="202">202.</span> Properly free allocated memory upon the
completion of functions and at all exit points

## General Coding Practices

<span id="203">203.</span> Use tested and approved managed code rather
than creating new unmanaged code for common tasks

<span id="204">204.</span> Utilize task specific built-in APIs to
conduct operating system tasks. Do not allow the application to issue
commands directly to the Operating System, especially through the use of
application initiated command shells

<span id="205">205.</span> Use checksums or hashes to verify the
integrity of interpreted code, libraries, executables, and configuration
files

<span id="206">206.</span> Utilize locking to prevent multiple
simultaneous requests or use a synchronization mechanism to prevent race
conditions

<span id="207">207.</span> Protect shared variables and resources from
inappropriate concurrent access

<span id="208">208.</span> Explicitly initialize all your variables and
other data stores, either during declaration or just before the first
usage

<span id="209">209.</span> In cases where the application must run with
elevated privileges, raise privileges as late as possible, and drop them
as soon as possible

<span id="210">210.</span> Avoid calculation errors by understanding
your programming language's underlying representation and how it
interacts with numeric calculation. Pay close attention to byte size
discrepancies, precision, signed/unsigned distinctions, truncation,
conversion and casting between types, "not-a-number" calculations, and
how your language handles numbers that are too large or too small for
its underlying representation

<span id="211">211.</span> Do not pass user supplied data to any dynamic
execution function

<span id="212">212.</span> Restrict users from generating new code or
altering existing code

<span id="213">213.</span> Review all secondary applications, third
party code and libraries to determine business necessity and validate
safe functionality, as these can introduce new vulnerabilities

<span id="214">214.</span> Implement safe updating. If the application
will utilize automatic updates, then use cryptographic signatures for
your code and ensure your download clients verify those signatures. Use
encrypted channels to transfer the code from the host server