*This article is for the OWASP Top 10 2004*

## Description

Authentication and session management includes all aspects of handling
user authentication and managing active sessions. Authentication is a
critical aspect of this process, but even solid authentication
mechanisms can be undermined by flawed credential management functions,
including password change, forgot my password, remember my password,
account update, and other related functions. Because “walk by” attacks
are likely for many web applications, all account management functions
should require reauthentication even if the user has a valid session id.

User authentication on the web typically involves the use of a userid
and password. Stronger methods of authentication are commercially
available such as software and hardware based cryptographic tokens or
biometrics, but such mechanisms are cost prohibitive for most web
applications. A wide array of account and session management flaws can
result in the compromise of user or system administration accounts.
Development teams frequently underestimate the complexity of designing
an authentication and session management scheme that adequately protects
credentials in all aspects of the site. Web applications must establish
sessions to keep track of the stream of requests from each user. HTTP
does not provide this capability, so web applications must create it
themselves. Frequently, the web application environment provides a
session capability, but many developers prefer to create their own
session tokens. In either case, if the session tokens are not properly
protected, an attacker can hijack an active session and assume the
identity of a user. Creating a scheme to create strong session tokens
and protect them throughout their lifecycle has proven elusive for many
developers. Unless all authentication credentials and session
identifiers are protected with SSL at all times and protected against
disclosure from other flaws, such as cross site scripting, an attacker
can hijack a user’s session and assume their identity.

## Environments Affected

All known web servers, application servers, and web application
environments are susceptible to broken authentication and session
management issues.

## Examples and References

  - OWASP Guide to Building Secure Web Applications and Web Services,
    Chapter 6: Authentication and Chapter 7: [Session
    Management](Session_Management "wikilink")
  - White paper on the Session Fixation Vulnerability in Web-based
    Applications: <http://www.acros.si/papers/session_fixation.pdf>
  - White paper on Password Recovery for Web-based Applications -
    <http://fishbowl.pastiche.org/archives/docs/PasswordRecovery.pdf>

A3.4 How to Determine If You Are Vulnerable

Both code review and penetration testing can be used to diagnose
authentication and session management problems. Carefully review each
aspect of your authentication mechanisms to ensure that user’s
credentials are protected at all times, while they are at rest (e.g., on
disk), and while they are in transit (e.g., during login). Review every
available mechanism for changing a user’s credentials to ensure that
only an authorized user can change them. Review your session management
mechanism to ensure that session identifiers are always protected and
are used in such a way as to minimize the likelihood of accidental or
hostile exposure.

## How to Protect Yourself

Careful and proper use of custom or off the shelf authentication and
session management mechanisms should significantly reduce the likelihood
of a problem in this area. Defining and documenting your site’s policy
with respect to securely managing users credentials is a good first
step. Ensuring that your implementation consistently enforces this
policy is key to having a secure and robust authentication and session
management mechanism. Some critical areas include:

  - **Password Strength** - passwords should have restrictions that
    require a minimum size and complexity for the password. Complexity
    typically requires the use of minimum combinations of alphabetic,
    numeric, and/or non-alphanumeric characters in a user’s password
    (e.g., at least one of each). Users should be required to change
    their password periodically. Users should be prevented from reusing
    previous passwords.
  - **Password Use** - Users should be restricted to a defined number of
    login attempts per unit of time and repeated failed login attempts
    should be logged. Passwords provided during failed login attempts
    should not be recorded, as this may expose a user’s password to
    whoever can gain access to this log. The system should not indicate
    whether it was the username or password that was wrong if a login
    attempt fails. Users should be informed of the date/time of their
    last successful login and the number of failed access attempts to
    their account since that time.
  - **Password Change Controls** - A single password change mechanism
    should be used wherever users are allowed to change a password,
    regardless of the situation. Users should always be required to
    provide both their old and new password when changing their password
    (like all account information). If forgotten passwords are emailed
    to users, the system should require the user to reauthenticate
    whenever the user is changing their e-mail address, otherwise an
    attacker who temporarily has access to their session (e.g., by
    walking up to their computer while they are logged in) can simply
    change their e-mail address and request a ‘forgotten’ password be
    mailed to them.
  - **Password Storage** - All passwords must be stored in either hashed
    or encrypted form to protect them from exposure, regardless of where
    they are stored. Hashed form is preferred since it is not
    reversible. Encryption should be used when the plaintext password is
    needed, such as when using the password to login to another system.
    Passwords should never be hardcoded in any source code. Decryption
    keys must be strongly protected to ensure that they cannot be
    grabbed and used to decrypt the password file.
  - **Protecting Credentials in Transit** - The only effective technique
    is to encrypt the entire login transaction using something like SSL.
    Simple transformations of the password such as hashing it on the
    client prior to transmission provide little protection as the hashed
    version can simply be intercepted and retransmitted even though the
    actual plaintext password might not be known.
  - **Session ID Protection** – Ideally, a user’s entire session should
    be protected via SSL. If this is done, then the session ID (e.g.,
    session cookie) cannot be grabbed off the network, which is the
    biggest risk of exposure for a session ID. If SSL is not viable for
    performance or other reasons then session IDs themselves must be
    protected in other ways. First, they should never be included in the
    URL as they can be cached by the browser, sent in the referrer
    header, or accidentally forwarded to a ‘friend’. Session IDs should
    be long, complicated, random numbers that cannot be easily guessed.
    Session IDs can also be changed frequently during a session to
    reduce how long a session ID is valid. Session IDs must be changed
    when switching to SSL, authenticating, or other major transitions.
    Session IDs chosen by a user should never be accepted.
  - **Account Lists** - Systems should be designed to avoid allowing
    users to gain access to a list of the account names on the site. If
    lists of users must be presented, it is recommended that some form
    of pseudonym (screen name) that maps to the actual account be listed
    instead. That way, the pseudonym can’t be used during a login
    attempt or some other hack that goes after a user’s account.
  - **Browser Caching** – Authentication and session data should never
    be submitted as part of a GET, POST should always be used instead.
    Authentication pages should be marked with all varieties of the no
    cache tag to prevent someone from using the back button in a user’s
    browser to backup to the login page and resubmit the previously
    typed in credentials. Many browsers now support the
    autocomplete=false flag to prevent storing of credentials in
    autocomplete caches.
  - **Trust Relationships** – Your site architecture should avoid
    implicit trust between components whenever possible. Each component
    should authenticate itself to any other component it is interacting
    with unless there is a strong reason not to (such as performance or
    lack of a usable mechanism). If trust relationships are required,
    strong procedural and architecture mechanisms should be in place to
    ensure that such trust cannot be abused as the site architecture
    evolves over time.

__NOEDITSECTION__

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")