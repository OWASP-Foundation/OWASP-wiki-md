__TOC__

## Introduction

“Who are you?” Authentication is the process where an entity proves the
identity of another entity, typically through credentials, such as a
username and password.

Depending on your requirements, there are several available
authentication mechanisms to choose from. If they are not correctly
chosen and implemented, the authentication mechanism can expose
vulnerabilities that attackers can exploit to gain access to your
system.

The storage of passwords and user credentials is an issue from a defense
in depth approach, but also from a compliance standpoint. The following
section also discusses password storage and what to review for.

The following discusses aspects of source code relating to weak
authentication functionality. This could be due to flawed implementation
or broken business logic: Authentication is a key line of defence in
protecting non-public data, sensitive functionality.

### Weak Passwords and Password Functionality

Password strength should be enforced upon a user setting/selecting a
password. Passwords should be complex in composition. Such checks should
be done on the backend/server side of the application upon an attempt to
submit a new password.

#### Bad Example

Simply checking that a password is not NULL is not sufficient:

`String password = request.getParameter("Password");`
`if (password == Null) `
`   {throw InvalidPasswordException()`
`   }`

#### Good Example

Passwords should be checked for the following composition or a variance
of such

  - at least: 1 uppercase character (A-Z)
  - at least: 1 lowercase character (a-z)
  - at least: 1 digit (0-9)
  - at least one special character (\!"£$%&...)
  - a defined minimum length (8 chars)
  - a defined maximum length (as with all external input)
  - no contiguous characters (123abcd)
  - not more than 2 identical characters in a row (1111)

Such rules should be looked for in code and used as soon as the http
request is received. The rules can be complex RegEx expressions or
logical code statements:

`if password.RegEx([a-z])`
`   and password.RegEx([A-Z])`
`   and password.RegEx([0-9])`
`   and password.RegEx({8-30})`
`   and password.RexEX([!"£$%^&*()])`
`   return true;`
`else`
`return false;`

A regular expression statement for code above:

`(?=^.{8,30}$)(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[!@#$%^&*()_+}{"":;'?/>.<,]).*$`

### **.NET Authentication controls**

In the .NET, there is Authentication tags in the configuration file.

The \<**authentication**\> element configures the authentication mode
that your applications use.

\<**authentication**\>

The appropriate authentication mode depends on how your application or
Web service has been designed. The default Machine.config setting
applies a secure Windows authentication default as shown below.

''' authentication Attributes:mode="\[Windows|Forms|Passport|None\]" '''

<authentication mode="Windows" />

''' Forms Authentication Guidelines ''' To use Forms authentication, set
mode=“Forms” on the <authentication> element. Next, configure Forms
authentication using the child <forms> element. The following fragment
shows a secure <forms> authentication element configuration:

<authentication mode="Forms">
<forms loginUrl="Restricted\login.aspx"     Login page in an SSL protected folder
       protection="All"                      Privacy and integrity
       requireSSL="true"                     Prevents cookie being sent over http
       timeout="10"                          Limited session lifetime
       name="AppNameCookie"                  Unique per-application name
       path="/FormsAuth"                     and path
       slidingExpiration="true" >`            Sliding session lifetime`
</forms>
</authentication>

Use the following recommendations to improve Forms authentication
security:

  - Partition your Web site.
  - Set protection=“All”.
  - Use small cookie time-out values.
  - Consider using a fixed expiration period.
  - Use SSL with Forms authentication.
  - If you do not use SSL, set slidingExpiration = “false”.
  - Do not use the <credentials> element on production servers.
  - Configure the <machineKey> element.
  - Use unique cookie names and paths.

For classic ASP pages, authentication is usually performed manually by
including the user information in session variables after validation
against a DB, so you can look for something like:

`Session ("UserId") = UserName`
`Session ("Roles") = UserRoles`

#### Cookieless Forms authentication

Authentication tickets in forms are by default stored in cookies
(Authentication tickets are used to remember if the user has
authenticated to the system), such as a unique ID in the cookie of the
HTTP header. Other methods to preserve authentication in the stateless
HTTP protocol. The directive cookieless can define thet type of
authentication ticket to be used.

Types of cookieless values on the <forms> element:

  - UseCookies – specifies that cookie tickets will always be used.
  - UseUri – indicates that cookie tickets will never be used.
  - AutoDetect – cookie tickets are not used if device does not support
    such; if the device profile supports cookies, a probing function is
    used to determine if cookies are enabled.
  - UseDeviceProfile – the default setting if not defined; uses
    cookie-based authentication tickets only if the device profile
    supports cookies. A probing function is not used.

cookieless="UseUri" : What may be found in the <forms> element above

When we talk about probing we are refering to the user agent directive
in the HTTP header. This can inform ASP.NET is cookies are supported.

## Password Storage Strategy

The storage of passwords is also of concern, as unauthorized access to
an application may give rise to an attacker to access the area where
passwords are stored.

Passwords should be stored using a one-way hash algorithm. One way
functions (SHA-256 SHA-1 MD5, ..;) are also known as Hashing functions.
Once passwords are persisted, there is no reason why they should be
human-readable. The functionality for authentication performs a hash of
the password passed by the user and compares it to the stored hash. If
the passwords are identical, the hashes are equal.

Storing a hash of a password, which cannot be reversed, makes it more
difficult to recover the plain text passwords. It also ensures that
administration staff for an application does not have access to other
users’ passwords, and hence helps mitigate the internal threat vector.

Example code in Java implementing SHA-1 hashing:

`import java.security.MessageDigest;`
`public byte[] getHash(String password) throws NoSuchAlgorithmException {`
`      MessageDigest digest = MessageDigest.getInstance("SHA-1");`
`      digest.reset();`
`      byte[] input = digest.digest(password.getBytes("UTF-8"));`

**Salting:** Storing simply hashed passwords has its issues, such as the
possibility to identify two identical passwords (identical hashes) and
also the [birthday
attack](http://en.wikipedia.org/wiki/Birthday_paradox). A countermeasure
for such issues is to introduce a salt. A salt is a random number of a
fixed length. This salt must be different for each stored entry. It must
be stored as clear text next to the hashed password:

`import java.security.MessageDigest;`
`public byte[] getHash(String password, byte[] salt) throws NoSuchAlgorithmException {`
`      MessageDigest digest = MessageDigest.getInstance("SHA-256");`
`      digest.reset();`
`      digest.update(salt);`
`      return digest.digest(password.getBytes("UTF-8"));`
`}`

### Vulnerabilities related to authentication

There are many issues relating to authentication which utilise form
fields. Inadequate field validation can give rise to the following
issues:

  - [Reviewing Code for SQL
    Injection](Reviewing_Code_for_SQL_Injection "wikilink")

SQL injection can be used to bypass authentication functionality and
even add a malicious user to a system for future use.

  - [Reviewing Code for Data
    Validation](Reviewing_Code_for_Data_Validation "wikilink")

Data validation of all external input must be performed. This also goes
for authentication fields.

  - [Reviewing Code for Cross-site
    scripting](Reviewing_Code_for_Cross-site_scripting "wikilink")

Cross site scripting can be used on the authentication page to perform
identity theft, Phishing, and session hijacking attacks.

  - [Reviewing Code for Error
    Handling](Reviewing_Code_for_Error_Handling "wikilink")

Bad/weak error handling can be used to establish the internal workings
of the authentication functionality such as giving insight into the
database structure, insight into valid and invalid user IDs, etc.

  - [Hashing with Java](Hashing_Java "wikilink")

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")