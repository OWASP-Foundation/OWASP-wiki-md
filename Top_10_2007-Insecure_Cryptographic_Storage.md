Protecting sensitive data with cryptography has become a key part of
most web applications. Simply failing to encrypt sensitive data is very
widespread. Applications that do encrypt frequently contain poorly
designed cryptography, either using inappropriate ciphers or making
serious mistakes using strong ciphers. These flaws can lead to
disclosure of sensitive data and compliance violations.

## Environments Affected

All web application frameworks are vulnerable to insecure cryptographic
storage.

## Vulnerability

Preventing cryptographic flaws takes careful planning. The most common
problems are:

  - Not encrypting sensitive data
  - Using home grown algorithms
  - Insecure use of strong algorithms
  - Continued use of proven weak algorithms (MD5, SHA-1, RC3, RC4, etc…)
  - Hard coding keys, and storing keys in unprotected stores

## Verifying Security

The goal is to verify that the application properly encrypts sensitive
information in storage.

Automated approaches: Vulnerability scanning tools cannot verify
cryptographic storage at all. Code scanning tools can detect use of
known cryptographic APIs, but cannot detect if it is being used properly
or if the encryption is performed in an external component.

Manual approaches: Like scanning, testing cannot verify cryptographic
storage. Code review is the best way to verify that an application
encrypts sensitive data and has properly implemented the mechanism and
key management. This may involve the examination of the configuration of
external systems in some cases.

## Protection

The most important aspect is to ensure that everything that should be
encrypted is actually encrypted. Then you must ensure that the
cryptography is implemented properly. As there are so many ways of using
cryptography improperly, the following recommendations should be taken
as part of your testing regime to help ensure secure cryptographic
materials handling:

  - **Do not** **create cryptographic algorithms**. Only use approved
    public algorithms such as AES, RSA public key cryptography, and
    SHA-256 or better for hashing.
  - **Do not** **use weak algorithms**, such as MD5 / SHA1. Favor safer
    alternatives, such as SHA-256 or better.
  - '''Generate keys offline and store private keys with extreme care.
    '''Never transmit private keys over insecure channels
  - **Ensure that infrastructure credentials such as database
    credentials or MQ queue access details are properly secured** (via
    tight file system permissions and controls), or securely encrypted
    and not easily decrypted by local or remote users
  - **Ensure that encrypted data stored on disk is not easy to
    decrypt**. For example, database encryption is worthless if the
    database connection pool provides unencrypted access.
  - Under PCI Data Security Standard requirement 3, you must protect
    cardholder data. PCI DSS compliance is mandatory by 2008 for
    merchants and anyone else dealing with credit cards. **Good practice
    is to never store unnecessary data**, such as the magnetic stripe
    information or the primary account number (PAN, otherwise known as
    the credit card number). If you store the PAN, the DSS compliance
    requirements are significant. For example, you are NEVER allowed to
    store the CVV number (the three digit number on the rear of the
    card) under any circumstances. For more information, please see the
    PCI DSS Guidelines and implement controls as necessary.

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-6145>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-1664>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-1999-1101>
  - True of most Java EE servlet containers, too.

## Related Articles

  - [Guide to Cryptography](Guide_to_Cryptography "wikilink")
  - [Insecure Storage](Insecure_Storage "wikilink")
  - [How to protect sensitive data in
    URL's](How_to_protect_sensitive_data_in_URL's "wikilink")

## References

  - CWE: CWE-311 (Failure to encrypt data), CWE-326 (Weak Encryption),
    CWE-321 (Use of hard-coded cryptographic key), CWE-325 (Missing
    Required Cryptographic Step), others.
  - WASC Threat Classification: No explicit mapping
  - PCI Data Security Standard v1.1,
    <https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf>
  - Bruce Schneier, <http://www.schneier.com/>
  - CryptoAPI Next Generation,
    <http://msdn2.microsoft.com/en-us/library/aa376210.aspx>

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")