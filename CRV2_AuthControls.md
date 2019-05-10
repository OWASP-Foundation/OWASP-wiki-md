# This is a draft version

## Overview

Authentication is the process of verifying that an individual or an
entity is who it claims to be. Authentication is commonly performed by
submitting a user name or ID and one or more items of private
information that only a given user should know.

## Description

Authentication is important as it is the gateway to the functionality
you are wishing to protect. Once a user is authenticated their requests
will be authorized to perform some level of interaction with your
application that non-authenticated users will be barred from. You cannot
control how users manage their authentication information or tokens, but
you can ensure there is now way to perform application functions without
proper authentication occurring.

There are many forms of authentication with passwords being the most
common. Other forms include client certificates, biometrics, one time
passwords over SMS or special devices, or authentication frameworks such
as Open Authorization (OAUTH) or Single Sign On (SSO).

Typically authentication is done once, when the user logs into a
website, and successful authentication results in a web session being
setup for the user (see Session Management). Further (and stronger)
authentication can be subsequently requested if the user attempts to
perform a high risk function, for example a bank user could be asked to
confirm an 6 digit number that was sent to their registered phone number
before allowing money to be transferred.

Authentication is just as important within a companies firewall as
outside it. Attackers should not be able to run free on a companies
internal applications simply because they found a way in through a
firewall. Also separation of privilege (or duties) means someone working
in accounts should not be able to modify code in a repository, or
application managers should not be able to edit the payroll
spreadsheets.

## What to Review

When reviewing code modules which perform authentication functions, some
common issues to look out for include:

  - Ensure the login page is only available over TLS. Some sites leave
    the login page has HTTP, but make the form submission URL HTTPS so
    that the users username and password are encrypted when sent to the
    server. However if the login page is not secured, a risk exists for
    a man-in-the-middle to modify the form submission URL to an HTTP
    URL, and when the user enters their username & password they are
    sent in the clear.
  - Make sure your usernames/userids are case insensitive. Many sites
    use email addresses for usernames and email addresses are already
    case insensitive. Regardless, it would be very strange for user
    'smith' and user 'Smith' to be different users. Could result in
    serious confusion.
  - Ensure failure messages for invalid usernames or passwords do not
    leak information. If the error message indicates the username was
    valid, but the password was wrong, then attackers will know that
    username exists. If the password was wrong, do not indicate how it
    was wrong.
  - Make sure that every character the user types in is actually
    included in the password.
  - Do not log invalid passwords. Many times an e-mail address is used
    as the username, and those users will have a few passwords memorized
    but may forget which one they used on your web site. The first time
    they may use a password that in invalid for your site, but valid for
    many other sites that this user (identified by the username). If you
    log that username and password combination, and that log leaks out,
    this low level compromise on your site could negatively affect many
    other sites.
  - Longer passwords provide a greater combination of characters and
    consequently make it more difficult for an attacker to guess.
    Minimum length of the passwords should be enforced by the
    application. Passwords shorter than 10 characters are considered to
    be weak (\[1\]). Passphrases should be encouraged. For more on
    password lengths see the OWASP Authentication Cheat Sheet.
  - To prevent brute force attacks, implement temporary account lockouts
    or rate limit login responses. If a user fails to provide the
    correct username and password 5 times, then lock the account for X
    minutes, or implement logic where login responses take an extra 10
    seconds. Be careful though, this could leak the fact that the
    username is valid to attackers continually trying random usernames,
    so as an extra measure, consider implementing the same logic for
    invalid usernames.
  - For internal systems, consider forcing the users to change passwords
    after a set period of time, and store a reference (e.g. hash) of the
    last 5 or more passwords to ensure the user is not simply re-using
    their old password.
  - Password complexity should be enforced by making users choose
    password strings that include various types of characters (e.g.
    upper- and lower-case letters, numbers, punctuation, etc). Ideally,
    the application would indicate to the user as they type in their new
    password how much of the complexity policy their new password meets.
    For more on password complexity see the OWASP Authentication Cheat
    Sheet.
  - It is common for an application to have a mechanism that provides a
    means for a user to gain access to their account in the event they
    forget their password. This is an example of web site functionality
    this is invoked by unauthenticated users (as they have not provided
    their password). Ensure interfaces like this are protected from
    misuse, if asking for password reminder results in an e-mail or SMS
    being sent to the registered user, do not allow the password reset
    feature to be used to spam the user by attackers constantly entering
    the username into this form. Please see Forgot Password Cheat Sheet
    for details on this feature.
  - It is critical for a application to store a password using the right
    cryptographic technique. Please see Password Storage Cheat Sheet for
    details on this feature.
  - For high risk functions, e.g. banking transactions, user profile
    updates, etc, utilize multi-factor authentication (MFA). This also
    mitigates against CSRF and session hijacking attacks. MFA is using
    more than one authentication factor to logon or process a
    transaction:
      - Something you know (account details or passwords)
      - Something you have (tokens or mobile phones)
      - Something you are (biometrics)
  - If the client machine is in a controlled environment utilize SSL
    Client Authentication, also known as two-way SSL authentication,
    which consists of both browser and server sending their respective
    SSL certificates during the TLS handshake process. This provides
    stronger authentication as the server administrator can create and
    issue client certificates, allowing the server to only trust login
    requests from machines that have this client SSL certificate
    installed. Secure transmission of the client certificate is
    important.

## Languages

## References

  - <https://www.owasp.org/index.php/Authentication_Cheat_Sheet>
  - <http://csrc.nist.gov/publications/nistpubs/800-132/nist-sp800-132.pdf>
  - <http://www.codeproject.com/Articles/326574/An-Introduction-to-Mutual-SSL-Authentication>
  - <https://www.owasp.org/index.php/Session_Management_Cheat_Sheet>