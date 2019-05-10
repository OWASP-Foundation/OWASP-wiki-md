`    <td ``>Consider anonymous external attackers, as well as users with their own accounts, who may attempt to steal accounts from others. Also consider insiders wanting to disguise their actions.`

</td>

`    <td ``>Attacker uses leaks or flaws in the authentication or session management functions (e.g., exposed accounts, passwords, session IDs) to impersonate users.`

</td>

`    <td colspan=2  ``>Developers frequently build custom authentication and session management schemes, but building these correctly is hard. As a result, these custom schemes frequently have flaws in areas such as logout, password management, timeouts, remember me, secret question, account update, etc. Finding such flaws can sometimes be difficult, as each implementation is unique.`

</td>

`    <td ``>Such flaws may allow some or even all accounts to be attacked. Once successful, the attacker can do anything the victim could do. Privileged accounts are frequently targeted.`

</td>

`    <td ``>Consider the business value of the affected data or application functions.`

`Also consider the business impact of public exposure of the vulnerability.`

</td>

The primary assets to protect are credentials and session IDs.

1.  Are credentials always protected when stored using hashing or
    encryption? [See A7](Top_10_2010-A7 "wikilink").
2.  Can credentials be guessed or overwritten through weak account
    management functions (e.g., account creation, change password,
    recover password, weak session IDs)?
3.  Are session IDs exposed in the URL (e.g., URL rewriting)?
4.  Are session IDs vulnerable to session fixation attacks?
5.  Do session IDs timeout and can users log out?
6.  Are session IDs rotated after successful login?
7.  Are passwords, session IDs, and other credentials sent only over TLS
    connections? [See A9](Top_10_2010-A9 "wikilink").

See the [ASVS](http://www.owasp.org/index.php/ASVS#tab=Downloads)
requirement areas V2 and V3 for more details.  The primary
recommendation for an organization is to make available to developers:

1.  A single set of strong authentication and session management
    controls. Such controls should strive to:
    1.  meet all the authentication and session management requirements
        defined in OWASP’s [Application Security Verification
        Standard](http://www.owasp.org/index.php/ASVS#tab=Downloads)
        (ASVS) areas V2 (Authentication) and V3 (Session Management).
    2.  have a simple interface for developers. Consider the [ESAPI
        Authenticator and User
        APIs](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Authenticator.html)
        as good examples to emulate, use, or build upon.
2.  Strong efforts should also be made to avoid XSS flaws which can be
    used to steal session IDs. [See A2](Top_10_2010-A2 "wikilink").

<u>Scenario \#1</u>: Airline reservations application supports URL
rewriting, putting session IDs in the URL:
http://example.com/sale/saleitems;<span style="color:red;">
jsessionid=2P0OC2JDPXM0OQSNDLPSKHCJUN2JV</span>
?dest=Hawaii An authenticated user of the site wants to let his friends
know about the sale. He e-mails the above link without knowing he is
also giving away his session ID. When his friends use the link they will
use his session and credit card.

<u>Scenario \#2</u>: Application’s timeouts aren’t set properly. User
uses a public computer to access site. Instead of selecting “logout” the
user simply closes the browser tab and walks away. Attacker uses the
same browser an hour later, and that browser is still authenticated.

<u>Scenario \#3</u>: Insider or external attacker gains access to the
system’s password database. User passwords are not encrypted, exposing
every users’ password to the attacker.

For a more complete set of requirements and problems to avoid in this
area, see the [ASVS requirements areas for Authentication (V2) and
Session Management
(V3)](http://www.owasp.org/index.php/ASVS#tab=Downloads)

  - [OWASP Authentication Cheat
    Sheet](Authentication_Cheat_Sheet "wikilink")
  - [ESAPI Authenticator
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Authenticator.html)
  - [ESAPI User
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/User.html)
  - [OWASP Development Guide: Chapter on
    Authentication](Guide_to_Authentication "wikilink")
  - [OWASP Testing Guide: Chapter on
    Authentication](Testing_for_authentication "wikilink")

<!-- end list -->

  - [CWE Entry 287 on Improper
    Authentication](http://cwe.mitre.org/data/definitions/287.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")