

## Status

Requires review

*The code included in this article has not been reviewed and should not
be used without proper analysis. If you have reviewed the included code
(or portions of it), please post your findings back to this page or to:
stephen \[at\] corsaire.com.*

## Overview

### What is SSL ?

SSL - Secure Socket Layer is an Application layer cryptographic protocol
developed by Netscape for securing communication over the Internet. The
security services provided by SSL are

1.  Confidentiality through Encryption of data using Symmetric Key
    Encryption Algorithms
2.  Non - Repudiation of Origin / Origin Integrity through Digital
    Signatures using Asymmetric key Encryption Algorithms or Public Key
    Cryptographic Algorithms
3.  Data Integrity through Hashing using Message Digest or Hashing
    Algorithms

### What is JSSE ?

JSSE is the acronym of Jave Secure Socket Extensions. As the name
implies it is a set of Java API's which provides SSL / TLS
functionality. JSSE follows a Provider Architecture wherein the
functionality specified in the Service Provider Interface can be
implemented by any Service Provider. JSSE comes bundled with a default
service provider named SunJSSE. JSSE was an optional package on jdk
\#\#x and \#\#x. Since jdk \#\#x, JSSE comes pre-configured with the
standard jdk package

### The JSSE Implementation of SSL

JSSE provides an implementation for creating SSLSocket (used by clients)
and SSLServerSocket (used by server).

#### Algorithm for creating SSL Client socket

1.  Determine the SSL Server Name and port in which the SSL server is
    listening
2.  Register the JSSE provider
3.  Create an instance of SSLSocketFactory
4.  Create an instance of SSLSocket
5.  Create an OutputStream object to write to the SSL Server
6.  Create an InputStream object to receive messages back from the SSL
    Server

#### Algorithm for creating SSL Server socket

1.  Register the JSSE provider
2.  Set System property for keystore by specifying the keystore which
    contains the server certificate
3.  Set System property for the password of the keystore which contains
    the server certificate
4.  Create an instance of SSLServerSocketFactory
5.  Create an instance of SSLServerSocket by specifying the port to
    which the SSL Server socket needs to bind with
6.  Initialize an object of SSLSocket
7.  Create InputStream object to read data sent by clients
8.  Create an OutputStream object to write data back to clients.

### SSL Handshake Protocol

The SSL handshake protocol happens between the client and the server and
comprises of 4 rounds that enable peers to agree on keys, ciphers and
MAC algorithms. The handshake is explained below with the parameters
captured in the debug mode during the execution of SSLClient and
SSLServer java files.

#### Round 1 : Create the SSL connection between the Client and the Server

```
    C -> S {ver || randomcookie1 || sessionid || Cipher Suites || Compression Methods }
*** ClientHello, TLSv1
RandomCookie:  GMT: 1165141617 bytes = { 250, 20, 142, 231, 143, 78, 72, 52, 254, 46, 199, 39, 146, 23, 238, 5, 108, 171, 75, 192, 78, 173, 26, 151, 89, 86, 58, 197 }
Session ID:  {}
Cipher Suites: [SSL_RSA_WITH_RC4_128_MD5, SSL_RSA_WITH_RC4_128_SHA, TLS_RSA_WITH_AES_128_CBC_SHA, TLS_DHE_RSA_WITH_AES_128_CBC_SHA, TLS_DHE_DSS_WITH_AES_128_CBC_SHA, SSL_RSA_WITH_3DES_EDE_CBC_SHA, SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA, SSL_DHE_DSS_WITH_3DES_EDE_CBC_SHA, SSL_RSA_WITH_DES_CBC_SHA, SSL_DHE_RSA_WITH_DES_CBC_SHA, SSL_DHE_DSS_WITH_DES_CBC_SHA, SSL_RSA_EXPORT_WITH_RC4_40_MD5, SSL_RSA_EXPORT_WITH_DES40_CBC_SHA, SSL_DHE_RSA_EXPORT_WITH_DES40_CBC_SHA, SSL_DHE_DSS_EXPORT_WITH_DES40_CBC_SHA]
Compression Methods:  { 0 }
    S -> C {ver || randomcookie2 || session_id || cipher || compression }
*** ServerHello, TLSv1
RandomCookie:  GMT: 1165141617 bytes = { 33, 91, 78, 189, 156, 183, 142, 253, 119, 155, 22, 193, 46, 0, 50, 153, 168, 170, 19, 220, 68, 97, 98, 3, 36, 228, 103, 117 }
Session ID:  {69, 115, 166, 113, 102, 3, 65, 68, 227, 239, 225, 34, 115, 49, 73, 69, 174, 111, 222, 219, 119, 162, 5, 11, 77, 149, 181, 24, 38, 98, 5, 204}
Cipher Suite: SSL_RSA_WITH_RC4_128_MD5
Compression Method: 0
```

