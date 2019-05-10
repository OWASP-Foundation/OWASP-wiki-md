` `

`    <td ``>Consider who can gain access to your sensitive data and any backups of that data. This includes the data at rest, in transit, and even in your customers’ browsers. Include both external and internal threats.`

</td>

`    <td ``>`

Attackers typically don’t break crypto directly. They break something
else, such as steal keys, do man-in-the-middle attacks, or steal clear
text data off the server, while in transit, or from the user’s browser.

</td>

`    <td colspan=2  ``>`

The most common flaw is simply not encrypting sensitive data. When
crypto is employed, weak key generation and management, and weak
algorithm usage is common, particularly weak password hashing
techniques. Browser weaknesses are very common and easy to detect, but
hard to exploit on a large scale. External attackers have difficulty
detecting server side flaws due to limited access and they are also
usually hard to exploit.

</td>

`    <td ``>`

Failure frequently compromises all data that should have been protected.
Typically, this information includes sensitive data such as health
records, credentials, personal data, credit cards, etc.

</td>

`    <td ``>`

Consider the business value of the lost data and impact to your
reputation. What is your legal liability if this data is exposed? Also
consider the damage to your reputation.

</td>

The first thing you have to determine is which data is sensitive enough
to require extra protection. For example, passwords, credit card
numbers, health records, and personal information should be protected.
For all such data:

1.  Is any of this data stored in clear text long term, including
    backups of this data?
2.  Is any of this data transmitted in clear text, internally or
    externally? Internet traffic is especially dangerous.
3.  Are any old / weak cryptographic algorithms used?
4.  Are weak crypto keys generated, or is proper key management or
    rotation missing?
5.  Are any browser security directives or headers missing when
    sensitive data is provided by / sent to the browser?

And more … For a more complete set of problems to avoid, see [ASVS areas
Crypto (V7), Data Prot. (V9), and SSL
(V10)](https://www.owasp.org/index.php/ASVS).

1.  The full perils of unsafe cryptography, SSL usage, and data
    protection are well beyond the scope of the Top 10. That said, for
    all sensitive data, do all of the following, at a minimum:
2.  Considering the threats you plan to protect this data from (e.g.,
    insider attack, external user), make sure you encrypt all sensitive
    data at rest and in transit in a manner that defends against these
    threats.
3.  Don’t store sensitive data unnecessarily. Discard it as soon as
    possible. Data you don’t have can’t be stolen.
4.  Ensure strong standard algorithms and strong keys are used, and
    proper key management is in place. Consider using [FIPS 140
    validated cryptographic
    modules](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/140val-all.htm).
5.  Ensure passwords are stored with an algorithm specifically designed
    for password protection, such as
    [bcrypt](http://en.wikipedia.org/wiki/Bcrypt),
    [PBKDF2](http://en.wikipedia.org/wiki/PBKDF2), or
    [scrypt](http://en.wikipedia.org/wiki/Scrypt).
6.  Disable autocomplete on forms collecting sensitive data and disable
    caching for pages that contain sensitive data.

**Scenario \#1:** An application encrypts credit card numbers in a
database using automatic database encryption. However, this means it
also decrypts this data automatically when retrieved, allowing an SQL
injection flaw to retrieve credit card numbers in clear text. The system
should have encrypted the credit card numbers using a public key, and
only allowed back-end applications to decrypt them with the private key.

**Scenario \#2:** A site simply doesn’t use SSL for all authenticated
pages. Attacker simply monitors network traffic (like an open wireless
network), and steals the user’s session cookie. Attacker then replays
this cookie and hijacks the user’s session, accessing the user’s private
data.

**Scenario \#3:** The password database uses unsalted hashes to store
everyone’s passwords. A file upload flaw allows an attacker to retrieve
the password file. All of the unsalted hashes can be exposed with a
rainbow table of precalculated hashes.

For a more complete set of requirements, see [ASVS req’ts on
Cryptography (V7), Data Protection
(V9)](https://www.owasp.org/index.php/ASVS) and [Communications Security
(V10)](https://www.owasp.org/index.php/ASVS)

  - [OWASP Cryptographic Storage Cheat
    Sheet](https://www.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet)
  - [OWASP Password Storage Cheat
    Sheet](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet)
  - [OWASP Transport Layer Protection Cheat
    Sheet](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet)
  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](https://www.owasp.org/index.php/Testing_for_SSL-TLS)

<!-- end list -->

  - [CWE Entry 310 on Cryptographic
    Issues](http://cwe.mitre.org/data/definitions/310.html)
  - [CWE Entry 312 on Cleartext Storage of Sensitive
    Information](http://cwe.mitre.org/data/definitions/312.html)
  - [CWE Entry 319 on Cleartext Transmission of Sensitive
    Information](http://cwe.mitre.org/data/definitions/319.html)
  - [CWE Entry 326 on Weak
    Encryption](http://cwe.mitre.org/data/definitions/326.html)