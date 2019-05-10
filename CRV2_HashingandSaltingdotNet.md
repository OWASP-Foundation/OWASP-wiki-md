# Introduction

A cryptographic hash algorithm; also called a hash "function" is a
computer algorithm designed to provide a random mapping from an
arbitrary block of data (string of binary data) and return a fixed-size
bit string known as a “message digest” and achieve certain security.
Cryptographic hashing functions are used to create digital signatures,
message authentication codes (MACs), other forms of authentication and
many other security applications in the information infrastructure. They
are also used to store user passwords in databases instead of storing
the password in clear text and help prevent data leakage in session
management for web applications. The actual algorithm used to create a
cryptology function varies per implementation (SHA-256, SHA-512, etc.)

The code reviewer needs to be aware of three main things when reviewing
code that uses cryptographic hashing functions.

  - ''Legality of the cryptographic hashing functions if the source code
    is being exported to another country.

<!-- end list -->

  - ''The life cycle of the cryptographic hashing function being used.

<!-- end list -->

  - ''Basic programming of cryptographic hashing functions.

## Legal

In the United States in 2000, the department of Commerce Bureau of
Export revised encryption export regulations. The results of the new
export regulations it that the regulations have been greatly relaxed.
However if the code is to be exported outside of the source country
current export laws for the export and import counties should be
reviewed for compliance.

Case in point is if the entire message is hashed instead of a digital
signature of the of message the National Security Agency (NSA) considers
this a quasi-encryption and State controls would apply.

It is always a valid choice to seek legal advice within the organization
that the code review is being done to ensure legal compliance.

## Lifecycle

With security nothing is secure forever. This is especially true with
cryptographic hashing functions. Some hashing algorithms such as Windows
LanMan hashes are considered completely broken. Others like MD5, while
currently considered safe for password hash usage, have known issues
like collision attacks (note that collision attacks do not affect
password hashes). The code reviewer needs to understand the weaknesses
of obsolete hashing functions as well as the current best practices for
the choice of cryptographic algorithms.

## Programming/Vulnerabilities

The most common programmatic issue with hashing is not using a salt
value or if using a salt the salt value is too short and or the same
salt value is used in multiple hashes. The purpose of a salt is to make
it harder for an attacker to perform pre-computed hashing attack (e.g.,
using rainbow tables) but other benefits of a salt can include making it
difficult for an attacker to perform even password guessing attacks by
obsfucating the hashed value.

## Salt

One way to generate a secure salt value is using a pseudo-random number
generator. Note that a salt value does not need to possess the quality
of a cryptographically secure randomness. Best practices is to use a
cryptographically function to create the salt, salt value should be
created for each hash value, and a minimum value of 128 bits. The bits
are not costly so don't save a few bits thinking you gain something back
in performance instead use a value of 256-bit salt value. It is highly
recommended.

### .Net Salt

`   private int minSaltSize = 8;`
`   private int maxSaltSize = 24;`
`   private int saltSize; `
` `
`   private byte[] GetSalt(string input) {`
`           byte[] data;`
`           byte[] saltBytes;`
`           RNGCryptoServiceProvider rng = new RNGCryptoServiceProvider();`
`           saltBytes = new byte[saltSize];`
`           rng.GetNonZeroBytes(saltBytes);`
`           data = Encoding.UTF8.GetBytes(input);`
`           byte[] dataWithSaltBytes =`
`               new byte[data.Length + saltBytes.Length];`
`           for (int i = 0; i < data.Length; i++)`
`               dataWithSaltBytes[i] = data[i];`
`           for (int i = 0; i < saltBytes.Length; i++)`
`               dataWithSaltBytes[data.Length + i] = saltBytes[i];`
`           return dataWithSaltBytes;`
`       }`

This method uses an agile approach to calling a hash function. It is
explained below.

`    private string computeHashWithSalt(HashAlgorithm myHash, string input) {`
`           byte[] data;`
`           data = myHash.ComputeHash(GetSalt(input));`
`           sb = new StringBuilder();`
`           for (int i = 0; i < data.Length; i++) {`
`               sb.Append(data[i].ToString("x2"));`
`           }`
`           return sb.ToString();`
`       }`

