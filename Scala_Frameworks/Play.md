## Play Framework

The Playframework has excellent documentation on many topics, however
when it touches security, this section is quite limited regarding how to
do secure implementations. Documentation refers to the latest
version.For more information please check:
<https://www.playframework.com/documentation/2.6.x/Home>

The following sections contain some important security aspects to be
considered while implementing certain configurations and features.

### Sensitive information in Configuration Files

Every Scala project will contain configuration files that can contain
sensitive information such as:

  - Passwords in clear text
  - Path to Keystores
  - Passwords from Keystores

Programers should avoid configuring clear text passwords in
Application.conf files, for that purpose, encryption is necessary

### Configuration Keystore

At some point, especially for projects requiring secure communications
(HTTPS), the implementation and use of Keystore is required. The
Playframework provides some examples of implementing
[this](https://www.playframework.com/documentation/2.6.x/ConfiguringHttps#SSL-Certificates-from-a-keystore)
unfortunately, there is no further information on how to create this
information securely. The developer must also keep in mind that the
default configuration is quite insecure and certificates generated are
self-signed, becoming unsuitable for real applications.

Developers should revise the following configuration information:

**play.server.https.keyStore.path** - The path to the keystore
containing the private key and certificate, if not provided generates a
keystore for you

*Security issue*: Keys must be secure guarded, allowing the 'generated'
one, can allow an attacker obtain such information if code is
compromised

More information refer to: [Cryptographic Storage Cheat Sheet\#Rule -
Protect keys in a key
vault](Cryptographic_Storage_Cheat_Sheet "wikilink")

**play.server.https.keyStore.password** - The password, defaults to a
blank password

*Security issue*: Blank passwords are a 'no-go', therefore, it is
essential to change this information. Again, do not create a
'clear-text' passwords, but make sure you use an environment variable
for this purpose, or encrypt properly if you place one in the
configuration file

**play.server.https.keyStore.algorithm** - The key store algorithm,
defaults to the platforms default algorithm

*Security issue*: Developer should check what is the 'defaults' being
used and make sure the algorithm in question is secure as recommended by
NIST guidelines

#### Encryption Keystore Password

Using Environment in configuration files instead of clear text
passwords, example

`password=${?MAIL_PASSWD}`

Following best practices, if you need to store a password, make sure
that

  - It's hashed
  - Use salt
  - Implement a slow algorithm against brute force such as Bcrypt The
    following example uses Bcrypt library for this purpose

`def PasswordHash( name:String, pwd:String, version:Int = 1 ) : String = {   if( version == 2 && false )                                                               {     // ANY CHANGES SHOULD BE MADE AS A NEW VERSION AND ADDED HERE     ""   }                                                                                    else   {     import org.mindrot.jbcrypt.BCrypt      // jbcrypt-0.3m.jar                                                                                             // Salt will be incorporated in the password hash                                                                                                                    val salt = BCrypt.gensalt(12) // Default is 10, or 2**10 rounds.  More rounds is slower.                                                                    BCrypt.hashpw( (name + pwd), salt )   } }                                                                                                                           def VerifyPassword( name:String, pwd:String, hash:String, version:Int = 1 ) : Boolean = {   if( version == 1 )                                                       {     import org.mindrot.jbcrypt.BCrypt                                                                                                                              // jbcrypt-0.3m.jar                                                                                                                                         BCrypt.checkpw( (name + pwd), hash )   }                                                                                                                             else                                                                                                                                                                false }`

### Enabling SSL in Production

[Play
recommends](https://www.playframework.com/documentation/2.3.x/ConfiguringHttps)
to use the latest JDK , at the moment of writing is 1.8, which provides
a number of new features that make JSSE feasible as a TLS termination
layer.

### Security Features

The Play framework contains some essential security features, the
following is a guide map to them. This is valid for version 2.6.x

  - Input Validation
  - CRSF Token
  - [Security
    Headers](https://www.playframework.com/documentation/2.6.x/ScalaCsrf#Plays-CSRF-protection)

Extending Security

There are different frameworks supporting Play with granular security
features. For more information, please check the [Scala Security
Frameworks](:Category:Scala "wikilink")