`    <td ``>`

Consider anonymous external attackers, as well as users with their own
accounts, who may attempt to steal accounts from others. Also consider
insiders wanting to disguise their actions.

</td>

`    <td ``>`

Attacker uses leaks or flaws in the authentication or session management
functions (e.g., exposed accounts, passwords, session IDs) to
impersonate users.

</td>

`    <td colspan=2  ``>`

Developers frequently build custom authentication and session management
schemes, but building these correctly is hard. As a result, these custom
schemes frequently have flaws in areas such as logout, password
management, timeouts, remember me, secret question, account update, etc.
Finding such flaws can sometimes be difficult, as each implementation is
unique.

</td>

`    <td ``>`

Such flaws may allow some or even <u>all</u> accounts to be attacked.
Once successful, the attacker can do anything the victim could do.
Privileged accounts are frequently targeted.

</td>

`    <td ``>`

Consider the business value of the affected data or application
functions.

Also consider the business impact of public exposure of the
vulnerability.

</td>

Are session management assets like user credentials and session IDs
properly protected? You may be vulnerable if:

1.  User authentication credentials aren’t protected when stored using
    hashing or encryption. See A6.
2.  Credentials can be guessed or overwritten through weak account
    management functions (e.g., account creation, change password,
    recover password, weak session IDs).
3.  Session IDs are exposed in the URL (e.g., URL rewriting).
4.  Session IDs are vulnerable to [session
    fixation](https://www.owasp.org/index.php/Session_fixation) attacks.
5.  Session IDs don’t timeout, or user sessions or authentication
    tokens, particularly single sign-on (SSO) tokens, aren’t properly
    invalidated during logout.
6.  Session IDs aren’t rotated after successful login.
7.  Passwords, session IDs, and other credentials are sent over
    unencrypted connections. See A6.

See the [ASVS](https://www.owasp.org/index.php/ASVS) requirement areas
V2 and V3 for more details.

The primary recommendation for an organization is to make available to
developers:

1.  **A single set of strong authentication and session management
    controls.** Such controls should strive to:
    1.  meet all the authentication and session management requirements
        defined in OWASP’s [Application Security Verification
        Standard](https://www.owasp.org/index.php/ASVS) (ASVS) areas V2
        (Authentication) and V3 (Session Management).
    2.  have a simple interface for developers. Consider the [ESAPI
        Authenticator and User
        APIs](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Authenticator.html)
        as good examples to emulate, use, or build upon.
2.  Strong efforts should also be made to avoid XSS flaws which can be
    used to steal session IDs. See A3.

**Scenario \#1:** Airline reservations application supports URL
rewriting, putting session IDs in the URL:
http://example.com/sale/saleitems<span style="color: red;">

  - jsessionid=2P0OC2JSNDLPSKHCJUN2JV</span>

?dest=Hawaii  An authenticated user of the site wants to let his friends
know about the sale. He e-mails the above link without knowing he is
also giving away his session ID. When his friends use the link they will
use his session and credit card.

**Scenario \#2:** Application’s timeouts aren’t set properly. User uses
a public computer to access site. Instead of selecting “logout” the user
simply closes the browser tab and walks away. Attacker uses the same
browser an hour later, and that browser is still authenticated.

**Scenario \#3:** Insider or external attacker gains access to the
system’s password database. User passwords are not properly hashed,
exposing every users’ password to the attacker.

For a more complete set of requirements and problems to avoid in this
area, see the [ASVS requirements areas for Authentication (V2) and
Session Management (V3)](https://www.owasp.org/index.php/ASVS).

  - [OWASP Authentication Cheat
    Sheet](https://www.owasp.org/index.php/Authentication_Cheat_Sheet)
  - [OWASP Forgot Password Cheat
    Sheet](https://www.owasp.org/index.php/Forgot_Password_Cheat_Sheet)
  - [OWASP Session Management Cheat
    Sheet](https://www.owasp.org/index.php/Session_Management_Cheat_Sheet)
  - [OWASP Development Guide: Chapter on
    Authentication](https://www.owasp.org/index.php/Forgot_Password_Cheat_Sheet)
  - [OWASP Testing Guide: Chapter on
    Authentication](https://www.owasp.org/index.php/Testing_for_authentication)

<!-- end list -->

  - [CWE Entry 287 on Improper
    Authentication](http://cwe.mitre.org/data/definitions/287.html)
  - [CWE Entry 384 on Session
    Fixation](http://cwe.mitre.org/data/definitions/384.html)