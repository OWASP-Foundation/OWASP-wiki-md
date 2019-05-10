`   <td colspan=2 ``>`

Attackers have access to hundreds of millions of valid username and
password combinations for credential stuffing, default administrative
account lists, automated brute force, and dictionary attack tools.
Session management attacks are well understood, particularly in relation
to unexpired session tokens.

</td>

`   <td colspan=2 ``>`

The prevalence of broken authentication is widespread due to the design
and implementation of most identity and access controls. Session
management is the bedrock of authentication and access controls, and is
present in all stateful applications.
Attackers can detect broken authentication using manual means and
exploit them using automated tools with password lists and dictionary
attacks.

</td>

`   <td colspan=2 ``>`

Attackers have to gain access to only a few accounts, or just one admin
account to compromise the system. Depending on the domain of the
application, this may allow money laundering, social security fraud, and
identity theft, or disclose legally protected highly sensitive
information.

</td>

Confirmation of the user's identity, authentication, and session
management are critical to protect against authentication-related
attacks. There may be authentication weaknesses if the application:

  - Permits automated attacks such as <u>[credential
    stuffing](Credential_stuffing "wikilink")</u>, where the attacker
    has a list of valid usernames and passwords.
  - Permits brute force or other automated attacks.
  - Permits default, weak, or well-known passwords, such as "Password1"
    or "admin/admin“.
  - Uses weak or ineffective credential recovery and forgot-password
    processes, such as "knowledge-based answers", which cannot be made
    safe.
  - Uses plain text, encrypted, or weakly hashed passwords (see
    <u><b>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</b></u>).
  - Has missing or ineffective multi-factor authentication.
  - Exposes Session IDs in the URL (e.g., URL rewriting).
  - Does not rotate Session IDs after successful login.
  - Does not properly invalidate Session IDs. User sessions or
    authentication tokens (particularly single sign-on (SSO) tokens)
    aren't properly invalidated during logout or a period of inactivity.

<!-- end list -->

  - Where possible, implement multi-factor authentication to prevent
    automated, credential stuffing, brute force, and stolen credential
    re-use attacks.
  - Do not ship or deploy with any default credentials, particularly for
    admin users.
  - Implement weak-password checks, such as testing new or changed
    passwords against a list of the <u>[top 10000 worst
    passwords](https://github.com/danielmiessler/SecLists/tree/master/Passwords)</u>.
  - Align password length, complexity and rotation policies with
    <u>[NIST 800-63 B's guidelines in section 5.1.1 for Memorized
    Secrets](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecret)</u>
    or other modern, evidence based password policies.
  - Ensure registration, credential recovery, and API pathways are
    hardened against account enumeration attacks by using the same
    messages for all outcomes.
  - Limit or increasingly delay failed login attempts. Log all failures
    and alert administrators when credential stuffing, brute force, or
    other attacks are detected.
  - Use a server-side, secure, built-in session manager that generates a
    new random session ID with high entropy after login. Session IDs
    should not be in the URL, be securely stored and invalidated after
    logout, idle, and absolute timeouts.

<b>Scenario \#1</b>: <u>[Credential
stuffing](Credential_stuffing "wikilink")</u>, the use of <u>[lists of
known passwords](https://github.com/danielmiessler/SecLists)</u>, is a
common attack. If an application does not implement automated threat or
credential stuffing protections, the application can be used as a
password oracle to determine if the credentials are valid.

<b>Scenario \#2</b>: Most authentication attacks occur due to the
continued use of passwords as a sole factor. Once considered best
practices, password rotation and complexity requirements are viewed as
encouraging users to use, and reuse, weak passwords. Organizations are
recommended to stop these practices per NIST 800-63 and use multi-factor
authentication.

<b>Scenario \#3</b>: Application session timeouts aren't set properly. A
user uses a public computer to access an application. Instead of
selecting “logout” the user simply closes the browser tab and walks
away. An attacker uses the same browser an hour later, and the user is
still authenticated.

  - <u>[OWASP Proactive Controls: Implement Identity and Authentication
    Controls](OWASP_Proactive_Controls#5:_Implement_Identity_and_Authentication_Controls "wikilink")</u>
  - <u>[OWASP Application Security Verification Standard: V2
    Authentication](:Category:OWASP_Application_Security_Verification_Standard_Project#tab=Home "wikilink")</u>
  - <u>[OWASP Application Security Verification Standard: V3 Session
    Management](:Category:OWASP_Application_Security_Verification_Standard_Project#tab=Home "wikilink")</u>
  - <u>[OWASP Testing Guide:
    Identity](Testing_Identity_Management "wikilink")</u>,
    <u>[Authentication](Testing_for_authentication "wikilink")</u>
  - <u>[OWASP Cheat Sheet:
    Authentication](Authentication_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Credential
    Stuffing](Credential_Stuffing_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Forgot
    Password](Forgot_Password_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Session
    Management](Session_Management_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Automated Threats
    Handbook](OWASP_Automated_Threats_to_Web_Applications "wikilink")</u>

<!-- end list -->

  - <u>[NIST 800-63b: 5.1.1 Memorized
    Secrets](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecret)</u>
  - <u>[CWE-287: Improper
    Authentication](https://cwe.mitre.org/data/definitions/287.html)</u>
  - <u>[CWE-384: Session
    Fixation](https://cwe.mitre.org/data/definitions/384.html)</u>