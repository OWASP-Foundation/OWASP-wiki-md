<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>



## Introduction

This page helps Java developers hash passwords safely. We rely on
OWASP's [Password Storage Cheat
Sheet](Password_Storage_Cheat_Sheet "wikilink") to explain hashing best
practice and theory.

## Java Example

`   public static byte[] hashPassword( final char[] password, final byte[] salt, final int iterations, final int keyLength ) {`
` `
`       try {`
`           SecretKeyFactory skf = SecretKeyFactory.getInstance( "PBKDF2WithHmacSHA512" );`
`           PBEKeySpec spec = new PBEKeySpec( password, salt, iterations, keyLength );`
`           SecretKey key = skf.generateSecret( spec );`
`           byte[] res = key.getEncoded( );`
`           return res;`
` `
`       } catch( NoSuchAlgorithmException | InvalidKeySpecException e ) {`
`           throw new RuntimeException( e );`
`       }`
`   }`

## Guidance

The password and salt arguments are arrays, as is the result of the
hashPassword function. Sensitive data should be *cleared* after you have
used it (set the array elements to zero).

The example uses a Password Based Key Derivation Function 2 (PBKDF2), as
discussed in the [Password Storage Cheat
Sheet](Password_Storage_Cheat_Sheet "wikilink").

The *salt* argument should be random data and vary for each user. It
should be at least 32 bytes long. Remember to save the salt with the
hashed password\!

The *iterations* argument specifies how many times the PBKDF2 executes
its underlying algorithm. A higher value is safer. You need to
experiment on hardware equivalent to your production systems. As a
starting point, find a value that requires one half second to execute.
Scaling to huge number of users is beyond the scope of this document.
Remember to save the value of iterations with the hashed password\!

A keyLength of 256 is safe.

If the example code generates a NoSuchAlgorithmException, replace
PBKDF2WithHmacSHA512 with PBKDF2WithHmacSHA1. Both are adequate to the
task but you may be criticized when people see "SHA1" in the
specification (SHA1 can be unsafe outside of the context of PBKDF2).

The SecretKeyFactory and PBEKeySpec classes have been part of Java SE
since version 1.4.

## Reference

See *Iron-Clad Java: Building Secure Web Applications* by Manico and
Detlefsen, 2015, Oracle Press.

[Category:Java](Category:Java "wikilink")