__TOC__

## Introduction

There are two types of cryptography in this world: cryptography that
will stop your kid sister from reading your files, and cryptography that
will stop major governments from reading your files \[1\]. Developers
are at the forefront of deciding which category a particular application
resides in. Cryptography provides for security of data at rest (via
encryption), enforcement of data integrity (via hashing/digesting), and
non-repudiation of data (via signing). As a result, the coding in a
secure manner of any of the above cryptographic processes within source
code must conform in principle to the use of standard cryptographically
secure algorithms with strong key sizes.

The use of non-standard cryptographic algorithms, custom implementation
of cryptography (standard & non-standard) algorithms, use of standard
algorithms which are cryptographically insecure (e.g. DES), and the
implementation of insecure keys can weaken the overall security posture
of any application. Implementation of the aforementioned methods enables
the use of known cryptanalytic tools and techniques to decrypt sensitive
data.

## Related Security Activities

[Guide to Cryptography](Guide_to_Cryptography "wikilink")
[Using the Java Cryptographic
Extensions](Using_the_Java_Cryptographic_Extensions "wikilink")

## Use of Standard Cryptographic Libraries

As a general recommendation, there is strong reasoning behind not
creating custom cryptographic libraries and algorithms. There is a huge
distinction between groups, organizations, and individuals developing
cryptographic algorithms and those that implement cryptography either in
software or in hardware.

### .NET and C/C++ (Win32)

For .NET code, class libraries and implementations within
System.Security.Cryptography should be used \[2\]. This namespace within
.NET aims to provide a number of wrappers that do not require proficient
knowledge of cryptography in order to use it \[3\].

For C/C++ code running on Win32 platforms, the CryptoAPI is recommended
\[2\]. This has been an integral component for any Visual C++
developer's toolkit prior to the release of the latest replacement with
Windows Vista. The CryptoAPI today offers an original benchmark for what
will become legacy applications.

### Classic ASP

Classic ASP pages do not have direct access to cryptographic functions,
so the only way is to create COM wrappers in Visual C++ or Visual Basic,
implementing calls to DPAPI or CryptoAPI, then call it from ASP pages
using the **Server.CreateObject** method.

### Java

The Java Cryptography Extension (JCE) \[5\] was introduced as an
optional package in the Java 2 SDK and has since been included with J2SE
1.4 and later versions. When implementing code in this language, the use
of a library that is a provider of the JCE is recommended. Sun provides
a list of companies that act as Cryptographic Service Providers and/or
offer clean room implementations of the Java Cryptography Extension
\[6\].

## Vulnerable Patterns Examples for Cryptography

A secure way to implement robust encryption mechanisms within source
code is by implementing FIPS\[7\] compliant algorithms with the use of
the Microsoft Data Protection API (DPAPI)\[4\] or the Java Cryptography
Extension (JCE)\[5\]. The following should be identified when
establishing your cryptographic code strategy:

  - Standard Algorithms
  - Strong Algorithms
  - Strong Key Sizes

Additionally, all sensitive data that the application handles should be
identified and encryption should be enforced. This includes user
sensitive data, configuration data, etc. Specifically, presence of the
following identifies issues with Cryptographic Code:

