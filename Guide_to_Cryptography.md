[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

__TOC__

## Objective

To ensure that cryptography is safely used to protect the
confidentiality and integrity of sensitive user data.

## Platforms Affected

All.

## Relevant COBIT Topics

DS5.18 – Cryptographic key management

## Description

Initially confined to the realms of academia and the military,
cryptography has become ubiquitous thanks to the Internet. Common every
day uses of cryptography include mobile phones, passwords, SSL, smart
cards, and DVDs. Cryptography has permeated everyday life, and is
heavily used by many web applications.

Cryptography (or crypto) is one of the more advanced topics of
information security, and one whose understanding requires the most
schooling and experience. It is difficult to get right because there are
many approaches to encryption, each with advantages and disadvantages
that need to be thoroughly understood by web solution architects and
developers. In addition, serious cryptography research is typically
based in advanced mathematics and number theory, providing a serious
barrier to entry.

The proper and accurate implementation of cryptography is extremely
critical to its efficacy. A small mistake in configuration or coding
will result in removing a large degree of the protection it affords and
rending the crypto implementation useless against serious attacks.

A good understanding of crypto is required to be able to discern between
solid products and snake oil. The inherent complexity of crypto makes it
easy to fall for fantastic claims from vendors about their product.
Typically, these are “a breakthrough in cryptography” or “unbreakable”
or provide "military grade" security. If a vendor says "trust us, we
have had experts look at this,” chances are they weren't experts\!

## Cryptographic Functions

Cryptographic systems can provide one or more of the following four
services. It is important to distinguish between these, as some
algorithms are more suited to particular tasks, but not to others.

When analyzing your requirements and risks, you need to decide which of
these four functions should be used to protect your data.

### Authentication

Using a cryptographic system, we can establish the identity of a remote
user (or system). A typical example is the SSL certificate of a web
server providing proof to the user that he or she is connected to the
correct server.

The identity is not of the user, but of the cryptographic key of the
user. Having a less secure key lowers the trust we can place on the
identity.

### Non-Repudiation

The concept of non-repudiation is particularly important for financial
or e-commerce applications. Often, cryptographic tools are required to
prove that a unique user has made a transaction request. It must not be
possible for the user to refute his or her actions.

For example, a customer may request a transfer of money from her account
to be paid to another account. Later, she claims never to have made the
request and demands the money be refunded to the account. If we have
non-repudiation through cryptography, we can prove – usually through
digitally signing the transaction request, that the user authorized the
transaction.

### Confidentiality

More commonly, the biggest concern will be to keep information private.
Cryptographic systems were originally developed to function in this
capacity. Whether it be passwords sent during a log on process, or
storing confidential medical records in a database, encryption can
assure that only users who have access to the appropriate key will get
access to the data.

### Integrity

We can use cryptography to provide a means to ensure data is not viewed
or altered during storage or transmission. Cryptographic hashes for
example, can safeguard data by providing a secure checksum.

## Cryptographic Algorithms

Various types of cryptographic systems exist that have different
strengths and weaknesses. Typically, they are divided into two classes;
those that are strong, but slow to run and those that are quick, but
less secure. Most often a combination of the two approaches is used
(e.g.: SSL), whereby we establish the connection with a secure
algorithm, and then if successful, encrypt the actual transmission with
the weaker, but much faster algorithm.

### Symmetric Cryptography

Symmetric Cryptography is the most traditional form of cryptography. In
a symmetric cryptosystem, the involved parties share a common secret
(password, pass phrase, or key). Data is encrypted and decrypted using
the same key. These algorithms tend to be comparatively fast, but they
cannot be used unless the involved parties have already exchanged keys.
Any party possessing a specific key can create encrypted messages using
that key as well as decrypt any messages encrypted with the key. In
systems involving a number of users who each need to set up independent,
secure communication channels symmetric cryptosystems can have practical
limitations due to the requirement to securely distribute and manage
large numbers of keys.

Common examples of symmetric algorithms are DES, 3DES and AES. The
56-bit keys used in DES are short enough to be easily brute-forced by
modern hardware and DES should no longer be used. Triple DES (or 3DES)
uses the same algorithm, applied three times with different keys giving
it an effective key length of 112 bits (due to an attack that reduces
the strength to the work that would be involved). Due to the problems
using the DES algorithm, the United States National Institute of
Standards and Technology (NIST) hosted a selection process for a new
algorithm. The winning algorithm was Rijndael and the associated
cryptosystem is now known as the Advanced Encryption Standard or AES. It
is advisable to use AES, as DES is deprecated.

### Asymmetric Cryptography (also called Public/Private Key Cryptography)

Asymmetric algorithms use two keys, one to encrypt the data, and either
key to decrypt. These inter-dependent keys are generated together. One
is labeled the Public key and is distributed freely. The other is
labeled the Private Key and must be kept hidden.

Often referred to as Public/Private Key Cryptography, these
cryptosystems can provide a number of different functions depending on
how they are used.

The most common usage of asymmetric cryptography is to send messages
with a guarantee of confidentiality. If User A wanted to send a message
to User B, User A would get access to User B’s publicly-available Public
Key. The message is then encrypted with this key and sent to User B.
Because of the cryptosystem’s property that messages encoded with the
Public Key of User B can only be decrypted with User B’s Private Key,
only User B can read the message.

Another usage scenario is one where User A wants to send User B a
message and wants User B to have a guarantee that the message was sent
by User A. In order to accomplish this, User A would encrypt the message
with their Private Key. The message can then only be decrypted using
User A’s Public Key. This guarantees that User A created the message
Because they are then only entity who had access to the Private Key
required to create a message that can be decrcrypted by User A’s Public
Key. This is essentially a digital signature guaranteeing that the
message was created by User A.

A Certificate Authority (CA), whose public certificates are installed
with browsers or otherwise commonly available, may also digitally sign
public keys or certificates. We can authenticate remote systems or users
via a mutual trust of an issuing CA. We trust their ‘root’ certificates,
which in turn authenticate the public certificate presented by the
server.

PGP and SSL are prime examples of a systems implementing asymmetric
cryptography, using RSA or other algorithms.

### Hashes

Hash functions take some data of an arbitrary length (and possibly a key
or password) and generate a fixed-length hash based on this input. Hash
functions used in cryptography have the property that it is easy to
calculate the hash, but difficult or impossible to re-generate the
original input if only the hash value is known. In addition, hash
functions useful for cryptography have the property that it is difficult
to craft an initial input such that the hash will match a specific
desired value.

MD5 and SHA-1 are common hashing algorithms used today. These algorithms
are considered weak (see below) and are likely to be replaced after a
process similar to the AES selection. New applications should consider
using SHA-256 instead of these weaker algorithms.

### Key Exchange Algorithms

Lastly, we have key exchange algorithms (such as Diffie-Hellman for
SSL). These allow use to safely exchange encryption keys with an unknown
party.

## Algorithm Selection

As modern cryptography relies on being computationally expensive to
break, specific standards can be set for key sizes that will provide
assurance that with today’s technology and understanding, it will take
too long to decrypt a message by attempting all possible keys.

Therefore, we need to ensure that both the algorithm and the key size
are taken into account when selecting an algorithm.

### How to determine if you are vulnerable

Proprietary encryption algorithms are not to be trusted as they
typically rely on ‘security through obscurity’ and not sound
mathematics. These algorithms should be avoided if possible.

Specific algorithms to avoid:

  - MD5 has recently been found less secure than previously thought.
    While still safe for most applications such as hashes for binaries
    made available publicly, secure applications should now be migrating
    away from this algorithm.

<!-- end list -->

  - SHA-0 has been conclusively broken. It should no longer be used for
    any sensitive applications.

<!-- end list -->

  - SHA-1 has been reduced in strength and we encourage a migration to
    SHA-256, which implements a larger key size.

<!-- end list -->

  - DES was once the standard crypto algorithm for encryption; a normal
    desktop machine can now break it. AES is the current preferred
    symmetric algorithm.

Cryptography is a constantly changing field. As new discoveries in
cryptanalysis are made, older algorithms will be found unsafe. In
addition, as computing power increases the feasibility of brute force
attacks will render other cryptosystems or the use of certain key
lengths unsafe. Standard bodies such as NIST should be monitored for
future recommendations.

Specific applications, such as banking transaction systems, may have
specific requirements for algorithms and key sizes.

### How to protect yourself

Assuming you have chosen an open, standard algorithm, the following
recommendations should be considered when reviewing algorithms:

**Symmetric:**

  - Key sizes of 128 bits (standard for SSL) are sufficient for most
    applications

<!-- end list -->

  - Consider 168 or 256 bits for secure systems such as large financial
    transactions

<!-- end list -->

  - [Symmetric-key encryption protocols should include message
    authentication](https://paragonie.com/blog/2015/05/using-encryption-and-authentication-correctly)

<!-- end list -->

  - [Always Encrypt then
    MAC\!](http://www.thoughtcrime.org/blog/the-cryptographic-doom-principle/)

**Asymmetric:**

The difficulty of cracking a 2048 bit key compared to a 1024 bit key is
far, far, far, more than the twice you might expect. Don’t use excessive
key sizes unless you know you need them. Bruce Schneier in 2002 (see the
references section) recommended the following key lengths for circa 2005
threats:

  - Key sizes of 1280 bits are sufficient for most personal applications

<!-- end list -->

  - 1536 bits should be acceptable today for most secure applications

<!-- end list -->

  - 2048 bits should be considered for highly protected applications.

**Hashes:**

  - Hash sizes of 128 bits (standard for SSL) are sufficient for most
    applications

<!-- end list -->

  - Consider 168 or 256 bits for secure systems, as many hash functions
    are currently being revised (see above).

NIST and other standards bodies will provide up to date guidance on
suggested key sizes.

**Design your application to cope with new hashes and algorithms**

## Key Storage

As highlighted above, crypto relies on keys to assure a user’s identity,
provide confidentiality and integrity as well as non-repudiation. It is
vital that the keys are adequately protected. Should a key be
compromised, it can no longer be trusted.

Any system that has been compromised in any way should have all its
cryptographic keys replaced.

### How to determine if you are vulnerable

Unless you are using hardware cryptographic devices, your keys will most
likely be stored as binary files on the system providing the encryption.

Can you export the private key or certificate from the store?

  - Are any private keys or certificate import files (usually in
    PKCS\#12 format) on the file system? Can they be imported without a
    password?

<!-- end list -->

  - Keys are often stored in code. This is a bad idea, as it means you
    will not be able to easily replace keys should they become
    compromised.

### How to protect yourself

  - Cryptographic keys should be protected as much as is possible with
    file system permissions. They should be read only and only the
    application or user directly accessing them should have these
    rights.

<!-- end list -->

  - Private keys should be marked as not exportable when generating the
    certificate signing request.

<!-- end list -->

  - Once imported into the key store (CryptoAPI, Certificates snap-in,
    Java Key Store, etc.), the private certificate import file obtained
    from the certificate provider should be safely destroyed from
    front-end systems. This file should be safely stored in a safe until
    required (such as installing or replacing a new front end server).

<!-- end list -->

  - Host based intrusion systems should be deployed to monitor access of
    keys. At the very least, changes in keys should be monitored.

<!-- end list -->

  - Applications should log any changes to keys.

<!-- end list -->

  - Pass phrases used to protect keys should be stored in physically
    secure places; in some environments, it may be necessary to split
    the pass phrase or password into two components such that two people
    will be required to authorize access to the key. These physical,
    manual processes should be tightly monitored and controlled.

<!-- end list -->

  - Storage of keys within source code or binaries should be avoided.
    This not only has consequences if developers have access to source
    code, but key management will be almost impossible.

<!-- end list -->

  - In a typical web environment, web servers themselves will need
    permission to access the key. This has obvious implications that
    other web processes or malicious code may also have access to the
    key. In these cases, it is vital to minimize the functionality of
    the system and application requiring access to the keys.

<!-- end list -->

  - For interactive applications, a sufficient safeguard is to use a
    pass phrase or password to encrypt the key when stored on disk. This
    requires the user to supply a password on startup, but means the key
    can safely be stored in cases where other users may have greater
    file system privileges.

Storage of keys in hardware crypto devices is beyond the scope of this
document. If you require this level of security, you should really be
consulting with crypto specialists.

## Insecure transmission of secrets

In security, we assess the level of trust we have in information. When
applied to transmission of sensitive data, we need to ensure that
encryption occurs before we transmit the data onto any untrusted
network.

In practical terms, this means we should aim to encrypt as close to the
source of the data as possible.

### How to determine if you are vulnerable

This can be extremely difficult without expert help. We can try to at
least eliminate the most common problems:

  - The encryption algorithm or protocol needs to be adequate to the
    task. The above discussion on weak algorithms and weak keys should
    be a good starting point.

<!-- end list -->

  - We must ensure that through all paths of the transmission we apply
    this level of encryption.

<!-- end list -->

  - Extreme care needs to be taken at the point of encryption and
    decryption. If your encryption library needs to use temporary files,
    are these adequately protected?

<!-- end list -->

  - Are keys stored securely? Is an unsecured file left behind after it
    has been encrypted?

### How to protect yourself

We have the possibility to encrypt or otherwise protect data at
different levels. Choosing the right place for this to occur can involve
looking at both security as well as resource requirements.

**Application**: at this level, the actual application performs the
encryption or other crypto function. This is the most desirable, but can
place additional strain on resources and create unmanageable complexity.
Encryption would be performed typically through an API such as the
OpenSSL toolkit (www.openssl.com) or operating system provided crypto
functions.

An example would be an S/MIME encrypted email, which is transmitted as
encoded text within a standard email. No changes to intermediate email
hosts are necessary to transmit the message because we do not require a
change to the protocol itself.

**Protocol**: at this layer, the protocol provides the encryption
service. Most commonly, this is seen in HTTPS, using SSL encryption to
protect sensitive web traffic. The application no longer needs to
implement secure connectivity. However, this does not mean the
application has a free ride. SSL requires careful attention when used
for mutual (client-side) authentication, as there are two different
session keys, one for each direction. Each should be verified before
transmitting sensitive data.

Attackers and penetration testers love SSL to hide malicious requests
(such as injection attacks for example). Content scanners are most
likely unable to decode the SSL connection, letting it pass to the
vulnerable web server.

**Network**: below the protocol layer, we can use technologies such as
Virtual Private Networks (VPN) to protect data. This has many
incarnations, the most popular being IPsec (Internet Protocol v6
Security), typically implemented as a protected ‘tunnel’ between two
gateway routers. Neither the application nor the protocol needs to be
crypto aware – all traffic is encrypted regardless.

Possible issues at this level are computational and bandwidth overheads
on network devices.

## Reversible Authentication Tokens

Today’s web servers typically deal with large numbers of users.
Differentiating between them is often done through cookies or other
session identifiers. If these session identifiers use a predictable
sequence, an attacker need only generate a value in the sequence in
order to present a seemingly valid session token.

This can occur at a number of places; the network level for TCP sequence
numbers, or right through to the application layer with cookies used as
authenticating tokens.

### How to determine if you are vulnerable

Any deterministic sequence generator is likely to be vulnerable.

### How to protect yourself

The only way to generate secure authentication tokens is to ensure there
is no way to predict their sequence. In other words: true random
numbers.

It could be argued that computers can not generate true random numbers,
but using new techniques such as reading mouse movements and key strokes
to improve entropy has significantly increased the randomness of random
number generators. It is critical that you do not try to implement this
on your own; use of existing, proven implementations is highly
desirable.

Most operating systems include functions to generate random numbers that
can be called from almost any programming language.

**Windows & .NET:** On Microsoft platforms including .NET, it is
recommended to use the inbuilt CryptGenRandom function
(<u><http://msdn.microsoft.com/library/default.asp?url=/library/en-us/seccrypto/security/cryptgenrandom.asp></u>.

**Unix:** For all Unix based platforms, OpenSSL is an excellent option
(<u><http://www.openssl.org/></u>). It features tools and API functions
to generate random numbers. On some platforms, /dev/urandom is a
suitable source of pseudo-random entropy.

**PHP:** mt_rand() uses a Mersenne Twister, but is nowhere near as good
as CryptoAPI’s secure random number generation options, OpenSSL, or
/dev/urandom which is available on many Unix variants. mt_rand() has
been noted to produce the same number on some platforms – test prior to
deployment. **Do not use rand() as it is very weak.**

**Java:** java.security.SecureRandom within the Java Cryptography
Extension (JCE) provides secure random numbers. This should be used in
preference to other random number generators.

*'ColdFusion: **ColdFusion MX 7 leverages the JCE
java.security.SecureRandom class of the underlying JVM as its pseudo
random number generator (PRNG)***.'' '''

## Safe UUID generation

UUIDs (such as GUIDs and so on) are only unique if you generate them.
This seems relatively straightforward. However, there are many code
snippets available that contain existing UUIDS.

### How to determine if you are vulnerable

1.  Determine the source of your existing UUIDS
    1.  Did they come from MSDN?
    2.  Or from an example found on the Internet?
2.  Use your favorite search engine to find out

### How to protect yourself

  - Do not cut and paste UUIDs and GUIDs from anything other than the
    UUIDGEN program or from the UuidCreate() API

<!-- end list -->

  - Generate fresh UUIDs or GUIDs for each new program

## Summary

Cryptography is one of pillars of information security. Its usage and
propagation has exploded due to the Internet and it is now included in
most areas computing. Crypto can be used for:

  - Remote access such as IPsec VPN

<!-- end list -->

  - Certificate based authentication

<!-- end list -->

  - Securing confidential or sensitive information

<!-- end list -->

  - Obtaining non-repudiation using digital certificates

<!-- end list -->

  - ?Online orders and payments

<!-- end list -->

  - Email and messaging security such as S/MIME

A web application can implement cryptography at multiple layers:
application, application server or runtime (such as .NET), operating
system and hardware. Selecting an optimal approach requires a good
understanding of application requirements, the areas of risk, and the
level of security strength it might require, flexibility, cost, etc.

Although cryptography is not a panacea, the majority of security
breaches do not come from brute force computation but from exploiting
mistakes in implementation. The strength of a cryptographic system is
measured in key length. Using a large key length and then storing the
unprotected keys on the same server eliminates most of the protection
benefit gained. Besides the secure storage of keys, another classic
mistake is engineering custom cryptographic algorithms (to generate
random session ids for example). Many web applications were successfully
attacked because the developers thought they could create their crypto
functions.

Our recommendation is to use proven products, tools, or packages rather
than rolling your own.

## Further Reading

  - Wu, H., *Misuse of stream ciphers in Word and Excel*

<u><http://eprint.iacr.org/2005/007.pdf></u>

  - Bindview, *Vulnerability in Windows NT's SYSKEY encryption*

<u><http://seclists.org/bugtraq/1999/Dec/208></u>

  - Schneier, B. ''Is 1024 bits enough?, ''April 2002 Cryptogram

''<u><http://www.schneier.com/crypto-gram-0204.html#3></u> ''

  - Schneier, B., Cryptogram,

<u><http://www.schneier.com/crypto-gram.html></u>

  - NIST, Replacing SHA-1 with stronger variants: SHA-256 ? 512

<u><http://csrc.nist.gov/groups/ST/toolkit/secure_hashing.html></u>

  - UUIDs are only unique if you generate them:

<u><http://blogs.msdn.com/larryosterman/archive/2005/07/21/441417.aspx></u>

  - Cryptographically Secure Random Numbers on Win32:

<u><http://blogs.msdn.com/michael_howard/archive/2005/01/14/353379.aspx></u>

## Cryptography

The following section describes ColdFusion’s cryptography features.
ColdFusion MX leverages the Java Cryptography Extension (JCE) of the
underlying J2EE platform for cryptography and random number generation.
It provides functions for symmetric (or private-key) encryption. While
it does not provide native functionality for public-key (asymmetric)
encryption, it does use the Java Secure Socket Extension (JSSE) for SSL
communication.

**Pseudo-Random Number Generation**

ColdFusion provides three functions for random number generation:
rand(), randomize(), and randRange(). Function descriptions and syntax:

**Rand** – Use to generate a pseudo-random number

*' rand(\[algorithm\])*'

**Randomize** – Use to seed the pseudo-random number generator (PRNG)
with an integer.

*' randomize(number \[, algorithm\])*'

**RandRange** – Use to generate a pseudo-random integer within the range
of the specified numbers

*' randrange(number1, number2 \[, algorithm\])*'

The following values are the allowed algorithm parameters:

CFMX_COMPAT: (default) – Invokes java.util.rand

SHA1PRNG: (recommended) – Invokes java.security.SecureRandom using the
Sun Java SHA-1 PRNG algorithm.

IBMSecureRandom: IBM WebSphere’s JVM does not support the SHA1PRNG
algorithm.

**Symmetric Encryption**

ColdFusion MX 7 provides six encryption functions: decrypt(),
decryptBinary(), encrypt(), encryptBinary(), generateSecretKey(), and
hash(). Function descriptions and syntax:

**Decrypt** – Use to decrypt encrypted strings with specified key,
algorithm, encoding, initialization vector or salt, and iterations

*' decrypt(encrypted_string, key\[, algorithm\[, encoding\[,
IVorSalt\[, iterations\]\]\]\]))*'

**DecryptBinary** – Use to decrypt encrypted binary data with specified
key, algorithm, initialization vector or salt, and iterations

*' decryptBinary(bytes, key\[, algorithm\[, IVorSalt\[,
iterations\]\]\])*'

**Encrypt** – Use to encrypt string using specific algorithm, encoding,
initialization vector or salt, and iterations

*' encrypt(string, key\[, algorithm\[, encoding\[, IVorSalt\[,
iterations\]\]\]\]))*'

**EncryptBinary** – Use to encrypt binary data with specified key,
algorithm, initialization vector or salt, and iterations

*' encryptBinary(bytes, key\[, algorithm\[, IVorSalt\[,
iterations\]\]\])*'

**GenerateSecretKey** – Use to generate a secure key using the specified
algorithm for the encrypt and encryptBinary functions

*' generateSecretKey(algorithm)*'

'''Hash '''– Use for one-way conversion of a variable-length string to
fixed-length string using the specified algorithm and encoding

*' hash(string\[, algorithm\[, encoding\]\] )*'

ColdFusion offers the following default algorithms for these functions:

CFMX_COMPAT: the algorithm used in ColdFusion MX and prior releases.
This algorithm is the least secure option (default).

AES: the Advanced Encryption Standard specified by the National
Institute of Standards and Technology (NIST) FIPS-197. (recommended)

BLOWFISH: the Blowfish algorithm defined by Bruce Schneier.

DES: the Data Encryption Standard algorithm defined by NIST FIPS-46-3.

DESEDE: the "Triple DES" algorithm defined by NIST FIPS-46-3.

PBEWithMD5AndDES: A password-based version of the DES algorithm which
uses a MD5 hash of the specified password as the encryption key

PBEWithMD5AndTripleDES: A password-based version of the DESEDE algorithm
which uses a MD5 hash of the specified password as the encryption key

The following algorithms are provided by default for the hash()
function. Note, SHA algorithms used in ColdFusion are NIST FIPS-180-2
compliant:

CFMX_COMPAT: Generates a MD5 hash string identical to that generated by
ColdFusion MX and ColdFusion MX 6.1 (default).

MD5: Generates a 128-bit digest.

SHA: Generates a 160-bit digest. (SHA-1)

SHA-256: Generates a 256-bit digest

SHA-384: Generates a 384-bit digest

SHA-512: Generates a 512-bit digest

**Pluggable Encryption**

ColdFusion MX 7 introduced pluggable encryption for CFML. The JCE allows
developers to specify multiple cryptographic service providers.
ColdFusion can leverage the algorithms, feedback modes, and padding
methods of third-party Java security providers to strengthen its
cryptography functions. For example, ColdFusion can leverage the Bouncy
Castle (**<u><http://www.bouncycastle.org/>**) crypto package and use
the SHA-224 algorithm for the hash() function or the Serpent block
encryption for the encrypt() function.

See Macromedia’s Strong Encryption in ColdFusion MX 7 technote for
information on installing additional security providers for ColdFusion
at <http://www.macromedia.com/go/e546373d>.

**SSL**

ColdFusion does not provide tags and functions for public-key
encryption, but it can communicate over SSL. ColdFusion leverages the
Sun JSSE to communicate over SSL with web and LDAP (lightweight
directory access protocol) servers. ColdFusion uses the Java certificate
database (e.g. jre_root/lib/security/cacerts) to store server
certificates. It compares presented certificate of remote systems to
those stored in the database. It also grabs the host system’s
certificate from this database and uses it to present to remote systems
to initiate the SSL handshake. Certificate information is then exposed
as CGI variables.

***Best Practices***

  - Enable /dev/urandom for higher entropy for random number generation

<!-- end list -->

  - Call the randomize function before calling rand() or randRange() to
    seed the random number generator

<!-- end list -->

  - DO NOT use the CFMX_COMPAT algorithms. Upgrade your application to
    use stronger cryptographic ciphers.

<!-- end list -->

  - Use AES or higher for symmetric encryption

<!-- end list -->

  - Use SHA-256 or higher for the hash function

<!-- end list -->

  - Use a salt (or random string) for password generation with the hash
    function

<!-- end list -->

  - Always use generateSecretKey() to generate keys of the appropriate
    length for Block Encryption algorithms unless a customized key is
    required

<!-- end list -->

  - Use separate key databases to store remote server certificates
    separately from the ColdFusion server’s certificate

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[seems%20like%20there%20should%20be%20a%20noun%20after%20"avialable"](Category:FIXME "wikilink")
[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Encryption](Category:Encryption "wikilink")