#### Round 2 : Server authenticates itself

```
    S -> C {server_cert}
***
%% Created:  [Session-1, SSL_RSA_WITH_RC4_128_MD5]
** SSL_RSA_WITH_RC4_128_MD5
[read] MD5 and SHA1 hashes:  len = 74
0000: 02 00 00 46 03 01 45 73   A6 71 21 5B 4E BD 9C B7  ...F..Es.q![N...
0010: 8E FD 77 9B 16 C1 2E 00   32 99 A8 AA 13 DC 44 61  ..w.....#....Da
0020: 62 03 24 E4 67 75 20 45   73 A6 71 66 03 41 44 E3  b.$.gu Es.qf.AD.
0030: EF E1 22 73 31 49 45 AE   6F DE DB 77 A2 05 0B 4D  .."s1IE.o..w...M
0040: 95 B5 18 26 62 05 CC 00   04 00                    ...&b.....

    S -> C {public key modulus || exponent || {hash (randomcookie1 || randomcookie2 || public key modulus || exponent )} signed by Server}
*** Certificate chain
chain [0] = [
[
  Version: V1
  Subject: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
  Signature Algorithm: MD5withRSA, OID = ######4

  Key:  Sun RSA public key, 1024 bits
  modulus: 125799608853960565468693082080524019040787802862173204033354805928537584240351554241990082493719007271501637788649255493925650447292814949263542483518710211756489915623917992726468465059340034326131973495929283930754477403752766287367308326998219377123365800989254595407827915805528431637337980240073881550879
  public exponent: 65537
  Validity: [From: Sun Nov 26 06:33:42 EST 2006,
               To: Wed Apr 12 07:33:42 EDT 2034]
  Issuer: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
  SerialNumber: [    45697b96]

]
  Algorithm: [MD5withRSA]
  Signature:
0000: 1A 35 AD 99 24 0A 8C 09   58 0C FC B4 B3 F8 3F DC  .#.$...X.....?.
0010: 44 BF 56 A2 3A 5D E5 DF   0D CF D2 59 51 F2 6E 1C  D.V.:].....YQ.n.
0020: 2A C0 03 9B 7C 3F 8B 53   C8 E9 16 A7 BC 28 23 C1  *....?.S.....(#.
0030: 67 F3 E4 05 D9 55 13 65   2E E3 80 BA A3 0A 9C F6  g....U.e........
0040: A1 50 46 90 D7 E0 8F 50   6C E4 00 5D 3F F8 D0 62  .PF....Pl..]?..b
0050: D2 A9 47 DF 65 3B 02 E8   1C 04 8A 3C 7B 19 B3 EB  ..G.e;.....<....
0060: B6 50 23 6E C6 8A 49 95   6E 38 70 D2 2B 40 31 A5  .P#n..I.n8p.+@#
0070: FE 3F 44 EF 3A E4 12 69   46 D1 4F A0 83 40 F7 F3  .?D.:..iF.O..@..
]
***
    S -> C { cert_type || good_cert_authorities}
    S -> C {end_round_2}
```

#### Round 3 : Client validates the Server certificate

```
    C -> S {client_cert}
    C -> S {pre master secret}
*** ClientKeyExchange, RSA PreMasterSecret, TLSv1
Random Secret:  { 3, 1, 161, 37, 5, 17, 154, 202, 73, 33, 75, 50, 61, 242, 44, 252, 232, 80, 161, 185, 2, 61, 154, 54, 177, 192, 141, 235, 95, 174, 219, 216, 251, 150, 189, 99, 188, 180, 15, 253, 28, 168, 85, 124, 17, 124, 218, 101 }
    C -> S {hash(master secret || padding value || hash(messages || master secret || padding value))}
    where messages refers to concatenation messages exchanged from 1 through #
```

#### Round 4 : Acknowledgment between Client and the Server