**.NET**
Check for examples for Cryptography in the MSDN Library [Security
Practices: .NET Framework 2.0 Security Practices at a
Glance](http://msdn.microsoft.com/en-us/library/aa480479.aspx#pagpractices0002_cryptography)

1.  Check that the Data Protection API (DPAPI) is being used
2.  Verify no proprietary algorithms are being used
3.  Check that RNGCryptoServiceProvider is used for PRNG
4.  Verify key length is at least 128 bits

**Classic ASP**
Perform all of these checks on the COM wrapper as ASP does not have
direct access to cryptographic functions

1.  Check that the Data Protection API (DPAPI) or CryptoAPI is being
    used into COM object
2.  Verify no proprietary algorithms are being used
3.  Check that RNGCryptoServiceProvider is used for PRNG
4.  Verify key length is at least 128 bits

**Java**

1.  Check that the Java Cryptography Extension (JCE) is being used
2.  Verify no proprietary algorithms are being used
3.  Check that SecureRandom (or similar) is used for PRNG
4.  Verify key length is at least 128 bits

**Bad Practice: Use of Insecure Cryptographic Algorithms**

The following algorithms are cryptographically insecure: DES and SHA-0.
Below outlines a cryptographic implementation of DES (available per
[Using the Java Cryptographic
Extensions](Using_the_Java_Cryptographic_Extensions "wikilink")):

    package org.owasp.crypto;

    import javax.crypto.KeyGenerator;
    import javax.crypto.SecretKey;
    import javax.crypto.Cipher;

    import java.security.NoSuchAlgorithmException;
    import java.security.InvalidKeyException;
    import java.security.InvalidAlgorithmParameterException;
    import javax.crypto.NoSuchPaddingException;
    import javax.crypto.BadPaddingException;
    import javax.crypto.IllegalBlockSizeException;

    import sun.misc.BASE64Encoder;

    /**
     * @author Joe Prasanna Kumar
     * This program provides the following cryptographic functionalities
     * 1. Encryption using DES
     * 2. Decryption using DES
     *
     * The following modes of DES encryption are supported by SUNJce provider
     * 1. ECB (Electronic code Book) - Every plaintext block is encrypted separately
     * 2. CBC (Cipher Block Chaining) - Every plaintext block is XORed with the previous ciphertext block
     * 3. PCBC (Propogating Cipher Block Chaining) -
     * 4. CFB (Cipher Feedback Mode) - The previous ciphertext block is encrypted and this enciphered block is XORed with the plaintext block to produce the corresponding ciphertext block
     * 5. OFB (Output Feedback Mode) -
     *
     *  High Level Algorithm :
     * 1. Generate a DES key
     * 2. Create the Cipher (Specify the Mode and Padding)
     * 3. To Encrypt : Initialize the Cipher for Encryption
     * 4. To Decrypt : Initialize the Cipher for Decryption
     *
     * Need for Padding :
     * Block ciphers operates on data blocks on fixed size n.
     * Since the data to be encrypted might not always be a multiple of n, the remainder of the bits are padded.
     * PKCS#5 Padding is what will be used in this program
     *
     */

    public class DES {
        public static void main(String[] args) {

            String strDataToEncrypt = new String();
            String strCipherText = new String();
            String strDecryptedText = new String();

            try{
            /**
             *  Step 1. Generate a DES key using KeyGenerator
             *
             */
            KeyGenerator keyGen = KeyGenerator.getInstance("DES");
            SecretKey secretKey = keyGen.generateKey();

            /**
             *  Step2. Create a Cipher by specifying the following parameters
             *          a. Algorithm name - here it is DES
             *          b. Mode - here it is CBC
             *          c. Padding - PKCS5Padding
             */

            Cipher desCipher = Cipher.getInstance("DES/CBC/PKCS5Padding");

            /**
             *  Step 3. Initialize the Cipher for Encryption
             */

            desCipher.init(Cipher.ENCRYPT_MODE,secretKey);

            /**
             *  Step 4. Encrypt the Data
             *          1. Declare / Initialize the Data. Here the data is of type String
             *          2. Convert the Input Text to Bytes
             *          3. Encrypt the bytes using doFinal method
             */
            strDataToEncrypt = "Hello World of Encryption using DES ";
            byte[] byteDataToEncrypt = strDataToEncrypt.getBytes();
            byte[] byteCipherText = desCipher.doFinal(byteDataToEncrypt);
            strCipherText = new BASE64Encoder().encode(byteCipherText);
            System.out.println("Cipher Text generated using DES with CBC mode and PKCS5 Padding is " +strCipherText);

            /**
             *  Step 5. Decrypt the Data
             *          1. Initialize the Cipher for Decryption
             *          2. Decrypt the cipher bytes using doFinal method
             */
            desCipher.init(Cipher.DECRYPT_MODE,secretKey,desCipher.getParameters());
             //desCipher.init(Cipher.DECRYPT_MODE,secretKey);
            byte[] byteDecryptedText = desCipher.doFinal(byteCipherText);
            strDecryptedText = new String(byteDecryptedText);
            System.out.println(" Decrypted Text message is " +strDecryptedText);
            }

            catch (NoSuchAlgorithmException noSuchAlgo)
            {
                System.out.println(" No Such Algorithm exists " + noSuchAlgo);
            }

                catch (NoSuchPaddingException noSuchPad)
                {
                    System.out.println(" No Such Padding exists " + noSuchPad);
                }

                    catch (InvalidKeyException invalidKey)
                    {
                        System.out.println(" Invalid Key " + invalidKey);
                    }

                    catch (BadPaddingException badPadding)
                    {
                        System.out.println(" Bad Padding " + badPadding);
                    }

                    catch (IllegalBlockSizeException illegalBlockSize)
                    {
                        System.out.println(" Illegal Block Size " + illegalBlockSize);
                    }

                    catch (InvalidAlgorithmParameterException invalidParam)
                    {
                        System.out.println(" Invalid Parameter " + invalidParam);
                    }
        }

    }

Additionally, SHA-1 and MD5 should be avoided in new applications moving
forward.

## Good Patterns Examples for Cryptography

**Good Practice: Use Strong Entropy**
The following source code outlines secure key generation per use of
strong entropy
(available per [Using the Java Cryptographic
Extensions](Using_the_Java_Cryptographic_Extensions "wikilink")):

    package org.owasp.java.crypto;

    import java.security.SecureRandom;
    import java.security.NoSuchAlgorithmException;

    import sun.misc.BASE64Encoder;

    /**
     * @author Joe Prasanna Kumar
     * This program provides the functionality for Generating a Secure Random Number.
     *
     * There are 2 ways to generate a  Random number through SecureRandom.
     * 1. By calling nextBytes method to generate Random Bytes
     * 2. Using setSeed(byte[]) to reseed a Random object
     *
     */


    public class SecureRandomGen {

        /**
         * @param args
         */
        public static void main(String[] args) {
            try {
                // Initialize a secure random number generator
                SecureRandom secureRandom = SecureRandom.getInstance("SHA1PRNG");

                // Method 1 - Calling nextBytes method to generate Random Bytes
                byte[] bytes = new byte[512];
                secureRandom.nextBytes(bytes);

                // Printing the SecureRandom number by calling secureRandom.nextDouble()
                System.out.println(" Secure Random # generated by calling nextBytes() is " + secureRandom.nextDouble());

                // Method 2 - Using setSeed(byte[]) to reseed a Random object
                int seedByteCount = 10;
                byte[] seed = secureRandom.generateSeed(seedByteCount);

                // TBR System.out.println(" Seed value is " + new BASE64Encoder().encode(seed));

                secureRandom.setSeed(seed);

                System.out.println(" Secure Random # generated using setSeed(byte[]) is  " + secureRandom.nextDouble());

            } catch (NoSuchAlgorithmException noSuchAlgo)
            {
                System.out.println(" No Such Algorithm exists " + noSuchAlgo);
            }
        }

    }

**Good Practice: Use Strong Algorithms**

Below illustrates the implementation of AES (available per [Using the
Java Cryptographic
Extensions](Using_the_Java_Cryptographic_Extensions "wikilink")):

    package org.owasp.java.crypto;

    import javax.crypto.KeyGenerator;
    import javax.crypto.SecretKey;
    import javax.crypto.Cipher;

    import java.security.NoSuchAlgorithmException;
    import java.security.InvalidKeyException;
    import java.security.InvalidAlgorithmParameterException;
    import javax.crypto.NoSuchPaddingException;
    import javax.crypto.BadPaddingException;
    import javax.crypto.IllegalBlockSizeException;

    import sun.misc.BASE64Encoder;

    /**
     * @author Joe Prasanna Kumar
     * This program provides the following cryptographic functionalities
     * 1. Encryption using AES
     * 2. Decryption using AES
     *
     * High Level Algorithm :
     * 1. Generate a DES key (specify the Key size during this phase)
     * 2. Create the Cipher
     * 3. To Encrypt : Initialize the Cipher for Encryption
     * 4. To Decrypt : Initialize the Cipher for Decryption
     *
     *
     */

    public class AES {
        public static void main(String[] args) {

            String strDataToEncrypt = new String();
            String strCipherText = new String();
            String strDecryptedText = new String();

            try{
            /**
             *  Step 1. Generate an AES key using KeyGenerator
             *          Initialize the keysize to 128
             *
             */
            KeyGenerator keyGen = KeyGenerator.getInstance("AES");
            keyGen.init(128);
            SecretKey secretKey = keyGen.generateKey();

            /**
             *  Step2. Create a Cipher by specifying the following parameters
             *          a. Algorithm name - here it is AES
             */

            Cipher aesCipher = Cipher.getInstance("AES");

            /**
             *  Step 3. Initialize the Cipher for Encryption
             */

            aesCipher.init(Cipher.ENCRYPT_MODE,secretKey);

            /**
             *  Step 4. Encrypt the Data
             *          1. Declare / Initialize the Data. Here the data is of type String
             *          2. Convert the Input Text to Bytes
             *          3. Encrypt the bytes using doFinal method
             */
            strDataToEncrypt = "Hello World of Encryption using AES ";
            byte[] byteDataToEncrypt = strDataToEncrypt.getBytes();
            byte[] byteCipherText = aesCipher.doFinal(byteDataToEncrypt);
            strCipherText = new BASE64Encoder().encode(byteCipherText);
            System.out.println("Cipher Text generated using AES is " +strCipherText);

            /**
             *  Step 5. Decrypt the Data
             *          1. Initialize the Cipher for Decryption
             *          2. Decrypt the cipher bytes using doFinal method
             */
            aesCipher.init(Cipher.DECRYPT_MODE,secretKey,aesCipher.getParameters());
            byte[] byteDecryptedText = aesCipher.doFinal(byteCipherText);
            strDecryptedText = new String(byteDecryptedText);
            System.out.println(" Decrypted Text message is " +strDecryptedText);
            }

            catch (NoSuchAlgorithmException noSuchAlgo)
            {
                System.out.println(" No Such Algorithm exists " + noSuchAlgo);
            }

                catch (NoSuchPaddingException noSuchPad)
                {
                    System.out.println(" No Such Padding exists " + noSuchPad);
                }

                    catch (InvalidKeyException invalidKey)
                    {
                        System.out.println(" Invalid Key " + invalidKey);
                    }

                    catch (BadPaddingException badPadding)
                    {
                        System.out.println(" Bad Padding " + badPadding);
                    }

                    catch (IllegalBlockSizeException illegalBlockSize)
                    {
                        System.out.println(" Illegal Block Size " + illegalBlockSize);
                    }

                    catch (InvalidAlgorithmParameterException invalidParam)
                    {
                        System.out.println(" Invalid Parameter " + invalidParam);
                    }
        }

    }

## Laws and Regulations on Cryptography

There are a number of countries in which encryption is outlawed. As a
result, the development or use of applications that deploy cryptographic
processes could have an impact depending on location. The following
crypto law survey attempts to give an overview on the current state of
affairs regarding cryptography on a per-country basis \[8\].

## Design and Implementation

### Specification Definitions

Any code implementing cryptographic processes and algorithms should be
audited against a set of specifications. This will have as an objective
to capture the level of security the software is attempting to meet and
thus offer a measure point with regards to the cryptography used.

### Level of Code Quality

Cryptographic code written or used should be of the highest level in
terms of implementation. This should include simplicity, assertions,
unit testing, as well as modularization.

### Side Channel and Protocol Attacks

As an algorithm is static in nature, its use over a communication medium
constitutes a protocol. Thus issues relating to timeouts, how a message
is received and over what channel should be considered.

## References

\[1\] Bruce Schneier, Applied Cryptography, John Wiley & Sons, 2nd
edition, 1996.

\[2\] Michael Howard, Steve Lipner, The Security Development Lifecycle,
2006, pp. 251 - 258

\[3\] .NET Framework Developer's Guide, Cryptographic Services,
<http://msdn2.microsoft.com/en-us/library/93bskf9z.aspx>

\[4\] Microsoft Developer Network, Windows Data Protection,
<http://msdn2.microsoft.com/en-us/library/ms995355.aspx>

\[5\] Sun Developer Network, Java Cryptography Extension,
<http://java.sun.com/products/jce/>

\[6\] Sun Developer Network, Cryptographic Service Providers and Clean
Room Implementations,
<http://java.sun.com/products/jce/jce122_providers.html>

\[7\] Federal Information Processing Standards,
<http://csrc.nist.gov/publications/fips/>

\[8\] Bert-Jaap Koops, Crypto Law Survey, 2007,
<http://rechten.uvt.nl/koops/cryptolaw/>

[Can you check the links for 5 and 6? They go to the same
page.](Category:FIXME "wikilink") [Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")