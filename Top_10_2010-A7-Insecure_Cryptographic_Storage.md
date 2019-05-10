`    <td ``>Consider the users of your system. Would they like to gain access to protected data they aren’t authorized for? What about internal administrators?`

</td>

`    <td ``>Attackers typically don’t break the crypto. They break something else, such as find keys, get cleartext copies of data, or access data via channels that automatically decrypt.`

</td>

`    <td colspan=2  ``>The most common flaw in this area is simply not encrypting data that deserves encryption. When encryption is employed, unsafe key generation and storage, not rotating keys, and weak algorithm usage is common. Use of weak or unsalted hashes to protect passwords is also common. External attackers have difficulty detecting such flaws due to limited access. They usually must exploit something else first to gain the needed access.`

</td>

`    <td ``>Failure frequently compromises all data that should have been encrypted. Typically this information includes sensitive data such as health records, credentials, personal data, credit cards, etc.`

</td>

`    <td ``>Consider the business value of the lost data and impact to your reputation. What is your legal liability if this data is exposed? Also consider the damage to your reputation.`

</td>

The first thing you have to determine is which data is sensitive enough
to require encryption. For example, passwords, credit cards, health
records, and personal information should be encrypted. For all such
data, ensure:

1.  It is encrypted everywhere it is stored long term, particularly in
    backups of this data.
2.  Only authorized users can access decrypted copies of the data (i.e.,
    access control – See [A4](Top_10_2010-A4 "wikilink") and
    [A8](Top_10_2010-A8 "wikilink")).
3.  A strong standard encryption algorithm is used.
4.  A strong key is generated, protected from unauthorized access, and
    key change is planned for.

And more ... For a more complete set of problems to avoid, see the [ASVS
requirements on Cryptography (V7)](ASVS "wikilink").  The full perils of
unsafe cryptography are well beyond the scope of this Top 10. That said,
for all sensitive data deserving encryption, do all of the following, at
a minimum:

1.  Considering the threats you plan to protect this data from (e.g.,
    insider attack, external user), make sure you encrypt all such data
    at rest in a manner that defends against these threats.
2.  Ensure offsite backups are encrypted, but the keys are managed and
    backed up separately.
3.  Ensure appropriate strong standard algorithms and strong keys are
    used, and key management is in place.
4.  Ensure passwords are hashed with a strong standard algorithm and an
    appropriate salt is used.
5.  Ensure all keys and passwords are protected from unauthorized
    access.

**Scenario \#1**: An application encrypts credit cards in a database to
prevent exposure to end users. However, the database is set to
automatically decrypt queries against the credit card columns, allowing
an SQL injection flaw to retrieve all the credit cards in cleartext. The
system should have been configured to allow only back end applications
to decrypt them, not the front end web application.

**Scenario \#2**: A backup tape is made of encrypted health records, but
the encryption key is on the same backup. The tape never arrives at the
backup center.

**Scenario \#3**: The password database uses unsalted hashes to store
everyone’s passwords. A file upload flaw allows an attacker to retrieve
the password file. All the unsalted hashes can be brute forced in 4
weeks, while properly salted hashes would have taken over 3000 years.

For a more complete set of requirements and problems to avoid in this
area, see the [ASVS requirements on Cryptography
(V7)](http://www.owasp.org/index.php/ASVS#tab=Downloads).

  - [OWASP Top 10-2007 on Insecure Cryptographic
    Storage](Top_10_2007-Insecure_Cryptographic_Storage "wikilink")
  - [ESAPI Encryptor
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encryptor.html)
  - [OWASP Development Guide: Chapter on
    Cryptography](http://www.owasp.org/index.php/Guide_to_Cryptography#Insecure_transmission_of_secrets)
  - [OWASP Code Review Guide: Chapter on
    Cryptography](Codereview-Cryptography "wikilink")

<!-- end list -->

  - [CWE Entry 310 on Cryptographic
    Issues](http://cwe.mitre.org/data/definitions/310.html)
  - [CWE Entry 312 on Cleartext Storage of Sensitive
    Information](http://cwe.mitre.org/data/definitions/312.html)
  - [CWE Entry 326 on Weak
    Encryption](http://cwe.mitre.org/data/definitions/326.html)

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")