```
    The client updates the session and connection information to reflect the cipher it uses and then sends a “finished” message
SESSION KEYGEN:
PreMaster Secret:
0000: 03 01 A1 25 05 11 9A CA   49 21 4B 32 3D F2 2C FC  ...%....I!K2=.,.
0010: E8 50 A1 B9 02 3D 9A 36   B1 C0 8D EB 5F AE DB D8  .P...=.#..._...
0020: FB 96 BD 63 BC B4 0F FD   1C A8 55 7C 11 7C DA 65  ...c......U....e
CONNECTION KEYGEN:
Client Nonce:
0000: 45 73 A6 71 FA 14 8E E7   8F 4E 48 34 FE 2E C7 27  Es.q.....NH#..'
0010: 92 17 EE 05 6C AB 4B C0   4E AD 1A 97 59 56 3A C5  ....l.K.N...YV:.
Server Nonce:
0000: 45 73 A6 71 21 5B 4E BD   9C B7 8E FD 77 9B 16 C1  Es.q![N.....w...
0010: 2E 00 32 99 A8 AA 13 DC   44 61 62 03 24 E4 67 75  ..#....Dab.$.gu
Master Secret:
0000: B5 AF 35 36 65 B8 2E A9   F0 5C C1 A7 BD 85 98 92  ..56e....\......
0010: 64 61 B6 B9 7D 86 AB C7   72 CA 67 9A E1 C1 C4 3F  da......r.g....?
0020: C5 8B 67 1A 49 C9 6E B2   FC AB 65 96 EA 7E 67 8C  ..g.I.n...e...g.
Client MAC write Secret:
0000: A4 C0 36 E3 9A D3 8B 67   AA 51 D6 78 59 BF 0A 5E  ..#...g.Q.xY..^
Server MAC write Secret:
0000: F7 D0 65 1D 4C 0E 81 0F   1F 76 86 D7 91 68 37 50  ..e.L....v...h7P
Client write key:
0000: A6 C5 F0 7D FE 1C 0E 58   85 00 A5 02 AE 08 B5 0E  .......X........
Server write key:
0000: 20 D3 07 A2 02 02 34 67   2C C3 5A 50 7C 0F 87 CB   .....4g,.ZP....
... no IV for cipher
[read] MD5 and SHA1 hashes:  len = 134
0000: 10 00 00 82 00 80 10 D4   F8 1C 1D 96 62 B2 59 DD  ............b.Y.
0010: D6 F8 F1 0F A5 5E 75 0F   4F 3D 5B 56 2C 6A 24 FD  .....^u.O=[V,j$.
0020: 4A 90 D4 3A F3 3F 7E 22   D2 00 18 3B 7D 3F CD 02  J..:.?."...;.?..
0030: 0C E1 11 7C 12 59 D8 A3   85 8D CB 23 B7 90 1C 59  .....Y.....#...Y
0040: 94 65 5F 7E 8E 46 6D A9   7D FC 54 5D 81 DC 69 82  .e_..Fm...T]..i.
0050: 1A EE 1A A5 F1 52 66 A6   43 34 EE E0 F7 12 36 CF  .....Rf.C#...#
0060: 7A 38 48 5A C9 8E 11 CB   AE 7A 36 2D FD 0B CD 1A  z8HZ.....z6-....
0070: 0B F1 45 1E C6 71 D9 57   39 80 75 BF D6 68 43 15  ..E..q.W#u..hC.
0080: FE 4D 67 DC 2F BD                                  .Mg./.
[Raw read]: length = 5
0000: 14 03 01 00 01                                     .....
[Raw read]: length = 1
0000: 01                                                 .
main, READ: TLSv1 Change Cipher Spec, length = 1
[Raw read]: length = 5
0000: 16 03 01 00 20                                     ....
[Raw read]: length = 32
0000: C7 D8 CC 69 F7 F7 7F 00   29 F6 23 C8 DD 11 50 33  ...i....).#...P3
0010: 89 BB 91 21 BD 05 24 8C   5B 77 33 9D 78 0A B4 3C  ...!..$.[w#x..<
main, READ: TLSv1 Handshake, length = 32
Padded plaintext after DECRYPTION:  len = 32
0000: 14 00 00 0C 01 B0 24 0D   BC AD E7 E9 DC CB E4 17  ......$.........
0010: F9 FF 44 03 B2 00 37 12   9C A2 16 62 2E 9E 3C 33  ..D...#...b..<3
*** Finished
verify_data:  { 1, 176, 36, 13, 188, 173, 231, 233, 220, 203, 228, 23 }

    Server responds back with a “change cipher spec” message and updates its session and connection information accordingly and sends a finish message.
SESSION KEYGEN:
PreMaster Secret:
0000: 03 01 A1 25 05 11 9A CA   49 21 4B 32 3D F2 2C FC  ...%....I!K2=.,.
0010: E8 50 A1 B9 02 3D 9A 36   B1 C0 8D EB 5F AE DB D8  .P...=.#..._...
0020: FB 96 BD 63 BC B4 0F FD   1C A8 55 7C 11 7C DA 65  ...c......U....e
CONNECTION KEYGEN:
Client Nonce:
0000: 45 73 A6 71 FA 14 8E E7   8F 4E 48 34 FE 2E C7 27  Es.q.....NH#..'
0010: 92 17 EE 05 6C AB 4B C0   4E AD 1A 97 59 56 3A C5  ....l.K.N...YV:.
Server Nonce:
0000: 45 73 A6 71 21 5B 4E BD   9C B7 8E FD 77 9B 16 C1  Es.q![N.....w...
0010: 2E 00 32 99 A8 AA 13 DC   44 61 62 03 24 E4 67 75  ..#....Dab.$.gu
Master Secret:
0000: B5 AF 35 36 65 B8 2E A9   F0 5C C1 A7 BD 85 98 92  ..56e....\......
0010: 64 61 B6 B9 7D 86 AB C7   72 CA 67 9A E1 C1 C4 3F  da......r.g....?
0020: C5 8B 67 1A 49 C9 6E B2   FC AB 65 96 EA 7E 67 8C  ..g.I.n...e...g.
Client MAC write Secret:
0000: A4 C0 36 E3 9A D3 8B 67   AA 51 D6 78 59 BF 0A 5E  ..#...g.Q.xY..^
Server MAC write Secret:
0000: F7 D0 65 1D 4C 0E 81 0F   1F 76 86 D7 91 68 37 50  ..e.L....v...h7P
Client write key:
0000: A6 C5 F0 7D FE 1C 0E 58   85 00 A5 02 AE 08 B5 0E  .......X........
Server write key:
0000: 20 D3 07 A2 02 02 34 67   2C C3 5A 50 7C 0F 87 CB   .....4g,.ZP....
... no IV for cipher
main, WRITE: TLSv1 Change Cipher Spec, length = 1
[Raw write]: length = 6
0000: 14 03 01 00 01 01                                  ......
*** Finished
verify_data:  { 1, 176, 36, 13, 188, 173, 231, 233, 220, 203, 228, 23 }
```

