## WARNING

Jim Manico recently brought to my attention this wiki page, the same who
asked me to check exactly. In doing so, I noticed several errors and
areas of weakness. Lately, I have the intention to revisit this page
(hopefully with the help of one of the original owners), but I do not
have time to do a full review at this time. Therefore, I will summarize
the problems observed on this page and leaving you the decision to use
or not, with these warnings.
\#First, this page does not describe "digital signatures". Rather, it
describes a concept known as "digital envelopes", which is a scheme used
with objects such as S / MIME. Digital signatures not only encrypt the
actual message text, only encrypts the hash of the message text.

1.  UTF-8 should be used to convert between Java byte strings and arrays
    to ensure adequate portability across different operating systems.
2.  The certificate chain must always be validated. In this example, the
    certificate is self-signed, so this is not relevant and will not be
    true in the normal case. Furthermore, it should be noted that the
    self-signed, but acceptable for demonstration purposes certificates
    is considered a dubious practice for production, as it opens the
    door to spoofing attacks.
3.  [NIST](http://www.nist.gov/) now recommends using key size 2048 bits
    for RSA or DSA keys.
4.  There is a consistent use of weak algorithms. Here are some
    suggested replacements:
    1.  Use "RSA/ECB/OAEPWithSHA1AndMGF1Padding" instead of
        "RSA/ECB/PKCS1Padding".
    2.  Use SHA1 (or better SHA256, SHA1 but at least) instead of MD5
        for message digest.
    3.  Use "SHA1withRSA" for the signature algorithm instead of
        "MD5withRSA".
    4.  When creating a symmetric encryption system to encrypt the
        message text, use "AES / CBC / PKCS5Padding" and choose an IV
        random for each text message instead of simply using "AES",
        ending with "AES / ECB / PKCS5Padding ". ECB mode is extremely
        weak for a regular plain text. (OK for random bit encryption,
        however, is well used with RSA.) However, the use CBC and
        PKCS5Padding could make it vulnerable to "Padding Oracle"
        attacks, so caution is advised. You can use Encryptor 2.0 ESAPI
        's to avoid it. (Note also, this part is the concept of "on
        digital". If this page was really limited by "digital
        signatures" would not apply because it would be irrelevant.)


I hope to get soonest, before cleaning this wiki page. Meanwhile, email
me your questions.
\-Kevin Wall

## Overview

This article presents a brief overview of the concepts involved with
digital signatures and provides code examples for the application of
digital signatures in Java using the [Java Cryptography Architecture
(JCA)](http://docs.oracle.com/javase/6/docs/technotes/guides/security/crypto/CryptoSpec.html).

### What is a digital signature?

A digital signature is a concept that helps to get the non-repudiation
of origin (ie, the integrity of Origin) data. By digitally signing the
document, the person signing, says he is the author of the document or
the signed message.

### Need for Digital Signature

During the "E" revolution was a need for authentication of critical
transactions especially in the financial world. If Alice agreed to
transfer $ x to Bob, then there had to be a way for Bob to ensure that:

  - It was Alice who performed the transaction and not someone else
    impersonating Alice (Authentication).
  - The amount agreed by Alice is $ x (Integrity).
  - Alice could not discuss his statement transaction $ x a Bob
    (Non-repudiation of origin).

These concerns were treated with a solution known as digital signatures.
More background information on digital signatures can be found
[here](http://en.wikipedia.org/wiki/Digital_signature)

## Digital signatures in Java using JCA

Java Cryptography Architecture is a framework for accessing and
developing cryptographic functionality for the Java platform. JCA
provider implements cryptographic functionality such as digital
signatures and message digests. The default JCA provider is SUN JDK
1.4.2.

### Security considerations when implementing digital signature

Two major safety considerations that must be taken into account when
applying digital signatures are:

1.  Sign the message and then encrypt the signed message.
2.  Sign the hash of the message instead of the entire message.

### Performance considerations when implementing digital signature

Because asymmetric encryption algorithms such as RSA, DSA are
computationally slower than symmetric encryption algorithms such as AES,
it is a good practice, encrypt the actual message that is transmitted
using a symmetric key algorithm and then encrypt the key that is used in
symmetric key algorithm using an asymmetric key algorithm. For example,
if you want to convey the message "Hello World Digital Signatures", then
this message is first encrypted with a symmetric key, for example, an
AES 128-bit key as x7oFaHSPnWxEMiZE/0qYrg and then this key is encrypted
with an algorithm as RSA asymmetric key.

## Algorithm to implement digital signature using the RSA algorithm

The provider RSA Java implementation has a limitation in that encryption
can be performed on the data length \<= 117 bytes only. If the data is
of a length\> 117 bytes, it will launch a IllegalBlockSizeException:
Data must have more than 117 bytes symmetry there has to be encrypted
and then signed.

RSA PKCS \# 1 algorithm can only encrypt data size k - 11, where k whose
length is one byte and the RSA module 11 is the number of bytes used by
the filling PCKS \# 1 v1.5. Therefore, if we use an RSA key size of 1024
bits, we could encrypt only 128-11 =\> 117 bytes of data. There are two
options available to encrypt data byte size larger.

1.  We could use an RSA key length\> 1024. For example, using 2048 bits,
    then we could encrypt 256-11 =\> 245 bytes of data. The disadvantage
    of this approach is that it would be capable of encoding data size\>
    x bytes (in the above example x is 245).
2.  Analyze the input data chunks of bytes in size \<117 and apply
    encryption on each piece. The code example of this approach can be
    found
    [here](http://www.aviransplace.com/2004/10/12/using-rsa-encryption-with-java/3/).

Both approaches could affect performance since the RSA key larger or
approach of ["divide and
conquer"](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithms)
of input bytes are computationally expensive.

### Algorithm

With the foregoing, the following algorithm can be used for the
implementation of public key cryptography in Java.

1.  Encrypt the message using a symmetric key
2.  Concatenate the symmetric key + symmetric hash + hash key message.
3.  Encrypt the concatenated string with the public key of the
    recipient.
4.  Sign data to be transmitted (encrypted symmetric key + the + Hash
    hash key message).
5.  Validate the signature.
6.  Deciphering the message with the recipient's private key to obtain
    the symmetric key.
7.  Validate the integrity of the key using the hash key.
8.  It decipher the real message using the symmetric key that has been
    decrypted, analyzed and integrity checks.
9.  Calculate MessageDigest of data.
10. Validate whether the message digest decrypted text matches the
    message digest of the original message.

### Commands for key generation

prompt\# keytool -genkey -alias testsender -keystore testkeystore.ks
-keyalg RSA Enter keystore password: testpwd

What is your first and last name?

`[Unknown]:  Alice Sender`

What is your name?

`[Unknown]:  IT`

What is the name of the OU?

`[Unknown]:  ABC Inc`

What is the name of your organization?

`[Unknown]:  LA`

What is the name of your city or town?

`[Unknown]:  CA`

What is the name of your state or province?

`[Unknown]:  US`

Is CN = Alice Sender, OU = IT, O = ABC Inc, L = LA, ST = CA, C = EE.UU.
correct?

`[no]:  y`

Enter the key password for <testsender>

`(RETURN if same as keystore password):  send123`

prompt \# keytool -genkey -alias testrecv -keystore testkeystore.ks
-keyalg RSA Enter the password of KeyStore: testpwd

What is your name?

`[Unknown]:  Bob Receiver`

What is the name of the OU?

`[Unknown]:  HR`

What is the name of your organization?

`[Unknown]:  ABC Inc`

What is the name of your city or town?

`[Unknown]:  SFO`

What is the name of your state or province?

`[Unknown]:  CA`

What is the country code of two letters for this unit?

`[Unknown]:  US`

Is CN = Bob receptor, OU = HR, O = ABC Inc, L = SFO, ST = CA, C = EE.UU.
correct?

`[no]:  y`

Enter the key password for <testrecv>

`(RETURN if same as keystore password):  recv123`

### Code Example

#### PublicKeyCryptography.java

    package org.owasp.crypto;

    import java.security.*;
    import java.security.cert.*;
    import javax.crypto.*;

    import sun.misc.BASE64Encoder;
    import sun.misc.BASE64Decoder;

    / **
     *
     * @author Joe Prasanna Kumar
     *
     * 1. Encrypt data using a symmetric key
     * 2. Encrypt the symmetric key with the public key Receivers
     * 3. Create a message digest of the data to be transmitted
     * 4. Sign the message to be transmitted
     * 5. Send the data through a nonsecure channel
     * 6. Validate signature
     * 7. Decoding the message using the private key Pets for the symmetric key
     * 8. Deciphering the data using the symmetric key
     * 9. Calculate MessageDigest signed message data +
     * 10.Valide if the text message digest matches the decrypted message digest of the original message
     */

    public class PublicKeyCryptography {

        public static void main(String[] args) {

        SymmetricEncrypt encryptUtil = new SymmetricEncrypt();
        String strDataToEncrypt = "Hello World";
        byte[] byteDataToTransmit = strDataToEncrypt.getBytes();

        // Generación de un SecretKey para el cifrado simétrico
        SecretKey senderSecretKey = SymmetricEncrypt.getSecret();

        //1. Cifrar los datos utilizando una clave simétrica
        byte[] byteCipherText = encryptUtil.encryptData(byteDataToTransmit,senderSecretKey,"AES");
        String strCipherText = new BASE64Encoder().encode(byteCipherText);


        //2. Cifrar la clave simétrica con la clave pública
        try{
            // 2.1 Especifique el almacén de claves que se haya importado el certificado Receptores
        KeyStore ks = KeyStore.getInstance(KeyStore.getDefaultType());
        char [] password = "testpwd".toCharArray();
        java.io.FileInputStream fis = new java.io.FileInputStream("/home/Joebi/workspace/OWASP_Crypto/org/owasp/crypto/testkeystore.ks");
        ks.load(fis, password);
        fis.close();

            // 2.2 Creación de un certificado X509 del receptor
        X509Certificate recvcert ;
        MessageDigest md = MessageDigest.getInstance("MD5");
        recvcert = (X509Certificate)ks.getCertificate("testrecv");
        // 2.3 Obtención de la llave pública de los certificados
        PublicKey pubKeyReceiver = recvcert.getPublicKey();

        // 2.4 Cifrado de la SecretKey con la clave pública Receptores
        byte[] byteEncryptWithPublicKey = encryptUtil.encryptData(senderSecretKey.getEncoded(),pubKeyReceiver,"RSA/ECB/PKCS1Padding");
        String strSenbyteEncryptWithPublicKey = new BASE64Encoder().encode(byteEncryptWithPublicKey);

        // 3. Crear un resumen del mensaje de los datos a transmitir
        md.update(byteDataToTransmit);
        byte byteMDofDataToTransmit[] = md.digest();

        String strMDofDataToTransmit = new String();
        for (int i = 0; i < byteMDofDataToTransmit.length; i++){
            strMDofDataToTransmit = strMDofDataToTransmit + Integer.toHexString((int)byteMDofDataToTransmit[i] & 0xFF) ;
                 }

        // 3.1 Mensaje que se Firmado = clave secreta cifrada + MAC de los datos a transmitir
        String strMsgToSign = strSenbyteEncryptWithPublicKey + "|" + strMDofDataToTransmit;

        // 4. Firma el mensaje
        // 4.1 Obtener la clave privada del remitente desde el almacén de claves, proporcionando la contraseña establecida para la llave privada mientras se crea las llaves usados.
        char[] keypassword = "send123".toCharArray();
        Key myKey =  ks.getKey("testsender", keypassword);
        PrivateKey myPrivateKey = (PrivateKey)myKey;

        // 4.2 Firmar el mensaje
        Signature mySign = Signature.getInstance("MD5withRSA");
        mySign.initSign(myPrivateKey);
        mySign.update(strMsgToSign.getBytes());
        byte[] byteSignedData = mySign.sign();

        // 5. Los valores byteSignedData (la firma) y strMsgToSign (los datos que se firmó) se pueden enviar a través del receptor

        // 6. Validar la firma
        // 6.1 Extraer la clave pública de su certificado de remitentes
        X509Certificate sendercert ;
        sendercert = (X509Certificate)ks.getCertificate("testsender");
        PublicKey pubKeySender = sendercert.getPublicKey();
        // 6.2 Verificar la Firma
        Signature myVerifySign = Signature.getInstance("MD5withRSA");
        myVerifySign.initVerify(pubKeySender);
        myVerifySign.update(strMsgToSign.getBytes());

        boolean verifySign = myVerifySign.verify(byteSignedData);
        if (verifySign == false)
        {
            System.out.println(" Error in validating Signature ");
        }

        else
            System.out.println(" Successfully validated Signature ");

        // 7. Descifrar el mensaje usando la llave privada Pets para obtener la clave simétrica
        char[] recvpassword = "recv123".toCharArray();
        Key recvKey =  ks.getKey("testrecv", recvpassword);
        PrivateKey recvPrivateKey = (PrivateKey)recvKey;

        // Analizar el MessageDigest y el valor cifrado
        String strRecvSignedData = new String (byteSignedData);
        String[] strRecvSignedDataArray = new String [10];
        strRecvSignedDataArray = strMsgToSign.split("|");
        int intindexofsep = strMsgToSign.indexOf("|");
        String strEncryptWithPublicKey = strMsgToSign.substring(0,intindexofsep);
        String strHashOfData = strMsgToSign.substring(intindexofsep+1);

        // Descifrado para obtener la clave simétrica
        byte[] bytestrEncryptWithPublicKey = new BASE64Decoder().decodeBuffer(strEncryptWithPublicKey);
        byte[] byteDecryptWithPrivateKey = encryptUtil.decryptData(byteEncryptWithPublicKey,recvPrivateKey,"RSA/ECB/PKCS1Padding");

        // 8. Descifrar los datos usando la clave simétrica
        javax.crypto.spec.SecretKeySpec secretKeySpecDecrypted = new javax.crypto.spec.SecretKeySpec(byteDecryptWithPrivateKey,"AES");
        byte[] byteDecryptText = encryptUtil.decryptData(byteCipherText,secretKeySpecDecrypted,"AES");
        String strDecryptedText = new String(byteDecryptText);
        System.out.println(" Decrypted data is " +strDecryptedText);

        // 9. Calcule MessageDigest de datos + mensaje firmado
        MessageDigest recvmd = MessageDigest.getInstance("MD5");
        recvmd.update(byteDecryptText);
        byte byteHashOfRecvSignedData[] = recvmd.digest();

        String strHashOfRecvSignedData = new String();

        for (int i = 0; i < byteHashOfRecvSignedData.length; i++){
            strHashOfRecvSignedData = strHashOfRecvSignedData + Integer.toHexString((int)byteHashOfRecvSignedData[i] & 0xFF) ;
                 }
        // 10. Validar si la síntesis del mensaje del texto coincide con el mensaje descifrado
       Digest of the Original Message

        if (!strHashOfRecvSignedData.equals(strHashOfData))
        {
            System.out.println(" Message has been tampered ");
        }

        }

        catch(Exception exp)
        {
            System.out.println(" Exception caught " + exp);
            exp.printStackTrace();
        }


        }

    }

#### SymmetricEncrypt.java

    package org.owasp.crypto;

    import javax.crypto.KeyGenerator;
    import javax.crypto.SecretKey;
    import javax.crypto.Cipher;
    import java.security.Key;

    import java.security.NoSuchAlgorithmException;
    import java.security.InvalidKeyException;
    import java.security.InvalidAlgorithmParameterException;
    import javax.crypto.NoSuchPaddingException;
    import javax.crypto.BadPaddingException;
    import javax.crypto.IllegalBlockSizeException;

    import sun.misc.BASE64Encoder;

    /**
     * @author Joe Prasanna Kumar
     * Este programa ofrece las funcionalidades criptográficas siguientes
     * 1. Cifrado con AES
     * 2. El descifrado con AES
     *
     * Algoritmo de alto nivel:
     * 1. Generar una clave DES (especificar el tamaño de la clave durante esta fase)
     * 2. Cree el Cipher
     * 3. Para cifrar: Inicializar el cifrado para el cifrado
     * 4. Para descifrar: Inicializar el cifrado para descifrar
     *
     *
     */

    public class SymmetricEncrypt {

            String strDataToEncrypt = new String();
            String strCipherText = new String();
            String strDecryptedText = new String();
            static KeyGenerator keyGen;
            private static String strHexVal = "0123456789abcdef";

            public static SecretKey getSecret(){
            /**
             *  Paso 1. Generación de una clave AES mediante keygenerator
             *          Inicializa el tamaño de clave de 128
             *
             */

                try{
                    keyGen = KeyGenerator.getInstance("AES");
                    keyGen.init(128);

                    }

                catch(Exception exp)
                {
                    System.out.println(" Exception inside constructor " +exp);
                }

                SecretKey secretKey = keyGen.generateKey();
                return secretKey;
            }

            /**
             *  Paso 2. Crear un sistema de cifrado mediante la especificación de los siguientes parámetros
             *          a. Nombre del algoritmo - aquí es AES
             */


            public byte[] encryptData(byte[] byteDataToEncrypt, Key secretKey, String Algorithm) {
                byte[] byteCipherText = new byte[200];

                try {
                Cipher aesCipher = Cipher.getInstance(Algorithm);

            /**
             *  Paso 3. Inicialice el cifrado para el cifrado
             */
                if(Algorithm.equals("AES")){
                    aesCipher.init(Cipher.ENCRYPT_MODE,secretKey,aesCipher.getParameters());
                    }
                    else if(Algorithm.equals("RSA/ECB/PKCS1Padding")){
                    aesCipher.init(Cipher.ENCRYPT_MODE,secretKey);
                    }

            /**
             *  Paso 4. Cifrar los datos
             *          1. Declarar / inicializar los datos. Aquí los datos son de tipo String
             *          2. Convertir el texto de entrada a Bytes
             *          3. Cifrado de los bytes, utilizando el método doFinal
             */
            byteCipherText = aesCipher.doFinal(byteDataToEncrypt);
            strCipherText = new BASE64Encoder().encode(byteCipherText);

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
                            illegalBlockSize.printStackTrace();
                        }
                        catch (Exception exp)
                        {
                            exp.printStackTrace();
                        }

            return byteCipherText;
            }
            /**
             *  Paso 5. Descifrar los datos
             *          1. Inicialice el cifrado para descifrar
             *          2. Descifrar los bytes cifrados utilizando el método doFinal
             */

            public byte[] decryptData(byte[] byteCipherText, Key secretKey, String Algorithm) {
                byte[] byteDecryptedText = new byte[200];

                try{
            Cipher aesCipher = Cipher.getInstance(Algorithm);
            if(Algorithm.equals("AES")){
            aesCipher.init(Cipher.DECRYPT_MODE,secretKey,aesCipher.getParameters());
            }
            else if(Algorithm.equals("RSA/ECB/PKCS1Padding")){
            aesCipher.init(Cipher.DECRYPT_MODE,secretKey);
            }

            byteDecryptedText = aesCipher.doFinal(byteCipherText);
            strDecryptedText = new String(byteDecryptedText);
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
                        invalidKey.printStackTrace();
                    }

                    catch (BadPaddingException badPadding)
                    {
                        System.out.println(" Bad Padding " + badPadding);
                        badPadding.printStackTrace();
                    }

                    catch (IllegalBlockSizeException illegalBlockSize)
                    {
                        System.out.println(" Illegal Block Size " + illegalBlockSize);
                        illegalBlockSize.printStackTrace();
                    }

                    catch (InvalidAlgorithmParameterException invalidParam)
                    {
                        System.out.println(" Invalid Parameter " + invalidParam);
                    }

            return byteDecryptedText;
            }


            public static byte[] convertStringToByteArray(String strInput) {
                strInput = strInput.toLowerCase();
                byte[] byteConverted = new byte[(strInput.length() + 1) / 2];
                int j = 0;
                int interimVal;
                int nibble = -1;

                for (int i = 0; i < strInput.length(); ++i) {
                    interimVal = strHexVal.indexOf(strInput.charAt(i));
                    if (interimVal >= 0) {
                        if (nibble < 0) {
                            nibble = interimVal;
                        } else {
                            byteConverted[j++] = (byte) ((nibble << 4) + interimVal);
                            nibble = -1;
                        }
                    }
                }

                if (nibble >= 0) {
                    byteConverted[j++] = (byte) (nibble << 4);
                }

                if (j < byteConverted.length) {
                    byte[] byteTemp = new byte[j];
                    System.arraycopy(byteConverted, 0, byteTemp, 0, j);
                    byteConverted = byteTemp;
                }

                return byteConverted;
            }

            public static String convertByteArrayToString(byte[] block) {
                StringBuffer buf = new StringBuffer();

                for (int i = 0; i < block.length; ++i) {
                    buf.append(strHexVal.charAt((block[i] >>> 4) & 0xf));
                    buf.append(strHexVal.charAt(block[i] & 0xf));
                }

                return buf.toString();
            }
    }

## References

1.  Computer Security Arts and Science – Matt Bishop
2.  Core Security Patterns – Christopher Steele, Ray Lai and Ramesh
    Nagappan

**Aplications in Free Environments**

**`Tutor:`**`  Ing. Tito Armas`

**`Translator:`**` Bravo Maria Jose and Portilla Maria Fernanda 2012`

[Category:Java](Category:Java "wikilink")