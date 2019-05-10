## Summary

Incorrect uses of encryption algorithm may result in sensitive data
exposure, key leakage, broken authentication, insecure session and
spoofing attack. There are some encryption or hash algorithm is known to
be weak and not suggested to be used anymore such MD5 and RC4.

In addition to the right choices of secure encryption or hash algorithm,
the right uses of parameters also mater the security level. For example,
ECB (Electronic Code Book) mode is not suggested to be used in
asymmetric encryption.

The testing guide is trying to provide a guideline how to identify the
weak encryption and hash.

## How to Test

### Basic Security Checklist

  - When the uses of AES128 and AES256, The IV (Initialization vector)
    must be random and unpredictable. Refer to *[FIPS 140-2, Security
    Requirements for Cryptographic
    Modules](http://csrc.nist.gov/cryptval/140-2.htm)*, section 4.9.1.
    random number generator tests. For example, in Java,
    "java.util.Random" is considered a weak random number generator.
    "java.security.SecureRandom" should be used instead of
    "java.util.Random".
  - When uses of RSA in encryption, Optimal Asymmetric Encryption
    Padding (OAEP) mode is recommended.
  - When uses of RSA in signature, PSS padding is recommended.
  - Weak hash/encryption algorithms should not be used such MD5, RC4,
    DES, Blowfish, SHA1. 1024-bit RSA or DSA, 160-bit ECDSA (elliptic
    curves), 80/112-bit 2TDEA (two key triple DES)
  - Minimum Key length requirement:

`Key exchange: Diffie–Hellman key exchange with minimum 2048 bits`
`Message Integrity: HMAC-SHA2`
`Message Hash: SHA2 256 bits`
`Assymetric encryption: RSA 2048 bits`
`Symmetric-key algorithm: AES 128 bits`
`Password Hashing: PBKDF2, Scrypt, Bcrypt`
`ECDH、ECDSA: 256 bits`

  - Uses of SSH, CBC mode should not be used.
  - When symmetric encryption algorithm is used, ECB (Electronic Code
    Book) mode should not be used.
  - When PBKDF2 is used to hash password, the parameter of iteration is
    recommended to be over 10000.
    [NIST](https://pages.nist.gov/800-63-3/sp800-63b.html#sec5) also
    suggests at least 10,000 iterations of the hash function. In
    addition, MD5 hash function is forbidden to be used with PBKDF2 such
    as PBKDF2WithHmacMD5.

### Source Code Review

  - Search for the following keyword to check if any weak encryption
    algorithm is used.

`MD4, MD5, RC4, RC2, DES, Blowfish, SHA-1, ECB`

  - For Java implementation, the following API is related to encyprtion.
    Review the parameters of the encryption implementation. The
    following example uses of DES is not recommended since DES is
    considered a weak encryption algorithm.

`SecretKeyFactory(SecretKeyFactorySpi keyFacSpi, Provider provider, String algorithm)`
`SecretKeySpec(byte[] key, int offset, int len, String algorithm)`
`Cipher c = Cipher.getInstance("DES/CBC/PKCS5Padding");`

  - For RSA encryption, the following padding mode are suggested.

`RSA/ECB/OAEPWithSHA-1AndMGF1Padding (2048)`
`RSA/ECB/OAEPWithSHA-256AndMGF1Padding (2048)`

  - Search for "ECB", it's not allowed to be used in padding.

<!-- end list -->

  - Review if different IV (initial Vector) is used.

`// Use a different IV value for every encryption`
`byte[] newIv = ...;`
`s = new GCMParameterSpec(s.getTLen(), newIv);`
`cipher.init(..., s);`
`...`

  - Search for "IvParameterSpec", check if the IV value is generated
    differently and randomly.

` IvParameterSpec iv = new IvParameterSpec(randBytes);`
` SecretKeySpec skey = new SecretKeySpec(key.getBytes(), "AES");`
` Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding");`
` cipher.init(Cipher.ENCRYPT_MODE, skey, iv);`

  - In Java, search for MessageDigest to check if weak hash althorithm
    (MD5 or CRC) is used. For example:

`MessageDigest md5 = MessageDigest.getInstance("MD5");`

  - For signature, SHA1 and MD5 should not be used. For example:

`Signature sig = Signature.getInstance("SHA1withRSA");`

  - Search for "PBKDF2". To generate the hash value of password, PBKDF2
    is suggested to be used. Review the parameters to generate the
    PBKDF2 has value.

The iterations should be over 10000, and the salt value should be
generated as random value.

`private static byte[] pbkdf2(char[] password, byte[] salt, int iterations, int bytes)`
`    throws NoSuchAlgorithmException, InvalidKeySpecException`
`  {`
`       PBEKeySpec spec = new PBEKeySpec(password, salt, iterations, bytes * 8);`
`       SecretKeyFactory skf = SecretKeyFactory.getInstance(PBKDF2_ALGORITHM);`
`       return skf.generateSecret(spec).getEncoded();`
`   }`

  - Hard-coded senstive information

`User related keywords: name, root, su, superuser, login, username, uid`
`Key related keywords: public key, AK, SK, secret Key,  private key, passwd, password, pwd, share key, cryto, base64`
`Other common senstive keywords: sysadmin, root, privilege, pass, key, code, master, admin, uname, session, joken, Oauth, priviatekey`

## Tools

  - Vulnerability scanner such as Nessus to scan weak encryption used in
    protocol such as SNMP, TLS,SSH
  - Use static code analysis tool to do source code review such as
    klocwork, Fortify, Coverity, CheckMark for the following cases.

`CWE-261: Weak Cryptography for Passwords`
`CWE-323: Reusing a Nonce, Key Pair in Encryption.`
`CWE-326: Inadequate Encryption Strength`
`CWE-327: Use of a Broken or Risky Cryptographic Algorithm`
`CWE-328: Reversible One-Way Hash`
`CWE-329: Not Using a Random IV with CBC Mode`
`CWE-330: Use of Insufficiently Random Values`
`CWE-347: Improper Verification of Cryptographic Signature`
`CWE-354: Improper Validation of Integrity Check Value`
`CWE-547: Use of Hard-coded, Security-relevant Constants`
`CWE-780 Use of RSA Algorithm without OAEP`

## References

  - NIST FIPS <http://csrc.nist.gov/publications/PubsFIPS.html>
  - IV <https://en.wikipedia.org/wiki/Initialization_vector>
  - <https://www.securecoding.cert.org/confluence/display/java/MSC02-J.+Generate+strong+random+numbers>
  - OAEP
    <http://en.wikipedia.org/wiki/Optimal_asymmetric_encryption_padding>
  - [Cryptographic Storage Cheat
    Sheet](Cryptographic_Storage_Cheat_Sheet "wikilink")
  - [Password Storage Cheat
    Sheet](Password_Storage_Cheat_Sheet "wikilink")
  - <https://www.securecoding.cert.org/confluence/display/java/MSC61-J.+Do+not+use+insecure+or+weak+cryptographic+algorithms>
  - [Insecure Randomness](Insecure_Randomness "wikilink")
  - [Insufficient Entropy](Insufficient_Entropy "wikilink")
  - [Insufficient Session-ID
    Length](Insufficient_Session-ID_Length "wikilink")
  - [Use of hard-coded cryptographic
    key](Use_of_hard-coded_cryptographic_key "wikilink")
  - [Using a broken or risky cryptographic
    algorithm](Using_a_broken_or_risky_cryptographic_algorithm "wikilink")
  - [Testing for SSL-TLS
    (OWASP-CM-001)](Testing_for_SSL-TLS_\(OWASP-CM-001\) "wikilink")
  - <https://docs.oracle.com/javase/8/docs/api/javax/crypto/Cipher.html>
  - ISO 18033-1:2015 – Encryption Algorithms
  - ISO 18033-2:2015 – Asymmetric Ciphers
  - ISO 18033-3:2015 – Block Ciphers
  - <http://csrc.nist.gov/groups/ST/toolkit/key_management.html>
  - PBKDF2 IETF RFC 2898 and NIST SP 800-132
  - HMAC <https://www.ietf.org/rfc/rfc2104.txt>

# Authors and Primary Editors

Tony Hsu - hsiang_chih\[at\]yahoo.com