Once the handshake is complete, secure communication can commence.

## The Need for Keytool

The server needs to generate a certificate and a private key associated
with its certificate. This certificate would be sent to the clients who
wishes to communicate with the server. These functionalities of Key
generation, Key management , certificate management are taken care by a
tool provided by Sun known as keytool. Keytool uses keystores to store
the public / private keys as well as certificates. keystores are
datastores implemented as files. Private keys are protected with
passwords.

### Algorithms supported by Keytool

Keytool supports any algorithm implemented by the registered
cryptographic service providers. Default key pair generation algorithm
is DSA with a keysize of 1024 bits. The signature algorithm is derived
from the algorithm of the private keys. DSA gets coupled with SHA1 by
default and so "SHA1withDSA" would be used. RSA gets coupled with MD5
and so "MD5withRSA" would be used.

### Some of the frequently used functions of keytool are:

#### Generating keys using keytools

Key pairs can be generated using keytool with the following command and
options

    $bash # keytool -genkey -alias testkey -keystore testkeystore.ks
    Enter keystore password:  testpwd
    What is your first and last name?
      [Unknown]:  Tom
    What is the name of your organizational unit?
      [Unknown]:  security
    What is the name of your organization?
      [Unknown]:  ABC Inc
    What is the name of your City or Locality?
      [Unknown]:  Fort Meade
    What is the name of your State or Province?
      [Unknown]:  MA
    What is the two-letter country code for this unit?
      [Unknown]:  US
    Is CN=Tom, OU=security, O=ABC Inc, L=Fort Meade, ST=MA, C=US correct?
      [no]:  y

    Enter key password for <testkey>
            (RETURN if same as keystore password):

  - The option *-genkey* is used to generate the keys.
  - *-alias* specifies the name of the key. This can be verified by the
    command keytool -list -keystore testkeystore.ks
  - *-keystore* is the name of the keystore to where the key needs to be
    added. If no keystore name is specified, the generated keys will be
    added to the default keystore. The default keystore gets
    autogenerated when the first key is created and is located in the
    users home directory with an ".keystore" extension.

