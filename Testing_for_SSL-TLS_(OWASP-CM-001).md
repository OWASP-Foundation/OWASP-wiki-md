## Brief Summary

Due to historic export restrictions of high grade cryptography, legacy
and new web servers are often able and configured to handle weak
cryptographic options.

Even if high grade ciphers are normally used and installed, some server
misconfiguration could be used to force the use of a weaker cipher to
gain access to the supposed secure communication channel.

## Testing SSL / TLS Cipher Specifications and Requirements

The http clear-text protocol is normally secured via an SSL or TLS
tunnel, resulting in https traffic. In addition to providing encryption
of data in transit, https allows the identification of servers (and,
optionally, of clients) by means of digital certificates.

Historically, there have been limitations set in place by the U.S.
government to allow cryptosystems to be exported only for key sizes of,
at most, 40 bits, a key length which could be broken and would allow the
decryption of communications. Since then, cryptographic export
regulations have been relaxed (though some constraints still hold);
however, it is important to check the SSL configuration being used to
avoid putting in place cryptographic support which could be easily
defeated. SSL-based services should not offer the possibility to choose
weak ciphers.

Cipher determination is performed as follows: in the initial phase of a
SSL connection setup, the client sends the server a Client Hello message
specifying, among other information, the cipher suites that it is able
to handle. A client is usually a web browser (most popular SSL client
nowadays), but not necessarily, since it can be any SSL-enabled
application; the same holds for the server, which needs not be a web
server, though this is the most common case. (For example, a noteworthy
class of SSL clients is that of SSL proxies such as stunnel
(www.stunnel.org) which can be used to allow non-SSL enabled tools to
talk to SSL services.) A cipher suite is specified by an encryption
protocol (DES, RC4, AES), the encryption key length (such as 40, 56, or
128 bits), and a hash algorithm (SHA, MD5) used for integrity checking.
Upon receiving a Client Hello message, the server decides which cipher
suite it will use for that session. It is possible (for example, by
means of configuration directives) to specify which cipher suites the
server will honor. In this way you may control, for example, whether or
not conversations with clients will support 40-bit encryption only.

## SSL Testing Criteria

