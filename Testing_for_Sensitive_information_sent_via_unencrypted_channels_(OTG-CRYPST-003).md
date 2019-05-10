## Summary

Sensitive data must be protected when it is transmitted through the
network. If data is transmitted over HTTPS or encrypted in another way
the protection mechanism must not have limitations or vulnerabilities,
as explained in the broader article [Testing for Weak SSL/TLS Ciphers,
Insufficient Transport Layer Protection
(OTG-CRYPST-001)](https://www.owasp.org/index.php?title=Testing_for_Weak_SSL/TLS_Ciphers,_Insufficient_Transport_Layer_Protection_%28OTG-CRYPST-001%29)
\[1\] and in other OWASP documentation \[2\], \[3\], \[4\], \[5\].

As a rule of thumb if data must be protected when it is stored, this
data must also be protected during transmission. Some examples for
sensitive data are:

  - Information used in authentication (e.g. Credentials, PINs, Session
    identifiers, Tokens, Cookies…)
  - Information protected by laws, regulations or specific
    organizational policy (e.g. Credit Cards, Customers data)

If the application transmits sensitive information via unencrypted
channels - e.g. HTTP - it is considered a security risk. Some examples
are Basic authentication which sends authentication credentials in
plain-text over HTTP, form based authentication credentials sent via
HTTP, or plain-text transmission of any other information considered
sensitive due to regulations, laws, organizational policy or application
business logic.

Examples for Personal Identifying Information (PII) are:

  - Social security numbers
  - Bank account numbers
  - Passport information
  - Healthcare related information
  - Medical insurance information
  - Student information
  - Credit and debit card numbers
  - Drivers license and State ID information

## How to Test

Various types of information that must be protected, could be
transmitted by the application in clear text. It is possible to check if
this information is transmitted over HTTP instead of HTTPS, or whether
weak cyphers are used. See more information about insecure transmission
of credentials [Top 10 2013-A6-Sensitive Data
Exposure](https://www.owasp.org/index.php/Top_10_2013-A6-Sensitive_Data_Exposure)
\[3\] or insufficient transport layer protection in general
[Top 10 2010-A9-Insufficient Transport Layer
Protection](https://www.owasp.org/index.php/Top_10_2010-A9-Insufficient_Transport_Layer_Protection)
\[2\].

### Example 1: Basic Authentication over HTTP

A typical example is the usage of Basic Authentication over HTTP. When
using Basic Authentication, user credentials are encoded rather than
encrypted, and are sent as HTTP headers. In the example below the tester
uses curl \[5\] to test for this issue. Note how the application uses
Basic authentication, and HTTP rather than HTTPS

    $ curl -kis http://example.com/restricted/
    HTTP/1.1 401 Authorization Required
    Date: Fri, 01 Aug 2013 00:00:00 GMT
    WWW-Authenticate: Basic realm="Restricted Area"
    Accept-Ranges: bytes Vary:
    Accept-Encoding Content-Length: 162
    Content-Type: text/html

    <html><head><title>401 Authorization Required</title></head>
    <body bgcolor=white> <h1>401 Authorization Required</h1>  Invalid login credentials!  </body></html>

### Example 2: Form-Based Authentication Performed over HTTP

Another typical example is authentication forms which transmit user
authentication credentials over HTTP. In the example below one can see
HTTP being used in the "action" attribute of the form. It is also
possible to see this issue by examining the HTTP traffic with an
interception proxy.

    <form action="http://example.com/login">
        <label for="username">User:</label> <input type="text" id="username" name="username" value=""/><br />
        <label for="password">Password:</label> <input type="password" id="password" name="password" value=""/>
        <input type="submit" value="Login"/>
    </form>

### Example 3: Cookie Containing Session ID Sent over HTTP

The Session ID Cookie must be transmitted over protected channels. If
the cookie does not have the secure flag set \[6\] it is permitted for
the application to transmit it unencrypted. Note below the setting of
the cookie is done without the Secure flag, and the entire log in
process is performed in HTTP and not HTTPS.

    https://secure.example.com/login

    POST /login HTTP/1.1
    Host: secure.example.com
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://secure.example.com/
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 188

    HTTP/1.1 302 Found
    Date: Tue, 03 Dec 2013 21:18:55 GMT
    Server: Apache
    Cache-Control: no-store, no-cache, must-revalidate, max-age=0
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Pragma: no-cache
    Set-Cookie: JSESSIONID=BD99F321233AF69593EDF52B123B5BDA; expires=Fri, 01-Jan-2014 00:00:00 GMT; path=/; domain=example.com; httponly
    Location: private/
    X-Content-Type-Options: nosniff
    X-XSS-Protection: 1; mode=block
    X-Frame-Options: SAMEORIGIN
    Content-Length: 0
    Keep-Alive: timeout=1, max=100
    Connection: Keep-Alive
    Content-Type: text/html

    ----------------------------------------------------------
    http://example.com/private

    GET /private HTTP/1.1
    Host: example.com
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate
    Referer: https://secure.example.com/login
    Cookie: JSESSIONID=BD99F321233AF69593EDF52B123B5BDA;
    Connection: keep-alive

    HTTP/1.1 200 OK
    Cache-Control: no-store
    Pragma: no-cache
    Expires: 0
    Content-Type: text/html;charset=UTF-8
    Content-Length: 730
    Date: Tue, 25 Dec 2013 00:00:00 GMT
    ----------------------------------------------------------

### Example 4: Testing password sensitive information in source code or logs

Use one of the following techniques to search for senstive information.

Checking if password or encyrption key is hardcoded int h e source code
or configuration files.

    * grep -r –E "Pass
    | password
    | pwd
    |user
    | guest
    | admin
    | encry
    | key
    | decrypt
    | sharekey " ./PathToSearch/

Checking if logs or source code may contain phone number, email address,
ID or any other PII. Change the regular expression based on the format
of the PII.

    * grep -r " {2\}[0-9]\{6\} "  ./PathToSearch/

## Tools

  - \[5\] [curl](http://curl.haxx.se/) can be used to check manually for
    pages
  - grep
  - Identity Finder
    <http://download.cnet.com/Identity-Finder-Free-Edition/3000-2144_4-10906766.html>

## References

**OWASP Resources**

  - \[1\] [OWASP Testing Guide - Testing for Weak SSL/TLS Ciphers,
    Insufficient Transport Layer Protection
    (OTG-CRYPST-001)](https://www.owasp.org/index.php/Testing_for_Weak_SSL/TLS_Ciphers,_Insufficient_Transport_Layer_Protection_%28OTG-CRYPST-001%29)
  - \[2\] [OWASP TOP 10 2010 - Insufficient Transport Layer
    Protection](https://www.owasp.org/index.php/Top_10_2010-A9-Insufficient_Transport_Layer_Protection)
  - \[3\] [OWASP TOP 10 2013 - Sensitive Data
    Exposure](https://www.owasp.org/index.php/Top_10_2013-A6-Sensitive_Data_Exposure)
  - \[4\] [OWASP ASVS v1.1 - V10 Communication Security Verification
    Requirements](https://code.google.com/p/owasp-asvs/wiki/Verification_V10)
  - \[6\] [OWASP Testing Guide - Testing for Cookies attributes
    (OTG-SESS-002)](https://www.owasp.org/index.php/Testing_for_cookies_attributes_\(OTG-SESS-002\))