[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Transport Layer Protection

### Root Cause Summary

Not all traffic flowing between two endpoints is properly secured, which
makes it possible for attackers to perform man-in-the-middle attacks.

### Browser / Standards Solution

Implement HTTP Strict Transport Security in all browsers, which makes it
possible to better enforce secure connections. Implement Certificate and
Public Key pinning in browsers where applicable.

### Perimeter Solution

  - Make sure that SSL is properly configured on the server:
      - Disable all weak SSL/TLS protocols (such as SSLv2)
      - Disable all weak 'export' algorithms (such as DES, RC4-40,
        DHE-RSA-Export)
      - Make sure that the minimum session key size is 128 bits
      - Use a SSL certificate with a minimum key size of 2048 bits
      - Do not use MD5 as cryptographic hash algorithm
      - Do not use the RC4 algorithm
      - Disable anonymous key establishment algorithms (Anonymous
        Diffie-Hellman, aNULL)
      - Disable algorithms offering no encryption (NULL, eNULL)
  - Enforce HTTP Strict Transport Security (HSTS)
  - Redirect all HTTP request to HTTPS

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

  - HTTP Strict Transport Security is at the entry-level maturity, a
    proposed standard. Not all browsers implement it (yet).
  - The security of ciphers changes over time, so it's important to
    periodically review whether certain ciphers and minimum key sizes
    are still considered safe enough.
  - Certificate and Public Key Pinning is a relatively new technique and
    not widely used or implemented. Google Chrome's browser is one of
    the first major browsers to use this technique.
  - According to NIST SP800-52, RC4 is "acceptable for use \[..\] where
    secure information is to be transferred \[..\] and 3DES or better
    (e.g., AES) is not supported by the server".
  - According to the RFC 7465 the use of RC4 is prohibited in TLS. This
    applies to all TLS Versions. "This document requires that Transport
    Layer Security (TLS) clients and servers never negotiate the use of
    RC4 cipher suites when they establish connections."

### References

[Insufficient Transport Layer Protection
(OWASP)](https://www.owasp.org/index.php/Top_10_2010-A9-Insufficient_Transport_Layer_Protection)
[Insufficient Transport Layer Protection (WASC
TC)](http://projects.webappsec.org/w/page/13246945/Insufficient%20Transport%20Layer%20Protection)
[Guidelines for the Selection and Use of Transport Layer Security (TLS)
Implementations (NIST
SP 800-52)](http://csrc.nist.gov/publications/nistpubs/800-52/SP800-52.pdf)
[HTTP Strict Transport Security
(IETF)](http://tools.ietf.org/html/rfc6797)
[Certificate and Public Key Pinning
(OWASP)](https://www.owasp.org/index.php/Certificate_and_Public_Key_Pinning)
[Google Chrome implements certificate pinning
(Google)](http://blog.chromium.org/2011/06/new-chromium-security-features-june.html)