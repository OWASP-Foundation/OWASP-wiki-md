## Brief Summary

Today's web applications typically run on popular open source or
commercial software that is installed on servers and requires
configuration or customization by the server administrator. In addition,
most of today's hardware appliances, i.e., network routers and database
servers, offer web-based configuration or administrative interfaces.

Often these applications are not properly configured and the default
credentials provided for initial authentication and configuration are
never updated. In addition, it is typical to find generic accounts, left
over from testing or administration, that use common usernames and
passwords and are left enabled in the application and its
infrastructure.

These default username and password combinations are widely known by
penetration testers and malicious attackers, who can use them to gain
access to various types of custom, open source, or commercial
applications.
In addition, weak password policy enforcements seen in many applications
allow users to sign up using easy to guess usernames and passwords, and
may also not allow password changes to be undertaken.

## Description of the Issue

The root cause of this problem can be identified as:

  - Inexperienced IT personnel, who are unaware of the importance of
    changing default passwords on installed infrastructure components.
  - Programmers who leave backdoors to easily access and test their
    application and later forget to remove them.
  - Application administrators and users that choose an easy username
    and password for themselves
  - Applications with built-in, non-removable default accounts with a
    pre-set username and password.
  - Applications which leak information as to the validity of usernames
    during either authentication attempts, password resets, or account
    signup.

An additional problem stems from the use of blank passwords, which are
simply the result of a lack of security awareness or a desire to
simplify administration.

## Black Box testing and example

In Blackbox testing the tester knows nothing about the application, its
underlying infrastructure, and any username or password policies. In
reality this is often not the case, and some information about the
application is known. If this is the case, simply skip the steps that
refer to obtaining information you already have.

When testing a known application interface, for example a Cisco router
web interface or a Weblogic administrator portal, check that the known
usernames and passwords for these devices do not result in successful
authentication. Common credentials for many systems can be found using a
search engine or by using one of the sites listed in the Further Reading
section.

When facing applications to which we do not have a list of default and
common user accounts, or when common accounts do not work, we can
perform manual testing.

Note that the application being tested may have an account lockout, and
multiple password guess attempts with a known username may cause the
account to be locked. If it is possible to lock the administrator
account, it may be troublesome for the system administrator to reset it.

Many applications have verbose error messages that inform the site users
as to the validity of entered usernames. This information will be
helpful when testing for default or guessable user accounts. Such
functionality can be found, for example, on the login page, password
reset and forgotten password page, and sign up page. More information on
this can be seen in the section [Testing for user
enumeration](Testing_for_user_enumeration_\(OWASP-AT-002\) "wikilink").

  - Try the following usernames - "admin", "administrator", "root",
    "system", "guest", "operator", or "super". These are popular among
    system administrators and are often used. Additionally you could try
    "qa", "test", "test1", "testing" and similar names. Attempt any
    combination of the above in both the username and the password
    fields. If the application is vulnerable to username enumeration,
    and you successfully manage to identify any of the above usernames,
    attempt passwords in a similar manner. In addition try an empty
    password or one of the following "password", "pass123",
    "password123", "admin", or "guest" with the above accounts or any
    other enumerated accounts. Further permutations of the above can
    also be attempted. If these passwords fail, it may be worth using a
    common username and password list and attempting multiple requests
    against the application. This can, of course, be scripted to save
    time.
  - Application administrative users are often named after the
    application or organization. This means if you are testing an
    application named "Obscurity", try using obscurity/obscurity or any
    other similar combination as the username and password.
  - When performing a test for a customer, attempt using names of
    contacts you have received as usernames with any common passwords.
  - Viewing the User Registration page may help determine the expected
    format and length of the application usernames and passwords. If a
    user registration page does not exist, determine if the organization
    uses a standard naming convention for user names such as their email
    address or the name before the "@" in the email.
  - Attempt using all the above usernames with blank passwords.
  - Review the page source and javascript either through a proxy or by
    viewing the source. Look for any references to users and passwords
    in the source. For example "If username='admin' then
    starturl=/admin.asp else /index.asp" (for a successful login vs a
    failed login). Also, if you have a valid account, then login and
    view every request and response for a valid login vs an invalid
    login, such as additional hidden parameters, interesting GET request
    (login=yes), etc.
  - Look for account names and passwords written in comments in the
    source code. Also look in backup directories, etc for source code
    that may contain comments of interest.
  - Try to extrapolate from the application how usernames are generated.
    For example, can a user create their own username or does the system
    create an account for the user based on some personal information or
    a predictable sequence? If the application does create its own
    accounts in a predictable sequence, such as user7811, try fuzzing
    all possible accounts recursively. If you can identify a different
    response from the application when using a valid username and a
    wrong password, then you can try a brute force attack on the valid
    username (or quickly try any of the identified common passwords
    above or in the reference section).
  - If the application creates its own passwords for new users, whether
    or not the username is created by the application or by the user,
    then try to determine if the password is predictable. Try to create
    many new accounts in quick succession to compare and determine if
    the passwords are predictable. If predictable, then try to correlate
    these with the usernames, or any enumerated accounts, and use them
    as a basis for a brute force attack.

**Result Expected:**
Successful authentication to the application or system being tested.

## Gray Box testing and example

The following steps rely on an entirely Gray Box approach. If only some
of the information is available to you, refer to black box testing to
fill the gaps.

  - Talk to the IT personnel to determine passwords they use for
    administrative access and how administration of the application is
    undertaken.
  - Examine the password policy for the application, checking whether
    username and passwords are complex, difficult to guess, and not
    related to the application name, person name, or administrative
    names ("system").
  - Examine the user database for default names, application names, and
    easily guessed names as described in the Black Box testing section.
    Check for empty password fields.
  - Examine the code for hard coded usernames and passwords.
  - Check for configuration files that contain usernames and
    passwords.

**Result Expected:**
Successful authentication to the application or system being tested.

## References

**Whitepapers**
\* CIRT <http://www.cirt.net/passwords>

  - Government Security - Default Logins and Passwords for Networked
    Devices
    <http://www.governmentsecurity.org/articles/DefaultLoginsandPasswordsforNetworkedDevices.php>
  - Virus.org <http://www.virus.org/default-password/>

**Tools**
\* Burp Intruder: <http://portswigger.net/intruder/>

  - THC Hydra: <http://www.thc.org/thc-hydra/>
  - Brutus <http://www.hoobie.net/brutus/>