The following defaults would be applied during the genkey process:

`       * keyalg - defaults to DSA`
`       * keysize - defaults to 1024 bits`
`       * validity - defaults to 90 days`

#### Importing certificates into keystore from .cer files

A certificate represented usually by a .cer file is imported into the
keystore so that it gets added to the list of trusted certificates.

    $bash # keytool -import -keystore testkeystore.ks -file ssltest.cer
    Enter keystore password:  testpwd
    Owner: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
    Issuer: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
    Serial number: 45697b96
    Valid from: Sun Nov 26 06:33:42 EST 2006 until: Wed Apr 12 07:33:42 EDT 2034
    Certificate fingerprints:
             MD5:  BD:AA:A5:77:AC:92:17:0E:D3:6E:E2:8F:2B:12:A5:6C
             SHA1: 2F:BF:88:E1:2F:26:B9:C3:64:5E:C5:7F:F4:BF:43:7F:37:3D:BE:C5
    Trust this certificate? [no]:  yes
    Certificate was added to keystore

The certificate ssltest.cer is successfully imported into the keystore.
The serial number generated is unique to this certificate and is useful
during certificate revocations. When a certificate is revoked, the
serial number gets added to the CRL (Certificate revocation list).
**Warning:** **Before importing a certificate, validate if the
certificate really belongs to the entity it claims to represent.**

#### Use the keytool -printcert -file ssltest.cer to view the contents of the certificate

    $bash # keytool -printcert -file ssltest.cer
    Owner: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
    Issuer: CN=Jane P, OU=Network Admins, O=NewCo, L=Denver, ST=CO, C=US
    Serial number: 45697b96
    Valid from: Sun Nov 26 06:33:42 EST 2006 until: Wed Apr 12 07:33:42 EDT 2034
    Certificate fingerprints:
             MD5:  BD:AA:A5:77:AC:92:17:0E:D3:6E:E2:8F:2B:12:A5:6C
             SHA1: 2F:BF:88:E1:2F:26:B9:C3:64:5E:C5:7F:F4:BF:43:7F:37:3D:BE:C5

    # Verify from the Issuer of the certificate if the Certificate fingerprint matches.

#### Exporting certificates from keystore to files

To export a certificate from a keystore to a file, the following command
could be used

    $bash # keytool -export -alias testkey -keystore testkeystore.ks -file testkey.cer
    Enter keystore password:  testpwd
    Certificate stored in file <testkey.cer>
    Now you can verify the contents of the exported certificate using the command.
    $bash # keytool -printcert -file testkey.cer
    Owner: CN=Tom, OU=security, O=ABC Inc, L=Fort Meade, ST=MA, C=US
    Issuer: CN=Tom, OU=security, O=ABC Inc, L=Fort Meade, ST=MA, C=US
    Serial number: 45736152
    Valid from: Sun Dec 03 18:44:18 EST 2006 until: Sat Mar 03 18:44:18 EST 2007
    Certificate fingerprints:
             MD5:  8F:D3:EA:E7:B0:CF:9C:03:16:2F:3F:C9:6C:BC:5A:D4
             SHA1: 03:2B:C6:BD:D9:82:31:08:F1:88:3C:35:AD:8D:F9:C3:90:5E:53:6F

## Examples

