**Esimerkki** Sovelluksen istuntotunniste generoidaan liittämällä
käyttäjän tunnus sekä päivämäärä ja kellonaika, ja tästä muodostetaan
hash-arvo. Hyökkääjä pystyy helposti arvaamaan istuntotunnisteen, kun
tietää käyttäjän nimen ja kirjautumisajan. Monesti myös käytetään
heikkoja satunnaislukugeneraattoreita, joiden tuottamat satunnaisluvut
ovat ennustettavia.

**Suositus** Käytä riittävän vahvoja salasanoja sekä istuntotunnisteita.

TODO: Käännä seuraavat

Proper authentication and session management is critical to web
application security. Flaws in this area most frequently involve the
failure to protect credentials and session tokens through their
lifecycle. These flaws can lead to the hijacking of user or
administrative accounts, undermine authorization and accountability
controls, and cause privacy violations.

## Environments Affected

All web application frameworks are vulnerable to authentication and
session management flaws.

## Vulnerability

Flaws in the main authentication mechanism are not uncommon, but
weaknesses are more often introduced through ancillary authentication
functions such as logout, password management, timeout, remember me,
secret question, and account update.

## Verifying Security

The goal is to verify that the application properly authenticates users
and properly protects identities and their associated credentials.

Automated approaches: Vulnerability scanning tools have a very difficult
time detecting vulnerabilities in custom authentication and session
management schemes. Static analysis tools are also not likely to detect
authentication and session management problems in custom code.

Manual approaches: Code review and testing, especially in combination,
are quite effective at verifying that the authentication, session
management, and ancillary functions are all implemented properly.

## Protection

Authentication relies on secure communication and credential storage.
First ensure that SSL is the only option for all authenticated parts of
the application (see A9 Ã¢ÂÂ Insecure Communications) and that all
credentials are stored in hashed or encrypted form (see A8 Ã¢ÂÂ
Insecure Cryptographic Storage).

Preventing authentication flaws takes careful planning. Among the most
important considerations are:

  - **Only use the inbuilt session management mechanism.** Do not write
    or use secondary session handlers under any circumstances.
  - **Do not accept new, preset or invalid session identifiers** from
    the URL or in the request. This is called a session fixation attack.
  - '''Limit or rid your code of custom cookies for authentication or
    session management '''purposes, such as "remember me" type
    functionality or home grown single-sign on functionality. This does
    not apply to robust, well proven SSO or federated authentication
    solutions.
  - **Use a single authentication mechanism** with appropriate strength
    and number of factors. Make sure that this mechanism is not easily
    subjected to spoofing or replay attacks. Do not make this mechanism
    overly complex, which then may become subject to its own attack.
  - **Do not allow the login process to start from an unencrypted
    page.** Always start the login process from a second, encrypted page
    with a fresh or new session token to prevent credential or session
    stealing, phishing attacks and session fixation attacks.
  - Consider **regenerating a new session upon successful
    authentication** or privilege level change.
  - **Ensure that every page has a logout link.** Logout should destroy
    all server side session state and client side cookies. Consider
    human factors: do not ask for confirmation as users will end up just
    closing the tab or window rather than logging out successfully.
  - **Use a timeout period** that automatically logs out an inactive
    session as per the value of the data being protected (shorter is
    always better).
  - **Use only strong ancillary authentication functions** (questions
    and answers, password reset) as these are credentials in the same
    way usernames and passwords or tokens are credentials. Apply a
    one-One way hash to answers to prevent disclosure attacks.
  - **Do not expose any session identifiers or any portion of valid
    credentials in URLs or logs (no session rewriting or storing the
    userÃ¢ÂÂs password in log files)**
  - **Check the old password when the user changes to a new password**
  - **Do not rely upon spoofable credentials as the sole form of
    authentication**, such as IP addresses or address range masks, DNS
    or reverse DNS lookups, referrer headers or similar''' '''
  - **Be careful of sending secrets to registered e-mail addresses**
    (see RSNAKE02 in the references) as a mechanism for password resets.
    Use limited time only random numbers to reset access and send a
    follow up e-mail as soon as the password has been reset. Be careful
    of allowing self-registered users changing their e-mail address -
    send a message to the previous e-mail address before enacting the
    change

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6145>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6229>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6528>

## Related Articles

  - [Guide to Authentication](Guide_to_Authentication "wikilink")
  - [Testing for authentication](Testing_for_authentication "wikilink")
  - [Reviewing Code for
    Authentication](Reviewing_Code_for_Authentication "wikilink")

## References

  - CWE: CWE-287 (Authentication Issues), CWE-522 (Insufficiently
    Protected Credentials), CWE-301 (Reflection attack in an
    authentication protocol), others.
  - WASC Threat Classification:
      - <http://www.webappsec.org/projects/threat/classes/insufficient_authentication.shtml>
      - <http://www.webappsec.org/projects/threat/classes/credential_session_prediction.shtml>
      - <http://www.webappsec.org/projects/threat/classes/session_fixation.shtml>
  - RSNAKE01 -
    <http://ha.ckers.org/blog/20070122/ip-trust-relationships-xss-and-you>
  - RSNAKE02 -
    <http://ha.ckers.org/blog/20061109/email-as-half-factor-authentication>