## Microsoft .Net Notes on Hashing

Microsoft does not recommend using MD5 or SHA-1. With .Net 3.5 and above
Microsoft supports the Suite B set of cryptographic algorithms published
by the National Security Agency (NSA).

  - ''Java – java.security.SecureRandom
  - ''PHP - ???
  - ''Ruby - ???
  - ''Perl - ???
  - ''C++ none managed code on CLR or none windows ????
  - ''Javascript ?????

The salt value does not need to be secret and can be stored along with
the hash value. Some may use a combination of account details (username,
user full name, ID, creation date, etc.) as the salt for hash to further
obsfucate the hash computation: for example salt = (username |lastname
|firstname |ID |generated_salt_value).

## Best Practices

Industry leading Cryptographer’s are advising that MD5 and SHA-1 should
not be used for any applications. The United State FEDERAL INFORMATION
PROCESSING STANDARDS PUBLICATION (FIPS) specifies seven cryptographic
hash algorithms — SHA-1, SHA-224, SHA-256, SHA-384, SHA-512,
SHA-512/224, and SHA-512/256 are approved for federal use. The code
reviewer should consider this standard because the FIPS is also widely
adopted by the information technology industry.

The code reviewer should raise a red flag if MD5 and SHA-1 are used and
a risk assessment be done to understand why these functions would be
used instead of other better-suited hash functions. FIPS does allow that
MD5 can be used only when used as part of an approved key transport
scheme (e.g. SSL v3.1) where no security is provided by the algorithm.

FIPS disapproves the following functions DES; MD51; RC4; Blowfish;
Diffie-Hellman2; Diffie-Hellman3 (key agreement); EC Diffie-Hellman2
(key agreement); AES4 (non-compliant); Diffie-Hellman5 (key agreement);
EC Diffie-Hellman4 (vendor affirmed); RSA4 (key agreement); RSA2 (key
wrapping).

## .Net Agile Code example for hashing

App Code File: <add key="HashMethod" value="SHA512"/>

C\# Code:

`  1:  preferredHash = HashAlgorithm.Create((string)ConfigurationManager.AppSettings["HashMethod"]);`
`  2:   `
`  3:  hash = computeHash(preferredHash, testString);`
`  4:   `
`  5:  private string computeHash(HashAlgorithm myHash, string input) {`
`  6:       byte[] data;`
`  7:       data = myHash.ComputeHash(Encoding.UTF8.GetBytes(input));`
`  8:       sb = new StringBuilder();`
`  9:       for (int i = 0; i < data.Length; i++) {`
` 10:           sb.Append(data[i].ToString("x2"));`
` 11:       }`
` 12:      return sb.ToString();`
` 13:  }`

 Line 1 let's us get our hashing algorithm we are going to use from the
config file. If we use the machine config file our implementation would
be server wide instead of application specific. Line 3 allows us to use
the config value and set it according as our choice of hashing function.
ComputHash can be SHA-256 or SHA-512.

The drawback to this method is key size. I would suggest of giving
yourself twice the size of the largest key of hashing algorithm you
could possible use to store hash values. This means we need a varchar of
1024 if we are going to store our hash value in the database.

## Afterword

Lastly, never accept in a code review an algorithm created by the
programmer for hashing or copy a hashing function taken from the
Internet. Always use cryptographic functions that are provided by the
language framework the code is written in. These functions are well
vetted and well tested by experience cryptographers.

# References:

  - ''<http://valerieaurora.org/hash.html> (Lifetimes of cryptographic
    hash functions)
  - ''<http://docs.oracle.com/javase/6/docs/api/java/security/SecureRandom.html>
  - ''<http://msdn.microsoft.com/en-us/library/system.security.cryptography.rngcryptoserviceprovider.aspx>
  - ''<http://csrc.nist.gov/publications/fips/fips180-4/fips-180-4.pdf>
  - ''Ferguson and Schneier (2003) Practical Cryptography (see Chapter
    6; section 6.2 Real Hash Functions)