### SSLClient.java

    package org.owasp.crypto;

    import java.io.*;

    import javax.net.ssl.*;
    import com.sun.net.ssl.*;
    import com.sun.net.ssl.internal.ssl.Provider;
    import java.security.Security;

    /**
     * @author Joe Prasanna Kumar
     * This program simulates a client socket program which communicates with the SSL Server
     *
     * Algorithm:
     * 1. Determine the SSL Server Name and port in which the SSL server is listening
     * 2. Register the JSSE provider
     * 3. Create an instance of SSLSocketFactory
     * 4. Create an instance of SSLSocket
     * 5. Create an OutputStream object to write to the SSL Server
     * 6. Create an InputStream object to receive messages back from the SSL Server
     *
     */

    public class SSLClient {

        /**
         * @param args
         */
        public static void main(String[] args) throws Exception{
            String strServerName = "localhost"; // SSL Server Name
            int intSSLport = 4443; // Port where the SSL Server is listening
            PrintWriter out = null;
            BufferedReader in = null;

            {
                // Registering the JSSE provider
                Security.addProvider(new Provider());
            }

            try {
                // Creating Client Sockets
                SSLSocketFactory sslsocketfactory = (SSLSocketFactory)SSLSocketFactory.getDefault();
                SSLSocket sslSocket = (SSLSocket)sslsocketfactory.createSocket(strServerName,intSSLport);

                // Initializing the streams for Communication with the Server
                out = new PrintWriter(sslSocket.getOutputStream(), true);
                in = new BufferedReader(new InputStreamReader(sslSocket.getInputStream()));

                BufferedReader stdIn = new BufferedReader(new InputStreamReader(System.in));
                String userInput = "Hello Testing ";
                out.println(userInput);

                while ((userInput = stdIn.readLine()) != null) {
                    out.println(userInput);
                    System.out.println("echo: " + in.readLine());
                }

                    out.println(userInput);

                    // Closing the Streams and the Socket
                    out.close();
                    in.close();
                    stdIn.close();
                    sslSocket.close();
            }

            catch(Exception exp)
            {
                System.out.println(" Exception occurred .... " +exp);
                exp.printStackTrace();
            }

        }

    }

### SSLServer.java

    package org.owasp.crypto;

    import java.io.*;
    import java.security.Security;
    import java.security.PrivilegedActionException;

    import javax.net.ssl.*;
    import com.sun.net.ssl.*;
    import com.sun.net.ssl.internal.ssl.Provider;

    /**
     * @author Joe Prasanna Kumar
     * This program simulates an SSL Server listening on a specific port for client requests
     *
     * Algorithm:
     * 1. Regsiter the JSSE provider
     * 2. Set System property for keystore by specifying the keystore which contains the server certificate
     * 3. Set System property for the password of the keystore which contains the server certificate
     * 4. Create an instance of SSLServerSocketFactory
     * 5. Create an instance of SSLServerSocket by specifying the port to which the SSL Server socket needs to bind with
     * 6. Initialize an object of SSLSocket
     * 7. Create InputStream object to read data sent by clients
     * 8. Create an OutputStream object to write data back to clients.
     *
     */


    public class SSLServer {

        /**
         * @param args
         */

        public static void main(String[] args) throws Exception{

            int intSSLport = 4443; // Port where the SSL Server needs to listen for new requests from the client

            {
                // Registering the JSSE provider
                Security.addProvider(new Provider());

                //Specifying the Keystore details
                System.setProperty("javax.net.ssl.keyStore","server.ks");
                System.setProperty("javax.net.ssl.keyStorePassword","JsEkey@4");

                // Enable debugging to view the handshake and communication which happens between the SSLClient and the SSLServer
                // System.setProperty("javax.net.debug","all");
            }

            try {
                    // Initialize the Server Socket
                    SSLServerSocketFactory sslServerSocketfactory = (SSLServerSocketFactory)SSLServerSocketFactory.getDefault();
                    SSLServerSocket sslServerSocket = (SSLServerSocket)sslServerSocketfactory.createServerSocket(intSSLport);
                    SSLSocket sslSocket = (SSLSocket)sslServerSocket.accept();

                    // Create Input / Output Streams for communication with the client
                    while(true)
                    {
                    PrintWriter out = new PrintWriter(sslSocket.getOutputStream(), true);
                    BufferedReader in = new BufferedReader(
                            new InputStreamReader(
                                    sslSocket.getInputStream()));
                    String inputLine, outputLine;

                    while ((inputLine = in.readLine()) != null) {
                         out.println(inputLine);
                         System.out.println(inputLine);
                    }

                    // Close the streams and the socket
                    out.close();
                    in.close();
                    sslSocket.close();
                    sslServerSocket.close();

                    }
                }


            catch(Exception exp)
            {
                PrivilegedActionException priexp = new PrivilegedActionException(exp);
                System.out.println(" Priv exp --- " + priexp.getMessage());

                System.out.println(" Exception occurred .... " +exp);
                exp.printStackTrace();
            }

        }

    }

## References

  - Computer Security – Arts and Science - Matt Bishop
  - Core Security Patterns – Christopher Steele, Ray Lai and Ramesh
    Nagappan
  - <http://java.sun.com/j2se/##2/docs/tooldocs/windows/keytool.html>
  - <http://blogs.borland.com/krish/archive/2005/07/28/#aspx>

[Category:Java](Category:Java "wikilink")