Large number of available cipher suites and quick progress in
cryptoanalysis makes judging a SSL server a non-trivial task. These
criteria are widely recognised as minimum checklist:

  - SSLv2, due to known weaknesses in protocol design
    [1](http://www.schneier.com/paper-ssl.html)
  - SSLv3, due to known weaknesses in protocol design
    [2](http://www.yaksman.org/~lweith/ssl.pdf)
  - Compression, due to known weaknesses in protocol design
    [3](http://www.ekoparty.org/2012/juliano-rizzo.php)
  - Cipher suites with symmetric encryption algorithm smaller than 112
    bits
  - X.509 certificates with RSA key smaller than 2048 bits
  - X.509 certificates with DSA key smaller than 2048 bits
  - X.509 certificates signed using MD5 hash, due to known collision
    attacks on this hash
  - TLS Renegotiation vulnerability
    [4](http://www.phonefactor.com/sslgap/ssl-tls-authentication-patches)

The following standards can be used as reference while assessing SSL
servers:

  - [NIST
    SP 800-52](http://csrc.nist.gov/publications/nistpubs/800-52/SP800-52.pdf)
    recommends U.S. federal systems to use at least TLS 1.0 with
    ciphersuites based on RSA or DSA key agreement with ephemeral
    Diffie-Hellman, 3DES or AES for confidentality and SHA1 for
    integrity protection. NIST SP 800-52 specifically disallows non-FIPS
    compliant algorithms like RC4 and MD5. An exception is U.S. federal
    systems making connections to outside servers, where these
    algorithms can be used in SSL client mode.
  - [PCI-DSS
    v1.2](https://www.pcisecuritystandards.org/security_standards/pci_dss.shtml)
    in point 4.1 requires compliant parties to use "strong cryptography"
    without precisely defining key lengths and algorithms. Common
    interpretation, partially based on previous versions of the
    standard, is that at least 128 bit key cipher, no export strength
    algorithms and no SSLv2 should be
    used[5](http://www.digicert.com/news/DigiCert_PCI_White_Paper.pdf).
  - [SSL Server Rating
    Guide](https://www.ssllabs.com/projects/rating-guide/index.html) has
    been proposed to standardize SSL server assessment and currently is
    in draft version.

SSL Server Database can be used to assess configuration of publicly
available SSL servers[6](https://www.ssllabs.com/ssldb/analyze.html)
based on SSL Rating
Guide[7](https://www.ssllabs.com/projects/rating-guide/index.html)

## Black Box Test and example

In order to detect possible support of weak ciphers, the ports
associated to SSL/TLS wrapped services must be identified. These
typically include port 443, which is the standard https port; however,
this may change because a) https services may be configured to run on
non-standard ports, and b) there may be additional SSL/TLS wrapped
services related to the web application. In general, a service discovery
is required to identify such ports.

The nmap scanner, via the “–sV” scan option, is able to identify SSL
services. Vulnerability Scanners, in addition to performing service
discovery, may include checks against weak ciphers (for example, the
Nessus scanner has the capability of checking SSL services on arbitrary
ports, and will report weak ciphers).

**Example 1**. SSL service recognition via nmap.

    [root@test]# nmap -F -sV localhost

    Starting nmap 3.75 ( http://www.insecure.org/nmap/ ) at 2005-07-27 14:41 CEST
    Interesting ports on localhost.localdomain (127.0.0.1):
    (The 1205 ports scanned but not shown below are in state: closed)

    PORT      STATE SERVICE         VERSION
    443/tcp   open  ssl             OpenSSL
    901/tcp   open  http            Samba SWAT administration server
    8080/tcp  open  http            Apache httpd 2.0.54 ((Unix) mod_ssl/2.0.54 OpenSSL/0.9.7g PHP/4.3.11)
    8081/tcp  open  http            Apache Tomcat/Coyote JSP engine 1.0

    Nmap run completed -- 1 IP address (1 host up) scanned in 27.881 seconds
    [root@test]#

**Example 2**. Identifying weak ciphers with Nessus. The following is an
anonymized excerpt of a report generated by the Nessus scanner,
corresponding to the identification of a server certificate allowing
weak ciphers (see underlined text).

` `**`https``   ``(443/tcp)`**
` `**`Description`**
` Here is the SSLv2 server certificate:`
` Certificate:`
` Data:`
` Version: 3 (0x2)`
` Serial Number: 1 (0x1)`
` Signature Algorithm: md5WithRSAEncryption`
` Issuer: C=**, ST=******, L=******, O=******, OU=******, CN=******`
` Validity`
` Not Before: Oct 17 07:12:16 2002 GMT`
` Not After : Oct 16 07:12:16 2004 GMT`
` Subject: C=**, ST=******, L=******, O=******, CN=******`
` Subject Public Key Info:`
` Public Key Algorithm: rsaEncryption`
` RSA Public Key: (1024 bit)`
` Modulus (1024 bit):`
` 00:98:4f:24:16:cb:0f:74:e8:9c:55:ce:62:14:4e:`
` 6b:84:c5:81:43:59:c1:2e:ac:ba:af:92:51:f3:0b:`
` ad:e1:4b:22:ba:5a:9a:1e:0f:0b:fb:3d:5d:e6:fc:`
` ef:b8:8c:dc:78:28:97:8b:f0:1f:17:9f:69:3f:0e:`
` 72:51:24:1b:9c:3d:85:52:1d:df:da:5a:b8:2e:d2:`
` 09:00:76:24:43:bc:08:67:6b:dd:6b:e9:d2:f5:67:`
` e1:90:2a:b4:3b:b4:3c:b3:71:4e:88:08:74:b9:a8:`
` 2d:c4:8c:65:93:08:e6:2f:fd:e0:fa:dc:6d:d7:a2:`
` 3d:0a:75:26:cf:dc:47:74:29`
` Exponent: 65537 (0x10001)`
` X509v3 extensions:`
` X509v3 Basic Constraints:`
` CA:FALSE`
` Netscape Comment:`
` OpenSSL Generated Certificate`
` Page 10`
` Network Vulnerability Assessment Report 25.05.2005`
` X509v3 Subject Key Identifier:`
` 10:00:38:4C:45:F0:7C:E4:C6:A7:A4:E2:C9:F0:E4:2B:A8:F9:63:A8`
` X509v3 Authority Key Identifier:`
` keyid:CE:E5:F9:41:7B:D9:0E:5E:5D:DF:5E:B9:F3:E6:4A:12:19:02:76:CE`
` DirName:/C=**/ST=******/L=******/O=******/OU=******/CN=******`
` serial:00`
` Signature Algorithm: md5WithRSAEncryption`
` 7b:14:bd:c7:3c:0c:01:8d:69:91:95:46:5c:e6:1e:25:9b:aa:`
` 8b:f5:0d:de:e3:2e:82:1e:68:be:97:3b:39:4a:83:ae:fd:15:`
` 2e:50:c8:a7:16:6e:c9:4e:76:cc:fd:69:ae:4f:12:b8:e7:01:`
` b6:58:7e:39:d1:fa:8d:49:bd:ff:6b:a8:dd:ae:83:ed:bc:b2:`
` 40:e3:a5:e0:fd:ae:3f:57:4d:ec:f3:21:34:b1:84:97:06:6f:`
` f4:7d:f4:1c:84:cc:bb:1c:1c:e7:7a:7d:2d:e9:49:60:93:12:`
` 0d:9f:05:8c:8e:f9:cf:e8:9f:fc:15:c0:6e:e2:fe:e5:07:81:`
` 82:fc`
` Here is the list of available SSLv2 ciphers:`
` RC4-MD5`
` EXP-RC4-MD5`
` RC2-CBC-MD5`
` EXP-RC2-CBC-MD5`
` DES-CBC-MD5`
` DES-CBC3-MD5`
` RC4-64-MD5`
` `<u>`The SSLv2 server offers 5 strong ciphers, but also 0 medium strength and `**`2``
 ``weak``   ``"export``   ``class"``   ``ciphers`**`.`
` The weak/medium ciphers may be chosen by an export-grade or badly configured client software. They only offer a limited protection against a brute force attack`</u>
` `<u>`Solution: disable those ciphers and upgrade your client software if necessary.`</u>
` See `<http://support.microsoft.com/default.aspx?scid=kben-us216482>
` or `<http://httpd.apache.org/docs-2.0/mod/mod_ssl.html#sslciphersuite>
` This SSLv2 server also accepts SSLv3 connections.`
` This SSLv2 server also accepts TLSv1 connections.`
` `
` Vulnerable hosts`
` `*`(list``   ``of``   ``vulnerable``   ``hosts``   ``follows)`*

**Example 3**. Manually audit weak SSL cipher levels with OpenSSL. The
following will attempt to connect to Google.com with SSLv2.

    [root@test]# openssl s_client -no_tls1 -no_ssl3 -connect www.google.com:443
    CONNECTED(00000003)
    depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=www.google.com
    verify error:num=20:unable to get local issuer certificate
    verify return:1
    depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=www.google.com
    verify error:num=27:certificate not trusted
    verify return:1
    depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=www.google.com
    verify error:num=21:unable to verify the first certificate
    verify return:1
    ---
    Server certificate
    -----BEGIN CERTIFICATE-----
    MIIDYzCCAsygAwIBAgIQYFbAC3yUC8RFj9MS7lfBkzANBgkqhkiG9w0BAQQFADCB
    zjELMAkGA1UEBhMCWkExFTATBgNVBAgTDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBxMJ
    Q2FwZSBUb3duMR0wGwYDVQQKExRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UE
    CxMfQ2VydGlmaWNhdGlvbiBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAxMYVGhh
    d3RlIFByZW1pdW0gU2VydmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNl
    cnZlckB0aGF3dGUuY29tMB4XDTA2MDQyMTAxMDc0NVoXDTA3MDQyMTAxMDc0NVow
    aDELMAkGA1UEBhMCVVMxEzARBgNVBAgTCkNhbGlmb3JuaWExFjAUBgNVBAcTDU1v
    dW50YWluIFZpZXcxEzARBgNVBAoTCkdvb2dsZSBJbmMxFzAVBgNVBAMTDnd3dy5n
    b29nbGUuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC/e2Vs8U33fRDk
    5NNpNgkB1zKw4rqTozmfwty7eTEI8PVH1Bf6nthocQ9d9SgJAI2WOBP4grPj7MqO
    dXMTFWGDfiTnwes16G7NZlyh6peT68r7ifrwSsVLisJp6pUf31M5Z3D88b+Yy4PE
    D7BJaTxq6NNmP1vYUJeXsGSGrV6FUQIDAQABo4GmMIGjMB0GA1UdJQQWMBQGCCsG
    AQUFBwMBBggrBgEFBQcDAjBABgNVHR8EOTA3MDWgM6Axhi9odHRwOi8vY3JsLnRo
    YXd0ZS5jb20vVGhhd3RlUHJlbWl1bVNlcnZlckNBLmNybDAyBggrBgEFBQcBAQQm
    MCQwIgYIKwYBBQUHMAGGFmh0dHA6Ly9vY3NwLnRoYXd0ZS5jb20wDAYDVR0TAQH/
    BAIwADANBgkqhkiG9w0BAQQFAAOBgQADlTbBdVY6LD1nHWkhTadmzuWq2rWE0KO3
    Ay+7EleYWPOo+EST315QLpU6pQgblgobGoI5x/fUg2U8WiYj1I1cbavhX2h1hda3
    FJWnB3SiXaiuDTsGxQ267EwCVWD5bCrSWa64ilSJTgiUmzAv0a2W8YHXdG08+nYc
    X/dVk5WRTw==
    -----END CERTIFICATE-----
    subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=www.google.com
    issuer=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
    ---
    No client certificate CA names sent
    ---
    Ciphers common between both SSL endpoints:
    RC4-MD5         EXP-RC4-MD5     RC2-CBC-MD5
    EXP-RC2-CBC-MD5 DES-CBC-MD5     DES-CBC3-MD5
    RC4-64-MD5
    ---
    SSL handshake has read 1023 bytes and written 333 bytes
    ---
    New, SSLv2, Cipher is DES-CBC3-MD5
    Server public key is 1024 bit
    Compression: NONE
    Expansion: NONE
    SSL-Session:
        Protocol  : SSLv2
        Cipher    : DES-CBC3-MD5
        Session-ID: 709F48E4D567C70A2E49886E4C697CDE
        Session-ID-ctx:
        Master-Key: 649E68F8CF936E69642286AC40A80F433602E3C36FD288C3
        Key-Arg   : E8CB6FEB9ECF3033
        Start Time: 1156977226
        Timeout   : 300 (sec)
        Verify return code: 21 (unable to verify the first certificate)
    ---
    closed

**Example 4**. Testing supported protocols and ciphers using SSLScan.

SSLScan is a free command line tool that scans a HTTPS service to
enumerate what protocols (supports SSLv2, SSLv3 and TLS1) and what
ciphers the HTTPS service supports. It runs both on Linux and Windows OS
(OSX not tested) and is released under a open source license.

    [user@test]$ ./SSLScan --no-failed mail.google.com
                       _
               ___ ___
    |
    |___  ___ __ _ _ __
              / __/ __
    | / __
    |/ __/ _`
    | '_ \
              __ __ \ __ \ (_
    | (_
    |
    |
    |
    |
    |

    |___/___/_
    |___/_____,_
    |_
    |
    |_
    |

                      Version 1.9.0-win
                 http://www.titania.co.uk
     Copyright 2010 Ian Ventura-Whiting / Michael Boman
        Compiled against OpenSSL 0.9.8n 24 Mar 2010

    Testing SSL server mail.google.com on port 443

      Supported Server Cipher(s):
        accepted  SSLv3  256 bits  AES256-SHA
        accepted  SSLv3  128 bits  AES128-SHA
        accepted  SSLv3  168 bits  DES-CBC3-SHA
        accepted  SSLv3  128 bits  RC4-SHA
        accepted  SSLv3  128 bits  RC4-MD5
        accepted  TLSv1  256 bits  AES256-SHA
        accepted  TLSv1  128 bits  AES128-SHA
        accepted  TLSv1  168 bits  DES-CBC3-SHA
        accepted  TLSv1  128 bits  RC4-SHA
        accepted  TLSv1  128 bits  RC4-MD5

      Prefered Server Cipher(s):
        SSLv3  128 bits  RC4-SHA
        TLSv1  128 bits  RC4-SHA

      SSL Certificate:
        Version: 2
        Serial Number: -4294967295
        Signature Algorithm: sha1WithRSAEncryption
        Issuer: /C=ZA/O=Thawte Consulting (Pty) Ltd./CN=Thawte SGC CA
        Not valid before: Dec 18 00:00:00 2009 GMT
        Not valid after: Dec 18 23:59:59 2011 GMT
        Subject: /C=US/ST=California/L=Mountain View/O=Google Inc/CN=mail.google.com
        Public Key Algorithm: rsaEncryption
        RSA Public Key: (1024 bit)
          Modulus (1024 bit):
              00:d9:27:c8:11:f2:7b:e4:45:c9:46:b6:63:75:83:
              b1:77:7e:17:41:89:80:38:f1:45:27:a0:3c:d9:e8:
              a8:00:4b:d9:07:d0:ba:de:ed:f4:2c:a6:ac:dc:27:
              13:ec:0c:c1:a6:99:17:42:e6:8d:27:d2:81:14:b0:
              4b:82:fa:b2:c5:d0:bb:20:59:62:28:a3:96:b5:61:
              f6:76:c1:6d:46:d2:fd:ba:c6:0f:3d:d1:c9:77:9a:
              58:33:f6:06:76:32:ad:51:5f:29:5f:6e:f8:12:8b:
              ad:e6:c5:08:39:b3:43:43:a9:5b:91:1d:d7:e3:cf:
              51:df:75:59:8e:8d:80:ab:53
          Exponent: 65537 (0x10001)
        X509v3 Extensions:
          X509v3 Basic Constraints: critical
            CA:FALSE      X509v3 CRL Distribution Points:
            URI:http://crl.thawte.com/ThawteSGCCA.crl
          X509v3 Extended Key Usage:
            TLS Web Server Authentication, TLS Web Client Authentication, Netscape Server Gated Crypto      Authority Information Access:
            OCSP - URI:http://ocsp.thawte.com
            CA Issuers - URI:http://www.thawte.com/repository/Thawte_SGC_CA.crt
      Verify Certificate:
        unable to get local issuer certificate


    Renegotiation requests supported

**Example 5**. Testing common SSL flaws with ssl_tests

ssl_tests (http://www.pentesterscripting.com/discovery/ssl_tests) is a
bash script that uses sslscan and openssl to check for various flaws -
ssl version 2, weak ciphers, md5withRSAEncryption,SSLv3 Force Ciphering
Bug/Renegotiation.

```

[user@test]$ ./ssl_test.sh 192.168.1.3 443
+++++++++++++++++++++++++++++++++++++++++++++++++
SSL Tests - v2, weak ciphers, MD5, Renegotiation
by Aung Khant, http://yehg.net
+++++++++++++++++++++++++++++++++++++++++++++++++

[*] testing on 192.168.1.3:443 ..

[*] tesing for sslv2 ..
[*] sslscan 192.168.1.3:443
| grep Accepted  SSLv2
    Accepted  SSLv2  168 bits  DES-CBC3-MD5
    Accepted  SSLv2  56 bits   DES-CBC-MD5
    Accepted  SSLv2  40 bits   EXP-RC2-CBC-MD5
    Accepted  SSLv2  128 bits  RC2-CBC-MD5
    Accepted  SSLv2  40 bits   EXP-RC4-MD5
    Accepted  SSLv2  128 bits  RC4-MD5


[*] testing for weak ciphers ...
[*] sslscan 192.168.1.3:443
| grep  40 bits
| grep Accepted
    Accepted  SSLv2  40 bits   EXP-RC2-CBC-MD5
    Accepted  SSLv2  40 bits   EXP-RC4-MD5
    Accepted  SSLv3  40 bits   EXP-EDH-RSA-DES-CBC-SHA
    Accepted  SSLv3  40 bits   EXP-DES-CBC-SHA
    Accepted  SSLv3  40 bits   EXP-RC2-CBC-MD5
    Accepted  SSLv3  40 bits   EXP-RC4-MD5
    Accepted  TLSv1  40 bits   EXP-EDH-RSA-DES-CBC-SHA
    Accepted  TLSv1  40 bits   EXP-DES-CBC-SHA
    Accepted  TLSv1  40 bits   EXP-RC2-CBC-MD5
    Accepted  TLSv1  40 bits   EXP-RC4-MD5

[*] sslscan 192.168.1.3:443
| grep  56 bits
| grep Accepted
    Accepted  SSLv2  56 bits   DES-CBC-MD5
    Accepted  SSLv3  56 bits   EDH-RSA-DES-CBC-SHA
    Accepted  SSLv3  56 bits   DES-CBC-SHA
    Accepted  TLSv1  56 bits   EDH-RSA-DES-CBC-SHA
    Accepted  TLSv1  56 bits   DES-CBC-SHA


[*] testing for MD5 certificate ..
[*] sslscan 192.168.1.3:443
| grep MD5WithRSAEncryption

[*] testing for SSLv3 Force Ciphering Bug/Renegotiation ..
[*] echo R
| openssl s_client -connect 192.168.1.3:443
| grep DONE
depth=0 /C=DE/ST=Berlin/L=Berlin/O=XAMPP/OU=XAMPP/CN=localhost/emailAddress=admin@localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 /C=DE/ST=Berlin/L=Berlin/O=XAMPP/OU=XAMPP/CN=localhost/emailAddress=admin@localhost
verify return:1
RENEGOTIATING
depth=0 /C=DE/ST=Berlin/L=Berlin/O=XAMPP/OU=XAMPP/CN=localhost/emailAddress=admin@localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 /C=DE/ST=Berlin/L=Berlin/O=XAMPP/OU=XAMPP/CN=localhost/emailAddress=admin@localhost
verify return:1
DONE


[*] done
```

## White Box Test and example

Check the configuration of the web servers which provide https services.
If the web application provides other SSL/TLS wrapped services, these
should be checked as well.

**Example:** The following registry path in Microsoft Windows 2003
defines the ciphers available to the server:

HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL\\Ciphers\\

## Testing SSL certificate validity – client and server

When accessing a web application via the https protocol, a secure
channel is established between the client (usually the browser) and the
server. The identity of one (the server) or both parties (client and
server) is then established by means of digital certificates. In order
for the communication to be set up, a number of checks on the
certificates must be passed. While discussing SSL and certificate based
authentication is beyond the scope of this Guide, we will focus on the
main criteria involved in ascertaining certificate validity: a) checking
if the Certificate Authority (CA) is a known one (meaning one considered
trusted), b) checking that the certificate is currently valid, and c)
checking that the name of the site and the name reported in the
certificate match. Remember to upgrade your browser because CA certs
expired too, in every release of the browser, CA Certs has been renewed.
Moreover it's important to update the browser because more web sites
require strong cipher more of 40 or 56 bit.

Let’s examine each check more in detail.

a) Each browser comes with a preloaded list of trusted CAs, against
which the certificate signing CA is compared (this list can be
customized and expanded at will). During the initial negotiations with
an https server, if the server certificate relates to a CA unknown to
the browser, a warning is usually raised. This happens most often
because a web application relies on a certificate signed by a
self-established CA. Whether this is to be considered a concern depends
on several factors. For example, this may be fine for an Intranet
environment (think of corporate web email being provided via https;
here, obviously all users recognize the internal CA as a trusted CA).
When a service is provided to the general public via the Internet,
however (i.e. when it is important to positively verify the identity of
the server we are talking to), it is usually imperative to rely on a
trusted CA, one which is recognized by all the user base (and here we
stop with our considerations; we won’t delve deeper in the implications
of the trust model being used by digital certificates).

b) Certificates have an associated period of validity, therefore they
may expire. Again, we are warned by the browser about this. A public
service needs a temporally valid certificate; otherwise, it means we are
talking with a server whose certificate was issued by someone we trust,
but has expired without being renewed.

c) What if the name on the certificate and the name of the server do not
match? If this happens, it might sound suspicious. For a number of
reasons, this is not so rare to see. A system may host a number of
name-based virtual hosts, which share the same IP address and are
identified by means of the HTTP 1.1 Host: header information. In this
case, since the SSL handshake checks the server certificate before the
HTTP request is processed, it is not possible to assign different
certificates to each virtual server. Therefore, if the name of the site
and the name reported in the certificate do not match, we have a
condition which is typically signalled by the browser. To avoid this,
one of two techniques should be used. First is Server Name Indication
(SNI), which is a TLS extension from
[RFC 3546](http://www.ietf.org/rfc/rfc3546.txt); and second is IP-based
virtual servers must be used. \[2\] and \[3\] describe techniques to
deal with this problem and allow name-based virtual hosts to be
correctly referenced.

### Black Box Testing and examples

Examine the validity of the certificates used by the application.
Browsers will issue a warning when encountering expired certificates,
certificates issued by untrusted CAs, and certificates which do not
match namewise with the site to which they should refer. By clicking on
the padlock which appears in the browser window when visiting an https
site, you can look at information related to the certificate – including
the issuer, period of validity, encryption characteristics, etc.

If the application requires a client certificate, you probably have
installed one to access it. Certificate information is available in the
browser by inspecting the relevant certificate(s) in the list of the
installed certificates.

These checks must be applied to all visible SSL-wrapped communication
channels used by the application. Though this is the usual https service
running on port 443, there may be additional services involved depending
on the web application architecture and on deployment issues (an https
administrative port left open, https services on non-standard ports,
etc.). Therefore, apply these checks to all SSL-wrapped ports which have
been discovered. For example, the nmap scanner features a scanning mode
(enabled by the –sV command line switch) which identifies SSL-wrapped
services. The Nessus vulnerability scanner has the capability of
performing SSL checks on all SSL/TLS-wrapped services.

**Examples**

Rather than providing a fictitious example, we have inserted an
anonymized real-life example to stress how frequently one stumbles on
https sites whose certificates are inaccurate with respect to naming.

The following screenshots refer to a regional site of a high-profile IT
company.

<u>Warning issued by Microsoft Internet Explorer.</u> We are visiting an
*.it* site and the certificate was issued to a ''.com ''site\! Internet
Explorer warns that the name on the certificate does not match the name
of the site.

![Image:SSL Certificate Validity Testing IE
Warning.gif](SSL_Certificate_Validity_Testing_IE_Warning.gif
"Image:SSL Certificate Validity Testing IE Warning.gif")

<u>Warning issued by Mozilla Firefox.</u> The message issued by Firefox
is different – Firefox complains because it cannot ascertain the
identity of the *.com* site the certificate refers to because it does
not know the CA which signed the certificate. In fact, Internet Explorer
and Firefox do not come preloaded with the same list of CAs. Therefore,
the behavior experienced with various browsers may differ.

![Image:SSL Certificate Validity Testing Firefox
Warning.gif](SSL_Certificate_Validity_Testing_Firefox_Warning.gif
"Image:SSL Certificate Validity Testing Firefox Warning.gif")

### White Box Testing and examples

Examine the validity of the certificates used by the application at both
server and client levels. The usage of certificates is primarily at the
web server level; however, there may be additional communication paths
protected by SSL (for example, towards the DBMS). You should check the
application architecture to identify all SSL protected channels.

## References

**Whitepapers**
\* \[1\] RFC2246. The TLS Protocol Version 1.0 (updated by RFC3546) -
<http://www.ietf.org/rfc/rfc2246.txt>

  - \[2\] RFC2817. Upgrading to TLS Within HTTP/1.1 -
    <http://www.ietf.org/rfc/rfc2817.txt>
  - \[3\] RFC3546. Transport Layer Security (TLS) Extensions -
    <http://www.ietf.org/rfc/rfc3546.txt>
  - \[4\] <u>www.verisign.net</u> features various material on the topic
  - <https://github.com/ssllabs/research/wiki>

**Tools**

  - <https://www.ssllabs.com/ssldb/>

<!-- end list -->

  - Vulnerability scanners may include checks regarding certificate
    validity, including name mismatch and time expiration. They usually
    report other information as well, such as the CA which issued the
    certificate. Remember that there is no unified notion of a “trusted
    CA”; what is trusted depends on the configuration of the software
    and on the human assumptions made beforehand. Browsers come with a
    preloaded list of trusted CAs. If your web application relies on a
    CA which is not in this list (for example, because you rely on a
    self-made CA), you should take into account the process of
    configuring user browsers to recognize the CA.

<!-- end list -->

  - The Nessus scanner includes a plugin to check for expired
    certificates or certificates which are going to expire within 60
    days (plugin “SSL certificate expiry”, plugin id 15901). This plugin
    will check certificates ''installed on the server.

<!-- end list -->

  - Vulnerability scanners may include checks against weak ciphers. For
    example, the Nessus scanner (http://www.nessus.org) has this
    capability and flags the presence of SSL weak ciphers (see example
    provided above).

<!-- end list -->

  - You may also rely on specialized tools such as SSL Digger
    (http://www.mcafee.com/us/downloads/free-tools/ssldigger.aspx), or –
    for the command line oriented – experiment with the openssl tool,
    which provides access to OpenSSL cryptographic functions directly
    from a Unix shell (may be already available on \*nix boxes,
    otherwise see www.openssl.org).

<!-- end list -->

  - To identify SSL-based services, use a vulnerability scanner or a
    port scanner with service recognition capabilities. The nmap scanner
    features a “-sV” scanning option which tries to identify services,
    while the nessus vulnerability scanner has the capability of
    identifying SSL-based services on arbitrary ports and to run
    vulnerability checks on them regardless of whether they are
    configured on standard or non-standard ports.

<!-- end list -->

  - In case you need to talk to a SSL service but your favourite tool
    doesn’t support SSL, you may benefit from a SSL proxy such as
    stunnel; stunnel will take care of tunneling the underlying protocol
    (usually http, but not necessarily so) and communicate with the SSL
    service you need to reach.

<!-- end list -->

  - ssl_tests, <http://www.pentesterscripting.com/discovery/ssl_tests>

<!-- end list -->

  - testssl.sh <http://drwetter.eu/software/ssl/>

<!-- end list -->

  - O-Saft [<https://www.owasp.org/index.php/O-Saft>](O-Saft "wikilink")
    can test for **any** cipher, independent of the underlaying SSL
    library (such as OpenSSL).

<!-- end list -->

  - Nmap includes NSE scripts to test for SSLv2
    (https://nmap.org/nsedoc/scripts/sslv2.html) and enumerating
    SSLv3/TLS ciphers
    (https://nmap.org/nsedoc/scripts/ssl-enum-ciphers.html).
    Additionally it can also detect Diffie-Hellman weaknesses
    (https://nmap.org/nsedoc/scripts/ssl-dh-params.html), Poodle
    (https://nmap.org/nsedoc/scripts/ssl-poodle.html) and even
    Heartbleed (https://nmap.org/nsedoc/scripts/ssl-heartbleed.html)

<!-- end list -->

  - Finally, a word of advice. Though it may be tempting to use a
    regular browser to check certificates, there are various reasons for
    not doing so. Browsers have been plagued by various bugs in this
    area, and the way the browser will perform the check might be
    influenced by configuration settings that may not be evident.
    Instead, rely on vulnerability scanners or on specialized tools to
    do the job.

<!-- end list -->

  - [OWASP Transport Layer Protection Cheat
    Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")

<!-- end list -->

  - [High-Tech Bridge](https://www.htbridge.com/ssl/) - Online tool to
    verify SSL/TLS compliance with NIST SP 800-52 guidelines and PCI DSS
    requirements on any TCP port.

[Category:Cryptographic
Vulnerability](Category:Cryptographic_Vulnerability "wikilink")
[Category:SSL](Category:SSL "wikilink")