## A

### Access Control List

A list of credentials attached to a resource indicating whether or not
the credentials have access to the resource. Also referred to as an ACL.
ACL's are typically used for authorizing actions in applications.

### Active Attack

Any attack that involves actions that are detectable as an attack by the
target. A port scan is active because it can be detected by the remote
host. Of course it isn't really an attack. An active attack might
involve posting data to an endpoint with the hope of achieving XSS or
SQL Injectino. Logging of regular http request/response activity that is
later analyzed for potential vulnerabilities is passive.

### Advanced Encryption Standard (AES)

A fast general-purpose block cipher standardized by NIST (the National
Institute of Standards and Technology). The AES selection process was a
multi-year competition, where Rijndael was the winning cipher.

### Anti-debugger

Referring to technology that detects or thwarts the use of a debugger on
a piece of software.

### Anti-tampering

Referring to technology that attempts to thwart the reverse engineering
and patching of a piece of software in binary format.

### Architectural security assessment

See also: [Threat Model](#Threat_model "wikilink")

### ASN.1

Abstract Syntax Notation is a language for representing data objects. It
is popular to use this in specifying cryptographic protocols, usually
using DER (Distinguished Encoding Rules), which allows the data layout
to be unambiguously specified.

See also: [Distinguished Encoding
Rules](#Distinguished_Encoding_Rules "wikilink").

### Asymmetric cryptography

Cryptography involving public keys, as opposed to cryptography making
use of shared secrets.

See also: [Symmetric cryptography](#Symmetric_cryptography "wikilink").

### Audit

In the context of security, a review of a system in order to validate
the security of the system. Generally, this either refers to code
auditing or reviewing audit logs.

See also: [Audit log](#Audit_log "wikilink"), [Code
auditing](#Code_auditing "wikilink").

### Audit log

Records that are kept for the purpose of later verifying that the
security properties of a system have remained intact.

### Authenticate-and-encrypt

When using a cipher to encrypt and a [MAC](#MAC "wikilink") to provide
message integrity, this paradigm specifies that one authenticates the
plaintext and encrypts the plaintext, possibly in parallel. This is not
secure in the general case.

See also:
[Authenticate-then-encrypt](#Authenticate-then-encrypt "wikilink"),
[Encrypt-then-authenticate](#Encrypt-then-authenticate "wikilink").

### Authenticate-then-encrypt

When using a cipher to encrypt and a [MAC](#MAC "wikilink") to provide
message integrity, this paradigm specifies that one authenticates the
plaintext and then encrypts the plaintext concatenated with the MAC tag.
This is not secure in the general case, but usually works well in
practice.

See also:
[Authenticate-and-encrypt](#Authenticate-and-encrypt "wikilink"),
[Encrypt-then-authenticate](#Encrypt-then-authenticate "wikilink").

### Authentication

The process of verifying that someone or something is the actual entity
that they claim to be. Authentication is what happens when you log into
a system. It compares your credentials (often user name and password)
with a previously established known value such that the system can know
that you are who you say you are. For sensitive systems, there is a
trend toward using two factor authentication (2FA) which essentially
means that users must supply two different secrets, usually one is a
password (something they know) and the other is a pin supplied via text
(verifying something they have).

### Authorization

Authorization is the process of determining whether an authenticated
subject (a user) can see, change, delete or take other actions upon
data. For example, if you log into a time keeping application, submit
your timesheet and then your boss approves it, the act of logging in is
authenticating, the act of filling out your timesheet and submitting
should only be something your user is authorized to do and approving the
timesheet is something only the boss is authorized to do. Authorization
is tied to both \#4 and \#7 of the 2013 OWASP Top 10.

## B

### Backdoor

Malicious code inserted into a program for the purposes of providing the
author covert access to machines running the program.

### Base 64

A method for encoding binary data into printable ASCII strings. Every
byte of output maps to six bits of input (minus possible padding bytes).

### Big endian

Refers to machines representing words most significant byte first. While
x86 machines do not use big endian byte ordering (instead using little
endian), the PowerPC and SPARC architectures do. This is also network
byte order.

See also: [Little endian](#Little_endian "wikilink").

### Birthday attack

Take a function f() that seems to map an input to a random output of
some fixed size (a pseudo-random function or PRF). A birthday attack is
simply selecting random inputs for f() and checking to see if any
previous values gave the same output. Statistically, if the output size
is S bits, then one can find a collision in 2S/2 operations, on average.

### Bit-flipping attack

In a stream cipher, flipping a bit in the ciphertext flips the
corresponding bit in the plaintext. If using a message authentication
code ([MAC](#MAC "wikilink")), such attacks are not practical.

### Blacklist

When performing input validation, the set of items that — if matched —
result in the input being considered invalid. If no invalid items are
found, the result is valid.

See also: [Whitelist](#Whitelist "wikilink").

### Blinding

A technique used to thwart timing attacks.

### Block cipher

An encryption algorithm that maps inputs of size n to outputs of size n
(n is called the block size). Data that is not a valid block size must
somehow be padded (generally by using an encryption mode). The same
input always produces the same output.

See also: [Stream cipher](#Stream_cipher "wikilink").

### Blowfish

A block cipher with 64-bit blocks and variable length keys, created by
Bruce Schneier. This cipher is infamous for having slow key-setup times.

### Brute-force attack

An attack on an encryption algorithm where the encryption key for a
ciphertext is determined by trying to decrypt with every key until valid
plaintext is obtained.

### Buffer overflow

A buffer overflow is when you can put more data into a memory location
than is allocated to hold that data. Languages like C and C++ that do no
built-in bounds checking are susceptible to such problems. These
problems are often security-critical.

## C

### CA

See also: [Certification
Authority](#Certification_Authority "wikilink").

### Canary

A piece of data, the absence of which indicates a violation of a
security policy. Several tools use a canary for preventing certain
stack-smashing buffer overflow attacks.

See also: [Buffer overflow](#Buffer_overflow "wikilink"), [Stack
smashing](#Stack_smashing "wikilink").

### Capture-replay attacks

When an attacker can capture data off the wire and replay it later
without the bogus data being detected as bogus.

### Carter-Wegman Counter (data encryption mode)

A parallelizable and patent-free high-level encryption mode that
provides both encryption and built-in message integrity.

### CAST5

A block cipher with 64-bit blocks and key sizes up to 128 bits. It is
patent- free, and generally considered sound, but modern algorithms with
larger block sizes are generally preferred (e.g., AES).

See also: [AES](#AES "wikilink").

### CBC Mode

See also: [Cipher-Block Chaining
mode](#Cipher-Block_Chaining_mode "wikilink").

### CBC-MAC

A simple construction for turning a block cipher into a message
authentication code. It only is secure when all messages MAC’d with a
single key are the same size. However, there are several variants that
thwart this problem, the most important being OMAC.

See also: [OMAC](#OMAC "wikilink").

### CCM mode

See also: [Counter mode with CBC-MAC
(CCM)](#Counter_mode_with_CBC-MAC_\(CCM\) "wikilink").

### Certificate

A data object that binds information about a person or some other entity
to a public key. The binding is generally done using a digital signature
from a trusted third party (a certification authority).

### Certificate Revocation List

A list published by a certification authority indicating which issued
certificates should be considered invalid.

### Certificate Signing Request

Data about an entity given to a certification authority. The authority
will package the data into a certificate and sign the certificate if the
data in the signing request is validated.

### Certification Authority

An entity that manages digital certificates — i.e., issues and revokes.
Verisign and InstantSSL are two well known CAs.

### CFB mode

See also: [Cipher Feedback mode](#Cipher_Feedback_mode "wikilink").

### Chain responder

An OCSP responder that relays the results of querying another OCSP
responder.

See also: [OCSP](#OCSP "wikilink").

### Choke point

In computer security, a place in a system where input is routed for the
purposes of performing data validation. The implication is that there
are few such places in a system and that all data must pass through one
or more of the choke points. The idea is that funneling input through a
small number of choke points makes it easier to ensure that input is
properly validated. One potential concern is that poorly chosen choke
points may not have enough information to perform input validation that
is as accurate as possible.

### chroot

A UNIX system call that sets the root directory for a process to any
arbitrary directory. The idea is compartmentalization: Even if a process
is compromised, it should not be able to see interesting parts of the
file system beyond its own little world. There are some instances where
chroot "jails" can be circumvented; it can be difficult to build proper
operating environments to make chroot work well.

### Cipher-Block Chaining mode

A block cipher mode that provides secrecy but not message integrity.
Messages encrypted with this mode should have random initialization
vectors.

### Cipher Feedback mode

A mode that turns a block cipher into a stream cipher. This mode is safe
only when used in particular configurations. Generally, CTR mode and OFB
mode are used instead since both have better security bounds.

### Ciphertext

The result of encrypting a message.

See also: [Plaintext](#Plaintext "wikilink").

### Ciphertext stealing mode

A block cipher mode of operation that is similar to CBC mode except that
the final block is processed in such a way that the output is always the
same length as the input. That is, this mode is similar to CBC mode but
does not require padding.

See also: [Cipher-Block Chaining
mode](#Cipher-Block_Chaining_mode "wikilink"),
[Padding](#Padding "wikilink").

### CLASP

See also: [Comprehesive, Lightweight Application Security
Process](#Comprehesive,_Lightweight_Application_Security_Process "wikilink")

### Code auditing

Reviewing computer software for security problems.

See also: [Audit](#Audit "wikilink").

### Code signing

Signing executable code to establish that it comes from a trustworthy
vendor. The signature must be validated using a trusted third party in
order to establish identity.

### Compartmentalization

Separating a system into parts with distinct boundaries, using simple,
well- defined interfaces. The basic idea is that of containment — i.e.,
if one part is compromised, perhaps the extent of the damage can be
limited.

See also: [Jail](#Jail "wikilink"), [Chroot](#Chroot "wikilink").

### Comprehesive, Lightweight Application Security Process

An activity-driven, role based set of process components whose core
contains formalized best practices for building security into your
existing or new-start software development lifecycles in a structured,
repeatable, and measurable way.

See also:

  - [OWASP CLASP Project](:Category:OWASP_CLASP_Project "wikilink")

### Context object

In a cryptographic library, a data object that holds the intermediate
state associated with the cryptographic processing of a piece of data.
For example, if incrementally hashing a string, a context object stores
the internal state of the hash function necessary to process further
data.

### Counter mode

A parallelizable encryption mode that effectively turns a block cipher
into a stream cipher. It is a popular component in authenticated
encryption schemes due to its optimal security bounds and good
performance characteristics.

### Counter mode with CBC-MAC (CCM)

An encryption mode that provides both message secrecy and integrity. It
was the first such mode that was not covered by patent.

### CRAM

A password-based authentication mechanism using a cryptographic hash
function (usually MD5). It does not provide adequate protection against
several common threats to password-based authentication systems. HTTP
Digest Authentication is a somewhat better alternative; it is replacing
CRAM in most places.

### CRC

Cyclic Redundancy Check. A means of determining whether accidental
transmission errors have occurred. Such algorithms are not
cryptographically secure because attackers can often forge CRC values or
even modify data maliciously in such a way that the CRC value does not
change. Instead, one should use a strong, keyed message authentication
code such as HMAC or OMAC.

See also: [HMAC](#HMAC "wikilink"), [Message Authentication
Code](#Message_Authentication_Code "wikilink"),
[OMAC](#OMAC "wikilink").

### Critical extensions

In an X.509 certificate, those extensions that must be recognized by any
software processing the certificate. If a piece of software does not
recognize an extension marked as critical, the software must regard the
certificate as invalid.

### CRL

See also: [Certificate Revocation
List](#Certificate_Revocation_List "wikilink").

### Cross-site request forgery

[CSRF](CSRF "wikilink") is an attack which forces an end user to execute
unwanted actions on a web application in which he/she is currently
authenticated. With little help of social engineering (like sending a
link via email/chat), an attacker may force the users of a web
application to execute actions of the attackers choosing. A successful
CSRF exploit can compromise end user data and operation in case of
normal user. If the targeted end user is the administrator account, this
can compromise the entire web application.

### Cross-site scripting

A class of problems resulting from insufficient input validation where
one user can add content to a web site that can be malicious when viewed
by other users to the web site. For example, one might post to a message
board that accepts arbitrary HTML and include a malicious code item.

### Cryptanalysis

The science of breaking cryptographic algorithms.

### Cryptographic hash function

A function that takes an input string of arbitrary length and produces a
fixed- size output — where it is unfeasible to find two inputs that map
to the same output, and it is unfeasible to learn anything about the
input from the output.

### Cryptographic randomness

Data produced by a cryptographic pseudo-random number generator. The
probability of figuring out the internal state of the generator is
related to the strength of the underlying cryptography — i.e., assuming
the generator is seeded with enough entropy.

### Cryptography

The science of providing secrecy, integrity, and non-repudiation for
data.

### CSR

See also: [Certificate Signing
Request](#Certificate_Signing_Request "wikilink").

### CSS

Cross-site scripting. Generally, however, this is abbreviated to XSS in
order to avoid confusion with cascading style sheets.

See also: [Cross-site scripting](#Cross-site_scripting "wikilink").

### CTR mode

See also: [Counter mode](#Counter_mode "wikilink").

### CWC mode

See also: [Carter Wegmen + Counter
mode](#Carter-Wegmen_Counter_\(data_encryption_mode\) "wikilink").

## D

### DACL

Discretionary Access Control List. In a Windows ACL, a list that
determines access rights to an object.

See also: [Access Control List](#Access_Control_List "wikilink").

### Davies-Meyer

An algorithm for turning a block cipher into a cryptographic one-way
hash function.

### Default deny

A paradigm for access control and input validation where an action must
explicitly be allowed. The idea behind this paradigm is that one should
limit the possibilities for unexpected behavior by being strict, instead
of lenient, with rules.

### Defense-in-depth

A principle for building systems stating that multiple defensive
mechanisms at different layers of a system are usually more secure than
a single layer of defense. For example, when performing input
validation, one might validate user data as it comes in and then also
validate it before each use — just in case something was not caught, or
the underlying components are linked against a different front end, etc.

### DEK

Data encrypting key.

### Delta CRLs

A variation of Certificate Revocation Lists that allows for incremental
updating, as an effort to avoid frequently re-downloading a large amount
of unchanged data.

See also: [Certificate Revocation
List](#Certificate_Revocation_List "wikilink").

### Denial of service attack

Any attack that affects the availability of a service. Reliability bugs
that cause a service to crash or go into some sort of vegetative state
are usually potential denial-of-service problems.

### DES

See also: [Data Encryption
Standard](#Data_Encryption_Standard "wikilink"), [Triple
DES](#Triple_DES "wikilink").

### DESX

An extended version of DES that increases the resistance to brute-force
attack in a highly efficient way by increasing the key length. The extra
key material is mixed into the encryption process, using XORs. This
technique does not improve resistance to differential attacks, but such
attacks are still generally considered unfeasible against DES.

See also: [DES](#DES "wikilink").

### Dictionary attack

An attack against a cryptographic system, using precomputating values to
build a dictionary. For example, in a password system, one might keep a
dictionary mapping ciphertext pairs in plaintext form to keys for a
single plaintext that frequently occurs. A large enough key space can
render this attack useless. In a password system, there are similar
dictionary attacks, which are somewhat alleviated by salt. The end
result is that the attacker — once he knows the salt — can do a
“Crack”-style dictionary attack. Crack-style attacks can be avoided
to some degree by making the password verifier computationally expensive
to compute. Or select strong random passwords, or do not use a
password-based system.

### Differential cryptanalysis

A type of cryptographic attack where an attacker who can select related
inputs learns information about the key from comparing the outputs.
Modern ciphers of merit are designed in such a way as to thwart such
attacks. Also note that such attacks generally require enough chosen
plaintexts as to be considered unfeasible, even when there is a cipher
that theoretically falls prey to such a problem.

### Diffie-Hellman key exchange

A method for exchanging a secret key over an untrusted medium in such a
way as to preserve the secrecy of the key. The two parties both
contribute random data that factors into the final shared secret. The
fundamental problem with this method is authenticating the party with
whom you exchanged keys. The simple Diffie-Hellman protocol does not do
that. One must also use some public-key authentication system such as
DSA.

See also: [DSA](#DSA "wikilink"), [Station-to-station
protocol](#Station-to-station_protocol "wikilink").

### Digest size

The output size for a hash function.

### Data Encryption Standard

An encryption algorithm standardized by the US Government. The key
length is too short, so this algorithm should be considered insecure.
The effective key strength is 56 bits; the actual key size is 64 bits —
8 bits are wasted. However, there are variations such as Triple DES and
DESX that increase security while also increasing the key size.

See also: [Advanced Encryption
Standard](#Advanced_Encryption_Standard "wikilink"), [Triple
DES](#Triple_DES "wikilink").

### Digital signature

Data that proves that a document (or other piece of data) was not
modified since being processed by a particular entity. Generally, what
this really means is that — if someone ‘signs’ a piece of data — anyone
who has the right public key can demonstrated which private key was used
to sign the data.

### Digital Signature Algorithm

See also: [DSA](#DSA "wikilink").

### Distinguished Encoding Rules

A set of rules used that describes how to encode ASN.1 data objects
unambiguously.

See also: [ASN.1](#ASN.1 "wikilink").

### Distinguished Name

In an X.509 certificate, a field that uniquely specifies the user or
group to which the certificate is bound. Usually, the Distinguished Name
will contain a user’s name or User ID, an organizational name, and a
country designation. For a server certificate, it will often contain the
DNS name of the machine.

### DN

See also: [Distinguished Name](#Distinguished_Name "wikilink").

### DoS

Denial of Service.

See also: [Denial of service
attack](#Denial_of_service_attack "wikilink").

### DSA

The Digital Signature Algorithm, a public key algorithm dedicated to
digital signatures which was standardized by NIST. It is based on the
same mathematical principles as Diffie-Hellman.

## E

### Eavesdropping attack

Any attack on a data connection where one simply records or views data
instead of tampering with the connection.

See also: [Passive attack](#Passive_attack "wikilink").

### ECB Mode

See also: [Electronic Code Book
mode](#Electronic_Code_Book_mode "wikilink").

### ECC

See also: [Eliptic Curve
Cryptography](#Eliptic_Curve_Cryptography "wikilink").

### EGD

See also: [Entropy Gathering
Daemon](#Entropy_Gathering_Daemon "wikilink").

### Electronic Code Book mode

An encryption mode for block ciphers that is more or less a direct use
of the underlying block cipher. The only difference is that a message is
padded out to a multiple of the block length. This mode should not be
used under any circumstances.

### Eliptic Curve Cryptography

A type of public key cryptography that — due to smaller key sizes —
tends to be more efficient that standard cryptography. The basic
algorithms are essentially the same, except that the operations are
performed over different mathematical groups (called eliptic curves).

### EME-OAEP padding

A padding scheme for public key cryptography that uses a “random” value
generated, using a cryptographic hash function in order to prevent
particular types of attacks against RSA.

See also: [PKCS \#1 padding](#PKCS_#1 "wikilink").

### Encrypt-then-authenticate

When using a cipher to encrypt and a MAC to provide message integrity,
this paradigm specifies that one encrypts the plaintext, then MACs the
ciphertext. This paradigm has theoretically appealing properties and is
recommended to use in practice.

See also:
[Authenticate-and-encrypt](#Authenticate-and-encrypt "wikilink"),
[Authenticate-then-encrypt](#Authenticate-then-encrypt "wikilink").

### Endianess

The byte ordering scheme that a machine uses (usually either little
endian or big endian).

See also:[Big endian](#Big_endian "wikilink"), [Little
endian](#Little_endian "wikilink").

### Entropy

Refers to the inherent unknowability of data to external observers. If a
bit is just as likely to be a 1 as a 0 and a user does not know which it
is, then the bit contains one bit of entropy.

### Entropy Gathering Daemon

A substitute for /dev/random; a tool used for entropy harvesting.

### Entropy harvester

A piece of software responsible for gathering entropy from a machine and
distilling it into small pieces of high entropy data. Often an entropy
harvester will produce a seed for a cryptographic pseudo-random number
generator.

See also: [Entropy](#Entropy "wikilink"), [Pseudo-random number
generator](#Pseudo-random_number_generator "wikilink").

### Ephemeral keying

Using one-time public key pairs for session key exchange in order to
prevent recovering previous session keys if a private key is
compromised. Long-term public key pairs are still used to establish
identity.

### Euclidian algorithm

An algorithm that computes the greatest common divisor of any two
numbers.

### Extended Euclidian algorithm

An algorithm used to compute the inverse of a number modulo “some other
number.”

## F

### Fingerprint

The output of a cryptographic hash function.

See also: [Message digest](#Message_digest "wikilink").

### FIPS

Federal Information Processing Standard; a set of standards from NIST.

### FIPS-140

A standard authored by the U.S. National Institute of Standards and
Technology, that details general security requirements for cryptographic
software deployed in a government systems (primarily cryptographic
providers).

See also: [NIST](#NIST "wikilink"), [FIPS](#FIPS "wikilink").

### Format string attack

The C standard library uses specifiers to format output. If an attacker
can control the input to such a format string, he can often write to
arbitrary memory locations.

### Forward secrecy

Ensuring that the compromise of a secret does not divulge information
that could lead to data protected prior to the compromise. In many
systems with forward secrecy, it is only provided on a per-session
basis, meaning that a key compromise will not affect previous sessions,
but would allow an attacker to decrypt previous messages sent as a part
of the current session.

See also: [Perfect forward
secrecy](#Perfect_forward_secrecy "wikilink").

## G

## H

### Hash function

A function that maps a string of arbitrary length to a fixed size value
in a deterministic manner. Such a function may or may not have
cryptographic applications.

See also: [Cryptographic hash
function](#Cryptographic_hash_function "wikilink"), [Universal hash
function](#Universal_hash_function "wikilink"), [One-way hash
function](#One-way_hash_function "wikilink").

### Hash function (cryptographic)

See also: [Cryptographic hash
function](#Cryptographic_hash_function "wikilink").

### Hash function (one-way)

See also: [One-way hash function](#One-way_hash_function "wikilink").

### Hash function (universal)

See also: [Universal hash
function](#Universal_hash_function "wikilink").

### Hash output

See also: [Hash value](#Hash_value "wikilink").

### Hash value

The output of a hash function.

See also: [Fingerprint](#Fingerprint "wikilink"), [Message
digest](#Message_digest "wikilink").

### hash127

A fast universal hash function from Dan Bernstein.

### HMAC

A well-known algorithm for converting a cryptographic one-way hash
function into a message authentication code.

### Honey Pot

A strategy of setting up resources which an attacker believes are real
but are infact designed specifically to catch the attacker.

## I

### IDEA

A block cipher with 128-bit keys and 64-bit blocks popularly used with
PGP. It is currently protected by patents.

### Identity establishment

See [Authentication](#Authentication "wikilink")

### Impact

A component of [Risk](#Risk "wikilink"), the impact describes the
negative effect that results from a risk being realised. Example impacts
include financial loss, legal and regulatory issues, brand and
reputation damage, data loss, breach of contract, and so on. Impacts can
be reduced as part of risk [mitigation](#Mitigation "wikilink"). For
example, installing a second hard drive and configuring it as a RAID
mirror of a primary hard drive reduces the impact of a disk failure. It
does not address the likelihood of a disk failure at all.

Impacts, like risks, can be technical or business related. For example,
a technical impact could be corrupt data in the table storing a firm's
outstanding orders. The business impact might be customer ill-will,
increased customer service costs, and additional costs shipping and
tracking replacement items.

Some impacts can be contractually transferred to another party.
Insurance, for example, can transfer the financial impact of a business
risk to the insurer in exchange for a premium payment by the insured.
The technical impact of a DDoS attack can be transferred to another
entity by using their network and server resources. Not all impacts can
be transferred. Brand and reputation damage, some legal and regulatory
liability, and impacts on business qualities like time-to-market cannot
be transferred.

### Indirect CRLs

A CRL issued by a third party, that can contain certificates from
multiple CA’s.

See also: [Certificate](#Certificate "wikilink"), [Certificate
Revocation List](#Certificate_Revocation_List "wikilink"),
[Certification Authority](#Certification_Authority "wikilink").

### Initialization vector

A value used to initialize a cryptographic algorithm. Often, the
implication is that the value must be random.

See also: [Nonce](#Nonce "wikilink"), [Salt](#Salt "wikilink").

### Input validation

The act of determining that data input to a program is sound.

### Integer overflow

When an integer value is too big to be held by its associated data type,
the results can often be disastrous. This is often a problem when
converting unsigned numbers to signed values.

### Integrity checking

The act of checking whether a message has been modified either
maliciously or by accident. Cryptographically strong message integrity
algorithms should always be used when integrity is important.

### Interleaved encryption

Processing the encryption of a message as multiple messages, generally
treating every nth block as part of a single message.

### ISO/IEC 17799

Provides best practice recommendations on information security
management for use by those who are responsible for initiating,
implementing or maintaining information security management systems.

### IV

See also: [Initialization vector](#Initialization_vector "wikilink").

## J

### Jail

A restricted execution environment meant to compartmentalize a process,
so that — even if it has security problems — it cannot hurt resources
which it would not normally have access to use. On FreeBSD, a system
call similar to chroot that provides compartmentalization. Unlike
chroot, it can also restrict network resources in addition to file
system resources.

See also: [chroot](#chroot "wikilink").

## K

### Kerberos

An authentication protocol that relies solely on symmetric cryptography,
as opposed to public key cryptography. It still relies on a trusted
third party (an authentication server). While Kerberos is often looked
upon as a way to avoid problems with Public Key Infrastructure, it can
be difficult to scale Kerberos beyond medium-sized organizations.

See also: [Public Key
Infrastructure](#Public_Key_Infrastructure "wikilink"), [Trusted third
party](#Trusted_third_party "wikilink").

### Key agreement

The process of two parties agreeing on a shared secret, where both
parties contribute material to the key.

### Key establishment

The process of agreeing on a shared secret, where both parties
contribute material to the key.

### Key exchange

The process of two parties agreeing on a shared secret, usually implying
that both parties contribute to the key.

### Key management

Mechanisms and process for secure creation, storage, and handling of key
material.

### Key schedule

In a block cipher, keys used for individual “rounds” of encryption,
derived from the base key in a cipher-dependent manner.

### Key transport

When one party picks a session key and communicates it to a second
party.

### Keystream Output

from a stream cipher.

See also: [Pseudo-random number
generator](#Pseudo-random_number_generator "wikilink"), [Stream
cipher](#Stream_cipher "wikilink").

## L

### LDAP

Lightweight Directory Access Protocol. A directory protocol commonly
used for storing and distributing CRLs.

### Length extension attack

A class of attack on message authentication codes, where a tag can be
forged without the key by extending a pre-existing message in a
particular way. CBC-MAC in its simplest form has this problem, but
variants protect against it (particularly OMAC).

See also: [Message Authentication
Code](#Message_Authentication_Code "wikilink"),
[OMAC](#OMAC "wikilink").

### Likelihood

A component of [risk](#Risk "wikilink"), likelihood describes the chance
that a risk will be realised and the negative
[impact](#Impact "wikilink") will occur. It is typically described in
general terms like "low," "medium," and "high". Sometimes an actual
probability is possible (e.g., the probability of two documents
producing the same CRC-16 is approximately 1 in 65536).

The likelihood of a technical risk is often related to the likelihood of
a [vulnerability](:Category:Vulnerability "wikilink") being successfully
[exploited](#Exploit "wikilink"). This likelihood is often influenced by
factors like how accessible the vulnerability is, the degree to which
special tools need to be used to be successful, the amount of
specialised knowledge an attacker needs, and so on.

Likelihood is combined with [impact](#Impact "wikilink") to produce a
[severity](#Severity "wikilink") estimate for a
[risk](#Risk "wikilink").

### LFSR

See also: [Linear Feedback Shift
Register](#Linear_Feedback_Shift_Register "wikilink").

### Linear cryptanalysis

A type of cryptanalytic attack where linear approximations of behavior
are used. Modern ciphers of merit are designed in such a way as to
thwart such attacks. Also note that such attacks generally require
enough chosen plaintexts as to be considered unfeasible — even when
there is a cipher that theoretically falls prey to such a problem (such
as DES).

### Linear Feedback Shift Register

A non-cryptographic class of pseudo-random number generators, where
output is determined by shifting out "output" bits and shifting in
"input" bits, where the input bits are a function of the internal state
of the register, perhaps combined with new entropy. LFSRs are based on
polynomial math, and are not secure in and of themselves; however, they
can be put to good use as a component in more secure cryptosystems.

### Little endian

Refers to machines representing words of data least significant byte
first, such as the Intel x86.

See also: [Big endian](#Big_endian "wikilink").

## M

### MAC

See also: [Message Authentication
Code](#Message_Authentication_Code "wikilink").

### Man-in-the-middle attack

An eavesdropping attack where a client’s communication with a server is
proxied by an attacker. Generally, the implication is that the client
performs a cryptographic key exchange with an entity and fails to
authenticate that entity, thus allowing an attacker to look like a valid
server.

### Matyas-Meyer-Oseas

A construction for turning a block cipher into a cryptographic one-way
hash function.

### MCF

The Modular Crypt Format, a de-facto data format standard for storing
password hashes commonly used on UNIX boxes as a replacement for the
traditional UNIX crypt() format.

### MD-strengthening

Merkel-Damgard strengthening, a general method for turning a collision-
resistant compression function into a collision-resistant hash function
by adding padding and an encoded length to the end of the input message.
The key point behind MD-strengthening is that no possible input to the
underlying hash function can be the tail end of a different input.

### MD2

A cryptographic hash function optimized for 16-bit platforms. It has
poor performance characteristics on other platforms and has a weak
internal structure.

### MD4

A cryptographic hash function that is known to be broken and should not
be used under any circumstances.

### MD5

A popular and fast cryptographic hash function that outputs 128-bit
message digests. Its internal structure is known to be weak and should
be avoided if at all possible.

### MD5-MCF

A way of using MD5 to store password authentication information, using
the modular crypt format.

See also: [MCF](#MCF "wikilink"), [MD5](#MD5 "wikilink").

### MDC2

A construction for turning a block cipher into a cryptographic hash
function, where the output length is twice the block size of the cipher.

### Meet-in-the-middle attack

A theoretical attack against encrypting a message twice using a single
block cipher and two different keys. For example, double encryption with
DES theoretically is no more secure than DES, which is why Triple DES
became popular (it gives twice the effective key strength).

### Message Authentication Code

A function that takes a message and a secret key (and possibly a nonce)
and produces an output that cannot, in practice, be forged without
possessing the secret key.

### Message digest

The output of a hash function.

### Message integrity

A message has integrity if it maintains the value it is supposed to
maintain, as opposed to being modified on accident or as part of an
attack.

### Methodology

A mature set of processes applied to various stages of an applications'
lifecycle to help reduce the likelihood of security vulnerabilities
presence or exploitation.

### Metrics

A metric is a standard unit of measure, such as meter or mile for
length, or gram or ton for weight, or more generally, part of a system
of parameters, or systems of measurement, or a set of ways of
quantitatively and periodically measuring, assessing, controlling or
selecting a person, process, event, or institution, along with the
procedures to carry out measurements and the procedures for the
interpretation of the assessment in the light of previous or comparable
assessments.

### Miller-Rabin

A primality test that is efficient because it is probabilistic, meaning
that there is some chance it reports a composite (non-prime) number as a
prime. There is a trade-off between efficiency and probability, but one
can gain extremely high assurance without making unreasonable sacrifices
in efficiency.

### Model

A model is a pattern, plan, representation (especially in miniature), or
description designed to show the main object or workings of an object,
system, or concept.

### Modulus

In the context of public key cryptography, a value by which all other
values are reduced. That is, if a number is bigger than the modulus, the
value of the number is considered to be the same as if the number were
the remainder after dividing the number by the modulus.

## N

### Near-collision resistance

Given a plaintext value and the corresponding hash value, it should be
computationally unfeasible to find a second plaintext value that gives
the same hash value.

### NIST

The National Institute of Standards and Technology is a division of the
U.S. Department of Commerce. NIST issues standards and guidelines, with
the hope that they will be adopted by the computing community.

### Non-repudiation

The capability of establishing that a message was signed by a particular
entity. That is, a message is said to be non-repudiatable when a user
sends it, and one can prove that the user sent it. In practice,
cryptography can demonstrate that only particular key material was used
to produce a message. There are always legal defenses such as stolen
credentials or duress.

### Nonce

A value used with a cryptographic algorithm that must be unique in order
to maintain the security of the system. Generally, the uniqueness
requirement holds only for a single key — meaning that a {key, nonce}
pair should never be reused.

See also: [Initialization vector](#Initialization_vector "wikilink"),
[Salt](#Salt "wikilink").

## O

### OCB mode

See also: [Offset Code Book mode](#Offset_Code_Book_mode "wikilink").

### OCSP

See also: [Online Certificate Status
Protocol](#Online_Certificate_Status_Protocol "wikilink").

### OCSP responder

The server side software that answers OCSP requests.

See also: [Online Certificate Status
Protocol](#Online_Certificate_Status_Protocol "wikilink").

### OFB mode

See also: [Output Feedback mode](#Output_Feedback_mode "wikilink").

### Offset Code Book mode

A patented encryption mode for block ciphers that provides both secrecy
and message integrity and is capable of doing so at high speeds.

### OMAC

One-key CBC-MAC. A secure, efficient way for turning a block cipher into
a message authentication code. It is an improvement of the CBC-MAC,
which is not secure in the arbitrary case. Other CBC-MAC variants use
multiple keys in order to fix the problem with CBC-MAC. OMAC uses a
single key and still has appealing provable security properties.

### One-time pad

A particular cryptographic system that is provably secure in some sense,
but highly impractical, because it requires a bit of entropy for every
bit of message.

### One-time password

A password that is only valid once. Generally, such passwords are
derived from some master secret — which is shared by an entity and an
authentication server — and are calculated via a challenge-response
protocol.

### One-way hash function

A hash function, where it is computationally unfeasible to determine
anything about the input from the output.

### Online Certificate Status Protocol

A protocol for determining whether a digital certificate is valid in
real time without using CRLs. This protocol (usually abbreviated OCSP)
is specified in RFC 2560.

### Output Feedback mode

A block cipher mode that turns a block cipher into a stream cipher. The
mode works by continually encrypting the previous block of keystream.
The first block of keystream is generated by encrypting an
initialization vector.

## P

### Padding

Data added to a message that is not part of the message. For example,
some block cipher modes require messages to be padded to a length that
is evenly divisible by the block length of the cipher — i.e., the number
of bytes that the cipher processes at once.

### PAM

Pluggable Authentication Modules is a technology for abstracting out
authentication at the host level. It is similar to SASL, but is a bit
higher up in the network stack and tends to be a much easier technology
to use, particularly for system administrators, who can configure
authentication policies quite easily using PAM.

See also: [SASL](#SASL "wikilink").

### Partial collision resistance

When it is unfeasible to find two arbitrary inputs to a hash function
that produce similar outputs — i.e., outputs that differ in only a few
bits.

### Passive attack

See also: [Eavesdropping attack](#Eavesdropping_attack "wikilink").

### Passphrase

A synonym for “password,” meant to encourage people to use longer (it is
hoped, more secure) values.

### Password

A value that is used for authentication.

### PBKDF2

Password-Based Key Derivation Function \#2. An algorithm defined in PKCS
\#5 for deriving a random value from a password.

### PEM encoding

A simple encoding scheme for cryptographic objects that outputs
printable values (by Base 64 encoding a DER-encoded representation of
the cryptographic object). The scheme was first introduced in Privacy
Enhanced Mail, a defunct way of providing E-mail security.

### Perfect forward secrecy

Ensuring that the compromise of a secret does not divulge information
that could lead to the recovery of data protected prior to the
compromise.

See also: [Forward secrecy](#Forward_secrecy "wikilink").

### PKCS \#1

Public Key Cryptography Standard \#1. A standard from RSA Labs
specifying how to use the RSA algorithm for encrypting and signing data.

### PKCS \#1

padding This form of padding can encrypt messages up to 11 bytes smaller
than the modulus size in bytes. You should not use this method for any
purpose other than encrypting session keys or hash values.

### PKCS \#10

Describes a standard syntax for certification requests.

### PKCS \#11

Specifies a programming interface called Cryptoki for portable
cryptographic devices of all kinds.

### PKCS \#3

Public Key Cryptography Standard \#3. A standard from RSA Labs
specifying how to implement the Diffie-Hellman key exchange protocol.

### PKCS \#5

Public Key Cryptography Standard \#5. A standard from RSA Labs
specifying how to derive cryptographic keys from a password.

### PKCS \#7

Public Key Cryptography Standard \#7. A standard from RSA Labs
specifying a generic syntax for data that may be encrypted or signed.

### PKI

See also: [Public Key
Infrastructure](#Public_Key_Infrastructure "wikilink").

### Plaintext

An unencrypted message.

See also: [Ciphertext](#Ciphertext "wikilink").

### PMAC

The MAC portion of the OCB block cipher mode. It is a patented way of
turning a block cipher into a secure, parallelizable MAC.

### Precomputation attack

Any attack that involves precomputing significant amounts of data in
advance of opportunities to launch an attack. A dictionary attack is a
common precomputation attack.

### Predictive modelling

Predictive modelling is the process by which a model is created or
chosen to try to best predict the probability of an outcome. In many
cases the model is chosen on the basis of detection theory to try to
guess the probability of a signal given a set amount of input data, for
example given an email determining how likely that it is spam.

### Private key

In a public key cryptosystem, key material that is bound tightly to an
individual entity that must remain secret in order for there to be
secure communication.

### Privilege separation

A technique for trying to minimize the impact that a programming flaw
can have, where operations requiring privilege are separated out into a
small, independent component (hopefully audited with care). Generally,
the component is implemented as an independent process, and it spawns
off a non-privileged process to do most of the real work. The two
processes keep open a communication link, speaking a simple protocol.

### PRNG

See also: [Pseudo-random number
generator](#Pseudo-random_number_generator "wikilink").

### Pseudo-random number generator

An algorithm that produces statistically random outputs. Many PRNGs are
completely predictable, though their outputs are statistically random. A
pseudo-random number generator may be operated in a secure way if it is
regularly "seeded" with enough unpredictable entropy. Most popular
pseudo-random number generators are not secure.

See also: [Stream cipher](#Stream_cipher "wikilink") and
[\#Entropy](#Entropy "wikilink").

### Public key

In a public key cryptosystem, the key material that can be published
publicly without compromising the security of the system. Generally,
this material must be published; its authenticity must be determined
definitively.

### Public Key Infrastructure

A system that provides a means for establishing trust as to what
identity is associated with a public key. Some sort of Public Key
Infrastructure (PKI) is necessary to give reasonable assurance that one
is communicating securely with the proper party, even if that
infrastructure is ad hoc”

## Q

### QRLJacking

QRLJacking or Quick Response Code Login Jacking is a simple social
engineering attack vector capable of session hijacking affecting all
applications that rely on “Login with QR code” feature as a secure way
to login into accounts. In a simple way, In a nutshell victim scans the
attacker’s QR code results of session hijacking.

## R

### RA

See also: [Registration Authority](#Registration_Authority "wikilink").

### Race condition

A class of error in environments that are multi-threaded or otherwise
multi- tasking, where an operation is falsely assumed to be atomic. That
is, if two operations overlap instead of being done sequentially, there
is some risk of the resulting computation not being correct. There are
many cases where such a condition can be security critical.

See also: [TOCTOU problem](#TOCTOU_problem "wikilink").

### Randomness

Randomness has both mathematical and colloquial definitions.
Mathematically speaking, *random* outcomes are independent and equally
likely to occur. Colloquially, *random* usually implies being
unpredictable and/or unguessable. Random data is often tested with
statistical tests that search for evidence to disprove the assertion
that the data is random (e.g., patterns, cycles, bias). Data that is
statistically random can be completely predictable. Thus it is usually
insufficient to refer to "random data".

See also: [Entropy](#Entropy "wikilink").

### RC2

A block cipher with variable key sizes and 64-bit blocks.

### RC4

A widely used stream cipher that is relatively fast but with some
significant problems. One practical problem is that it has a weak key
setup algorithm, though this problem can be mitigated with care. Another
more theoretical problem is that RC4’s output is easy to distinguish
from a truly random stream of numbers. This problem indicates that RC4
is probably not a good long-term choice for data security.

### RC5

A block cipher that has several tunable parameters.

### Registration Authority

An organization that is responsible for validating the identity of
entities trying to obtain credentials in a Public Key Infrastructure.

See also: [Certification
Authority](#Certification_Authority "wikilink"), [Public Key
Infrastructure](#Public_Key_Infrastructure "wikilink").

### Rekeying

Changing a key in a cryptographic system.

### Related key attack

A class of cryptographic attack where one takes advantage of known
relationships between keys to expose information about the keys or the
messages those keys are protecting.

### Revocation

In the context of [Public Key
Infrastructure](#Public_Key_Infrastructure "wikilink"), the act of
voiding a digital certificate.

See also: [X.509 certificate](#X.509_certificate "wikilink").

### Risk

Risk is the possibility of a negative or undesirable occurance. There
are two independent parts of risk: [Impact](#Impact "wikilink") and
[Likelihood](#Likelihood "wikilink"). To reduce risk, one can reduce the
impact, reduce the likelihood, or both. Risk can also be accepted
(meaning that the full impact of the negative outcome will be borne by
the entity at risk). The impact and likelihood of a risk are usually
combined to create an estimate of its [Severity](#Severity "wikilink").

### RIPEMD-160

A cryptographic hash function that is well regarded. It has a 160-bit
output, and is a bit slower than SHA1.

### RMAC

A construction for making a Message Authentication Code out of a block
cipher. It is not generally secure in the way that OMAC is, and is
generally considered not worth using due to the existence of better
alternatives.

See also: [OMAC](#OMAC "wikilink").

### Rollback attack

An attack where one forces communicating parties to agree on an insecure
protocol version.

### Root certificate

A certificate that is intrinsically trusted by entities in a Public Key
Infrastructure — generally should be transported over a secure medium.
Root certificates belong to a Certification Authority and are used to
sign other certificates that are deemed to be valid. When a system tries
to establish the validity of a certificate, one of the first things that
should happen is that it should look for a chain of trust to a known,
trusted root certificate. That is, if the certificate to be validated is
not signed by a root, one checks the certificate(s) used to sign it to
determine if those were signed by a root cert. Lather, rinse, repeat.

See also: [Public Key
Infrastructure](#Public_Key_Infrastructure "wikilink").

### Round

In a block cipher, a group of operations applied as a unit that has an
inverse that undoes the operation. Most block ciphers define a round
operation and then apply that round operation numerous times — though
often applying a different key for each round, where the round key is
somehow derived from the base key.

### RSA

A popular public key algorithm for encryption and digital signatures
invented by Ron Rivest, Adi Shamir and Leonard Adleman. It is believed
that, if factoring large numbers is computationally unfeasible, then RSA
can be used securely in practice.

### RSASSA-PSS

A padding standard defined in PKCS \#1, used for padding data prior to
RSA signing operations.

## S

### S/Key

A popular [One-time password](#One-time_password "wikilink") system.

### S/MIME

A protocol for secure electronic mail standardized by the IETF. It
relies on standard X.509-based Public Key Infrastructure.

### SACL

System Access Control List. In Windows, the part of an ACL that
determines audit logging policy.

See also: [Access Control List](#Access_Control_List "wikilink"),
[DACL](#DACL "wikilink").

### Salt

Data that can be public but is used to prevent against precomputation
attacks.

See also: [Initialization vector](#Initialization_vector "wikilink"),
[Nonce](#Nonce "wikilink").

### SASL

The Simple Authentication and Security Layer, which is a method for
adding authentication services to network protocols somewhat
generically. It is also capable of providing key exchange in many
circumstances.

### Secret key

See also: [Symmetric key](#Symmetric_key "wikilink").

### Secure Socket Layer

A popular protocol for establishing secure channels over a reliable
transport, utilizing a standard X.509 Public Key Infrastructure for
authenticating machines. This protocol has evolved into the TLS
protocol, but the term SSL is often used to generically refer to both.

See also: [Transport Layer
Security](#Transport_Layer_Security "wikilink").

### SEED

128-bit Symmetric Block Cipher

### Seed

A value used to initialize a pseudo-random number generator.

See also: [Entropy](#Entropy "wikilink"), [Initialization
vector](#Initialization_vector "wikilink"), [Pseudo-random number
generator](#Pseudo-random_number_generator "wikilink").

### Self-signed certificate

A certificate signed by the private key associated with that
certificate. In an X.509 Public Key Infrastructure, all certificates
need to be signed. Since root certificates have no third-party signature
to establish their authenticity, they are used to sign themselves. In
such a case, trust in the certificate must be established by some other
means.

### Serpent

A modern block cipher with 128-bit blocks and variable-sized keys. A
finalist in the AES competition, Serpent has a higher security margin by
design than other candidates, and is a bit slower on typical 32-bit
hardware as a result.

See also: [AES](#AES "wikilink").

### Session Token

A value that represents a user's identity during their session.
Typically the user provides some form of credentials (e.g., username,
password, possibly a one-time token value from a second authentication
factor) and the server returns a token value that represents the user's
identity. In web applications, this token is often returned in a
[cookie](#Cookie "wikilink"). The client application includes the
session token with each request, enabling the server to associate each
request with the same user, role, and session.

### Severity

The severity of a [risk](#Risk "wikilink") combines its
[likelihood](#Likelihood "wikilink") and [impact](#Impact "wikilink")
into a single measure. This combination often follows the guidance of
[NIST Special
Publication 800-30](http://csrc.nist.gov/publications/nistpubs/800-30/sp800-30.pdf),
though some practitioners opt to use their own scale.

|             |                                      |             |                              |
| ----------- | ------------------------------------ | ----------- | ---------------------------- |
| colspan="2" |                                      | colspan="3" | [Impact](#Impact "wikilink") |
| colspan="2" |                                      | Low         | Medium                       |
| rowspan="4" | [Likelihood](#Likelihood "wikilink") |             |                              |
| High        | Low                                  | Medium      | High                         |
| Medium      | Low                                  | Medium      | Medium                       |
| Low         | Low                                  | Low         | Low                          |

### SHA-256

A cryptographic hash function from NIST with 256-bit message digests.

### SHA-384

SHA-512 with a truncated digest (as specified by NIST).

### SHA-512

A cryptographic hash function from NIST with 512-bit message digests.

### SHA1

A fairly fast, well regarded hash function with 160-bit digests that has
been standardized by the National Institute of Standards and Technology
(NIST).

### Shared secret

A value shared by parties that may wish to communicate, where the
secrecy of that value is an important component of secure
communications. Typically, a shared secret is either an encryption key,
a [MAC](#MAC "wikilink") key, or some value used to derive such keys.

See also: [Symmetric key](#Symmetric_key "wikilink").

### Shatter attack

A class of attack on the Windows event system. The Windows messaging
system is fundamentally fragile from a security perspective because it
allows for arbitrary processes to insert control events into the message
queue without sufficient mechanisms for authentication. Sometimes
messages can be used to trick other applications to execute malicious
code.

### Single sign-on

Single sign-on allows you to access all computing resources that you
should be able to reach by using a single set of authentication
credentials that are presented a single time per login session. Single
sign-on is a notion for improved usability of security systems that can
often increase the security exposure of a system significantly.

### Snooping attacks

Attacks where data is read off a network while in transit without
modifying or destroying the data.

### SNOW

A very fast stream cipher that is patent-free and seems to have a very
high security margin.

### SQL Injection

[SQL injection](SQL_injection "wikilink") is a security vulnerability
that occurs in the persistence/database layer of a web application. This
vulnerability is derived from the incorrect escaping of variables
embedded in SQL statements. It is in fact an instance of a more general
class of vulnerabilities based on poor input validation and bad design
that can occur whenever one programming or scripting language is
embedded inside another.

### SSL

See also: [Secure Socket Layer](#Secure_Socket_Layer "wikilink").

### Stack smashing

Overwriting a return address on the program execution stack by
exploiting a buffer overflow. Generally, the implication is that the
return address gets replaced with a pointer to malicious code.

See also: [Buffer overflow](#Buffer_overflow "wikilink").

### Station-to-station protocol

A simple variant of the Diffie-Hellman key exchange protocol that
provides key agreement and authenticates each party to the other. This
is done by adding digital signatures (which must be done carefully).

See also: [Diffie-Hellman key
exchange](#Diffie-Hellman_key_exchange "wikilink").

### Stream cipher

A pseudo-random number generator that is believed to be
cryptographically strong and always produces the same stream of output
given the same initial seed (i.e., key). Encrypting with a stream cipher
consists of combining the plaintext with the keystream, usually via XOR.

See also: [Pseudo-random number
generator](#Pseudo-random_number_generator "wikilink"), [Block
cipher](#Block_cipher "wikilink").

### Strong collision resistance

Strong collision resistance is a property that a hash function may have
(and a good cryptographic hash function will have), characterized by it
being computationally unfeasible to find two arbitrary inputs that yield
the same output.

See also: [Hash function](#Hash_function "wikilink"), [Weak collision
resistance](#Weak_collision_resistance "wikilink").

### Surreptitious forwarding

An attack on some public key cryptosystems where a malicious user
decrypts a digitally signed message and then encrypts the message using
someone else’s public key: giving the end receiver the impression that
the message was originally destined for them.

### Symmetric cryptography

Cryptography that makes use of shared secrets as opposed to public keys.

### Symmetric key

See also: [Shared secret](#Shared_secret "wikilink").

## T

### Tag

The result of applying a keyed message authentication code to a message.

See also: [Message Authentication
Code](#Message_Authentication_Code "wikilink").

### Tamper-proofing

See also: [Anti-tampering](#Anti-tampering "wikilink").

### Threat model

A representation of the system threats that are expected to be
reasonable. This includes denoting what kind of resources an attacker is
expected to have, in addition to what kinds of things the attacker may
be willing to try to do. Sometimes called an architectural security
assessment.

See also: [OWASP Threat Model
Project](https://www.owasp.org/index.php/OWASP_Threat_Model_Project)

### Time of check, time of use problem

See also: [TOCTOU problem](#TOCTOU_problem "wikilink").

### TMAC

A two-keyed variant of the CBC-MAC that overcomes the fundamental
limitation of that MAC.

See also: [Message Authentication
Code](#Message_Authentication_Code "wikilink"),
[CBC-MAC](#CBC-MAC "wikilink"), [OMAC](#OMAC "wikilink").

### TOCTOU problem

Time-of-check, time-of-use race condition. A type of race condition
between multiple processes on a file system. Generally what happens is
that a single program checks some sort of property on a file, and then
in subsequent instructions tries to use the resource if the check
succeeded. The problem is that — even if the use comes immediately after
the check — there is often some significant chance that a second process
can invalidate the check in a malicious way. For example, a privileged
program might check write privileges on a valid file, and the attacker
can then replace that file with a symbolic link to the system password
file.

See also: [Race condition](#Race_condition "wikilink").

### Transport Layer Security (TLS)

The successor to SSL, a protocol for establishing secure channels over a
reliable transport, using a standard X.509 Public Key Infrastructure for
authenticating machines. The protocol is standardized by the IETF.

See also: [Secure Socket Layer](#Secure_Socket_Layer "wikilink").

### Triple DES

A variant of the original Data Encryption Standard that doubles the
effective security. Often abbreviated to 3DES. The security level of
3DES is still considered to be very high, but there are faster block
ciphers that provide comparable levels of security — such as AES.

See also: [Data Encryption
Standard](#Data_Encryption_Standard "wikilink").

### Trojan

See also: [Backdoor](#Backdoor "wikilink").

### Trojan Horse

See also: [Backdoor](#Backdoor "wikilink").

### Trusted third party

An entity in a system to whom entities must extend some implicit trust.
For example, in a typical Public Key Infrastructure, the Certification
Authority constitutes a trusted third party.

### Twofish

A modern block cipher with 128-bit blocks and variable-sized keys. A
finalist in the AES competition; it is an evolution of the Blowfish
cipher.

See also: [AES](#AES "wikilink"), [Blowfish](#Blowfish "wikilink").

## U

### UMAC

A secure MAC based on a set of universal hash functions that is
extremely fast in software but so complex that there has never been a
validated implementation.

See also: [Universal hash
function](#Universal_hash_function "wikilink").

### Universal hash function

A keyed hash function that has ideal hash properties. In practice, the
only practical functions of this nature are really "almost universal"
hash functions, meaning they come very close to being ideal. Universal
and near-universal hash functions are not cryptographically secure when
used naively for message authentication but can be adapted to be secure
for this purpose easily.

See also: [Cryptographic hash
function](#Cryptographic_hash_function "wikilink"), [Hash
function](#Hash_function "wikilink"), [One-way hash
function](#One-way_hash_function "wikilink").

## V

### Validation

The act of determining that data is sound. In security, generally used
in the context of validating input.

### VMAC

Variant of UMAC optimized for 64-bit architectures.

See also: [UMAC](#UMAC "wikilink").

## W

### Weak collision resistance

A property that a hash function may have (and a good cryptographic hash
function will have), characterized by it being unfeasible to find a
second input that produces the same output as a known input.

See also: [Hash function](#Hash_function "wikilink"), [Strong collision
resistance](#Strong_collision_resistance "wikilink").

### Whitelist

When performing input validation, the set of items that, if matched,
results in the input being accepted as valid. If there is no match to
the whitelist, then the input is considered invalid. That is, a
whitelist uses a "default deny" policy.

See also: [Blacklist](#Blacklist "wikilink"), [Default
deny](#Default_deny "wikilink").

### Window of vulnerability

The period of time in which a vulnerability can possibly be exploited.

### [What are web applications?](What_are_web_applications? "wikilink")

## X

### X.509 certificate

A digital certificate that complies with the X.509 standard (produced by
ANSI).

### XCBC-MAC

A three-key variant of the CBC-MAC that overcomes the fundamental
limitation of that MAC.

See also: [Message Authentication
Code](#Message_Authentication_Code "wikilink"),
[CBC-MAC](#CBC-MAC "wikilink"), [OMAC](#OMAC "wikilink").

### XMACC

A patented parallelizable Message Authentication Code.

### XSS

See also: [Cross-site scripting](#Cross-site_scripting "wikilink").

## Y

## Z

[Category:Glossary](Category:Glossary "wikilink")