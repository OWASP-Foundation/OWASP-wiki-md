## Description

Most web applications have a need to store sensitive information, either
in a database or on a file system somewhere. The information might be
passwords, credit card numbers, account records, or proprietary
information. Frequently, encryption techniques are used to protect this
sensitive information. While encryption has become relatively easy to
implement and use, developers still frequently make mistakes while
integrating it into a web application. Developers may overestimate the
protection gained by using encryption and not be as careful in securing
other aspects of the site.

A few areas where mistakes are commonly made include:

  - Failure to encrypt critical data
  - Insecure storage of keys, certificates, and passwords
  - Improper storage of secrets in memory
  - Poor sources of randomness
  - Poor choice of algorithm
  - Attempting to invent a new encryption algorithm
  - Failure to include support for encryption key changes and other
    required maintenance procedures

The impact of these weaknesses can be devastating to the security of a
website. Encryption is generally used to protect a site’s most sensitive
assets, which may be totally compromised by a weakness.

## Environments Affected

Most web application environments include some form of cryptographic
support. In the rare case that such support is not already available,
there are a wide variety of third-party products that can be added. Only
web sites that use encryption to protect information in storage or
transit are susceptible to these attacks. Note that this section does
not cover the use of SSL, which is covered in A10 Insecure Configuration
Management. This section deals only with programmatic encryption of
application layer data.

## Examples and References

  - [OWASP Guide](:Category:OWASP_Guide_Project "wikilink") to Building
    Secure Web Applications and Web Services
  - Bruce Schneier, “Applied Cryptography”, 2nd edition, John Wiley &
    Sons, 1995

## How to Determine If You Are Vulnerable

Discovering cryptographic flaws without access to the source code can be
extremely time consuming. However, it is possible to examine tokens,
session IDs, cookies and other credentials to see if they are obviously
not random. All the traditional cryptanalysis approaches can be used to
attempt to uncover how a web site is using cryptographic functions.

By far the easiest approach is to review the code to see how the
cryptographic functions are implemented. A careful review of the
structure, quality, and implementation of the cryptographic modules
should be performed. The reviewer should have a strong background in the
use of cryptography and common flaws. The review should also cover how
keys, passwords, and other secrets are stored, protected, loaded,
processed, and cleared from memory.

## How to Protect Yourself

The easiest way to protect against cryptographic flaws is to minimize
the use of encryption and only keep information that is absolutely
necessary. For example, rather than encrypting credit card numbers and
storing them, simply require users to re-enter the numbers. Also,
instead of storing encrypted passwords, use a recent one-way hash
function (such as SHA-256) to hash the passwords.

If cryptography must be used, choose a library that has been exposed to
public scrutiny and make sure that there are no open vulnerabilities.
Encapsulate the cryptographic functions that are used and review the
code carefully. Be sure that secrets, such as keys, certificates, and
passwords, are stored securely. To make it difficult for an attacker,
the master secret should be split into at least two locations and
assembled at runtime. Such locations might include a configuration file,
an external server, or within the code itself.

__NOEDITSECTION__