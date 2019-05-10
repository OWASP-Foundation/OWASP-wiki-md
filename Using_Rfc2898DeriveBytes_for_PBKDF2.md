Password storage is a large topic in application security. If a security
failure occurs, and the database is stolen, the passwords of the users
are some of the most important data stored. Given the state of
contemporary authentication, they do not need to be stored in plain
text, so they should not. A hashed representation of the password, using
a contemporary encryption algorithm and process, is the accepted way to
store a password in today’s systems. More information can be found in
the Password Storage Cheat
Sheet[1](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet).

# Common .NET password storage

In .NET, the SQL
Membership\[<http://msdn.microsoft.com/en-us/library/6e9y4s5t(v=vs.100>).aspx\]
or ASP.NET
membership\[<http://msdn.microsoft.com/en-us/library/ms731049(v=vs.110>).aspx\]
patterns are often used for identity. In a best case scenario passwords
aren’t stored by the local application or a well-known and trusted
system is used such as AD, Facebook, or ASP.NET Identity. In each of
these cases, the password storage is either handled by the subsystem, or
not handled by the application at all.

Sometimes, however, there is no choice but to store the password in the
application using home grown code. When this is the case, it is upon the
software developer to select and use the correct hashing algorithm and
process for password storage. Hashing is the process of deriving a
unique, repeatable value form a text input and salt. This prevents the
storage of the password itself, thus protecting the password if the
database is stolen.

Hashes create unique values that cannot be reversed into their source
values, however, brute force could potentially lead an attacker to the
source values. As such, a key derivation function is often used to
increase the work factor needed to create the representative value.
Often this key derivitation function is PBKDF2, or the Password-Based
Key Derivation Function 2[2](http://en.wikipedia.org/wiki/PBKDF2).

# PBKDF2 basics

PBKDF2 uses a pseudorandom function and a configurable number of
iterations to derive a cryptographic key from a password. Because this
process is difficult to reverse (similar to a cryptographic hash
function) but can also be configured to be slow to compute, key
derivation functions are ideally suited for password hashing use cases.

The details of PBKDF2 are openly published, and the goal of this
document is not to replicate that information. Generally speaking, the
function is one that accepts a pseudorandom function (such as SHA1), a
salt, the number of iterations, the length of the resultant hash, and
the text to be hashed. The goal is one of ‘key stretching’, making the
overall process of generating or reversing the hash harder. The .NET
Framework can abstract the details of the algorithm from the developer.

# Implementing PBKDF2 in .NET

Microsoft’s .NET platform supports PBKDF2 out of the box.
Rfc2898DeriveBytes allows a developer to generate a key for a value
using PDKDF2 without implementing the algorithm. Using a number of
iterations and a salt, a developer can easily implement the key
stretching hash then store that data in the database. During
registration, rather than storing the password entered by the user, you
should store the password and salt. Guids provide a very strong salt, as
while they are not cryptographically random, they are guaranteed
globally unique. Rfc2898DeriveBytes will generate it's own salt, which
is retrievable before save, as we have done here.
Rfc2898DeriveBytes\[<http://msdn.microsoft.com/en-us/library/system.security.cryptography.rfc2898derivebytes(v=vs.110>).aspx\]
will generate a hash and return the derived key with the requested
number of iterations. You need to store them both.

Each base hash function sized block of output from PBKDF2 is iterated
independently of each other. Using PBKDF2 for password storage, one
should **never** output more bits than the base hash function's size.
With PBKDF2-SHA1 this is 160 bits or 20 bytes. Output more bits doesn't
make the hash more secure, but it costs the defender a lot more time
while not costing the attacker. An attacker will just compare the first
hash function sized output saving them the time to generate the reset of
the PBKDF2 output.

Here is an example of using the System.Security.Cryptography namespace
in a simple method. It returns the salt and key in a pipe delimited
string.

<code>

` public static string HashPassword(string password)`
`   {`
`       // Generate the hash, with an automatic 32 byte salt`
`       Rfc2898DeriveBytes rfc2898DeriveBytes = new Rfc2898DeriveBytes(password, 32);`
`       rfc2898DeriveBytes.IterationCount = 10000;`
`       byte[] hash = rfc2898DeriveBytes.GetBytes(20);`
`       byte[] salt = rfc2898DeriveBytes.Salt;`
`       //Return the salt and the hash`
`       return Convert.ToBase64String(salt) + "|" + Convert.ToBase64String(hash);`
`   }`

</code>

Another note is that related to the number of iterations. In the
Password Storage Cheat Sheet, it is recommended to make the password
generation process as slow as possible without negatively affecting the
user experience. Here, we have set the iterations to 10,000 and should
review that number every year.

# Using the hash on login

When a user later logs in, rather than using the password to confirm
authentication, you can use the hashing function to generate a hash with
the stored salt rather than a generated salt. Then compare the hash with
the stored hash.

# Limitations

The built-in .NET implementation of Rfc2898DeriveBytes limits the user
to one psudorandom function - HMAC with SHA-1. This is acceptable in
most scenarios today, but in the future, a more complex hashing function
may be required.

The .NET Compact Framework does not support Rfc2898DeriveBytes.

# References

  - [Password Storage Cheat
    Sheet](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet)
  - \[<http://msdn.microsoft.com/en-us/library/6e9y4s5t(v=vs.100>).aspx
    SQL Membership\]
  - \[<http://msdn.microsoft.com/en-us/library/ms731049(v=vs.110>).aspx
    ASP.NET Membership\]
  - \[<http://msdn.microsoft.com/en-us/library/system.security.cryptography.rfc2898derivebytes(v=vs.110>).aspx
    Rfc2898DeriveBytes\]
  - [Salted Password
    Hashing](https://crackstation.net/hashing-security.htm)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")